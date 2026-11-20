# TorLabAndr — corrected upstream CI starter

This is a **test-build pipeline for the official Tor Browser Android build system**.
It clones `tor-browser-build`, updates its RBM submodule, and invokes the upstream
`torbrowser-testbuild-android-aarch64` or `torbrowser-testbuild-android-armv7` Make target.

## Critical scope

This is an unmodified upstream test build. It is **not yet branded as TorLabAndr**.
Do not change the package ID, Tor networking, certificates, fingerprinting defenses,
or update mechanism without a reviewed upstream fork patch. The first goal is to prove
the official build pipeline can produce an APK.

A CI run can still fail due to runner storage, memory, network limits, upstream changes,
or GitHub-hosted runner restrictions. No one can guarantee a clean build without running
it on the actual runner and inspecting logs.

## Use from Android

1. Create a new GitHub repository named `TorLabAndr-CI`.
2. Download and extract this ZIP on your phone.
3. Upload the `.github` folder (including `workflows/android-build.yml`) to the repository's
   default branch. The `.github` directory may be hidden by Android file managers; enable
   "show hidden files".
4. In GitHub repository Settings > Actions > General, ensure Actions are allowed.
5. Open Actions > "TorLabAndr - upstream Android test build" > Run workflow.
6. Start with `arm64-v8a`. Use `armeabi-v7a` only if your Android system is 32-bit.
7. Wait for the job. If it fails, open the failed step and save/copy the log.
8. Download the artifact. Inspect `BUILD-INFO.txt`, `SHA256SUMS.txt`, and the APK.
   Do not install or distribute until signature, package identity, Tor bootstrap, onion
   connectivity, and leak behavior are verified.

## Build architecture

Official Tor Browser Build README documents `make submodule-update`, Android targets,
and testbuild targets. The testbuild is a faster alpha-style build intended for testing,
not a stable public release. This starter uploads diagnostics even when the build fails.

## Official source

https://gitlab.torproject.org/tpo/applications/tor-browser-build
