
##  Virtual Environment Setup Documentation

---

** What is a Virtual Environment?**
 A **virtual environment** in Python is an isolated workspace that allows you to install packages without affecting the system-wide Python or other virtual environments. It's essential for avoiding version conflicts across different projects.

---

** Why Use Virtual Environments?**
 Keeps dependencies isolated per project
 Prevents conflicts between package versions
 Helps maintain clean and reproducible setups
 Ideal for team collaboration and deployment

---

** Prerequisites**
 Make sure you have Python 3 installed. You can verify using:

```bash
python3 --version
```

---

** Step-by-Step Setup Instructions**

1. **Install `venv` module** (if not already installed):

```bash
sudo apt install python3-venv
```

2. **Create a Virtual Environment**

```bash
python3 -m venv venv_name
```

 This creates a directory named `venv_name` containing the isolated environment.

3. **Activate the Virtual Environment**

* On **Linux/macOS**:

```bash
source venv_name/bin/activate
```

* On **Windows (CMD)**:

```cmd
venv_name\Scripts\activate.bat
```

* On **Windows (PowerShell)**:

```powershell
venv_name\Scripts\Activate.ps1
```

4. **Verify Activation**
   You should see the environment name in your terminal prompt:

```bash
(venv_name) user@hostname:~$
```

5. **Install Python Packages** (inside the virtual env)

```bash
pip install <package_name>
```

6. **Deactivate the Environment**

```bash
deactivate
```

---

** Managing Requirements**
 To freeze current packages into a requirements file:

```bash
pip freeze > requirements.txt
```

 To install packages from a file:

```bash
pip install -r requirements.txt
```

---

** Common Issues & Fixes**

| Issue                                | Solution                                           |
| ------------------------------------ | -------------------------------------------------- |
| `command not found: python3`         | Install Python: `sudo apt install python3`         |
| `venv module not found`              | Install it: `sudo apt install python3-venv`        |
| Activation not working on PowerShell | Run: `Set-ExecutionPolicy RemoteSigned` (as Admin) |

---

** Tips**
 Use `.venv` as a convention to name your environment and add it to `.gitignore` to avoid committing it.

```bash
echo ".venv/" >> .gitignore
```

---

** Reference Links**
 Python venv Docs: [https://docs.python.org/3/library/venv.html](https://docs.python.org/3/library/venv.html)
 pip Docs: [https://pip.pypa.io/](https://pip.pypa.io/)

---

