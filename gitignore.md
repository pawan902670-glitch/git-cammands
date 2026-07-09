# Git Notes - `.gitignore` (Complete Guide)

## Topic: `.gitignore`

---

# What is `.gitignore`?

`.gitignore` is **not a Git command**.

It is a **special file** that tells Git:

> **"Do not track these files or folders."**

Git reads this file every time you run commands like:

```bash
git status
git add .
git commit
```

---

# Why do we use `.gitignore`?

When we execute

```bash
git add .
```

Git tries to add **every file and folder** inside the project.

Sometimes we don't want everything to be uploaded to GitHub.

Examples:

* `node_modules/`
* `.env`
* `dist/`
* `build/`
* Temporary files
* Log files

Instead of adding everything, we tell Git:

> Ignore these files.

That instruction is written inside `.gitignore`.

---

# Real Life Example

Suppose your project contains

```text
Project/
│
├── index.html
├── style.css
├── app.js
├── node_modules/
├── .env
└── .gitignore
```

Without `.gitignore`

```bash
git add .
```

Git will try to add

```
index.html
style.css
app.js
node_modules
.env
```

This is bad because

* node_modules contains thousands of generated files.
* .env contains passwords and API keys.

---

# After using `.gitignore`

Contents of `.gitignore`

```text
node_modules/
.env
```

Now when we run

```bash
git add .
```

Git adds

```
index.html
style.css
app.js
.gitignore
```

Git ignores

```
node_modules
.env
```

---

# Important Rule

`.gitignore` itself is uploaded to GitHub.

The files written inside `.gitignore` are NOT uploaded.

Many beginners think

".gitignore should also be ignored."

❌ Wrong

Correct:

`.gitignore` should always be committed so every developer gets the same ignore rules.

---

# How to create `.gitignore`

Create file

```bash
touch .gitignore
```

Check

```bash
ls -la
```

Output

```
.git
.gitignore
index.html
```

---

# Write inside `.gitignore`

```bash
echo node_modules/ > .gitignore
```

Check

```bash
cat .gitignore
```

Output

```
node_modules/
```

---

# Add more rules

```bash
echo .env >> .gitignore
```

```bash
echo dist/ >> .gitignore
```

Now

```bash
cat .gitignore
```

Output

```
node_modules/
.env
dist/
```

---

# Difference between > and >>

Overwrite file

```bash
echo node_modules/ > .gitignore
```

Meaning

Erase old content.

Write new content.

Append

```bash
echo .env >> .gitignore
```

Meaning

Keep old content.

Add a new line at the bottom.

---

# Internal Working

Suppose project contains

```
index.html
node_modules
.gitignore
```

Inside `.gitignore`

```
node_modules/
```

When we run

```bash
git add .
```

Git internally works like this

Step 1

Scan the project

```
✔ index.html

✔ node_modules

✔ .gitignore
```

Step 2

Read `.gitignore`

```
node_modules/
```

Step 3

Git says

```
Ignore node_modules
```

Step 4

Final result

```
✔ index.html

✔ .gitignore

✖ node_modules
```

---

# Mistake I Made

I typed

```bash
.gitignore
```

Error

```
bash: .gitignore: command not found
```

Reason

`.gitignore` is NOT a command.

It is a file.

Correct

```bash
touch .gitignore
```

---

# Mistake I Made

I thought

`.gitignore` itself should not be uploaded.

Wrong.

Correct

`.gitignore` is uploaded.

Its purpose is to tell everyone which files should be ignored.

---

# Mistake I Made

I created

```bash
mkdir node_modules
```

Then

```bash
git status
```

I expected

```
node_modules/
```

But nothing appeared.

Reason

Git does not track **empty folders**.

The folder was empty.

Correct

Create a file inside

```bash
touch node_modules/test.txt
```

Now

```bash
git status
```

Git shows

```
node_modules/
```

unless it is ignored by `.gitignore`.

---

# Mistake I Made

I created a new Git repository inside another Git repository.

Commands

```bash
mkdir ignore-demo

cd ignore-demo

git init
```

Then Git displayed

```
You've added another git repository inside your current repository.
```

Reason

A Git repository already existed.

I created another `.git` folder inside it.

Structure

```
Main Project
│
├── .git
└── ignore-demo
    └── .git
```

Correct way

Every project should have only one `.git` folder.

If the second repository was created by mistake

Go inside

```bash
cd ignore-demo
```

Remove Git history

```bash
rm -rf .git
```

Go back

```bash
cd ..
```

---

# Best Practices

✔ Always commit `.gitignore`.

✔ Ignore `node_modules`.

✔ Ignore `.env`.

✔ Ignore build folders.

✔ Do not create Git repositories inside other Git repositories unless using Git submodules intentionally.

✔ Create one `.gitignore` file in the root of the project.

---

# Most Common Interview Questions

### Is `.gitignore` a command?

No.

It is a file.

---

### Does `.gitignore` get uploaded to GitHub?

Yes.

---

### Does `.gitignore` delete files?

No.

It only tells Git to ignore them.

---

### Does `.gitignore` remove files from my computer?

No.

The files remain on the computer.

Git simply does not track them.

---

### Can Git track an empty folder?

No.

Git tracks files, not empty directories.

---

### One-Line Definition

> **`.gitignore` is a special file that tells Git which files and folders should not be tracked or uploaded to the repository.**
