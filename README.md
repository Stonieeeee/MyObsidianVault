# My Obsidian Vault
A personal knowledge base and learning repository for my journey as a systems/software developer.

### 1. Installation
```bash
# git clonning repo
git clone --depth=1 https://Stonieeeee:(Add token here)@github.com/Stonieeeee/MyObsidianVault.git
```

#### 1.1 iOS Environment (Setup)

```bash
# install 'iSH' and open
### install git
apk add it
### create directory
mkdir MyObsidianVault
### mount directory
mount -t ios . MyObisidianVault ## Select the obsidian folder in the files and open
### open and clone the directory
cd MyObsidianVault
git clone --depth=1 https://Stonieeeee:(Add token here)@github.com/Stonieeeee/MyObsidianVault.git
```

---
### 2. Issues
#### 2.1 "Merge with conflicts are not supported yet" (Solution)

**Step 1 — Make a backup of your iPhone vault**
Open the **Files** app.
Go to wherever your Obsidian vault stored.

Usually:
```text
On My iPhone
└── Obsidian
	└── YourVault
```
or possibly:
```text
iCloud Drive
└── Obsidian
	└── YourVault
```

**Copy the entire vault**
Long-press your vault &rarr; **Duplicate**
Rename the duplicate:
```text
YourVault_BACKUP
```
This is your safety net.
**Do not delete the backup.**

**Step 2 — Make a backup of your iPhone vault**
On your iPhone:
1. Swipe up from the bottom.
2. Find Obsidian.
3. Swipe Obsidian away.

We don't want Obsidian holding files open while we're replacing the vault.

**Step 3 — Remove the corrupted vault**
Go back to:
**Files** &rarr; **your Obsidian vault location**
You'll have something like:
```text
YourVault
YourVault_BACKUP
```
Rename the original:
```text
YourVault
```
to:
```text
YourVault_OLD
```
**Do not delete it yet.**
So now you have:
```text
YourVault_OLD
YourVault_BACKUP
```
This is safer than immediately deleting anything.
**Step 4 — Create an empty vault**
Open Obsidian.

Choose:

**Create new vault**

Use exactly the vault name you normally use, for example:
```text
MyObsidianVault
```
When choosing the location:

⚠️ **Don't select iCloud storage for this Git setup.**
The Obsidian Git documentation specifically recommends **not selecting "Store in iCloud"** when setting up a Git repository on iOS.

Use something like:
```text
On My iPhone
└── Obsidian
	└── MyObsidianVault
```
You should now have:
```text
On My iPhone
└── Obsidian
	├── MyObsidianVault         ← NEW empty vault
	├── YourVault_OLD 
	└── YourVault_BACKUP
```

**Step 5 — Install Obsidian Git**
In the new empty vault:

**Setting** &rarr; **Community plugins**

Install:

**Obsidian Git**

Enable it.

**Step 6 — Configure your GitHub authentication**
Go to:
**Setting &rarr; Community plugins &rarr; Obsidian Git**
Find:
**Authenication/Commit Author**
```text
Username: your GitHub username
Password: your GitHub Personal Access Token (VaultToken-Iphone classics)
Name: your Git commit name 
Email: your Git commit email
```
For GitHub HTTPS authentication, the Obsidian Git documentation says to use a **Personal Access Token**, rather than your normal GitHub password.

If your existing configuration already worked before, you can use the same credentials.

**Step 7 — Install Obsidian Git**
Open the Obsidian command palette:

**Ctrl/Cmd equivalent on iOS isn't needed — use the command palette button.**

Search:
```text
Git: Clone existing remote repo
```
Select it.

Enter your repository URL.

For example:
```text
https://github.com/USERNAME/REPOSITORY.git
```
The Obsidian Git documentation specifically states that the clone URL should have `.git` appended.

**Step 8 — Let the clone finish**
Don't close Obsidian while it's cloning.

You should eventually get a message asking you to restart Obsidian.

Restart it.

At this point, your iPhone should have a **brand-new Git repository**.

The old corrupted:
```text
.git/index
```
is gone.

A new one was created from GitHub.

**Step 9 — Verify your vault**

**Step 10 — Test Pull**

**Step 11 — Test Commit + Push**

**Done.**
