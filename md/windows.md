### Prerequisites

Before proceeding with the installation, ensure that you have the following prerequisites:

- Docker: Make sure you have Docker installed on your system. You can download Docker from the [official website](https://www.docker.com/products/docker-desktop) and follow the installation instructions for Windows.

### Step 1: Install Docker

1. Download Docker for Windows from the [official website](https://www.docker.com/products/docker-desktop).
2. Follow the installation instructions to install Docker on your system.
3. Once Docker is successfully installed, make sure it is running by opening the Docker application.

### Step 2: Install Git Bash

1. Download Git for Windows from the [official website](https://gitforwindows.org/).
2. Run the downloaded installer and follow the installation instructions.
3. During the installation, select the option to install Git Bash.
4. Once the installation is complete, open Git Bash from the Start Menu.

### Step 3: Download the Installation Script

In the Git Bash terminal, run the following command to download the installation script:

```
curl -O https://raw.githubusercontent.com/proxusiiotplatform/docs/main/install_proxus.sh
```

This will download the installation script and save it as `install_proxus.sh` in your current working directory.

### Step 4: Grant Execution Permissions

In the Git Bash terminal, navigate to the directory where the `install_proxus.sh` file is located. Run the following command to grant execution permissions to the script:

bashCopy code

`chmod +x install_proxus.sh`

### Step 5: Run the Installation Script

Run the following command in the Git Bash terminal to execute the Proxus installation script:

bashCopy code

`./install_proxus.sh`

### Step 6: Follow the Installation Prompts

The installation script will guide you through the installation process by presenting various prompts. Follow the instructions and provide the necessary information when prompted, such as passwords for database and environment settings.

### Step 7: Complete the Installation

Once the installation script completes its execution, Proxus should be installed and ready to use on your Windows system.

### Accessing Proxus

After the installation is complete, you can access Proxus by opening a web browser and navigating to `http://localhost:8080`. This will take you to the Proxus web interface, where you can log in and start using the platform.

### Important Notes

- The installation script automatically configures Proxus with default settings. If you wish to customize the configuration further, you can manually modify the generated `docker-compose.yml` file.
- Make sure to securely store the passwords generated during the installation process. The installation script saves the passwords to a file named `passwords.txt` located in the installation directory.

That's it! You have successfully installed Proxus on your Windows system using Docker and Git Bash. Enjoy using the powerful features of Proxus for your industrial IoT needs.
