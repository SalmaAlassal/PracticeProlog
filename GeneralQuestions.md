## Question 1

- Insert a list into another list at a given position.
- Sample goal: insertAt([1,2], [3,4], 1, L).
- L=[1,3,4,2]

```prolog
Domains
    lst = Integer*
Predicates
    nondeterm append(lst, lst, lst).
    nondeterm insertAt(lst, lst, Integer, lst)
Clauses
   append([], L, L).
   append([H|T], L2, [H|T1]):- append(T, L2, T1).
   
   insertAt(L1, L2, 0, R):- append(L2, L1, R).
   insertAt([H|T], L2, X, [H|T1]):- NX = X - 1, insertAt(T, L2, NX, T1).
Goal
   insertAt([1,2], [3,4], 1, L).
```