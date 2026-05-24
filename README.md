

# WSL2 Global Folder Shortcut Setup
A guide to jumping from deep Linux directories straight to your Windows folders (`Downloads`, `Desktop`, `Documents`) with a single command.

---

## Before You Begin: Find Your Windows Username
Every Windows computer has a unique user folder. We need to find yours first.

1. Open your **Kali/Ubuntu Linux terminal**.
2. Type this command and press **Enter**:
```bash
   ls /mnt/c/Users

```

3. Look at the output names (e.g., `escar`, `alex`, `john`).
4. **Copy or write down your specific name.** You will need it in Step 3.

---

## Step-by-Step Installation

### Step 1: Open the Configuration File

Linux keeps terminal settings in a hidden file. We will open it using a terminal text editor called `nano`.

Type this command and press **Enter**:

```bash
nano ~/.zshrc

```

> *Note: If you are using an older version of Linux that defaults to Bash instead of Zsh, use `nano ~/.bashrc` instead.*

---

### Step 2: Go to the Bottom of the File

* Press and hold the **Down Arrow Key (↓)** on your keyboard.
* Keep holding it until the cursor reaches the **very end** of the file where there is empty space.

---

### Step 3: Paste the Shortcut Code

Copy the line below and paste it into that blank space at the bottom:

```bash
export CDPATH=".:/mnt/c/Users/YOUR_WINDOWS_USERNAME"

```

 **CRITICAL CHANGE:**
Delete the text `YOUR_WINDOWS_USERNAME` and type the exact name you discovered during the **Before You Begin** phase.

* **Correct Example:** `export CDPATH=".:/mnt/c/Users/escar"`
* **Incorrect Example:** `export CDPATH=".:/mnt/c/Users/YOUR_WINDOWS_USERNAME"`

---

### Step 4: Save and Close the Editor

Press these keyboard shortcuts sequentially to save your file:

1. Press **`Ctrl + O`** (To write the changes).
2. Press **`Enter`** (To confirm the filename).
3. Press **`Ctrl + X`** (To safely close the editor).

---

### Step 5: Refresh Your Terminal

To force Linux to read your new configuration right away without closing the window, type:

```bash
source ~/.zshrc

```

> *Note: If you edited `.bashrc` in Step 1, run `source ~/.bashrc` instead.*

---

## Speed Test: How to Use It

You no longer need to type long paths like `cd /mnt/c/Users/...` anymore.

To test your new superpower, move into a deep, restrictive Linux system directory first:

```bash
cd /etc/apt

```

Now, execute the shortcut from that remote directory:

```bash
cd Downloads

```

**Result:** Your terminal context instantly teleports straight to your Windows Downloads directory. You can now use `cd Desktop` or `cd Documents` globally from any folder in your system.

