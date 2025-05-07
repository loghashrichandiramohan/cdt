1.UNIFICATION 
% unify/2 takes two terms and unifies them if possible 
unify(X, X) :- var(X), !. 
unify(X, Y) :- var(X), !, X = Y. 
unify(X, Y) :- var(Y), !, Y = X. 
unify(X, Y) :- compound(X), compound(Y), !, 
X =.. [F|Xs], Y =.. [F|Ys], 
unify_list(Xs, Ys). 
% unify_list/2 unifies two lists of terms 
unify_list([], []). 
unify_list([X|Xs], [Y|Ys]) :- unify(X, Y), unify_list(Xs, Ys). 
 
2.RESOLUTION 
% resolution/2 resolves a goal with a list of clauses 
resolution(Goal, Clauses) :- 
member(Clause, Clauses), 
resolve(Goal, Clause, Resolvent), 
(member([], Resolvent) -> writeln('Goal is true.'); resolution(Resolvent, Clauses)). 
% resolve/3 resolves two clauses and produces the resolvent 
resolve(Goal, Clause, Resolvent) :- 
select(Literal, Goal, RestGoal), 
select(not(Literal), Clause, RestClause), 
append(RestGoal, RestClause, Resolvent).
