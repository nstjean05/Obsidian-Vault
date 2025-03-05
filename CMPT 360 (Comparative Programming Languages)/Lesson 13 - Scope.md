**13. _Static and Dynamic Scope,_ _Lifetime_**

**[3]** a. What is the difference between dynamic type binding and implicit heap binding?
- Dynamic type binding refers to how in some languages (e.g. Python, Ruby), a type is not necessarily declared for a variable. The information held by the variable can change throughout the program. On the other hand, implicit heap binding is used to describe how memory is automatically chosen for those objects and variables.

**[3]** b. Explain the difference between scope and lifetime using an example from your favourite language.
- Scope is how many degrees of separation a variable can have from where it is created. Lifetime, however, is the time at which that variable is bound to a cell. For instance, a variable in Java may be created and used in one function, but cannot be referenced from another because it has too little scope. That same variable is automatically allocated a location in memory when it is initialized, and de-allocated at program termination (the time between these two points is its lifetime).
https://www.inf.unibz.it/~calvanese/teaching/04-05-ip/lecture-notes/uni03/node17.html

**[3]** c. Explain the difference between static and dynamic scope using an example from your favourite language.
- When using static scoping, the reference to a variable is set by where the variable sits in the program. In dynamic scoping, on the other hand, a variable is referred to by where it lies on the function call stack (at runtime). In the case of Java, static scoping is used, and dynamic scoping is completely unavailable. One example of dynamic scoping could be if you referred to a global variable *x*, and had a function f() which always returned it. Another function g() could return f(), and would end up returning the variable *x* from before.

https://www.geeksforgeeks.org/static-and-dynamic-scoping/

