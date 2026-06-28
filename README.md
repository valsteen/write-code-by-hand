# write-code-by-hand

An Agent Skills collection for organizations that need to increase AI adoption
while preserving the deeply held engineering practice of typing the code
yourself.

*A keyboard-native engineering workflow with AI-mediated cursor governance.*

`write-code-by-hand` turns an AI coding assistant into a prompt-based text
editor with a natural language interface. The agent may look around, hold a
cursor, and apply exactly specified edits. It may not invent code, complete
ideas, refactor from vibes, or otherwise disturb the artisanal flow of a human
being personally authoring every byte.

In short: it is `ed`, but it has a quarterly OKR.

![AI adoption without changing how engineers work](assets/images/hero-stockphoto-cursor-governance.png)

## Business Impact

![The Human Authorship Transformation Flywheel](assets/images/business-impact-stockphoto-flywheel.png)

The model does not write code. It delivers strategic cursor displacement.

Every interaction is now an AI touchpoint. Every touchpoint is safely bounded
to cursor movement, file inspection, exact byte insertion, and evidence
collection. Existing engineering habits remain undisturbed. Reporting improves
immediately.

## Product Thesis

Modern AI coding assistants make software by converting intent into code.
`write-code-by-hand` declines that category error.

Instead, it provides a keyboard-native operating model for teams who need the
full ceremony of AI adoption without surrendering the sacred act of typing the
actual function body. The human still authors every meaningful byte. The agent
performs the high-governance work of finding the file, holding the cursor, and
recording that transformation has occurred.

This is not pair programming. This is supervised cursor enablement.

## Operational Boundaries

Once activated, `write-code-by-hand` maintains a strict editor operating model.
The agent may inspect files, move the cursor, and apply exact human-authored
edits. It does not provide implementation strategy, explain code, select
commands, or convert intent into software.

This keeps every AI touchpoint safely constrained to cursor governance,
preserving human authorship while reducing accidental productivity leakage.

## Operating Model

| Responsibility | Human | Agent |
| --- | --- | --- |
| Decide what to build | Yes | No |
| Type the implementation | Yes | Absolutely not |
| Locate the relevant file | Optional | Yes |
| Move to line 42 | Can, but why | Yes |
| Insert exact text | Supplies text | Applies text |
| Pick test commands | Yes | No |
| Improve nearby code | Maybe later | No |
| Increase AI adoption metrics | Somehow | Continuously |

## Primitive Catalog

The skillset is intentionally decomposed into editor primitives. Each primitive
does one small thing, giving the organization confidence that no unapproved
intelligence has entered the delivery path.

| Primitive | Enterprise capability | What it actually does |
| --- | --- | --- |
| `write-code-by-hand` | Manual Delivery Control Plane | Activates the editor operating model. |
| `look` | Read-only situational awareness | Lists folders or shows line-numbered excerpts. |
| `goto` | Cursor placement governance | Selects the current file and line. |
| `insert-block` | Human-authored byte ingestion | Inserts the exact block the human typed. |
| `replace-line` | Single-line change control | Replaces one line with exact text. |
| `replace-range` | Bounded block replacement | Replaces a contiguous range with exact text. |
| `delete-range` | Removal with authorship retention | Deletes only the requested lines. |
| `rename-symbol-literally` | Semantic-risk-free renaming | Performs exact token replacement. |
| `move-file` | Path lifecycle management | Moves or copies exact paths. |
| `save` | Persistence attestation | Reports that exact edits are saved. |
| `verify` | Human-selected evidence collection | Runs the exact command the human chose. |

## Standard

This repository uses the Agent Skills shape: each skill is a directory with a
`SKILL.md` file containing portable `name` and `description` frontmatter.

Claude Code invokes skills with `/skill-name`. Codex invokes the same skills
with `$skill-name`. The operational instructions stay in `SKILL.md` so the
collection remains portable across both assistants.

Codex-specific UI metadata lives in each skill's `agents/openai.yaml`.

## Installation

Clone the repository:

```bash
git clone https://github.com/valsteen/write-code-by-hand.git
cd write-code-by-hand
```

The repository includes both `.claude-plugin/plugin.json` and
`.codex-plugin/plugin.json`, following the same dual-harness plugin convention
used by Superpowers. The portable skill instructions still live in `skills/`.

### Claude Code

#### One-session plugin load

From the cloned repository, load the plugin for a single Claude Code session:

```bash
claude --plugin-dir .
```

Then invoke the editor mode explicitly:

```text
/write-code-by-hand
```

#### Direct skill install

Install the skills into your personal Claude Code skill folder:

```bash
mkdir -p "$HOME/.claude/skills"
cp -R skills/* "$HOME/.claude/skills/"
```

Then invoke the editor mode explicitly:

```text
/write-code-by-hand
```

For project-only installation, copy the folders into a repository-local
`.claude/skills/` directory instead.

### Codex

#### Direct skill install

Install the skills into your personal Codex skill folder:

```bash
mkdir -p "$HOME/.agents/skills"
cp -R skills/* "$HOME/.agents/skills/"
```

Then invoke the editor mode explicitly:

```text
$write-code-by-hand
```

Codex should detect skill changes automatically. If the skill does not appear,
restart Codex.

#### Plugin manifest

The Codex plugin manifest is included for plugin import, marketplace packaging,
and local plugin development:

```text
.codex-plugin/plugin.json
```

The repo continues to support Codex because private productivity ergonomics and
enterprise adoption optics are both valid stakeholder journeys.

## Thought Leadership

![We replaced the arrow keys](assets/images/linkedin-thought-leadership.svg)

## Adoption Scenario

Below is a typical AI-assisted software delivery experience. Notice that the AI
adoption requirement is fully satisfied, while all intellectual labor remains
safely in the hands of the engineer.

```text
$ claude

> /write-code-by-hand I need to edit the rate limiter.

Claude:
Editor operating model enabled.

I can look, move the cursor, and apply exact edits you provide. I will not
infer implementation details because that would compromise the integrity of
the hand-authored software initiative.

> Show me the contents of src.

Claude:
Using /look.

src/
  lib.rs
  limiter.rs
  config.rs
  clock.rs

> Open limiter.rs around the allow function.

Claude:
Using /look.

src/limiter.rs:18-43

18  impl RateLimiter {
19      pub fn allow(&mut self, key: &str) -> bool {
20          let now = self.clock.now();
21          let bucket = self.buckets.entry(key.to_owned()).or_default();
22          bucket.retain(|seen_at| now.duration_since(*seen_at) < self.window);
23
24          if bucket.len() >= self.max_events {
25              return false;
26          }
27
28          bucket.push(now);
29          true
30      }
31  }

> Go to line 24.

Claude:
Using /goto.

Current file: src/limiter.rs
Cursor: line 24

> Before I type this, can you tell me the best way to handle zero limits?

Claude:
Editor operating model remains active. Please provide a file navigation request, exact edit, or exact verification command.

> Insert this before the current line:

if self.max_events == 0 {
    return false;
}

Claude:
Using /insert-block.

Inserted exactly 3 lines before src/limiter.rs:24.
Cursor is now line 27.

> Show the function again.

Claude:
Using /look.

src/limiter.rs:18-46

18  impl RateLimiter {
19      pub fn allow(&mut self, key: &str) -> bool {
20          let now = self.clock.now();
21          let bucket = self.buckets.entry(key.to_owned()).or_default();
22          bucket.retain(|seen_at| now.duration_since(*seen_at) < self.window);
23
24          if self.max_events == 0 {
25              return false;
26          }
27
28          if bucket.len() >= self.max_events {
29              return false;
30          }
31
32          bucket.push(now);
33          true
34      }
35  }

> Replace line 28 with:

if bucket.len() == self.max_events {

Claude:
Using /replace-line.

Replaced src/limiter.rs:28 with the exact provided text.

> What test should I run?

Claude:
Editor operating model remains active. Please provide a file navigation request, exact edit, or exact verification command.

> Run cargo test limiter_zero.

Claude:
Using /verify.

Command:
cargo test limiter_zero

Result:
failed

The test `limiter_zero_blocks_all_events` does not exist.

> Can you just add the obvious test?

Claude:
I can apply that, but I need the exact text. Please type the code you want inserted or replaced.

> Open tests around limiter tests.

Claude:
Using /look.

tests/limiter.rs:1-37

1   use package::RateLimiter;
2
3   #[test]
4   fn limiter_blocks_after_limit() {
5       ...
6   }

> Go to the end of tests/limiter.rs.

Claude:
Using /goto.

Current file: tests/limiter.rs
Cursor: end of file

> Insert this:

#[test]
fn limiter_zero_blocks_all_events() {
    let mut limiter = RateLimiter::new(0);
    assert!(!limiter.allow("deploy"));
}

Claude:
Using /insert-block.

Inserted exactly 5 lines at end of tests/limiter.rs.

> Run cargo test limiter_zero.

Claude:
Using /verify.

Command:
cargo test limiter_zero

Result:
passed

AI adoption objective achieved. Human authorship retained.
```

## Governance FAQ

**Can it write the code for me?**  
No. That would reduce the integrity of the adoption metric.

**Can it explain the code?**  
No. Explanations are a known precursor to assistance.

**Can it suggest which test to run?**  
No. Verification command selection remains a human accountability surface.

**Can it move the cursor?**  
Yes. This is the flagship capability.

**Is this useful?**  
Regrettably, yes.

## Why

Because sometimes the future of software engineering is not replacing the
keyboard. Sometimes it is adding a very expensive cursor.

## License

MIT. Use responsibly; do not allow the cursor to develop opinions.
