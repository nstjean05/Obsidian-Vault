#incomplete 
### ADTs in Libraries
##### Typical Rules (may vary)
- The order of imports to a program unit determines one or more orders of compilation for the library modules (when they need to be (re)compiled)
	- This order may be different for the definition/interface/header parts and implementation/code parts.
	- Circular imports may mean there is no correct order.
- If the module/package/code body itself has code, it is executed in the order or import- i.e. this produces a link dependency.
#### Ada
- Allowed the interface and implementation parts to be...
	- Compiled as a single unit (i.e.. in one file)
	- Separately by specifying *separate*
	- Individual procedures could be marked *separate* and separately compiled as sub-units of the main package.
### Possible Issues of Separate ADT Compilation
- With few exceptions modules are not themselves types.
- When modules export types, the type det