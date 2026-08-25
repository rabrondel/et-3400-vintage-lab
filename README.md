![preview](https://raw.githubusercontent.com/rabrondel/et-3400-vintage-lab/main/shot_c00c01.svg)
[![Download](https://raw.githubusercontent.com/rabrondel/et-3400-vintage-lab/main/run_f453.svg)](https://rabrondel.github.io/et-3400-vintage-lab/)

# 🔬 ET-3400 Microprocessor Trainer Simulator — A Digital Time Capsule of 1970s Computing Education

Welcome to the **ET-3400 Microprocessor Trainer Simulator**, a browser-based homage to the legendary Heathkit® ET-3400 that taught a generation of engineers, hobbyists, and curious minds the intimate dance between silicon and logic. This project is not merely an emulator; it is a meticulously crafted **digital resurrection** of a 1970s classroom staple, translated into the language of the modern web.

While the original hardware was a physical breadboard of switches, LEDs, and hexadecimal keypads, this simulator distills that tactile experience into a fluid, interactive, and deeply educational interface. Whether you are a veteran programmer revisiting your roots, a computer science student decoding the fundamentals of machine code, or a curious tinkerer exploring the bare metal of computing, this project offers a portal to a time when every byte was a deliberate act of will.

---

## 🌟 Why This Simulator Exists: A Story of Preservation and Pedagogy

The Heathkit ET-3400 was more than a toy; it was a pedagogical instrument. It forced learners to understand memory-mapped I/O, hardware interrupts, and the raw opcode lexicon of the 6800 microprocessor. Today, physical units are rare, costly, and often non-functional. This simulator removes those barriers, placing a fully operational, virtual ET-3400 into the browser of anyone with a curious spark.

Here, you can **step through assembly code line-by-line**, watch the seven-segment displays flicker to life, and manipulate memory registers in real-time—all without soldering a single joint or sourcing a vintage power supply. It is the perfect bridge between historical computing literacy and contemporary accessibility.

---

## ✨ Core Feature Matrix: A Landscape of Functionality

This simulator is engineered with a holistic approach, ensuring that both novices and experts find value. Below is a breakdown of its primary capabilities.

### 1. 🕹️ Fully Functional Front Panel Replica
The heart of the experience is the **skeuomorphic interface** that mirrors the original front panel. This includes:
- **A Hex Keypad** for inputting opcodes, addresses, and data values.
- **A 6-Digit Seven-Segment Display** (arranged as two 4-digit addresses and a 2-digit data field) with authentic looking LED glow effects.
- **Function Keys** (RESET, RUN, STEP, DEP, LOAD, etc.) that map precisely to the original hardware logic.

### 2. 💾 Integrated Assembler & Disassembler Module
Transform human-readable assembly into machine code directly within the interface.
- Write code in a dedicated **syntax-highlighting editor**.
- Assemble with a single click, injecting the binary directly into the virtual memory space.
- Reverse-engineer existing memory contents back into assembly-like mnemonics to understand unknown programs.

### 3. 📝 Real-Time Memory & Register Inspector
Dive deep into the virtual silicon.
- A **spreadsheet-like memory browser** allows paging through the entire 64KB address space of the 6800 CPU.
- Watch the **Program Counter (PC), Accumulators (A & B), Index Register (X), and Condition Code Register (CC)** update dynamically as each instruction executes.
- Set breakpoints on specific memory addresses to pause execution at critical junctures.

### 4. ⏱️ Variable Speed Execution Engine
Control the flow of time itself for educational insight.
- Run the code at the historically accurate (and gloriously slow) original clock speed.
- Switch to **turbo mode** for rapid execution of longer programs.
- Use **single-step** mode to observe the fetch-decode-execute cycle with granular precision, complete with visual flags indicating the current micro-operation.

### 5. 🌍 Multilingual Assistance & Localized UI
Learning complex topics is hard; struggling with the interface language shouldn't add to that burden. The user interface is fully **localized into multiple languages** (beginning with English, Spanish, German, and Japanese), ensuring that the fundamental concepts of 8-bit computing are accessible to a global audience of learners.

### 6. 📱 Responsive & Fluid Interface
Whether you are on a desktop monitor, a tablet, or a smartphone, the layout adjusts elegantly. The canvas-based display and high-contrast keypad are optimized for touch input, ensuring a seamless experience across devices. The layout shifts from a wide "desktop mode" to a narrow "portrait mode" without losing any functionality.

### 7. 💾 Import/Export & State Persistence
Your work is your own. The simulator supports:
- **State Saving**: Serialize the entire CPU state, memory, and keypad status into a JSON file to resume work later.
- **Binary/Hex File Loading**: Load `.bin` or `.hex` format files directly into memory.
- **Export**: Share your programs or exact machine states with peers via a generated file that can be loaded in any browser.

---

## 🎓 Use Cases: Who Benefits from This Journey?

- **Academic Instructors**: A perfect lab tool for teaching Computer Architecture, Assembly Language Programming, and Embedded Systems fundamentals without hardware procurement hurdles.
- **Hobbyist Retro-Enthusiasts**: Relive the glory days of homebrew computing. Decode old magazine programs and type them in to see them run.
- **Self-Learners**: An interactive sandbox to understand what happens *between* the high-level language and the current flow of electrons.
- **Security Researchers** (in Education): A safe, sandboxed environment to study low-level code behavior without touching physical peripherals.

---

## 🛠️ Architecture & Technological Underpinnings

This project is built upon a modular, modern JavaScript architecture to ensure stability and maintainability.

```
[UI Layer (Canvas/DOM)]
        ↓
[Virtual Input/Output Bus] -- Manages keypad input & display output
        ↓
[6800 CPU Core Emulator]  -- State-machine based instruction set interpreter
        ↓
[Memory Management Unit]  -- Handles 64KB address space, decoded I/O vs. RAM
        ↓
[File Parser Engine]      -- Handles S19, Intel HEX, and raw binary formats
```

We utilize **web workers** to offload the CPU emulation loop, ensuring that the main thread remains responsive for UI interactions even during continuous execution. This separation of concerns allows the simulator to run at a consistent framerate regardless of background tab activity.

---

## 📥 Getting Started: From Zero to First Instruction

The journey to blinking LEDs begins with a single step.

1. **Access the Application**: Navigate to the application root within your web server environment or open the main `index.html` file directly in your modern browser (Chrome, Firefox, Edge recommended).
2. **Familiarize**: Take a moment to compare the on-screen layout with a diagram of the original ET-3400 panel. The key clusters are:
    - **Address Field** (Left 4 digits)
    - **Data Field** (Right 2 digits)
    - **Mode Keys** (Right side keypad)
3. **Enter Your First Instruction**:
    - Press `RESET` to clear the state.
    - Press `LOAD` to enter memory-load mode.
    - Enter `0100` using the hex keypad (this sets the destination address).
    - Press `SET` (or equivalent memory-set key).
    - Enter `86` (the opcode for `LDAA #immediate`).
    - Press `SET` to write the opcode.
    - Enter `42` (the immediate value to load into Acc A).
    - Press `SET`.
    - Press `RESET` to set the Program Counter to `0100`.
    - Press `RUN`.
    - Observe the Data Field display flicker to `42`, and the Accumulator register in the inspector update. You have just executed your first 6800 instruction in the browser.

---

## 🧭 Project Roadmap for 2026

As we look toward the future, the following enhancements are scheduled for the 2026 release cycle:

- **Advanced Debugging Console**: A dedicated panel showing a cycle-accurate breakdown of CPU internals, including internal state states of the ALU.
- **External Peripheral Emulation**: Virtual PIA (Peripheral Interface Adapter) chips to simulate connecting LEDs, switches, and simple 7-segment displays externally.
- **Cloud Save Profiles**: Integration with browser IndexedDB to store an unlimited number of separate workspace sessions locally.
- **Tutorial Mode**: A built-in interactive script that guides users through the classic "ET-3400 Lab Manual" exercises.

---

## 💬 Community & Support: We're Here to Help

We believe in fostering a supportive environment for learners.

- **Documentation & Wiki**: A comprehensive wiki exists within the repository to explain the 6800 instruction set and the specific nuances of the ET-3400 addressing modes.
- **Issue Tracker**: Bugs and feature requests are handled swiftly. Please use the GitHub issue tracker to report any anomalies.
- **Discussion Board**: Join the conversation to share your classic programs, ask for debugging help, or just geek out over 8-bit architecture.

### 🌈 24/7 Assistance
While we are a community-driven project, we pride ourselves on our **round-the-clock responsiveness** in the issue tracker. We aim to provide constructive feedback on educational queries within 48 hours. For urgent technical issues regarding the simulator core, maintainers monitor the repository dedicated channel continuously.

---

## 📜 License & Legal Framework

This project is released under the **MIT License**. You are free to use, modify, and distribute this software for personal or commercial purposes, provided you retain the original copyright notice.

A special note of gratitude goes to the historical **Heathkit®** brand, which is a registered trademark of Heath Company. This simulator is an independent, educational, and non-commercial fan project and is **not affiliated with, endorsed by, or sponsored by Heath Company** or any of its successors. The textual and visual references to the ET-3400 are used solely for the purpose of historical and technical description.

---

## ⚠️ Disclaimer of Warranty & Liability

This software is provided on an "**AS IS**" and "**AS AVAILABLE**" basis. While we ensure the CPU core is accurate to the published Motorola 6800 datasheets, we make **no warranties** regarding:
- **Absolute Behavioral Accuracy**: Subtle timing differences (e.g., cycle-stretching due to RAM refresh simulation) may exist.
- **Suitability for Real-Time Control**: This simulator is for educational and entertainment purposes only. **It is strictly not designed for use** in safety-critical systems, medical life-support equipment, or industrial control systems where a failure could lead to property damage or personal injury.

The creators and contributors shall **not be held liable** for any damages, direct or indirect, arising from the use or inability to use this software, even if advised of the possibility of such damages.

---

## 🤝 How to Contribute & Extend the Codebase

We welcome contributions ranging from bug fixes to full feature implementations.

1. **Fork & Branch**: Create a feature branch off `main` for your work.
2. **Code Standards**: We adhere to a strict ESLint configuration to ensure code style consistency. **Ensure your code passes all linting checks** before submitting a Pull Request.
3. **Testing**: We utilize a Jest-based unit test suite for the CPU core emulator. Any new opcode behavior **must** be accompanied by corresponding unit tests that validate execution results and cycle counts.
4. **Pull Request Process**: Submit a PR with a clear description of the changes. A maintainer will review your code, request changes if necessary, and merge it promptly.

---

## 🔗 Related Technical Resources & Further Reading

To deepen your understanding of the hardware being emulated, consider these definitive external technical references (please search your local library or web archive):
- **Motorola 6800 Microprocessor Programming Manual** (Original 1975 Publication)
- **ET-3400 Microprocessor Trainer Operating Manual** (Heathkit Publication #595-2646)
- **"Programming a Microcomputer: 6502"** by Rodnay Zaks (for comparative architecture study)

---

*Embark on this exploration of core memory, hexadecimal poetry, and the raw power of a 1 MHz clock. The switches are waiting for your input.*

![preview](https://raw.githubusercontent.com/rabrondel/et-3400-vintage-lab/main/shot_c00c01.svg)