# WSL CUDA Setup Guide

Welcome to the **WSL CUDA Setup Guide**! This repository provides a step-by-step guide on setting up CUDA cores on the Windows Subsystem for Linux (WSL) to enable GPU-accelerated development and machine learning.

## Table of Contents
1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Step-by-Step Setup](#step-by-step-setup)
4. [Testing CUDA Installation](#testing-cuda-installation)
5. [Troubleshooting](#troubleshooting)
6. [Additional Resources](#additional-resources)

## Introduction
Setting up CUDA in WSL allows you to leverage NVIDIA GPUs for accelerated computation within Linux-based environments on Windows. This guide walks you through the necessary steps for installing CUDA, configuring the environment, and verifying the installation.

## Prerequisites
- **Windows 10/11** with WSL 2 enabled
- **NVIDIA GPU** (RTX series or any CUDA-capable GPU)
- **NVIDIA driver** compatible with WSL
- **WSL 2 kernel update** (Windows Build 19041 or higher)
- **Ubuntu (or any WSL-supported Linux distribution)**

## Step-by-Step Setup
Here’s an updated guide with additional commands for listing available distributions and installing a specific Linux distribution:

---

## 1. Windows Setup

### Enable WSL and Virtual Machine Platform
   - Open **PowerShell as Administrator** and run the following command to install WSL, set WSL2 as the default, and install Ubuntu as the default Linux distribution:
     ```powershell
     wsl --install
     ```

### Set WSL2 as Default Version
   - If WSL was previously installed, you may need to set WSL2 as the default:
     ```powershell
     wsl --set-default-version 2
     ```

### List Available Distributions
   - To see a list of Linux distributions available for installation, use:
     ```powershell
     wsl --list --online
     ```

### Install a Specific Linux Distribution
   - To install a specific distribution, use the following command, replacing `<Distribution Name>` with the desired distribution (e.g., `Ubuntu`):
     ```powershell
     wsl --install -d <Distribution Name>
     ```

### Check WSL Version
   - Verify that WSL2 is enabled by running:
     ```powershell
     wsl -l -v
     ```

## 2. Opening WSL Distro

- Launch **Ubuntu** (or your chosen Linux distribution) from the Start Menu. This will complete the initial setup.

## 3. WSL Setup

### Download and Install the NVIDIA Driver for WSL

1. **Download the NVIDIA Driver (Linux `.deb` Package)**
   - Visit the [NVIDIA WSL Drivers Page](https://developer.nvidia.com/cuda/wsl) and download the appropriate `.deb` package for your NVIDIA GPU.

2. **Install the Driver in WSL**
   - Open **Ubuntu** (or your WSL Linux distro) and navigate to the directory where the `.deb` file is saved.
   - Run the following commands to install the driver:
     ```bash
     sudo dpkg -i <driver-package-name>.deb
     sudo apt-get install -f
     ```

   - **Example**:
     ```bash
     sudo dpkg -i cuda-wsl-<version>.deb
     sudo apt-get install -f
     ```

### Verify Driver Installation
   - To ensure the NVIDIA driver is correctly installed, check your GPU’s status by running:
     ```bash
     nvidia-smi
     ```

---

Following these steps will enable WSL2 with CUDA support, allowing you to leverage GPU-accelerated processing on Linux within Windows. Let me know if you need further clarification on any step!

3. **Install CUDA Toolkit**
   - Open WSL and update your package lists:
     ```bash
     sudo apt update && sudo apt upgrade
     ```
   - Install CUDA:
     ```bash
     sudo apt install nvidia-cuda-toolkit
     ```

4. **Verify CUDA Installation**
   - After installation, check for GPU compatibility:
     ```bash
     nvidia-smi
     ```
   - Verify CUDA version:
     ```bash
     nvcc --version
     ```

## Testing CUDA Installation
To confirm that your CUDA setup is successful:
- Create a simple CUDA test program, or use `nvidia-smi` to check GPU status.

## Troubleshooting
- **Driver Issues**: Ensure your NVIDIA driver is up to date.
- **WSL Version**: Ensure you are using WSL 2.

## Additional Resources
- [NVIDIA's Guide to CUDA in WSL](https://developer.nvidia.com/cuda/wsl)
- [Microsoft WSL Documentation](https://docs.microsoft.com/en-us/windows/wsl/)

---

This README provides users with clear instructions and key terms for setting up CUDA in WSL. Let me know if you’d like more details on any step!