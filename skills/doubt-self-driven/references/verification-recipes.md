# Verification recipes

How to actually execute a check, per stack. A check that cannot be executed is
not a check.

Before running any of these, state the expected outcome. Then run. Then
compare.

The mistake classes these commands detect are named and explained in
`doubt-catalog.md`. Look there when a command surfaces a gap and you need to
know which class it belongs to, or what to sweep for afterwards.

---

## TypeScript and Node

```sh
npx tsc --noEmit                      # types
npx eslint <files>                    # lint, project config
npx vitest run                        # or jest / npm test
npx prettier --check <files>           # formatting
```

**Prediction examples.** "Type check passes with 0 errors." "The new test
fails before the fix and passes after." "The command exits 0."

**Checks worth making explicit.**

- Run the new test *before* the fix, to prove it can fail. A test that never
  failed proves nothing.
- Run the whole suite, not only the new file. A change can break a distant
  test.
- Check the exit code, not only the output. `echo $LASTEXITCODE` in
  PowerShell, `echo $?` in bash.

---

## Python

```sh
python -m pytest -q
python -m ruff check .
python -m mypy .
```

**Prediction examples.** "12 passed, 0 failed." "mypy reports no error on
`process.py`."

---

## n8n workflows

Use the `n8ncli` tool. It validates locally without an instance.

```sh
n8ncli validate --lint            # syntax, schema, node versions, expressions
n8ncli lint --fix                 # style standards, duplicate names
n8ncli test <file-or-id>          # local run with mock pin data
n8ncli exec <file-or-id>          # real execution, needs a configured env
n8ncli diff --summary             # what actually changed
```

**Prediction examples.** "Validation exits 0 with no warnings." "The test run
produces 3 items, each with a `title` field." "The workflow node count is
unchanged."

**Caveats.**

- `validate` and `test` are local. `exec`, `push` and `nodes search` need a
  configured environment with an access token; without one they fail with an
  authentication error, which is a configuration gap, not a code defect.
- `pull` renames local files to the remote display name. Do not rely on
  custom filenames.

---

## Shell and PowerShell

```sh
# PowerShell
$LASTEXITCODE
# bash
echo $?
```

**Checks worth making explicit.**

- Run with a non-trivial argument, not the empty default.
- Redirect stderr as well as stdout; a silent failure can hide in stderr.
- Check that the command is idempotent when it writes.

---

## Web and HTTP

```sh
curl -s -o body.txt -w "%{http_code}\n" <url>
```

**Prediction examples.** "Status 200." "The body contains the field
`posted_iso`." "The response is under 50 KB."

**Checks worth making explicit.**

- Assert on the *body*, not only the status. A 200 can carry an error page.
- Check the failure status too: 403, 404, 429. A checker that only ever sees
  success paths proves little.
- Check headers when they matter: `content-type`, `retry-after`, pagination
  cursors.

---

## JSON, YAML and config files

Parse them with a real parser. Do not eyeball the syntax.

```sh
node -e "JSON.parse(require('fs').readFileSync('f.json','utf8'))"
node -e "require('js-yaml').load(require('fs').readFileSync('f.yaml','utf8'))"
```

For OpenCode configuration, validate against the published schema:
<https://opencode.ai/config.json>.

**Prediction examples.** "The file parses without error." "The config has 3
keys." "The schema accepts every field used."

---

## Markdown and documents

- Every internal link resolves: extract the paths, check each file exists.
- Every heading anchor referenced actually exists.
- Code blocks with a language tag are syntactically valid for that language.
- Frontmatter parses, and the fields match what the tool expects.

---

## Git and diffs

```sh
git diff --stat
git diff
git status --short
```

**Checks worth making explicit.**

- Read every hunk and justify it against the request. This is the detection
  method for scope drift.
- Check for files that changed but were not meant to: secrets, lockfiles,
  generated artifacts, formatting noise.
- `git diff --check` for whitespace errors.

---

## Frontmatter and skills

A skill file is a document with a contract. Verify it:

- The frontmatter parses as YAML.
- The `description` states when the skill applies, in the words a user would
  use.
- Every file the skill references exists.
- The skill is discovered by the tool that loads it.

```sh
opencode api get /api/skill
```

The response lists every discovered skill with its id, name, description and
path. A skill that is not listed is not loaded, however correct it looks.

---

## Executable artifacts

For anything that runs — a script, a generator, a template engine, a skill
that produces files:

1. Run it against a realistic input.
2. Inspect the output it produced, not just the fact that it exited 0.
3. Run it against an edge input: empty, malformed, oversized.
4. Run it twice, to check it does not corrupt its own state.

The artifact is only verified once its output has been read.
