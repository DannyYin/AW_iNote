#GitHub Pages

## What is GitHub Pages

GitHub Pages are public webpages hosted and published through GitHub site.

## User, Organisation, and Project Pages

There are two basic types of GitHub Pages: User/Organization Pages and Project Pages. 
They are nearly identical, but there are a few important differences between them.

### User & Organisation Pages

User & Organization Pages live in a special repository dedicated to GitHub Pages files. 
You will need to name this repository with the account name, e.g. `li-xinyang/li-xinyang.github.io`.

### Project Pages

Project Pages are kept in the same repository as their project. Both personal accounts and organizations can create Project Pages.
The URL for a personal account's Project Page will be `http(s)://<username>.github.io/<projectname>`, while an organization's URL will be `http(s)://<orgname>.github.io/<projectname>`. 
The steps for creating Project Pages are the same for both.

Project Pages are similar to User and Organization Pages, with a few slight differences:

- The `gh-pages` branch is used to build and publish Project Pages sites.
- If no custom domain is used, the Project Pages are served under a subpath of the User Pages Site. e.g. `li-xinyang.github.io/projectname`.
- A custom domain on User and Organisation Pages sites applies the smae domain redirection to all Project PAges sites hosted under the account.
- Custom 404s will only work if a custom domain is used.

### Create Project Pages Manually

1. Make a fresh clone
2. Create a `gh-pages` branch
3. Add content and push
4. Load your new GitHub Pages Site

```
$ git clone github.com/user/repository.git
# Clone our repository

$ cd repository

$ git checkout --orphan gh-pages
# Creates our branch, without any parents (it's an orphan!)
# Switched to a new branch 'gh-pages'

$ git rm -rf .
# Remove all files from the old working tree

$ echo "My Page" > index.html
$ git add index.html
$ git commit -a -m "First pages commit"
$ git push origin gh-pages
```