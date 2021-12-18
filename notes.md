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
