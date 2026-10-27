# Contributing

## Changelog

[`CHANGELOG.md`](CHANGELOG.md) is generated at release time by
[chloggen](https://github.com/open-telemetry/opentelemetry-go-build-tools/tree/main/chloggen),
the same tool the core semantic conventions use. Don't edit it directly. Instead, add one
entry file under `.chloggen/` to every pull request that changes something consumers of this
registry should notice, which is usually anything under `model/`.

1. Run `make chlog-new`. It needs Go on PATH, and creates `.chloggen/<branch-name>.yaml`
   from [`.chloggen/TEMPLATE.yaml`](.chloggen/TEMPLATE.yaml).
2. Fill it in:
   - `change_type`: one of `breaking`, `deprecation`, `new_component`, `enhancement`,
     `bug_fix`.
   - `component`: the namespace under `model/` the change affects, e.g. `browser`.
   - `note`: one sentence, written for someone consuming the conventions.
   - `issues`: the issue or pull request number(s).
3. Check it with `make chlog-validate`, and see how it renders with `make chlog-preview`.

A pull request that doesn't need an entry (tooling, CI, docs typos, …) can put `[chore]` in
its title or get the `Skip Changelog` label instead. Renovate's pull requests are exempt.
The [Changelog workflow](.github/workflows/changelog.yml) enforces all of this.
