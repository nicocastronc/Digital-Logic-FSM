# 🇪🇸 Documentación Completa del Proyecto

## 🚗 Controlador Secuencial para Vehículo Autónomo

**Diseño, simulación e implementación física de una Máquina de Estados Finitos (FSM) para la navegación autónoma.**

| Detalle | Información |
| :--- | :--- |
| **Materia** | Técnicas Digitales – UNS |
| **Cuatrimestre** | 2º Cuatrimestre, 2025 |
| **Autores** | Contreras Gerónimo, Castro Facundo Nicolás |

---

## 📘 Descripción del Proyecto

Este proyecto se centra en la implementación de un sistema lógico **secuencial** para el control de movimiento de un vehículo autónomo, aplicando la estrategia de navegación conocida como **"mantener la pared a la derecha"** (Right-Hand Rule).

El núcleo del sistema es una **Máquina de Estados Finitos (FSM) de tipo Moore**, diseñada para:

1.  Interpretar las señales de **dos sensores de proximidad** (Izquierdo y Derecho).
2.  Generar las señales de control para **dos motores independientes**.

Todo el diseño se validó mediante **circuitos digitales reales** (Flip-Flops JK, compuertas AND/Inversoras) tanto en simulación como en hardware físico sobre protoboard y, finalmente, montado en el vehículo.

---

## 🎯 Objetivos Principales

* **Diseñar** una FSM robusta y eficiente, capaz de navegar un entorno tipo laberinto.
* **Modelar** el sistema obteniendo la tabla de transición de estados y su versión codificada.
* **Optimizar** el circuito mediante K-Maps para derivar las ecuaciones de excitación de los **Flip-Flops JK**.
* **Implementar** la lógica combinacional y secuencial utilizando Circuitos Integrados (CI).
* **Validar** el funcionamiento en simulación, protoboard y, finalmente, en una prueba real de navegación.

---

## 🧠 Modelado del Sistema: Entradas y Salidas

La FSM trabaja con 2 bits de entrada ($I_S I_D$) provenientes de los sensores y 2 bits de salida ($M_I M_D$) para controlar los motores.

### Entradas – Sensores

| $I_S I_D$ | Lectura | Interpretación |
| :---: | :---: | :--- |
| **00** | Frente | Pared enfrente |
| **01** | Izquierda | Pared izquierda |
| **10** | Derecha | **Pared derecha** |
| **11** | Libre | Vía libre |

### Salidas – Motores

| $M_I M_D$ | Acción |
| :---: | :--- |
| **11** | **Avanzar** (Velocidad plena) |
| **01** | **Girar Izquierda** |
| **10** | **Girar Derecha** |
| **00** | **Parar** |

---

## 📐 Diseño de la Máquina de Estados

Se utilizó una **FSM de tipo Moore** con **cuatro (4) estados** principales.

| Estado | Símbolo | Acción de Salida ($M_I M_D$) |
| :---: | :---: | :--- |
| **A** | $Q_1 Q_0 = 11$ | Avanzar |
| **B** | $Q_1 Q_0 = 01$ | Girar izquierda |
| **C** | $Q_1 Q_0 = 10$ | Girar derecha |
| **D** | $Q_1 Q_0 = 00$ | Parar |

> El diseño se codificó con 2 bits ($log_2 4 = 2$), permitiendo la implementación de la secuencia con un único CI **74107 (Flip-Flop JK Dual)**.

### 🧩 Tablas y Ecuaciones

El proceso de diseño incluyó la generación de:
* Tabla de Transición de Estados **(TEE)**.
* Tabla de Excitación de **Flip-Flops JK**.
* **Mapas de Karnaugh** para las excitaciones ($J_0, K_0, J_1, K_1$) y las salidas ($M_I, M_D$).
* Derivación de las ecuaciones lógicas **simplificadas**.

Gracias a la elección de la Máquina de Moore, se logró una gran optimización: el circuito final requirió **solo 3 compuertas lógicas externas** además del integrado 74107.

---

## 🔌 Implementación del Circuito

### Componentes Utilizados

* 1× **74107** (Flip-Flops JK Duales)
* 1× **7404/7414** (Inversores)
* 1× **DM7408** (AND de 2 entradas $\times4$)
* Protoboard y fuente de alimentación (+5 V)
* Interruptores (Simulación de sensores)
* LEDs (Simulación de motores)
* Pulsador para la señal de CLOCK

### Etapas de Desarrollo

1.  Diseño Lógico y Modelado.
2.  Simulación Digital (Verificación de las transiciones).
3.  Implementación en **Protoboard** y pruebas de transición de estados.
4.  **Montaje** sobre el vehículo real.
5.  Prueba final en un entorno de laberinto $\rightarrow$ **Superada Exitosamente**.

---

## 🚀 Resultados y Conclusiones

La FSM diseñada operó de manera **correcta y predecible** tanto en simulación como en hardware real, permitiendo que el vehículo cumpliera exitosamente el algoritmo de navegación.

* Se confirmó la eficacia de la estrategia "mantener la pared a la derecha" al seguir las reglas codificadas en la FSM.
* Se realizó un análisis de las ventajas y desventajas (trade-offs) de diseño entre las arquitecturas **Moore vs. Mealy** en un contexto de ingeniería real.
* Se validó cómo la simplificación lógica basada en K-Maps es crucial para obtener implementaciones físicas optimizadas en cuanto a componentes.
