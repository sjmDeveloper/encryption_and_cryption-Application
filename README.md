# Text Encryption & Decryption App

## 1. About the Project
A desktop cryptography application built with **C++ and Qt6** that encrypts and decrypts lowercase alphabetical text using modular arithmetic (Caesar Cipher with a shift of 5).

## 2. Motivation & Architecture
* **Motivation:** Created to apply modular arithmetic ($\mathbb{Z}/26\mathbb{Z}$) and functional C++ (`std::function` lambdas) inside a clean Qt6 GUI.
* **Project Structure:**
  * `math/application.h`: Core application class managing character-by-character transformation pipelines.
  * `math/encrypt_crypt.h`: Defines the `crypt` and `uncrypt` functional lambdas (`std::function<num(num)>`) with constants `lenletter = 26` and `add = 5`.
  * `math/setToQstring.h`: Bridges standard C++ data types with Qt's `QString` for GUI rendering.
  * `mainwindow.h / .cpp / .ui`: Qt6 graphical user interface for text input and output.

## 3. Mathematics & Code Implementation
Each lowercase letter $c \in \{'a', \dots, 'z'\}$ is mapped to its zero-based alphabetical index $x = \text{ASCII}(c) - \text{ASCII}('a') \in \{0, \dots, 25\}$, while space characters (`' '`) remain untouched:

### Encryption (`crypt` lambda)
$$E_5(x) = \begin{cases} \text{' '} & \text{if } c = \text{' '} \\ (x + \text{add}) \bmod \text{lenletter} + \text{ASCII}('a') & \text{otherwise} \end{cases}$$

### Decryption (`uncrypt` lambda)
$$D_5(x) = \begin{cases} \text{' '} & \text{if } c = \text{' '} \\ ((x - \text{add}) \bmod \text{lenletter}) + \text{ASCII}('a') & \text{otherwise} \end{cases}$$

Where:
* **`lenletter = 26`**: Size of the English alphabet ($\mathbb{Z}/26\mathbb{Z}$).
* **`add = 5`**: Modular shift key.
* **Space Handling (`x == (int)' '`)**: Preserves whitespace directly without applying modular arithmetic.

## 4. Prerequisites & Installation
Before building and running the application, ensure you have **Qt6**, **CMake**, and a C++ compiler installed:

### Linux
* **Ubuntu / Debian / Mint:**
  ```bash
  sudo apt-get update && sudo apt-get install qt6-base-dev cmake build-essential
  ```
* **Fedora / RHEL / CentOS:**
  ```bash
  sudo dnf install qt6-qtbase-devel cmake gcc-c++
  ```
* **Arch Linux / Manjaro:**
  ```bash
  sudo pacman -S qt6-base cmake base-devel
  ```
* **openSUSE:**
  ```bash
  sudo zypper install qt6-base-devel cmake gcc-c++
  ```
* **Alpine Linux:**
  ```bash
  sudo apk add qt6-qtbase-dev cmake build-base
  ```
* **Other Distributions:** Install via the [Official Qt Online Installer](https://qt.io) or your distribution's package manager.

### Windows
Download and install **Qt6** (along with MinGW and CMake) from the [Official Qt Download Page](https://qt.io).

## 5. Build & Run

### 1. Clone & Build
Open your Terminal (Linux) or Command Prompt (Windows) and run:
```bash
git clone https://github.com/sjmDeveloper/encryption_and_cryption-Application
cd encryption_and_cryption-Application
mkdir build && cd build
cmake ..
cmake --build .
```

### 2. Run the Application
* **On Linux:**
  ```bash
  ./encryption_and_cryption-Application
  ```
* **On Windows (CMD):**
  ```cmd
  encryption_and_cryption-Application.exe
  ```

## 6. Version
`1.0.0`
