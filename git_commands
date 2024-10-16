
# Safely Deleting a Git Branch

This guide walks through the steps to safely delete a Git branch, ensuring that no unmerged changes are lost and that the deletion process is smooth.

## 1. Ensure you are not on the branch to be deleted

Before deleting a branch, switch to another branch (e.g., `main` or `master`):

```bash
git checkout main
```

Attempting to delete the branch you are currently on will result in an error.

## 2. Check if the branch has been merged (for local branches)

To safely delete a branch, it's good practice to check if the branch has been merged. You can do this by running:

```bash
git branch --merged
```

This command lists branches that have been merged into the current branch. If your branch appears in the list, it has been merged. If it doesn’t appear, there may still be unmerged changes.

You can also check a specific branch for merge status:

```bash
git branch --merged <branch>
```

## 3. Delete a Local Branch

Once you're sure the branch has been merged (or you're sure you no longer need it), delete the branch using:

```bash
git branch -d <branch-name>
```

If the branch has not been merged and you want to delete it regardless (force delete), use:

```bash
git branch -D <branch-name>
```

## 4. Delete a Remote Branch

To delete a branch from a remote repository (e.g., GitHub):

```bash
git push origin --delete <branch-name>
```

Alternatively, for older Git versions:

```bash
git push origin :<branch-name>
```

## 5. Confirm the Deletion

After deleting the branch, list your branches to confirm:

- To list local branches:
  ```bash
  git branch
  ```

- To list remote branches:
  ```bash
  git branch -r
  ```

---

### Example:

Let's say you want to delete a branch named `feature-branch`:

1. **Switch to another branch**:
   ```bash
   git checkout main
   ```

2. **Check if `feature-branch` has been merged**:
   ```bash
   git branch --merged
   ```

3. **Delete the local branch**:
   ```bash
   git branch -d feature-branch
   ```

4. **Delete the remote branch** (if necessary):
   ```bash
   git push origin --delete feature-branch
   ```
