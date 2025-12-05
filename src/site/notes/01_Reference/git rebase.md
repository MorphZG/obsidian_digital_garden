---
{"dg-publish":true,"permalink":"/01-reference/git-rebase/","title":"How to Squash Your Last 4 Git Commits","tags":["devops","linux","utility"]}
---


# How to Squash Your Last 4 Git Commits

Here are the step-by-step instructions to combine your last four commits into a single one.

### Step 1: Start the Interactive Rebase

Open your terminal and run the following command to start an interactive rebase for the last 4 commits:

```sh
git rebase -i HEAD~4
```

This will open your default text editor (like Vim or Nano) with a list of the last four commits, looking something like this:

```sh
pick a1b2c3d Commit message 1
pick e4f5g6h Commit message 2
pick i7j8k9l Commit message 3
pick m0n1o2p Commit message 4

# Rebase ...
#
# Commands:
# p, pick <commit> = use commit
# s, squash <commit> = use commit, but meld into previous commit
# ...
```

### Step 2: Mark Commits for Squashing

You want to combine all of these into the first commit. To do this, change the word `pick` to `squash` (or just `s`) for the second, third, and fourth commits.

Leave the first commit as `pick`. It will look like this:

```sh
pick a1b2c3d Commit message 1
squash e4f5g6h Commit message 2
squash i7j8k9l Commit message 3
squash m0n1o2p Commit message 4
```

When you save and close this file, Git will meld these four commits together.

### Step 3: Write the New Commit Message

After you save the first file, Git will immediately open another editor window. This window contains the commit messages from all four of your previous commits.

You can now delete the old messages and write a single, clear commit message that describes the combined change.

Once you are happy with the new message, save and close the file.

### Step 4: Force Push the Changes

Your local history is now changed. To update your remote repository on GitHub, you need to force push. It is best practice to use `--force-with-lease`, which is a safer version of `--force`. It ensures you don't overwrite work if someone else has pushed to the branch in the meantime.

```sh
git push --force-with-lease
```

## Read more

- [[01_Reference/git reference\|git reference]] - Personal note
