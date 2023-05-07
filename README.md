Download Link: https://assignmentchef.com/product/solved-mce747-homework-4
<br>
<h1>1: LQR design with linearized plant</h1>

A magnetic levitation system consists of an electromagnet and an optical sensor to detect the vertical position of a steel ball. The objective is to establish a feedback loop to maintain the ball floating in mid-air, between the sensor post and the electromagnet’s end surface. A system schematic is shown in Fig. 1. Assume that we can control the current using an

Figure 1: Schematic of Maglev System

amplifier capable of delivering any requested current between -2.5 and 2.5 A. The upward force exerted by the electromagnet on the ball is

where <em>k </em>= 6<em>.</em>5308× 10<sup>−5 </sup>N-m<sup>2</sup>/A<sup>2</sup>, <em>i </em>is the current on the coil and <em>x </em>is the gap between the top of the ball and the electromagnet’s flat end. The mass of the ball is <em>m </em>= 0<em>.</em>068 kg and the acceleration of gravity is <em>g </em>= 9<em>.</em>81 m/s<sup>2</sup>.

<ol>

 <li>Find the differential equation relating <em>i </em>(input) to <em>x </em>(output), accounting for gravity and electromagnetic force.</li>

 <li>Show that the current needed to maintain the ball in equlibrium at an air gap valueof <em>x<sub>eq </sub></em>is</li>

</ol>

(1)

<ol start="3">

 <li>Obtain a linearized differential equation model for operation near <em>i<sub>eq </sub></em>and <em>x<sub>eq</sub></em>. For this, use a 2-variable Taylor expansion formula for <em>mg </em>− <em>F </em>at the equilibrium point. 4. Use the above to show that the linearized transfer function from ∆<em>i </em>to ∆<em>x </em>is</li>

</ol>

(2)

<ol start="5">

 <li>Obtain a state-space representation of the linearized system at the equilibrium point.</li>

 <li>Find <em>i<sub>eq </sub></em>corresponding to <em>x<sub>eq </sub></em>= 0<em>.</em>006 m from Eq. 1. Then obtain the numerical value for the feedforward gain <em>k<sub>ff</sub></em>.</li>

</ol>

<strong>Control Design by LQR</strong>

Use a state-space representation to design a linear state feedback controller for regulation to a setpoint with the following specifications:

<ol>

 <li>Zero steady-state error to step changes in target position.</li>

 <li>Settling time to a step input of approx. 1 second</li>

 <li>Overshoot as small as you can.</li>

 <li>The range of motion is limited between <em>x </em>= 0 and <em>x </em>= 0<em>.</em>014 m. The current must be kept within ±2<em>.</em>5 A.</li>

 <li>Test for a stable response using a Simulink model. Use the <em>linearized </em>plant and a step input of 1 mm. The settling time should be near 1 second, but the overshoot may be high (100%).</li>

 <li>Check that the current spike stays within ±1 A for a step input of 1mm.</li>

 <li>Prepare a Simulink model to test the controller against the actual nonlinear plant, asdone in class (you have to account for offsets, in this case the bias current must be injected in a feedforward fashion). Transfer the position from rest at the post (14mm) to mid-air, at 6mm from the flat end of the electromagnet as fast as possible while checking that the current remains within bounds.</li>

</ol>

<h1>2: Quadratic Lyapunov Function and Region of Attraction</h1>

The linearized system under the state feedback gain is a globally asymptotically stable closed-loop system. The nonlinear system under the same controller has only local stability, however. In this problem, a quadratic Lyapunov function will be used to obtain a crude estimate of the region of attraction.

<ol>

 <li>Use the closed-loop system matrix <em>A<sub>c </sub></em>= <em>A </em>− <em>BK </em>to obtain a quadratic Lyapunov function. For this, select any symmetric positive-definite matrix <em>Q </em>and solve the Lyapunov equation for <em>P</em>:</li>

</ol>

<em>A<sub>C</sub></em><sup>′ </sup><em>P </em>+ <em>P </em><sup>′</sup><em>A<sub>c </sub></em>+ <em>Q </em>= 0

In Matlab this is done with P=lyap(Ac’,Q)

<ol start="2">

 <li>Use symbolic and numeric processing to evaluate the derivative of <em>V </em>along the trajectories of the nonlinear closed-loop system. Then use a polar scan around the equlibrium point to detect a failure of the <em>V &lt;</em>˙ 0 condition. Essentially, you will be finding the boundary defined by <em>V</em>˙ = 0.</li>

 <li>The region determined above is conservative for 2 reasons: <em>Q </em>(in the Lyapunov equation) is selected arbitrarily and the Lyapunov method is only a sufficient condition (quadratic functions are not necessarily the best to show stability of a given nonlinear system). Show (by simulation example) that there are initial conditions inside the true region of attraction that do not belong to the polar region you found.</li>

 <li>Bonus points: iterate <em>Q </em>(manually or by any optmization method you feel comfortable with) to obtain some improvement to the area of your polar region. You must report the exact values of the area before and after optimization.</li>

</ol>