# Git Bash Workflow — Linux Task 03

Follow these steps from Git Bash on Windows. Replace `YOUR-GITHUB-USERNAME` with your GitHub username and create an **empty** GitHub repository named `Linux-Task-03` first. Do not initialize the GitHub repository with a README if you use the commands below.

## 1. Extract and locate the project

Extract the downloaded ZIP. In File Explorer, open the extracted folder, right-click inside it, and choose **Open Git Bash here** (wording may vary).

Check the folder contents:

```bash
pwd
ls -la
```

You should see `README.md`, `.gitignore`, `docs/`, `screenshots/`, `commands/`, `evidence/`, `output/`, and `references/`.

## 2. Initialize Git

Run these commands from the project root:

```bash
git init
git branch -M main
git status
```

If Git asks you to configure your identity, use the name and email you want associated with your commits:

```bash
git config --global user.name "Your Name"
git config --global user.email "YOUR-GITHUB-EMAIL"
```

## 3. Add your lab evidence

1. Read the assignment carefully and enter its exact objectives in `README.md`.
2. Record commands you actually execute in `commands/commands-log.md`.
3. Write your step-by-step procedure and results in `docs/LAB_REPORT.md`.
4. Save screenshots in `screenshots/` with descriptive names, for example `01-task-setup.png`, `02-command-result.png`. Use names that match the actual activity.
5. Add only relevant, permitted output files to `output/`.
6. Review images and text for passwords, access tokens, private keys, personal data, and unrelated information before committing.

Then review the files:

```bash
git status
git diff --check
```

## 4. Stage and commit

```bash
git add README.md .gitignore docs screenshots commands evidence output references
git status
git diff --cached
git commit -m "Document Linux Task 03 lab"
```

If `git diff --cached` opens a pager, press `q` to exit. Check the staged file list carefully before committing.

## 5. Connect to GitHub and push

Create an empty repository on GitHub named `Linux-Task-03`. Copy its HTTPS repository URL, then run:

```bash
git remote add origin https://github.com/YOUR-GITHUB-USERNAME/Linux-Task-03.git
git remote -v
git push -u origin main
```

Replace the sample URL with the real URL of your repository. GitHub may ask you to authenticate using its supported sign-in flow or credential manager; your GitHub account password is not accepted for Git HTTPS authentication.

## 6. Confirm the upload

```bash
git status
git log -1 --oneline
git remote -v
```

Open the repository page in your browser and confirm that the README, report, command log, and screenshot folder are visible. Git does not track empty folders, so add at least one screenshot or keep the supplied `screenshots/README.md` in that folder.

## 7. Updating the repository later

After adding more screenshots or editing your report:

```bash
git status
git add .
git diff --cached
git commit -m "Add Linux Task 03 evidence"
git push
```

## Common problems

### `fatal: not a git repository`
You are not inside the project root. Use `cd` to enter the extracted `Linux-Task-03-GitHub-Workflow` folder, then run `ls -la` and `git status`.

### `remote origin already exists`
Inspect the remote before changing it:

```bash
git remote -v
```

If this project should point to a different repository, update it deliberately:

```bash
git remote set-url origin https://github.com/YOUR-GITHUB-USERNAME/Linux-Task-03.git
git remote -v
```

Do not point this project at another lab's repository by mistake.

### `src refspec main does not match any`
You may not have created a commit yet. Check `git status`, stage the project files, and create the initial commit before pushing.

### Push rejected because the GitHub repository already has files
The remote may have been initialized with a README or other commit. Do not force-push blindly. Review the GitHub repository and reconcile the histories safely first.
