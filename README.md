# Zephyr FIDO2/CTAP2 Subsystem: Google Summer of Code 2026 Contributor Application

## You

- **Name**: Siratul Islam
- **Current/last occupation**: Maintainer of the Biometrics subsystem in Zephyr RTOS / Undergrad Physics Student / Research Assistant in the EEE department at Shahjalal University of Science and Technology, Sylhet, Bangladesh
- **Short bio / overview of your background**:
  I am the maintainer of Zephyr's Biometrics subsystem. Over the past year I have had 20 PRs merged, added support for 9 new boards, implemented 2 display drivers, 2 biometric (meta)drivers, and authored the Biometrics API. I also review PRs and fix bugs on existing codebase. This makes me deeply familiar with Zephyr's internals and structure. I also authored a Time-of-Flight sensor driver (ST VL53L1X) that is now accepted into the Linux Kernel IIO subsystem. My first-author paper on the Vendor-Agnostic Biometric Subsystem for Industrial IoT is under revision at IEEE Transactions on Industrial Informatics.
- **Subscribe to the mailing list** of the appropriate group and introduce yourself:
  I'm already subscribed to Zephyr `devel` mailing list where I get regular updates for Architecture WG meetings and other updates.
- **Tell us your IRC nick** with which you will use the group's IRC channel:
  Zephyr community primarily uses Discord. I'm on discord as Sirat (@heronet)

## Your Coding Skills

- What platform do you use to code? Hardware specifications and operating system:

  I use Arch Linux on a Thinkpad T14 AMD Gen1 (6/12 Threads, 16 GB RAM) (it's the last model to take 2 SSDs), and a MacBook Air M1 with macOS 15. I use podman to run Ubuntu LTS for Yocto and ROS2.
- Did you ever code in C or C++/Perl/python/... ? What is your experience?

  My true first programming language was C++ I learned in 7th grade. Since then, I have learned many other languages. Now I mostly use C, primarily for Zephyr and the Linux Kernel. I use C to write drivers/API for Zephyr/STM32 HAL/ESP-IDF. I also work on Linux drivers and recently wrote one for ST VL53L1X ToF sensor which is now accepted into the Linux Kernel IIO subsystem.
- If you apply for a project on our ideas list, have you experience in the areas listed under "Desired knowledge"?

  I do. But this is a custom project.

## Set yourself up

- Set up your platform to build a GIT snapshot of the current state of Zephyr:

  Done. I can build projects and submit PRs.
- If you need help, ask on the mailing list or IRC:

  I have been actively contributing since June of last year.

## You and Us

- Were you involved in development in the project's group in the past? What was your contribution?

  Yes. I am the active maintainer of the Biometrics subsystem in Zephyr RTOS (PR #100139, the first biometric authentication framework in any RTOS). My contributions include:
  - **20 merged PRs** in Zephyr mainline
  - 9 board support packages + more board upgrades
  - 3 display/auxdisplay drivers + upgrades (HUB12 LED matrix with chaining, TM1637 7-segment)
  - 1 toolchain integration
  - Full subsystem architecture, drivers (ZFM-x0 & GT-5x fingerprint), samples, documentation, and Kconfig
  - Currently designing the FIDO2/CTAP2 authenticator subsystem RFC (PR [#104327](https://github.com/zephyrproject-rtos/zephyr/pull/104327)) the implementation of which will be done for GSoC.
  - I also hold both the Linux Foundation Zephyr Maintainer Badge and the Zephyr Technical Contributor Badge from Credly.

- Were you involved in other OpenSource development projects in the past? Which, when and in what role?

  I authored the "STMicroelectronics VL53L1X ToF Sensor" for the Linux Kernel IIO subsystem and am listed as its Maintainer in the MAINTAINERS file.

- Why have you chosen your development idea and what do you expect from your implementation?

  FIDO2 is a modern passwordless authentication system. Since I am already involved with Zephyr security, implementing a new security feature is natural for me. Also, it will make Zephyr the first RTOS (to my knowledge) to include a first class, OS level implementation of FIDO2. This will allow developers to include FIDO to any of their apps, without the knowledge of the internals of FIDO, or the deep security concepts of CTAP2. Which also means fewer security flaws, since that part is already done for them.

## Your Project

- **What do you want to achieve?**
  I want to implement a FIDO2/CTAP2 authenticator subsystem with biometric user verification integration. It will turn any application into a hardware security key. I want to make it the reference for all other embedded implementations to follow.

  It will unlock use cases like an nRF52840/STM32/ESP32 becoming a USB hardware security key with two function calls, a smart lock panel gaining phishing-resistant entry without separate key hardware, a medical device replacing its password database with hardware-bound clinician authentication.

- **If you are proposing a project of your own, what is unique about it?**
  This will make Zephyr the first RTOS with native OS-level FIDO2 support. Unlike standalone implementations, this subsystem never sees the private key. The cryptographic boundary is enforced by design, not convention. Zephyr's existing security framework like PSA Crypto + Biometrics allow for easy integration. Many real-world use cases like passwordless login on embedded devices.

- **What makes you suited to carry the project?**
  Being the author and maintainer of the Biometrics subsystem, I know the internals and workflow of Zephyr and the security aspects. The full public API headers are already authored and open for community review in (PR #104327). The FIDO2/CTAP2 architecture RFC was presented to the Zephyr Security Working Group on 23 March 2026 and received positive feedback / green light. The RFC was also featured in Zephyr Podcast #024 (February 2026), where the hosts highlighted it as a good GSoC project with potential. Plus I will be working directly with Zephyr Lead Security Architect Flavio Ceolin and Zephyr Developer Advocate Benjamin Cabé as my mentors.

- **How much time do you plan to invest** in the project before, during and after the Summer of Code (We expect full time 40h/week during GSoC, but better make this explicit)?
  40 hours/week during GSoC. I am already doing the research part, going through the CTAP2 specs and I plan to maintain the subsystem after GSoC ends along with the biometrics subsystem.

- **Please provide a schedule** of how this time will be spent on subtasks of the project.
  The section below details the schedule

### Schedule

**Total: ~350 hours over 12 weeks (Jun 2 – Aug 24)**

**Phase 1: USB on the wire (W1–W2, Jun 2–15, ~60 h)**

- W1: CTAPHID framing: INIT command, channel allocation, packet reassembly with timeout, error responses.
- W2: authenticatorGetInfo end-to-end over USB. Goal: webauthn.io enumerates the device.

**Phase 2: Core CTAP2 commands (W3–W5, Jun 16 – Jul 6, ~90 h)**

- W3: authenticatorMakeCredential: decode params, UP check, ES256 keygen, authenticatorData construction, self-attestation, store resident credential. Goal: registration completes on real hardware.
- W4: authenticatorGetAssertion: credential lookup, signing, sign_count, allowList, getNextAssertion. Goal: full login on webauthn.io.
- W5: clientPIN: getKeyAgreement, setPIN, changePIN, getPINToken, retry counter, UV-blocked path.

**Midterm (~Jul 6–10)**
Deliverable: a real USB hardware key that registers and authenticates on webauthn.io.

**Phase 3: Completeness (W6–W10, Jul 7 – Aug 10, ~110 h)**

- W6: authenticatorReset: UP guard, 10-second power-up window per spec.
- W7: Biometric UV: Wire fido2_uv_perform() to ZFM-x0/GT-5x via the Biometrics API, PIN fallback on timeout. Goal: full MakeCredential + GetAssertion with `CONFIG_FIDO2_UV_BIOMETRIC=y` on real hardware.
- W8: credentialManagement: enumerateRPs, enumerateCreds, deleteCred, updateUserInfo.
- W9-W10: FIDO conformance tool runs, fix failures, ztest suite.

**Phase 4: Documentation and PR (W11–W12, Aug 11–24, ~80 h)**

- W11: Doxygen + RST docs, sample application, Kconfig documentation, address review comments.
- W12: Final PR to mainline, review cycle buffer, final evaluation.

**Post-GSoC**
I will add BLE transport and NFC transport once the Zephyr NFC subsystem (currently in RFC) is merged. I will also continue maintaining the subsystem, just as I maintain the Biometrics subsystem.