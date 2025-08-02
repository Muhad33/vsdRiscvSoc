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

## 🚀 Step-by-Step Implementation

### 🧩 Step 1: Update APT Package Index

```bash
sudo apt update
