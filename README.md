
#  Virtual Environment Setup Documentation (Ubuntu/Debian)

---

## Version History

| Author      | Created on | Version   | Last updated by | Internal Reviewer |
|-------------|------------|-----------|------------------|--------------------|
| Anuj Jain   | 17-07-25   | version 1 | N/A              | Prashnat           |

---


##  Table of Contents

1. [What is a Virtual Environment?](#-what-is-a-virtual-environment)
2. [Prerequisites](#-prerequisites)
3. [Installation Steps](#-installation-steps)

   * [Install `venv`](#1-install-venv-if-not-already-installed)
   * [Create a Virtual Environment](#2-create-a-virtual-environment)
   * [Activate the Virtual Environment](#3-activate-the-virtual-environment)
   * [Install Python Packages](#4-install-python-packages)
   * [Freeze Requirements](#5-freeze-requirements-optional-but-recommended)
   * [Deactivate the Environment](#6-deactivate-the-environment)
4. [Typical Project Structure](#-typical-project-structure)
5. [Notes & Best Practices](#-notes--best-practices)
6. [References](#-references)

---

##  What is a Virtual Environment?

A **virtual environment** is an isolated Python environment that allows you to install packages without affecting the system-wide Python installation. It’s useful for managing dependencies on a per-project basis.

---

##  Prerequisites

* Ubuntu/Debian-based system
* Python 3 installed (`python3 --version`)
* `pip` installed (`pip3 --version`)

---

## 🛠️ Installation Steps

### 1. Install `venv` (if not already installed)

```bash
sudo apt update
sudo apt install python3-venv -y
```

### 2. Create a Virtual Environment

Navigate to your project folder:

```bash
cd ~/myproject
```

Now create a virtual environment named `.venv`:

```bash
python3 -m venv .venv
```

>  This will create a `.venv/` folder inside your project containing the isolated environment.

---

### 3. Activate the Virtual Environment

* **On Linux/macOS:**

```bash
source .venv/bin/activate
```

* **On Windows (CMD):**

```cmd
.venv\Scripts\activate.bat
```

>  You’ll notice the terminal prompt changes to show the environment is active, e.g.,
> `(.venv) user@system:~/myproject$`

---

### 4. Install Python Packages

While the virtual environment is active:

```bash
pip install flask requests pandas
```

---

### 5. Freeze Requirements (optional but recommended)

To save the environment's dependencies in a file:

```bash
pip freeze > requirements.txt
```

---

### 6. Deactivate the Environment

To exit the virtual environment:

```bash
deactivate
```

---

## Typical Project Structure

```
myproject/
├── .venv/              # Virtual environment directory
├── app.py              # Main Python script
├── requirements.txt    # List of dependencies
└── README.md
```

---

##  Notes & Best Practices

* Always **add `.venv/` to `.gitignore`** so it doesn't get pushed to GitHub.
* Use `requirements.txt` to recreate the same environment later:

```bash
pip install -r requirements.txt
```

* If you're using VS Code, it auto-detects `.venv` and activates it.

---

## Contact Information

| Name      | Email Address                                               |
| --------- | ----------------------------------------------------------- |
| Anuj Jain | [anuj.jain@mygurukulam.co](mailto:anuj.jain@mygurukulam.co) |

---


## References

* **Python venv Docs**: [https://docs.python.org/3/library/venv.html](https://docs.python.org/3/library/venv.html)
* **pip Docs**: [https://pip.pypa.io/en/stable/](https://pip.pypa.io/en/stable/)

---

