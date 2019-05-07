# instructions to collect ad-hoc output

# run linux host with ansible installed
# example here will run as 'root' user and collect output on 'leaf01'
# output will be stored locally in /var/cumulus-collected/leaf01 directory
cumulus@oob-mgmt-server:~/triage$ ansible-playbook -u root collect.evpn.yml --extra-vars "node=leaf01"
