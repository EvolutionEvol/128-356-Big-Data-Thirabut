# ☁️ Student Guide: Syncing Lectures in Google Colab

If you are using Google Colab, you might be saving your work to **Google Drive** or directly to **GitHub**.

## Option A: Using Google Drive (Recommended for keeping all files together)
To get the teacher's new Week 3 updates, you can run Git commands directly inside a Colab cell.

### Step 1: Mount Google Drive
Create a new cell at the top of any notebook and run this to connect your files:
```python
from google.colab import drive
drive.mount('/content/drive')
```

---

### Step 2: Navigate to your Project
In a new cell, move into your repository folder (replace `Your-Repo-Name` with your actual folder name):
```bash
%cd /content/drive/MyDrive/Your-Repo-Name
```

---

### Step 3: Run the Sync Commands
Run these commands in a single cell. This will add the teacher's repo and pull the new Week 3 file.

```bash
# 1. Add the teacher's repo (only need to do this once)
!git remote add upstream https://github.com/witsarutsarai12-Academic/128-356-Big-Data.git

# 2. Get the new files
!git fetch upstream

# 3. Merge Week 3 into your Drive
!git merge upstream/main
```

---

### Phase 4: What about Conflicts?
If you edited Week 2 and Git gives an error, run this to **keep your notes** and still get Week 3:
```bash
!git checkout --ours BigData_Week2_FileFormats_and_Storage.ipynb
!git add .
!git commit -m "Fixed conflict in Colab"
```

---

### 💡 Why do it this way?
1.  **Everything in one place**: All your weeks stay in one folder in your Google Drive.
2.  **No re-cloning**: You don't have to delete and restart your project to get new files.
3.  **Real-world skills**: You are learning how professional developers sync code!

---

## Option B: Saving "Copy in GitHub" (No Google Drive)
If you prefer not to mount Drive and just want to save your work directly to your GitHub repo:

1.  **Open the Teacher's New Notebook**: Go to the teacher's Week 3 file on GitHub and click "Open in Colab".
2.  **Save to YOUR GitHub**:
    *   In Colab, go to **File > Save a copy in GitHub**.
    *   Select **your** repository (the Test/Student fork).
    *   Click **OK**.
    
*Note: This method is great for adding new files, but if you need to update an existing file (like Week 2) without losing your notes, Option A (Git) is safer.*
