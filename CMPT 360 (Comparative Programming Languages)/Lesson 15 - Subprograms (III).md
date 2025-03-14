### What can a function return?
- Usually any built-in type can be a return type.
- The type matching rule for a return value is *usually* the same as for assignment.
- *Some* languages prohibit structured types, or even all user defined types from being return types, though C allows pointers as returns
- Even if structured types are allowed, they must be names, not anonymous.
	- `PROCEDURE DoIT(VAR p:REAL):ARRAY10 OF REAL`
- In most languages, a pure function (i.e. with a return value) should *not* also have reference parameters that are writable. This is a side-effect that as a previous example showed, could cause such things as commutivity to fail