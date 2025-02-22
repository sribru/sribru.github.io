---
title: "NASA Aeronautics Design University Challenge: AMPHIBIAN DYNAMICS"
excerpt: "This project was part of NASA ARMD 2022 Univesrsity challenge <br/><img src='/images/frog.jpg'>"
collection: portfolio
---
Urban Air Mobility (UAM) and Regional Air Mobility (RAM) vehicles have gained popularity in recent years due to their suitability as small-scale aerial vehicles for use in urbanized areas. Currently, these aerial vehicles are being used as passenger or cargo vehicles, but to encourage wider usage of these vehicles, NASA has issued a request for proposals that seek to investigate the feasibility of using UAM aircraft as dedicated firefighting aircraft. UAMs possess great firefighting capabilities such as rapid deployment, short or vertical takeoff and landings, and high utilization rates making them great for firefighting. NASA aims to design aircraft capable of flying from small airports, collecting 3000 gallons of water from nearby sources, and delivering to the fire location that is no morethan 100 nautical miles away in a single pass. The proposed aircraft design from our team, F.R.O.G (Firefighting Rotorcraft,Original Generation), is an amphibious tilt-rotor aircraft with water collection tanks, that combines the aerial maneuverability of traditional helicopters, with the long-range endurance and payload capacity of fixed-wing aircraft. 

<img src='/images/frog.jpg'>

NASA ARMD’s proposal requires an aircraft with a few notable characteristics: 
* It has to be a **high-lift, V/STOL aircraft** capable of executing steep descents and ascents to achieve water collection in tree-enclosed water sources.
* The requirement dictates that it must be able to **collect 3,000 gallons** of water, which is equal to **25,000 pounds**.
* A takeoff/ landing distance of **< 1000ft** and a minimum ceiling height of **8000ft** .
* A travel range of **≤ 100 nmi** and a mximum payload capacity of **25,000 lbs** .  


Owing to these requirments, the F.R.O.G is designed as a quick-fire response fighting amphibious tiltrotor aircraft with a payload capacity of 3000 gallons of water 
It has two take-off options: one is to vertically take-off with both rotors pointed upwards and achieve a climb rate of 16.4 feet per second and reach an altitude
of 5000 feet before pitching forwards and tilting the rotors forward into fixed-wing flight. 

As a part of Amphian Dynamics, I was responsible for designing an novel aircraft control system for the tiltirotor aircraft in different flight conditions.The key problem in the development process of a tilt rotor is its mathematical modeling. Aircraft system identification is mainly concerned with providing a
mathematical description for the aerodynamic forces and moments in terms of relevant measurable quantities such as control surface deflections, aircraft angular velocities, airspeed,and the orientation of the aircraft to the relative wind. But mathematical modelling of a tilitrotor while considering these measurable quantities and other extenral and internal force is more complex than on the case of a fixed wing aircraft owing to the variable wing configurations. This problem was solved by  parition modelling method, where the aircraft is divided into five different primary aerodynamic components: the rotors, wing, fuselage, horizontal tail and vertical fin.For each componenet, an aerodynamic model for each component is developed where the aerodynamic force of each component will find its solution in wind axis system and finally be converted to body axis system with the conversion matrix. The different componentsof the tiltrotor aircraft can be seen below.

<img src='/images/tiltrotor_comp.jpg'>

After building the nonlinear simulation model in MATLAB/Simulink,the effectiveness and accuracy of the model is validated at the steady state using MATLAB's trim fucntion to achieve the trim condition or the steady state. After validation of our results we now moveon to linearizing our nonlinear model. The linearization can be performed using the Linmod function in the MATLAB/Simulink workspace. Our team concluded that an amphibious aircraft is the best option for this mission, if utilized firefighting units will have a greater chance of minimizing and putting out larger fires at a more efficient rate. Our next step includes developing a full-fledged control system which is built upon the validation model for the aircraft based on our multi-part mathematic modeling of the aircraft.

<img src='/images/simulink_model.jpg'>
