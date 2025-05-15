
# ⚡ Getting Started with **`uv`** – A Fast Python Project Manager

**uv** is a extremely fast Python package and project manager written in Rust. 

This guide helps you get started with `uv` on **macOS**, but the steps are applicable to other operating systems too. If you're using Windows or Linux, just copy the commands and search online for OS-specific alternatives. For complete and up-to-date information, refer to the [official uv documentation](https://docs.astral.sh/uv).

> ⚠️ While AI models like ChatGPT, Google Gemini or Anthropic Claude can help, always cross-reference with the [official uv documentation](https://docs.astral.sh/uv) to ensure accuracy.

---

## 📦 1. Installing `uv`

You can install `uv` using either a **standalone installer** or a **package manager**.

### ✅ Option 1: Standalone Installer

Install directly using `curl`:

```sh
curl -LsSf https://astral.sh/uv/install.sh | sh
```

📚 [Read More info on the standalone installer →](https://docs.astral.sh/uv/getting-started/installation/#standalone-installer)

---

### ✅ Option 2: Using a Package Manager (Recommended on macOS)

On macOS, we’ll use [**Homebrew**](https://brew.sh/):

1. **Install Homebrew** (if not already installed):

   ```sh
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. **Install `uv`** via Homebrew:

   ```sh
   brew install uv
   ```

For Linux or Windows, check out:

* [APT (Linux)](https://documentation.ubuntu.com/server/how-to/software/package-management/index.html)
* [Chocolatey (Windows)](https://chocolatey.org/install)

---

## 🚀 2. Using `uv`

After installation, verify that `uv` is available:

```sh
uv
```

You’ll see a list of available commands like:

```bash
An extremely fast Python package manager.

Usage: uv [OPTIONS] <COMMAND>

Commands:
  run      Run a command or script
  init     Create a new project
  add      Add dependencies
  remove   Remove dependencies
  sync     Update project environment
  ...
```

---

## 🐍 2.1 Installing Python

`uv` can manage Python versions directly—no manual installation needed!

### 🔧 Common Commands

```sh
uv python list            # View available versions
uv python install 3.12    # Install a specific version
uv python uninstall 3.12  # Remove a version
uv python find            # Find an installed Python
```

### 🧪 Examples

```sh
uv python install 3.11 3.12     # To install multiple Python versions
uv python install pypy@3.10     # To install an alternative Python implementation, e.g., PyPy
uv python list --all-versions   # To view all versions
uv python find '>=3.11'         # To find a Python executable that has a version of 3.11 or newer
uv python find --system         # To ignore virtual environments, use the --system flag
```

---

## 📁 2.2 Creating a Project

Initialize a new project:

```sh
uv init uv-tutorial-guide
cd uv-tutorial-guide
```

Or manually:

```sh
mkdir uv-tutorial-guide
cd uv-tutorial-guide
uv init
```

This will generate:

```
.
├── .python-version
├── README.md
├── main.py
└── pyproject.toml
```

Run the default script:

```sh
uv run main.py
```

---

## 🧪 2.3 Creating a Virtual Environment

To create a new virtual environment:

```sh
uv venv
```

Specify a Python version:

```sh
uv venv --python 3.11.6
```

Activate it:

```sh
source .venv/bin/activate
```

Or, Alternatively, just run without activation:

```sh
uv run main.py
```

---

## 🏗️ 2.4 Project Structure

Once initialized, your project may look like this:

```
.
├── .venv
│   ├── bin
│   └── ...
├── .python-version
├── README.md
├── main.py
├── pyproject.toml
└── uv.lock
```

### 📌 Key Files

* **`pyproject.toml`** – Project metadata and dependencies.
* **`.python-version`** – Specifies the default Python version.
* **`.venv/`** – Local virtual environment.
* **`uv.lock`** – Lockfile with resolved dependencies versions

> ⚠️ Do not manually edit `uv.lock`. It’s managed by `uv`.

---

## 📦 2.5 Managing Dependencies

### ➕ Add Dependencies

```sh
uv add requests
uv add 'requests==2.31.0'
```

From a `requirements.txt`:

```sh
uv add -r requirements.txt
```

### ➖ Remove Dependencies

```sh
uv remove requests
```

### 🔁 Modify or Upgrade

```sh
uv add 'requests>2.15'
uv lock --upgrade-package requests
```

---

## ⚙️ 2.6 Running Commands

Run scripts or commands in your project's environment:

```sh
uv run example.py
```

Or:

```sh
uv add flask
uv run -- flask run -p 3000
```

---

## ✅ Summary

With `uv`, managing Python projects becomes faster and more efficient. Whether you're setting up Python, managing virtual environments, or handling dependencies, `uv` offers a seamless and modern workflow.

🔗 **Explore more in the [official documentation](https://docs.astral.sh/uv)**