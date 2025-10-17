# STM32_4x4_Keypad_Checker

This repository contains example code to test a **4x4 keypad** with an **STM32 Blue Pill (F103C6T6A)** microcontroller using the **built-in LED on PC13** for feedback. The code is uploaded via **ST-Link V2** using **STM32CubeIDE v1.12.1** (the latest version caused code generation issues, so this stable version is used).

Testing the keypad first ensures that the input component works correctly before integrating it with other parts of your project. During testing, some **Blue Pill pins** were faulty or missing (e.g., B2 not available, B4 not working), which required rerouting connections like connecting **keypad R4 to STM32 A7**. Early component checks save you hours of pain so you don’t end up smashing your STM32 to pieces while tearing your hair out hunting for faults in every tiny component.

---

## Hardware Used

- STM32 Blue Pill (F103C6T6A)  
- 4x4 Keypad  
- Built-in LED (PC13)  
- ST-Link V2 Programmer  
- Jumper wires and breadboard  

---

## Circuit Connections

| Keypad Pin | STM32 Pin | Notes |
|------------|-----------|-------|
| R1         | PB0       | Output row |
| R2         | PB1       | Output row |
| R3         | PB3       | Output row |
| R4         | PA7       | Output row (rerouted from missing/faulty pin) |
| C1         | PB5       | Input column with Pull-up |
| C2         | PB6       | Input column with Pull-up |
| C3         | PB7       | Input column with Pull-up |
| C4         | PB8       | Input column with Pull-up |
| LED        | PC13      | Built-in LED for feedback |

---
## Circuit Diagram (Simplified)

        4x4 Keypad Layout
   -------------------------
   | 1 | 2 | 3 | A |   <- Columns Y1 Y2 Y3 Y4
   | 4 | 5 | 6 | B |
   | 7 | 8 | 9 | C |
   | * | 0 | # | D |
   -------------------------
Rows (Outputs) ----> STM32
X1 -> PB0
X2 -> PB1
X3 -> PB3
X4 -> PA7

Columns (Inputs, Pull-up) ----> STM32
Y1 -> PB5
Y2 -> PB6
Y3 -> PB7
Y4 -> PB8

Built-in LED ----> PC13

---

## Software

- **IDE:** STM32CubeIDE v1.12.1  
- **Code Language:** C  
- **Purpose:** Check keypad input functionality and LED feedback  

---

## Usage Instructions

1. Connect the hardware as per the circuit table.  
2. Open the project in STM32CubeIDE v1.12.1.  
3. Compile the code.  
4. Upload using **ST-Link V2**.  
5. Press keys on the 4x4 keypad; the built-in LED should indicate key detection.  

---

## Testing Recommendations

When testing the keypad, if any row or column does not respond:  
1. Check which pin is not working.  
2. Try changing the jumper wires to rule out loose connections.  
3. Connect the wire directly to the STM32 pin to ensure the connection is solid.  
4. If it still doesn’t work, the pin itself might be faulty, replace or reroute to another available pin as needed.  

Following this process helps identify faulty pins early and prevents troubleshooting headaches later.
