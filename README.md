# vmtrace
A tool that will map VMware virtual machines to interfaces on JUNOS based devices

It uses the Python SDK for vCenter (pyvmomi) for VMware related information

The tool extracts the following information from vCenter
  - vm.name
  - vm.macAddress
  - host.name

It uses PyEZ for Juniper JUNOS related information
  - Ethernet-switching table
  - vlans



Syntax

```          
vmtrace.py list
  options:  -i/--interface  'searching for all active VM:s seen on a logical interface
                            uses the syntax ge-0/0/0.0
             -s/--sort       'sort the output based on:
                                                        vmname
                                                        vlan
                                                        vm-mac
                                                        interface-name

vmtrace find
  options:  -v/--vm         'searching for all VM:s with specified characters:
                            --vm 'VM' will search for all VM:s with the charecters VM in the name
                                  NOTE: the seach is case sensitive
            -s/--sort       'sort the output based on:
                                                        vmname
                                                        vlan
                                                        vm-mac
                                                        interface-name
```  
Sample output:
```
mac:vmtrace user$ python vmtracep.py list -i ge-2/0/35.0  -s vlan
Established connection to Juniper VMware vCenter
Established connection to Juniper System...

Interface	  VLAN ID		VM MAC			        VMware Host		  Virtual Machine Name
ge-2/0/35.0	105		    00:50:56:a8:1a:e9	  172.30.105.56		w2k1.swelab.jnpr.net
ge-2/0/35.0	105		    00:50:56:a8:81:81	  172.30.105.56		w2k2.swelab.jnpr.net
ge-2/0/35.0	105		    00:50:56:a8:0c:d1	  172.30.105.56		contrail_ctrl.swelab.jnpr.net
ge-2/0/35.0	105		    00:50:56:a8:24:d6	  172.30.105.56		contrail_cnl.swelab.jnpr.net
ge-2/0/35.0	105		    00:50:56:a8:b0:68	  172.30.105.56		contrail_cn2.swelab.jnpr.net
ge-2/0/35.0	105		    00:50:56:a8:67:a2	  172.30.105.56		space.swelab.jnpr.net
```

