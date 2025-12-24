# Prefix Key

`Ctrl + Space` → Prefix Key **(Can be modified according to needs)**

### Using prefix key changes
1. Change the name of window
2. Start a new session

### To start a tmux session

```bash
tmux
```

### To detach from a tmux session

- Command
    
    - `Prefix + D`
- Script
```bash
tmux detach
    ```

### To attach to the recent tmux session

```bash
tmux a
```

### To create a session with custom name

```bash
tmux new -s bob
```

### To kill a session

```bash
tmux kill-session [session-name]

```

### To create a horizontal and vertical panes

- Commands
    - `Prefix + %` -> To create vertical pane
    - `Prefix + "` -> To create horizontal pane

### Moving across panes

- Commands
    - `Prefix + Arrow Key` -> To move across panes

### To close a pane

- Command
    - `Prefix + X`

### Listing tmux sessions

```bash
tmux ls
```