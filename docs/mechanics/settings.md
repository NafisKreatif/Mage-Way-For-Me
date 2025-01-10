# Documentation: Settings Menu

## Overview
This document provides an overview of three interconnected C# scripts that collectively manage and control the settings menu for the game. These scripts include:
- **SettingsButtonSetter.cs**: Handles the interaction between buttons and canvases.
- **SettingsManager.cs**: Manages the settings data, saves it persistently, and synchronizes it with UI elements.
- **SettingsMenu.cs**: Controls specific settings-related operations, including volume adjustments using sliders.

---

## **1. SettingsButtonSetter.cs**

### Purpose
The `SettingsButtonSetter` script manages navigation between different UI canvases, particularly the settings menu. It ensures that the "Settings" button can toggle visibility of the settings canvas and the original canvas menu where it was opened from.


## **2. SettingsManager.cs**

### Purpose
`SettingsManager` is the core script for managing application settings. It persists settings across sessions and synchronizes them with UI elements.

### Interaction with Other Scripts
- Provides the settings canvas reference to `SettingsButtonSetter`.
- Synchronizes with sliders in `SettingsMenu`.

---

## **3. SettingsMenu.cs**

### Purpose
The `SettingsMenu` script handles specific settings operations, primarily related to audio. It uses sliders to adjust audio levels in real time.

## **Script Interactions**

### Initialization Flow
1. **`SettingsManager`**
   - Acts as the central manager for settings data and UI.
   - Provides references to other scripts (e.g., settings canvas for `SettingsButtonSetter`).

2. **`SettingsButtonSetter`**
   - Uses `SettingsManager` to retrieve the settings canvas and back button.
   - Handles navigation to and from the settings menu.

3. **`SettingsMenu`**
   - Reads initial settings from `PlayerPrefs` (saved by `SettingsManager`).
   - Synchronizes sliders with the saved settings.
   - Adjusts audio levels in real time using the Unity `AudioMixer`.

### User Interaction Flow
1. The user clicks a button (e.g., "Settings").
   - `SettingsButtonSetter` enables the settings canvas using the reference from `SettingsManager`.
2. The user adjusts a slider (e.g., master volume).
   - The slider triggers an event in `SettingsManager`, updating the internal settings dictionary and `PlayerPrefs`.
   - Simultaneously, `SettingsMenu` adjusts the audio mixer levels in real time.
3. The user clicks the back button.
   - `SettingsButtonSetter` disables the settings canvas and returns to the previous canvas.

---
