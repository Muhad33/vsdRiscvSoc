# 🛠️ Task 2: Prove Your Local RISC‑V Setup (Run, Disassemble, Decode)

![Platform](https://img.shields.io/badge/Platform-VirtualBox-orange)
![Toolchain](https://img.shields.io/badge/Toolchain-RISC--V-blue)
![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)
![Environment](https://img.shields.io/badge/Environment-Ubuntu%2022.04-yellow)

---

## 🎯 Objective

* ✅ Run 4 RISC‑V C programs locally using the installed toolchain and `spike pk`
* ✅ Embed uniqueness via `username`, `hostname`, `machine ID`, and timestamps
* ✅ Disassemble and decode main section of each binary
* ✅ Decode RISC-V integer instructions manually

---

## 🧩 Task 2.1 - Set Up Unique Identity Variables

### 🎯 Objective

Set identity variables in the Linux host shell so that each build is uniquely tied to the system.

### ⚙️ Commands Used

```bash
export U=$(id -un)
export H=$(hostname -s)
export M=$(cat /etc/machine-id | head -c 16)
export T=$(date -u +%Y-%m-%dT%H:%M:%SZ)
export E=$(date +%s)
```

### ✅ Summary

* Stored username, hostname, machine ID, UTC time, and epoch time as environment variables
* These values are passed as `#define` macros to every program

### 🔴 Output

![Output_2.1](https://github.com/user-attachments/assets/d7a00437-74e4-4591-b7c3-5c4c911bc8a5)

