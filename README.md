# workflowCheck
Copilot is all over the place. I need a clean check to make sure workflows behave as intended.

## GitHub Actions Pass/Fail Control

This repository contains a simple GitHub Actions workflow that can be controlled to pass or fail by adding or removing specific files.

### How it works

The workflow checks for the presence of control files in the repository root:

- **PASS**: If this file exists, the workflow will pass
- **FAIL**: If this file exists, the workflow will fail  
- **Default**: If neither file exists, the workflow will pass by default

### Usage

To make the workflow **pass**:
```bash
touch PASS
git add PASS
git commit -m "Set workflow to pass"
git push
```

To make the workflow **fail**:
```bash
rm -f PASS  # Remove PASS file if it exists
touch FAIL
git add FAIL
git commit -m "Set workflow to fail"
git push
```

To reset to **default behavior** (pass):
```bash
rm -f PASS FAIL  # Remove both control files
git add -A
git commit -m "Reset to default behavior (pass)"
git push
```

The workflow runs on:
- Pushes to main/master branches
- Pull requests to main/master branches
- Manual workflow dispatch
