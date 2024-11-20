# Deploying a FastAPI Application on Render

Here’s how you can deploy your FastAPI application on Render step-by-step:

## Step 1: Prepare Your Project Locally

1. **Set up a Virtual Environment**:
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # Activate on Linux/Mac
   .\.venv\Scripts\activate   # Activate on Windows
   ```

2. **Create Project Structure**:
   ```
   my_fastapi_project/
   ├── main.py              # FastAPI application entry point
   ├── requirements.txt     # Python dependencies
   ├── .gitignore           # Files to ignore in Git
   └── .venv/               # Virtual environment folder (optional)
   ```

3. **Add Dependencies**:
   Create a `requirements.txt` file listing your project dependencies:
   ```
   fastapi
   uvicorn
   ```

4. **Run Locally**:
   Test the app locally:
   ```bash
   uvicorn main:app --reload
   ```
   Visit [http://127.0.0.1:8000](http://127.0.0.1:8000) to verify it works.

---

## Step 2: Push to GitHub

1. **Initialize Git**:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   ```

2. **Push to GitHub**:
   - Create a repository on GitHub.
   - Link your project to GitHub:
     ```bash
     git remote add origin <your-repo-url>
     git branch -M main
     git push -u origin main
     ```

---

## Step 3: Deploy on Render

1. **Login to Render**:
   Go to [Render](https://render.com) and log in.

2. **Create a New Web Service**:
   - Click `New +` > **Web Service**.

3. **Connect GitHub Repository**:
   - Link your Render account to GitHub.
   - Select your FastAPI repository.

4. **Configure Deployment**:
   - **Environment**: Python
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `uvicorn main:app --host 0.0.0.0 --port 10000`
   - **Branch**: `main` (or your default branch)

5. **Add Environment Variables**:
   Add variables like:
   - `DATABASE_URL`
   - `API_KEYS`
   - `SECRET_CONFIGURATIONS`

6. **Deploy**:
   Click **Deploy Web Service**. Render will build and deploy your app.

---

## Step 4: Debugging and Updating

- If deployment issues occur:
  1. Fix the problem in your code.
  2. Push the changes to GitHub:
     ```bash
     git add .
     git commit -m "Fix issue"
     git push origin main
     ```
  3. Render will auto-redeploy.

- When successful, you’ll see a **green checkmark** in Render.

---

## Example `main.py`

Here’s an example `main.py` file:
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello, World! Welcome to my FastAPI app on Render."}
```

---

## Summary

1. Prepare your FastAPI app.
2. Push the project to GitHub.
3. Deploy on Render and configure settings.
4. Debug and update if necessary.

**Live URL**: Once deployed, your app will be live at `[https://your-app-name.onrender.com](https://doctor-recommendation-system.onrender.com/docs)`.

🎉 Happy coding!
```

