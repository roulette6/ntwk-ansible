# NetOps Ansible
This is the repository for NetOps Ansible playbooks. The structure will change to reflect [best practices](https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html). In the meantime, the main playbook is __playbook_backup_cfg.yml__, which backs up all network devices, commmits changes to Git, and pushes the changes to the backups folder in the [username/ansible](https://github.example.com/username/ansible) repo on the Serenova Github enterprise server.

You can run __playbook_backup_cfg.yml__ as follows:

    # default command
    ansible-playbook playbook_backup_cfg.yml --vault-id prod@vault_key

    # send STDOUT to /dev/null
    ansible-playbook -i inventory_dev.yml playbook_backup_cfg.yml --vault-id prod@vault_key 1> /dev/null

    # use dev inventory
    ansible-playbook -i inventory_dev.yml playbook_backup_cfg.yml --vault-id prod@vault_key

    # limit
    ansible-playbook playbook_backup_cfg.yml --vault-id prod@vault_key --limit="<hosts>"

    # only run specified tags or skip tags
    ansible-playbook playbook_backup_cfg.yml --vault-id prod@vault_key --tags git
    ansible-playbook playbook_backup_cfg.yml --vault-id prod@vault_key --skip-tags git

You can run _playbook_f5_backup.yml_ as follows:

    ansible-playbook playbook_f5_backup.yml --vault-id prod@vault_key --extra-vars "date=yyyy-mm-dd"

You can encrypt, decrypt, and view the encrypted group vars as follows:

    ansible-vault view --vault-id prod@vault_key group_vars/file

    ansible-vault encrypt --vault-id prod@vault_key group_vars/file

    ansible-vault decrypt --vault-id prod@vault_key group_vars/file
