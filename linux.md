# Linux Notes

## Concepts

### Whoami & Identity
In Linux, you sometimes switch between different user accounts (like your personal account or a restricted "root" administrator account) to perform different tasks. If you ever feel lost or aren't sure which account is active, `whoami` acts as a quick "identity check" to make sure you're logged in as the right person before running commands.

### The Filesystem Tree
Unlike Windows, which has multiple drives (`C:`, `D:`, `E:`), Linux uses a single unified **tree structure**. `/` is the root node, and everything else branches from it as child nodes.

- `pwd` ("print working directory") tells you *where you are* — the parent node you're currently standing in.
- `ls` tells you *what's inside* that location — its children.

> In short: `pwd` tells you the parent, `ls` tells you the children.

You can create your own directories, but the main ones found on every Linux system include `etc`, `bin`, `usr`, `tmp`, and `dev`.

**Reading a prompt:**
```
asma-waseen@inova-lab:/ $
```
- `asma-waseen` → username
- `inova-lab` → machine/VM name
- `$` → regular user (root shows `#` instead)
- `/` → current directory

### Absolute vs. Relative Paths
```
              /
         ┌────┼────┐
        bin   tmp   etc
        │
       fo1
      ┌──┴──┐
     f1     f2
```
- **Relative path** — described from wherever you currently stand. If `pwd` is `fo1` and you want `f2`, just run `cd f2`.
- **Absolute path** — always starts at `/`, describing the full route from root regardless of where you currently are. From `etc`, reaching `f2` means: `cd /bin/fo1/f2`.

> ⚠️ Common mistake: an absolute path **must** start with `/`. Writing `bin/fo1/f2` without the leading slash makes it a relative path, not absolute — it only works by coincidence if you happen to be sitting right above `bin`.

### Users in Linux
- **Regular users** — full control over their *own* home directory only (view/modify/delete). Can't access another user's home directory without permission.
- **Root / superuser** — full access to the entire system, including every user's home directory. Regular users borrow root's power temporarily using `sudo` when they need to perform an admin-level task.

---

## Cheat Sheet

| Command | What it does |
|---|---|
| `whoami` | who am I logged in as? |
| `pwd` | where am I? |
| `ls` | what's here? |
| `cd <dir>` | go into `<dir>` |
| `cd ..` | go up one level |
| `mkdir <name>` | make a directory |
| `touch <file>` | make an empty file |
| `mv <a> <b>` | move/rename |
| `cp <a> <b>` | copy |
| `rm <file>` | delete a file |
| `rmdir <dir>` | delete an empty directory |
| `rm -r <dir>` | delete a directory + contents |
| `rm -f <file>` | force delete, no prompt |
| `clear` / `Ctrl+L` | clear screen |
| `history` | show past commands |

---

## Notes / Gotchas

- `touch` doesn't just create files — if the file already exists, it just updates its timestamp without touching the content.
- `rmdir` only works on **empty** directories. Use `rm -r` if there's anything inside.
- Absolute paths always start with `/` — a path without the leading slash is relative, even if it looks "complete."
- `clear` only wipes the visible screen — your command history is still intact and accessible via `history`.
