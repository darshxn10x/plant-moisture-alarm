# 🌿 SproutSense: Arduino Plant Moisture Alarm

A beginner-friendly IoT project that monitors plant soil moisture, sounds an alarm when your plant is thirsty, and provides a nature-inspired phone dashboard UI.

---

## 📱 Dashboard UI Features

- **Large Current Reading**: High-contrast, easy-to-read numeric display (e.g. `42%`).
- **Clear Status Labels**: Three intuitive zones:
  - 💧 **Needs water** (`< 30%`): Parched soil, triggers warning chirp.
  - 🌱 **Healthy** (`30% – 65%`): Optimal dampness and root aeration.
  - 🌊 **Too wet** (`> 65%`): Saturated soil, prompts drainage check.
- **Semicircular Moisture Gauge**: Color-coded zones (Low, Healthy, High) with an animated indicator needle.
- **Friendly Plant Avatar**: Responsive illustration ("Monty" the Monstera) that smiles when hydrated and looks thirsty when dry.
- **Contextual Care Tips**: Dynamic, beginner-oriented guidance based on live readings.
- **12-Hour History Sparkline**: Recent moisture trend line with optimal baseline bounds.
- **Connection Pill & Ticker**: Real-time Arduino connection indicator and last-updated timestamp.
- **Interactive Simulator + USB Web Serial**: Test with quick preset buttons or connect a real Arduino via USB in Google Chrome or Microsoft Edge with zero server setup!

---

## 🛠️ Hardware Components

| Component | Quantity | Description |
|---|---|---|
| **Arduino Uno / Nano** | 1 | Microcontroller board |
| **Capacitive Soil Moisture Sensor v1.2** (or Resistive) | 1 | Reads volumetric water content in soil (Analog) |
| **Piezo Buzzer** | 1 | Emits gentle alert chirps when plant is dry |
| **LED + 220Ω Resistor** | 1 | Optional visual alarm (or uses built-in Pin 13 LED) |
| **Jumper Wires & Breadboard** | 1 set | For solderless connections |

---

## 🔌 Wiring Diagram

```
Arduino Pin       Connected To
-----------------------------------------------
5V             -> Sensor VCC
GND            -> Sensor GND & Buzzer (-) & LED Cathode
A0             -> Sensor Analog Out (AOUT)
Digital Pin 8  -> Buzzer (+)
Digital Pin 13 -> 220Ω Resistor -> LED Anode (+)
```

---

## ⚙️ Sensor Calibration

Every sensor and soil type has slightly different raw analog values:

1. Open `arduino/plant_moisture_alarm.ino` in the Arduino IDE.
2. Hold the sensor dry in the air. Open the Serial Monitor at **9600 baud** and read the raw analog value (typically `~750–820`). Set this as `DRY_AIR_VALUE`.
3. Dip the sensor probe into a glass of tap water (up to the white line). Note the raw reading (typically `~300–350`). Set this as `WET_WATER_VALUE`.
4. Upload the sketch to your board!

---

## 🚀 Running the Dashboard

### Option A: Direct Browser Launch
1. Double-click `index.html` or open it with any web browser.
2. Use the **Manual Moisture Slider** or quick preset buttons (`Dry 22%`, `Healthy 42%`, `Wet 78%`) to explore the interface and test the alarm sound.

### Option B: Real USB Web Serial (Chrome / Edge)
1. Plug your Arduino into your computer via USB.
2. Make sure the Arduino IDE Serial Monitor is closed (so the USB port is free).
3. Open `index.html` in Chrome or Edge and click **"Connect Arduino USB (Web Serial)"**.
4. Select your Arduino's serial port (e.g. `COM3` on Windows, or `/dev/tty.usbmodem...` on macOS/Linux).
5. The dashboard will immediately stream live sensor data and update in real time!