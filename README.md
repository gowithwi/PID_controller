# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

---
1. Summary
In this project I implanted the PID controller to drive the car so that it followed the designed track.

2. effect each of the P, I, D components

The steering value is defnied in main.cpp as:
          steer_value = pid.TotalError();
whereas the TotalError() is defined in PID.cpp as:
          d_error = cte-p_error;
          p_error = cte;
          i_error += cte;
    
          return Kp*p_error + Ki*i_error + Kd*d_error;

p_error is the cte. d_error and i_error represent the differencial error and integral error, respectively. Hence, the "P" component is to minimize the cte, the "I" component is to minimize the system bias, the "D" component is to minimize the oscillation.

3. down selection of hyperparameters.
I am using the hyperparameters as below:
          double Kp = -0.3;
          double Ki = -0.001;
          double Kd = -15;
Those hyperparameters are defined by hand tuning. As the oscillation is serious, I increased the Kd all the way up to -15. Further increase will reduce the response to track turns. Regarding Ki, since our systematic bias is not that obvious, I keep it as a low value.

