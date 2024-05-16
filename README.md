# FAST - Fast Astro Sky Tracking

**WORK IN PROGRESS**

This project looks into creating a software to allow the tracking of fast objects (ISS, Tiangong, LEO satellites, or even planes) with an amateur telescope, motorized mount and camera.

### Work principle

1. Acquire timed trajectory of the target (TLE, sky maps from HeavenAbove, online queries...)
2. Roughly track the target using this trajectory
3. Find target in camera image
4. Apply real time corrections to the mount tracking to keep target in frame

### Features

[] Acquire timed trajectory from

### Simulators

To allow for testing, FAST will integrate simulators for the camera and the motorized mount. The goal is for these simulators to be replacable seamlessly by hardware (especially the mount) for hardware-in-the-loop simulations.

* Camera simulator:
    * Inputs: Scene (object + trajectory), telescope + camera pixel scale and FOV, telescope pointing
    * Output: ASCOM Camera emulator usable with common astro software (FireCapture, N.I.N.A., ...)

* Mount simulator:
    * ASCOM compatible mount that can receive commands
    * Should be able to be replaced by real hardware