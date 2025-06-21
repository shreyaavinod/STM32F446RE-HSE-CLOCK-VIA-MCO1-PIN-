# STM32F4 - Output HSE Clock via MCO1 (PA8)

This project demonstrates how to configure an STM32F446RE microcontroller to output the **HSE clock** via **MCO1** pin (PA8) using **direct register programming** (no HAL).

## 🔧 What it Does

- Enables the external high-speed oscillator (HSE)
- Bypasses HSE with an external clock source (ST-Link or crystal)
- Waits for HSE to stabilize
- Selects HSE as the MCO1 output clock
- Configures GPIOA pin 8 (PA8) to **Alternate Function 0 (AF0)** to output the MCO1 signal
- Outputs raw HSE clock to PA8 — can be viewed using a logic analyzer or Arduino

---

## 📍 Pin Used

| Pin   | Function        |
|--------|------------------|
| PA8   | MCO1 Output (AF0) |

---

## 🧠 How it Works (Registers)

- `RCC_CR` → Enable HSE and set bypass mode
- `RCC_CFGR` → Select HSE as the MCO1 source (`MCO1[22:21] = 01`)
- `GPIOA_MODER` → Set PA8 to Alternate Function Mode (`10`)
- `GPIOA_AFRH` → Set PA8 to AF0 (MCO1)

---

## 🧪 How to Observe Output

- Connect PA8 to an oscilloscope or logic analyzer
- If you want to slow the clock down:
  - Add a prescaler in `RCC_CFGR` (`MCO1PRE[26:24]`)
- Alternatively, you can connect PA8 to an Arduino analog pin, sample the waveform, and plot it via UART/SerialPlot

---

## 💻 Requirements

- STM32F446RE (Nucleo-64)
- STM32CubeIDE
- External clock (ST-Link clock or crystal)
- Logic Analyzer / Oscilloscope / Arduino

---


