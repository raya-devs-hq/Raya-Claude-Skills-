# Raya Claude Skills

Shared Claude Code skills for the AI Platform team.

## Skills

### `aip-okr-update`
Generates the monthly AI Platform OKR status update — fetches Jira tickets and GitHub PRs, then creates and populates a Confluence page.

Trigger: `/aip-okr-update`

## Installation

```bash
# Clone the repo
git clone https://github.com/raya-devs-hq/Raya-Claude-Skills-.git

# Copy the skill(s) you want into your Claude skills directory
cp -r Raya-Claude-Skills-/aip-okr-update ~/.claude/skills/
```

Then restart Claude Code — the skill will be available as `/aip-okr-update`.

## Keeping up to date

```bash
cd Raya-Claude-Skills-
git pull
cp -r aip-okr-update ~/.claude/skills/
```
