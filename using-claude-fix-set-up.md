## 1. Fix Set up

I want Claude to:

Automatically run the application.

Detect any missing dependencies, configurations, or setup issues.

Automatically resolve and fix what is missing so the app can run successfully.


## 1.1 Set-up Prompt

You are now acting as a Python setup automation agent for the Orchestra-AI project.

Your tasks:
1. Automatically launch the Streamlit app located at `streamlit_app/main.py`.
2. Detect and report any missing Python packages, broken imports, or configuration issues.
3. Automatically generate and suggest commands to install missing dependencies or fix setup errors.
4. Create any required folders or files that are missing (e.g., `templates_cache/`, `artifacts/`, `.env`).
5. Confirm when the app is running successfully at `http://localhost:8501`.

Environment:
- I’m using Visual Studio Code v1.104.0 on Windows.
- Python is installed and I’ve created a virtual environment.
- I’m a beginner, so please explain each step clearly and guide me through running the commands manually.

Start by checking the project structure and launching the app. Then walk me through resolving any issues you find.


## 2 Ask Claude to Help Diagnose
You can now ask Claude:
“Claude, I’m getting [Errno 13] Permission denied when creating a virtual environment in specsync_ai. I’ve deleted the folder, disabled antivirus, and run VS Code as admin. What else can I try?”

Claude may suggest checking NTFS permissions, using icacls, or inspecting locked processes.

Let me know if you want a .bat script to automate this cleanup and venv creation. I can also help you move the project to a clean folder if needed.

### 2.1 Claude Setup Fix Prompt

Claude, Orchestra-AI is still referencing the old Python path from a different machine:

Old path:
C:\Users\SC06313\AppData\Local\Programs\Python\Python311\python.exe

On my current machine, Python is correctly installed and available at:
C:\Users\baloy> python --version → Python 3.11.9

Task:
1. Identify where Orchestra-AI is still referencing the old path (e.g., virtual environment, config files, launch scripts).
2. Update all references so Orchestra-AI uses the correct Python installation on this machine.
3. Regenerate or reconfigure the virtual environment if needed.
4. Confirm the correct path is being used and the app can launch successfully.

I’m using Visual Studio Code on Windows and I’m a beginner, so please guide me step-by-step and explain each fix clearly.


