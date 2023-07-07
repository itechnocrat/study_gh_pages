# Study GitHub Pages

## Prepare

```sh
NAME_REPO='study_gh_pages'
GITHUB_USERNAME='itechnocrat'
```

## Step I

### Task list

- Creating a personal public repository `$NAME_REPO`
- Add `about.md` to repository
- Deploy it on GitHub Pages

### Action

#### Create a new local repository

Just a note: [master or main](https://github.com/settings/repositories)

```sh
mkdir $NAME_REPO
cd $NAME_REPO
#echo "# ${NAME_REPO}" >> README.md
#
git init
#
touch README.md
git status
git add README.md
git commit -m "init: create README.md"
```

First commit done.

```sh
git status
git log --decorate --graph --all --oneline
```

Next, the local repository is connected to the remote one using the GitHub web-interface or using the [GitHub CLI](https://cli.github.com/).

##### Use GitHub CLI

Authentication:

```sh
gh auth setup-git
gh auth login
gh auth status
```

```sh
gh repo create
#
# gh repo delete # To remove an external repository, the command must be given in the project directory
```

The external repository is created and linked to the local one!

### Continuation of work

Create a `gh-pages` branch from `main` and switch to `gh-pages`:

```sh
git checkout -b gh-pages
```

In the `gh-pages` branch, create a file `about.md`.

```sh
git status
git branch
touch about.md
git add about.md
git commit -m "init: create about.md"
```

Second commit done.

```sh
git status
git log --decorate --graph --all --oneline
```

Create content of `about.md`.

```sh
git status
git add about.md
git commit -m "feat: add content to about.md"
git status
git log --decorate --graph --all --oneline
```

Third commit done.

In the `README.md` file (`gh-pages` branch), add a link like <https://$GITHUB_USERNAME.github.io/$NAME_REPO/about>

```sh
echo "https://$GITHUB_USERNAME.github.io/$NAME_REPO/about" > README.md
git add README.md
git commit -m "feat: add link to README.md"
git status
git log --decorate --graph --all --oneline
git push --set-upstream origin gh-pages
```

Pull Request from `gh-pages` in `main`/`master`

PR name: Step 1  
Pull Request description: The Step 1 of researching GitHub Pages

__Do not Megre Pull Request__

## Step 2

### Task list Step 2

- In an existing repository, create a branch named `html` from `gh-pages`
- Add a `index.html` and `style.css` file to the repository
- Deploy it on GitHub Pages

### Action Step 2

```sh
git status
git branch
git log --decorate --graph --all --oneline
git checkout gh-pages
git checkout -b html
touch index.html style.css
#
git add index.html && \
git commit -m "init: create index.html"
#
git add style.css && \
git commit -m "init: create style.css"
#
# edit index.html normalize.css
#
git add index.html && \
git commit -m "edit: add layout in index.html"
#
git add style.css && \
git commit -m "edit: add styles in style.css"

echo "<https://$GITHUB_USERNAME.github.io/$NAME_REPO/>" >> README.md
git add README.md
git commit -m "edit: add link to README.md"

git push --set-upstream origin html
```

### Pull Request Step 2

Pull Request from `html` in `gh-pages`

PR name: Step 2  
Pull Request description: The Step 2 of researching GitHub Pages

**Make a Merge Pull Request**

```sh
# git push --force origin html
git push origin html
```

## Step 3

Layout and styling of your `about`

```sh
git status
git branch
git log --decorate --graph --all --oneline
git checkout -b html
```

### Task list Step 3

Markup and styling work ...  

### Action Step 3

indexing, commits, pushing ...

### Pull Request Step 3

#### 1

Pull Request from `html` in `main`/`master`

PR name: Step 3 Phase 1  
Pull Request description: The Step 3 of researching GitHub Pages

**Do not Megre Pull Request**

#### 2

Pull Request from `html` in `gh-pages`

PR name: Step 3 Phase 2  
Pull Request description: *not required*

**Make a Merge Pull Request**

```sh
# git push --force origin html
git push origin html
```

## Resources

[Edit commit messages](https://docs.github.com/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/changing-a-commit-message#amending-older-or-multiple-commit-messages)

Delete branch

```sh
git branch -d html
```

Clone branch

```sh
git clone --branch gh-pages https://github.com/$GITHUB_USERNAME/$NAME_REPO
```

```sh
mkdir -p assets/{img,svg,fonts,video}
```
