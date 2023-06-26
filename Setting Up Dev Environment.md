Monday, 26 June 2023

**Setting Up your Development Environment**

**Requirements:**

-   Golang

-   GoLand (IDE)

-   Git

-   SSH (for a secure connection with GitHub) 

**How to ?**

-   Install Golang:

    -   Download the Golang binary distribution suitable for your
        > operating system from the official Golang website
        > (<https://golang.org/dl/>).

        > Run the installer and follow the instructions for your
        > specific operating system.

        > Make sure to set the appropriate environment variables, such
        > as GOROOT and GOPATH, as per the installation instructions.

To set the appropriate environment variables (GOROOT and GOPATH) on
macOS, you can follow these steps:

-   Open Terminal: Launch the Terminal application on your macOS. You
    > can find it by navigating to \"Applications\" -\> \"Utilities\"
    > -\> \"Terminal\".

    > Locate your bash profile: In the Terminal window, enter the
    > following command:

```bash
nano ~/.bashrc
```
OR 
```bash
nano ~/.zshrc
```
(If you are using zsh)

This command will open the bash profile file in the nano text editor.

-   Set the GOROOT variable: Add the following line to the bash profile
    > file, specifying the location where you installed Golang:

```bash
export GOROOT=/usr/local/go
```

Make sure to replace **/usr/local/go** with the actual path where Golang
is installed if it\'s different on your system.

-   Set the GOPATH variable: Below the line for GOROOT, add the
    > following line to set the GOPATH variable:

```bash
export GOPATH=$HOME/go
```

By default, the GOPATH is set to \$HOME**/go**, but you can specify a
different directory if desired.

-   Save and exit the file: Press `Ctrl + X` (on macOS `**\^+x**`) to exit
    > nano, and it will prompt you to save the changes. Press `Y` to
    > confirm the changes and then press Enter to save the file with the
    > same name.

    > Load the updated shell profile: In the Terminal, run the following
    > command to reload the bash profile and apply the changes:

```bash
source ~/.bashrc
```
 **OR** **source ~/.zshrc**

Now, the GOROOT and GOPATH environment variables should be set correctly
on your macOS. You can verify this by running the following command in
the Terminal:

```bash
go env
```

It should display the values of GOROOT and GOPATH among other Go-related
environment variables.

-   Install Git:

    -   -   Open Terminal: Launch the Terminal application on your
            > macOS. You can find it by navigating to \"Applications\"
            > -\> \"Utilities\" -\> \"Terminal\".

            > Check if Git is already installed: In the Terminal, run
            > the following command to check if Git is already installed
            > on your system:

```bash
git --version
```

If Git is installed, it will display the version number.

If not, you will see an error message indicating that the command was
not found.

-   Install Git using Homebrew (recommended): Homebrew is a popular
    > package manager for macOS. If you don\'t have Homebrew installed,
    > you can install it by following the instructions at
    > <https://brew.sh/>.

    > Once Homebrew is installed, run the following command in the
    > Terminal to install Git:

```bash
brew install git
```

This command will download and install the latest version of Git.

-   Verify the Git installation: After the installation is complete, run
    > the following command to verify that Git is installed properly:

```bash
git --version
```

You should see the Git version number displayed in the Terminal.

-   Install GoLand:

    -   Download the installer for GoLand from the JetBrains website
        > (<https://www.jetbrains.com/go/>).

        > Run the installer and follow the installation wizard
        > instructions.

        > Once installed, launch GoLand.

        > **Pro-tip:** Login JetBrains with your Student ID to get 1
        > Year Subscription to IDEs for free.

    > Generate SSH key for GitHub:

    -   Open a terminal or command prompt on your local machine.

        > Run the following command to generate an SSH key:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com\"
```

```{=html}
-   -   You can replace the email address with your own email associated
        > with GitHub.

        > You\'ll be prompted to enter a file location to save the key.
        > Press Enter to save it in the default location.

        > You\'ll also be prompted to enter a passphrase for the key.
        > It\'s recommended to use a strong passphrase.

        > Two files will be generated: id_ed25519 (private key) and
        > id_ed25519.pub (public key).

```
-   -   Add SSH key to SSH agent:

        > Start the SSH agent by running the following command:

        ```bash
        eval "$(ssh-agent -s)"
        ```

Add your SSH private key to the SSH agent by running the command:

```bash
ssh-add -K ~/.ssh/id_ed25519
```

Copy the public key to clipboard

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

-   Add SSH key to GitHub:

    -   Log in to your GitHub account.

        > Go to \"Settings\" by clicking on your profile picture in the
        > top-right corner and selecting \"Settings\" from the dropdown
        > menu.

        > In the left sidebar, click on \"SSH and GPG keys\".

        > Click on \"New SSH key\".

        > Give your SSH key a title (e.g., \"My SSH Key").

        > Paste the key you copied in the clipboard into the \"Key\"
        > field on the GitHub website.

        > OR if key is not present in the clipboard, launch the terminal
        > and run command:

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

-   -   Paste the key into the \"Key\" field on the GitHub website.

        > Click \"Add SSH key\" to save it.

    > Test SSH connection:

    -   Open a terminal or command prompt on your local machine.

        -   Run the following command to test the SSH connection with
            > GitHub:

            ```bash
            > ssh -T git@github.com
            ```

            > If the connection is successful, you\'ll see a message
            > like \"Hi username! You\'ve successfully authenticated,
            > but GitHub does not provide shell access.\".

    > Configure GoLand with GitHub:

    -   In GoLand, go to \"File\" -\> \"Settings\" -\> \"Version
        > Control\" -\> \"GitHub\" on the menu bar.

        > Click on the \"+\" button to add a new GitHub account.

        > Choose \"Log in with Token\" and follow the prompts to
        > generate a GitHub personal access token.

        > Once you have the token, enter it in the provided field.

        > Click \"Test\" to verify the connection with GitHub.

Now you can use SSH for secure communication with GitHub repositories.
When cloning or accessing a GitHub repository, use the SSH URL, which
starts with git@github.com: instead of https://github.com/.

For example, to clone a repository using SSH, you can run:

git clone git@github.com:user/repo.git

Make sure to replace user with your GitHub username and repo with the
repository name.

> Clone the repository from Omniful's Github using SSH:
>
> First Create a directory structure where you clone everything from
> Omniful:

go =\> src =\> [github.com](http://github.com/) =\> Omniful

> Open Terminal and Run Below Commands:
>
```bash
> cd go/src/github.com/Omniful
```
>
> Let's say we are cloning sales-channel-service repository

```bash
git clone git@github.com:omniful/sales-channel-service.git
```

Open the sales-channel-service project folder in GoLand

Open Integrated terminal and run:

```bash
go mod tidy
```

to sync all dependencies of project.

If you encountered an error while installing private Go modules
(go_commons) from the GitHub repository github.com/omniful. Do the
Configuration mentioned in below Note.

> Note :

Set the GOPRIVATE environment variable to include github.com/omniful/.

This step ensures that Go treats the repository as private and allows
access to it. Run the following command in terminal after above
configurations:

```bash
go env -w GOPRIVATE="github.com/omniful/"
```

Configure your Git settings by creating or modifying
the \~/.gitconfig file.

Open the file and add the following configuration, replacing {name} with
your Git username and {email} with your Git email:
```text

[user]

    name = {name}
    
    email = {email}

[url "ssh://git@github.com/"]

    insteadOf = https://github.com/

```

This configuration tells Git to use SSH for GitHub URLs instead of
HTTPS, which is required for accessing private repositories. Save the
changes to \~/.gitconfig.
