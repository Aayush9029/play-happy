# play-happy

`play-happy` is a Bash CLI that plays a random meme video with a text overlay in `mpv`. AI agents run it after a long task. It ships through the Homebrew tap `aayush9029/tap`. Status: shipped.

## Commands

| Task | Command |
|------|---------|
| Run | `bin/play-happy "we shipped it"` |
| Pick a video | `bin/play-happy -p gladiator "are you not entertained"` |
| List videos | `bin/play-happy -l` |
| Skip the lid check | `bin/play-happy --no-check "testing locally"` |
| Release | Load the `oss-cli-release` skill |

## How it works

- `bin/play-happy` is the full tool. It needs `mpv`.
- It loads videos from `$(brew --prefix)/share/play-happy/media`. If that folder does not exist, it uses `media/` next to the script.
- It reads `AppleClamshellState` from `ioreg` and does nothing when the lid is closed.

## Rules

- Add a video as an `.mp4` file in `media/`. The file name without `.mp4` is the name for `-p`.
- The tap formula `../../homebrew-tap/Formula/play-happy.rb` installs `bin/play-happy` and copies `media/*.mp4` to `share/play-happy/media`. If you add another media type, update the formula too.
- This repository has no `LICENSE` file, and the formula has no `license` line.
- Keep `VERSION` in `bin/play-happy` the same as the git tag.
