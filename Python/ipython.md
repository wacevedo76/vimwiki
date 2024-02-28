Ipython
--------------------------------------------------------------------------------
Set vim keybindings for      | within ~/.ipython/profile_default/ipython_config.py
Ipython                      |    (create the file if it does not exist)
                             |
                             | c.TerminalInteractiveShell.editing_mode = 'vi' 
                             | c.TerminalInteractiveShell.emacs_bindings_in_vi_insert_mode = False
                             |
--------------------------------------------------------------------------------
Reset the ipython session    | load_ext autoreload
at the command line          | %autoreload 2
                             |
