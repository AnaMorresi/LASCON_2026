# Basic Git Guide for the LASCON_2026 Project

This guide explains:

1. How to connect a Git repository to a folder on your computer
2. How to create your own branch
3. How to check that everything is set up correctly
4. How to upload files and changes

---

## 1. Connect the repository to a local folder

### Option A: The folder does NOT exist yet

Git will create the folder automatically.

```bash
cd /path/where/you/want/the/folder
git clone https://github.com/USERNAME/LASCON_2026.git
cd LASCON_2026
```

---

### Option B: The folder ALREADY exists (most common case)

Go into the folder:

```bash
cd /path/to/your/folder
```

Initialize Git:

```bash
git init
```

Connect the remote repository:

```bash
git remote add origin https://github.com/USERNAME/LASCON_2026.git
```

Pull the remote content without deleting local files:

```bash
git pull origin main --allow-unrelated-histories
```

---

## 2. Create your own branch (ONLY ONCE)

Each person must work on their own branch.

Example for a person named `ana`:

```bash
git checkout main
git pull origin main
git checkout -b ana
git push -u origin ana
```

This:

* creates the branch `ana` locally
* uploads it to the remote repository
* sets it as your working branch

---

## 3. Check that everything is correct

### Check which branch you are on

```bash
git branch
```

The active branch is marked with `*`.

Correct example:

```text
* ana
  main
```

---

### See local and remote branches

```bash
git branch -a
```

Example:

```text
* ana
  main
  remotes/origin/ana
  remotes/origin/main
```

---

### Check repository status

```bash
git status
```

If it says:

```text
working tree clean
```

→ there are no uncommitted changes.

---

## 4. Daily workflow (normal work)

### 1) Make sure you are on your branch

```bash
git checkout ana
```

---

### 2) Edit files

Work normally using your editor (VSCode, etc.).

---

### 3) Save changes (commit)

```bash
git add .
git commit -m "Clear description of the change"
```

Examples of good commit messages:

* `"Add Hopfield simulation"`
* `"Fix bug in data loading"`

---

### 4) Upload changes to the repository

```bash
git push
```

---

## 5. Keep your branch up to date with `main` (recommended)

Before continuing work or before merging:

```bash
git checkout main
git pull origin main
git checkout ana
git merge main
```

If conflicts appear:

* resolve them in your branch
* never directly in `main`

---

## 6. Merge your work into `main`

### Recommended way: Pull Request (on GitHub)

1. Go to GitHub
2. Click **New Pull Request**
3. base: `main`
4. compare: your branch (`ana`)
5. Another team member reviews
6. Merge

---

## 7. Important team rules

* Do not work directly on `main`
* Do not use `git push --force`
* Make small, clear commits
* Each person works only on their own branch
* `main` should always be stable

---

## 8. Quick safety check

Before writing any code, always run:

```bash
git branch
```

If you are not on your branch, switch before working.
