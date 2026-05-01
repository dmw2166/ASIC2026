# ASIC2026 Python coding — Pre-Workshop Setup

Before the workshop, please complete the steps below so you arrive ready to code along. The whole process takes about 15 minutes.

By the end you will have:
1. Anaconda installed
2. A blank Jupyter notebook open in your browser
3. Confirmed that the packages we'll use are working

---

## 1. Install Anaconda

Anaconda is a free Python distribution that comes with Jupyter Notebook and almost every package we'll need already included.

1. Go to **https://www.anaconda.com/download**. You can skip the email signup by clicking *Skip registration*.
2. Download the installer for your operating system. On macOS, choose the version matching your chip — Apple Silicon (M1/M2/M3/M4) or Intel. If you're unsure, click the Apple menu → *About This Mac* and look at "Chip."
3. Run the installer and accept all the default options. It's a large download (~700 MB) and may take several minutes to install.

---

## 2. Open Anaconda Navigator

Anaconda Navigator is the graphical app that lets you launch Jupyter without touching a terminal.

- **Windows**: Open the Start Menu and search for *Anaconda Navigator*.
- **macOS**: Open Launchpad or your Applications folder and click *Anaconda Navigator*.
- **Linux**: Open your applications menu and search for *Anaconda Navigator*.

The first launch can take 30–60 seconds. You'll see a window with several tiles, one of which is **Jupyter Notebook**.

---

## 3. Launch Jupyter Notebook

In Anaconda Navigator, find the **Jupyter Notebook** tile and click the **Launch** button beneath it.

A new tab will open in your default browser showing a file browser. You're now looking at the contents of your home folder (Documents, Downloads, etc.). Don't close the small black terminal-looking window that opens in the background; that's the Jupyter server, and closing it will shut Jupyter down.

---

## 4. Create a new blank notebook

In the Jupyter file browser:

1. Navigate into a folder where you'd like to save your work, for example, *Documents* or *Desktop*. You can click into folders just like in any file explorer.
2. In the top-right corner, click **New**, then choose **Python 3 (ipykernel)**.

A blank notebook will open in a new tab. This is what we'll be coding in during the workshop. Feel free to rename it from "Untitled" by clicking the title at the top of the page.

---

## 5. Confirm the packages work

To make sure everything we'll use during the live demo is installed, click into the first empty cell of your new notebook, paste the code below, and press **Shift + Enter** to run it:

```python
import pandas
import matplotlib
import scipy
import sklearn
import fsspec
import aiohttp

print("All packages loaded successfully")
```

If you see `All packages loaded successfully` with no error messages, you're done — close the notebook and you're ready for the workshop.

If you instead see `ModuleNotFoundError: No module named '...'` for any package, jump to the troubleshooting section below.

---

## Troubleshooting

**`ModuleNotFoundError: No module named 'aiohttp'` (or any other package)**

The package isn't installed in your environment yet. The easiest fix is to install it from inside the notebook itself. In a new cell, paste this — replacing `aiohttp` with whichever package was missing — and run it:

```python
%pip install aiohttp
```

After it finishes, restart the kernel by going to **Kernel → Restart** in the menu, then re-run the import cell from step 5.

If multiple packages are missing, you can install them all at once:

```python
%pip install pandas matplotlib scipy scikit-learn fsspec aiohttp
```


---

## You're all set

See you at the workshop. If you run into any issues with these steps, please come a few minutes early so we can sort them out before the live demo starts.
