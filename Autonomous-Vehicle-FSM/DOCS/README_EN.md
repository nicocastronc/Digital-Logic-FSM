# 🇺🇸 Complete Project Documentation

## 🚗 Sequential Controller for Autonomous Vehicle

**Design, simulation, and physical implementation of a Finite State Machine (FSM) for autonomous navigation.**

| Detail | Information |
| :--- | :--- |
| **Course** | Técnicas Digitales – UNS (Digital Techniques) |
| **Term** | 2nd Semester, 2025 |
| **Authors** | Contreras Gerónimo, Castro Facundo Nicolás |

---

## 📘 Project Description

This project focuses on implementing a **sequential** logic system for controlling the movement of an autonomous vehicle, applying the navigation strategy known as the **"Right-Hand Rule"** (wall-following).

The core of the system is a **Moore-type Finite State Machine (FSM)**, designed to:

1.  Interpret signals from **two proximity sensors** (Left and Right).
2.  Generate control signals for **two independent motors**.

The entire design was validated using **real digital circuits** (JK Flip-Flops, AND/Inverter gates) both in simulation and on physical hardware (breadboard), and finally mounted on the vehicle. 

---

## 🎯 Main Objectives

* **Design** a robust and efficient FSM capable of navigating a maze-like environment.
* **Model** the system by deriving the state transition table and its encoded version.
* **Optimize** the circuit using K-Maps to derive the excitation equations for the **JK Flip-Flops**.
* **Implement** the combinational and sequential logic using Integrated Circuits (ICs).
* **Validate** the functionality in simulation, on a breadboard, and finally, in a real navigation test.

---

## 🧠 System Modeling: Inputs and Outputs

The FSM operates with 2 input bits ($I_S I_D$) from the sensors and 2 output bits ($M_I M_D$) to control the motors.

### Inputs – Sensors

| $I_S I_D$ | Reading | Interpretation |
| :---: | :---: | :--- |
| **00** | Front | Wall in front |
| **01** | Left | Left wall detected |
| **10** | Right | **Right wall detected** |
| **11** | Clear | Open path |

### Outputs – Motors

| $M_I M_D$ | Action |
| :---: | :--- |
| **11** | **Move Forward** (Full speed) |
| **01** | **Turn Left** |
| **10** | **Turn Right** |
| **00** | **Stop** |

---

## 📐 State Machine Design

A **Moore-type FSM** with **four (4) main states** was used.

| State | Symbol | Output Action ($M_I M_D$) |
| :---: | :---: | :--- |
| **A** | $Q_1 Q_0 = 11$ | Move Forward |
| **B** | $Q_1 Q_0 = 01$ | Turn Left |
| **C** | $Q_1 Q_0 = 10$ | Turn Right |
| **D** | $Q_1 Q_0 = 00$ | Stop |

> The design was encoded with 2 bits ($log_2 4 = 2$), allowing the sequence to be implemented with a single **74107 Dual JK Flip-Flop** IC.

### 🧩 Tables and Equations

The design process included generating the:
* State Transition Table **(STT)**.
* **JK Flip-Flop** Excitation Table.
* **Karnaugh Maps** for the excitations ($J_0, K_0, J_1, K_1$) and the outputs ($M_I, M_D$). 
* Derivation of the **simplified** logic equations.

Thanks to the choice of a Moore Machine, significant optimization was achieved: the final circuit only required **3 external logic gates** in addition to the 74107 IC.

---

## 🔌 Circuit Implementation

### Components Used

* 1× **74107** (Dual JK Flip-Flops)
* 1× **7404/7414** (Inverters)
* 1× **DM7408** (2-input AND $\times4$)
* Breadboard and power supply (+5 V)
* Switches (simulated sensors)
* LEDs (simulated motors)
* Push button for the CLOCK signal

### Etapas de Desarrollo

1.  Logic Design and Modeling.
2.  Digital Simulation (State transition verification).
3.  Implementation on **Breadboard** and state transition testing.
4.  **Mounting** on the physical vehicle. 
5.  Final test in a maze environment $\rightarrow$ **Successfully passed**.

---

## 🚀 Results and Conclusions

The designed FSM operated **correctly and predictably** in both simulation and real hardware.

* The efficiency of the "Right-Hand Rule" strategy was confirmed by following the rules encoded in the FSM.
* An analysis of the advantages and disadvantages (trade-offs) of design between **Moore vs. Mealy** architectures was performed in a real engineering context.
* It was validated that logic simplification based on K-Maps is crucial for achieving physically optimized implementations in terms of components.
