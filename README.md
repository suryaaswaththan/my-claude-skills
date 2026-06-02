# my-claude-skills

A backup of my personal [Claude Code](https://claude.com/claude-code) skills. Each
subdirectory is one skill containing a `SKILL.md` (plus any supporting scripts,
prompts, or assets the skill needs).

Claude Code automatically discovers any skill placed in `~/.claude/skills/`.

## What's in here

33 skills, each in its own folder:

| Skill | Skill | Skill |
|-------|-------|-------|
| brainstorming | gpt-taste | requesting-code-review |
| brandkit | high-end-visual-design | senior-architect |
| context-engineering-collection | image-to-code | stitch-design-taste |
| design-taste-frontend | imagegen-frontend-mobile | subagent-driven-development |
| design-taste-frontend-v1 | imagegen-frontend-web | systematic-debugging |
| dispatching-parallel-agents | impeccable | test-driven-development |
| emil-design-eng | industrial-brutalist-ui | ui-ux-pro-max |
| executing-plans | minimalist-ui | using-git-worktrees |
| finishing-a-development-branch | receiving-code-review | using-superpowers |
| frontend-design | redesign-existing-projects | verification-before-completion |
| full-output-enforcement | writing-plans | writing-skills |

Some skills (e.g. `context-engineering-collection`) bundle nested sub-skills, so the
total number of `SKILL.md` files in the repo is higher than 33.

## Install on a new device

These skills live in your **user** skills directory: `~/.claude/skills/`.

### Option A — clone the whole repo as your skills directory

If you don't already have a `~/.claude/skills/` directory:

```bash
git clone https://github.com/suryaaswaththan/my-claude-skills.git ~/.claude/skills
```

Restart Claude Code (or start a new session). Run `/help` or just ask Claude to
list skills to confirm they loaded.

### Option B — you already have a `~/.claude/skills/` directory

Clone elsewhere and copy the skill folders in, so you don't clobber existing skills:

```bash
git clone https://github.com/suryaaswaththan/my-claude-skills.git /tmp/my-claude-skills
mkdir -p ~/.claude/skills
cp -R /tmp/my-claude-skills/*/ ~/.claude/skills/
rm -rf /tmp/my-claude-skills
```

### Option C — install a single skill

```bash
git clone https://github.com/suryaaswaththan/my-claude-skills.git /tmp/my-claude-skills
mkdir -p ~/.claude/skills
cp -R /tmp/my-claude-skills/senior-architect ~/.claude/skills/
```

Replace `senior-architect` with whichever skill folder you want.

## Updating this backup

When you add or change skills locally:

```bash
cd ~/.claude/skills
git add -A
git commit -m "Update skills"
git push
```

> **Note:** Skills are stored here as **real files**, not symlinks. If you maintain a
> source copy elsewhere (e.g. `~/.agents/skills`), copy the real content into this
> directory before committing — git stores a symlink as just its target path, not the
> file contents, so symlinked skills would push as empty links and not transfer to
> other devices.

## How skills work

Each skill is a folder with a `SKILL.md` whose YAML frontmatter (`name`,
`description`) tells Claude when to use it. Claude Code loads the metadata of every
skill in `~/.claude/skills/` at startup and invokes the full skill on demand. See the
official docs: <https://docs.claude.com/en/docs/claude-code/skills>.
