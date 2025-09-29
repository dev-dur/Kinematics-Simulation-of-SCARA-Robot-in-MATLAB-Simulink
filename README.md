# Kinematics-Simulation-of-SCARA-Robot-in-MATLAB-Simulink
A project focused on simulating the forward and inverse kinematics of a SCARA robot using MATLAB &amp; Simulink. The SCARA (Selective Compliance Articulated Robot Arm) is widely used in pick-and-place and precision assembly applications, making it an ideal test case for academic modeling, validation, and simulation.

## 📌 Project Overview
- Year: 2025
- Industry: Mechanical Simulations
- Client: University Project
- Duration: 1 Month

### Goal:
To model, analyze, and validate the kinematic behavior of a SCARA robot, including its workspace, degrees of freedom, and motion trajectories using MATLAB & Simulink.

## ⚙️ Workspace & Degrees of Freedom (DOF)
The SCARA robot model has 3 degrees of freedom (DOF):
- θ1 (Theta1): Base rotation joint (−145° to +145°)
- θ2 (Theta2): Elbow rotation joint (−145° to +145°)
- d3 (Prismatic Joint): Vertical displacement (−0.23 m to +0.07 m)
- θ4 (end-effector rotation) is ignored, as the model uses a suction-type end effector.

### Workspace:
- Horizontal: Circular area defined by reach (L1 + L2).
- Vertical: Range from −0.23 m to +0.15 m.

## 🛠️ CAD & Multibody Modeling
The robot was modeled using SolidWorks → Simulink Multibody Integration.
### Link Parameters:
- Link 1 (L1): 40 cm
- Link 2 (L2): 30 cm
- Prismatic Joint (d3): Range −0.23 m to +0.07 m
<img width="527" height="377" alt="image" src="https://github.com/user-attachments/assets/fd81f8ef-84bf-4466-8720-ed610e144219" />


### Workflow:
- Geometry & joints defined in CAD.
- Exported as XML via Export CAD to XML.
- Imported to Simulink using smimport.

## 📐 Theoretical Calculations
### DH Parameters
| Link | aᵢ | αᵢ | dᵢ  | θᵢ           |
| ---- | -- | -- | --- | ------------ |
| 1    | L1 | 0  | 0   | θ1           |
| 2    | L2 | 0  | 0   | θ2           |
| 3    | 0  | 0  | −d3 | 0            |
| 4    | 0  | 0  | 0   | θ4 (ignored) |

### Forward Kinematics
- Planar Position:
  X = L1·cos(θ1) + L2·cos(θ1 + θ2)
  Y = L1·sin(θ1) + L2·sin(θ1 + θ2)

- Vertical Position:
  Z = -d3

### Inverse Kinematics
- Compute reach radius: R = √(X² + Y²)
- Solve θ1, θ2 using trigonometric relations.
- Compute d3 directly from Z.
- Validate by feeding results back into forward kinematics.

## 🔬 MATLAB & Simulink Integration
Implemented both script-based computation and block-based simulation.
### Features:
- Input joint values via script.
- End-effector position output in MATLAB console.
- Motion visualization in Simulink.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/651adb6e-8a5d-4e55-9d75-2be12ea10847" />

  
## ✅ Case Studies
| Case | Joint Inputs (θ1, θ2, d3) | Status                            |
| ---- | ------------------------- | --------------------------------- |
| 1    | (140°, 100°, 0.01 m)      | ✅ Simulated successfully          |
| 2    | (−145°, −145°, 0.015 m)   | ✅ Simulated successfully          |
| 3    | (130°, −135°, 0.07 m)     | ⚠️ Out of range – Error validated |

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3e7865b9-5d54-4b8f-819c-2247f73627d7" />


## 📊 Outcomes
- Verified forward & inverse kinematics through MATLAB-Simulink integration.
- Validated workspace boundaries for both planar and vertical reach.
- Implemented error handling for out-of-range configurations.
- Delivered a modular workflow for future robotic manipulator simulations.

## 🏁 Conclusion
This project provided practical insights into:
- Kinematic modeling of SCARA manipulators.
- Using DH parameters for forward/inverse analysis.
- Integrating CAD, MATLAB, and Simulink for robotic simulations.
- Validating theoretical equations with simulation-based testing.
