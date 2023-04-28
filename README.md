# ROLE dginhoux.glusterfs



## DESCRIPTION

This ansible role configure glusterfs server.<br />
The variable `gluster_node_peer_address` need to be defined on each host (host_vars).



## REQUIREMENTS

#### SUPPORTED PLATFORMS

This role require a supported platform.<br />
It will skip node with unsupported platform to avoid any compatibility problem.<br />
This behaviour can be bypassed by settings the following variable `skip_check_platform_compatibility=True`.

| Platform | Versions |
|----------|----------|
| Debian | buster, bullseye |
| Fedora | 33, 34, 35, 36, 37, 38 |
| EL | 7, 8 |

#### ANSIBLE VERSION

Ansible >= 2.13

#### DEPENDENCIES

None.



## INSTALLATION

#### ANSIBLE GALAXY

```shell
ansible-galaxy install dginhoux.glusterfs
```
#### GIT

```shell
git clone https://github.com/dginhoux/ansible_role.glusterfs dginhoux.glusterfs
```


## USAGE

#### EXAMPLE PLAYBOOK

```yaml
- hosts: all
  roles:
    - name: start role dginhoux.glusterfs
      ansible.builtin.include_role:
        name: dginhoux.glusterfs
```


## VARIABLES

#### DEFAULT VARIABLES

Defaults variables defined in `defaults/main.yml` : 

```yaml
# For Ubuntu.
# glusterfs_default_release: ""
# glusterfs_ppa_use: true
# glusterfs_ppa_version: "7"
# For Debian.
# glusterfs_gpg_key_version: "7"
# glusterfs_deb_version: "LATEST"

gluster_version: 9
glusterfs_daemon: glusterd

# internal_ip:
# gluster_use_internal_ip: false

gluster_bricks_list:
  - name: gfs_lv_swarm_prod
    path: /mnt/lv_swarm_prod
    replicas: 3
    state: present
    mount_localy: false
    mount_local_path: /mnt/gfs_lv_swarm_prod
    nodes:
      - 192.168.175.51
      - 192.168.175.52
      - 192.168.175.53
    options: {
      cache-invalidation-timeout: "600",
      client.event-threads: "8",
      # cluster.daemon-log-level: "WARNING",
      cluster.data-self-heal: "off",
      cluster.data-change-log: "off",
      cluster.data-self-heal-algorithm: "full",
      cluster.entry-change-log: "off",
      cluster.entry-self-heal: "off",
      cluster.metadata-change-log: "off",
      cluster.min-free-disk: "20%",
      cluster.min-free-inodes: "5%",
      cluster.optimistic-change-log: "off",
      cluster.self-heal-daemon: "on",
      cluster.shd-max-threads: "1",
      cluster.shd-wait-qlength: "128",
      # cluster.heal-timeout: "600",
      cluster.metadata-self-heal: "off",
      diagnostics.brick-log-level: "WARNING",
      diagnostics.client-log-level: "WARNING",
      diagnostics.brick-sys-log-level: "WARNING",
      diagnostics.client-sys-log-level: "WARNING",
      disperse.optimistic-change-log: "off",
      features.acl: "enable",
      features.barrier: "disable",
      # features.bitrot: "disable",
      features.cache-invalidation: "on",
      features.cloudsync: "off",
      features.ctime: "on",
      features.leases: "off",
      # features.quota: "off",
      # features.scrub: "false",
      features.sdfs: "off",
      features.selinux: "off",
      features.shard: "off",
      features.trash: "off",
      features.uss: "off",
      features.worm: "off",
      # ganesha.enable: "off",
      network.compression: "off",
      network.compression.mem-level: "8",
      network.compression.min-size: "0",
      network.compression.debug: "false",
      network.compression.compression-level: "-1",
      network.compression.window-size: "-15",
      network.inode-lru-limit: "30000",
      nfs.disable: "on",
      nl-cache-positive-entry: "on",
      performance.aggregate-size: "256KB",
      performance.cache-invalidation: "on",
      performance.cache-max-file-size: "2MB",
      performance.cache-size: "512MB",
      performance.client-io-threads: "on",
      performance.flush-behind: "on",
      performance.high-prio-threads: "32",
      performance.io-thread-count: "32",
      performance.low-prio-threads: "32",
      performance.normal-prio-threads: "32",
      performance.io-cache: "on",
      performance.io-cache-size: "512MB",
      performance.parallel-readdir: "on",
      performance.qr-cache-timeout: "600",
      performance.write-behind: "on",
      performance.read-ahead: "on",
      performance.readdir-ahead: "on",
      server.allow-insecure: "on",
      server.event-threads: "8",
      server.ssl: "off",
    }
```

#### DEFAULT OS SPECIFIC VARIABLES

Those variables files are located in `vars/*.yml` are used to handle OS differences.<br />
One of theses is loaded dynamically during role runtime using the `include_vars` module and set OS specifics variable's.

`NOT USED BY THIS ROLE`


## AUTHOR

Dany GINHOUX - https://github.com/dginhoux



## LICENSE

MIT
