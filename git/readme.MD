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
