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