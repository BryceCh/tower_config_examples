# Ansible Automation Platform Configuration as Code examples

## Requirements

Note: awxkit >18.0 requires Python >3.6
This project was tested with Python 3.8

See `requirements.txt` for a full list of python dependencies  

Required Ansible collections are under `collections/requirements.yml`

## Setup

Create a virtualenv, pull down code and install dependencies:

```
/usr/bin/python3.8 -m pip install virtualenv --user
/usr/bin/python3.8 -m virtualenv py38
source py38/bin/activate
git clone https://github.com/BryceCh/tower_config_examples
cd tower_config_examples
pip install --upgrade pip
pip install -r requirements.txt
ansible-galaxy collection install -r collections/requirements.yml -p collections/
```

## Usage

Edit `inventory.ini` to match hosts in your environment. Replace secrets under `group_vars/all/vault.yml` as required.

Export AAP credentials as environment variables:  
`export tower_username=myUser`  
`export tower_password=myPassword`

Then, to run the play:  
`ansible-playbook -i inventory.ini configure_tower.yaml --ask-vault-pass -e "ansible_python_interpeter=$(which python)"`

## Recommended reading
- [Introducing: The AWX and Ansible Tower Collections](https://www.ansible.com/blog/introducing-the-awx-collection)  
- [redhat_cop controller_configuration collection](https://galaxy.ansible.com/redhat_cop/controller_configuration)  
- [redhat-cop/aap-configuration-template](https://github.com/redhat-cop/aap_configuration_template)
