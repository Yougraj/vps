# Automated GitHub Actions VNC Desktop (macOS + Pinggy)

This repository contains a GitHub Actions workflow that automatically boots up a macOS virtual machine, starts Apple's built-in VNC server with the password `0000`, and tunnels it using **Pinggy** so you can connect securely using **RealVNC Viewer**.

---

## 🚀 How to Launch the VNC Desktop

### 1. Push the files to GitHub
Push these files to the `main` branch of your repository:
```bash
git add .
git commit -m "Switch VNC workflow to Pinggy and fix VNC password parameters"
git push origin main
```

### 2. View the Action Console
* Go to the **Actions** tab on your GitHub repository.
* Select the **VNC Desktop Runner (macOS + Pinggy)** workflow and click on the running job.
* Click on the **Start VNC Tunnel (Pinggy)** step to expand its logs.

---

## 🔌 How to Connect using RealVNC Viewer

1. Find the connection URL in the logs. It will look like this:
   ```text
   tcp://lthok-...run.pinggy-free.link:39315
   ```
2. Open **RealVNC Viewer** on your local computer.
3. Paste the address using a **double colon (`::`)** to separate the hostname and port number:
   ```text
   lthok-...run.pinggy-free.link::39315
   ```
4. Click **Connect** (and select Continue if prompted with a security warning).
5. Enter the connection details:
  * **Username:** `runner`
  * **Password:** `0000`

---

## 🖥️ Specifications
* **Operating System:** macOS Sequoia (15.x)
* **Processor:** Apple M1 (Virtual) 3-Core CPU
* **RAM:** 7 GB
* **Timeout:** The VM runs for a maximum of **6 hours** before automatically shutting down.
