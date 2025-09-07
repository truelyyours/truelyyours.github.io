---
title: "Automating Content Sync with GitHub Actions"
description: "How to automatically sync content from private repositories while maintaining privacy"
tags: 
  - automation
  - github-actions
  - workflow
  - privacy
date: 2024-09-05
---

# Automating Content Sync with GitHub Actions

One of the challenges in maintaining a digital garden is keeping your public site in sync with your private notes while maintaining privacy boundaries.

## The Challenge

When working with sensitive information—like HTB writeups, work notes, or personal reflections—you need a system that can:

- Automatically sync approved content
- Exclude private or sensitive material
- Maintain consistent publishing schedules
- Handle different content formats gracefully

## My Solution

I've developed a GitHub Actions workflow that:

1. **Monitors my private repository** for changes
2. **Filters content** based on predefined rules
3. **Transforms formats** as needed (Obsidian → Quartz)
4. **Publishes updates** to the public site

## Content Filtering Rules

My filtering system uses several criteria:

### Folder-based Exclusions
```yaml
exclude_paths:
  - "private/"
  - "work/"
  - "htb-machines/"
  - ".obsidian/"
```

### Tag-based Filtering
Posts tagged with `#private` or `#draft` are automatically excluded from sync.

### Date-based Publishing
Future-dated posts remain private until their publish date.

## Implementation Details

The workflow runs on a schedule and also responds to manual triggers:

```yaml
on:
  schedule:
    - cron: '0 */6 * * *'  # Every 6 hours
  workflow_dispatch:  # Manual trigger
```

## Benefits

This automation has transformed my workflow:

- **Reduced friction**: I can write freely without worrying about accidental publication
- **Consistent updates**: Regular sync keeps the public site fresh
- **Peace of mind**: Sensitive content stays private automatically

## Future Improvements

I'm considering adding:
- Content staging area for review before publication
- Automatic social media posting
- Analytics integration for popular content

The goal is to make sharing knowledge as frictionless as possible while maintaining appropriate boundaries.
