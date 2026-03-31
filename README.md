# PassionSeed Agent Skills

Universal agent skills that work with **Droid (Factory)**, **Claude Code**, and other agents that support `SKILL.md` format.

## Skills

| Skill | Description |
|-------|-------------|
| `pathlab-manager` | Manage expert interviews, PathLab content, seeds, paths, and Supabase data |

## Quick Install

### Droid (Factory)
```bash
droid skills add pathlab-manager https://github.com/passionseed/ps-skills/tree/main/pathlab-manager
```

### Claude Code
```bash
# Clone to your project's .claude/skills/ directory
git clone https://github.com/passionseed/ps-skills.git /tmp/ps-skills
cp -r /tmp/ps-skills/pathlab-manager .claude/skills/
```

Or add to your global Claude skills:
```bash
mkdir -p ~/.claude/skills
git clone https://github.com/passionseed/ps-skills.git ~/.claude/skills/passionseed
```

## Adding New Skills

1. Create a folder: `mkdir new-skill-name/`
2. Add `SKILL.md` with YAML frontmatter:
   ```yaml
   ---
   name: skill-name
   description: Use when... 
   ---
   ```
3. Update this README
4. Commit and push

## Skill Format

All skills use the standard markdown format supported by both Droid and Claude Code:

```markdown
---
name: skill-identifier
description: Trigger description for the agent
---

# Skill Title

## Overview
...
```

## Syncing Across Devices

```bash
# Pull latest skills
git pull origin main

# Or re-add in Droid
droid skills add pathlab-manager https://github.com/passionseed/ps-skills/tree/main/pathlab-manager --force
```
