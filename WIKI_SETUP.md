# Wiki.js Setup Guide

## Structure Created ✅

All files are organized into 19 thematic directories for Wiki.js.

## What Was Done:

1. ✅ Created main file `home.md` - home page for Wiki.js
2. ✅ Created 19 directories by topic
3. ✅ All existing MD files moved to corresponding directories
4. ✅ Updated `README.md` with structure description

## Directory Structure:

```
ecozy_identity_guidline/
├── home.md (Wiki.js home page)
├── README.md (repository description)
│
├── introduction/ (1 file)
├── brand-policies/ (4 files)
├── development-policies/ (12 files) 
├── technology-roadmap/ (9 files)
├── logo/ (8 files)
├── typography/ (5 files)
├── colors/ (5 files)
├── style/ (4 files)
├── images/ (3 files)
├── visual-identity/ (11 files)
├── sustainability/ (1 file)
├── it-security/ (1 file)
├── gdpr/ (1 file)
├── privacy-policy/ (1 file)
├── terms-of-use/ (1 file)
├── partnerships/ (1 file)
├── distribution-network/ (1 file)
├── authors/ (1 file)
└── company-data/ (1 file)

Total: 71 files in 19 directories
```

## Importing to Wiki.js:

### Method 1: Git Sync (recommended)
1. In Wiki.js, go to Administration → Storage
2. Configure Git Storage and point to this repository
3. Wiki.js will automatically synchronize all files
4. The `home.md` file will become the home page

### Method 2: Manual Import
1. In Wiki.js, create pages manually
2. Copy content from MD files
3. Create folder structure matching the directories

## Front Matter for New Pages:

Each new MD file for Wiki.js should start with:

```yaml
---
title: Page Title
description: Page description
published: true
date: 2025-12-18T10:00:00.000Z
tags: tag1, tag2, tag3
editor: markdown
dateCreated: 2025-12-18T10:00:00.000Z
---
```

## Navigation:

Wiki.js will automatically create navigation based on:
- Directory structure
- Front matter in files
- File names

## Next Steps:

1. Add front matter to existing files (if not already added)
2. Configure Git Storage in Wiki.js
3. Synchronize the repository
4. Configure navigation and appearance in Wiki.js

## Useful Links:

- Wiki.js Documentation: https://docs.requarks.io/
- Git Storage Setup: https://docs.requarks.io/storage/git
- Markdown Guide: https://docs.requarks.io/editors/markdown

---

**Status:** Ready for Wiki.js import ✅
