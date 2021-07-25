# TERMINAL COMMANDS

Creating a new repository\
`mkdir folder && cd folder` - makes a new directory and switches to it\
`git init` - initializes a new repo in this directory\
Create a new repo with the same name in GitHub\
Grab the SSH url from GitHub\
`git remote add origin URL` - ensures that the local repo and GitHub are in sync\
`git push -u origin master`

Adding/committing/pushing files\
`git add .`\
`git commit -m "Commit message"`\
`git push origin master`\
`git status`

Cloning a forked gist\
`git clone git@gist.github.com:YOUR_FORKS_ID.git lunch`

Lint a program\
`eslint app.js`\
`eslint .`\ 

List
`ls` - list files in the directory \
`ls -l` - list files in long format\
`ls -a` - list files including hidden files

Removing a directory\
`rm -rf path/to/your/gist/directory`

# WEEK 1 - DAY 1

### Gists
What is a gist? It is another git repository.\
Except it's smaller and used for sharing smaller snippets of code.\
Gists cannot be given names.

### Fork
A fork is a GitHub operation.\
Where a user creates their own copy of another GitHub's user's existing repository.\
Forked repo links back to the original.\
However the forked one is fully controllable by the user that created that fork.

Terminal command:\
`git clone git@gist.github.com:YOUR_FORKS_ID.git lunch`

command - git clone\
SSH link - git@gist.github.com:YOUR_FORKS_ID.git\
directory name - lunch

### Linting
Linting helps us fix code inconsistencies.\
Analyzes code to see what errors, bugs, stlistic errors, and suspicious constructs are present.

Terminal command:\
`eslint app.js`\
`eslint .`

# WEEK 1 - DAY 4

### Vim
Vim Cheat Sheet:\
![Vim Cheat Sheet](http://www.viemu.com/vi-vim-cheat-sheet.gif)

### Recursion

To start figuring out how to solve a problem using recursion, it's helpful to first figure out the base case and the recursive case. 

The recursive case is when the function will continue to call itself. Every time the function calls itself, the input gets closer and closer to the base case.

The base case involves no calls to itself.

The base case is simply when the function doesn't make any recursive calls.

Packages are self-contained code libraries that we can install and use in our projects.

