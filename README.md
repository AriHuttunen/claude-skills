# Claude Skills

A collection of custom skills for [Claude Code](https://claude.ai/code).

## Skills

### [repo-why](repo-why/)

Analyse a software project's purpose using Simon Sinek's **Start With Why** framework. Produces a structured Why/How/What assessment of any codebase — from a local directory or a repository URL.

## Installation

Clone this repository, then copy the skill you want into your Claude Code skills directory:

```bash
git clone https://github.com/AriHuttunen/claude-skills.git
cp -r claude-skills/repo-why ~/.claude/skills/repo-why
```

Claude Code automatically discovers skills from `~/.claude/skills/`. After copying, the skill is immediately available — invoke it with `/repo-why` or just ask about a project's purpose.

## License

[MIT](LICENSE)
