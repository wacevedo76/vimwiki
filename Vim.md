--------------------------------------------------------------------------------
Learn Vim Script the Hard way
--------------------------------------------------------------------------------
== Working with vim on windows ==
-- interact with system clipboard
    set clipboard+=unnamedplus
--------------------------------------------------------------------------------
== Useful help pages ==
key-notation                 |
                             |
--------------------------------------------------------------------------------
== Various tips ==
  move to specific position  | 30|
  ga                         | find the ASCI number for the character on cursor
  g<                         | redisplay previous command output
  g#                         | repeat previous replace command
  gu< movement >             | lowercase text (based on movement)
  g<shift>u< movement >      | uppercase text (based on movement)
  g~< movement >             | Swap case
  gq                         | format long lines (according to textwidth)
  gqq                        | format the entire document
  gq(number)(movement)       |
                             |
  gu                         | uncapitalize
  gU                         | capitalize
                             |
  gf                         | while on text object, if file, go to file
  ctr-^                      | while in different file, go bact to previous file
                             |
  gv                         | re-select previously selected line(s)
                             |
  J                          | join lines (with spaces)
  gJ                         | join lines (without spaces)
                             |
  Auto increment numers      |  select the numbers (cntr-v) and press g,  cntr-a
                             |
--------------------------------------------------------------------------------
== Useful movements ==
  Normal-Mode
    Scroll buffer one line at| Normal-mode  <C-e> / <C-y>
                             |
  Insert-Mode                |
    Command prefix when in   | <C-x>
    Insert-mode              |
                             |
    Scroll buffer one line   | Insert-mode  <C-x> <C-e> / <C-x> <C-y>
    at a time (insert-mode)  |
                             |
    Complete filepath under  | Insert-mode <C-x> <C-f>
    the cursor               |
                             |
    Complete with the        | <C-x> <C-v>
    command line history     |
                             |
  Command-Line-Mode          |
    Command prefix when in   | <C-r>
    Command-Line-Mode        |
                             |
    Copy the filename under  | <C-r> <C-f>
    the buffer's cursor      |
                             |
    Copy the word under the  | <C-r> <C-w>
    buffer's cursor          |
                             |
    Copy the line under the  | <C-r> <C-l>
    buffer's cursor          |
                             |
--------------------------------------------------------------------------------
== Useful settings ==
textwidth                    | set width of line
  gq                         | reformat line based on textwidth
                             |
                             |
--------------------------------------------------------------------------------
== Commonly used Commands ==
   Resize split height       |
     Incr/decr by 1          | <c-w>+ / <c-w>-
      Incr/decr by amount    | <c-w>10+ / <c-w>10-
--------------------------------------------------------------------------------
  == Abbreviations ==
                             | {mode}abbrev {char sequence} <output>
                             | :iabbrev adn and
                             |
  Buffer-Local Abbreviations | :iabbrev <buffer> --- %mdash;
--------------------------------------------------------------------------------
== Autocommands ==
    Autocommand structure    |` :autocmd BufNewFile * :write`
                             |`          ^          ^ ^`
                             | `         |          | |`
                             |`          |          | The command to run`
                             | `         |          |`
                             |`          |          A "pattern" to filter the event`
                             | `         |`
                             |`          The "event" to watch for`
                             |
    Bind single autocmd to   |
    multiple events          | :autocmd BufWritePre,BufRead `*`.html :normal gg=G
      Autocommand triggers   |
      on both commands       |
                             |
      common idiom           | :autocmd BufNewFile,BufRead `*`.html setlocal nowrap
                             | (This will turn line wrapping off whenever you'r
                             | regardless of whether the file happens to already
                             | exist, or not
                             |
    FileType Events          | :autocmd FileType javascript nnoremap <buffer> <localleader>c I//<esc>
      (:h autocmd-events)    | :autocmd FileType javascript nnoremap <buffer> <localleader>c I#<esc>
                             |
    FileType Events          | :autocmd FileType javascript nnoremap <buffer> <localleader>c I//<esc>
  Pairing Autocommands and   | :autocmd FileType python :abbrev <buffer> iff if:<left>
  Abbreviations              | :autocmd FileType javascript :abbrev <buffer> iff if ():<left>
---------------------------------------------------------------------------------
== Grouping autocmds ==
                             | :augroup testgroup
                             | :    autocmd BuffWrite * :echom "Foo"
                             | :    autocmd BuffWrite * :echom "Bar"
                             | :augroup END
                             |
  autocommand that does not  | :augroup testgroup
  duplicate                  | :    autocmd!          <--- negates the autocommand
                             | :    autocmd BuffWrite * :echom "Cats"
    (:h autocmd-groups)      | :augroup END
--------------------------------------------------------------------------------
== Operator-Pending Mappings ==
                             | An operator is a command that waits for you to
                             | enter a movement command:
                             |
                             | Keys  Operator  Movemnt
                             | ----  --------  ------------
                             | dw    Delete    to next word
                             | ci(   Change    Inside parens
                             | yt,   Yank      until comma
                             |
  Moement mappings           |
    :onoremap                | :onoremap p i(
    (Operator non recursive  |   :normal -> dp    ---> deletes all within ()
    mapping)                 |   :normal -> cp    ---> changes all within ()
                             |
--------------------------------------------------------------------------------
== Folds keybindings ==
  zf#j                       | creates a fold from the cursor down # lines.
  zf/string                  | creates a fold from the cursor to string.
  zj                         | moves the cursor to the next fold.
  zk                         | moves the cursor to the previous fold.
  zo                         | opens a fold at the cursor.
  zO                         | opens all folds at the cursor.
  zm                         | increases the foldlevel by one.
  zM                         | closes all open folds.
  zr                         | decreases the foldlevel by one.
  zR                         | decreases the foldlevel to zero — all folds will be open.
  zd                         | deletes the fold at the cursor.
  zE                         | deletes all folds.
  [z                         | move to start of open fold.
  ]z                         | move to end of open fold.
                             |
--------------------------------------------------------------------------------
== Telescope ==
                             | Telescope.nvim
                             | Telescope.setup
                             | Telescope.builtin
                             | Telescope.layout
                             | Telescope.action
                             |
--------------------------------------------------------------------------------
