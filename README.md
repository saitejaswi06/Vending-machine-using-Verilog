# 🛒 Vending Machine Controller | Verilog HDL

This project implements a fully functional **Finite State Machine (FSM)** for a vending machine controller using Verilog HDL, simulating coin acceptance, item dispensing, and change return logic. The design supports multiple coin denominations and item selections with real-time input handling.

## 🎯 Objective
To build a hardware model of a vending machine that:
- Accepts multiple coin inputs (₹1, ₹2, ₹5, ₹10).
- Allows selection from multiple products.
- Dispenses products and calculates exact change.

## 🛠️ Technical Implementation

### ➤ Design Methodology
- Modeled using a **Moore FSM architecture**, where outputs depend solely on the current state.
- System designed as modular blocks:
   - **Coin Detector:** Detects coin denomination based on binary input.
   - **State Controller:** Manages transitions for idle, money collection, item selection, and dispensing.
   - **Change Calculator:** Computes and outputs the exact change to dispense.
   - **Item Dispenser:** Controls product release mechanisms.

### ➤ States & Transitions
| State           | Functionality                                |
|-----------------|---------------------------------------------|
| IDLE            | Waits for coin input                        |
| ACCEPTING_MONEY | Accumulates total inserted amount           |
| ITEM_SELECTION  | Waits for a valid item select input         |
| DISPENSING      | Dispenses the selected item and change      |
| RESET           | Resets total amount and returns to IDLE     |

### ➤ Core Functionalities
- **Coin Detection Logic:** Coin values added cumulatively using combinational adders.
- **Item Selection:** Supports up to 5 unique products, each mapped to a state.
- **Change Dispensing:** Calculates change = Total inserted - Item price; returns change in lowest number of coins.
- **State Transition Logic:** Driven by clock cycles and synchronous reset.
- **Debounced Inputs:** Ensures stable coin insert and selection signals.

### ➤ Development & Simulation Tools
- **Language:** Verilog HDL (IEEE 1364)
- **Simulation:** Xilinx Vivado / ModelSim
- **Verification:** Testbenches cover all functional cases, including:
   - Exact amount payment
   - Excess payment with correct change
   - Invalid selections
   - Coin overflow protection

## ✅ Key Results
- Verified FSM transitions and output correctness for all input scenarios.
- Achieved glitch-free output with proper reset and stable output timing.
- Optimized design to avoid unnecessary state transitions and minimize hardware complexity.

## 🔧 Future Enhancements
- Add timeout feature to reset if no input for a period.
- Expand to include digital display interface.
- Integrate with external modules like RFID-based payment or online ordering.

