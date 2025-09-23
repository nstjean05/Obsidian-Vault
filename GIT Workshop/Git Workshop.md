## What is Git useful for?
- Version control systems are necessary for all but the smallest programming projects.
- Highly useful for later courses.
## Why VCS?
- Without a VCS, you end up with a lot of documents with slightly different draft names.
	- Stored across computers.
	- Zombie code commented out everywhere.
	- Send code files over email.
- With VCS, we can do a lot more complicated things.
	- Different versions/branches simultaneously.
	- Test different branches.
	- Code paths can be merged together.
	- See differences between files side by side.
## Git Basics
- Create an folder in VSCode
- Use `git init` in terminal to initialize a Git repository.
- Use `git add main.py` (add file) or `git add .` (add all changes)
- Can add a descriptor with each new snapshot of the program to see the graph over time.
-  Use `git checkout <branch-name>` to switch between the branch you're working in.
- Use `git merge <branch-name>` to unite branches.