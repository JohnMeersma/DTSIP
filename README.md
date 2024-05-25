# Ansible Playbooks

This repository contains Ansible playbooks to configure multiple Cisco 1000v routers. Follow the steps below to set up your environment and run the playbooks.

## Prerequisites

- AWS Linux instance
- Git
- Python 3
- Ansible

## Setup Instructions

### Step 1: Clone the Repository

Clone the DTSIP repository to your local machine

```sh

git clone <https://github.com/JohnMeersma/DTSIP.git>
cd DTSIP

### Step 2: Create a Virtual Environment

Create a virtual environment to manage dependencies:

```sh

python3 -m venv venv-mdd

### Step 3: Activate the Virtual Environment

Activate the virtual environment:

```sh

source ./venv-mdd/bin/activate

### Step 4: Install Required Python Packages

Install the required Python packages listed in requirements.txt:

```sh

pip install -r requirements.txt
pip install certifi

### Step 5: Install Ansible Collections

Install the necessary Ansible collections specified in requirements.yml:

```sh

ansible-galaxy collection install -r requirements.yml

### Step 6: Disable Host Key Checking

Disable host key checking to avoid SSH key verification issues:

```sh

export ANSIBLE_HOST_KEY_CHECKING=False

### Step 7: Prepare the Inventory File

Ensure your hosts inventory file includes all router configurations. Here is an example hosts file:

```sh

[cisco]
router1 ansible_host=10.1.5.12 ansible_user=admin ansible_password=admin ansible_network_os=ios
router2 ansible_host=10.1.5.13 ansible_user=admin ansible_password=admin ansible_network_os=ios
router3 ansible_host=10.1.5.14 ansible_user=admin ansible_password=admin ansible_network_os=ios
router4 ansible_host=10.1.5.15 ansible_user=admin ansible_password=admin ansible_network_os=ios
router5 ansible_host=10.1.5.16 ansible_user=admin ansible_password=admin ansible_network_os=ios
router6 ansible_host=10.1.5.17 ansible_user=admin ansible_password=admin ansible_network_os=ios
router7 ansible_host=10.1.5.18 ansible_user=admin ansible_password=admin ansible_network_os=ios
router8 ansible_host=10.1.5.19 ansible_user=admin ansible_password=admin ansible_network_os=ios

### Step 8: Run the Master Playbook

Run the master playbook (main.yml) to apply configurations to all routers:

```sh

ansible-playbook -i hosts main.yml

Directory Structure
Here is an overview of the key files and directories in this repository:

```sh

DTSIP/
├── Pods/
│   ├── pod1_vCUBE2_config.yml
│   ├── pod2_vCUBE2_config.yml
│   ├── pod3_vCUBE2_config.yml
│   ├── pod4_vCUBE2_config.yml
│   ├── pod5_vCUBE2_config.yml
│   ├── pod6_vCUBE2_config.yml
│   ├── pod7_vCUBE2_config.yml
│   └── pod8_vCUBE2_config.yml
├── hosts
├── main.yml
├── requirements.txt
└── requirements.yml

### Ensure that your Ubuntu instance has network connectivity to all the routers

- Modify the hosts file as needed to match your network configuration.
- If you encounter any issues, refer to the Ansible documentation or check the configuration files for errors.
