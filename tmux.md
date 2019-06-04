# tmux

## Commands

List sessions:

```bash
tmux ls
tmux list-sessions
```

Create new session:

```bash
tmux new -s <session name>
tmux new-session -s <session name>
```

Attach to session:

```bash
tmux attach -t <target session>
tmux attach-session -t <target session>
```

Detach current client:

```txt
CTRL+B, D
```

Give named commands:

```txt
CTRL+B, :
```

Scrolling:

```txt
CTRL+B, PgUp
CTRL+B, PgDown

# Press `Q` to quit
```

Close a window or pane:

```txt
CTRL+D

# Or `exit`
```

Close all windows and panes:

```txt
CTRL+B, :kill-session
```

## Windows

Create new window:

```txt
CTRL+B, C
```

Rename current window:

```txt
CTRL+B, ,
```

List all windows:

```txt
CTRL+B, W
```

Move to next window:

```txt
CTRL+B, N
```

Move to previous window:

```txt
CTRL+B, P
```

Move to window number `X`:

```txt
CTRL+B, [X]
```

Kill the current window:

```txt
CTRL+B, &
```

## Panes

Split vertically into panes:

```txt
CTRL+B, %
```

Move to the next (vertical) pane:

```txt
CTRL+B, →
```

Move to the previous (vertical) pane:

```txt
CTRL+B, ←
```

Split horizontally into panes:

```txt
CTRL+B, "
```

Move to the next (horizontal) pane:

```txt
CTRL+B, ↑
```

Move to the previous (horizontal) pane:

```txt
CTRL+B, ↓
```

Show pane numbers for switching:

```txt
CTRL+B, Q
```
