# 🛠️ Task 1: RISC-V Toolchain Setup & Uniqueness Test

![Platform](https://img.shields.io/badge/Platform-VirtualBox-orange)
![Toolchain](https://img.shields.io/badge/Toolchain-RISC--V-blue)
![Status](https://img.shields.io/badge/Status-✅%20Complete-brightgreen)
![Environment](https://img.shields.io/badge/Environment-Ubuntu%2022.04-yellow)

---

## 🎯 Objective

Successfully install essential base developer tools required for compiling the RISC-V simulator, proxy kernel, and associated components.  
This includes compilers, linkers, autotools, and waveform visualizer **GTKWave**.

---

## 📋 Prerequisites

- ✅ Oracle VirtualBox installed on Windows  
- ✅ Ubuntu 22.04 LTS (64-bit) set up in a Virtual Machine  
- ✅ Minimum 2 vCPUs, 4GB RAM, 30GB disk space  
- ✅ Internet connectivity inside VM  
- ✅ `sudo` access in Ubuntu  

---

## 🚀 Task 1.1 - Install base developer tools

Why: These are common build prerequisites (compilers, linkers, autotools) and libraries
required by the RISC‑V simulator, proxy kernel, and other tooling. GTKWaves is included for
waveform viewing in digital design flows.

#### 🧩 Step 1: Update APT Package Index

```bash
sudo apt update
```
#### 📦 Step 2: Install Developer Tools (Installation Command)

```bash
sudo apt-get install -y git vim autoconf automake autotools-dev curl \
libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex \
texinfo gperf libtool patchutils bc zlib1g-dev libexpat1-dev gtkwave
```
#### ✅ Installation Summary

- 📦 76 new packages were installed
- 🔄 6 packages were upgraded
- ❌ 0 packages were removed
- 📌 Examples of installed packages:
  - Development tools: `gcc`, `g++`, `make`, `binutils`, `build-essential`
  - Build tools: `autoconf`, `automake`, `libtool`, `bison`, `flex`
  - Libraries: `libgmp-dev`, `libmpfr-dev`, `libmpc-dev`, `zlib1g-dev`
  - Others: `curl`, `vim`, `git`, `gtkwave`, `texinfo`, `patchutils`
- 📡 Internet connection and working repositories were required
- ✅ Installation completed successfully with no errors

#### 🔴 Output
![Task 1.1 Output](Task_1.1_Output.png)





