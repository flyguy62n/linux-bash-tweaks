# Linux Bash Tweaks

This repository contains a collection of `.bashrc` tweaks and customizations to enhance and personalize me Bash environment. These tweaks are designed to improve productivity, streamline workflows, and add useful functionality to me terminal.  Maybe you'll like something in them too.

## Features
- Custom aliases for common commands
- Enhanced prompt customization
- Environment variable optimizations
- Handy functions for everyday tasks

## Usage
1. Clone this repository:
    ```bash
    git clone https://github.com/flyhuy62n/linux-bash-tweaks.git
    ```
2. Symbolicly link the `bashrc-additions` and `.daily_tasks.d/` items to your `/home/<username>` directory
    ```bash
    cd ~
    ln -s /path/to/bash-additions
    ln -s /path/to/.daily_tasks.d
3. Add `bash-additions` to the end of your `.bashrc` file:
    ```bash
    echo -e "~/bashrc-additions\ncd ~" >> ~/.bashrc
    ```
3. Reload your shell:
    ```bash
    source ~/.bashrc
    ```

## Contributions
Feel free to submit pull requests or open issues to suggest new tweaks or improvements.

## License
This project is licensed under the MIT License.