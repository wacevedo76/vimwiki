--------------------------------------------------------------------------------
= General Tmux notes =
--------------------------------------------------------------------------------
  Change working directory   | attach-session -t . -c /path/to/new/directory
                             |
--------------------------------------------------------------------------------
Copy and Past
  set for vi control keys    | <C-b>:
                             | set-window-option -g mode-keys vi
                             |
Start new session            | tmux new-session -d -s <session name>
                             |   -d   |  detached mode
                             |   -s   |  session name
                             |
Create a new window          | tmux new-window -t <session name>:1 -n "<window name>"
                             |   (notice the <session name>:1  <--
                             |
Attach session               | tmux attach -t <session name>
                             |
Select window                | tmux select-window -t <session name>:1
                             |
split window                 | tmux split-window -h
                             |
Send commands to tmux        | tmux send-keys 'command ; another command' C-m
                             |   (notice C-m -> sent enter keystroke)
                             |
Attach to session            | tmux attach -t <session name>
                             |
synconize commands on all    | :set synchronize-panes (off)
panes                        |
                             |
