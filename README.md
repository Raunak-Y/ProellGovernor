# Proell Governor Report

**ME22B044 Raunak Yadav**

## Objectives

1.  **Understanding Operation Principles:** Exploring the theoretical
    foundations of Proell governors, including equations and control
    mechanisms.
2.  **Building A Simulation Model:** Construct a dynamic simulation
    model in MATLAB to replicate the behaviour of a Proell governor
    under different conditions.
3.  **Investigating System Performance:** The simulation model is used
    to analyse the performance of the Proell governor system under
    various scenarios, such as changes in load, speed setpoints, and
    system parameters.

## Assumptions

1.  Friction at all joints is negligible. 
2.  Air resistance is ignored. 
3.  Gravity acts in -z direction.

## Scope

Governors are employed to maintain engine speeds within specified
boundaries, ranging from no load to full load conditions. Their function
is to regulate the throttle of the carburettor in gasoline-powered
engines and the fuel pump in diesel engines. Among the various types,
centrifugal governors that rely on flyweights are the most prevalent.
The positioning of these weights is dependent on the speed at which they
are rotating.

The dynamic system comprises a spindle that is mounted in a vertical
orientation. The governor linkages are connected to a sleeve that
undergoes upward movement due to the outward force exerted by the balls
as a result of centrifugal force. The extent of this sleeve's lift is
determined by utilizing a scale.

There exists a category of governors known as dead weight governors,
which are controlled by the force of gravity and are a form of
centrifugal governors, for example Porter Governor and Proell Governor.

## Description

The Proell Governor is a centrifugal governor variant featuring an
elongated arm carrying the rotating balls, moving at the extended arm's
rotational velocity. Moreover, dead weights augment the rotation speed,
facilitating accurate high-speed operation. This governor's design
ensures consistent functioning devoid of fluctuations.

## Construction

The Proell Governor's construction comprises two arms joined at a pivot
point, plus an extended arm supporting the balls, also connected to the
other arms. A connecting rod links the sleeve and arms, causing sleeve
lift when balls rotate around the fixed pivot.

**Key components include:** - **Pivot:** linking arm point. - **Arms:**
rotating with attached balls. - **Extended arms:** straight arms at ends
supporting balls. - **Balls:** predetermined weight atop extended arms,
moving sleeve up/down via connecting rod. - **Connecting rod:** joining
sleeve to balls. - **Sleeve:** linked to balls by rod, sliding along
spindle to regulate fuel tank-to-engine flow. - **Fuel pump:** supplying
engine fuel from tank.

## Working Principle

When engine load decreases, the spindle's faster rotation causes the
governor arms and balls to move outward due to increased centrifugal
force. This lifts the sleeve, triggering a mechanism closing the
throttle valve, reducing fuel supply to maintain engine speed.
Conversely, increased engine load slows the spindle and ball rotation,
lowering the sleeve and activating a mechanism opening the throttle
valve, increasing fuel supply and engine speed.

The Proell Governor's height is given by:

    h = FM/BM * (m + M/m) / (895 * ω^2)

## Kinematic Analysis

-   m - Mass of each ball (kg) 
-   W - Weight of each ball = m *g (N) 
-   M - Mass of central load (N) 
-   r - Radius of rotation (m) 
-   h - Height of governor (m) 
-   w - Angular speed of the ball (rad/s) 
-   Fc - Centrifugal force acting on the ball (N) 
-   T1 - Tension in the arm (N) 
-   T2 - Tension in the link (N) 
-   α - Angle of inclination of the arm (rad) 
-   β - Angle of inclination of the link (rad)

Equation derivation:

    Fc × BM = mg × IM + Mg/2 × ID

    Fc = (FM/BM) [mg tan α + Mg/2 (tan α + tan β)]
    mw²r = (FM/BM) * (r/h) [mg + Mg/2 (1+q)]
    w² = (FM/BM) [mg + Mg/2 (1+q)] g/h

Where **tan α = r/h** and **q = tan β/tan α**.

## Modelling Procedure

MATLAB Simscape was utilized to develop the project model. The model
construction process involved either importing CAD files or using the
solids tool to create the necessary parts. Initially, the solver
configuration block, world frame, and mechanism configuration were
added.

-   Cylinders were used to create the central rod, arms, sleeve, and
    other links. 
-   Spheres represented the spherical side weights. 
-   Bricks were used to create the top solid. 
-   Joints, such as revolute and cylindrical joints, were necessary to
    connect different parts of the model. 
-   The Rigid Transform tool in MATLAB Simscape was employed to
    correctly position the created bodies.

A ramp block was used to provide input and adjust the rotational speed.
Graphs can be plotted using the scope and multiplot graph. The data
inspector is used to analyze the graphs.

Mass of the sleeve: **0.37 kg**.

## Simscape Multibody Model

*(Insert Model Diagram Here)*

## Graphs

-   **Variable angular speed vs time** 
-   **Constant angular speed vs time @ w=10 rad/s** 
-   **Variation of lift with angular velocity** 
-   **Effect of deadweight on lift @ w=10 rad/s**

## Inference

-   Increasing the spin velocity leads to an increase in the lift of the
    sleeve. 
-   The lift of the sleeve increases when the mass of the balls (dead
    weight) is increased.

## Applications

1.  Automobiles, aircraft, turbine controls, and other industries.
2.  Electrical generators and mopeds.
3.  Speed regulators in various types of vehicles.
