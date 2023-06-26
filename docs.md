Setting Up your Development Environment
Requirements:
Golang
GoLand (IDE)
Git
SSH (for a secure connection with GitHub) 
Installation Steps:
Install Golang:

Download the Golang binary distribution suitable for your operating system from the official Golang website (https://golang.org/dl/).
Run the installer and follow the instructions for your specific operating system.
Set the appropriate environment variables, such as GOROOT and GOPATH, as per the installation instructions.
Install Git:

Check if Git is already installed on your system by running the command git --version in the terminal.
If Git is not installed, you can install it using Homebrew (recommended for macOS) by following the instructions at https://brew.sh/.
After installing Homebrew, run the command brew install git in the terminal to install Git.
Verify the Git installation by running the command git --version in the terminal.
Install GoLand:

Download the installer for GoLand from the JetBrains website (https://www.jetbrains.com/go/).
Run the installer and follow the installation wizard instructions.
Once installed, launch GoLand.
Generate SSH key for GitHub:

Open a terminal or command prompt on your local machine.
Run the following command to generate an SSH key: ssh-keygen -t ed25519 -C "your_email@example.com". Replace the email address with your own email associated with GitHub.
You'll be prompted to enter a file location to save the key. Press Enter to save it in the default location.
You'll also be prompted to enter a passphrase for the key. It's recommended to use a strong passphrase.
Two files will be generated: id_ed25519 (private key) and id_ed25519.pub (public key).
Add SSH key to SSH agent:

Start the SSH agent by running the command eval "$(ssh-agent -s)" in the terminal.
Add your SSH private key to the SSH agent by running the command ssh-add -K ~/.ssh/id_ed25519 in the terminal.
Add SSH key to GitHub:

Log in to your GitHub account.
Go to "Settings" by clicking on your profile picture in the top-right corner and selecting "Settings" from the dropdown menu.
In the left sidebar, click on "SSH and GPG keys".
Click on "New SSH key".
Give your SSH key a title (e.g., "My SSH Key").
Paste the public key (id_ed25519.pub) into the "Key" field on the GitHub website.
Click "Add SSH key" to save it.
Test SSH connection:

Open a terminal or command prompt on your local machine.
Run the command ssh -T git@github.com to test the SSH connection with GitHub.
If the connection is successful, you'll see a message like "Hi username! You've successfully authenticated, but GitHub does not provide shell access.".
Configure GoLand with GitHub:

In GoLand, go to "File" -> "Settings" -> "Version Control" -> "GitHub" on the menu bar.
Click on the "+" button to add a new GitHub account.
Choose "Log in with Token" and follow the prompts to generate a GitHub personal access token.
Once you have the token, enter it in the provided field.
Click "Test" to verify the connection with GitHub.
Clone the repository from Omniful’s Github using SSH:

Create a directory structure where you clone everything from Omniful: go/src/github.com/Omniful.
Open the terminal and navigate to the go/src/github.com/Omniful directory.
Run the command git clone git@github.com:omniful/sales-channel-service.git to clone the repository.
Open the sales-channel-service project folder in GoLand.
Open the integrated terminal in GoLand and run go mod tidy to sync all dependencies of the project.
Configure Git settings:

Create or modify the ~/.gitconfig file.
Add the following configuration, replacing {name} with your Git username and {email} with your Git email:
[user]
    name = {name}
    email = {email}
[url "ssh://git@github.com/"]
    insteadOf = https://github.com/
Save the changes to ~/.gitconfig.
Now you have successfully set up your development environment with Golang, GoLand, Git, and SSH for a secure connection with GitHub.
