# Text Encryption & Decryption App

## 1. About the Project
A desktop cryptography application built with C/C++ to encrypt and decrypt text using modular arithmetic (Caesar Cipher with a shift of 5).

## 2. Motivation & Features
* **Motivation:** Created to test and apply algebraic concepts and modular arithmetic ($\mathbb{Z}/26\mathbb{Z}$) in practical cryptography.
* **Key Features:**
  * **Text Encryption:** Shifts alphabetical characters forward by 5 positions modulo 26.
  * **Text Decryption:** Reverses the shift backward by 5 positions modulo 26 to restore the original text.
  * **Lightweight & Fast:** Built with low-level C/C++ for high execution speed and zero overhead.

## 3. Mathematics & Algebraic Formulation
The encryption and decryption algorithms are based on **Modular Arithmetic (Congruences)** over the ring $\mathbb{Z}/26\mathbb{Z}$, where each letter of the English alphabet is mapped to an integer $x \in \{0, 1, 2, \dots, 25\}$ (with $A=0, B=1, \dots, Z=25$) and a shift key $k = 5$:

### Encryption Function ($E_5$)
$$E_5(x) \equiv (x + 5) \pmod{26}$$

### Decryption Function ($D_5$)
$$D_5(y) \equiv (y - 5) \equiv (y + 21) \pmod{26}$$

Where:
* **$x$**: Numerical index of the plaintext character ($0 \leq x \leq 25$).
* **$y$**: Numerical index of the ciphertext character ($0 \leq y \leq 25$).
* **$k = 5$**: The shift key (5 steps).
* **$\pmod{26}$**: Ensures cyclic wrapping around the 26-letter alphabet (Note: adding $21$ in decryption avoids negative remainders in C/C++ `%` operator, since $-5 \equiv 21 \pmod{26}$).

## 4. Prerequisites & Installation
Before building and running the application, ensure you have **CMake** and a C/C++ compiler installed on your system:

### Linux
* **Ubuntu / Debian / Mint:**
  ```bash
  sudo apt-get update && sudo apt-get install cmake build-essential
  ```
* **Fedora / RHEL / CentOS:**
  ```bash
  sudo dnf install cmake gcc gcc-c++
  ```
* **Arch Linux / Manjaro:**
  ```bash
  sudo pacman -S cmake base-devel
  ```
* **openSUSE:**
  ```bash
  sudo zypper install cmake gcc gcc-c++
  ```
* **Alpine Linux:**
  ```bash
  sudo apk add cmake build-base
  ```

### Windows
Download and install **CMake** from the [Official CMake Download Page](https://cmake.org) along with a C/C++ compiler (MinGW or MSVC).

## 5. Build & Run

### 1. Clone & Build
Open your Terminal (Linux) or Command Prompt (Windows) and run:
```bash
git clone https://github.com
cd encryption_and_cryption-Application
mkdir build && cd build
cmake ..
cmake --build .
```

### 2. Run the Application
* **On Linux:**
  ```bash
  ./encryption_app
  ```
* **On Windows (CMD):**
  ```cmd
  encryption_app.exe
  ```

## 6. Version
`1.0.0`
