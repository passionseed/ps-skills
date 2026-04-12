# PassionSeed Agent Skills

Universal agent skills that work with **Droid (Factory)**, **Claude Code**, and other agents that support `SKILL.md` format.

## Skills

| Skill | Description |
|-------|-------------|
| `hackathon-journey-manager` | Manage hackathon programs, phases, activities, content, and assessments |
| `hackathon-learning-activities` | Update hackathon learning activity content, naming, ordering, metadata, assessments, and production Supabase rows |
| `thai-cinematic-comic-generation` | Generate cinematic portrait comic concepts, Thai captions, panel scripts, and hackathon-ready content payloads |
| `webtoon-cutter` | Cut long webtoon images into mobile-friendly chunks, upload them, and generate DB-ready metadata |
| `pathlab-manager` | Manage expert interviews, PathLab content, seeds, paths, and Supabase data |

## Quick Install

### All Skills at Once

```bash
# Clone to your project
git clone https://github.com/passionseed/ps-skills.git /tmp/ps-skills
cp -r /tmp/ps-skills/* .claude/skills/
```

### Individual Skills

#### hackathon-journey-manager
```bash
droid skills add hackathon-journey-manager https://github.com/passionseed/ps-skills/tree/main/hackathon-journey-manager
```

#### hackathon-learning-activities
```bash
droid skills add hackathon-learning-activities https://github.com/passionseed/ps-skills/tree/main/hackathon-learning-activities
```

#### thai-cinematic-comic-generation
```bash
droid skills add thai-cinematic-comic-generation https://github.com/passionseed/ps-skills/tree/main/thai-cinematic-comic-generation
```

#### webtoon-cutter
```bash
droid skills add webtoon-cutter https://github.com/passionseed/ps-skills/tree/main/webtoon-cutter
```

#### pathlab-manager
```bash
droid skills add pathlab-manager https://github.com/passionseed/ps-skills/tree/main/pathlab-manager
```

## Skill Details

### hackathon-journey-manager

**Use when:** Creating or editing hackathon programs with multiple phases, activities, content, and assessments.

**Features:**
- Create hackathon programs with phases
- Add activities to each phase
- Configure content types (video, text, AI chat, webtoon, etc.)
- Set up assessments and grading
- Manage submission workflows

### hackathon-learning-activities

**Use when:** Updating hackathon learning activity content, metadata, assessments, or production Supabase rows.

**Features:**
- Update activity names and descriptions
- Reorder activities within phases
- Configure metadata and assessments
- Sync to production Supabase
- Generate preview fallbacks

### thai-cinematic-comic-generation

**Use when:** Generating comic-style learning content with Thai captions for hackathon activities.

**Features:**
- Generate cinematic portrait comic concepts
- Create Thai-captioned storyboards
- Write panel scripts with emotional beats
- Prepare production-ready image prompts
- Create DB-ready hackathon comic metadata

### webtoon-cutter

**Use when:** Cutting tall webtoon images into fixed-height chunks for hackathon activities and storage upload.

**Features:**
- Slice long images into mobile-friendly vertical chunks
- Upload chunked assets to Supabase storage
- Generate DB-ready metadata payloads
- Handle uneven final chunk heights safely
- Support hackathon webtoon content workflows

### pathlab-manager

**Use when:** Managing expert interviews, PathLab content, seeds, paths, and learning content in Supabase.

**Features:**
- View and edit expert interviews
- Manage PathLab generation workflow
- Handle seeds, paths, path_days, path_activities
- Work with path_content and assessments
- Admin-level Supabase operations

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
droid skills add hackathon-journey-manager https://github.com/passionseed/ps-skills/tree/main/hackathon-journey-manager --force
```

## Related Skills

These skills work well together:

- **hackathon-journey-manager** + **hackathon-learning-activities** — Create programs and manage content
- **thai-cinematic-comic-generation** + **hackathon-learning-activities** — Generate comics and add to activities
- **webtoon-cutter** + **hackathon-learning-activities** — Slice webtoons and attach chunk metadata to activities
- **pathlab-manager** + **hackathon-journey-manager** — Manage both PathLab and hackathon content
