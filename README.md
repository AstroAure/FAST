# FAST - Fast Astro Sky Tracking

**WORK IN PROGRESS**

This project looks into creating a software to allow the tracking of fast objects (ISS, Tiangong, LEO satellites, or even planes) with an amateur telescope, motorized mount and camera.

### Work principle

1. Acquire timed trajectory of the target (TLE, sky maps from HeavenAbove, online queries...)
2. Roughly track the target using this trajectory
3. Find target in camera image
4. Apply real time corrections to the mount tracking to keep target in frame

### Features

1. Acquire timed trajectory from:
    1. TLE
    2. Sky maps (HeavenAbove, ...)
    3. Online queries
2. Control mount to follow a timed trajectory
3. Find target on camera feed (auto or manual exposure settings)
4. Calculate tracking corrections to keep target centered
5. Send corrections to the mount
6. Integrate main and guide camera for tracking:
    1. Auto-switch between cameras if target is visible in main camera or not
    2. Spiral search while tracking with the guide camera to find target in main camera
    3. Remember position of main camera FOV in guide camera FOV
7. Manual control:
    1. Manual corrections from the rough tracking
    2. Framing on the camera feed in auto-tracking
    3. Activate/deactivate auto-tracking
    4. Integrate keyboard
    5. Integrate gamepad
8. Safety:
    1. Sun safety bubble
    2. Meridian flip safety
9. GUI:
    1. Display camera feed(s)
    2. Display tracking state:
        1. Rough tracking
        2. Guide camera tracking
        3. Main camera tracking
        4. Manual tracking
    3. Overlay on camera feed(s):
        1. Main camera FOV in guide camera FOV
        2. Found target position in image
        3. Goal target position in image
        4. Correction graphs
    4. Display trajectory on sky map and telescope position
    5. Raise safety alerts
10. Save raw video and/or allow third-party software (FireCapture) to save raw video

### Simulators

To allow for testing, FAST will integrate simulators for the camera and the motorized mount. The goal is for these simulators to be replacable seamlessly by hardware (especially the mount) for hardware-in-the-loop simulations.

* Camera simulator:
    * Inputs: Scene (object + trajectory), telescope + camera pixel scale and FOV, telescope pointing
    * Output: ASCOM Camera emulator usable with common astro software (FireCapture, N.I.N.A., ...)

* Mount simulator:
    * ASCOM compatible mount that can receive commands
    * Should be able to be replaced by real hardware