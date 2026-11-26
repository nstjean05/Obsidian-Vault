# Install guide (you already have the Cloudflare Tunnel)

This is the short path for a server that already has a tunnel and no need for Docker.
(The Docker path is in `docs/00-START-HERE.md` if you prefer it. The database files are identical either way.)

## What you have

| Download | What is in it |
|---|---|
| `omada-frontend.zip` | The pages: 4 HTML files, 1 CSS file, 5 JavaScript files |
| `omada-database.zip` | The database: 5 SQL scripts, the single combined `omada_full.sql`, the install script |
| `omada-scheduler-full.zip` | Everything above **plus the backend** and the docs. Use this one to install. |

**The pages cannot work on their own.** Every screen fetches its data from `/api/...` on the same web address, and that is the backend (the Python program in `backend/`). The backend also serves the pages, so you only run one thing and your tunnel points at one place: `http://localhost:8000`.

```
browser  --https-->  Cloudflare Tunnel  -->  backend on port 8000  -->  PostgreSQL
                                             (serves the pages too)
```

## Install in 5 steps (Ubuntu 24.04)

I tested this setup with Python 3.12 and PostgreSQL 16, which is what Ubuntu 24.04 gives you. On Ubuntu 22.04 the default Python is older, so use the Docker path there.

### 1. Put the files on the server

```bash
sudo apt update && sudo apt install -y postgresql python3-venv unzip
sudo unzip omada-scheduler-full.zip -d /opt          # creates /opt/omada-scheduler
sudo chown -R "$USER": /opt/omada-scheduler          # so you can create files in it (step 5 hands it to a service user)
cd /opt/omada-scheduler
```

### 2. Create the database

Choose a password for the application's database login and keep it. You will paste the same one into a settings file in step 3.

```bash
export APP_DB_PASSWORD=$(openssl rand -hex 16)
echo "$APP_DB_PASSWORD"                      # copy this somewhere safe
./scripts/install_db_native.sh               # creates database "omada" with the sample data
```

It prints `tables: 16` at the end. (Add `SKIP_SEED=1` in front of the command for an empty database with no sample data.)
Prefer pgAdmin? Create an empty database, open `omada_full.sql` in the Query Tool and run it, then give the application login a password: `ALTER ROLE omada_app WITH LOGIN PASSWORD 'your-password';`

### 3. Set up the backend

```bash
cd /opt/omada-scheduler/backend
python3 -m venv .venv
.venv/bin/pip install -r requirements.txt
cp .env.example .env && chmod 600 .env
nano .env
```

In `.env` change these (leave the rest for later):

| Setting | Value |
|---|---|
| `DATABASE_URL` | `postgresql://omada_app:THE_PASSWORD_FROM_STEP_2@127.0.0.1:5432/omada` |
| `SECRET_KEY` | the output of `openssl rand -hex 32` |
| `COOKIE_SECURE` | `true` (your tunnel address is https) |
| `DEMO_LOGIN_ENABLED` | `true` (so you can sign in before Google is set up) |
| `DEMO_LOGIN_PASSPHRASE` | a passphrase you choose |

Start it by hand to see it work:

```bash
.venv/bin/uvicorn app.main:app --host 127.0.0.1 --port 8000
```

In a second terminal: `curl http://127.0.0.1:8000/api/health` should print `{"status":"ok"}`. Press Ctrl+C in the first terminal when you are happy.

### 4. Point the tunnel at it

In Cloudflare: **Networking > Tunnels** > your tunnel > **Routes**. Set the service for your hostname to `http://localhost:8000`.
If your `cloudflared` connector runs inside a Docker container, `localhost` means that container, so use the server's address instead (for example `http://172.17.0.1:8000`).

Open `https://your-hostname/`. You should see the OMADA sign-in page with a "demo sign-in" form. Sign in with:

* `manager@example.test` (manager dashboard)
* `employee@example.test` (employee view)
* `admin@example.test` (administration)

and the passphrase from step 3.

### 5. Make it permanent

So it starts on boot and restarts if it crashes:

```bash
sudo useradd --system --home /opt/omada-scheduler --shell /usr/sbin/nologin omada
sudo chown -R omada:omada /opt/omada-scheduler
sudo cp /opt/omada-scheduler/deploy/omada-scheduler.service /etc/systemd/system/
sudo systemctl daemon-reload
sudo systemctl enable --now omada-scheduler
systemctl status omada-scheduler           # should say active (running)
journalctl -u omada-scheduler -f           # the log (Ctrl+C to leave)
```

Done. The site is live with sample data.

---

## Real Google sign-in (when you are ready)

1. Google Cloud Console > Credentials > **Create credentials > OAuth client ID > Web application**. Under **Authorized JavaScript origins** add `https://your-hostname` (no path, no trailing slash). No redirect URI is needed. Copy the client ID.
2. In `backend/.env`: `GOOGLE_CLIENT_ID=...apps.googleusercontent.com` and `BOOTSTRAP_ADMIN_EMAIL=the-google-account-you-sign-in-with`.
3. `sudo systemctl restart omada-scheduler`, open the site and click **Sign in with Google**.
4. Add people: Manager dashboard > **Employees** (their email must be their Google email), then Admin dashboard > **Accounts > Authorize**.
5. For marking, either publish the Google consent screen or add the marker as a test user, and keep the demo sign-in as a fallback. Details: `docs/02-HOSTING-AND-GOOGLE-SIGN-IN.md`.

## Changing the pages

The pages in `frontend/` are served straight from disk. Edit an HTML, CSS or JS file and refresh the browser (hard refresh with Ctrl+Shift+R if you do not see the change). No restart needed. Changes to anything in `backend/` need `sudo systemctl restart omada-scheduler`.

| File | What it is |
|---|---|
| `index.html`, `js/login.js` | Sign-in page |
| `employee.html`, `js/employee.js` | Employee: calendar, availability, profile, ask about hours |
| `manager.html`, `js/manager.js` | Manager: schedule and assignments, bookings with email autofill, employees, certifications, reviews, reports, lists |
| `admin.html`, `js/admin.js` | Administrator: accounts and roles, email log |
| `js/common.js` | Helpers shared by every page (API calls, tables, tabs) |
| `css/style.css` | All the styling. Colours are the variables at the top. |

The calendar library (FullCalendar) loads from a CDN, so visitors' browsers need internet access.

## If something already serves your web address

If another web server (nginx, Caddy, Apache) already serves a site on the tunnel, you have two choices:

* **Easiest:** point the tunnel route at `http://localhost:8000` as in step 4, so the backend serves everything.
* **Keep your web server:** copy the `frontend/` files to its web root and forward everything under `/api/` to `http://127.0.0.1:8000`. The pages and `/api` must be on the **same hostname**, because the login cookie is only sent to that hostname. `deploy/nginx-omada.conf` has an nginx example.

## Troubleshooting

| What you see | What to do |
|---|---|
| Cloudflare error 502 or 1033 on the site | The backend is not running or the route points at the wrong port. Run `curl http://127.0.0.1:8000/api/health` on the server. |
| `{"status":"database unavailable"}` | Wrong password in `DATABASE_URL`, or PostgreSQL is not running (`systemctl status postgresql`). |
| `password authentication failed for user "omada_app"` in the log | The password in `backend/.env` is not the one you gave the install script. Reset it: `sudo -u postgres psql -c "ALTER ROLE omada_app WITH PASSWORD 'new'"` and update `.env`. |
| Sign-in seems to work but you land back on the sign-in page | The cookie is not being kept. With `COOKIE_SECURE=true` it only works over https. Use your tunnel address, not `http://server-ip:8000`. For plain http testing set `COOKIE_SECURE=false`. |
| No demo sign-in form | `DEMO_LOGIN_ENABLED=true` and a non-empty `DEMO_LOGIN_PASSPHRASE` are both needed. Restart the service after editing `.env`. |
| Page loads but the calendar is empty or missing | The browser could not load FullCalendar from the CDN, or the data really is empty for that week (the sample data is centred on late November 2026). |
| "Google sign-in is not set up on this server" | `GOOGLE_CLIENT_ID` is empty in `backend/.env`. |
| Google sign-in button errors with "origin_mismatch" | The address in the browser is not listed under Authorized JavaScript origins for the client ID. |
| The AI says it is not set up | No `ANTHROPIC_API_KEY` in `.env`. Everything else works without it. |
| Dates in the sample data look old | Regenerate: `python3 scripts/generate_seed.py --today YYYY-MM-DD`, then recreate the database (drop it and run step 2 again). |

## Starting over

```bash
sudo -u postgres psql -c "DROP DATABASE omada WITH (FORCE)"     # deletes all data
./scripts/install_db_native.sh                                   # with APP_DB_PASSWORD set again
sudo systemctl restart omada-scheduler
```
