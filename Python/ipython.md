# Ipython

### Set vim keybindings for Ipython  
Within `~/.ipython/profile_default/ipython_config.py`  
(create the file if it does not exist)

Add these two lines  
```
c.TerminalInteractiveShell.editing_mode = 'vi' 
c.TerminalInteractiveShell.emacs_bindings_in_vi_insert_mode = False
```

### List all Magic Functions  
`%lsmagic`

### List of all available Magic Functions

* Available line magics:  
```
| %alias           | %alias_magic   | %autoawait  | %autocall   | %autoindent   |
| %automagic       | %bookmark      | %cat        | %cd         | %clear        |
| %code_wrap       | %colors        | %conda      | %config     | %cp           |
| %cpaste          | %debug         | %dhist      | %dirs       | %doctest_mode |
| %ed              | %edit          | %env        | %gui        | %hist         |
| %history         | %killbgscripts | %ldir       | %less       | %lf           |
| %lk              | %ll            | %load       | %load_ext   | %loadpy       |
| %logoff          | %logon         | %logstart   | %logstate   | %logstop      |
| %ls              | %lsmagic       | %lx         | %macro      | %magic        |
| %mamba           | %man           | %matplotlib | %micromamba | %mkdir        |
| %more            | %mv            | %notebook   | %page       | %paste        |
| %pastebin        | %pdb           | %pdef       | %pdoc       | %pfile        |
| %pinfo           | %pinfo2        | %pip        | %popd       | %pprint       |
| %precision       | %prun          | %psearch    | %psource    | %pushd        |
| %pwd             | %pycat         | %pylab      | %quickref   | %recall       |
| %rehashx         | %reload_ext    | %rep        | %rerun      | %reset        |
| %reset_selective | %rm            | %rmdir      | %run        | %save         |
| %sc              | %set_env       | %store      | %sx         | %system       |
| %tb              | %time          | %timeit     | %unalias    | %unload_ext   |
| %who             | %who_ls        | %whos       | %xdel       | %xmode        |
```
* Available cell magics:  
```
| %%!         | %%HTML   | %%SVG       | %%bash    | %%capture    |
| %%code_wrap | %%debug  | %%file      | %%html    | %%javascript |
| %%js        | %%latex  | %%markdown  | %%perl    | %%prun       |
| %%pypy      | %%python | %%python2   | %%python3 | %%ruby       |
| %%script    | %%sh     | %%svg       | %%sx      | %%system     |
| %%time      | %%timeit | %%writefile |           |              |
```

### Documentation for Magic functions  
To view the documentation (Docstring) for a Magic function, enter the magic  
function and add a `'?'` as the last character

### Reset the ipython session 
`%reset`
