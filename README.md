# 🛩 PX4 Simulation Using jMAVsim Installation on Ubuntu 22.04 (WSL)

This guide walks you through installing PX4 Autopilot with JMAVSim on Ubuntu using WSL.

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
> You need **JDK 11** or higher. Check your current version with:
>
> ```bash
> sudo update-alternatives --config java
> ```

---

## 🔄 3. Clone the PX4-Autopilot Repository

```bash
git clone https://github.com/PX4/PX4-Autopilot.git --recursive
```

> ℹ️ **Note:** Restart your terminal after the installation finishes.

---

## ⚙️ 4. Run the PX4 Installation Script

```bash
cd ~/PX4-Autopilot
bash ./Tools/setup/ubuntu.sh
make px4_sitl jmavsim
```

---

## 🔁 5. Restart WSL

Shut down WSL from regular CMD:

```cmd
wsl --shutdown
```

Then relaunch WSL:

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

Happy flying! 🛫
