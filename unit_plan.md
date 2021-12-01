# UNIT PLAN: Constructing Computer Animations in Earth Science

by TEAM MEMBERS

Jovani Cardenas, Peter Tsun

-----

## General Overview
(include here description of unit, what class(es) it fits into, when...)

This unit provides students with introduction to key ideas in computer science and skills in logo programming language
in Earth Science classes during the astronomy unit.

---

## Motivation for Unit
(why have you decided to make this?)

For many students, computers are thought of as consumer electronics, not as a medium for putting their own ideas into reality.
Students typically do not get to have experience at school or at home to realize that they can actually create useful products themselves.
This unit is created to make a small dent in helping children think of themselves as creative thinkers who can turn their ideas into reality.

---

## Standards Referenced
(select one of the standards sets reviewed in class (CSTA, NY, MA, RI), include a link and a brief explanation as to why you selected that set)
9-12.CT.1 Create a simple digital model that makes predictions of outcomes.
In these Earth Science computer programming lessons, students will learn how
to design and implement simple programs that recreate observations of planetary orbits.
These simple models are attempts to predict how planets will move in the future.

---

## Tools Used
(include programming language(s), specific programs/environments, and other tools (digital or otherwise) if necessary)

NetLogo

---

## Resources
(include any links/books/readings to be used during this unit)

https://mindstorms.media.mit.edu/

---

## Lessons
Total lenght: 2 Weeks (realistically, an ES teacher would try to get it done in 7 or 8 days to keep up with NYS ES curriculum)

(list each lesson with main topic(s))
- day 1. lesson on iteration (loop)
- day 2. lesson on procedure
- day 3. lesson on variable, passing by parameters to procedures
- day 4. lesson on recursion and conditional
- day 5. lesson on constructing a circle
- day 6. lesson on drawing a graph paper for plotting experimentall data - reinforcement on recursion
- day 7. lesson on constructing an elliptical orbit of a planet around the sun
- day 8. lesson on drainage pattern with GIS 3D NetLogo modeling  
leave extra 2 days for students to have more time to explore certain topics that they have yet to understand.


---

## Assesments
(list summative and/or formative assessments used)

---



Just because teachers tell students the facts that will be tested on regents exams, students may not internalize the information as well as if they can build a computer model and see for themselves that the planets do indeed move faster at perihelion and move slower at aphelion.
After students can draw circles of certain sizes, teachers can do live coding with students to
apply Newton’s law of Gravitation (F = G M m /r<sup>2</sup>) to draw an ellipse. Here is the code on the following page:

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
        setxy max-pxcor max-pycor
    ]
    ask turtle 1 [
        setxy 2 0
    ]
    ask turtle 2 [
        setxy 10 0
        pen-down
        set color red
    ]
    end

    to go
        repeat 1500 [
            ask turtle 2 [
            forward 0.23 / sqrt (distance turtle 1)  ; this is v, a result of Newton’s law of gravity Fg
            left 1 / sqrt (distance turtle 1)            ; this is ⍵, angular speed, also a result of Fg
        ]
    ]
    end

A follow-up to the first attempt is to calculate the eccentricity of the orbit as shown on next page:










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
        setxy max-pxcor max-pycor
    ]
        ask turtle 1 [
        setxy 1 0
    ]
        ask turtle 2 [
        setxy 10 0
        pen-down
        set color red
    ]
        end

    to go
        let max-tx 10
        let min-tx 10
        let max-ty 0
        let min-ty 0

        repeat 1500 [
            ask turtle 2 [
                forward .153 / sqrt (distance turtle 1)
                if (([xcor] of turtle 2) > max-tx) [
                    set max-tx ([xcor] of turtle 2)
                ]
                if (([ycor] of turtle 2) > max-ty) [
                    set max-ty ([ycor] of turtle 2)
                ]
                if (([xcor] of turtle 2) < min-tx) [
                    set min-tx ([xcor] of turtle 2)
                ]
                if (([ycor] of turtle 2) < min-ty) [
                    set min-ty ([ycor] of turtle 2)
                ]
                left 1 / sqrt (distance turtle 1)
                ]
            ]

        output-type "ellipse max x value = " output-print max-tx
        output-type "ellipse min x value = " output-print min-tx
        output-type "ellipse max y value = " output-print max-ty
        output-type "ellipse min y value = " output-print min-ty
        output-type "ellipse x-axis length = " output-print (max-tx - min-tx)
        output-type "ellipse y-axis length = " output-print (max-ty - min-ty)

        ask turtle 0 [
            setxy min-tx + (10 - 2)  0
        ]
        let foci-distance 0
        ask turtle 1 [
            set foci-distance distance turtle 0
        ]
        let eccentricity foci-distance / (max-tx - min-tx)
        output-type "eccentricity = " output-print eccentricity
        end

;https://www.youtube.com/watch?v=czoPyHx3RZM

