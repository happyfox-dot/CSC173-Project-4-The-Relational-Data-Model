# CSC173-Project-4-The-Relational-Data-Model
CSC173: Project 4 The Relational Data Model_ code_material

#get help from happyfox123@qq.com 

In this project you will gain experience with databases and relational algebra by implementing your own database system. We will build on the presentation (and code) in the
textbook. You must follow the formal model, even though your database will be very
small. If you do it properly, it would also work for a large database.
Part 1 (40%)
1. Implement a database containing the relations (tables) shown in Appendix A. This
database is similar to the “Registrar” database from FOCS Figs. 8.1 and 8.2 (also
seen in class). Use the method described in Section 8.2 in the section “Representing Relations” and elaborated in Section 8.4 “Primary Storage Structures for
Relations.” Use hashtables to store the sets of tuples, as seen in class and in the
textbook.
2. Implement the basic single-relation insert, delete, and lookup operations as functions. Using the implementation described in the textbook, you will need separate
functions for each relation (e.g., insert CSG for the Registrar database CSG table). You should support leaving some attributes unspecified for delete and lookup
(denoted with “*” in the textbook, perhaps something else in your code).
3. Use your insert method to populate the tables with the data in Appendix A. Print
the contents of the database clearly after loading the data.
4. Finally, demonstrate all three operations by performing the following operations,
which are similar to those shown in FOCS Example 8.2 (p. 409). Print what operation is being performed, for lookup print the results, and for insert and delete, print
the affected table after the operation.
(a) lookup(⟨“Americans”, 61367, 99⟩, Team-PlayerId-Number)
(b) lookup(⟨“Crunch”, 51213, ∗⟩, Team-PlayerId-Number)
(c) lookup(⟨“Americans”, “Toronto”⟩, Team-City)
(d) delete(⟨“Redwings”, “Maple Leafs”, “6 Jan 2023”⟩, GameId-HomeTeam-AwayTeam-Date)
(e) delete(⟨“Redwings”, “Crunch”, ∗⟩, GameId-HomeTeam-AwayTeam-Date)
(f) delete(⟨“Americans”, ∗, ∗⟩, GameId-HomeTeam-AwayTeam-Date)
(g) insert(⟨“Ice Pilots”, “Pensacola”⟩, Team-City)
(h) insert(⟨“Crunch”, “Syracuse”⟩, Team-City)
1
Part 2 (30%)
For this part, use the database with all the tuples from Appendix A (that is, before any
deletions or insertions). I suggest that you have a function that prepares the database
(creates the relations and inserts the tuples). Then use that function twice, once for Part
1 and once for Part 2.
1. Write a function to answer the query “What number did Name wear when playing for Team?” similar to FOCS Section 8.6 “Navigation Among Relations.” The
code for your function must look like the pseudocode in FOCS Fig. 8.8 or 8.9. (I
recommend using the pseudocode as comments in your code.)
Demonstrate this functionality with a “Read-Eval-Print Loop” or “REPL”: ask the
user for the query parameters (Name and Team), not an entire English sentence),
perform the query, print the results informatively, until the user says to stop.
2. Write a function to answer the query “How many goals did Name score on Date?”
The code for your function must follow the model shown in FOCS Fig. 8.10 (described starting on p. 426), also seen in class.
Demonstrate this functionality with a REPL also.
Make sure it is clear what query is being used, what values the program is asking for,
and what are the results of the query. It is your responsibility to makie it clear for us.
Part 3 (30%)
Implement the Relational Algebra operations as described in FOCS Section 8.8. Demonstrate this by evaluating the following Relational Algebra expressions, which are similar
to those in FOCS Examples 8.12–8.15. Print an informative description of the expression and print the table that is the result of evaluating it.
1. Selection: σPlayerId=51213(TPN )
2. Projection: πTeam(σPlayerId=51213(TPN ))
3. Join: GHVD ▷◁ GPG
4. All of the above: πPlayerId,Goals(σDate=“8Jan2023′′(GHVD ▷◁ GPG))
2
If you follow the implementation in the textbook, you will probably need a different function for each different set of arguments to the operator (e.g., select TPN PlayerId,
join GHVD GPG, . . . ). You only need to implement the ones that you need for the examples listed above.
Note that some of the Relational Algebra operations create a relation with a different
schema from that of their operands. (You should know which operations do this. . . )
But if tuples are implemented using structs, how do you create instances of these new
“on-the-fly” relations?
The answer is that you should solve the problem yourself by hand so that you know the
schemas needed by your examples. Then add appropriate structure definitions to your
program to allow you to code up the required examples using your implementations of
the Relational Algebra operators. This is one of many differences between what you
need to do for this project and a real database framework.
