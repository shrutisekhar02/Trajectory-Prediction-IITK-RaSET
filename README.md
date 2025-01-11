# TRAJECTORY PREDICTION
This project predicts the latitude, longitude, and altitude of a rocket at the next time step using an LSTM model with a local attention mechanism. The input includes historical sensor data collected from:

    1. IMU (6 degrees of freedom): Linear acceleration (a_x, a_y, a_z) and angular velocity (W_x, W_y, W_z).
    2. GPS Data: Latitude, longitude, and altitude.

\
The project uses 5 seconds of historical IMU and GPS data to predict the rocket’s latitude, longitude, and altitude for the next second in real-time.


## Introduction
Traditionally, rocket trajectory prediction has been accomplished using Kalman Filters, which are widely regarded as robust tools for estimating a system’s state in the presence of noise. Kalman Filters rely on mathematical models and sensor fusion to make predictions, but they often struggle to capture the nonlinear dynamics of complex systems like rocket flight.

In this project, we take an innovative approach by leveraging Recurrent Neural Networks (RNNs), specifically Long Short-Term Memory (LSTM) networks, for trajectory prediction. Unlike Kalman Filters, LSTMs excel at modeling nonlinear temporal dependencies in time-series data.

To further refine our predictions, we implemented a local attention mechanism. While LSTMs process sequential data, they treat all time steps equally, which is suboptimal for trajectory prediction. In reality, recent data points (closer to the prediction moment) have a stronger influence on the trajectory than older ones.
 

## Dataset
The dataset consists of .mat files (imu.mat and gps.mat) that were generated using a  [MATLAB-based toolbox](https://github.com/saeedmozafari/IMU_Magnetometer_GPS_Trajectory_Generator) for simulating rocket flight sensor data.




