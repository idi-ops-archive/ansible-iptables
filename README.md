Ansible Role: iptables
======================

This role will deploy iptables rules that block everything by default and only allow certain ports to receive connections.

Requirements
------------

iptables and iptables-services packages pre-installed.

Role Variables
--------------

 * iptables_rules

  * format: `[ proto, dest_port, src_addr ]`
  * `proto` can be either `tcp` or `udp`.
  * `dest_port` must be a numeric value between 1 and 65535.
  * `src_addr` can be either `any` or a CIDR value.

 *   iptables_allow_icmp (boolean, default: yes)
 *   iptables_log (boolean,default: no)
 *   iptables_log_rate (numeric, default: 15 per minute)

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: iptables
           iptables_rules:
             - [ tcp,   22, 192.168.100/24 ]
             - [ tcp,   80,            any ]
             - [ udp,  123,            any ]
