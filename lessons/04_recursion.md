# Aim: How do we use recursion?
## Objectives
 * Use procedure's parameters for recursion
 * Use conditionals to end recursion
 * Modify various parameters to create different recursion patterns.

## NYS COMPUTER SCIENCE AND DIGITAL FLUENCY LEARNING STANDARDS
 * **9-12.IC.7** Investigate the use of computer science in multiple fields.
 * **9-12.CT.4** Implement a program using a combination of student-defined and
 third-party functions to  organize the computation.
 
## Warm Up
Time: 5 minutes  
Teacher asks students to type an example of recursion into NetLogo.

## Lesson Content
Time: 20 minutes  

This computer program is unique because the program calls a copy
of a procedure, and the procedure calls a copy of the same procedure.
This concept of a procedure calling a copy of itself is called recursion.
Normally people tend to avoid recursion, because recursion seems like
a never-ending invoking of a copy of the same procedure.

However, this program will definitely end because the starting length is small.
Every time a copy of the procedure is called, a slightly larger length is fed into
the procedure. When the length is greater some threshold, the recursive call to the procedure will not be made. This results in the stopping of continued recursive calls.


## Lesson Activity  
Time: 15 minutes  

Students are invited to change various parameters in their recursion program, and discover the effects of their changes.

They can try to integrate the globals variable to give significance to their parameters. Students may even try to add GUI slider to control global variable from the graphical interface.

```
globals [length-side]

to setup
  clear-all
  create-turtles 1 [
    set shape "turtle"
    set color sky
    set size 2
    set heading 90
    pen-down
  ]
  set length-side .5
end

to go
  ask turtle 0 [
    spiral length-side
  ]
end

to spiral [length-spiral]
  forward length-spiral + 0.3
  right 90
  if (length-spiral < 25) [
    spiral (length-spiral + 0.5)
  ]
end
```


## Closing  
Time: 5 minutes  

Students will explain how a recursive call is made and terminated. Every student is invited to share their recursive graphical patterns.

## Explanation
The lesson is designed for students who will write program in NetLogo to produce
virtual models of Earth Science.
