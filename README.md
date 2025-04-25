# 🛩 PX4 Simulation Using jMAVsim Installation on Ubuntu 22.04 (WSL)

This guide walks you through installing PX4 Autopilot with JMAVSim on Ubuntu using WSL.

---

## 🪟 Setting up WSL (Windows Subsystem Linux)

If you are on Windows, you will need WSL with Ubuntu 22.04.  
You can install it by opening **CMD** (Command Prompt) and running:

```bash
wsl --install -d Ubuntu-22.04
```

> ⚠️ **Note:**  
> WSL may not work correctly on older Windows versions. Some additional setup or troubleshooting might be needed.

---

## ✅ 1. Update Your System

```bash
cd
sudo apt update && sudo apt upgrade -y
```

---

## 📦 2. Install Required Dependencies

```bash
sudo apt install ant
sudo apt install openjdk-11-jdk
```

> ⚠️ **Debugging Note:**  
> You need **JDK 11**. Check your Java version with:
>
> ```bash
> sudo update-alternatives --config java
> ```

---

## 🔄 3. Clone the PX4-Autopilot Repository

```bash
git clone https://github.com/PX4/PX4-Autopilot.git --recursive
```

> ℹ️ **Note:** After cloning, restart your terminal to refresh environment variables if needed.

---

## ⚙️ 4. Run the PX4 Installation Script

```bash
cd ~/PX4-Autopilot
bash ./Tools/setup/ubuntu.sh
make px4_sitl jmavsim
```
### Now it should work, but if it didn't then do step 5 and 6
---

## 🔁 5. Restart WSL

Shut down WSL from regular CMD:

```cmd
wsl --shutdown
```

Then reopen WSL:

```cmd
wsl
```

---

## 🚀 6. Run JMAVSim

```bash
cd ~/PX4-Autopilot
make distclean
make clean
bash ./Tools/setup/ubuntu.sh
make px4_sitl jmavsim
```

---

Sit back, relax, and enjoy the flight! 🛫

> ⚠**Note:**  
>
> This repository contains the user-friendly version. For more frequent or experimental updates, please check out the [Gist](https://gist.github.com/asnb0/31527f37c84ecd09002f63a51ce4464f).. 
