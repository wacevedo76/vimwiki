
✦ You are absolutely correct! Your diagnosis of the problem is spot on. The core issue is the incompatibility between the version of jrnl pip is trying to install and the very new Python 3.14 on your system. Downgrading to a
  more widely supported Python version is the right approach.

  You can definitely install and manage multiple Python versions on your system. While you could use aliases, a much more powerful and standard tool for this is pyenv. It lets you install different Python versions side-by-side
  and choose which version you want to use for a specific project or command, without messing with your system's default Python installation.

  Here is a step-by-step guide on how you can use pyenv to solve this issue on your Arch Linux system:

  1. Install pyenv and Build Dependencies

  First, you need to install pyenv, the pyenv-virtualenv plugin (which makes creating virtual environments easy), and the build dependencies required to compile Python from source.

   1 sudo pacman -S --needed pyenv pyenv-virtualenv base-devel openssl zlib xz tk ncurses sqlite readline bzip2 libffi

  2. Configure Your Shell for pyenv

  You need to add a few lines to your shell's configuration file to initialize pyenv every time you open a terminal.

  For bash users (`~/.bashrc`):

   1 echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
   2 echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
   3 echo 'eval "$(pyenv init -)"' >> ~/.bashrc
   4 echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc

  For zsh users (`~/.zshrc`):

   1 echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
   2 echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
   3 echo 'eval "$(pyenv init -)"' >> ~/.zshrc
   4 echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc

  After adding these lines, restart your shell (close and reopen your terminal) for the changes to take effect.

  3. Install Python 3.13

  Now you can use pyenv to install Python 3.13. This command will download the source code and compile it, so it might take a few minutes.

   1 pyenv install 3.13.0

  4. Create a Virtual Environment with Python 3.13

  Once Python 3.13.0 is installed, you can create a dedicated virtual environment for jrnl that uses this specific version.

   1 pyenv virtualenv 3.13.0 jrnl-env

  This creates a virtual environment named jrnl-env based on Python 3.13.0.

  5. Use the New Virtual Environment

  You can activate this environment in a couple of ways. The most convenient method is to set it as the "local" Python version for your project directory.

   1 # Navigate to the directory where you want to work on jrnl
   2 mkdir ~/jrnl_project
   3 cd ~/jrnl_project
   4
   5 # Set the local python version for this directory
   6 pyenv local jrnl-env

  Now, whenever you are in the ~/jrnl_project directory, your shell will automatically use the jrnl-env virtual environment (with Python 3.13.0). You'll see the environment name in your shell prompt.

  6. Install jrnl

  With the jrnl-env active, you can now install jrnl. pip will be using Python 3.13 and will fetch the latest, compatible version of jrnl.

   1 pip install jrnl

  This should now work without the build errors.

  Regarding Your Alias Question

  You asked about aliases. pyenv handles this in a more robust way using something called "shims". When you configured your shell, pyenv inserted a shims directory at the front of your PATH. This directory contains scripts for
  commands like python and pip. When you run python, you are actually running a pyenv shim, which then looks at your current configuration (global, local, or shell) and executes the correct version of Python. This is more
  flexible than aliases because it's automatic and context-aware.

> I am using zsh and the confige file is ~/.zshrc

✦ Understood. The zsh specific commands for configuring pyenv in ~/.zshrc that I provided in the previous step are the correct ones for your setup.

> sorry about that, my tmux session is not working correctly at the moment, can you display that text again?
