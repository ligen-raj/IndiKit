---
title: "IndiKit"
abstract: "A lightweight, SwiftUI-native toolkit for building customizable status indicators (battery, Wi-Fi, signal, sound, and more)."
---

# ``IndiKit``

IndiKit is a small, modular SwiftUI framework that provides a collection of reusable, animated status indicators — battery, Wi-Fi, cellular signal, sound level, and more — with customizable colors, sizes, and styles. It's designed to be SwiftUI-first and easy to integrate into apps, widgets, and dashboards.

## Overview

IndiKit focuses on three goals:

- **Composability:** Each indicator is a lightweight SwiftUI `View` that can be used directly or composed inside larger UIs.  
- **Customizability:** Configure colors, shapes, sizes, animation behavior, and indicator styles through a simple API.  
- **Portability:** Works as a framework or Swift package; example app provided for previews.

### Key components
- ``IndiKit/BatteryIndicator`` — a configurable battery level view with charging state and color thresholds.  
- ``IndiKit/WiFiIndicator`` — visualizes Wi-Fi signal strength and connection state.  
- ``IndiKit/SignalIndicator`` — cellular/signal bars with customizable number of bars and thresholds.  
- ``IndiKit/SoundIndicator`` — shows volume level and mute state.  
- ``IndiKit/IndicatorStyle`` — shared style configuration used across indicators (size, stroke, cornerRadius, animation options).

---

## Topics

### Getting Started

A minimal example of using a battery indicator in SwiftUI:

```swift
import SwiftUI
import IndiKit

struct ContentView: View {
    @State private var level: Double = 0.72

    var body: some View {
        VStack(spacing: 20) {
            BatteryIndicator(level: level)
                .indicatorStyle(.init(size: CGSize(width: 120, height: 40),
                                     fillColors: [.green, .yellow, .red]))
                .padding()

            WiFiIndicator(strength: 3, maxBars: 4)
                .indicatorStyle(.compact)

            SoundIndicator(level: 0.6, muted: false)
                .frame(width: 44, height: 44)

            Slider(value: $level)
                .padding()
        }
        .padding()
    }
}

