# When there is a folder with the same name as a branch

```
git checkout test --
```

# git clone subdirectory

```cmd
git clone --filter=blob:none --sparse  %your-git-repo-url%
cd %the repository directory%
git sparse-checkout add %subdirectory-to-be-cloned%
cd %your-subdirectory%
```

# Remove file from git repo history 
-  This removes the local file too!!!!. Make sure to backup
git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch <filename>' --prune-empty --tag-name-filter cat -- --all

