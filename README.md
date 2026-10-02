# DFRootBuilder

Automated GitHub Actions builder for [diabl0w/DFRoot](https://github.com/diabl0w/DFRoot).

This repository builds the latest DFRoot source using the upstream project's own build process and publishes the resulting APK as a GitHub Release.

## Releases

APK builds are generated automatically every 4 hours using GitHub Actions and are available in the repository's [Releases](https://github.com/bygalacos/DFRootBuilder/releases) section.

Each release corresponds to a specific upstream DFRoot commit, allowing the exact source revision used for a build to be identified from the APK filename and release information.

## About

DFRootBuilder does **not** maintain or modify the DFRoot source code.

The goal is to keep the build process as close as possible to the upstream DFRoot developer build.

<details>
<summary><strong>Workflow Details</strong></summary>

<br>

The workflow:

1. Checks out the latest source from [diabl0w/DFRoot](https://github.com/diabl0w/DFRoot).
2. Sets up the required Java and Android build environment.
3. Uses DFRoot's own `build.sh` script to build the release APK.
4. Reads the application version from `app/build.gradle.kts`.
5. Reads the current DFRoot commit SHA and commit message.
6. Renames the generated APK using the application version and commit SHA.
7. Creates a GitHub Release containing the built APK.

</details>

<details>
<summary><strong>Build Output</strong></summary>

<br>

Release APKs use the following naming format:

```text
DFRoot_<VERSION>_<COMMIT>.apk
```

Example:

```text
DFRoot_2.0_3050d5b9.apk
```

The corresponding release title uses:

```text
DFRoot <VERSION> <COMMIT>
```

Example:

```text
DFRoot 2.0 3050d5b9
```

Each release also includes the full upstream commit and its commit message.

Example:

```text
DFRoot builder by bygalacos
Version: 2.0
Commit: https://github.com/diabl0w/DFRoot/commit/3050d5b91dd9a6a78c13e16f0a80d7e1f6f5e7c2
Remove 6.1 support
```

</details>

<details>
<summary><strong>Building</strong></summary>

<br>

The workflow can be started manually from:

**Actions → Build DFRoot APK → Run workflow**

DFRootBuilder uses the upstream build script:

```bash
chmod +x gradlew build.sh
./build.sh
```

The generated upstream APK is:

```text
dirtyfrag.apk
```

It is then renamed before being attached to the GitHub Release.

</details>

## Disclaimer

This is an **unofficial build repository**.

DFRootBuilder is not affiliated with or maintained by the DFRoot or KernelSU developers.

All credit for DFRoot belongs to its respective developer and contributors:

- [diabl0w/DFRoot](https://github.com/diabl0w/DFRoot)
- [diabl0w/KernelSU](https://github.com/diabl0w/KernelSU)

This repository only provides GitHub Actions automation for building the upstream source.

Use DFRoot and the generated APKs at your own risk. Rooting, kernel exploitation, and related modifications can cause instability, data loss, boot failures, or other unexpected behavior depending on the device and software version.

## Credits

- [diabl0w](https://github.com/diabl0w) — DFRoot and KernelSU fork
- [KernelSU](https://github.com/tiann/KernelSU) — KernelSU
