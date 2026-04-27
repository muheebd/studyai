# 🚀 StudyAI — Deployment Guide
## Making the App Live on the Internet

---

## Option A — Railway (Recommended, Fastest)

Railway gives you a free public URL like `studyai-production.up.railway.app`

### Steps:

**1. Create a free GitHub account**
- Go to github.com → Sign Up (free)

**2. Create a new GitHub repository**
- Click the **+** button top-right → New repository
- Name it: `studyai`
- Set to **Public**
- Click **Create repository**

**3. Upload the project files to GitHub**
- On your new repo page, click **uploading an existing file**
- Drag ALL files from this folder into the browser window
- Make sure you upload the `frontend/` folder too
- Click **Commit changes**

**4. Create a free Railway account**
- Go to **railway.app** → Login with GitHub

**5. Deploy on Railway**
- Click **New Project**
- Click **Deploy from GitHub repo**
- Select your `studyai` repository
- Railway detects Python automatically and deploys
- Wait ~2 minutes for the build to finish

**6. Get your live URL**
- In Railway dashboard, click your project
- Click **Settings** → **Domains**
- Click **Generate Domain**
- Your app is now live at that URL! Share it with your supervisor.

---

## Option B — Render (Also Free)

**1–3. Same as above** — create GitHub account and upload files

**4. Go to render.com** → Sign up with GitHub

**5. Click New → Web Service**
- Connect your GitHub repo
- Render detects the `render.yaml` file automatically
- Build command: `pip install -r requirements.txt`
- Start command: `python server.py`
- Click **Create Web Service**

**6. Get your URL**
- Render gives you a URL like `studyai.onrender.com`
- Free tier may sleep after 15 min of inactivity (wakes on first visit)

---

## Important Notes

### Database
- The live app uses a SQLite file (`studyai.db`) stored on the server
- Railway and Render **do not persist files between redeploys**
- For a final production app, upgrade to PostgreSQL (free on Railway)
- For demo / presentation purposes, SQLite is perfectly fine

### Environment Variables
- Railway and Render automatically set the `PORT` variable
- The server reads `PORT` automatically — no changes needed

### Sharing the App
Once deployed, anyone with the URL can:
- Register a student account
- Register a lecturer account
- Use the full AI semester planning system

---

## Running Locally (for testing before deploy)

```bash
# Install dependencies (once)
pip install scikit-learn numpy

# Start the server
python server.py

# Open in browser
# http://localhost:8000         → Homepage
# http://localhost:8000/student → Student Portal
# http://localhost:8000/admin   → Admin Portal
```

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Build fails on Railway | Check the build logs — usually a missing dependency |
| "Module not found: sklearn" | Make sure `requirements.txt` is uploaded |
| App crashes on start | Check Railway logs for the error message |
| Database resets on redeploy | Expected on free tier — use PostgreSQL for persistence |

---

*StudyAI — Al-Hikmah University · January 2026*
*Bello Muhammad · Ahmed Abdulbaqqi · Abdulrazak Yahaya*
*Supervised by Engr. Mrs. Aishat Jimoh-Mahmud*
