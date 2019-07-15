## PID Controller

In this project, I implemented a PID controller in C++ to maneuver the vehicle around a lake race track in a Unity simulator. The goal was to adjust the position of the car on the road by calculating the steering angle needed to correctly place it in the middle.

In the attached video file, the car drives a lap around the track autonomously.


**_The different P, I, D components had a different effect on the PID algorithm:_**

- **P** (proportional) accounted for the present value of the steering angle. For example, if the error was large and positive, the steering angle was large and negative, to adjust the car’s location.
Since the car is located correctly on the middle of the road and we want to keep it that way, the coefficient was very small.

- **I** (integral) accounted for past values of error, so if there is a bias in the navigation system of the car, the car can correctly adjust its location.
For example, if the error is not sufficiently strong, the integral of the error will accumulate over time, and the controller will respond by applying a stronger action.
In this project, we assume that there is no problem with the navigation system of the car and therefore the coefficient is zero.

- **D** (differential) accounted for possible future trends of the error, based on its current rate of change, which means that it functions as a mechanism to reduce the strength of the steering to prevent overshot. This coefficient was large because of the turns in the road.

I chose the final hyperparameters (P, I, D coefficients) through manual tuning. I tried different combinations until I found a good combination and the car drove as I expected.

