# Beginner Friendly React + GitHub Workflow Notes

This guide shows the complete workflow from creating a React project to pushing code to GitHub.

Follow the steps in order.

Do not skip steps.

Every section contains:

* command
* what the command does
* possible error
* reason
* fix

This makes the workflow easier to understand and avoids confusion.

---

# Simple React + GitHub Workflow Notes

# Step 1 — Open Desktop Folder

### Command

```bash
cd ~/OneDrive/Desktop
```

## What this command does

This step is important before moving to the next step.

* Moves the terminal to the Desktop folder.
* Your project will now be stored on the Desktop.

## Possible Error

```bash
No such file or directory
```

## Reason

* OneDrive Desktop path may not exist.

## Fix

```bash
cd ~/Desktop
```

---

# Step 2 — Clone GitHub Repository

### Command

```bash
git clone https://github.com/USERNAME/REPO.git
```

## Example

```bash
git clone https://github.com/pawan902670-glitch/Frontend.git
```

## What this command does

* Downloads the GitHub repository to your computer.
* Creates a folder with the repository name.

## Possible Error

```bash
fatal: destination path already exists
```

## Reason

* A folder with the same name already exists.

## Fix

* Delete or rename the old folder.
* Or clone using a different folder name.

Example:

```bash
git clone REPO-LINK Frontend-New
```

---

# Step 3 — Open Repository Folder

### Command

```bash
cd Frontend
```

## What this command does

* Opens the repository folder in terminal.

---

# Step 4 — Create React Project

### Command

```bash
npm create vite@latest
```

## Select Options

```text
Project Name: Quizz-project
Framework: React
Variant: JavaScript
```

## What this command does

* Creates a React + Vite project.

## Possible Error

```bash
npm is not recognized
```

## Reason

* Node.js is not installed.

## Fix

* Install Node.js from:
  [https://nodejs.org](https://nodejs.org)

---

# Step 5 — Open React Project Folder

### Command

```bash
cd Quizz-project
```

## What this command does

* Opens the React project folder.

---

# Step 6 — Install Packages

### Command

```bash
npm install
```

## What this command does

* Installs all required project packages.
* Creates the node_modules folder.

---

# Step 7 — Run React Project

### Command

```bash
npm run dev
```

## What this command does

* Starts the React development server.
* Opens the app in browser.

## Possible Error

```bash
Port already in use
```

## Reason

* Another project is already running.

## Fix

* Stop old terminal/server.
* Or restart VS Code.

---

# Step 8 — Open VS Code

### Command

```bash
code .
```

## What this command does

* Opens the current project in VS Code.

## Possible Error

```bash
code is not recognized
```

## Fix

* Install VS Code terminal command.
* Open VS Code → Ctrl + Shift + P
* Type:

```text
Shell Command: Install 'code' command in PATH
```

---

# Step 9 — Important Files

## React UI File

```text
src/App.jsx
```

## CSS File

```text
src/App.css
```

## Global CSS

```text
src/index.css
```

## Main Entry File

```text
src/main.jsx
```

## What to do

* Write your React code inside these files.

---

# Step 10 — Check Changed Files

### Command

```bash
git status
```

## What this command does

* Shows changed files.
* Shows untracked files.

---

# Step 11 — Add Files

### Command

```bash
git add .
```

## What this command does

* Adds all changed files to Git staging area.

## Important

* No output after command is normal.

## Possible Warning

```bash
LF will be replaced by CRLF
```

## Reason

* Windows line-ending warning.
* Not an error.

## Fix

```bash
git config --global core.autocrlf true
```

---

# Step 12 — Commit Changes

### Command

```bash
git commit -m "Updated project"
```

## What this command does

* Saves a snapshot of current changes.

---

# Step 13 — Push to GitHub

### Command

```bash
git push origin main
```

## What this command does

* Uploads local commits to GitHub.

## Possible Error

```bash
failed to push some refs
```

## Reason

* GitHub repository has new changes.

## Fix

```bash
git pull origin main
```

Then run:

```bash
git push origin main
```

---

# Merge Conflict Error

## Error

```bash
unmerged paths
```

## Reason

* Same files changed in both local and GitHub.

## Fix

```bash
git add .
git commit -m "Merge resolved"
```

---

# node_modules Delete Error

## Error

```bash
Deletion of directory node_modules failed
```

## Reason

* VS Code or npm server is using node_modules.

## Fix

* Close VS Code.
* Stop npm run dev.
* Delete node_modules manually.

---

# Important Rule

## .gitignore file should contain

```text
node_modules
dist
```

## Reason

* node_modules should never be pushed to GitHub.

---

# Simple Daily Workflow

Whenever you start coding:

1. Open the project folder
2. Pull latest changes
3. Write your code
4. Add files
5. Commit changes
6. Push to GitHub

Commands:

```bash
git pull origin main
git add .
git commit -m "Updated UI"
git push origin main
```

---

# Daily Workflow

## Before Starting Work

```bash
git pull origin main
```

## After Completing Work

```bash
git add .
git commit -m "Updated UI"
git push origin main
```

---

# Final Folder Structure

```text
Desktop/
│
└── Frontend/
    │
    ├── README.md
    │
    └── Quizz-project/
        │
        ├── src/
        ├── public/
        ├── node_modules/
        ├── package.json
        ├── package-lock.json
        └── vite.config.js
```

````text
Desktop/
│
└── Frontend/
    │
    ├── README.md
    │
    └── Quizz-project/
        │
        ├── src/
        ├── public/
        ├── node_modules/
        ├── package.json
        ├── package-lock.json
        └── vite.config.js
```text
Desktop/
│
└── Frontend/
    │
    ├── README.md
    │
    └── Quizz-project/
        │
        ├── src/
        ├── public/
        ├── node_modules/
        ├── package.json
        ├── package-lock.json
        └── vite.config.js
````
