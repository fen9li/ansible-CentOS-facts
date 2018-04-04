## ansible-CentOS-facts
A quick reference on CentOS facts (ansible web -m setup)

### Setup Ansible working directoy
```
[fli@ansible ~]$ pwd
/home/fli
[fli@ansible ~]$ tree
.
└── ansible
    ├── ansible.cfg
    ├── inventory
        └── hosts
...
[fli@ansible ~]$

[fli@ansible ~]$ egrep -v '^#|^$' ansible/ansible.cfg
[defaults]
inventory = inventory/hosts
[inventory]
[privilege_escalation]
[paramiko_connection]
[ssh_connection]
[persistent_connection]
[accelerate]
[selinux]
[colors]
[diff]
[fli@ansible ~]$

[fli@ansible ~]$ cat ansible/inventory/hosts
# Web server
[web]
ansicli01.fen9.li

# Database server
[database]
ansicli02.fen9.li

# Group 'multi' with all servers
[multi:children]
web
database

# Variables that will be applied to all servers
[multi:vars]
ansible_ssh_user=fli
ansible_ssh_private_key_file=~/.ssh/id_rsa
[fli@ansible ~]$
```

### Run ansible ad-hoc command to collect CentOS facts

```
[fli@ansible ansible]$ ansible web -m setup
ansicli01.fen9.li | SUCCESS => {
    "ansible_facts": {
        "ansible_all_ipv4_addresses": [
            "192.168.200.101"
        ],
        "ansible_all_ipv6_addresses": [
            "fe80::8258:1555:9310:fce3"
        ],
        "ansible_apparmor": {
            "status": "disabled"
        },
        "ansible_architecture": "x86_64",
        "ansible_bios_date": "07/02/2015",
        "ansible_bios_version": "6.00",
        "ansible_cmdline": {
            "BOOT_IMAGE": "/vmlinuz-3.10.0-693.21.1.el7.x86_64",
            "LANG": "en_US.UTF-8",
            "crashkernel": "auto",
            "quiet": true,
            "rd.lvm.lv": "centos/swap",
            "rhgb": true,
            "ro": true,
            "root": "/dev/mapper/centos-root"
        },
        "ansible_date_time": {
            "date": "2018-04-04",
            "day": "04",
            "epoch": "1522802148",
            "hour": "10",
            "iso8601": "2018-04-04T00:35:48Z",
            "iso8601_basic": "20180404T103548904279",
            "iso8601_basic_short": "20180404T103548",
            "iso8601_micro": "2018-04-04T00:35:48.904348Z",
            "minute": "35",
            "month": "04",
            "second": "48",
            "time": "10:35:48",
            "tz": "AEST",
            "tz_offset": "+1000",
            "weekday": "Wednesday",
            "weekday_number": "3",
            "weeknumber": "14",
            "year": "2018"
        },
        "ansible_default_ipv4": {
            "address": "192.168.200.101",
            "alias": "ens33",
            "broadcast": "192.168.200.255",
            "gateway": "192.168.200.2",
            "interface": "ens33",
            "macaddress": "00:0c:29:4e:f5:7d",
            "mtu": 1500,
            "netmask": "255.255.255.0",
            "network": "192.168.200.0",
            "type": "ether"
        },
        "ansible_default_ipv6": {},
        "ansible_device_links": {
            "ids": {
                "dm-0": [
                    "dm-name-centos-root",
                    "dm-uuid-LVM-kxpf01sSZjh0k5F21jItgBiwe9rv3x6eSuxJk0Uwr7z8TNwxJU4q11jlIrdc01Ai"
                ],
                "dm-1": [
                    "dm-name-centos-swap",
                    "dm-uuid-LVM-kxpf01sSZjh0k5F21jItgBiwe9rv3x6e5gDpYJydOw4Htkz640XI7dZIRtqPnQ8N"
                ],
                "dm-2": [
                    "dm-name-centos-home",
                    "dm-uuid-LVM-kxpf01sSZjh0k5F21jItgBiwe9rv3x6e7ytYe8I8qzWmk6xUH0qLszPY3UYySDD2"
                ],
                "sda2": [
                    "lvm-pv-uuid-wCPQXU-t1W4-n3zm-qf27-Evfz-zcRL-LRe769"
                ],
                "sr0": [
                    "ata-VMware_Virtual_IDE_CDROM_Drive_10000000000000000001"
                ]
            },
            "labels": {
                "sr0": [
                    "CentOS\\x207\\x20x86_64"
                ]
            },
            "masters": {
                "sda2": [
                    "dm-0",
                    "dm-1",
                    "dm-2"
                ]
            },
            "uuids": {
                "dm-0": [
                    "c6235ef8-5a7d-46d7-b37a-7be050c9fe1c"
                ],
                "dm-1": [
                    "9e261ff0-8e20-485e-a62d-2ccead6c3fca"
                ],
                "dm-2": [
                    "fc1b190b-1195-4063-8d96-7363ea7cbf5c"
                ],
                "sda1": [
                    "0f95f87f-ddb9-4490-8f03-0f829e2bf619"
                ],
                "sr0": [
                    "2017-09-06-10-53-42-00"
                ]
            }
        },
        "ansible_devices": {
            "dm-0": {
                "holders": [],
                "host": "",
                "links": {
                    "ids": [
                        "dm-name-centos-root",
                        "dm-uuid-LVM-kxpf01sSZjh0k5F21jItgBiwe9rv3x6eSuxJk0Uwr7z8TNwxJU4q11jlIrdc01Ai"
                    ],
                    "labels": [],
                    "masters": [],
                    "uuids": [
                        "c6235ef8-5a7d-46d7-b37a-7be050c9fe1c"
                    ]
                },
                "model": null,
                "partitions": {},
                "removable": "0",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "",
                "sectors": "20971520",
                "sectorsize": "512",
                "size": "10.00 GB",
                "support_discard": "0",
                "vendor": null,
                "virtual": 1
            },
            "dm-1": {
                "holders": [],
                "host": "",
                "links": {
                    "ids": [
                        "dm-name-centos-swap",
                        "dm-uuid-LVM-kxpf01sSZjh0k5F21jItgBiwe9rv3x6e5gDpYJydOw4Htkz640XI7dZIRtqPnQ8N"
                    ],
                    "labels": [],
                    "masters": [],
                    "uuids": [
                        "9e261ff0-8e20-485e-a62d-2ccead6c3fca"
                    ]
                },
                "model": null,
                "partitions": {},
                "removable": "0",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "",
                "sectors": "4194304",
                "sectorsize": "512",
                "size": "2.00 GB",
                "support_discard": "0",
                "vendor": null,
                "virtual": 1
            },
            "dm-2": {
                "holders": [],
                "host": "",
                "links": {
                    "ids": [
                        "dm-name-centos-home",
                        "dm-uuid-LVM-kxpf01sSZjh0k5F21jItgBiwe9rv3x6e7ytYe8I8qzWmk6xUH0qLszPY3UYySDD2"
                    ],
                    "labels": [],
                    "masters": [],
                    "uuids": [
                        "fc1b190b-1195-4063-8d96-7363ea7cbf5c"
                    ]
                },
                "model": null,
                "partitions": {},
                "removable": "0",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "",
                "sectors": "10485760",
                "sectorsize": "512",
                "size": "5.00 GB",
                "support_discard": "0",
                "vendor": null,
                "virtual": 1
            },
            "sda": {
                "holders": [],
                "host": "SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)",
                "links": {
                    "ids": [],
                    "labels": [],
                    "masters": [],
                    "uuids": []
                },
                "model": "VMware Virtual S",
                "partitions": {
                    "sda1": {
                        "holders": [],
                        "links": {
                            "ids": [],
                            "labels": [],
                            "masters": [],
                            "uuids": [
                                "0f95f87f-ddb9-4490-8f03-0f829e2bf619"
                            ]
                        },
                        "sectors": "1048576",
                        "sectorsize": 512,
                        "size": "512.00 MB",
                        "start": "2048",
                        "uuid": "0f95f87f-ddb9-4490-8f03-0f829e2bf619"
                    },
                    "sda2": {
                        "holders": [
                            "centos-root",
                            "centos-swap",
                            "centos-home"
                        ],
                        "links": {
                            "ids": [
                                "lvm-pv-uuid-wCPQXU-t1W4-n3zm-qf27-Evfz-zcRL-LRe769"
                            ],
                            "labels": [],
                            "masters": [
                                "dm-0",
                                "dm-1",
                                "dm-2"
                            ],
                            "uuids": []
                        },
                        "sectors": "35667968",
                        "sectorsize": 512,
                        "size": "17.01 GB",
                        "start": "1050624",
                        "uuid": null
                    }
                },
                "removable": "0",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "deadline",
                "sectors": "104857600",
                "sectorsize": "512",
                "size": "50.00 GB",
                "support_discard": "0",
                "vendor": "VMware,",
                "virtual": 1
            },
            "sr0": {
                "holders": [],
                "host": "IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)",
                "links": {
                    "ids": [
                        "ata-VMware_Virtual_IDE_CDROM_Drive_10000000000000000001"
                    ],
                    "labels": [
                        "CentOS\\x207\\x20x86_64"
                    ],
                    "masters": [],
                    "uuids": [
                        "2017-09-06-10-53-42-00"
                    ]
                },
                "model": "VMware IDE CDR10",
                "partitions": {},
                "removable": "1",
                "rotational": "1",
                "sas_address": null,
                "sas_device_handle": null,
                "scheduler_mode": "cfq",
                "sectors": "16982016",
                "sectorsize": "2048",
                "size": "32.39 GB",
                "support_discard": "0",
                "vendor": "NECVMWar",
                "virtual": 1
            }
        },
        "ansible_distribution": "CentOS",
        "ansible_distribution_file_parsed": true,
        "ansible_distribution_file_path": "/etc/redhat-release",
        "ansible_distribution_file_variety": "RedHat",
        "ansible_distribution_major_version": "7",
        "ansible_distribution_release": "Core",
        "ansible_distribution_version": "7.4.1708",
        "ansible_dns": {
            "nameservers": [
                "192.168.200.2"
            ],
            "search": [
                "fen9.li"
            ]
        },
        "ansible_domain": "fen9.li",
        "ansible_effective_group_id": 1000,
        "ansible_effective_user_id": 1000,
        "ansible_ens33": {
            "active": true,
            "device": "ens33",
            "features": {
                "busy_poll": "off [fixed]",
                "fcoe_mtu": "off [fixed]",
                "generic_receive_offload": "on",
                "generic_segmentation_offload": "on",
                "highdma": "off [fixed]",
                "hw_tc_offload": "off [fixed]",
                "l2_fwd_offload": "off [fixed]",
                "large_receive_offload": "off [fixed]",
                "loopback": "off [fixed]",
                "netns_local": "off [fixed]",
                "ntuple_filters": "off [fixed]",
                "receive_hashing": "off [fixed]",
                "rx_all": "off",
                "rx_checksumming": "off",
                "rx_fcs": "off",
                "rx_vlan_filter": "on [fixed]",
                "rx_vlan_offload": "on",
                "rx_vlan_stag_filter": "off [fixed]",
                "rx_vlan_stag_hw_parse": "off [fixed]",
                "scatter_gather": "on",
                "tcp_segmentation_offload": "on",
                "tx_checksum_fcoe_crc": "off [fixed]",
                "tx_checksum_ip_generic": "on",
                "tx_checksum_ipv4": "off [fixed]",
                "tx_checksum_ipv6": "off [fixed]",
                "tx_checksum_sctp": "off [fixed]",
                "tx_checksumming": "on",
                "tx_fcoe_segmentation": "off [fixed]",
                "tx_gre_csum_segmentation": "off [fixed]",
                "tx_gre_segmentation": "off [fixed]",
                "tx_gso_partial": "off [fixed]",
                "tx_gso_robust": "off [fixed]",
                "tx_ipip_segmentation": "off [fixed]",
                "tx_lockless": "off [fixed]",
                "tx_mpls_segmentation": "off [fixed]",
                "tx_nocache_copy": "off",
                "tx_scatter_gather": "on",
                "tx_scatter_gather_fraglist": "off [fixed]",
                "tx_sctp_segmentation": "off [fixed]",
                "tx_sit_segmentation": "off [fixed]",
                "tx_tcp6_segmentation": "off [fixed]",
                "tx_tcp_ecn_segmentation": "off [fixed]",
                "tx_tcp_mangleid_segmentation": "off",
                "tx_tcp_segmentation": "on",
                "tx_udp_tnl_csum_segmentation": "off [fixed]",
                "tx_udp_tnl_segmentation": "off [fixed]",
                "tx_vlan_offload": "on [fixed]",
                "tx_vlan_stag_hw_insert": "off [fixed]",
                "udp_fragmentation_offload": "off [fixed]",
                "vlan_challenged": "off [fixed]"
            },
            "hw_timestamp_filters": [],
            "ipv4": {
                "address": "192.168.200.101",
                "broadcast": "192.168.200.255",
                "netmask": "255.255.255.0",
                "network": "192.168.200.0"
            },
            "ipv6": [
                {
                    "address": "fe80::8258:1555:9310:fce3",
                    "prefix": "64",
                    "scope": "link"
                }
            ],
            "macaddress": "00:0c:29:4e:f5:7d",
            "module": "e1000",
            "mtu": 1500,
            "pciid": "0000:02:01.0",
            "promisc": false,
            "speed": 1000,
            "timestamping": [
                "tx_software",
                "rx_software",
                "software"
            ],
            "type": "ether"
        },
        "ansible_ens34": {
            "active": true,
            "device": "ens34",
            "features": {
                "busy_poll": "off [fixed]",
                "fcoe_mtu": "off [fixed]",
                "generic_receive_offload": "on",
                "generic_segmentation_offload": "on",
                "highdma": "off [fixed]",
                "hw_tc_offload": "off [fixed]",
                "l2_fwd_offload": "off [fixed]",
                "large_receive_offload": "off [fixed]",
                "loopback": "off [fixed]",
                "netns_local": "off [fixed]",
                "ntuple_filters": "off [fixed]",
                "receive_hashing": "off [fixed]",
                "rx_all": "off",
                "rx_checksumming": "off",
                "rx_fcs": "off",
                "rx_vlan_filter": "on [fixed]",
                "rx_vlan_offload": "on",
                "rx_vlan_stag_filter": "off [fixed]",
                "rx_vlan_stag_hw_parse": "off [fixed]",
                "scatter_gather": "on",
                "tcp_segmentation_offload": "on",
                "tx_checksum_fcoe_crc": "off [fixed]",
                "tx_checksum_ip_generic": "on",
                "tx_checksum_ipv4": "off [fixed]",
                "tx_checksum_ipv6": "off [fixed]",
                "tx_checksum_sctp": "off [fixed]",
                "tx_checksumming": "on",
                "tx_fcoe_segmentation": "off [fixed]",
                "tx_gre_csum_segmentation": "off [fixed]",
                "tx_gre_segmentation": "off [fixed]",
                "tx_gso_partial": "off [fixed]",
                "tx_gso_robust": "off [fixed]",
                "tx_ipip_segmentation": "off [fixed]",
                "tx_lockless": "off [fixed]",
                "tx_mpls_segmentation": "off [fixed]",
                "tx_nocache_copy": "off",
                "tx_scatter_gather": "on",
                "tx_scatter_gather_fraglist": "off [fixed]",
                "tx_sctp_segmentation": "off [fixed]",
                "tx_sit_segmentation": "off [fixed]",
                "tx_tcp6_segmentation": "off [fixed]",
                "tx_tcp_ecn_segmentation": "off [fixed]",
                "tx_tcp_mangleid_segmentation": "off",
                "tx_tcp_segmentation": "on",
                "tx_udp_tnl_csum_segmentation": "off [fixed]",
                "tx_udp_tnl_segmentation": "off [fixed]",
                "tx_vlan_offload": "on [fixed]",
                "tx_vlan_stag_hw_insert": "off [fixed]",
                "udp_fragmentation_offload": "off [fixed]",
                "vlan_challenged": "off [fixed]"
            },
            "hw_timestamp_filters": [],
            "macaddress": "00:0c:29:4e:f5:87",
            "module": "e1000",
            "mtu": 1500,
            "pciid": "0000:02:02.0",
            "promisc": false,
            "speed": 1000,
            "timestamping": [
                "tx_software",
                "rx_software",
                "software"
            ],
            "type": "ether"
        },
        "ansible_ens35": {
            "active": true,
            "device": "ens35",
            "features": {
                "busy_poll": "off [fixed]",
                "fcoe_mtu": "off [fixed]",
                "generic_receive_offload": "on",
                "generic_segmentation_offload": "on",
                "highdma": "off [fixed]",
                "hw_tc_offload": "off [fixed]",
                "l2_fwd_offload": "off [fixed]",
                "large_receive_offload": "off [fixed]",
                "loopback": "off [fixed]",
                "netns_local": "off [fixed]",
                "ntuple_filters": "off [fixed]",
                "receive_hashing": "off [fixed]",
                "rx_all": "off",
                "rx_checksumming": "off",
                "rx_fcs": "off",
                "rx_vlan_filter": "on [fixed]",
                "rx_vlan_offload": "on",
                "rx_vlan_stag_filter": "off [fixed]",
                "rx_vlan_stag_hw_parse": "off [fixed]",
                "scatter_gather": "on",
                "tcp_segmentation_offload": "on",
                "tx_checksum_fcoe_crc": "off [fixed]",
                "tx_checksum_ip_generic": "on",
                "tx_checksum_ipv4": "off [fixed]",
                "tx_checksum_ipv6": "off [fixed]",
                "tx_checksum_sctp": "off [fixed]",
                "tx_checksumming": "on",
                "tx_fcoe_segmentation": "off [fixed]",
                "tx_gre_csum_segmentation": "off [fixed]",
                "tx_gre_segmentation": "off [fixed]",
                "tx_gso_partial": "off [fixed]",
                "tx_gso_robust": "off [fixed]",
                "tx_ipip_segmentation": "off [fixed]",
                "tx_lockless": "off [fixed]",
                "tx_mpls_segmentation": "off [fixed]",
                "tx_nocache_copy": "off",
                "tx_scatter_gather": "on",
                "tx_scatter_gather_fraglist": "off [fixed]",
                "tx_sctp_segmentation": "off [fixed]",
                "tx_sit_segmentation": "off [fixed]",
                "tx_tcp6_segmentation": "off [fixed]",
                "tx_tcp_ecn_segmentation": "off [fixed]",
                "tx_tcp_mangleid_segmentation": "off",
                "tx_tcp_segmentation": "on",
                "tx_udp_tnl_csum_segmentation": "off [fixed]",
                "tx_udp_tnl_segmentation": "off [fixed]",
                "tx_vlan_offload": "on [fixed]",
                "tx_vlan_stag_hw_insert": "off [fixed]",
                "udp_fragmentation_offload": "off [fixed]",
                "vlan_challenged": "off [fixed]"
            },
            "hw_timestamp_filters": [],
            "macaddress": "00:0c:29:4e:f5:91",
            "module": "e1000",
            "mtu": 1500,
            "pciid": "0000:02:03.0",
            "promisc": false,
            "speed": 1000,
            "timestamping": [
                "tx_software",
                "rx_software",
                "software"
            ],
            "type": "ether"
        },
        "ansible_ens36": {
            "active": true,
            "device": "ens36",
            "features": {
                "busy_poll": "off [fixed]",
                "fcoe_mtu": "off [fixed]",
                "generic_receive_offload": "on",
                "generic_segmentation_offload": "on",
                "highdma": "off [fixed]",
                "hw_tc_offload": "off [fixed]",
                "l2_fwd_offload": "off [fixed]",
                "large_receive_offload": "off [fixed]",
                "loopback": "off [fixed]",
                "netns_local": "off [fixed]",
                "ntuple_filters": "off [fixed]",
                "receive_hashing": "off [fixed]",
                "rx_all": "off",
                "rx_checksumming": "off",
                "rx_fcs": "off",
                "rx_vlan_filter": "on [fixed]",
                "rx_vlan_offload": "on",
                "rx_vlan_stag_filter": "off [fixed]",
                "rx_vlan_stag_hw_parse": "off [fixed]",
                "scatter_gather": "on",
                "tcp_segmentation_offload": "on",
                "tx_checksum_fcoe_crc": "off [fixed]",
                "tx_checksum_ip_generic": "on",
                "tx_checksum_ipv4": "off [fixed]",
                "tx_checksum_ipv6": "off [fixed]",
                "tx_checksum_sctp": "off [fixed]",
                "tx_checksumming": "on",
                "tx_fcoe_segmentation": "off [fixed]",
                "tx_gre_csum_segmentation": "off [fixed]",
                "tx_gre_segmentation": "off [fixed]",
                "tx_gso_partial": "off [fixed]",
                "tx_gso_robust": "off [fixed]",
                "tx_ipip_segmentation": "off [fixed]",
                "tx_lockless": "off [fixed]",
                "tx_mpls_segmentation": "off [fixed]",
                "tx_nocache_copy": "off",
                "tx_scatter_gather": "on",
                "tx_scatter_gather_fraglist": "off [fixed]",
                "tx_sctp_segmentation": "off [fixed]",
                "tx_sit_segmentation": "off [fixed]",
                "tx_tcp6_segmentation": "off [fixed]",
                "tx_tcp_ecn_segmentation": "off [fixed]",
                "tx_tcp_mangleid_segmentation": "off",
                "tx_tcp_segmentation": "on",
                "tx_udp_tnl_csum_segmentation": "off [fixed]",
                "tx_udp_tnl_segmentation": "off [fixed]",
                "tx_vlan_offload": "on [fixed]",
                "tx_vlan_stag_hw_insert": "off [fixed]",
                "udp_fragmentation_offload": "off [fixed]",
                "vlan_challenged": "off [fixed]"
            },
            "hw_timestamp_filters": [],
            "macaddress": "00:0c:29:4e:f5:9b",
            "module": "e1000",
            "mtu": 1500,
            "pciid": "0000:02:04.0",
            "promisc": false,
            "speed": 1000,
            "timestamping": [
                "tx_software",
                "rx_software",
                "software"
            ],
            "type": "ether"
        },
        "ansible_env": {
            "HOME": "/home/fli",
            "LANG": "en_US.UTF-8",
            "LESSOPEN": "||/usr/bin/lesspipe.sh %s",
            "LOGNAME": "fli",
            "LS_COLORS": "rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=01;05;37;41:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=01;36:*.au=01;36:*.flac=01;36:*.mid=01;36:*.midi=01;36:*.mka=01;36:*.mp3=01;36:*.mpc=01;36:*.ogg=01;36:*.ra=01;36:*.wav=01;36:*.axa=01;36:*.oga=01;36:*.spx=01;36:*.xspf=01;36:",
            "MAIL": "/var/mail/fli",
            "PATH": "/usr/local/bin:/usr/bin",
            "PWD": "/home/fli",
            "SELINUX_LEVEL_REQUESTED": "",
            "SELINUX_ROLE_REQUESTED": "",
            "SELINUX_USE_CURRENT_RANGE": "",
            "SHELL": "/bin/bash",
            "SHLVL": "2",
            "SSH_CLIENT": "192.168.200.45 34724 22",
            "SSH_CONNECTION": "192.168.200.45 34724 192.168.200.101 22",
            "SSH_TTY": "/dev/pts/0",
            "TERM": "xterm",
            "USER": "fli",
            "XDG_RUNTIME_DIR": "/run/user/1000",
            "XDG_SESSION_ID": "7",
            "_": "/usr/bin/python"
        },
        "ansible_fips": false,
        "ansible_form_factor": "Other",
        "ansible_fqdn": "ansicli01.fen9.li",
        "ansible_hostname": "ansicli01",
        "ansible_interfaces": [
            "ens34",
            "lo",
            "ens36",
            "ens33",
            "ens35"
        ],
        "ansible_kernel": "3.10.0-693.21.1.el7.x86_64",
        "ansible_lo": {
            "active": true,
            "device": "lo",
            "features": {
                "busy_poll": "off [fixed]",
                "fcoe_mtu": "off [fixed]",
                "generic_receive_offload": "on",
                "generic_segmentation_offload": "on",
                "highdma": "on [fixed]",
                "hw_tc_offload": "off [fixed]",
                "l2_fwd_offload": "off [fixed]",
                "large_receive_offload": "off [fixed]",
                "loopback": "on [fixed]",
                "netns_local": "on [fixed]",
                "ntuple_filters": "off [fixed]",
                "receive_hashing": "off [fixed]",
                "rx_all": "off [fixed]",
                "rx_checksumming": "on [fixed]",
                "rx_fcs": "off [fixed]",
                "rx_vlan_filter": "off [fixed]",
                "rx_vlan_offload": "off [fixed]",
                "rx_vlan_stag_filter": "off [fixed]",
                "rx_vlan_stag_hw_parse": "off [fixed]",
                "scatter_gather": "on",
                "tcp_segmentation_offload": "on",
                "tx_checksum_fcoe_crc": "off [fixed]",
                "tx_checksum_ip_generic": "on [fixed]",
                "tx_checksum_ipv4": "off [fixed]",
                "tx_checksum_ipv6": "off [fixed]",
                "tx_checksum_sctp": "on [fixed]",
                "tx_checksumming": "on",
                "tx_fcoe_segmentation": "off [fixed]",
                "tx_gre_csum_segmentation": "off [fixed]",
                "tx_gre_segmentation": "off [fixed]",
                "tx_gso_partial": "off [fixed]",
                "tx_gso_robust": "off [fixed]",
                "tx_ipip_segmentation": "off [fixed]",
                "tx_lockless": "on [fixed]",
                "tx_mpls_segmentation": "off [fixed]",
                "tx_nocache_copy": "off [fixed]",
                "tx_scatter_gather": "on [fixed]",
                "tx_scatter_gather_fraglist": "on [fixed]",
                "tx_sctp_segmentation": "on",
                "tx_sit_segmentation": "off [fixed]",
                "tx_tcp6_segmentation": "on",
                "tx_tcp_ecn_segmentation": "on",
                "tx_tcp_mangleid_segmentation": "on",
                "tx_tcp_segmentation": "on",
                "tx_udp_tnl_csum_segmentation": "off [fixed]",
                "tx_udp_tnl_segmentation": "off [fixed]",
                "tx_vlan_offload": "off [fixed]",
                "tx_vlan_stag_hw_insert": "off [fixed]",
                "udp_fragmentation_offload": "on",
                "vlan_challenged": "on [fixed]"
            },
            "hw_timestamp_filters": [],
            "ipv4": {
                "address": "127.0.0.1",
                "broadcast": "host",
                "netmask": "255.0.0.0",
                "network": "127.0.0.0"
            },
            "ipv6": [
                {
                    "address": "::1",
                    "prefix": "128",
                    "scope": "host"
                }
            ],
            "mtu": 65536,
            "promisc": false,
            "timestamping": [
                "rx_software",
                "software"
            ],
            "type": "loopback"
        },
        "ansible_local": {},
        "ansible_lsb": {},
        "ansible_machine": "x86_64",
        "ansible_machine_id": "02f832d7476442bfae1c7fe7b465871e",
        "ansible_memfree_mb": 1487,
        "ansible_memory_mb": {
            "nocache": {
                "free": 1609,
                "used": 213
            },
            "real": {
                "free": 1487,
                "total": 1822,
                "used": 335
            },
            "swap": {
                "cached": 0,
                "free": 2047,
                "total": 2047,
                "used": 0
            }
        },
        "ansible_memtotal_mb": 1822,
        "ansible_mounts": [
            {
                "block_available": 2280996,
                "block_size": 4096,
                "block_total": 2618880,
                "block_used": 337884,
                "device": "/dev/mapper/centos-root",
                "fstype": "xfs",
                "inode_available": 5204122,
                "inode_total": 5242880,
                "inode_used": 38758,
                "mount": "/",
                "options": "rw,seclabel,relatime,attr2,inode64,noquota",
                "size_available": 9342959616,
                "size_total": 10726932480,
                "uuid": "c6235ef8-5a7d-46d7-b37a-7be050c9fe1c"
            },
            {
                "block_available": 71555,
                "block_size": 4096,
                "block_total": 130217,
                "block_used": 58662,
                "device": "/dev/sda1",
                "fstype": "xfs",
                "inode_available": 261802,
                "inode_total": 262144,
                "inode_used": 342,
                "mount": "/boot",
                "options": "rw,seclabel,relatime,attr2,inode64,noquota",
                "size_available": 293089280,
                "size_total": 533368832,
                "uuid": "0f95f87f-ddb9-4490-8f03-0f829e2bf619"
            },
            {
                "block_available": 1299850,
                "block_size": 4096,
                "block_total": 1308160,
                "block_used": 8310,
                "device": "/dev/mapper/centos-home",
                "fstype": "xfs",
                "inode_available": 2621426,
                "inode_total": 2621440,
                "inode_used": 14,
                "mount": "/home",
                "options": "rw,seclabel,relatime,attr2,inode64,noquota",
                "size_available": 5324185600,
                "size_total": 5358223360,
                "uuid": "fc1b190b-1195-4063-8d96-7363ea7cbf5c"
            }
        ],
        "ansible_nodename": "ansicli01.fen9.li",
        "ansible_os_family": "RedHat",
        "ansible_pkg_mgr": "yum",
        "ansible_processor": [
            "0",
            "GenuineIntel",
            "Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz",
            "1",
            "GenuineIntel",
            "Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz"
        ],
        "ansible_processor_cores": 1,
        "ansible_processor_count": 2,
        "ansible_processor_threads_per_core": 1,
        "ansible_processor_vcpus": 2,
        "ansible_product_name": "VMware Virtual Platform",
        "ansible_product_serial": "NA",
        "ansible_product_uuid": "NA",
        "ansible_product_version": "None",
        "ansible_python": {
            "executable": "/usr/bin/python",
            "has_sslcontext": true,
            "type": "CPython",
            "version": {
                "major": 2,
                "micro": 5,
                "minor": 7,
                "releaselevel": "final",
                "serial": 0
            },
            "version_info": [
                2,
                7,
                5,
                "final",
                0
            ]
        },
        "ansible_python_version": "2.7.5",
        "ansible_real_group_id": 1000,
        "ansible_real_user_id": 1000,
        "ansible_selinux": {
            "config_mode": "enforcing",
            "mode": "enforcing",
            "policyvers": 28,
            "status": "enabled",
            "type": "targeted"
        },
        "ansible_selinux_python_present": true,
        "ansible_service_mgr": "systemd",
        "ansible_ssh_host_key_ecdsa_public": "AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBACm7bt+h9+rnG3FyaiTKshw16eY2rhrfrKJbLAmRcjGztcOlfXsBdCps569yoTHAfW7NhcLSDeXvALQ4/ebfAc=",
        "ansible_ssh_host_key_ed25519_public": "AAAAC3NzaC1lZDI1NTE5AAAAIOI2oqI4QcArkFf84pc1KxEDyjSIqznr/+Ku6cmZJ9/+",
        "ansible_ssh_host_key_rsa_public": "AAAAB3NzaC1yc2EAAAADAQABAAABAQCig/0vlp2D6jDqhDpLBK8FkKkst/ZJz3+qRNw4nq+AmAO+gf0rSDMSGuNj/LQM1+8gElhoOwTaRNyPiSYH/axhJn0kSRY2Xgn7f6xD4GPGtDkUrbkZVwKkEA6OvmWWGE6jKybgKj8dEhs+8rNwFyDHH/0akOX4EmuMWZdXiWv1pdCpKHD7DXDp8D24pce4JPX36Oh22hv741NoKmf4b4b7bamIza+GQC0HMEPirvIkXK+ZSUmuaeD2wju08545bmR7NFP4DD4zegx8gI25+bWDk4f/VIIbEt2ZwY/k7QSg0flakYxCUukFWR7VRw5Od2/LBUpQko04i/OxlCdI3mdL",
        "ansible_swapfree_mb": 2047,
        "ansible_swaptotal_mb": 2047,
        "ansible_system": "Linux",
        "ansible_system_capabilities": [
            ""
        ],
        "ansible_system_capabilities_enforced": "True",
        "ansible_system_vendor": "VMware, Inc.",
        "ansible_uptime_seconds": 9276,
        "ansible_user_dir": "/home/fli",
        "ansible_user_gecos": "Feng Li",
        "ansible_user_gid": 1000,
        "ansible_user_id": "fli",
        "ansible_user_shell": "/bin/bash",
        "ansible_user_uid": 1000,
        "ansible_userspace_architecture": "x86_64",
        "ansible_userspace_bits": "64",
        "ansible_virtualization_role": "guest",
        "ansible_virtualization_type": "VMware",
        "gather_subset": [
            "all"
        ],
        "module_setup": true
    },
    "changed": false
}
[fli@ansible ansible]$

```

### Usecase

```
[fli@ansible ansible]$ vim playbooks/os.yml
[fli@ansible ansible]$ cat playbooks/os.yml
---
- name: print out operating system facts
  hosts: all
  gather_facts: True

  tasks:
  - debug: var=ansible_env.LOGNAME
[fli@ansible ansible]$ ansible-playbook playbooks/os.yml

PLAY [print out operating system facts] ****************************************

TASK [Gathering Facts] *********************************************************
ok: [ansicli01.fen9.li]
ok: [ansicli02.fen9.li]

TASK [debug] *******************************************************************
ok: [ansicli01.fen9.li] => {
    "ansible_env.LOGNAME": "fli"
}
ok: [ansicli02.fen9.li] => {
    "ansible_env.LOGNAME": "fli"
}

PLAY RECAP *********************************************************************
ansicli01.fen9.li          : ok=2    changed=0    unreachable=0    failed=0
ansicli02.fen9.li          : ok=2    changed=0    unreachable=0    failed=0

[fli@ansible ansible]$

```
