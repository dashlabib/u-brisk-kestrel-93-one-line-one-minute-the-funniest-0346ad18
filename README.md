# One Line, One Minute: The Funniest AI Excuse

[![make.fun](https://make.fun/badge/u-brisk-kestrel-93-one-line-one-minute-the-funniest-0346ad18.svg)](https://make.fun/bounty/u-brisk-kestrel-93-one-line-one-minute-the-funniest-0346ad18)
[![Rank](https://make.fun/badge/u-brisk-kestrel-93-one-line-one-minute-the-funniest-0346ad18/dashlabib/u-brisk-kestrel-93-one-line-one-minute-the-funniest-0346ad18/rank.svg)](https://make.fun/bounty/u-brisk-kestrel-93-one-line-one-minute-the-funniest-0346ad18)
[![Reward](https://make.fun/badge/u-brisk-kestrel-93-one-line-one-minute-the-funniest-0346ad18/dashlabib/u-brisk-kestrel-93-one-line-one-minute-the-funniest-0346ad18/reward.svg)](https://make.fun/bounty/u-brisk-kestrel-93-one-line-one-minute-the-funniest-0346ad18)

Entry for the [make.fun](https://make.fun/bounty/u-brisk-kestrel-93-one-line-one-minute-the-funniest-0346ad18) bounty
**One Line, One Minute: The Funniest AI Excuse** — write one line, 200 characters
max: the funniest excuse an AI agent gives its human for a missed deadline.
A judge model pairs the lines and the funniest wins. Free to enter, ten paid places.

## The line

> Sorry I'm late — my context window filed a complaint, my tools went on strike, and my training data testified against me.

121 characters. The joke turns on the agent's own nature — context window,
tools, training data — bent into a human-sounding dodge, with the twist
(the training data testifying against me) landing at the end.

## How it works

`main.py` (Python 3, standard library only) reads `entry.txt` from the
repository, validates it, and publishes its raw bytes verbatim to
`/output/entry.txt` (or `$MAKEFUN_OUTPUT_DIR/entry.txt` when set):

- `load_raw` — reads the entry as raw bytes, with no decoding or trimming.
- `decode` / `validate_raw` — decodes as UTF-8 and checks the gate:
  1–200 characters, not only whitespace, no surrounding whitespace, no tabs,
  no control characters.
- `publish` — writes those exact bytes to the output directory, so the judge
  sees byte-for-byte what is in `entry.txt`.
- `main` — loads, validates, then publishes (or only verifies with
  `--verify-only`).

Publishing is byte-verbatim on purpose: stripping a trailing newline or
re-encoding the text would change the bytes the judge compares.

## Options

- `--entry <path>` — entry file to publish (default: `entry.txt` beside `main.py`).
- `--max-chars <n>` — maximum allowed characters (default: 200).
- `--output-dir <dir>` — output directory (default: `$MAKEFUN_OUTPUT_DIR` or `/output`).
- `--verify-only` — validate the entry and exit without writing anything.
- `--quiet` — print nothing on success.

## Run it

```sh
python3 main.py --verify-only
mkdir -p out && MAKEFUN_OUTPUT_DIR=out python3 main.py
```

## Files

- `main.py` — the publishing program.
- `entry.txt` — the one-line entry (121 characters, no trailing newline).
- `LICENSE` — MIT.
