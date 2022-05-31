--------------------------------------------------------------------------------
= Virtual Environment =
--------------------------------------------------------------------------------
== Vitrual Environment in Python ==
--------------------------------------------------------------------------------
== virtualenvwrapper ==
  Install virtualenvwrapper  | A virtual env wrapper; Store all project dependencies
                             | in one location and activate the environment anywhere using
                             | workon <name of project>
                             |
  Installation               | On Winodws
                             |   pip install virtualenvwrapper
                             | On Linux / macOS
                             |   pip install --user virtualenvwrapper
                             |
                             | (add "source virtualenvwrapper.sh" into your .SHELLrc file (~/.zshrc | ~/.bashrc))
                             |
  Initialize new project     | mkvirtualenv --python=python3.9 <name of project>
                             |
  activate project           | workon <name of project>
                             |
--------------------------------------------------------------------------------
venv                         | python3 -m venv <new roject>
                             | venv will create a few new directories
                             |   bin/ - python scripts and new executalbes by other
                             |          packages
                             |   lib/
                             |   inclued/
                             |   New packages will be installed in:
                             |     <new project>/lib/pythonx.y/site-packages/
                             |
  Activate new environment   | source <new project>/bin/activate
                             |
  Deactivate new environment | deactivate
                             |
  requirements.txt           | virtual environments are not portable, so it is
                             | common practice to provied a requirements file
                             | which facilitates recreating the same environment
                             | within different developent environments/machines
                             | an example file would look lik this
                             |     # lines followed by hast (#) are treated as comments
                             |
                             |     # Strict version names are best for reproducibility
                             |     eventlet==0.17.4
                             |     graceflu--0.1.1
                             |
                             |     # for project that are well tested with different
                             |     # dependency version the relative version specifiers
                             |     # are acceptable too
                             |     falcon>=0.3.0,<0.5.0
                             |
                             |     # packages withoutversion should be avoided unless
                             |     # latest release is always requred/desired
                             |     pytz
                             |
  Installing enviornment     | pip install -r requirements.txt
  with pip                   |
                             |
  list packages/modules      | pip list
  installed in virtual env   |
                             |
  export packages for        | pip freeze > requirements.txt
  specific environment       |
                             |
  command to deactivate      | deactivate
  virtual environment        |
                             |
  install dependencies/      | pip3 -r requirements.txt
  requierments from          |
  requirements.txt file      |
                             |
  By convention, you create  | mkdir my_project
  your vitual env _within_   | python3 -m venv my_project/venv
  your project folder; never | source my_project/venv/bin/activate
  place your project files   |
  in your virtual env dir    |
                             |
  virtual environments should|
  not be commited to git repo|
  just the requirements.txt  |
                             |
  if you want your local     | python -m venv venv --system-site-packages
  packages available within  |
  your project               |
                             |
  list only packages locally | pip list --local
  installed in the package   |
--------------------------------------------------------------------------------
== pipenv ==
  Install pipenv             |  pip install pipenv
    (when installed it takes |
    the name of the parent   |
    directory as its virtenv |
    environment name)        |
                             |
  Start the virtual env      |  pipenv shell
                             |
                             |
                             |
                             |
                             |
                             |
                             |
