# Git Branch and PR Practice

# Git Branching, Pull Requests & Merge Conflict Practice

## Overview

This repository was created to practice the basic Git and GitHub workflow, including creating commits, working with branches, opening Pull Requests (PRs), merging changes, and resolving merge conflicts.

The exercise demonstrates how changes can be developed independently on different branches and then integrated into the `main` branch using Pull Requests.

---

## Repository Structure

```text
git-branch-practice/
├── README.md
├── index.html
└── style.css
```

---

## 1. Repository Creation

A new GitHub repository was created to practice Git branching and Pull Request workflows.

The repository was cloned locally using SSH:

```bash
git clone git@github.com:USERNAME/git-branch-practice.git
```

The repository was then opened locally:

```bash
cd git-branch-practice
```

---

## 2. Adding the README

The first change was adding this `README.md` file to document the work performed in the repository.

The changes were staged and committed separately:

```bash
git add README.md
git commit -m "Add README"
```

The commit was then pushed to the `main` branch.

---

## 3. Adding the Hello World Page

An `index.html` file was created containing a simple Hello World page.

The file contains:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Hello World</title>
</head>
<body>
    <h1>Hello World</h1>
</body>
</html>
```

The change was committed separately:

```bash
git add index.html
git commit -m "Add Hello World index page"
```

The commit was then pushed to `main`.

---

## 4. Creating a Feature Branch

A separate feature branch was created to add styling without directly modifying `main`.

```bash
git switch -c feature/add-styles
```

This created the following branch:

```text
feature/add-styles
```

---

## 5. Adding CSS

A `style.css` file was created on the feature branch.

Example:

```css
body {
    font-family: Arial, sans-serif;
    text-align: center;
}

h1 {
    font-size: 40px;
}
```

The CSS file was committed separately:

```bash
git add style.css
git commit -m "Add basic styling"
```

The feature branch was then pushed to GitHub:

```bash
git push -u origin feature/add-styles
```

---

## 6. Creating and Merging a Pull Request

A Pull Request was created from:

```text
feature/add-styles → main
```

The Pull Request was reviewed and then merged into `main`.

This demonstrated how a feature can be developed independently and integrated into the main codebase through a Pull Request.

After merging, the local `main` branch was updated:

```bash
git switch main
git pull origin main
```

---

## 7. Simulating a Merge Conflict

To understand how Git handles conflicting changes, a merge conflict was deliberately created.

First, a new branch was created:

```bash
git switch -c feature/change-heading
```

The heading in `index.html` was changed on this branch:

```html
<h1>Hello from Feature Branch</h1>
```

The change was committed:

```bash
git add index.html
git commit -m "Update heading from feature branch"
```

At the same time, the same line was changed differently on the `main` branch:

```html
<h1>Hello from Main Branch</h1>
```

This change was also committed.

Because both branches modified the same line differently, Git could not automatically determine which version should be kept.

---

## 8. Resolving the Merge Conflict

The latest version of `main` was fetched:

```bash
git fetch origin
```

Then `main` was merged into the feature branch:

```bash
git merge origin/main
```

Git reported a conflict in `index.html`.

The file contained conflict markers similar to:

```text
<<<<<<< HEAD
<h1>Hello from Feature Branch</h1>
=======
<h1>Hello from Main Branch</h1>
>>>>>>> origin/main
```

The conflict was manually resolved by selecting the desired final content and removing the conflict markers.

The resolved version was:

```html
<h1>Hello from Feature and Main Branches</h1>
```

The resolved file was staged:

```bash
git add index.html
```

A merge-resolution commit was then created:

```bash
git commit -m "Resolve merge conflict in index"
```

The feature branch was pushed again:

```bash
git push origin feature/change-heading
```

The Pull Request was then updated and merged into `main`.

---

## 9. Git Workflow Demonstrated

The complete workflow practiced in this repository was:

```text
Create Repository
       ↓
Clone Repository
       ↓
Create Commit
       ↓
Create Feature Branch
       ↓
Make Changes
       ↓
Commit Changes
       ↓
Push Branch
       ↓
Open Pull Request
       ↓
Review & Merge
       ↓
Create Merge Conflict
       ↓
Resolve Conflict
       ↓
Commit Resolution
       ↓
Push Changes
       ↓
Merge Pull Request
```

---

## 10. Key Git Commands Used

### Check repository status

```bash
git status
```

### Create a branch

```bash
git switch -c branch-name
```

### Switch branches

```bash
git switch main
```

### Stage changes

```bash
git add .
```

### Create a commit

```bash
git commit -m "Commit message"
```

### Push a branch

```bash
git push -u origin branch-name
```

### Fetch remote changes

```bash
git fetch origin
```

### Merge a branch

```bash
git merge branch-name
```

### View commit history

```bash
git log --oneline
```

---

## Conclusion

This exercise provided hands-on practice with Git and GitHub collaboration workflows. I created separate commits for different changes, worked with feature branches, created and merged Pull Requests, and deliberately created and resolved a merge conflict.

The exercise helped demonstrate how Git allows multiple developers to work independently while providing mechanisms such as branches, commits, Pull Requests, and conflict resolution to safely integrate changes into the main codebase.

