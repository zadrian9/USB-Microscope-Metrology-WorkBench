# USB Microscope Metrology & Inspection Studio

A browser-based metrology and visual inspection workbench for connecting to a USB microscope or webcam, calibrating the live view, performing geometric measurements, and tagging surface defects.

## Overview

`USB-Microscope-Metrology-WorkBench` is a self-contained single-file HTML5 application (`index.html`) that turns a standard USB microscope or camera into a calibrated inspection station directly in your web browser. It combines live video capture, 2-click spatial calibration, multi-tool geometric measurement, real-time edge/contrast filtering, luminance profiling, and CSV data export.

## Features

- **Live USB Camera & Resolution Control**:
  - Enumerates available video input devices (`cameraSelect`).
  - Supports `1080p (FHD)`, `720p (HD)`, `4K (UHD)`, and `Max Hardware Res` presets.
  - `Start Feed`, `Freeze Frame`, and `Snapshot` controls, plus a **Session Gallery** drawer for captured frames.
- **2-Click Calibration & Unit Conversion**:
  - `2-Click Calibrate` workflow to set scale against a known reference object.
  - Adjustable Scale Factor (`px/mm`, default `100.00 px/mm`).
  - Switchable display units: `mm`, `µm`, `mil`, `in`, and `px`.
- **Measurement & Inspection Tools**:
  - `Select / Edit`
  - `Line / Dist` (linear distance)
  - `Circle (R/D)` (radius and diameter)
  - `3-Pt Arc`
  - `3-Pt Angle`
  - `Polyline`
  - `Polygon (Area)`
  - `Profile Line` with an interactive **Line Intensity Profile Graph (0–255 Luminance)** bottom drawer
  - `Tag Defect` with defect categories (`Burr`, `Micro-Crack`, `HAZ / Thermal Zone`, `Pitting / Pit`, `Tool Chipping`, `Tool Wear`), severity levels (`Minor`, `Moderate`, `Critical`), and custom notes
- **Real-Time Image Processing**:
  - Filter modes: `None`, `Sobel Edges`, `Prewitt Edges`, `Laplacian Edge`, and `Unsharp Filter`.
  - Adjustable `Brightness` (`-100` to `100`) and `Contrast` (`-100` to `100`) sliders.
- **Reticles, Overlays & Export**:
  - Toggleable `Crosshair Center` and `Calibrated Grid` overlays.
  - `Export CSV` to save measurements and defect tags.

## Requirements / Dependencies

- **Hardware**: A USB microscope or UVC-compatible webcam connected to your computer.
- **Runtime**: Any modern web browser supporting `navigator.mediaDevices.getUserMedia` (WebRTC MediaDevices API) and HTML5 Canvas (e.g., Chrome, Edge, Firefox).
- **Dependencies**: None. `index.html` is a single self-contained file with zero external libraries or build steps.
- **Permissions**: Browser camera access requires a secure context (`https://`, `http://localhost`, or `file://` depending on browser security settings).

## Installation / Setup

1. Download or clone this repository from GitHub (`zadrian9/USB-Microscope-Metrology-WorkBench`).
2. Serve `index.html` over `https://` (such as GitHub Pages) or a local server (e.g., `python -m http.server`), or open `index.html` directly in a browser that allows camera access on `file://`.
3. Grant camera permission when prompted by the browser.

### Install / Offline (PWA)

When opened over `https://` (such as GitHub Pages) or `http://localhost`, you can install the app from your browser's address bar / menu; it caches all shell assets on first load and continues working offline.

## Usage

1. **Connect Camera**: Select your USB microscope from the camera dropdown, choose a target resolution, and click **Start Feed**.
2. **Calibrate**: Place a calibration slide or ruler under the microscope, click **2-Click Calibrate**, and follow the two-point calibration prompt (or enter a known `px/mm` scale factor). Select your preferred display unit (`mm`, `µm`, `mil`, `in`, or `px`).
3. **Inspect & Measure**:
   - Optionally click **Freeze Frame** to lock a still image for precise measurement.
   - Choose a measurement tool (`Line / Dist`, `Circle (R/D)`, `3-Pt Arc`, `3-Pt Angle`, `Polyline`, `Polygon (Area)`, or `Profile Line`) and draw on the canvas.
   - Use **Tag Defect** to annotate features with category, severity, and notes.
4. **Enhance & Overlay**: Apply edge-detection filters (`Sobel`, `Prewitt`, `Laplacian`, `Unsharp`), adjust brightness/contrast, or enable the **Crosshair Center** and **Calibrated Grid** overlays.
5. **Save Results**: Capture stills with **Snapshot** (stored in the Session Gallery) or click **Export CSV** to download your measurement and defect log.

## License

This project is licensed under the [Mozilla Public License 2.0](LICENSE).
