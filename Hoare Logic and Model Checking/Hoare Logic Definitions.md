## Lecture 1

##### Partial Correctness Triple
{P} C {Q}: P is a pre-condition, C is a program, Q is a post-condition.


##### State Predicate
P and Q define **state predicates**, they "predicate" over what what should hold before and after the execution of the program.
 
##### Assertion
Assertion language needed for defining a hoare logic.


##### Auxilliary Variables
AKA 'ghost' variables, introduced as constant user inputs. These are immutable from the POV of the program.

##### Program Variables
Introduced as variables within the program.

##### Inference Rule Schemas
The set of rules used for deriving consequences from premises of Hoare triples.

##### Consequence
Allows for the strengthing of preconditions and weakening of postconditions.

## Lecture 2

##### Proof outline
Derivations in Hoare logic more readline when given as proof outline (more akin to vertical layout of code) as opposed to proof trees (like in types).

##### Loop Invariant
A set of conditions that must hold before, during, and after the execution of a while loop.

##### Verification
The process used to determine whether a program is valid.

## Lecture 3

##### Dynamic Semantics
Explains the dynamic execution of [[Hoare Logic Definitions#Partial Correctness Triple]]. Uses the small-step operational semantics used in IB semantics.


##### Safety
It will always terminate with skip (Type safety from IB Semantics).

##### Determinacy
There is only one direction the program can go in at all times.

##### Assertations
used to describe and reason about the states of a program.

##### Soundness 
Any triple derivable using the syntactic proof system holds semantically.


The formal semantics of programming: chapters 6-7


##### Completness
The converse of soundness:

##### Relative Completeness
Hoare logic is **relatively complete** in comparison to arithmetic.

##### Decidability
The property of a language that allows us to effectively determine whether a given program will be valid without having to run it.

##### Stack
A total function describin the current value of every program variable.

## Lecture 4

##### Separation Logic
Allows us to separate the state predicates into disjoint sets. Permits cocurrent dynamic semantics.

##### Heap
Stores the current values of allocated locations. It uses locations, similar to the concept of addresses, whereas the stack maps program variables to values.

##### Failure
If the given location is not currently allocated, failure happens.

##### Free Variables
The variables used in a program.

##### Constancy
Assertions that don't refer to program vars modified by a command are automatically preserved during execution.

##### Modularity
Allows us to access only the part of the state that is needed.

##### Aliasing
When syntactially different expressions refer to the same location; can happen with Hoare logic.

##### Ownership
A separation logic assertation asserts ownership of resources.

##### Resources
The part of the heap owned by a given state predicate.

##### Framing
Using the separating conjunction to express separation (similar to the rule of constancy). 

This is the core behind the concept of modularity in separation logic; it allows us to prove something about a program C whilst having a larger context.

##### Free Variables vs Mod

Mod defines a syntactic overapproximates of the set of Program variables that might be modified by a command C.

Free variables on the other hand define the same thing but in relation to the pre-condition or the post-condition. I think.


## Lecture 5

##### Pure
Assertion is pure when it doesn't talk about the heap.

##### ADTs
Abstract data types, like lists.

##### Representation Predicates
State predicates used to represent [[Hoare Logic Definitions#ADTs]] like lists.

##### Partial Lists
Part of a list.


## Lecture 6


##### Total Correctness
Accounts for termination of Hoare triples.

##### Loop variants
A decreasing variant that is not true at the end of a while loop's progression, but holds before and during the loop's progression.