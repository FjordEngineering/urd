# urd

A terminal-based time tracker built with Go and [Bubble Tea](https://github.com/charmbracelet/bubbletea). Named after Urðr, the Norse Norn who governs the past — fitting for a tool that records what has been.

Define work streams, activate one or more simultaneously, and see live timers tick. Data persists in a local `urd.json` file.

## Install

```
go install github.com/nshern/urd@latest
```

Or clone and build:

```
git clone https://github.com/nshern/urd.git
cd urd
go build .
```

## Usage

```
./urd
```

The TUI launches in fullscreen. Work streams are listed with their elapsed time, percentage of wall-clock time, and a red dot when actively recording.

## Key Bindings

| Key | Action |
|---|---|
| `j` / `k` / arrows / `ctrl+j` / `ctrl+k` | Navigate up/down |
| `1`-`9` | Jump to stream by number |
| `enter` / `space` | Toggle stream active/inactive |
| `o` | Add stream below cursor |
| `O` | Add stream above cursor |
| `dd` | Delete stream (confirms if time recorded) |
| `s` | Stop all active streams |
| `c` | Continue previously active streams |
| `q` / `ctrl+c` | Save and quit |

## Features

- Multiple streams can be active simultaneously
- Wall-clock time tracks actual time spent (no double-counting overlaps)
- Total time shows the sum of all stream durations
- Per-stream percentage of wall-clock time
- Streams auto-sort: active first, then by elapsed time descending
- Stop all / continue workflow for breaks
- Data validation on load detects inconsistent state

## Data

All data is stored in `urd.json` in the current directory. The file is written atomically (write to temp file, then rename) to prevent corruption.

## Tests

```
go test ./...
```
