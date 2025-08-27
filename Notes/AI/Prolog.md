[[lecture14.pdf]]
- Unique-names assumption: Every constant symbol refers to a distinct object
- Closed world assumption: Atomic sentences not known are false
- Domain closure assumption: A model contains no more objects than the constant symbols
- Uses depth-first backward-chaining search without checking for infinite recursion
	- Some programs will fail to terminate
![[Screenshot 2025-03-04 at 9.02.42 AM.png]]
###### Queries 
- After loading facts and rules, user poses queries
- If query contains no variables, it is a binary question and prolog responds with true or false
- If query contains variables, prolog prints valid variable mappings/bindings (if any) one at a time
	- Enter ; to get next binding