### common commands

`setup`
- setups up a new directory with git init, adds all files, makes initial commit

`undo`
- remove the latest commit, or last x: `g undo 3`

`reset FILE`
- reset one file to `HEAD` or a certain commit
- `g reset-file .htaccess`

`ignore`
- adds to .gitignore: `g ignore build "*.log"`
- without arguments, lists currently ignored patterns: `g ignore`

`obliterate`
- totally remove a file from the repo, including past commits
- `g obliterate secrets.json`

`local-commits`
- lists all un-pushed commits

`delta`
- list files that differ from another branch

`missing`
- list the commits that are on one branch or the other but not both
- `g missing master`

`feature NAME`
- create the given feature, refactor, bug or chore branch: `g feature login-screen`
- once the branch exists, the same command will check it out
- when finished, merge it into another branch with `g feature finish login-screen`

`create-branch NAME`
- creates local and remote

`fresh-branch`
- creates empty local branch

`delete-branch NAME`
- deletes local and remote

`delete-tag NAME`
- deletes local and remote

`delete-submodule NAME`
- deletes submodule: `g delete-submodule lib/foo`

`merge-into`
- merge `src` into `dest`
- `src` defaults to current, but can be other branch
- does not switch current branch

`delete-merged-branches`
- deletes branches that have been merged into the one you're on

`info`
- shows repo info

`release TAG`
- release commit with given tag: `g release 0.1.0`
- runs pre/post release hooks
- pushes branch/tags

`gh-pages`
- sets up a gh-pages branch

`fork`
- forks (on github) and clones repo locally
- adds original repo as remote to track upstream changes

### misc. commands

`squash` 
- merge commits from `src` into the current branch as a single commit
- takes optional message: `g squash fixed-login "fixes login problems"`

`alias`
- not using, b/c aliases set-up in zsh (doesn't seem to play well with .gitconfig aliases)

`count`
- total commit count
- `g count -all` shows per-contributor counts

`commits-since`
- defaults to 'last week'

`effort`
- outputs number of commits per file
- `g effort --above 5`

`summary`
- outputs a full summary of the repo


`contrib AUTHOR`
- output author's contributions to a project: `g contrib ryandeussing` 