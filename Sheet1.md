## Question 1

- Write a program that increments the elements of a list.
- Sample goal: increment([1,5,7,2] , L). 
- L=[2,6,8,3]

```prolog
Domains
    lst = Integer*
Predicates
    increment(lst, lst)
Clauses
    increment([], []).
    increment([H|T], [H1|T1]) :- H1 = H + 1, increment(T, T1).
Goal
    increment([1,5,7,2], L).
```

## Question 2

- Implement insertion into a sorted list (the result is sorted as well)
- Sample goal: InsertSorted (5, [1,3,6,7,10,45] , L )
- L=[1,3,5,6,7,10,45]

```prolog
Domains
    lst = Integer*
Predicates
     insertSorted(Integer, lst, lst)
Clauses
    insertSorted(X, [], [X]).
    insertSorted(X, [H|T], [X,H|T]):- X <= H,!.
    insertSorted(X, [H|T], [H|T1]):- insertSorted(X, T, T1).
Goal
    insertSorted(5, [1,3,6,7,10,45], L).
```

## Question 3

- Implement list difference.
- Sample goal: difference ([a,b,c,d,e,f,g,h] , [a,g,h], L).
- L=[b,c,d,e,f]

```prolog
Domains
    lst = Symbol*
Predicates
    nondeterm difference(lst, lst, lst)
    nondeterm member(Symbol, lst).
Clauses
   member(X, [X|_]).
   member(X, [_|T]):- member(X, T).

   difference([], _,[]).
   difference([H|T], L2, L):- member(H, L2), difference(T, L2, L).
   difference([H|T], L2, [H|T1]):- not(member(H, L2)), difference(T, L2, T1). 
  
Goal
    difference([a,b,c,d,e,f,g,h], [a,g,h], L).
```

## Question 4

- Write a program that counts the number of vowels in a list.
- Sample goal: num_vowels ([o,r,a,n,g,e] , Num).
- Num=3

```prolog
Domains
    lst = Symbol*
Predicates
    nondeterm num_vowels(lst, Integer)
    nondeterm member(Symbol, lst).
Clauses
    member(X, [X|_]).
    member(X, [_|T]):- member(X, T).
    
    num_vowels([], 0).
    num_vowels([H|T], N):- member(H, [a,e,i,o,u]), num_vowels(T, N1), N = N1 + 1.
    num_vowels([H|T], N):- not(member(H, [a,e,i,o,u])), num_vowels(T, N).
Goal
    num_vowels([o,r,a,n,g,e], N).
```