# SURGE Lab — Visual simulator

Open [index.html](index.html) locally in any modern desktop or mobile browser (no build or server required).

## Purpose
This lightweight, MIT-compatible demonstrator visualizes the mod's simplified **current electrical demand convention**: `EC/s = drives × configured acceleration × throttle`. It is suitable for explaining power shortfalls and idealized multi-drive acceleration before making changes to KSP code.

## Features
- 1–8 identically oriented drives, 0–200 m/s² per drive, adjustable throttle.
- Adjustable continuous reactor EC/s, finite battery EC and 1–100× simulation speed.
- Velocity, distance, g-equivalent acceleration, EC demand, battery state, ideal constant-acceleration stopping distance and time.
- Moving starfield and a scrolling velocity history.
- Pure client-side HTML/CSS/JavaScript with responsive layout; no network or telemetry access.

## Important limitations
- **Not KSP:** no gravity, atmospheric drag, Unity, KSP resource-flow graphs, warp/rails, orbital motion, or independently mounted drive orientations.
- Resource distribution is modeled as an ideal *shared* bus. Actual `WarpEngineModule` code calls `RequestResource` separately for each part. The simulator cannot diagnose Issue #2 without KSP measurements.
- EC is a gameplay resource rather than joules. Supply model uses reactor continuously plus battery for deficits, recharging from unused output. This is a *proposed illustrative power system*, not a representation of current engine integration.
- Idealized acceleration and stopping distance assume straight-line flight. Coasting at constant velocity after battery depletion is normal.
- The velocity chart shows history, not proof of a 30g cap.
- Changes to controls during a run affect subsequent steps; **Reset** applies the selected starting battery value.
- All sources are local; no data is collected or transmitted.

## Contributing to upstream
This simulator is intentionally isolated under `tools/surge-lab/`. It can be reviewed and merged independently of physics refactors, diagnostic branches and the documentation baseline. Once accepted, it could be linked from README or hosted using GitHub Pages at the maintainer's discretion.
