---
title: "Field Oriented Control 101: The concept"
date: 2024-11-10T06:00:23+06:00
hero: hero.jpg
theme: Toha
menu:
  sidebar:
    name: Field Oriented Control 101
    identifier: foc-101
    parent: motor_control
    weight: 10
math: true
mermaid: true
---

Field Oriented Control (FOC) is a widely used control technique for brushless motors due to its ability to deliver precise and efficient motor operation. It is especially popular in applications that require smooth torque delivery, energy efficiency, and precise speed control.

### Brushless motor

{{< img src="brushed_motor.gif" height="30%" width="30%" align="center">}}
{{< vs 1>}}

A brushless motor operates using three-phase currents, with two of the three phases energized at any given time to create an electromagnetic field that drives the rotation of the permanent magnet rotor. Controlling these phases to switch on and off in a precise manner is critical for achieving a desired speed or torque. This requires a carefully designed control strategy, commonly referred to as Field-Oriented Control (FOC).


### The math behind FOC

FOC algorithm includes of two famous transformation: Clarke Transformation (CT) and Park Transformation (PT). CT converts three-phase (a-b-c) currents or voltages into a two-phase ($\alpha$-$\beta$) orthogonal coordinate system. Note that the a-b-c coordinate is a three-axe coordinate on a 2D plain. 

{{< img src="clark_transformation.png" height="50%" width="50%" align="center">}}
{{< vs 1>}}

Hence we have

$$ I_\alpha = I_a - \sin 30^\circ I_b - \cos 60^\circ I_c = I_a - \frac{1}{2} I_b - \frac{1}{2} I_c $$

$$ I_\beta = \cos 30^\circ I_b - \cos 30^\circ I_c = \frac{\sqrt{3}}{2} I_b - \frac{\sqrt{3}}{2} I_c $$

Kirchhoff Circuit Laws tells us that $I_a + I_b + I_c = 0$. So we can substitute $I_c = -I_a - I_b$ and combine with the above equations. Write it in matrix form we have

$$ 
\begin{bmatrix} I_\alpha \newline I_\beta \end{bmatrix} = \begin{bmatrix} \frac{3}{2} \space 0 \newline \space \frac{\sqrt{3}}{2} \space \sqrt{3} \end{bmatrix} \begin{bmatrix} I_a \newline I_b \end{bmatrix}
$$

To maintain $I_\alpha = I_a$, we have to add an extra coefficient before the matrix, then

$$ 
\begin{bmatrix} I_\alpha \newline I_\beta \end{bmatrix} = \frac{2}{3} \begin{bmatrix} \frac{3}{2} \space 0 \newline \space \frac{\sqrt{3}}{2} \space \sqrt{3} \end{bmatrix} \begin{bmatrix} I_a \newline I_b \end{bmatrix} = \begin{bmatrix} 1 \space 0 \newline \frac{1}{\sqrt{3}} \space \frac{2}{\sqrt{3}} \end{bmatrix} \begin{bmatrix} I_a \newline I_b \end{bmatrix}
$$

PT then transforms two-phase stationary ($\alpha$-$\beta$) reference frame into a two-phase rotating (d-q) reference frame aligned with the rotor's magnetic field.

{{< img src="park_transformation.png" height="30%" width="30%" align="center">}}
{{< vs 1>}}

The transformation can be done with a 2D transformation matrix as follows:

$$ 
\begin{bmatrix} I_d \newline I_q \end{bmatrix} = \begin{bmatrix} \cos \theta \space \sin \theta \newline - sin \theta \space \cos \theta \end{bmatrix} \begin{bmatrix} I_\alpha \newline I_\beta \end{bmatrix}
$$

where $\theta$ can be measured by a sensor.

### Summary

FOC is essentially converting between the three-phase currents ($I_a, I_b, I_c$) and the rotor's two-phase currents ($I_d, I_q$). Mathematically, we have

$$ 
\begin{bmatrix} I_d \newline I_q \end{bmatrix} = \begin{bmatrix} \cos \theta \space \sin \theta \newline - \sin \theta \space \cos \theta \end{bmatrix} \begin{bmatrix} I_\alpha \newline I_\beta \end{bmatrix} = \begin{bmatrix} \cos \theta \space \sin \theta \newline - \sin \theta \space \cos \theta \end{bmatrix} \begin{bmatrix} \frac{3}{2} \space 0 \newline \space \frac{\sqrt{3}}{2} \space \sqrt{3} \end{bmatrix} \begin{bmatrix} I_a \newline I_b \end{bmatrix}
$$

Or, if ($I_a$, $I_b$) are placed on the left hand side,

$$ 
\begin{bmatrix} I_a \newline I_b \end{bmatrix}
 = \begin{bmatrix} \frac{2}{3} \space 0 \newline \space -\frac{1}{3} \space \frac{\sqrt{3}}{3} \end{bmatrix} \begin{bmatrix} \cos \theta \space - \sin \theta \newline \sin \theta \space \cos \theta \end{bmatrix}  \begin{bmatrix} I_d \newline I_q \end{bmatrix}
$$















