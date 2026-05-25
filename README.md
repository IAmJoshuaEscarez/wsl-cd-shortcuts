
# WSL2 Global Folder Shortcut & Prompt Optimizer
A guide to jumping from deep Linux directories straight to your Windows folders (`Downloads`, `Desktop`, `Documents`) with a single command, while maintaining a clean, native-feeling Linux prompt.

---

##  Before You Begin: Find Your Windows Username
Every Windows computer has a unique user folder. We need to find yours first.

1. Open your terminal.
2. Type this command and press **Enter**:
```bash
   ls /mnt/c/Users

```

3. Look at the output names (e.g., `escar`, `alex`, `john`).
4. **Copy or write down your specific name.** You will need it in Step 3.

---

## Step-by-Step Installation

### Step 1: Open Your Configuration File

Linux keeps terminal settings in a hidden file. We will open it using a terminal text editor called `nano`.

* **If you are using Bash shell (Default Kali/Ubuntu in most setups), type:**

```bash
  nano ~/.bashrc

```

* **If you are using Zsh shell, type:**

```bash
  nano ~/.zshrc

```

---

### Step 2: Go to the Bottom of the File

* Press and hold the **Down Arrow Key (↓)** on your keyboard.
* Keep holding it until the cursor reaches the **very end** of the file where there is empty space.

---

### Step 3: Paste the Shortcut & Prompt Optimization Code

Copy the lines below and paste them into that blank space at the bottom of the file:

```bash
# 1. Global Navigation Shortcut
export CDPATH=".:/mnt/c/Users/YOUR_WINDOWS_USERNAME"

# 2. Native Linux Feels Prompt (Hides /mnt/c/... and keeps Kali colors)
PS1='${debian_chroot:+($debian_chroot)}┌──(${debian_chroot:+($debian_chroot)}\[\e[1;31m\]\u\[\e[0m\]㉿\[\e[1;34m\]\h\[\e[0m\])-\[\e[0m\][\[\e[1;32m\]${PWD/#\/mnt\/c\/Users\/YOUR_WINDOWS_USERNAME/\~}\[\e[0m\]]\n└─$ '

```

**CRITICAL CHANGE:**
Delete **BOTH** instances of `YOUR_WINDOWS_USERNAME` in the code above and replace them with the exact Windows name you discovered during the **Before You Begin** phase.

* **Correct Example (If your username is escar):**
`export CDPATH=".:/mnt/c/Users/escar"`
`... ${PWD/#\/mnt\/c\/Users\/escar/\~} ...`

---

### Step 4: Save and Close the Editor

Press these keyboard shortcuts sequentially to save your file:

1. Press **`Ctrl + O`** (To write the changes).
2. Press **`Enter`** (To confirm the filename).
3. Press **`Ctrl + X`** (To safely close the editor).

---

### Step 5: Refresh Your Terminal

To force Linux to read your new configuration right away without closing the window, type:

* **For Bash users:** `source ~/.bashrc`
* **For Zsh users:** `source ~/.zshrc`

---

##  Speed Test: How to Use It

You no longer need to type long paths like `cd /mnt/c/Users/...` anymore.

To test your new superpower, move into a deep, restrictive Linux system directory first:

```bash
cd /etc/apt

```

Now, execute the shortcut from that remote directory:

```bash
cd Downloads

```

**Result:** Your terminal context instantly teleports straight to your Windows Downloads directory.


* Instead of the long `/mnt/c/Users/username/Downloads` path, your prompt will display a clean, native-looking `[~/Downloads]`.

---

## Bonus: Hide the Annoying Kali Developer Banner

If your Kali Linux terminal spams you with a large minimum installation message every time you open it, you can silence it permanently.

Run this single command in your terminal:

```bash
touch ~/.hushlogin

```

*Close your terminal and open it again. The banner is now gone forever!*

