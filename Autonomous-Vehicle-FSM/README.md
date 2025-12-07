**🚗 Sequential Controller for Autonomous Vehicle (FSM)**

🌐 **Project Summary**

This project documents the design, simulation, and physical implementation of a **Moore Finite State Machine (FSM)** used to autonomously control a vehicle. The core function is to implement the **"Right-Hand Rule"** navigation strategy in a maze environment.

The system translates inputs from two proximity sensors into control signals for two independent motors. The final implementation was built using real Digital ICs (Flip-Flops, AND, Inverters) and tested on a physical prototype vehicle.

### 🛠️ Key Components & Technologies

| Aspect | Detail |
| :--- | :--- |
| **System** | FSM, Moore Type (4 States) |
| **IC Used** | 1× 74107 (JK Flip-Flops), 7404/7414, 7408 |
| **Logic Design** | K-Maps for Excitation and Output Equations |
| **Strategy** | Right-Hand Rule (Wall Following) |
| **Results** | Successful navigation in real-world labyrinth testing. |

## 🔗 Project Files

* **`./diagrams`**: State Transition Diagram, Excitation Tables, and K-Maps.
* **`./code`**: Logic equations and simulation files.
* **`./DOCS/README-ES.md`**: Full academic description of the project (in Spanish).
* * **`./DOCS/README-EN.md`**: Full academic description of the project (in English).

---

## 👨‍💻 Authors

* Contreras Gerónimo
* Castro Facundo Nicolás
* Course: Técnicas Digitales – UNS (2º Cuat. 2025)
