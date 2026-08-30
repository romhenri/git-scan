# git-scan

> Github desc: Bash script that scans a directory tree and prints clean/pending status, sync state, and branch per git repo.

A one-line status table for every git repository under a folder. Instead of `cd`-ing
into each project to check `git status` and `git fetch`, point `git-scan` at a parent
directory and see at a glance which repos have uncommitted changes and which are
ahead, behind, or diverged from their upstream.

## Installation

OS X & Linux:

```sh
chmod +x git-scan
sudo mv git-scan /usr/local/bin/git-scan
```

Windows isn't supported since the script relies on Bash and the standard Unix
`find`/`git` toolchain.

## Usage example

```sh
$ git-scan ~/Dev
REPO                      STATUS         SYNC            BRANCH
---------------------------------------------------------------------------
md-track                  ✅ Clean      Synced          main
tail-app                  ⚠️  Pending Synced          main
mock-interviewer          ✅ Clean      Synced          per-request-measurement
tail-data                 ⚠️  Pending Synced          main
```

Sync state reads `Synced`, `Ahead N`, `Behind N`, `Diverged`, or `No upstream` when the
current branch has nothing configured to compare against. `git-scan` doesn't fetch, so
sync state reflects the last time each repo talked to its remote.

## Development setup

Single-file Bash script, no build step or test suite. Edit `git-scan` directly and run
it against a local directory to check your changes.
