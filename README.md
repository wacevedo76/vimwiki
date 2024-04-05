
```
`__        ___ _ _ _                      __     ___                   _ _    _`
`\ \      / (_) | (_) __ _ _ __ __   ___  \ \   / (_)_ __ _____      _(_) | _(_)`
` \ \ /\ / /| | | | |/ _\ | '_ '_ \ / __|  \ \ / /| | '_ '_  \ \ /\ / / | |/ / |`
`  \ V  V / | | | | | (_| | | | | | \__ \   \ V / | | | | | | \ V  V /| |   <| |`
`   \_/\_/  |_|_|_|_|\__,_|_| |_| |_|___/    \_/  |_|_| |_| |_|\_/\_/ |_|_|\_\_|`
```

Welcome to my personal wiki. a collection of notes on various subject subjects within I.T.

While the notes are written in markdown, the links do not work correctly while  
being viewed within a web browser. I recommend using the [vimwiki](https://github.com/vimwiki/vimwiki) plugin for vim.

I haven't checked whether they've supplied correct configuration for [lazy.nvim](https://github.com/folke/lazy.nvim), but here is  
my setup config:
```
return {
  "vimwiki/vimwiki",
  branch = "dev",
  lazy = false,
  init = function()
    vim.g.vimwiki_global_ext = 0
    vim.g.vimwiki_list = {
      {
        path = "~/code/wacevedo76/vimwiki/",  -- Specifies the directory target wiki is located
        syntax = "markdown",                  -- Specifies markdown, vimwiki, or mediawiki
        ext = ".md",                          -- Specifies file extension
      },
    }
  end,
}
```
Hope this is helpful :smile:

