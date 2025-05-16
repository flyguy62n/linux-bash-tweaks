# Linux Bash Tweaks

This repository contains a collection of `.bashrc` tweaks and customizations to enhance and personalize me Bash environment. These tweaks are designed to improve productivity, streamline workflows, and add useful functionality to my terminal.  Maybe you'll like something in them too.

## Features
- Simple activation in `.bashrc` to install and maintain
- Custom aliases for common commands
- Enhanced prompt customization
- Once-daily auto-update of `git clone`d and `pipx`-managed utilities
- WSL support for YubiKey FIDO tokens in SSH and GPG

## Usage
Add the following to the end of your `~/.bashrc` file and restart your Bash session or run `source ~/.bashrc`:

```bash
# function to retrieve the latest linux-bash-tweaks release from GitHub
function get_latest_bash_tweaks() {
    # Get the latest release from the GitHub API
    local install_path="${HOME}/tools/linux-bash-tweaks"
    local latest_release=$(curl -s https://api.github.com/repos/flyguy62n/linux-bash-tweaks/releases/latest | grep -oP '"tag_name": "\K(.*)(?=")')
    local current_version=$(cat ${install_path}/version 2>/dev/null)
    
    # Check if the latest release is not empty
    if [ -z "$latest_release" ]; then
        echo "Bash Tweaks Error: Unable to retrieve the latest release."
        return 1
    fi
    
    # Make sure the intall path exists
    if [ ! -d "$install_path" ]; then
        mkdir -p "$install_path"
        if [ $? -ne 0 ]; then
            echo "Bash Tweaks Error: Unable to create install path: $install_path"
            return 1
        fi
    fi

    if [ "$latest_release" == "$current_version" ]; then
        echo "Latest Bash Tweaks already installed: $current_version"
        return 0
    fi

    # Fetch the latest release from GitHub
    echo "Fetching latest Bash Tweaks release from GitHub..."

    local fetch_url="$(curl -s https://api.github.com/repos/flyguy62n/linux-bash-tweaks/releases/latest \
        | grep "tarball_url" \
        | awk '{ print $2 }' \
        | sed 's/,$//'       \
        | sed 's/"//g' )"
        
    # Download the latest release
    curl -s -L "$fetch_url" -o ${install_path}/latest.tar.gz
    if [ $? -ne 0 ]; then
        echo "Bash Tweaks Error: Unable to download the latest release: $fetch_url"
        return 1
    fi

    # Unzip the latest release
    tar xzvf ${install_path}/latest.tar.gz --strip-components=1 -C ${install_path}/ 1>/dev/null

    # Update the version marker file
    echo "$latest_release" > ${install_path}/version
    
    # Set the executable bit on any .sh files in the recently updated tool
    chmod -R u+x ${install_path}/*.sh 2>/dev/null

    # Print the latest release
    echo "Installed release: $latest_release"
}

# Fetch the latest release of linux-bash-tweaks
get_latest_bash_tweaks

# Check if the bashrc-additions file exists
if [ -f "${HOME}/tools/linux-bash-tweaks/bashrc-additions" ]; then
    source ${HOME}/tools/linux-bash-tweaks/bashrc-additions
else
    echo "Bash Tweaks Error: Unable to find bashrc-additions file."
    return 1
fi

cd ~
```

This will make sure that your local copy is always in sync with the current release.  If you add new files to your own local `daily_tasks.d` directory, your changes will be retained. But if you change any of the files provided in the release, it will reset when I make a new release.

## Contributions
Feel free to submit pull requests or open issues to suggest new tweaks or improvements.

## License
This project is licensed under the MIT License.