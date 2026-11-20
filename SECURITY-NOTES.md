# Security notes

- The generated APK is an upstream test build, not a reviewed TorLabAndr release.
- This pipeline does not alter Tor networking or introduce a direct fallback.
- Never upload signing keys, credentials, or personal data to the repository.
- A build success is not a security audit.
- Test Tor bootstrap, onion v3 access, HTTPS validation, DNS/IP leak resistance,
  offline/fail-closed behavior, lifecycle and Wi-Fi/mobile transitions before use.
