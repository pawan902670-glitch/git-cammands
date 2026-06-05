
# ✅ YOUR GIT ROADMAP (Correct Version)

## 🔰 1. Project Setup

```bash id="kq3x1a"
mkdir my-project
cd my-project
git init
```

✔ Repo start

---

## 📁 2. File Creation

```bash id="m8q7dp"
echo "Hello" > file.txt
```

OR

```bash id="v2l9kc"
touch css.txt html.txt
```

✔ Files create

---

## ⚙️ 3. Git Config (One time)

```bash id="a7p0wd"
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

git config --global core.autocrlf true
```

✔ Setup complete

---

## 📊 4. Check Status

```bash id="x9m1ef"
git status
```

---

## ➕ 5. Add Files

```bash id="p3t8uv"
git add .
```

---

## 💾 6. Commit

```bash id="c6r4ja"
git commit -m "initial commit"
```

---

## 🌐 7. Connect GitHub Repo

```bash id="q1z7hb"
git remote add origin YOUR_URL
```

Check:

```bash id="l2w9mk"
git remote -v
```

---

## 🚀 8. Push Code

First time:

```bash id="t8n3sd"
git push -u origin main
```

Normal push:

```bash id="f5x0cv"
git push
```

If error (history mismatch):

```bash id="r4k6lp"
git pull origin main --allow-unrelated-histories
```

---

## 🔄 9. Branching

Create branch:

```bash id="z7c2qa"
git checkout -b feature-login
```

Switch branch:

```bash id="n4d9vh"
git checkout main
```

---

## ✏️ 10. Modify Files

```bash id="s1j8xr"
echo "new content" >> demo.txt
```

---

## 🔍 11. Check Differences

```bash id="u3p7yn"
git diff
```

---

## 🔁 12. Merge Workflow

```bash id="e6q5bt"
git add .
git commit -m "update"
git push origin feature-login
```

Then PR or merge:

```bash id="k9w2lm"
git checkout main
git merge feature-login
```

---

## 🌐 13. Remote Info

```bash id="b8n4xz"
git remote -v
```

---

## 🔧 14. Change Remote URL

```bash id="d5v0qp"
git remote set-url origin NEW_URL
```

---

## 📥 15. Fetch

```bash id="h2c7zn"
git fetch origin
```

---

## 📥 16. Pull

```bash id="j6m1sa"
git pull origin main
```

---

# 📊 FINAL STATUS OF YOUR LEARNING

## ✔ You are already here:

| Topic              | Level |
| ------------------ | ----- |
| Basic Git commands | ⭐⭐⭐⭐⭐ |
| Branching          | ⭐⭐⭐⭐  |
| Push/Pull          | ⭐⭐⭐⭐  |
| Remote GitHub      | ⭐⭐⭐⭐  |
| File operations    | ⭐⭐⭐⭐⭐ |

---

## ⚠️ You still need next level:

These are IMPORTANT for exams + interviews:

### ❗ Advanced Git (Next Step)

1. Merge Conflict ⭐⭐⭐⭐
2. Revert ⭐⭐⭐
3. Reset ⭐⭐⭐⭐
4. Rebase ⭐⭐⭐⭐⭐ (very important)
5. Cherry-pick ⭐⭐⭐
6. Stash ⭐⭐⭐
7. Fork + Pull Request (real collaboration)