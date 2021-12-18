# UNIT PLAN: Constructing Computer Animations in Earth Science

by TEAM MEMBERS

Jovani Cardenas, Peter Tsun

-----

## General Overview
(include here description of unit, what class(es) it fits into, when...)

This unit provides students with introduction to key ideas in computer science and skills in logo programming language
in Earth Science classes during the astronomy unit. NetLogo allows students to explore coding in a more visually appealing manner. It also hosts a vast library of models such as a climate change model in which it can be used to explore its variables, and later explore its limitations to predict climate change.

---

## Motivation for Unit
(why have you decided to make this?)

For many students, computers are thought of as consumer electronics, not as a medium for putting their own ideas into reality.
Students typically do not get to have experience at school or at home to realize that they can actually create useful products themselves.
This unit is created to make a small dent in helping children think of themselves as creative thinkers who can turn their ideas into reality. It also serves to demonstrate the benefits and limitations of real-world tools such as computer simulations.

---

## Standards Referenced
Standards utilized from NYSED 9-12 Computer Science Standards (http://www.nysed.gov/common/nysed/files/programs/curriculum-instruction/computer-science-digital-fluency-standards-9-12.pdf)

- 9-12.CT.1 Create a simple digital model that makes predictions of outcomes. 
- 9-12.CT.2 Collect and evaluate data from multiple sources for use in a computational artifact.
- 9-12.CT.4 Implement a program using a combination of student-defined and third-party functions to organize the computation.
- 9-12.CT.8 Develop a program that effectively uses control structures in order to create a computer program for practical intent
- 9-12.IC.1 Evaluate the impact of computing technologies on equity, access, and influence in a global society.
- 9-12.IC.3 Debate issues of ethics related to real world computing technologies.
- 9-12.IC.7 Investigate the use of computer science in multiple fields.


In these Earth Science computer programming lessons, students will learn how
to design and implement simple programs that recreate observations of planetary orbits.
These simple models are attempts to predict how planets will move in the future. We also take a brief look at the benefits of computer simulations as well as its limitations.

---

## Tools Used
(include programming language(s), specific programs/environments, and other tools (digital or otherwise) if necessary)

NetLogo

---

## Resources
(include any links/books/readings to be used during this unit)
1. Thanks to clouds, new climate simulations predict more warming than predecessors (https://www.imperial.ac.uk/news/194738/thanks-clouds-climate-simulations-predict-more/)
2. How reliable are climate models? (https://skepticalscience.com/climate-models.htm)
3. Climate simulations are mostly accurate, study finds (https://apnews.com/article/science-ap-top-news-climate-climate-change-9898308e485f8dea65adb699cb2054a0)
4. https://mindstorms.media.mit.edu/


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
- day 9. lesson on climate change model found within NetLogo library
- day 10. lesson on exploring limitations of models like the climate change model in NetLogo and its implications.


---

## Assesments
(list summative and/or formative assessments used)
- Short response on the limitations of computer simulation models such as used in climate change.
- Verbal explanation of the models explored.
- Verbal explanation of student code and logic.
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

