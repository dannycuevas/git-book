
[Git - git-cherry-pick Documentation (git-scm.com)](https://git-scm.com/docs/git-cherry-pick)


# ✅ **What is `git cherry-pick`?**

`git cherry-pick` lets you **pick a specific commit** from one branch and **apply it** to another branch, even if that commit doesn't belong to it. It’s like **copy-pasting** the commit to your current branch.

---

# 🛠️ **Scenario 1: Recover a Commit After a Bad Rollback**

Let’s say you accidentally did a **hard reset** and deleted a commit:
```
git reset --hard abc1234  # Uh-oh! Lost some important changes!
```

You realize **one of those commits was important**. You can get it back if you know its **commit hash**.

### **Step 1: Find the Commit Hash**

Even after a `--hard reset`, you can still find old commit hashes in the **reflog**:
```
git reflog
```

✅ **Example Output:**
```
d4e5f67 HEAD@{0}: reset: moving to abc1234
f3c2b1a HEAD@{1}: commit: Added new feature
```
The commit you need is `f3c2b1a`.

### **Step 2: Cherry-Pick the Commit**

To **recover it**, simply cherry-pick it:
```
git cherry-pick f3c2b1a
```

✅ **Example Output:**
```
[main 1d4e5f6] Added new feature
 Date: Mon May 8 14:23:42 2023 +0000
 1 file changed, 15 insertions(+)
```

💡 **What Happened?**
- Git took only that **one commit** and **re-applied it** to your current branch.
- You didn't have to undo everything else.

### **Step 3: Push Your Changes**

If this is a shared branch:
```
git push origin main
```

---

# 🛠️ **Scenario 2: Pick a Commit from Another Branch**

You’re working on **feature-branch** and realize that **main** has a bug fix you need **right now**.

### **Step 1: Get the Commit Hash**

Check the history of `main`:
```
git log main --oneline
```

✅ **Example Output:**
```
f3c2b1a Fix critical bug in auth
7e2d5a1 Add new logging
5b4a1c0 Update documentation
```

### **Step 2: Cherry-Pick the Commit**

Switch to your **feature-branch**:
```
git checkout feature-branch
```

Now apply just that **one specific commit**:
```
git cherry-pick f3c2b1a
```

✅ **Output:**
```
[feature-branch 2d3e4f5] Fix critical bug in auth
 Date: Mon May 8 14:23:42 2023 +0000
 1 file changed, 5 insertions(+), 2 deletions(-)
```

💡 **What Happened?**
- The bug fix from `main` is now on your `feature-branch` without merging the whole branch! 🚀

---

# 🔥 **Quick Cheat Sheet for Cherry-Pick**

|**Command**|**What It Does**|
|---|---|
|`git cherry-pick <hash>`|Apply the specific commit to the current branch.|
|`git cherry-pick <hash1> <hash2>`|Apply multiple commits at once.|
|`git cherry-pick --abort`|Stop a cherry-pick if there are conflicts.|
|`git cherry-pick --continue`|Continue after fixing conflicts.|

"`git cherry-pick` allows me to apply specific commits from any branch to my current branch. This is extremely useful for recovering important changes after a bad reset, or for applying isolated fixes without a full merge. It’s like copy-pasting only the good stuff directly into your branch safely."

