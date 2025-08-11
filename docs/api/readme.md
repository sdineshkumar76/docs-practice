# docs-practice

## Installation & Setup
### Install MkDocs
pip install mkdocs

###  (Optional) Install Material theme for better design
pip install mkdocs-material

### Check installation
mkdocs --version

## Basic Commands mkdocs
bash
Copy
Edit

### Create a new MkDocs project in current folder
mkdocs new .

### Start local server for preview
mkdocs serve

### Stop the server
CTRL + C

## File Structure

.
├── mkdocs.yml      # Config file for the site
└── docs/           # All your documentation (.md files)
    ├── index.md    # Homepage
    └── api/        # API docs folder
        └── readme.md

## MkDocs + GitHub Pages + GitHub Actions

### Step 1 — Install the deploy plugin
In your Codespaces terminal:

bash
Copy
Edit
pip install mkdocs ghp-import
mkdocs → the site generator

ghp-import → sends the built site to GitHub Pages

### Step 2 — Update mkdocs.yml
Open:

bash
Copy
Edit
nano mkdocs.yml
At the bottom, add:

yaml
Copy
Edit
site_url: https://<your-github-username>.github.io/<your-repo-name>/
Example:

yaml
Copy
Edit
site_url: https://sdineshkumar76.github.io/api-docs-demo/
Save with CTRL + O, then CTRL + X.

### Step 3 — Create GitHub Action
In terminal:

bash
Copy
Edit
mkdir -p .github/workflows
nano .github/workflows/deploy.yml
Paste this:

yaml
Copy
Edit
name: Deploy MkDocs site to GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: 3.x
      - run: pip install mkdocs ghp-import
      - run: mkdocs build
      - run: ghp-import -n -p -f site
Save and exit.

### Step 4 — Push changes
bash
Copy
Edit
git add .
git commit -m "Set up auto-deploy"
git push origin main
Step 5 — Wait for GitHub Pages
Go to your repo Settings → Pages

Set the branch to gh-pages (if not already done)

Wait 1–2 min, your site will be live.

this is the change for the new branch