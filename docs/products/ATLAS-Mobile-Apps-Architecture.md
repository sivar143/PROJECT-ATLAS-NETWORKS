# ATLAS Mobile Applications — Architecture

## Platforms

- Android
- iOS

## Primary functions

- device onboarding
- network setup
- Wi-Fi configuration
- guest/IoT network management
- client discovery
- alerts
- diagnostics
- firmware update approval/status
- parental/content policy management where implemented
- remote administration through the cloud controller

## Pairing

Initial local pairing should use a secure short-range/bootstrap mechanism such as QR code or authenticated local discovery. Credentials must never be embedded in QR codes in plaintext.

## Offline behavior

The application should preserve access to cached non-sensitive status while clearly distinguishing stale information from live device state.
