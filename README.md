# MeshBench scripting skills

Agent skills for **driving and scripting** a running [MeshBench](https://github.com/MeshBench/meshbench)
workbench from outside — the Python, Go or Node client, the control socket, or
raw verbs. For people *using* MeshBench, not developing it (those live in
[meshbench-dev-skills](https://github.com/MeshBench/meshbench-dev-skills)).

Two skills:

| skill | when it loads |
|---|---|
| `meshbench-driving` | driving the simulator to answer an RF or mesh question — coverage, why a packet failed, site selection, a firmware A/B |
| `meshbench-scripting` | writing or debugging a script that opens a session, brings a mesh up and waits for it — an example, a CI check, a soak driver |

Both encode what silent failures taught, which is the part a fresh reading of
the verb list will not give you.

## Installing

A skill is a directory with a `SKILL.md` whose front-matter carries a `name`
and a `description`; an agent loads it by that description when a task matches.
The format is portable, so drop the directories where your agent looks:

- **Claude Code** — copy `skills/<name>` into `.claude/skills/` in your project,
  or into `~/.claude/skills/` for every project. It is read on the next run.
- **Cursor / Windsurf and other agents** — point your agent's rules/skills
  directory at `skills/`, or paste a `SKILL.md` into the project rules. The
  content is plain Markdown; nothing here is Claude-specific bar the directory
  convention.

```bash
git clone https://github.com/MeshBench/meshbench-scripting-skills
cp -r meshbench-scripting-skills/skills/* ~/.claude/skills/
```

## Keeping them true

These are maintained in the MeshBench repository under `.claude/skills/` and
mirrored here for installing elsewhere. The canonical copy is the one beside the
code; when they disagree, that one is right.
