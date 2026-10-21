# ChapelDirExec

<p align="center">
<img src="/img/cde.png">
</p>

## what `this` is

- `ChapelDirExec` (`cde`) is a fast multithreaded SSH credential auditor written in `C`.
- it scans for live SSH services, then dictionary-attacks logins with a target list and a credentials list.
- fork of the `cbrutekrag` codebase by `Jorge Matricali` — his project, his design, cleaned up and kept alive here.

## what `it` does

- `scan phase` — probes targets for open SSH ports, skips non-SSH / tcpwrapped services.
- `bruteforce phase` — multithreaded login attempts with custom timeout, threads and ports.
- `dry-run` (`-D`) — test your target lists without sending auth traffic.
- `macros` — `$TARGET` expands dynamically inside usernames and passwords.
- `custom output` — pick your log format (`-F`) and write hits to a file (`-o`).

## `build`

```bash
git clone https://github.com/foxcornlab/ChapelDirExec.git
cd ChapelDirExec
make
```

needs `make`, `gcc` and `libssh-dev`:

```bash
sudo apt-get install libssh-dev
```

### `static` build

```bash
bash static-build.sh
make install
```

needs `cmake`, `libssl-dev` and `libz-dev`.

## `usage`

```
usage: cde [-h] [-v] [-aA] [-D] [-P] [-T TARGETS.lst] [-C credentials.lst]
		[-t THREADS] [-F OUTPUT FORMAT] [-o OUTPUT.txt] [TARGETS...]
```

- `-T` targets file, `-C` credentials file (`user:pass` per line)
- `-t` thread count, `-p` custom port
- `-s` scan-only, `-D` dry-run, `-P` progress bar
- `-v` verbose, `-V` libssh debug output
- `-a` accept non-OpenSSH servers too

## `Thanks to`

- `Jorge Matricali` — wrote the original `cbrutekrag` this forks from. (Upstream repo has since been taken down; all original copyright notices kept intact.)

## `disclaimer`

educational and authorized-testing use only. run it against systems you own or have written permission to test. if you use this somewhere you shouldn't, that's on you.

## `licence`

Eclipse Public License v2.0 — see `LICENSE`.

> Research by `Vineeth Kumar` (`foxcornlab`). Found a bug or want a feature, open an `issue`.
