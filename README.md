# Practicing interactive rebase

## Instructions

In this exercise, we're going to be practicing with the `git rebase --interactive` command (abbreviated to `git rebase -i`).

Before beginning, clone this repo locally and create a new branch with `git checkout -b <your branch name>`

## Part 1: Create git history

Right now, you have no git history for this repo! In part one, we'll add the commits you need in order to rebase in part two.

1. In favorites directory, you'll find several json files that already have examples.

2. In `animals.json`, please add your name and favorite animal as shown in the example. Don't worry too much about syntax being perfect.

3. Before continuing, stage and commit your changes with a message. Don't push up to Github just yet.

```
git add <your file>
git commit -m <your commit message>
```

4. Repeat steps 2 and 3 for the remaining json files.

5. At this point, you should have 7 individual commits on your branch. You can verify this by running `git log` to see the commits, and `git status` to see how far your local branch is ahead of Github.

6. Push your changes upstream to Github with `git push -u origin <your branch name>`. `-u` is short for `--set-upstream-to` which sets the remote branch.

## Part 2: Interactive Rebase

Now you have commits to work with! Yay!

1. It's time to start rebasing. You can enter interactive rebase by running one of the following:

```
git rebase main --interactive
```

```
git rebase main -i
```

This should take you to a screen that looks something like this:

TODO: add image

Most of these commands are pretty specific. For the most part, you won't need to use most of them very often. Today, we're going to try out `pick`, `reword`, `edit`, `squash`, and `drop`.

In order to edit in zsh, you'll need to do `SHIFT + i` or `SHIFT + r` to get into edit mode. From there, you should be able to make the edits below. To quit edit mode and leave this screen, do `ESC`, then `:wq!` as noted below.

2. Using the arrow keys, navigate to the line that contains your first commit, the animals.json one. We'll be keeping your `animals` commit, so you don't have to change anything there.

3. Key down to the line containing your `colors` commit and replace the word `pick` with `reword`.

4. Key down to the line containing your `games` commit and replace the word `pick` with `edit`.

5. Next we'll be skipping the ice cream commit. We still want to keep it, so leave `pick` there. Key down to the line containing your `music` commit and replace the word `pick` with `squash`.

6. Key down to the line containing your `seasons` commit and replace the word `pick` with `drop`.

7. Pick your `snacks` commit, i.e. no changes needed to that line.

8. Save and exit your rebase by keying out of the commit lines and typing `:wq!` and `enter`. `:wq!` writes your changes and quits the rebase UI.

9. Watch as your rebase executes. It will stop in two places: at the `colors` commit, where you can edit the commit message, and the `games` commit, where you can edit the actual commit changes.

10. Once it's complete, run `git log` and inspect the changes.

11. Congrats! You just finished an interactive rebase. What next? You'll see errors if you trying running `git push` on the branch you just rebased. This is because the rebase re-assigned the commit hash of every commit on your branch. Although the changes/diff may be the same, git acknowledges your new branch as a set of completely different commits. For that reason, it's necessary to force push to see your freshly rebased branch up on Github.

```
git push --force origin <your branch name>
```

```
git push -f origin <your branch name>
```

Be sure to double check the branch you're (`git status`) and the commits on your branch (`git log`) before force pushing. Force pushing can be a destructive action! See slide in presentation for more considerations around rebasing.

Don't want to make alterations to your branch, but still want to rebase? 🤔 Simply run `git rebase <base branch name>`. You'll still need to force push if pushing up to a remote branch.
