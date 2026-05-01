# ASIC2026 — Setup Guide

This guide walks you through everything you need to run **`sensor_correction_ASIC.ipynb`** on your own laptop. The notebook is a hands-on tutorial that calibrates a PurpleAir low-cost sensor against US Embassy reference data using multiple linear regression in Python.

If you already have Jupyter Notebooks setup on your laptop, you can probably skip most of this. No prior Python experience is required to follow these setup steps.

---

## 1. Install Anaconda

Anaconda is a free Python distribution that comes bundled with Jupyter Notebook and almost every scientific package this tutorial uses. One installer gives you everything.

1. Go to the official download page: **https://www.anaconda.com/download**
2. Choose the installer for your operating system (Windows, macOS, or Linux). On macOS, pick the version that matches your chip — Apple Silicon (M1/M2/M3/M4) or Intel.
3. Run the installer and accept the default options. When prompted:
   - **Windows**: leave "Add Anaconda to my PATH" *unchecked* (the default) and let it register Anaconda as your default Python.
   - **macOS / Linux**: accept the default install location and let the installer run `conda init` at the end.
4. After it finishes, **close and reopen your terminal** (or open a fresh **Anaconda Prompt** on Windows). This is required for the `conda` command to be picked up.

Verify it worked:

```bash
conda --version
```

You should see something like `conda 24.x.x`. If you get "command not found," reopen the terminal once more — on Windows, use **Anaconda Prompt** specifically, not regular Command Prompt or PowerShell.

---

## 2. Download the notebook

You have two options.

**Option A — Download as a ZIP (easiest):**
1. Go to https://github.com/dmw2166/ASIC2026
2. Click the green **Code** button, then **Download ZIP**.
3. Unzip it somewhere convenient (e.g. your Desktop or Documents folder).

**Option B — Clone with git** (if you already have git installed):

```bash
git clone https://github.com/dmw2166/ASIC2026.git
```

Either way, you should end up with a folder called `ASIC2026` containing `sensor_correction_ASIC.ipynb`.

---

## 3. Create an environment and install the required packages

The notebook uses these libraries:

| Package | Used for |
|---|---|
| `pandas` | Loading and reshaping the sensor data |
| `matplotlib` | Plotting time series and diurnal profiles |
| `scipy` | Linear regression statistics |
| `scikit-learn` | The multiple linear regression model and train/test split |
| `fsspec` + `aiohttp` | Streaming the zipped PurpleAir CSVs directly from a URL |
| `jupyter` | Running the notebook itself |

You can either install these into Anaconda's default `base` environment or create a dedicated one. A dedicated environment is cleaner and is the recommended approach.

Open a terminal (**Anaconda Prompt** on Windows) and run:

```bash
conda create -n asic2026 python=3.13 pandas matplotlib scipy scikit-learn fsspec aiohttp jupyter -c conda-forge -y
conda activate asic2026
```

The first command builds a new environment called `asic2026` and installs everything in one shot. The second one activates it — you'll see `(asic2026)` appear at the start of your prompt.

> **Tip:** every time you open a new terminal to work on this tutorial, you'll need to run `conda activate asic2026` first.

---

## 4. Launch Jupyter and open the notebook

With the environment activated, navigate to the folder where you put the notebook and start Jupyter:

```bash
cd path/to/ASIC2026
jupyter notebook
```

Replace `path/to/ASIC2026` with the actual path on your machine. For example:

- **Windows**: `cd C:\Users\YourName\Downloads\ASIC2026`
- **macOS / Linux**: `cd ~/Downloads/ASIC2026`

A browser tab will open showing the contents of the folder. Click **`sensor_correction_ASIC.ipynb`** to open it.

If you'd rather use **JupyterLab** (a more modern interface that's also included with Anaconda), use `jupyter lab` instead.

---

## 5. Run the notebook

Once the notebook is open, run the cells one at a time using **Shift + Enter**, or run everything at once via the menu: **Cell → Run All** (in classic Jupyter) or **Run → Run All Cells** (in JupyterLab).

The first code cell loads PurpleAir data from a remote zip file, so make sure you have an active internet connection the first time you run it.

---

## Troubleshooting

**`ModuleNotFoundError: No module named 'fsspec'`** (or any other package)
You probably opened the notebook in the wrong environment. Confirm by running `import sys; print(sys.executable)` in a notebook cell — the path should contain `asic2026`. If it doesn't, shut down Jupyter, run `conda activate asic2026` in your terminal, and relaunch with `jupyter notebook`.

**The notebook hangs on the first data-loading cell**
That cell streams a zip file over HTTP. If it never completes, check your internet connection or any corporate firewall / VPN that might block the download.

**`jupyter: command not found` after activating the environment**
The environment was created without Jupyter. Install it now: `conda install jupyter -y`.

**Anaconda installer is too large or fails to install**
A lighter alternative is **Miniconda** (https://www.anaconda.com/docs/getting-started/miniconda/install). All of the `conda create` commands above work identically with Miniconda.

---

## Quick reference

```bash
# one-time setup
conda create -n asic2026 python=3.13 pandas matplotlib scipy scikit-learn fsspec aiohttp jupyter -c conda-forge -y

# every time you work on the tutorial
conda activate asic2026
cd path/to/ASIC2026
jupyter notebook
```
