# instructions to collect ad-hoc output

- run linux host with ansible installed
- example here will run as 'root' user and collect output on 'leaf01'
- output will be stored locally in /var/cumulus-collected/leaf01 directory
```
cumulus@oob-mgmt-server:~/triage$ ansible-playbook -u root collect.evpn.yml --extra-vars "node=leaf01"
```
```
cumulus@oob-mgmt-server:~/triage$ ls -lrt /var/cumulus-collected/leaf01/
total 52
-rwxrwxrwx 1 root root  4844 May  7 09:38 bridge_result.stdout
-rwxrwxrwx 1 root root  2858 May  7 09:38 arp_result.stdout
-rwxrwxrwx 1 root root  2014 May  7 09:38 evpn_mac_result.stdout
-rwxrwxrwx 1 root root 17408 May  7 09:38 evpn_route_result.stdout
-rwxrwxrwx 1 root root 15608 May  7 09:38 evpn_overlay_result.stdout
```
```
cumulus@oob-mgmt-server:~/triage$ head -n2 /var/cumulus-collected/leaf01/*
==> /var/cumulus-collected/leaf01/arp_result.stdout <==
10.2.4.102 dev vlan24 lladdr 00:03:00:22:22:02 REACHABLE
10.1.3.103 dev vlan13 lladdr 00:03:00:33:33:02 offload NOARP

==> /var/cumulus-collected/leaf01/bridge_result.stdout <==
44:38:39:00:00:15 dev peerlink vlan 13 master bridge static
44:38:39:00:00:15 dev peerlink vlan 24 master bridge static

==> /var/cumulus-collected/leaf01/evpn_mac_result.stdout <==

VNI 24 #MACs (local and remote) 8

==> /var/cumulus-collected/leaf01/evpn_overlay_result.stdout <==
Route Distinguisher: ip 10.0.0.11:2


==> /var/cumulus-collected/leaf01/evpn_route_result.stdout <==
BGP table version is 5, local router ID is 10.0.0.11
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal
```
