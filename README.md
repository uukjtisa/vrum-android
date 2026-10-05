# VRUM for Android

The [VRUM](https://github.com/uukjtisa/vrum) engine simulator on your phone —
the same physics, the same sound, the same gearbox logic as the desktop build.

> **Status: in development.** No APK yet. This repo holds the Android app; the
> engine itself comes in through the `core` submodule.

## How it fits together

```
VRUM-Android/
├── core/        submodule → uukjtisa/vrum  (the C++ engine, shared with desktop)
└── app/         Android app (coming): NDK build of core, Oboe audio,
                 Jetpack Compose UI
```

Nothing in the engine is rewritten for Android. The simulation, the sound
synthesis, and all the driving logic — TCU, launch control, Shift Assist,
cooling — live in `core`'s `DriveController`, so the phone and the PC drive
exactly the same car. Only the screen and the audio output are Android-specific.

## Planned

- **Cockpit** (landscape): paddles, analog brake and throttle pedals, tach with
  shift lights, gear with Shift Advisor, LAUNCH / ASSIST / TCU controls
- **Garage**: engine picker and live tuning (HF gain, convolution, acoustics,
  pedal travel)
- **Engine cutaway** view
- **Gamepad** support (triggers = pedals, bumpers = paddles) and haptics on
  shifts and the limiter
- **Record and share** a WAV of what you hear
- **Quality presets** — simulation frequency and fluid substeps are
  configurable, with live headroom shown, because a phone CPU has about half
  the per-core speed of a desktop: big engines need a lower preset to run in
  real time, small ones can run higher

## Clone

```
git clone --recurse-submodules https://github.com/uukjtisa/vrum-android.git
```

## Licence

MIT. The engine in `core` is MIT too — © Ange Yaghi (engine-sim) and Niccc2007
(VRUM modifications).
