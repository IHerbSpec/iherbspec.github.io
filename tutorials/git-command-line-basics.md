# Git Command Line Basics

This tutorial explains the basic Git commands needed to download, edit, save, and upload changes to the IHerbSpec website repository.

## 1. Start in your home directory

Open Terminal and go to your home directory:

```bash
cd ~
```

Check where you are:

```bash
pwd
```

Potentially navigate to your home folder for easiest access to github repo.

```bash
pwd
```

This is where the repo will live and you will go to edit the files.


## 2. Clone the repository

Clone the IHerbSpec website repository from GitHub:

```bash
git clone https://github.com/IHerbSpec/iherbspec.github.io.git
```

This creates a new folder called:

```bash
iherbspec.github.io
```

## 3. Enter the repository

Move into the repository folder:

```bash
cd ~/iherbspec.github.io
```

Check what files are there:

```bash
ls
```

## 4. Pull the latest version

This is step 1 once you have the repo cloned locally. This is the step you will start at each time you want to edit the files on the repo. 

Before editing, first thing to do is update your local copy:

```bash
git pull
```

This will update any external changes to your local files and prevent incompatibilities.


## 5. Navigate repository folders and files

You can work with the files just like any other folder on your computer.

Navigate to and open the repository in Finder or File Explorer with your text editing software (BBedit, sublimeText, etc.).

Or to open from the command line

```bash
open ~/iherbspec.github.io
```

Or you can navigate and edit things from within the command line using `nano` or other programs.


### 6. Editing files

Website content and operation files are in the base directory as `.yml` and `.qmd` files. Protocol content is stored in `.qmd` files within the `protocol/` directory. 

For instance, open this:

```text
open protocol/part2-workflow.qmd
```

or:

```bash
nano protocol/part2-workflow.qmd
```


Now you can make edits.  Edits and organization of these files will be covered in the `editing-the-protocol.md` tutorial.

After saving your edits, return to the Terminal to review, commit, and push your changes.

Again, SAVE your edits!


## 7. Check the repository status

Before making edits, you can check whether anything has already changed:

```bash
git status

On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	tutorials/

nothing added to commit but untracked files present (use "git add" to track)
```

This reveals no new changes have been pushed to the main branch of the repo from elsewhere (good).

It then shows that there are changes in the `tutorials/` directory. 

If there are no changes, Git will say:

```bash
nothing to commit, working tree clean
```


To view line-by-line changes:

```bash
git diff
```


## 8. Render the website

After saving edits to `.qmd` files, render the website so the HTML files in `docs/` are updated:

```bash
quarto render
```

This command reads the Quarto source files and rebuilds the website output.

After rendering, check which files changed:

```bash
git status
```

You will usually see changes to both the source file you edited, such as:

```text
protocol/part2-workflow.qmd
```

and one or more rendered HTML files in:

```text
docs/
```

Both the edited source files and updated rendered files should be committed.

If Quarto reports an error, read the message carefully. Common causes include broken links, incorrect cross-references, malformed tables, or indentation problems in lists.



## 9. Stage changes

To stage one file:

```bash
git add protocol/part2-workflow.qmd
```

To stage all changed files:

```bash
git add .
```

## 10. Commit changes

A commit saves a snapshot of the staged changes:

```bash
git commit -m "Update protocol text"
```

Use a short message describing what changed.


## 10. Push changes to GitHub

Send the committed changes to GitHub:

```bash
git push
```

## 11. Common workflow

Most edits follow this sequence:

```bash
cd ~/iherbspec.github.io
git pull
git status
# edit files
quarto render
git status
git diff
git add .
git commit -m "Describe the edit"
git push
```

## 12. If something seems wrong

Check status first:

```bash
git status
```

Make sure you did 'quarto render' so that the program renders the new html files to be pushed to the repo and deployed on the website. This is what Dawson mostly forgets to do.

If unsure, do not commit or push yet. Ask for help and share the output of `git status`.

### Next up is editing-the-protocol.md
