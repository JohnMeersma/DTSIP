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

```
git clone <https://github.com/JohnMeersma/DTSIP.git>
cd DTSIP
sudo apt update
sudo apt install -y python3.11 python3.11-venv
```

### Step 2: Create a Virtual Environment

Create a virtual environment to manage dependencies:
```
python3.11 -m venv venv-mdd
```

### Step 3: Activate the Virtual Environment

Activate the virtual environment:
```
source venv-mdd/bin/activate
```

### Step 4: Install Required Python Packages

Install the required Python packages listed in requirements.txt:
```
pip install --upgrade pip setuptools wheel
pip install -r requirements.txt
pip install certifi
```

### Step 5: Install Ansible Collections

Install the necessary Ansible collections specified in requirements.yml:
```
ansible-galaxy collection install -r requirements.yml
```

### Step 6: Disable Host Key Checking

Disable host key checking to avoid SSH key verification issues:
```
export ANSIBLE_HOST_KEY_CHECKING=False
```

### Step 7: Prepare the Inventory File

Ensure your hosts inventory file includes all router configurations. Here is an example hosts file:

```
[cisco]
router1 ansible_host=10.1.5.101 ansible_user=cucmadmin ansible_password=cisco ansible_network_os=ios
```

### Step 8: Run the Master Playbook

Run the master playbook (main.yml) to apply configurations to all routers:
```
ansible-playbook -i hosts config.yml
```
### Step 9: Run the Cleanup Playbook

Run the cleanup playbook (main.yml) to remove CUBE configurations to vCUBE:
```
ansible-playbook -i hosts cleanup.yml
```
### Step 10: Resynch the June1 Branch 

Run the cleanup playbook (main.yml) to remove CUBE configurations to vCUBE:
```
 git pull origin June1
```

### Ensure that your Ubuntu instance has network connectivity to all the routers

- Modify the hosts file as needed to match your network configuration.
- If you encounter any issues, refer to the Ansible documentation or check the configuration files for errors.
