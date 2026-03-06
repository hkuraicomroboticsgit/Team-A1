# Git & Unity Daily Workflow Practices

Follow this routine **every single time** you work on the project to keep everything stable.

## Core Rule #1: Close Unity Before Any Git Commands
- **Always close Unity completely** before running `git pull`, `git add`, `git commit`, `git push`, or any other git operation.
- Why? Unity locks files (especially in `Library/`, scenes, prefabs) and can cause .meta file desyncs or corruption if you git while the editor is open.

## Every Work Session: Step-by-Step Routine

1. **Start / Before touching anything**
   - Open your terminal in the project folder (`PlayVision-Phrase1`).
   - Make sure Unity is **closed**.
   - Pull the latest changes from the remote:
     ```bash
     git pull origin your-branch
     ```
   - If conflicts appear → resolve them carefully (see Troubleshooting below).
   - (Optional: Run git status to confirm clean working tree.)

2. **Open Unity and work**
   - Launch Unity Hub → open the project.
   - Do your work: edit scripts, scenes, prefabs, assets, etc.
   - Save frequently inside Unity (File → Save Project, or Ctrl+S on scenes/prefabs).

3. **Finish working / Before leaving**
   - In Unity: Save everything (scenes, project).
   - Close Unity completely (important!).
   - Back in terminal:
     ```bash
     git status
     ```
   - You should see modified/added files (scripts, .meta, prefabs, etc.).
   - You should never see huge unexpected changes (if you do, something's wrong with .gitignore or LFS).

4. **Stage, commit & push**
   - Stage all changes:
     ```bash
     git add .
     ```
     or selectively: 
     ```bash
     git add Assets/Scripts/*.cs Assets/Scripts/*.cs.meta
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

## When Things Go Wrong

- Push rejected? git pull origin main first.
- Merge conflicts? Edit files (choose which version to keep, or edit manually), commit & push again.
- .meta conflicts common? Usually safe to keep "theirs" or "ours" based on who changed the asset last.
- Still stuck? Run git status, screenshot errors, and open an Issue.
