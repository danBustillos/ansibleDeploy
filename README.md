# ansible deploy for aci

The orchestration order is defined by the ansible code bases provided.

## The general build process is:

1. cd to the appropriate directory
2. modify relevant variables located in /group_vars/apic.yml or msc.yml respectively
3. confirm hosts.ini file contains the correct management IP/username/passowrd for apic and msc respectively.
4. execute main.yml
5. command: ansible-playbook -i hosts.ini main.yml


# aci.build directory
1. aci.fabric.policies
    1. role to provision day one build fabric policies
    2. tasks/main.yml
2. aci.access.policies
    1. role to provision day one access policies
    2. tasks/main.yml
3. aci.global.policies
    1. role to provision day one global policies
    2. tasks/main.yml
4. aci.tenant.policies
    1. role to provision day one tenant policies
    2. tasks/main.yml
5. aci.oob.policies
    1. role to provision day one tenant policies
    2. tasks/main.yml
6. group_vars
    1. apic.yml
    2. container for all apic variables respective to the directory
    3. apic.yml
    4. container for all apic variables respective to the directory
7. hosts.ini
    1. contains target ip or fqdn information, username and password for apic and msc to be passed in during deployment
Execution
8. execution
    1. ansible-playbook -i hosts.ini main.yml


# aci.operations directory
1. aci.policy.group
    1. role to provision day two policy groups
    2. tasks/main.yml
2. aci.port.selector
    1. role to provision day two port selectors
    2. tasks/main.yml
3. aci.port.static.mapping
    1. role to provision day two port static mapping
    2. tasks/main.yml
4. group_vars
    1. apic.yml
    2. container for all apic variables respective to the directory
    3. apic.yml
    4. container for all apic variables respective to the directory
5. hosts.ini
    1. contains target ip or fqdn information, username and password for apic and msc to be passed in during deployment
Execution
6. execution
    1. ansible-playbook -i hosts.ini main.yml

# aci.migrations directory
1. aci.bd1-3
    1. role to provision the enablement of a gateway on a bridge domain
    2. role to provision the enablement of adding a bridge domain to an l3out
    role to provision the enablement of adding a custom mac to the bridge domain
    3. tasks/main.yml
2. aci.gateway1-3
    1. role to provision the shutting down of a gateway on a non aci device
    2. tasks/main.yml
3. aci.pre_check
    1. role to provision the capture of arp information of the legacy vlan being migrated to aci
    2. role to output the result to a file in the directory
    3. tasks/main.yml
4. group_vars
    1. apic.yml
    2. container for all apic variables respective to the directory
    3. apic.yml
    4. container for all apic variables respective to the directory
5. hosts.ini
    1. contains target ip or fqdn information, username and password for apic and msc to be passed in during deployment
Execution
6. execution
    1. ansible-playbook -i hosts.ini main.yml


# msc.build directory
1. msc.build
    1. role to provision the configuration of the following. 
    		** Note:assumes schema and template are created prior to execution **

        * create.vrf
        * create.bd
        * create.ap
        * create.epg
        * create.epg-to-domain
    3. tasks/main.yml
4. group_vars
    1. msc.yml
    2. container for all msc variables respective to the directory

5. hosts.ini
    1. contains target ip or fqdn information, username and password for apic and msc to be passed in during deployment
Execution
6. execution
    1. ansible-playbook -i hosts.ini main.yml


