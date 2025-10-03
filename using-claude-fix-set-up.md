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
