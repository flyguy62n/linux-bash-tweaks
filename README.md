# Linux Bash Tweaks

This repository contains a collection of `.bashrc` tweaks and customizations to enhance and personalize me Bash environment. These tweaks are designed to improve productivity, streamline workflows, and add useful functionality to my terminal.  Maybe you'll like something in them too.

## Features
- Simple activation in `.bashrc` to install and maintain
- Custom aliases for common commands
- Enhanced prompt customization
- Once-daily auto-update of `git clone`d and `pipx`-managed utilities
- WSL support for YubiKey FIDO tokens in SSH and GPG

## Usage
Add the following to the end of your `~/.bashrc` file:

```bash
# Bootstrap the linux-bash-tweaks repo
if [ ! -d ${HOME}/tools/linux-bash-tweaks ]; then
    echo "Cloning linux-bash-tweaks"
    mkdir -p ${HOME}/tools && cd ${HOME}/tools
    git clone https://github.com/flyguy62n/linux-bash-tweaks
else
    echo "Updating linux-bash-tweaks"
    cd ${HOME}/tools/linux-bash-tweaks
    git fetch && git reset --hard HEAD && git merge
    # Make sure the executable bit is set on files in the recently updated directory
    chmod u+x bashrc-additions configure-yubikey 2>/dev/null    
fi

source ${HOME}/tools/linux-bash-tweaks/bashrc-additions
cd ~
```

This will make sure that your local copy is always in sync with mine.  That is, if you make any changes locally, the `git fetch && git reset ...` line will throw those changes away the next time you start a new shell session.

If you'd rather add your own content -- maybe add a few of your own 3rd party tools to `.daily_tasks.d/01-update-git-repos` or whatver -- make a fork of my repo, change the `git clone` line above, and have fun with it.

## Contributions
Feel free to submit pull requests or open issues to suggest new tweaks or improvements.

## License
This project is licensed under the MIT License.