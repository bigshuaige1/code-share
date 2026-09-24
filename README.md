# code-share

A Codex skill for source-grounded technical project guides. It explains WHAT the subject is, WHY it works, and HOW the inspected implementation runs. The default delivery is three separate, in-depth Markdown guides; `low`, `high`, and `ultra` select the depth and figure artifacts.

## Install

Clone this repository into your Codex skills directory:

```bash
git clone https://github.com/bigshuaige1/code-share.git ~/.codex/skills/code-share
```

Install these external skills separately when you use the corresponding workflow:

- [Archify](https://github.com/tt-a1i/archify) creates and validates the diagrams requested by Code Share.
- [Grill Me](https://github.com/mattpocock/skills) runs an opt-in interview about the document structure and figure design.

Neither external repository is bundled here. Follow each project's installation instructions and license.

## Use

- `$code-share` — create the default WHAT, WHY, and HOW guides.
- `$code-share low` or `$code-share ultra` — change the depth or figure artifact set.
- `$code-share grill me` — first discuss the reader's goals, document structure, and figures through a decision-tree interview.

See [SKILL.md](SKILL.md) for the full workflow and [references/figure-workflow.md](references/figure-workflow.md) for figure requirements.
