# Using Kepler-s-Laws-in-Higher-Dimensions-Extending-the-RKF-Algorithm-with-Multi-Dimensional-Orbits



[![GitHub](https://img.shields.io/github/stars/Nkdarmel/AI-Powered-Temporal-Analysis-Long-Short-Term-Memory-LSTM-Neural-Network.svg?style=social)](https://github.com/Nkdarmel/AI-Powered-Temporal-Analysis-Long-Short-Term-Memory-LSTM-Neural-Network)

This project contains a Python script that utilizes the LSTM neural network for temporal analysis. The LSTM method is effective for handling sequential data and making predictions based on historical trends.

[![GitHub](https://img.shields.io/github/stars/Nkdarmel/AI-Powered-Temporal-Analysis-Long-Short-Term-Memory-LSTM-Neural-Network.svg?style=social)](https://github.com/Nkdarmel/AI-Powered-Temporal-Analysis-Long-Short-Term-Memory-LSTM-Neural-Network)
```

Description

This project presents a Python script that utilizes the Runge-Kutta-Fehlberg (RKF) method to calculate satellite positions based on Kepler's laws. The RKF method [Press et al. \cite{press2007numerical], providing a robust and efficient way to solve ordinary differential equations accurately.
The script leverages PyAutoCAD, an interface for interacting with AutoCAD from Python [Hugues et al. \cite{hugues2018pyautocad]. This allows the predicted satellite positions to be visualized in real-time within the CAD environment, making it a powerful tool for educational demonstrations and practical applications. Initial conditions and time steps are defined using NumPy arrays, enabling precise control over the simulation parameters. By connecting to CAD, the script clears any existing points and plots new satellite positions as dynamic entities. This script serves as a basic framework for integrating Python with CAD software for applications such as real-time satellite tracking or educational demonstrations of orbital mechanics. Future enhancements could include user input for varying satellite parameters or integrating machine learning models like LSTM networks to predict future trajectories based on historical data, thereby expanding the script's utility and applicability in various domains.

Project Modelling

create a tool that interacts with AutoCAD using PyAutoCAD and visualizes predicted satellite positions

Install the necessary libraries

pip install pyautocad pythonnet numpy matplotlib

Python script to interact with AutoCAD and visualize satellite position

import numpy as np
from PyAutoCAD import Autocad, APoint

# Define Kepler's laws to calculate satellite position at time t
def f(y, t):
    return [y[1], -0.5 * (y[0]**2 + 3)]

# Runge-Kutta-Fehlberg algorithm to solve ODEs
def RKF(y, t, dt):
    k1 = f(y, t) * dt
    k2 = f([y[0] + 0.5 * k1[0], y[1]], t + 0.5 * dt) * dt
    k3 = f([y[0] - 0.5 * k2[0], y[1]], t + 0.5 * dt) * dt
    return [y[0] + (k1[0] + 4*k2[0] + k3[0]) / 6, y[1] + (k1[1] + 4*k2[1] + k3[1]) / 6]

# Initial conditions
y = [0.5, 0]
t = 0
dt = 0.1

# Time steps
time_steps = np.arange(0, 1, dt)

# Calculate positions using RKF algorithm
positions = []
for t in time_steps:
    y = RKF(y, t, dt)
    positions.append([y[0], y[1]])

print(positions)

# Function to visualize the satellite positions in AutoCAD
def visualize_positions_in_autocad():
    acad = Autocad(create_if_not_exists=True)
    
    # Clear existing points
    for entity in acad.iter_objects('Point'):
        entity.Delete()
    
    # Plot predicted positions
    for pos in positions:
        point = APoint(pos[0], pos[1])
        acad.model.AddPoint(point)

# Call the function to visualize the satellite positions
visualize_positions_in_autocad()

print("Satellite positions visualized in AutoCAD.")




## Table of Contents
- [Project Overview](#project-overview)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Project Overview
This project aims to extend the RKF algorithm, a widely used numerical method for solving ordinary differential equations (ODEs), to handle multi-dimensional orbits in GIS Technology. By doing so, we can explore Kepler's laws in higher dimensions and gain insights into the behavior of celestial bodies.

## Getting Started

##  Prerequisites
- Node.js installed on your machine.
- npm or yarn package manager.

### Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/Nkdarmel/Kepler-s-Laws-in-Higher-Dimensions-Extending-the-RKF-Algorithm-with-Multi-Dimensional-Orbits.git
   ```
2. Navigate to the project directory:
   ```bash
   cd Kepler-s-Laws-in-Higher-Dimensions-Extending-the-RKF-Algorithm-with-Multi-Dimensional-Orbits
   ```
3. Install dependencies:
   ```bash
   npm install
   ```

## Usage
To run the example code, use the following command:
```bash
npm start
```
This will execute the RKF algorithm to simulate orbits and display the results.

## Contributing
Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/AmazingFeature`).
3. Make your changes and commit them (`git commit -m 'Add some AmazingFeature'`).
4. Push to the branch (`git push origin feature/AmazingFeature`).
5. Open a pull request.

## License
This project is licensed under the GNU GENERAL PUBLIC License - see the [LICENSE](LICENSE) file for details.
```

[![Build Status](https://github.com/Nkdarmel/Kepler-s-Laws-in-Higher-Dimensions-Extending-the-RKF-Algorithm-with-Multi-Dimensional-Orbits/workflows/Main%20Workflow/badge.svg)](https://github.com/Nkdarmel/Kepler-s-Laws-in-Higher-Dimensions-Extending-the-RKF-Algorithm-with-Multi-Dimensional-Orbits/actions)
```
