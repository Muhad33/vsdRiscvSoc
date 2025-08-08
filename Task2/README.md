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

## 🧩 Task 2.2 - Create Common Header unique.h

### 🎯 Objective

Create a reusable header for printing build/run metadata like user, host, machine ID, build time, etc.

### ⚙️ Common Header code
```bash
#ifndef UNIQUE_H
#define UNIQUE_H
#include <stdio.h>
#include <stdint.h>
#include <time.h>
#ifndef USERNAME
#define USERNAME "unknown_user"
#endif
#ifndef HOSTNAME
#define HOSTNAME "unknown_host"
#endif
#ifndef MACHINE_ID
#define MACHINE_ID "unknown_machine"
#endif
#ifndef BUILD_UTC
#define BUILD_UTC "unknown_time"
#endif
#ifndef BUILD_EPOCH
#define BUILD_EPOCH 0
#endif
static uint64_t fnv1a64(const char *s) {
const uint64_t OFF = 1469598103934665603ULL, PRIME = 1099511628211ULL;
uint64_t h = OFF;
for (const unsigned char *p=(const unsigned char*)s; *p; ++p) {
h ^= *p; h *= PRIME;
}
return h;
}
static void uniq_print_header(const char *program_name) {
time_t now = time(NULL);
char buf[512];
int n = snprintf(buf, sizeof(buf), "%s|%s|%s|%s|%ld|%s|%s",
USERNAME, HOSTNAME, MACHINE_ID, BUILD_UTC,
(long)BUILD_EPOCH, __VERSION__, program_name);
(void)n;
uint64_t proof = fnv1a64(buf);
char rbuf[600];
snprintf(rbuf, sizeof(rbuf), "%s|run_epoch=%ld", buf, (long)now);
uint64_t runid = fnv1a64(rbuf);
printf("=== RISC-V Proof Header ===\n");
printf("User : %s\n", USERNAME);
printf("Host : %s\n", HOSTNAME);
printf("MachineID : %s\n", MACHINE_ID);
printf("BuildUTC : %s\n", BUILD_UTC);
printf("BuildEpoch : %ld\n", (long)BUILD_EPOCH);
printf("GCC : %s\n", __VERSION__);
printf("PointerBits: %d\n", (int)(8*(int)sizeof(void*)));
printf("Program : %s\n", program_name);
printf("ProofID : 0x%016llx\n", (unsigned long long)proof);
printf("RunID : 0x%016llx\n", (unsigned long long)runid);
printf("===========================\n");
}
#endif
```

Contains:

* Preprocessor macros
* fnv1a64() hash function
* uniq_print_header() function that prints a unique proof block

### ✅ Summary

* Generates ProofID (compile-unique) and RunID (per-execution unique)

## 🧩 Task 2.3 - Program 1: factorial.c

### 🎯 Objective

Run a recursive factorial calculation while embedding unique metadata
### ⚙ Factorial Code
```bash
#include "unique.h"
static unsigned long long fact(unsigned n){ return (n<2)?1ULL:n*fact(n-1); }
int main(void){
uniq_print_header("factorial");
unsigned n = 12;
printf("n=%u, n!=%llu\n", n, fact(n));
return 0;
}
```

### ⚙ Compile Command


```bash
riscv64-unknown-elf-gcc -O0 -g -march=rv64imac -mabi=lp64 \
-DUSERNAME="\"$U\"" -DHOSTNAME="\"$H\"" -DMACHINE_ID="\"$M\"" \
-DBUILD_UTC="\"$T\"" -DBUILD_EPOCH=$E \
factorial.c -o factorial
```
### 🔴 Output
![Output_2.3](https://github.com/user-attachments/assets/9236d511-3c2c-4688-81b8-fc223fd4d37c)

### ▶ Run


```bash
spike pk ./factorial
```


### 🧠 Assembly


```bash
riscv64-unknown-elf-gcc -O0 -S factorial.c -o factorial.s
```


### 🛠 Disassemble Main

bash
```
riscv64-unknown-elf-objdump -d ./factorial | sed -n '/<main>:/,/^$/p' | tee factorial_main_objdump.txt
```
### 🔴 Output
![Output_2.31](https://github.com/user-attachments/assets/d03ab41f-5cda-4b87-b7da-0b18ff6da69b)
![Output_2.32](https://github.com/user-attachments/assets/de3089f3-68d5-47aa-a839-f688f93e9e16)



