# Test Ansible role repo
ansible-playbook -i invetory.yml pg_promise/deploy.yml -e @secrets.yml --ask-vault-pass
