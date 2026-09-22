# Setup Installation Guide

A personal installation guide for configuring my iOS development environment on iPhone. This note consolidates the required setup procedures, tools, and configurations, along with a reference tutorial from Proflead for additional guidance. It serves as a quick reference for future installations, maintenance, and troubleshooting.

### What Would Need
1. GitHub Account & Repository
2. GitHub Access Token
3. SSH key (optional)
4. Git
5. Obsidian
6. Git Plugin for Obsidian
7. iSH app for iPhone
8. Obsidian App for iPhone :

---
### Installation

```bash
# git clonning repo
git clone --depth=1 https://Stonieeeee:(Add token here)@github.com/Stonieeeee/MyObsidianVault.git
```

#### iOS Environment (Setup)

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

### Reference Links

- [Obsidian Setup Tutorial by proflead](https://proflead.dev/posts/sync-obsidian-notes-for-free-mobile-and-desktop/)