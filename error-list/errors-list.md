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
**Cause**: Repositories have no common ancestor.  
**Fix**: `git pull origin main --allow-unrelated-histories`.

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
**Cause**: Concurrent access or permission issue.  
**Fix**: Remove `.git/refs/.../lock` file manually.

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
