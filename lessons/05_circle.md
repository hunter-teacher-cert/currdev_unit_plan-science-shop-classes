# Aim: How do we construct a circle?
## Objectives
 * Use basic commands to draw an arc
 * Use simple instruction to draw a generic circle
 * Use mathematical formula to draw a circle with specfic size.

## NYS COMPUTER SCIENCE AND DIGITAL FLUENCY LEARNING STANDARDS
 * **9-12.IC.7** Investigate the use of computer science in multiple fields.
 * **9-12.CT.4** Implement a program using a combination of student-defined and
   third-party functions to  organize the computation.

## Warm Up
Time: 5 minutes  
Teacher asks students to draw an arc in NetLogo.

## Lesson Content
Time: 20 minutes

Students get a hint for drawing an arc by tracing a pen a little forward
and a little to the right.

```
globals [length-side]

to setup
  clear-all
  create-turtles 1 [
    set shape "turtle"
    set color sky
    set size 2
    set heading 0
    setxy -12 0
    pen-down
  ]
  set length-side .5
end

to go
  ask turtle 0 [
    circle
  ]
end

to circle
  repeat 80 [
    forward 0.1
    right 0.5
  ]
end
```

Students are asked to draw a circle. At first their circles are not complete,
but eventually they realize they need 360 degrees for a circle if they turn
1 degree for each iteration.

```
globals [radius]

to setup
  clear-all
  create-turtles 1 [
    set shape "turtle"
    set color sky
    set size 2
    set heading 0
    setxy -12 0
    pen-down
  ]
  set radius 5
end

to go
  ask turtle 0 [
    circle
  ]
end

to circle
  repeat 360 [
    forward 0.1
    right 1
  ]
end
```

## Lesson Activity  
Time: 15 minutes

The students are asked to try to draw a circle of exactly the size they want.
They may eventually realize they need to use the circumference formula:
C = 2 * pi * r, where r = radius. If a turtle turns 1 degree per iteration,
then the distance traveled during an iteration will be (1/360) C or 2 * pi * r / 360.

```
globals [radius]

to setup
  clear-all
  create-turtles 1 [
    set shape "turtle"
    set color sky
    set size 2
    set heading 0
  ]

end

to go
  set radius 15
  ask turtle 0 [
    pen-up
    setxy (-1 * radius) 0
    pen-down
    circle
  ]
end

to circle
  repeat 360 [
    forward 2 * pi * radius / 360
    right 1
  ]
end
```


## Closing  
Time: 5 minutes  

Students explain their codes to students in other groups.
Some students explain their circle program to students in the class.
As an exercise, students can incorporate slider variable to adjust
the radius of their circles.   

## Explanation
The lesson is designed for students who will write program in NetLogo to produce
virtual models of Earth Science.
