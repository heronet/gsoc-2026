# Zephyr FIDO2/CTAP2 Sybsystem: Google Summer of Code 2026 Contributor Application

## You

- **Name**: Siratul Islam
- **Current/last occupation**: Maintainer of the Biometrics subsystem in Zephyr RTOS / Undergrad Physics Student at  Shahjalal University of Science and Technology, Sylhet, Bangladesh
- **Short bio / overview of your background**:  
  I am the maintainer of Zephyr’s Biometrics subsystem. Over the past year I have had 18 PRs merged, added support for 9 new boards, implemented 2 display drivers, 2 biometric (meta)drivers, and authored the complete Biometrics API and framework from scratch. I also review PRs and fix bugs on existing codebase. This makes me deeply familiar with Zephyr’s internals and structure. I also authored a Time-of-Flight sensor driver (ST VL53L1X) that is currently in v5 review for Linux mainline. My first-author paper on the Vendor-Agnostic Biometric Subsystem for Industrial IoT is under revision at IEEE Transactions on Industrial Informatics.
- **Subscribe to the mailing list** of the appropriate group and introduce yourself:  
  I'm already subscribed to Zephyr `devel` mailing list where I get regular updates for Architecture WG meetings and other updates.
- **Tell us your IRC nick** with which you will use the group's IRC channel:  
  Zephyr community primarily uses Discord. I'm on discord as Sirat (@heronet)

## Your Coding Skills

- What platform do you use to code? Hardware specifications and operating system:  
  I use Arch Linux on a Thinkpad T14a G1 (6/12 Threads, 16 GB RAM) (it's the last model to take 2 SSDs), and a MacBook Air M1 with macOS 15 (don't like macOS 26). I use podman to run Ubuntu LTS (don't like it as a desktop OS) for Yocto and ROS2.
- Did you ever code in C or C++/Perl/python/... ? What is your experience?  
  My true first programming language was C++ I learned in 7th grade. Since then, I learned many other languages. Now I mostly use C, primary for Zephyr and the Linux Kernel. I use C extensively to write drivers/API for Zephyr. I also work on Linux applications and recently wrote a Linux Driver for ST VL53L1X ToF sensor. It is currently beign upstreamed in the Kernel and can be found in lore.kernel.org
- If you apply for a project on our ideas list, have you experience in the areas listed under "Desired knowledge"?  
  I do. But this is a custom project.

## Set yourself up

- Set up your platform to build a GIT snapshot of the current state of Zephyr:  
  Done. I can build projects and submit PRs
- If you need help, ask on the mailing list or IRC:  
  I have been actively contributing since Jun of last year.

## You and Us

- Were you involved in development in the project's group in the past? What was your contribution?  
  Yes. I am the active maintainer of the Biometrics subsystem in Zephyr RTOS (PR #100139, the first biometric authentication framework in any RTOS). My contributions include:
  - **18 merged PRs** in Zephyr mainline
  - 9 board support packages + more board upgrades
  - 3 display/auxdisplay drivers + upgrades (HUB12 LED matrix with chaining, TM1637 7-segment)
  - 1 toolchain integration
  - Full subsystem architecture, drivers (ZFM-x0 & GT-5x fingerprint), samples, documentation, and Kconfig
  - Currently designing the FIDO2/CTAP2 authenticator subsystem RFC (PR #104327) the implementation of which will be done for GSoC.
- Were you involved in other OpenSource development projects in the past? Which, when and in what role?  
  I authored the `iio: proximity: add driver for ST VL53L1X` patch series (v5, under review) for the Linux kernel mainline:  
  https://lore.kernel.org/linux-iio/20260313113737.151881-1-email@sirat.me/
- Why have you chosen your development idea and what do you expect from your implementation?  
  FIDO2 is a modern passwordless authentication system. Since I am already involved with Zephyr security, implementing a new security feature is natural for me. Also, it will make Zephyr the first RTOS (to my knowledge) to inlcude a first class, OS level implementation of FIDO2. This will allow developers to include FIDO to any of their apps, without the knowledge of the internals of FIDO, or the deep security concepts of CTAP2. Which also means less security flaw, since that part is already done for them.

## Your Project

- **What do you want to achieve?**  
  I want to implement a FIDO2/CTAP2 authenticator subsystem with biometric user verification integration. It will turn any application into a hardware security key. It will also be the first for an RTOS to have OS level support for FIDO2. I want to make it the reference for all other embedded implementations to follow.

- **If you are proposing a project of your own, what is unique about it?**  
  OS level IoT Security. First FIDO2 support in any RTOS. Zephyr’s existing security framework like PSA Crypto + Biometrics allow for easy integration. Many real-world use cases like passwordless login on embedded devices.

- **What makes you suited to carry the project?**  
  Being the author and maintainer of the Biometrics subsystem, I know the internals and workflow of zephyr and the security aspects. I have already drafted the full public API headers (PR #104327) for FIDO2. Plus I will be working directly with Zephyr Lead Security Architect Flavio Ceolin as my mentor)

- **How much time do you plan to invest** in the project before, during and after the Summer of Code (We expect full time 40h/week during GSoC, but better make this explicit)?  
  40 hours/week during GSoC. I am already doing the research part, going through the CTAP2 specs and I plan to maintain the subsystem after GSoC ends along with the biometrics subsystem.

- **Please provide a schedule** of how this time will be spent on subtasks of the project.  
  TODO

### Schedule
