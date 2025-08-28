#### Basics
1. git init

> You have:
local branch → `main` on your computer
remote branch → `origin/main` on GitHub

> origin = your gitHub repository

2. git remote add origin https://github.com/USERNAME/REPO_NAME.git    
> After this 👆🏻, your local git repository knows: `“I have a remote called origin, and its URL is https://github.com/USERNAME/REPO_NAME.git.”`


> **Tracking branch** = local branch + its linked remote branch.
> Tracking branch means **git push and git pull know automatically where to sync**.
✅ Command to link: `git push -u origin main`


3. git add .

4. git add filename.txt

5. git status

6. git commit -m "Your commit message"

7. git push -u origin main    

> For subsequent pushes: `git push`
-------------------------------------------------------------------------------
#### Pull
8. git pull origin main --rebase 
then use:  git push origin main

9. git pull origin main
-------------------------------------------------------------------------------
#### Branch
10. **Create a new branch**: git branch feature-login

11. **Switch to that branch**: 
    git switch feature-login 
    or, git checkout feature-login

12. **Create & switch in one step**: git switch -c feature-login

13. **List branches**: 
    git branch        `# local branches`
    git branch -a     `# local + remote branches`

> Local branch = your copy.
> Remote branch = GitHub’s copy.

14. **Push a branch to GitHub**: git push -u origin feature-login

15. **Delete a branch**:
    git branch -d feature-login   `# delete after merging`
    git branch -D feature-login   `# force` 
-------------------------------------------------------------------------------
#### Merge
 - Preserves full history (good for audit trails).
 - Creates a new merge commit that combines histories.
 - The Git history looks like a tree with branches and a merge commit tying them together.

 16. **When your feature is ready, you merge it into main**:
    git checkout main

17. **Merge the branch**:
    git merge feature-login



 #### Rebase
 - Creates a linear history (cleaner).
 - Moves your branch to start from the tip of another branch.
 - Re-applies your commits one by one. 
 - Doesn’t care about when commits were made.
 - It rewrites your commits so they look like they were created after the latest commit in the other branch.
 
18. git checkout feature-login

19. git rebase main

> 👉 Think of it this way:
  Merge = “Show how the work really happened.”
  Rebase = “Make it look like I started later, so history is tidy.”
-------------------------------------------------------------------------------
#### RollBack

20. git log --oneline

21. **For recent HEAD moves**: git reflog

22. git log

23. **Soft rollback (keep changes staged)**: git reset --soft <commit_hash>
- Moves HEAD to the chosen commit.
- Your changes after that commit remain staged, so you can recommit them.

24. **Mixed rollback (keep changes unstaged)**: git reset --mixed <commit_hash>
- Moves HEAD to the chosen commit.
- Your changes after that commit remain in your working directory but unstaged.

25. **Hard rollback (discard changes)**: git reset --hard <commit_hash>
- Moves HEAD to the chosen commit.
- All changes after that commit are lost permanently (unstaged & staged).

26. **Undo a commit that’s already pushed**:  git revert <commit_hash>
