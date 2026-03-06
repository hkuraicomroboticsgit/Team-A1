# Git & Unity Daily Workflow Practices

Follow this routine **every single time** you work on the project to keep everything stable.

## Core Rule #1: Develop on PC, Test on Robot
- Always develop and edit code on your PC. The robot cannot access the internet, so transfer files to the robot only for testing.
- If you make changes directly on the robot, transfer them back to your PC, then commit and push from there.
- Why? This ensures all changes are tracked in Git on the PC, prevents desyncs, and maintains a clean history on GitHub.

# Step-by-Step Routine

## Part A. Pure Programming

1. **Open Visual Studio Code**
   - Open VS Code -> choose "open folder" -> choose the folder containing the repository
   
2. **Git pull (always do so before working)**
   - Open your terminal in the project folder (eg. `Team-A1`).
   - Pull the latest changes from the remote:
     ```bash
     git pull origin your-branch
     ```
   - If conflicts appear → resolve them carefully (see Troubleshooting below).
   - (Optional: Run git status to confirm clean working tree.)

3. **Go on to develop**
   - Save frequently or enable auto-save in VS Code

4. **Stage, commit & push**
   - Stage all changes:
     ```bash
     git add .
     ```
   - Commit with a clear message:
     ```bash
     git commit -m "your commit message"
     ```
      - Good commit messages: what + why (short & descriptive)
   - Push to remote:
     ```bash
     git push origin your-branch
     ```
      - If push rejected (non-fast-forward), it means someone else pushed meanwhile. Git pull again, resolve, then push.
    
## Part B. Testing on Robot

1. **Start session – on PC**
   - Pull from github (follow the steps in A1)
     
2. **Transfer to robot**
   - Copy needed folders/files to robot using a USB

3. **Work on robot**
   - Run experiments / training / testing

4. **Transfer back to PC**
   If you have editted the code on the robot, copy back to your PC into correct places.

5. **Back on PC – commit changes**
   - Push to github (follow the steps in A4).
   
## When Things Go Wrong

- Push rejected? git pull origin main first.
- Merge conflicts? Edit files (choose which version to keep, or edit manually), commit & push again.
- .meta conflicts common? Usually safe to keep "theirs" or "ours" based on who changed the asset last.
- Still stuck? Run git status, screenshot errors, and open an Issue.
