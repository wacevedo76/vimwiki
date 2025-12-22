# Learn Vim Script the Hard way
## Quick Notes:  

### Yank a character into a register

#### ✅ 1. Identify the Character Under the Cursor
Use the `getchar()` and `getline()` + `col()` Vim functions (for scripting), but in normal usage, you can yank the character under the cursor using:

```vim
"cy
```

#### Explanation:
* `"c` — Specifies register c (you can pick any letter a–z).
* `y` — Yank...
* `l` — One character to the right of the cursor (default for `y` in normal mode without motion is one char).

So:

```vim
"cyl
```
If you want **only the character under the cursor** (not including the one to the right), you could use:

```vim
"cyv"ly
```
But `yl` is usually good enough for one character.

#### ✅ 2. Yank the Character Under Cursor Into a Register
Use:

```vim
"cyl
```
This yanks the **character under the cursor** into register `c`.

You can confirm it’s there with:

```vim
:reg c
```

#### ✅ 3. Use a Register in a Regex Pattern
In command-line mode (`:`), you can insert the contents of a register using `<C-r>{register}`.

For example, to insert the contents of register `c`:

```vim
<C-r>c
```
**Example Use Case**:
Let’s say you want to **replace all occurrences** of the character under the cursor with `X`.

1. Yank the character under the cursor into register `c`:

```vim
"cyl
```

2. Run the substitute command:

```vim
:%s/<C-r>c/X/g
```
* `%s/` – substitute in whole file
* `<C-r>c` – insert the character you yanked
* `/X/` – replace with "X"
* `/g` – globally on each line

This dynamically inserts the yanked character into the search pattern.

🚀 Summary Cheatsheet
| Task                                        | Vim Command        |
| ------------------------------------------- | ------------------ |
| Yank character under cursor to register `c` | `"cyl`             |
| Insert register in command line             | `<C-r>c`           |
| Substitute using char from register         | `:%s/<C-r>c/NEW/g` |

### Folds
| Command | Action                           |
| :-----: | ------                           |
| zR      | Open all folds                   |
| zM      | Close all folds                  |
| zo      | Open one fold under the cursor   |
| zc      | Close one fold under the cursor  |
| za      | Toggle fold under the cursor     |
| zO      | Open all folds under the cursor  |
| zC      | Close all folds under the cursor |

Start vim without default config
vim -u NONE

Remove blank lines from a file:
`:g/^$/d`
Working with vim on windows
- interact with system clipboard  
`set clipboard+=unnamedplus`

## Useful help pages 
* key-notation 

## Neovim Testing
| Purpose                          | Setting                              |
| -------                          | -------                              |
| Test alternate configuraion file | `nvim -u /path/to/custom/config.lua` |
| Test alertate configuration set  | `nvim -u /path/to/custom/init.lua`   |
| Disable all configurations       | `nvim -u NONE`                       |

## Various tips
| result                                            | keybinding or intention     |
|---------------------------------------------------|-----------------------------|
| Move to a specific location horizontally          | (desired position (int)) \| |
| Find the ASCI for the character on cursor         | ga                          |
| Find the ASCI number for the character on cursor  | ga                          |
| Redisplay previous command output                 | g<                          |
| Repeat previous replace command                   | g#                          |
| Lowercase text (based on movement)                | gu< movement >              |
| Uppercase text (based on movement)                | g<shift>u< movement >       |
| Swap case                                         | g~< movement >              |
| Format long lines (according to textwidth)        | gq                          |
| Format the entire document                        | gqq                         |
| Uncapitalize                                      | gu                          |
| Capitalize                                        | gU                          |
| While on text object, if file, go to file         | gf                          |
| While in different file, go bact to previous file | ctr-^                       |
| Re-select previously selected line(s)             | gv                          |
| Join lines (with spaces)                          | J                           |
| Join lines (without spaces)                       | gJ                          |
| Select the numbers (cntr-v) and press g,  cntr-a  | Auto increment numers       |

## Useful movements
| Mode    | Explaination                                 | Keybinding                |
|---------|----------------------------------------------|---------------------------|
| Normal  | Scroll buffer one line at a time             | `<C-e> / <C-y>`           |
| Insert  | Command prefix                               | `<C-x>`                   |
| Insert  | Scroll buffer one line at a time             | `<C-x><C-e> / <C-x><C-y>` |
| Insert  | Complete filepath under cursor               | `<C-x> <C-f>`             |
| Command | Command prefix                               | `<C-r>`                   |
| Command | Copy the filename under the buffers's cursor | `<C-r><C-f>`              |
| Command | Copy the word under the buffer's cursor      | `<C-r><C-w>               |
| Command | Copy the line under the buffer's cursor      | `<C-r><C-l>`              |

## Useful settings
| Setting   | Explanation                      |
|-----------|----------------------------------|
| textwidth | set width of line                |
| gq        | reformat line based on textwidth |

## Commonly used Commands
| Result                                    | Keybinding            |
|-------------------------------------------|-----------------------|
| Resize split height (incr / decr by 1)    | `<c-w>+ / <c-w>-`     |
| Resize split height (incr/decr by amount) | `<c-w>10+ / <c-w>10-` |

## Abbreviations
```
                             | {mode}abbrev {char sequence} <output>
                             | :iabbrev adn and
                             |
  Buffer-Local Abbreviations | :iabbrev <buffer> --- %mdash;
```

## Autocommands 
```
    Autocommand structure    | :autocmd BufNewFile * :write
                             |          ^          ^ ^
                             |          |          | |
                             |          |          | The command to run
                             |          |          |
                             |          |          A "pattern" to filter the event
                             |          |
                             |          The "event" to watch for
                             |
    Bind single autocmd to   |
    multiple events          | :autocmd BufWritePre,BufRead *.html :normal gg=G
      Autocommand triggers   |
      on both commands       |
                             |
      common idiom           | :autocmd BufNewFile,BufRead *.html setlocal nowrap
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
```

## Grouping autocmds 
```
                             | :augroup testgroup
                             | :    autocmd BuffWrite * :echom "Foo"
                             | :    autocmd BuffWrite * :echom "Bar"
                             | :augroup END
                             |
  autocommand that does not  | :augroup testgroup
  duplicate                  | :    autocmd!          <--- negates the autocommand
                             | :    autocmd BuffWrite * :echom "Cats"
    (:h autocmd-groups)      | :augroup END
```

## Operator-Pending Mappings 
```
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
```

## Folds keybindings 
```
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
```

## Telescope 
```
                             | Telescope.nvim
                             | Telescope.setup
                             | Telescope.builtin
                             | Telescope.layout
                             | Telescope.action
                             |
```
