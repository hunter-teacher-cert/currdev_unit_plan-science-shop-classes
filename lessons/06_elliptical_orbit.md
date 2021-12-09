# Aim: How do we recreate an elliptical orbit?
## Objectives
 * Use basic commands to draw an ellipse
 * Use a stopwatch to measure speeds at aphelion and perihelion
 * Compare the speeds at aphelion and perihelion

## NYS COMPUTER SCIENCE AND DIGITAL FLUENCY LEARNING STANDARDS
 * **9-12.IC.7** Investigate the use of computer science in multiple fields.
 * **9-12.CT.4** Implement a program using a combination of student-defined and
   third-party functions to  organize the computation.

## Warm Up
Time: 5 minutes  
Teacher asks students to write a setup for creating three turtles.

## Lesson Content
Time: 20 minutes

Students will code along with teacher who explains the thought process that goes
into creating an elliptical orbit during the code-along.

```
; Code for drawing an elliptical orbit
to setup
  clear-all
  create-turtles 3 [
    set shape "butterfly"
    set size 2
    set color pink
    set heading 0
    setxy 9 0
    pen-up
  ]
  ask turtle 0 [
    set color yellow
  ]
  ask turtle 1 [
    setxy 0 0
  ]
  ask turtle 2 [
    setxy 9 0
    pen-down
    set color red
  ]
  draw-grid
end

to go
  ;repeat 1500 [
    ask turtle 2 [
      forward .153 / sqrt (distance turtle 1)  ; this is v, a result of Newton’s law of gravity Fg
      left 0.5 / sqrt (distance turtle 1)      ; this is ⍵, angular speed, also a result of Fg
  ;  ]
  ]
end

to draw-grid
    ask patches [
    sprout 1 [
      set heading 0
      forward 0.5
      right 90
      set color white
      pen-down
      repeat 4 [ forward 0.5 right 90 forward 0.5 ]
      die
    ]
  ]
  ask turtle 0 [
    setxy min-pxcor 5
    pen-down
    set heading 90
    forward  (max-pxcor - min-pxcor)
    pen-up
    setxy min-pxcor -5
    pen-down
    forward ( max-pxcor - min-pxcor)
    pen-up
    setxy max-pxcor max-pycor
  ]
end

```

Students are asked to set the max px-cor to 30 and max py-cor to 30 in the settings.

## Lesson Activity  
Time: 15 minutes

The students are asked to measure the time interval when Earth is
orbiting closer to the Sun (perihelion). They start the stopwatch
when the Earth crosses the first yellow line and travels for 10 units
of distance, and stop the clock when the Earth reaches the second yellow line.
Then, students will measure the time interval when the Earth is orbiting
farthest away from the Sun (aphelion). They start the stopwatch
when the Earth crosses the first yellow line and travels for 10 units
moving towards the bottom of the screen, and stop the clock when the
Earth reaches the second yellow line.

After measuring the time intervals for aphelion and perihelion, compare
the speed of the Earth at aphelion and perihelion. Speed is calculated by
dividing distance traveled by time interval.


## Closing  
Time: 5 minutes  

Students explain what they discovered in this activity. From their model building
and measurement/analysis, they should be able to explain to others that
Earth travels faster when it is closer to the Sun (perihelion) and
Earth moves slower when it is farthest away from the Sun (aphelion).

## Explanation
The lesson is designed for students who will write program in NetLogo to produce
virtual models of Earth Science.
