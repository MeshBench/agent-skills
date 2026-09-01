# MeshBench scripting skills

Agent skills for **driving and scripting** a running [MeshBench](https://github.com/MeshBench/meshbench)
workbench from outside: the Python, Go or Node client, the control socket, or
raw verbs. For people *using* MeshBench, not developing it (those live in
[meshbench-dev-skills](https://github.com/MeshBench/meshbench-dev-skills)).

Two skills:

| skill | when it loads |
|---|---|
| `meshbench-driving` | driving the simulator to answer an RF or mesh question: coverage, why a packet missed, site selection, a firmware A/B |
| `meshbench-scripting` | writing or debugging a script that opens a session, brings a mesh up and waits for it: an example, a CI check, a soak driver |

Both encode what silent failures taught, which is the part a fresh reading of
the verb list will not give you: which reply is a refusal wearing the shape of
a success, which wait has a premise that does not hold, and which step decides
whether the mesh relays anything at all.

## Installing

A skill is a directory with a `SKILL.md` whose front matter carries a `name`
and a `description`; an agent loads the description at startup and the body
only when a task matches it. The format is the
[Agent Skills](https://agentskills.io) open standard, so the same directory
works in several agents and only the place it is dropped changes.

```bash
git clone https://github.com/MeshBench/meshbench-scripting-skills
```

| Agent | Project directory | User directory |
|---|---|---|
| Claude Code | `.claude/skills/` | `~/.claude/skills/` |
| VS Code and GitHub Copilot | `.github/skills/`, `.claude/skills/` or `.agents/skills/` | `~/.copilot/skills/`, `~/.claude/skills/` or `~/.agents/skills/` |
| Cursor | `.cursor/skills/` or `.agents/skills/` | `~/.cursor/skills/` or `~/.agents/skills/` |
| Gemini CLI | `.gemini/skills/` or `.agents/skills/` | `~/.gemini/skills/` or `~/.agents/skills/` |
| Codex | `.agents/skills/`, up to the repository root | `~/.agents/skills/` |

Only the Claude Code row is exercised by MeshBench itself. The rest are taken
from each tool's own documentation rather than tested here.

`.agents/skills/` is read by four of the five, so one directory installs for
several agents at once:

```bash
mkdir -p ~/.agents/skills
cp -r meshbench-scripting-skills/skills/* ~/.agents/skills/
```

A symbolic link works in place of a copy, and updates with `git pull` instead
of another copy.

The [documentation site](https://meshbench.github.io/docs/agent-skills.html)
covers this in more detail, including agents that take a skill as an upload
rather than from a directory.

## Keeping them true

These are maintained in the MeshBench repository under `.claude/skills/` and
mirrored here for installing elsewhere. **The canonical copy is the one beside
the code**; when they disagree, that one is right. Mirroring is a manual copy,
so diff before assuming the two agree. The one deliberate difference is the
directory name: `meshbench-driving` here is `meshcoresim` there.
