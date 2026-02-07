# 🎓 Student Guide: How to Sync New Lectures

When your teacher adds new files (like Week 3) or updates the course, you need to "pull" those changes into your project. Here is how to do it without losing your own notes or homework.

---

### Phase 1: One-Time Setup
*Run this only once ever in your project folder.*

Link your project to the teacher's original repository (we call this the **upstream**).
```bash
git remote add upstream https://github.com/witsarutsarai12-Academic/128-356-Big-Data.git
```

---

### Phase 2: Getting New Updates
*Run these steps whenever the teacher releases a new lecture.*

#### 1. Fetch the updates
This downloads the new files from the teacher but doesn't change your code yet.
```bash
git fetch upstream
```

#### 2. Merge the updates
This combines the teacher's new work into your own branch.
```bash
git merge upstream/main
```

---

### Phase 3: Handling Conflicts (The "Week 2" Problem)
If you made your own notes in `Week 2` and the teacher also updated `Week 2`, Git will get confused and say:
`CONFLICT (content): Merge conflict in BigData_Week2...`

**Don't panic! Here is how to fix it:**

1.  **If you want to keep YOUR version of Week 2:**
    ```bash
    git checkout --ours BigData_Week2_FileFormats_and_Storage.ipynb
    git add .
    git commit -m "Fixed conflict: kept my notes"
    ```

2.  **If you want the TEACHER'S version of Week 2:**
    ```bash
    git checkout --theirs BigData_Week2_FileFormats_and_Storage.ipynb
    git add .
    git commit -m "Fixed conflict: updated to teacher version"
    ```

---

### Phase 4: Save to your GitHub
Finally, push everything to your own online repository:
```bash
git push origin main
```

> [!TIP]
> **Why do this?**
> Using `merge` is safer than `downloading zip` because it keeps your history and only adds the new `Week 3` file cleanly while letting you choose what to do with `Week 2`.
