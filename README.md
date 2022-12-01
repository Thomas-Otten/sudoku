How to Create a Sudoku Solver Using the DLV Programming Language

What is DLV?
DLV is a deductive database system based on disjunctive logic programming. An easier 
way the phrase it is opposed to Java, C++, and python where you create a set of 
instructions for the computer to execute. In DLV all you must do is tell the computer 
what you do not want, and the computer will generate all possible "worlds" that 
meet your criteria. We are going to use this language to solve any sudoku puzzle given you 
provide it the locations of the pre-placed numbers.

Basic Overview of DLV

•	Facts
  o	You can create facts that must exist in the "world" that DLV generates.
  o	You create a fact in dlv by stating the fact as is in code, such as "joke." or if you want the inverse which is no joke "-joke."
•	Rules
  o	Rules are the rules that the DLV program must follow as well.
  o	A rule is represented with the name of the subject variable followed by a “:-“ then followed by the condition.
  o	An example of a rule is "laugh :- joke." this is the equivalent of saying in the program, "if there is joke, then laugh".
•	Constrictions
  o	Constrictions outline what combinations of facts are not allowed in the "world" that DLV generates
  o	A constriction is represented with a “:-“ at the start of the line.
  o	An example of a constriction would be ":- male(x), female(x)."
    	This example states that the individual "x" cannot be both a male and female.
•	Other Bits and Bobs
  o	All statements in DLV end with a “.” Opposed to the commonly used “;” to signify the end of a line
  o	Comments are lines of code that aren’t a part of the program, think of them as notes for yourself while programming.
  o	When programming in DLV, it does not matter the order in which statements are typed, thus why the figures are not in order.
  
  Materials Needed
•	A computer capable of running basic programs.
•	A text editor installed on previously mentioned computer.
  o	In my example, I will be using Microsoft Visual Studio Code as my text editor, 
    but you can use whatever you are most familiar with.
•	A download of DLV on the previously mentioned computer.

Solving a Sudoku in DLV	
1.	Creating the variables
  •	In the sudoku solver, all the facts that we need to complete the sudoku are the individual 81 squares that make up a sudoku board, 
    you can see how they are created in (figure 1).
  •	Additionally, we also need facts that give each of the 81 squares a value from 1 to 9.
  
2.	Generating all possible combinations of sudoku boards.
  •	we will create a "place" fact that has a row and column with an assigned value.
  •	To ensure that each place has only one value, we must use the logic operator "v" to indicate "or".
    o	An example of this would be "place(R, C, 1) v place(R, C, 2) :- row(R), col(C)", 
      this line says logically "place(R, C) can have a value of 1 or 2 but not both or neither.

3.	Setting Constrictions
  •	One rule to Sudoku is that you cannot have duplicate numbers in either rows or columns, to enforce that rule we set constrictions.
    o	We set the constriction: :- place(R, C1, VAL), place(R, C2, VAL), C1 != C2. (figure 3)
      	This line says logically "A place in the same row but different column cannot have the same value."
      	We will repeat this step but for the column.
      
4.	Enforce the rule of the small 3 x 3 grids that are in a sudoku.
  •	Using math operators, create 9 regions (figure 4).
    o	We create a region(REG, N) variable where the first value is what region the is being specified then the second variable is what number is in the region.
  •	set a constriction to prevent duplicate values in each region (figure 4).
    o	The constriction of :- not region(REG, VAL), val(VAL), region_set(REG). 
      	This specifies that there cannot be a region that does not have a unique number value in one of the 9 regions.
      
5.	Fill in the places of the sudoku that you want to solve
  •	You do this by creating place facts such as "place(1,1,4)", this indicates that row 1, column, 1 has a value of 4 (figure 5).
    o	Continue this for every space that is prefilled when starting the sudoku puzzle.

6.	Run the code and be impressed
•	If you applied all the code correctly and followed the instructions, your code should look like figure 6
  o	In order to run the program on your command line (to open a command line on windows, open your windows search bar and type “cmd”)
    	On the command line type “DLV -silent (name of the file). In this instance it was named sudoku.dlv so it should look like this: $ DLV -silent sudoku.dlv
•	once you run the code, you will notice that the program outputted all possible ways to solve the sudoku that you supplied it.
•	However, the output will be displayed as place(row, column, value) in a long list of all 81 places.

Summary
Despite how confusing it may be at first, DLV is a logic dependent language that 
requires some hard thinking but nothing too taxing except for maybe the math logic. Once 
you understand how the language works and its uses, it can be used for a multitude 
of tasks such has setting up a schedule or solving logic puzzles.
