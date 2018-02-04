# CarND-Controls-PID
This repository contains all the code needed to complete the PID Controller project for Udacity's Self-Driving Car Nanodegree.

---

## Submission

Files modified
- PID.cpp
- PID.h
- main.cpp

## Reflection

### Effect of P,I,D components

#### Controllers used
In order to meet the project requirements, I used two PID controllers
- The first PID controller controls the throttle and sets the desired velocity. This is similar to the PID controller covered in the course videos.
- The second PID controller is used to control the steering angle.
In both cases, the control is based on the cross track error(CTE)

#### Significance of P,I,D

- `P` or `Proportional` controller: This controller works proportionally to the CTE. If the CTE is too large, the control output will also be large. This can cause the car to oscillate uncomfortably.
- `I` or `Integral` controller: This controller integrates over previous value of CTE. The integral term eliminates residual error as it integrates over more time periods. It results in a stabilizing effect on the steering. This can help counteract biases like strong wind, misaligned wheels etc.
- `D` or `Derivative` controller: This controller is based on the rate of change of CTE. It helps dampen the oscillation. For example, if the car starts veering rapidly to the right, this controller will help dampen the action.

Intuitively,
- `P` controller alone will result in the car oscillating wildly.
- `PD` controller will help the car oscillate less. However, it will not be able to counteract biases.
- `I` controller helps the car counteract biases like misaligned steering.

### Parameter tuning

The final solution is based on the following parameters: P = 0.1, I = 0.0001, D = 5

These parameters were tuned manually as explained below:
- `P`: I chose a value suitable for the car velocity.
- `D`: The value of D was chosen to dampen oscillations. The value of 5 provided a relatively smooth output.
- `I`: A small value was sufficient here. Experimenting with larger values resulted in a very oscillating output. I think this is because there is not much bias in the simulation.

