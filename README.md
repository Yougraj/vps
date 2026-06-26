# Automated GitHub Actions VNC Desktop (macOS + Ngrok)

This repository contains a GitHub Actions workflow that automatically boots up a macOS virtual machine, starts Apple's built-in VNC server with the password `0000`, and tunnels it using **Ngrok** so you can connect securely using **RealVNC Viewer**.

---

## 🛠️ Step 1: Add your Ngrok Authtoken to GitHub Secrets
Because Ngrok requires authentication to tunnel TCP connections, you need to add your token to your GitHub repository's secrets:

1. Log in to [ngrok.com](https://ngrok.com/) and go to your dashboard to copy your **Authtoken**.
2. Go to your repository on GitHub.
3. Click on **Settings** (top menu bar) > **Secrets and variables** (left sidebar) > **Actions**.
4. Click the green **New repository secret** button.
5. Set the **Name** to:
   ```text
   NGROK_AUTHTOKEN
   ```
6. Paste your copied token into the **Value** box and click **Add secret**.

---

## 🚀 Step 2: Push the Files & Start the VNC Desktop

1. Push these files to the `main` branch of your repository:
   ```bash
   git add .
   git commit -m "Configure macOS VNC with Ngrok"
   git push origin main
   ```

2. View the Action Console:
   * Go to the **Actions** tab on your GitHub repository.
   * Select the **VNC Desktop Runner (macOS + Ngrok)** workflow and click on the running job.
   * Expand the **Start VNC Tunnel (Ngrok)** step to see the console logs.

---

## 🔌 Step 3: Connect using RealVNC Viewer

1. Find the connection URL in the logs. It will look like this:
   ```text
   tcp://0.tcp.ngrok.io:12345
   ```
2. Open **RealVNC Viewer** on your local computer.
3. Paste the address using a **double colon (`::`)** to separate the hostname and port number:
   ```text
   0.tcp.ngrok.io::12345
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
