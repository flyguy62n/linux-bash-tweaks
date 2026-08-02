# Linux Bash Tweaks

This repository contains a collection of `.bashrc` tweaks and customizations to enhance and personalize my Bash environment. These tweaks are designed to improve productivity, streamline workflows, and add useful functionality to my terminal.  Maybe you'll like something in them too.

## Features
- Simple activation in `.bashrc` to install and maintain
- Custom aliases for common commands
- Enhanced prompt customization
- Once-daily auto-update of `git clone`d and `uv`-managed utilities
- WSL support for YubiKey FIDO tokens in SSH and GPG
- Place user-provided scripts in `~/.config/linux-bash-tweaks/local.d/` (or `daily_tasks.d/`) — they survive updates since they live outside the install path

## Usage
Run `configure-wsl` in this repo.  

```bash
wget https://raw.githubusercontent.com/flyguy62n/linux-bash-tweaks/main/configure-wsl
bash configure-wsl
rm configure-wsl
```

Once done, restart your Bash session or run `source ~/.bashrc`.

This will make sure that your local copy is always in sync with the current release. The install path (`~/tools/linux-bash-tweaks/`) is disposable and gets replaced wholesale by every release, so any of your own scripts belong in `~/.config/linux-bash-tweaks/` instead — see below.

### User-managed local scripts
Place user-managed, local scripts in `~/.config/linux-bash-tweaks/local.d/` and they'll run every time.
1. Create a Bash shell script in `~/.config/linux-bash-tweaks/local.d/`
2. Be sure to include the she-bang `#!/bin/bash` at the top of the file
3. Mark the file executable with `chmod u+x <filename>`

You can do the same thing with daily tasks by placing them in `~/.config/linux-bash-tweaks/daily_tasks.d/`, alongside the built-in ones shipped in the release.

## Contributions
Feel free to submit pull requests or open issues to suggest new tweaks or improvements.

## License
This project is licensed under the MIT License.