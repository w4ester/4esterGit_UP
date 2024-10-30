# 4esterGit_UP
Complete Git Workflow Guides
# Git Workflow Guides

## 1. Solo Local Development (VSCode + Git)

### Initial Setup
```bash
# Create new repository
git init
git add .
git commit -m "Initial commit"

# Or clone existing
git clone https://github.com/yourusername/project.git
```

### Daily Workflow
```bash
# Start new feature
git checkout -b feature/new-signature

# Work in VSCode
# VSCode Git shortcuts:
# - Source Control panel (Ctrl+Shift+G)
# - Stage changes with + button
# - Commit with ✓ button
# - Push with ↑ button

# Command line equivalent
git add index.html
git commit -m "Add new signature format"
git push origin feature/new-signature

# View versions
git log --oneline  # Brief history
git log -p index.html  # File history
git checkout <commit-hash> # View old version
```

### Version Management
```bash
# Compare versions in VSCode
# Right-click file > Select for Compare
# Right-click another version > Compare with Selected

# Command line comparison
git diff main feature/new-signature index.html

# Restore previous version
git checkout <commit-hash> index.html
git commit -m "Restore previous version"
```

## 2. Team Local Development

### Initial Setup
```bash
# Clone team repository
git clone https://github.com/teamname/project.git

# Set up branch protection (through GitHub)
# - Require pull request reviews
# - Require status checks
```

### Daily Workflow
```bash
# Get latest changes
git checkout main
git pull origin main

# Create feature branch
git checkout -b feature/user-signature

# Work and commit regularly
git add .
git commit -m "Add user signature component"

# Stay updated with main
git checkout main
git pull origin main
git checkout feature/user-signature
git merge main

# Push changes
git push origin feature/user-signature

# Create PR through GitHub
gh pr create
```

## 3. CLI (Git) Local

### Version Management
```bash
# View all versions
git log --pretty=format:"%h %ad | %s" --date=short

# Create version tags
git tag v1.0.0
git push origin v1.0.0

# Branch management
git branch -a  # List all branches
git branch -d old-feature  # Delete branch

# Compare versions
git diff HEAD~1 HEAD  # Compare with previous
git diff main...feature  # Compare branches
```

## 4. CLI (GitHub) Local

### GitHub CLI Workflows
```bash
# Authentication
gh auth login

# PR management
gh pr create
gh pr checkout 123
gh pr review 123 --approve

# Release management
gh release create v1.0.0

# Issue management
gh issue create
gh issue list --assignee @me
```

## 5. GitHub Codespaces Solo

### Setup and Workflow
```bash
# Start new codespace
gh codespace create

# Version control in codespace
git checkout -b feature/new-design
git add .
git commit -m "Update design"
git push origin feature/new-design

# Manage versions
git log --graph --oneline
```

## 6. GitHub Codespaces Team

### Collaboration Workflow
```bash
# Create codespace from PR
gh codespace create -r teamname/project -b feature/team-design

# Review others' work
gh pr checkout 123
gh pr review 123 --comment "Looks good!"

# Sync work
git pull origin main
git merge main
```

## 7. Fork & PR (Open Source) Workflow

### Initial Setup
```bash
# Fork via GitHub UI
# Clone your fork
git clone https://github.com/yourusername/project.git

# Add upstream
git remote add upstream https://github.com/original/project.git
```

### Contributing
```bash
# Sync fork
git fetch upstream
git merge upstream/main

# Make changes
git checkout -b feature/improvement
git commit -am "Add improvement"
git push origin feature/improvement

# Create PR to upstream
gh pr create -R original/project
```

## Version Control Best Practices

### Commit Messages
```bash
# Good commit messages
git commit -m "feat: Add email signature generator"
git commit -m "fix: Correct signature formatting"
git commit -m "docs: Update installation instructions"
```

### Branching Strategy
```bash
# Feature branches
git checkout -b feature/new-feature

# Bugfix branches
git checkout -b fix/bug-description

# Release branches
git checkout -b release/v1.0.0
```

### Version Tagging
```bash
# Create semantic version tags
git tag -a v1.0.0 -m "Initial release"
git tag -a v1.0.1 -m "Bug fixes"
git push origin --tags
```

### Recovery and Backup
```bash
# Stash changes
git stash save "Work in progress"
git stash list
git stash pop

# Reset to previous version
git reset --hard HEAD~1
git reset --soft HEAD~1

# Create backup branch
git checkout -b backup/feature-jan24
```
