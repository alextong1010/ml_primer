# ML Primer

A machine learning primer repository with Docker support for both CPU and GPU environments.

## Prerequisites Installation

### 1. Install Git

#### Windows:
1. Download the installer from [Git for Windows](https://gitforwindows.org/)
2. Run the downloaded .exe file
3. Click "Next" through the installation wizard (default options are fine)
4. Open Command Prompt or PowerShell to verify installation:
   ```bash
   git --version
   ```

#### Mac:
Option 1 (if you don't have Homebrew):
1. Download the installer from [Git for Mac](https://git-scm.com/download/mac)
2. Run the downloaded .dmg file
3. Follow installation instructions

Option 2 (using Homebrew):
1. First install Homebrew (if you don't have it):
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
2. Then install Git:
   ```bash
   brew install git
   ```

#### Ubuntu/Debian:
```bash
sudo apt-get update
sudo apt-get install git
```

### 2. Install Docker

#### Windows:
1. Make sure you have Windows 10/11 Pro, Enterprise, or Education
2. Enable virtualization in BIOS (if not already enabled)
3. Download [Docker Desktop](https://www.docker.com/products/docker-desktop/)
4. Run the installer
5. Follow the installation wizard
6. Restart your computer when prompted

#### Mac:
1. Download [Docker Desktop](https://www.docker.com/products/docker-desktop/)
2. Double-click the downloaded .dmg file
3. Drag Docker to Applications folder
4. Open Docker from Applications
5. Follow any prompts for permissions

#### Ubuntu/Debian:
```bash
# Remove old versions (if any)
sudo apt-get remove docker docker-engine docker.io containerd runc

# Install Docker
sudo apt-get update
sudo apt-get install docker.io docker-compose

# Start Docker service
sudo systemctl start docker
sudo systemctl enable docker

# Add your user to docker group (to run docker without sudo)
sudo usermod -aG docker $USER
# Log out and log back in for changes to take effect
```

### 3. For GPU Support (Optional):

#### Windows:
1. Download and install [NVIDIA drivers](https://www.nvidia.com/download/index.aspx)
   - Click "Download"
   - Run the installer
   - Restart your computer
2. Install [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html)

#### Linux:
```bash
# Install NVIDIA drivers
sudo ubuntu-drivers autoinstall
sudo reboot

# Install NVIDIA Container Toolkit
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list

sudo apt-get update
sudo apt-get install -y nvidia-docker2
sudo systemctl restart docker
```

## Getting Started

1. **Open Terminal/Command Prompt**:
   - Windows: Press Win + R, type "cmd" and press Enter
   - Mac: Press Cmd + Space, type "terminal" and press Enter
   - Ubuntu: Press Ctrl + Alt + T

2. **Clone the repository**:
   ```bash
   git clone https://github.com/alextong1010/ml_primer.git
   cd ml_primer
   ```

3. **Choose your environment**:

   For CPU-only environment (recommended for beginners):
   ```bash
   docker-compose up transformer-cpu
   ```

   For GPU-enabled environment (if you have an NVIDIA GPU):
   ```bash
   docker-compose up transformer-gpu
   ```

   This will:
   - Build the Docker image (first time only, may take 5-10 minutes)
   - Start a container with all required dependencies
   - Mount the `./data` directory for persistent storage

4. **Verify Installation**:
   Once inside the container, you can verify the setup:
   ```python
   python3
   >>> import torch
   >>> print(torch.__version__)
   >>> print(torch.cuda.is_available())  # Should be True for GPU setup
   ```

5. **Work on it!**
   Open http://localhost:8888 in your browser
   Work on the notebooks
   Save your work - changes will persist in the files

## Common Issues and Solutions

1. **"docker: command not found"**:
   - Make sure Docker is installed
   - Try restarting your terminal
   - On Windows, make sure Docker Desktop is running

2. **Permission denied**:
   - On Linux, make sure you've added your user to the docker group
   - Try running the commands with `sudo`

3. **Docker fails to start**:
   - Windows: Make sure Hyper-V is enabled
   - Mac: Check if Docker Desktop is running
   - Linux: Try `sudo systemctl restart docker`

4. **Git clone fails**:
   - Check your internet connection
   - Make sure you typed the repository URL correctly

## Basic Terminal Commands

- `cd directory_name`: Change directory
- `ls` (Mac/Linux) or `dir` (Windows): List files in current directory
- `pwd`: Print working directory (show current location)
- `clear`: Clear terminal screen
- Ctrl+C: Stop current process
- Ctrl+D: Exit from Python interpreter

## Need Help?

If you encounter any issues:
1. Check the Common Issues section above
2. Google the error message
3. Reach out to Alex or Evelyn




