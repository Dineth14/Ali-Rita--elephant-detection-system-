# 🐘 ESP32 Elephant Detection System - Visual Flow

**Author:** Dineth Perera  
**License:** MIT License (see LICENSE file)  
**Version:** 2.0

# ESP32 Elephant Detection System - Visual System Flow

## System Architecture Overview

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    🐘 ESP32 ELEPHANT DETECTION SYSTEM                          │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                 │
│  ┌─────────────┐    ┌──────────────┐    ┌─────────────┐    ┌─────────────────┐  │
│  │  HARDWARE   │ ── │   SIGNAL     │ ── │  MACHINE    │ ── │  MODERN GUI     │  │
│  │   LAYER     │    │  PROCESSING  │    │  LEARNING   │    │   INTERFACE     │  │
│  │             │    │              │    │             │    │                 │  │
│  │ 🎤 Analog   │    │ 📊 8D Audio  │    │ 🧠 k-NN     │    │ 🎨 GitHub Theme │  │
│  │   Mic       │    │   Features   │    │   Classifier│    │ 📱 3-Column     │  │
│  │ 🔧 ESP32    │    │ ⚡ Real-time │    │ 🎯 Binary   │    │ 🚀 66 FPS       │  │
│  │   GPIO34    │    │   1kHz       │    │   Detection │    │ 📊 Status Bar   │  │
│  └─────────────┘    └──────────────┘    └─────────────┘    └─────────────────┘  │
│                                                                                 │
└─────────────────────────────────────────────────────────────────────────────────┘
```

## Modern GUI Architecture

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                           🎨 MODERN GUI LAYOUT                                 │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                 │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │                    🐘 ELEPHANT DETECTION SYSTEM                         │   │
│  │                 Real-time AI • High Performance • Modern Design         │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                 │
│  ┌──────────────────┐  ┌──────────────────┐  ┌─────────────────┐              │
│  │  🔗 CONNECTION   │  │  🎯 LIVE         │  │  🎛️ CONTROLS    │              │
│  │     STATUS       │  │   DETECTION      │  │                 │              │
│  │                  │  │                  │  │  📊 System      │              │
│  │ 🔄 Auto Connect  │  │ ⏳ INITIALIZING │  │     Status      │              │
│  │ 📋 Manual        │  │                  │  │                 │              │
│  │ ❌ Disconnect    │  │ 🎯 Classification│  │ 📊 Get Status   │              │
│  │ 🔍 Scan          │  │ 📊 Confidence    │  │ 💾 Save Data    │              │
│  └──────────────────┘  └──────────────────┘  └─────────────────┘              │
│                                                                                 │
│  ┌─────────────────────────────────────────┐  ┌─────────────────┐              │
│  │           📊 AUDIO FEATURES             │  │  📝 DETECTION   │              │
│  │          4x2 Color-Coded Grid           │  │      LOG        │              │
│  │                                         │  │                 │              │
│  │ 🔊 RMS     📈 Centroid  🌊 Infrasound  │  │ Real-time       │              │
│  │ 📊 Low     📉 Mid       🎵 Dominant    │  │ detection       │              │
│  │ ⏱️ Envelope 🌀 Flux                    │  │ events with     │              │
│  │                                         │  │ timestamps      │              │
│  └─────────────────────────────────────────┘  └─────────────────┘              │
│                                                                                 │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │ 🚀 System Ready • ⚡ Connected • 📊 66 FPS • 🎯 Real-time Processing │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                 │
└─────────────────────────────────────────────────────────────────────────────────┘
```

## Real-Time Signal Processing Flow

### 1. 🎤 High-Performance Audio Capture Chain
```
🐘 Elephant Sound Wave (10-200Hz)
       │ Environmental Capture
       ▼
┌───────────────┐
│ Analog Mic    │ ◄── 3.3V Bias Voltage
│ (Electret)    │     High-sensitivity for infrasound
└───────────────┬──────────────┘
                │ AC Signal (0.1-3.0V)
                ▼
┌───────────────┐
│  🚀 ESP32 ADC  │ ◄── 12-bit Resolution
│   GPIO34      │      0-4095 counts
└───────────────┬──────────────┘      ⚡ 1kHz High-Speed Sampling
                │ Digital Values
                ▼
┌───────────────┐
│ 📊 Real-time  │ ◄── 1ms intervals
│ Sample Rate   │      Interrupt-driven precision
│ Controller    │
└───────────────┬──────────────┘
                │
                ▼
```

### 2. 🧠 Digital Signal Processing Pipeline
```
Raw ADC Sample (12-bit)
                │
                ▼
┌───────────────┐
│  📐 DC Offset  │ ◄── Learn DC bias first 1000 samples
│   Removal     │     Center signal around zero
└───────────────┬──────────────┘
                │ Centered Signal
                ▼
┌───────────────┐
│  🔧 Low-Pass   │ ◄── 200Hz cutoff, preserves elephant infrasound
│    Filter     │     Remove high-freq noise, keep 0-200Hz
└───────────────┬──────────────┘     y[n] = αx[n] + (1-α)y[n-1]
                │ Clean Signal (Full Elephant Range)
                ▼
┌───────────────┐
│ 🔄 Circular    │ ◄── 256 samples (256ms)
│   Buffer       │     Overwrite oldest for real-time
│   Storage      │
└───────────────┬──────────────┘
                │ Frame Ready (256 samples)
                ▼
```

### 3. 🎯 Advanced Feature Extraction Process
```
Complete Audio Frame (256 samples)
                │
                ▼
┌───────────────┐
│ 📊 Hamming     │ ◄── Reduce spectral leakage
│   Window       │     w[n] = 0.54 - 0.46*cos(2πn/N)
│ Application    │
└───────────────┬──────────────┘
                │ Windowed Frame
                ├───────────────────────────────┬───────────────────────────────┬───────────────────────────────┐
                ▼                               ▼                               ▼
┌───────────────┐   ┌───────────────┐   ┌───────────────┐
│   🔊 TIME     │   │ 📈 FREQUENCY  │   │   🌊 SPECTRAL │
│    DOMAIN     │   │    DOMAIN     │   │    FEATURES   │
│   FEATURES    │   │  PROCESSING   │   │               │
└───────────────┬───┘   └───────────────┬───┘   └───────────────┬───┘
                │                               │                               │
                ▼                               ▼                               ▼
┌───────────────┐   ┌───────────────┐   ┌───────────────┐
│ 1. 🔊 RMS     │   │ ⚡ Fast       │   │ 4. 📈 Spectral│
│    Energy     │   │   Fourier     │   │    Centroid   │
│    √(Σx²/N)   │   │   Transform   │   │ Σ(f*E)/Σ(E)  │
│               │   │   (FFT)       │   │               │
│ 2. ⏱️ Temporal │   │ 256→128 bins  │   │ 5-7. 📊 Band  │
│    Envelope   │   │ 10–200Hz      │   │     Energies  │
│               │   │ range         │   │   High)       │
└───────────────┘   └───────────────┬───┘   └───────────────┬───┘
                │                               │                 │
                ▼                               ▼                 ▼
┌───────────────┐   ┌───────────────┐   ┌───────────────┐
│ 🌊 Infrasound │   │ 📊 Low Band   │   │ 📈 Mid Band   │
│   10–40Hz     │   │   40–100Hz    │   │   100–200Hz   │
└───────────────┘   └───────────────┘   └───────────────┘
                │
                ▼
┌───────────────┐   ┌───────────────┐
│ 🎵 Dominant   │   │ 8. 🌀 Spectral│
│   Frequency   │   │     Flux      │
└───────────────┘   └───────────────┘
                │
                ▼
┌───────────────────────────────────────────────┐
│        🎯 8D FEATURE VECTOR                   │
│ [RMS, Centroid, Infrasound, Low, Mid,         │
│  Dominant, Envelope, Flux] = 8 dimensions     │
└───────────────────────────────────────────────┘
                │
                ▼
```

### 4. 🧠 Machine Learning Classification
```
Feature Vector [8D]
                │
                ▼
┌───────────────┐
│   🗄️ Training │ ◄── Stored in SPIFFS flash
│    Database   │     Labeled feature vectors
└───────────────┬──────────────┘     JSON format
                │ Compare with all stored samples
                ▼
┌───────────────┐
│   📏 Distance │ ◄── Euclidean distance
│  Calculation  │     d = √Σ(fi - ti)²
└───────────────┬──────────────┘     i = 1 to 8 features
                │ Distance array
                ▼
┌───────────────┐
│   🎯 K-Nearest│ ◄── K=3 (configurable)
│   Neighbors   │     Sort by distance
└───────────────┬──────────────┘     Take closest K samples
                │ K closest samples
                ▼
┌───────────────┐
│   🗳️ Majority │ ◄── Count votes per label
│    Voting     │     Winner = most votes
└───────────────┬──────────────┘     Confidence = votes/K
                │ Classification + Confidence
                ▼
┌───────────────┐
│   🎯 Result   │ ◄── Label string + score
│   Output      │     "elephant" or "not_elephant"
└───────────────┬──────────────┘
                │
                ▼
```

### 5. 🚀 Communication and Output
```
Classification Result
                │
                ▼
┌───────────────┐
│   📡 Serial   │ ◄── Format: "FEATURES:..."
│   Protocol    │     115200 baud UART
└───────────────┬──────────────┘     ASCII text protocol
                │ Serial data stream
                ▼
┌───────────────┐
│   🔗 USB Cable│ ◄── ESP32 ↔ Computer
│   Connection  │     Virtual COM port
└───────────────┬──────────────┘
                │ USB Serial
                ▼
┌───────────────┐
│ 🎨 GUI Interface │ ◄── Modern GUI @ 66 FPS
│   Modern GUI  │     GitHub-inspired theme
└───────────────┬──────────────┘     3-column layout
                │ Real-time visualization
                ▼
┌───────────────┐
│ 📊 Live Status│ ◄── Status bar + feature cards
│   Display     │     Color-coded indicators
└───────────────┘

Serial Out:                                       █▓▓▓▓▓
                                                  │◄►│
                                                  TX

Legend: ████ Active Processing    ▓▓▓▓ Idle Time
```

### 📊 Processing Load Distribution
```
┌─────────────────────────────────────────────────────────────┐
│               🚀 ESP32 CPU UTILIZATION                     │
├─────────────────────────────────────────────────────────────┤
│ ⚡ Sampling (1kHz):      ████████████████ 45%              │
│ 🌊 Digital Filtering:    ████████ 25%                      │
│ 🎯 Feature Extraction:   ██████ 20%                        │
│ 🧠 ML Classification:    ████ 10%                          │
│ 📡 Serial Communication: ██ 8%                             │
│ ⚙️ System Overhead:      ██ 5%                             │
├─────────────────────────────────────────────────────────────┤
│ 🚀 TOTAL CPU USAGE:      ████████████████████████████ 70%  │
│ 💾 REMAINING CAPACITY:   ████████████ 30%                  │
└─────────────────────────────────────────────────────────────┘
```

## 🗄️ Memory Layout Diagram

### ESP32 Memory Map
```
┌─────────────────────────────────────────────────────────────┐
│                🚀 ESP32 MEMORY USAGE                       │
├─────────────────────────────────────────────────────────────┤
│ 💾 FLASH MEMORY (4MB):                                     │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ 🔧 Bootloader:        ████ 32KB                        │ │
│ │ 📋 Partition Table:   █ 4KB                            │ │
│ │ 💻 Application Code:  ████████████████████████ 100KB   │ │
│ │ 🗄️ SPIFFS Storage:    ████████████████████████████ 128KB │ │
│ │ 💿 Free Flash:        ████████████████████████████████...│ │
│ └─────────────────────────────────────────────────────────┘ │
│                                                             │
│ 🧠 RAM MEMORY (320KB):                                     │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ ⚙️ System/WiFi:       ████████████ 48KB                │ │
│ │ 📚 Application Stack: ████████ 32KB                    │ │
│ │ 🎵 Audio Buffers:     ████ 16KB                        │ │
│ │ 🧠 Training Data:     ████ 16KB                        │ │
│ │ 💾 Free RAM:          ████████████████████████████████..│ │
│ └─────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

## 🎯 Data Structure Flow

### Audio Data Journey
```
🎤 Raw Sound → 📊 ADC Values → 🌊 Filtered → 📦 Audio Frame → 🎯 Features → 🧠 Classification

uint16_t     int16_t        float         vector<float>   struct      string
[0-4095]     [-32768,       [-1.0, +1.0]  [256 samples]   {8 floats}  "elephant"/"not_elephant"
12-bit       +32767]        normalized     256ms window    features    + confidence %
```

### 🎵 Feature Vector Structure
```
AudioFeatures {
       float rms;                  // 🔊 Energy: 0.0 - 1.0
       float spectral_centroid;    // 📈 Hz: 0 - 200
       float infrasound_energy;    // 🌊 10–40 Hz
       float low_band_energy;      // 📊 40–100 Hz
       float mid_band_energy;      // 📈 100–200 Hz
       float dominant_freq;        // 🎵 Hz: 10–200
       float temporal_envelope;    // ⏱️ Max amplitude
       float spectral_flux;        // 🌀 Change: 0.0 - 1.0
}
```

## 🔄 State Machine Diagram

### System States
```
         ┌─────────────┐
         │ 🚀 STARTUP  │
         └──────┬──────┘
                │ Initialize hardware
                ▼
         ┌─────────────┐
         │ ⚙️ INIT     │ ◄── Load training data
         └──────┬──────┘     Setup filters
                │ Ready
                ▼
    ┌─────────────────────┐
    │ 🎤 SAMPLING         │ ◄─┐
    │   (Continuous)      │   │
    └──────┬──────────────┘   │
           │ Frame complete   │
           ▼                  │
    ┌─────────────────────┐   │
    │ 🎯 PROCESSING       │   │
    │  (Feature Extract)  │   │
    └──────┬──────────────┘   │
           │ Features ready   │
           ▼                  │
    ┌─────────────────────┐   │
    │ 🧠 CLASSIFICATION   │   │
    │    (k-NN Predict)   │   │
    └──────┬──────────────┘   │
           │ Result ready     │
           ▼                  │
    ┌─────────────────────┐   │
    │ 📡 OUTPUT           │   │
    │   (Serial Send)     │   │
    └──────┬──────────────┘   │
           │ Continue         │
           └──────────────────┘

🚨 States can be interrupted by:
- 📡 Serial commands (LABEL, SAVE, etc.)
- ⚠️ Error conditions
- 🔄 System reset
```

## 🎨 Interactive GUI Flow

### Modern Python GUI Data Flow
```
🔗 ESP32 Serial → 🧵 Python Thread → 📦 Queue → 🎨 GUI Update → 👤 User Display

┌─────────────┐   ┌─────────────┐   ┌─────────────┐   ┌─────────────┐
│ 📡 Serial   │──▶│ 🧵 Reader   │──▶│ 📦 Data     │──▶│ 🎨 GUI      │
│   Port      │   │   Thread    │   │   Queue     │   │   Thread    │
│ (115200)    │   │ (Background)│   │ (Thread     │   │ (tkinter)   │
│             │   │             │   │  Safe)      │   │             │
└─────────────┘   └─────────────┘   └─────────────┘   └─────────────┘
                                                               │
                                                               ▼
┌─────────────────────────────────────────────────────────────────────┐
│                  🎨 GUI COMPONENTS                                 │
├─────────────────────────────────────────────────────────────────────┤
│ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐   │
│ │ 📊 Feature  │ │ 🎯 Live     │ │ 📋 Detection│ │ 🎛️ Control  │   │
│ │   Display   │ │   Status    │ │   History   │ │   Panel     │   │
│ │ (4x2 Grid)  │ │ (Real-time) │ │ (Scrolling) │ │ (Status)    │   │
│ └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘   │
│                                                                     │
│ ┌─────────────────────────────────────────────────────────────┐   │
│ │ 🚀 Status: Connected • 66 FPS • Real-time Processing       │   │
│ └─────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────┘
                                   │
🎯 User Actions:          ▼
• 🏷️ Label sounds ──────────▶ Send "LABEL:elephant" or "LABEL:not_elephant"
• 💾 Save data ─────────────▶ Send "SAVE_DATA"  
• 🗑️ Clear data ────────────▶ Send "CLEAR_DATA"
• 📊 Get status ────────────▶ Real-time system monitoring
                          │
                          ▼
              🚀 Real-time Updates every 15ms (66 FPS)
                   Professional Performance & Modern UI
```

---

**🐘 ESP32 Elephant Detection System**  
*Real-time AI • Professional Performance • Modern Design • GitHub-inspired Theme*
                          ▼
                   ESP32 Serial Input
```

This comprehensive visual flow shows exactly how every component of the ESP32 Noise Logger system works together, from sound waves to final classification output!