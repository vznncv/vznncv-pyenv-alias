# vznncv-pyenv-alias

vznncv-pyenv-alias is a [pyenv](https://github.com/pyenv/pyenv) plugin that allows to create an "alias name" for a specific python installation.

This command can be useful if you want to specify python environment with `pyenv local` inside multiple places
and update/switch it with a single command.

## Installation

```
git clone "https://github.com/vznncv/vznncv-pyenv-alias.git" "$(pyenv root)/plugins/pyenv-alias"
```

## Usage

1. Create alias for a specific environment:

   ```
   pyenv alias <source_name> <alias_name>
   ```

   example:

   ```bash
   $ pyenv versions
   system
   3.6.11
   3.6.11/envs/venv-3.6
   3.7.8
   3.7.8/envs/venv-3.7
   3.8.5
   3.8.5/envs/venv-3.8
   venv-3.6
   venv-3.7
   venv-3.8
   
   $ pyenv alias venv-3.6 python3-dev
   INFO: Create alias python3-dev: venv-3.6 
   INFO: Complete
   
   $ pyenv versions
   system
   3.6.11
   3.6.11/envs/venv-3.6
   3.7.8
   3.7.8/envs/venv-3.7
   3.8.5
   3.8.5/envs/venv-3.8
   venv-3.6
   venv-3.7
   venv-3.8
   python3-dev
   
   $ pyenv shell python3-dev
   
   (python3-dev) $ python --version
   Python 3.6.11
   
   (python3-dev) $ pyenv alias venv-3.8 python3-dev
   INFO: Update alias python3-dev: venv-3.6 -> venv-3.8
   INFO: Complete

   (python3-dev) $ python --version
   Python 3.8.5
   ```

   note: a created alias environment represents simple symlink, so any operations with alias 
         update/change source python installation.

2. To delete alias, use ordinary `pyenv uninstall` command:

   ```bash
   $ pyenv uninstall python3-dev
   ```