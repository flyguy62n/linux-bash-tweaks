# Linux Bash Tweaks

This repository contains a collection of `.bashrc` tweaks and customizations to enhance and personalize my Bash environment. These tweaks are designed to improve productivity, streamline workflows, and add useful functionality to my terminal.  Maybe you'll like something in them too.

## Features
- Simple activation in `.bashrc` to install and maintain
- Custom aliases for common commands
- Enhanced prompt customization
- Once-daily auto-update of `git clone`d and `pipx`-managed utilities
- WSL support for YubiKey FIDO tokens in SSH and GPG

## Usage
Run `configure-wsl` in this repo.  Once done, restart your Bash session or run `source ~/.bashrc`.

This will make sure that your local copy is always in sync with the current release.  If you add new files to your own local `.daily_tasks.d/` directory, your changes will be retained. But if you change any of the files provided in the release, it will reset when I make a new release.

## Contributions
Feel free to submit pull requests or open issues to suggest new tweaks or improvements.

## License
This project is licensed under the MIT License.