Virtual Environment Setup Documentation (Ubuntu/Debian)
What is a Virtual Environment?
A virtual environment is an isolated Python environment that allows you to install packages without affecting the system-wide Python installation. It’s useful for managing dependencies on a per-project basis.

Prerequisites
Ubuntu/Debian-based system

Python 3 installed (python3 --version)

pip installed (pip3 --version)

Installation Steps
1. Install venv (if not already installed)
bash
Copy
Edit
sudo apt update
sudo apt install python3-venv -y
2. Create a Virtual Environment
Navigate to your project folder:

bash
Copy
Edit
cd ~/myproject
Now create a virtual environment named .venv:

bash
Copy
Edit
python3 -m venv .venv
This will create a .venv/ folder inside your project containing the isolated environment.

3. Activate the Virtual Environment
On Linux/macOS:

bash
Copy
Edit
source .venv/bin/activate
On Windows (CMD):

cmd
Copy
Edit
.venv\Scripts\activate.bat
You’ll notice the terminal prompt changes to show the environment is active, e.g.,
(.venv) user@system:~/myproject$

4. Install Python Packages
While the virtual environment is active:

bash
Copy
Edit
pip install flask requests pandas
5. Freeze Requirements (optional but recommended)
To save the environment's dependencies in a file:

bash
Copy
Edit
pip freeze > requirements.txt
6. Deactivate the Environment
To exit the virtual environment:

bash
Copy
Edit
deactivate
Typical Project Structure
bash
Copy
Edit
myproject/
├── .venv/              # Virtual environment directory
├── app.py              # Main Python script
├── requirements.txt    # List of dependencies
└── README.md
Always add .venv/ to .gitignore so it doesn't get pushed to GitHub.

Use requirements.txt to recreate the same environment later:

bash
Copy
Edit
pip install -r requirements.txt
If you're using VS Code, it auto-detects .venv and activates it.

References
Python venv Docs: https://docs.python.org/3/library/venv.html
