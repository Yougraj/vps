# Temporary GitHub Actions SSH VM (tmate)

This repository contains a GitHub Actions workflow that allows you to spin up a temporary macOS or Linux virtual machine and access it interactively via SSH or a web terminal.

---

## 🛠️ How to Set It Up

### 1. Register your SSH Key with GitHub (Prerequisite)
The workflow is configured with `limit-access-to-actor: true` for security. This means only you can SSH into the machine, using the SSH keys associated with your GitHub profile.
* If you haven't already, add your public SSH key (`id_rsa.pub` or `id_ed25519.pub`) to your GitHub account under **Settings > SSH and GPG keys**.

### 2. Push the files to GitHub
1. Initialize a git repository in this folder if you haven't already:
   ```bash
   git init
   git add .
   git commit -m "Add SSH workflow and README"
   ```
2. Create a new repository on GitHub.
3. Push this codebase to your main/default branch.

---

## 🚀 How to Launch the SSH Runner

1. Open your repository on GitHub.
2. Click on the **Actions** tab at the top.
3. In the left-hand menu under *Workflows*, select **SSH into Runner**.
4. Click the **Run workflow** dropdown on the right side of the screen.
5. Click the green **Run workflow** button.

---

## 🔌 How to Connect

1. Refresh the Actions page and click on the newly created active workflow run (it will have a yellow in-progress circle).
2. Click on the **ssh-session** job on the left or in the main panel.
3. Click to expand the **Start tmate SSH Session** step in the logs.
4. You will see two connection links:
   * **Web shell:** Click the HTTP link (e.g. `https://tmate.io/t/r/...`) to open a terminal directly inside your web browser.
   * **SSH:** Copy the SSH command (e.g. `ssh ...@ny1.tmate.io`) and run it in your computer's terminal:
     ```bash
     ssh <session-token>@ny1.tmate.io
     ```

---

## 🖥️ Runner Specifications

Depending on the `runs-on` value in [.github/workflows/ssh.yml](file://.github/workflows/ssh.yml):

| Operating System | CPU | RAM | Storage |
| :--- | :--- | :--- | :--- |
| **macOS** (`macos-latest`) | Apple Silicon (M1/M2 vCPU) | 14 GB | ~14 GB available |
| **Linux** (`ubuntu-latest`) | 4-core vCPU | 16 GB | ~14 GB available |

> **Tip:** You can switch between macOS and Linux by editing the `runs-on` value in [.github/workflows/ssh.yml](file://.github/workflows/ssh.yml).

---

## ⚠️ Important Warnings & Limits

* **Terms of Service:** Using GitHub Actions as a free host, runner, or general-purpose virtual machine violates the GitHub Terms of Service. Doing so excessively or for heavy tasks (like crypto mining or continuous bot hosting) will result in your GitHub account being permanently banned.
* **6-Hour Limit:** GitHub Actions jobs have a strict maximum runtime of **6 hours**. The VM will automatically shut down and be deleted once this limit is hit.
* **Ephemeral Storage:** Any files or tools you install or create during your SSH session will be completely lost when the workflow run ends or is cancelled.
