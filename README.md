# Wireless_radio2026_RF-Planning-Studio-Short-Analysis-Task
In this task, I will evaluate a wireless link as an RF engineer.  I will modify key design parameters and observe how they affect, such as coverage distance, received power, fresnel clearance, link feasibility. The goal is interpretation, not long calculations.

This RF planning analysis evaluates how physical and environmental parameters shift the feasibility of a wireless link. Based on the MATLAB script provided and standard electromagnetic theory, here is the breakdown of the four experiments.

1. Increase Gateway Height by +5 m

Modifications: htx_1 = 25 (up from 20)
Does maximum LOS distance change?
Yes. 

Using the approximation d_LOS approx 3.57* (sqrt{h_{tx}} + sqrt{h_{rx}}), increasing h_tx from 20m to 25m increases the LOS distance from approximately 21.0 km to 22.9 km.

Does link feasibility improve significantly?

In this specific 4 km link, the improvement is marginal for received power but significant for obstacle clearance. Why?  Radio waves require a "clear" path. Increasing height primarily helps "look over" local obstructions (buildings, trees) and extends the radio horizon. However, in a simple log-distance path loss model, height doesn't significantly change the path loss itself unless it fundamentally changes the environment exponent (n).

2. Increase Antenna Gain to 5 dBi

Modifications: Gtx_2 = 5, Grx_2 = 5

How does the received power curve change?

The entire curve shifts upward on the Y-axis. Since both Tx and Rx gains increased by 3 dB, the total system gain increases by 6 dB.

How much additional range is achieved?

Because n=2.7, a 6 dB boost roughly doubles the signal strength relative to the noise floor, extending the distance where the signal hits -120 dBm by roughly 60–70%.

Why does antenna gain extend coverage?

Antenna gain doesn't "amplify" power (it's passive); it focuses the radiated energy into a tighter beam (EIRP) and increases the "aperture" or sensitivity of the receiver.

3. Change Environment Exponent (n)

Test: n = 2.0 (Free Space), n = 3.5 (Urban), n = 4.0 (Dense Urban)

How does increasing n affect coverage?

The slope of the power decay curve becomes much steeper. As n increases, the signal hits the sensitivity floor (-120 dBm) much earlier.

Which has a stronger impact: gain increase or environment change?

The environment change (n) has a much more drastic impact.

Explain physically:

n represents how quickly energy is absorbed, scattered, or reflected by the surroundings. In free space (n=2), power drops by the square of the distance (d^2). In a dense city (n=4), it drops by d^4. No amount of antenna gain can easily overcome the exponential losses caused by a high n value.


4. Move Gateway/Obstacle (Fresnel Study)


Modifications: xObs_4 at 0.1D, 0.5D, 0.9D

Where is Fresnel radius largest?

The Fresnel radius (r_F) is largest at the midpoint (0.5D) of the link.

Why is the midpoint usually critical?

The Fresnel zone is an ellipsoid (football shape). Geometrically, the distance from the LOS path to the ellipsoid boundary is maximized exactly halfway between the transmitter and receiver.

What happens if the 60% clearance rule is violated?

If an obstacle enters the 60% Fresnel zone, you experience diffraction loss. Even if you have a visual line-of-sight (you can see the other antenna), the obstacle will "soak up" or reflect some of the electromagnetic energy, causing the signal to drop significantly—often by 6 dB or more.


In practical wireless deployment, the environment exponent (n) has the most profound impact on coverage because it dictates the rate of signal decay over distance.

While increasing antenna gain or transmitter power provides a linear, fixed boost in decibels, the environment exponent acts as an exponential factor in the path loss equation.

In a clear, rural environment (n approx 2), a signal can travel several kilometers with ease; however, in a dense urban canyon (n approx 4), that same signal may drop below the sensitivity threshold within a few hundred meters. 

This means that site selection—moving an antenna to avoid obstructions or achieving a better "line-of-sight" to lower the effective n  is far more effective for extending range than simply swapping for higher-gain hardware.


