## Git & GitHub Beginner Notes

``` bash
cd "/c/Users/jainn/Desktop/SB Practice/My Prod"
ls
git init
git status
git add .
```

Configure once:

``` bash
git config --global user.name "Nikunj Jain"
git config --global user.email "jainnikunj100@gmail.com"
```

Commit:

``` bash
git commit -m "Initial Commit"
```

Connect remote:

``` bash
git remote add origin https://github.com/Nj-18/Prod-Ready-Features.git
git remote -v
git branch -M main
git push -u origin main
```

Create develop:

``` bash
git checkout -b develop
git push -u origin develop
```

Daily:

``` bash
git status
git add .
git commit -m "message"
git push
```

Common mistakes: - `git add.` ❌ -\> `git add .` ✅ -
`git push -u develop` ❌ -\> `git push -u origin develop` ✅ - LF/CRLF
warnings are normal on Windows.
