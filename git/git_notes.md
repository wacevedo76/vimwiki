#Git General Notes

#### Global user settings
```
git config --global user.name "your name"
git config --global user.email your.email@example.com
git config --global --global init.defaultBranch main

git config --global alias.co checkout
git config -- global credential.helper "cache --timeout=86400"
```
#### A template for the first push to Github
```
git remote add origin https://github.com/<name>/<repo_name>.git
git branch -M main
git push -u origin main
```
