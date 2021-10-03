# Unit Plan for Teaching Earth Science with Computer Science   10/3/2021

## Jovani Cardenas

## Peter Tsun

In this unit plan, students learn about some essential ideas in computer science, and apply their newly acquired computer science knowledge to draw an elliptical orbit of a planet going around the sun. Typically in regents earth science, an astronomy unit, which contains elliptical orbit, is the last unit in earth science sequence, but in my school astronomy is the first unit because astronomy piques students’ interests in earth science better than calculating gradient and drawing profiles of a topographic map.

In earth science, students may see a video clip of computer rendering of planets orbiting around the sun or even play with computer simulations made by other people to show planets orbiting around the sun, but they don’t have the opportunity to build for themselves an animated model of planets orbiting the sun. Some teachers also show physical models of our solar system and emphatically tell students that planets speed up as they are closer to the sun (perihelion)  and planets slow down as they are farther away from the sun (aphelion).

 * https://javalab.org/en/solar_system_en/
 * https://phet.colorado.edu/sims/html/gravity-and-orbits/latest/gravity-and-orbits_en.html
 * https://ophysics.com/f6.html

However, just because teachers tell students the facts that will be tested on regents exams, students may not internalize the information as well as if they can build a computer model and see for themselves that the planets do indeed move faster at perihelion and move slower at aphelion. In this proposed unit, students will learn the reason for loop/repetition by drawing a polygon like square, pentagon, triangle, etc. It takes a day just to get everyone to install netlogo on their computers. Once they learn how to draw polygons in two to three days (including the first day of just installing netlogo), students will learn to draw a circle. If the students are advanced, they can learn to fine-tune the circle with the pi formula (𝜋 =Circumference/Diameter)
within the same day of drawing some random circle.

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

So far, this is the proposed plan; if we have only 5 or 6 days worth of lessons, then we can create a lesson of drawing three circles around three seismic stations to determine location of the epicenter. Additional ideas are using a GIS map to show drainage patterns on netlogo 3D.  
https://www.youtube.com/watch?v=czoPyHx3RZM
