---
name: skillhub-installer
description: Install any requested SkillHub registry skill from https://skillhub.clinkpay.team into Codex or Claude Code when the user asks to install a SkillHub skill coordinate.


---

# SkillHub Installer

Install the SkillHub skill requested by the user.

## Registry

Always use this registry:

```text
https://skillhub.clinkpay.team
```

## Parse The User Request

Read the skill coordinate from the user's prompt.

Preferred coordinate form:

```text
@<namespace>/<skill-slug>
```

Convert the coordinate before running the CLI:

- `@global/<skill-slug>` -> `<skill-slug>`
- `@<namespace>/<skill-slug>` -> `<skill-slug> --namespace <namespace>`
- `<skill-slug>` -> `<skill-slug>`

Do not pass `@<namespace>/<skill-slug>` directly to `@astron-team/skillhub@latest`. Current CLI releases use `--namespace` for non-global namespaces.

## Choose The Agent Profile

Choose the install target from the runtime you are operating in:

- In Codex, use `--agent codex`.
- In Claude Code, use `--agent claude-code`.

Use user scope so the installed skill remains available after Codex restarts:

```text
--scope user
```

## Install

Run the install command yourself. Do not ask the user to run it.

Build the install command from the parsed user coordinate:

- Set `<agent-profile>` to `codex` in Codex.
- Set `<agent-profile>` to `claude-code` in Claude Code.
- Set `<skill-args>` to the converted CLI arguments from the coordinate parsing section.

Replace every placeholder before execution. Never run a command that still contains `<...>`.

Run:

```bash
npx @astron-team/skillhub@latest install <skill-args> --agent <agent-profile> --scope user --registry https://skillhub.clinkpay.team --json
```

After the command finishes, summarize whether the install succeeded and include the installed directory from the JSON output when available.
