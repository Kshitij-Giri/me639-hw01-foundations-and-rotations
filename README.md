# ME 639 – Introduction to Robotics
## Homework 1: Foundations & Rotations

This repository contains my submission for **ME 639 – Introduction to Robotics, Homework 1: Foundations & Rotations**.

The repository is divided into **Part 1 (Questions 1–6)** and **Part 2 (Questions 7–9)**.  
The original homework question PDF is also included for reference.

---

# Part 1 – Pen and Paper

## Questions 1–6

Questions **1–6** were completed as the pen-and-paper portion of the homework.

As required by the assignment, **no AI was used in solving Part 1**.

The complete solutions and working for Questions 1–6 are provided in:

`hw01_Part1_Q1-Q6_23110177.pdf`

The original homework/question PDF is also included in the repository:

`hw01.pdf`

---

# Part 2 – Implementation & Visualization

Part 2 consists of Questions **7, 8, and 9**.

AI was used as a learning and implementation aid for these questions, and the corresponding **AI Use Notes** are included with each question.

---

# Question 7 – Rotation Sandbox: Does Order Matter?

## Objective

Question 7 asks for an extension of the provided MuJoCo rotation sandbox so that elemental rotations can be applied about either:

- the **current (body) frame**, or
- the **fixed (space) frame**,

and to visually demonstrate that the order and frame in which rotations are applied affect the final orientation. The assignment asks for short demonstration recordings of the different cases.

## Code

The main code edited for Question 7 is:

`Q7/01_rotation_sandbox.py`

## Demonstration Videos

The Question 7 demonstration videos are provided in the `Q7/` folder.

The four videos demonstrate two aspects of rotation composition:

### 1. Effect of reversing the order of rotations

For example:

- **X45C → Z30C**
- **Z30C → X45C**

where `C` means **current frame**.

The two sequences use the same rotations but in reversed order, and produce different final orientations. This demonstrates that 3D rotations are **non-commutative**, i.e. the order of rotations matters.

### 2. Effect of changing the rotation frame

The videos also compare the same rotations when they are applied about the **current frame** versus the **fixed frame**.

Thus, the demonstrations show that:

- changing the order of the rotations changes the final orientation, and
- changing whether the rotations are about the current or fixed frame also changes the final orientation.

### Video Naming Convention

The filenames use the following convention:

- `X45` = 45° rotation about the X-axis
- `Z30` = 30° rotation about the Z-axis
- `C` = current/body frame
- `F` = fixed/space frame

For example:

`Q7_x45c_z30c.webm`

means:

**X-axis 45° current-frame rotation, followed by Z-axis 30° current-frame rotation.**

The four videos are:

- `Q7_x45c_z30c.webm`
- `Q7_x45f_z30f.webm`
- `Q7_z30c_x45c.webm`
- `Q7_z30f_x45f.webm`

## AI Use Note

The AI Use Note for Question 7 is:

`Q7/AI_Use_Note_Q7.txt`

It documents what AI assistance was used for and what was changed and verified independently.

---

# Question 8 – Verifying the Skew-Symmetric Identities

## Objective

Question 8 asks for numerical verification in simulation of the two identities from Question 5:

`R(v × w) = (Rv) × (Rw)`

and

`Rω̂Rᵀ = (Rω)̂`

The simulation uses a time-varying angular velocity and checks the identities for several random vectors at several simulated time steps.

## Code

The main code edited for Question 8 is:

`Q8/02_verify_skew_properties.py`

The code performs the numerical checks and calculates the residuals for both identities.

The explanation requested in the question regarding why a small numerical residual does not mathematically prove the identities is also included in the comments at the end of this Python file.

## Additional Feature

The original code included a fixed angular velocity case.

In addition to the required **time-varying angular velocity** case, I added an option to run the simulation with either:

- **Time-varying angular velocity**, or
- **Fixed angular velocity**

This allows the numerical verification to be compared in both cases.

## Numerical Results

The residual data and plots are included in the `Q8/` folder.

### CSV Results

- `residuals_fixed.csv`
- `residuals_time_varying.csv`

These contain the numerical residuals obtained during the simulations.

### Plots

- `residuals_fixed_plot.png`
- `residuals_time_varying_plot.png`

The plots show the numerical residuals over the simulated time steps.

The residuals are near machine precision, providing numerical evidence that the identities hold for the tested rotations and vectors.

## AI Use Note

The AI Use Note for Question 8 is:

`Q8/AI_Use_Note_Q8.txt`

It documents the AI assistance used during implementation and the changes and results that were independently tested and verified.

---

# Question 9 – Current Frame vs. Fixed Frame in ROS/RViz2

## Objective

Question 9 asks for the body frame and space frame to be broadcast as ROS2 TF frames and visualized in RViz2.

It also requires a toggle that allows the next rotation to be composed about either the:

- **current/body frame**, or
- **fixed/space frame**,

so that the difference can be observed live.

## Code

The main edited ROS2 node is:

`Q9/tf_broadcaster_node.py`

The code broadcasts the relevant TF frames and applies the rotation sequence using either current-frame or fixed-frame composition.

## Live Current/Fixed Toggle

A keyboard input loop was added to allow the composition mode to be changed while the ROS2 node and RViz2 are running.

- Press `c` to select **current-frame** composition.
- Press `f` to select **fixed-frame** composition.

The change can therefore be made while the visualization is running, allowing the difference in the resulting orientation to be observed live in RViz2.

## Demonstration Video

The Question 9 demonstration is provided as:

`Q9/Q9.webm`

The video shows the ROS2 TF visualization in RViz2 and demonstrates switching between current-frame and fixed-frame composition while the system is running.

## AI Use Note

The AI Use Note for Question 9 is:

`Q9/AI_Use_Note_Q9.txt`

It documents the AI assistance used during the implementation and the parts that were tested and verified independently.

---

# Repository Structure

```text
me639-hw01-foundations-and-rotations/
│
├── README.md
├── hw01.pdf
├── hw01_Part1_Q1-Q6_23110177.pdf
│
├── Q7/
│   ├── 01_rotation_sandbox.py
│   ├── AI_Use_Note_Q7.txt
│   ├── Q7_x45c_z30c.webm
│   ├── Q7_x45f_z30f.webm
│   ├── Q7_z30c_x45c.webm
│   └── Q7_z30f_x45f.webm
│
├── Q8/
│   ├── 02_verify_skew_properties.py
│   ├── AI_Use_Note_Q8.txt
│   ├── residuals_fixed.csv
│   ├── residuals_fixed_plot.png
│   ├── residuals_time_varying.csv
│   └── residuals_time_varying_plot.png
│
└── Q9/
    ├── tf_broadcaster_node.py
    ├── AI_Use_Note_Q9.txt
    └── Q9.webm

---

Author: Kshitij Giri 23110177
