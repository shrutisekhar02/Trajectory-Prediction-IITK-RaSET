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
 

## Dataset Generation 
To generate data for multiple runs, you need to execute:  

```bash
python gnss-ins-sim/dataset_optimised.py
```

This script processes the IMU and GPS data, creating training datasets. It extracts 5-second time windows from the sensor data to ensure sufficient historical context for trajectory prediction.

## Model Training
The LSTM model is trained using the Jupyter Notebook:
```bash
lstm_trajectory.ipynb
```

This notebook loads the generated dataset, trains the LSTM model, and evaluates its performance.

## Project Structure

```bash
Trajectory-Prediction-IITK-RaSET/
│── gnss-ins-sim/                # Folder containing dataset generation scripts
│   ├── dataset_optimised.py     # Generates dataset for multiple runs
│── lstm_trajectory.ipynb        # Jupyter Notebook for training the model
│── X.npy                        # Processed input data
│── y.npy                        # Processed target data
│── README.md                    # Project documentation
│── .gitignore                   # Git ignore file
```
