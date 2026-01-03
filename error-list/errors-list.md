## Common Git Errors

## 1. error: failed to push some refs to
**Cause**: Local branch is behind remote.  
**Fix**: `git pull --rebase` then `git push`.

## 2. fatal: not a git repository
**Cause**: Not inside a Git repository.  
**Fix**: `git init` or `cd` into correct folder.

## 3. error: Your local changes would be overwritten by merge
**Cause**: Uncommitted changes conflict with incoming merge.  
**Fix**: `git stash` → `git pull` → `git stash pop`.

## 4. fatal: refusing to merge unrelated histories
**definition**:It happens when your local repository and the GitHub repository started independently.
This usually happens when:
- You ran git init locally and committed
- You also created the repo on GitHub with README / LICENSE
- Both histories started separately
- So Git sees two different roots.

**Cause**: Repositories have no common ancestor.  
**Fix**: `git pull origin main --allow-unrelated-histories`.or `git merge --allow-unrelated-histories`.<br>
**Note**: If you have already pushed to the remote repository, you can use `git pull origin main --allow-unrelated-histories` to pull the changes from the remote repository and merge them into your local repository.<br>
**Note**: If you want to keep your local changes, you can use `git merge --no-commit --allow-unrelated-histories` to merge the changes from the remote repository into your local repository without committing them.


## 5. error: pathspec did not match any file(s) known to git
**Cause**: File/path doesn’t exist in index.  
**Fix**: Check spelling or `git add` the file first.

## 6. error: src refspec master does not match any
**Cause**: No commits on local master.  
**Fix**: `git commit -m "initial"` then push.

## 7. warning: LF will be replaced by CRLF
**Cause**: Line-ending conversion on Windows.  
**Fix**: Configure `core.autocrlf` to `true` or `input`.

## 8. fatal: remote origin already exists
**Cause**: Remote named origin is already configured.  
**Fix**: `git remote set-url origin <new-url>` or remove first.

## 9. error: cannot lock ref
**definition**:It happens when you have multiple Git processes running at the same time.
This usually happens when one of these occurred during rebase:
- Another Git command modified main.
- You ran `git rebase` on main.
- The rebase state got partially interrupted.
- Windows file locking / index glitch.
- VS Code or another tool touched Git refs.


**Cause**: Concurrent access or permission issue.  
**Fix**: Remove `.git/refs/.../lock` file manually.or `git rebase --abort` and try again.

## 10. error: object file is empty
**Cause**: Corrupted object database.  
**Fix**: `git fsck` → delete empty objects → `git gc`.

## 11. error: unable to auto-detect email address
**Cause**: Git can’t find your user.email config.  
**Fix**: `git config --global user.email "you@example.com"`.

## 12. fatal: Authentication failed
**Cause**: Wrong credentials or token expired.  
**Fix**: Update password/token or use SSH instead of HTTPS.

## 13. error: RPC failed; curl 56 GnuTLS recv error
**Cause**: Large push over HTTPS times out.  
**Fix**: Increase buffer: `git config http.postBuffer 524288000`.

## 14. error: insufficient permission for adding an object
**Cause**: File system permissions on shared repo.  
**Fix**: `sudo chown -R $USER:$GROUP .git/objects`.

## 15. error: branch 'feature' not found
**Cause**: Local branch doesn’t exist.  
**Fix**: `git checkout -b feature` or `git fetch` first.

## 16. warning: refname 'HEAD' is ambiguous
**Cause**: Tag and branch both named HEAD.  
**Fix**: Rename tag: `git tag -d HEAD && git tag new-name`.

## 17. error: The following untracked working tree files would be overwritten
**Cause**: Checkout clashes with existing files.  
**Fix**: `git clean -fd` or move files out of the way.

## 18. fatal: bad config line 1 in .git/config
**Cause**: Hand-edited config is malformed.  
**Fix**: Open `.git/config` and fix syntax or delete offending lines.

## 19. error: cannot rebase: You have unstaged changes
**Cause**: Uncommitted changes block rebase.  
**Fix**: `git stash` → `git rebase` → `git stash pop`.

## 20. error: remote upstream already exists
**Cause**: Second `git remote add upstream` attempt.  
**Fix**: `git remote remove upstream` then add again.

## 21. fatal: invalid refspec 'HEAD'
**definition**:This usually happens when you are not on a normal branch or when HEAD is detached or in a broken state after rebase/merge attempts.
A refspec must look like one of these:
- local-branch
- local-branch:remote-branch
- HEAD:remote-branch

**Cause**: Invalid refspec passed to `git reset`.
**Fix**: `git reset --hard HEAD@{1}` or `git reset --hard HEAD~1`.or `git checkout <branch>` then `git reset --hard`.

## 22. non-fast-forward
**definition**:This usually happens when you are not on a normal branch or when HEAD is detached or in a broken state after rebase/merge attempts.
A refspec must look like one of these:HEAD -> main (non-fast-forward) → you pushed from HEAD ,main -> main (non-fast-forward) → you pushed from branch 
- local-branch
- local-branch:remote-branch(eg., `git push thisisremotebranch hereisdirectorybranch:main` when we reaname branches. ) 
- HEAD:remote-branch

**Cause**: Local branch is behind remote.
**Fix**: `git pull --rebase` then `git push`(pull first, then push).
