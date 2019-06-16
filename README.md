# Ansible Role: MariaDB

#### Version: 1.0.0

[![](https://img.shields.io/badge/role-sparknsh.mariadb-blue.svg)](https://galaxy.ansible.com/sparknsh/mariadb)

Development of this project is managed in a private repository then pushed out to [GitLab](https://gitlab.com/sparknsh/ansible-role-mariadb) and [GitHub](https://github.com/sparknsh/ansible-role-mariadb) when we have a new version for you. If you have any issues please contact [sparknsh](https://www.sparknsh.com/contact?type=issue&name=ansible-role-mariadb)

## Role Variables

```yaml
mariadb__version: 10.3
mariadb__repo_https: true

mariadb__root_password: root

mariadb__databases: []
#  - name: database10
#    state: present

mariadb__users: []
#  - name: user1
#    host: 127.0.0.1
#    password: secret
#    priv: "database10.*:ALL"
#    encrypted: false

# * Basic Settings
#
mariadb__bind_address: "127.0.0.1"
mariadb__port: 3306
mariadb__basedir: /usr
mariadb__datadir: /var/lib/mysql
mariadb__tmpdir: /tmp
mariadb__lc_messages_dir: /usr/share/mysql
mariadb__lc_messages: en_US
mariadb__skip_external_locking: true
mariadb__skip_name_resolve: true
mariadb__character_set_server: utf8
mariadb__collation_server: utf8_general_ci

# * Fine Tuning
#
# mariadb__max_connections: 100
mariadb__connect_timeout: 5
mariadb__wait_timeout: 600
mariadb__max_allowed_packet: 16M
mariadb__thread_cache_size: 128
mariadb__sort_buffer_size: 4M
mariadb__bulk_insert_buffer_size: 16M
mariadb__tmp_table_size: 32M
mariadb__max_heap_table_size: 32M

# * MyISAM
#
mariadb__myisam_recover_options: BACKUP
mariadb__key_buffer_size: 128M
# mariadb__open_files_limit: 2000
mariadb__table_open_cache: 400
mariadb__myisam_sort_buffer_size: 512M
mariadb__concurrent_insert: 2
mariadb__read_buffer_size: 2M
mariadb__read_rnd_buffer_size: 1M

# * Query Cache Configuration
#
mariadb__query_cache_limit: 128K
mariadb__query_cache_size: 64M
# for more write intensive setups, set to DEMAND or OFF
# mariadb__query_cache_type: DEMAND

# * Logging and Replication
#
# mariadb__general_log_file: mysql.log
# mariadb__general_log: 1
mariadb__log_warnings: 2
# mariadb__slow_query_log: 0
mariadb__slow_query_log_file: mariadb-slow.log
mariadb__long_query_time: 10
# mariadb__log_slow_rate_limit: 1000
mariadb__log_slow_verbosity: query_plan
# mariadb__log_queries_not_using_indexes: false
# mariadb__log_slow_admin_statements: false
# mariadb__server_id: 1
# mariadb__report_host: master1
# mariadb__auto_increment_increment: 2
# mariadb__auto_increment_offset: 1
mariadb__log_bin: mariadb-bin
mariadb__log_bin_index: mariadb-bin.index
# mariadb__sync_binlog: 1
mariadb__expire_logs_days: 10
mariadb__max_binlog_size: 100M
# mariadb__relay_log: relay-bin
# mariadb__relay_log_index: relay-bin.index
# mariadb__relay_log_info_file: relay-bin.info
# mariadb__log_slave_updates: false
# mariadb__read_only: false
# mariadb__sql_mode: "NO_ENGINE_SUBSTITUTION,TRADITIONAL"

# * InnoDB
#
mariadb__default_storage_engine: InnoDB
# mariadb__innodb_log_file_size: 50M
mariadb__innodb_buffer_pool_size: 256M
mariadb__innodb_log_buffer_size: 8M
mariadb__innodb_file_per_table: 1
mariadb__innodb_open_files: 400
mariadb__innodb_io_capacity: 400
mariadb__innodb_flush_method: O_DIRECT

# * Custom
#
mariadb__custom_configs: []
#  innodb_file_format: barracuda
```

#### Example

```yaml
mariadb__version: 10.2
mariadb__root_password: Se(ureRooTp@s$word!
mariadb__databases:
  - name: database10
    state: present

mariadb__users:
  - name: user1
    host: 127.0.0.1
    password: secret
    priv: "database10.*:ALL"
    encrypted: false

mariadb__custom_configs:
  innodb_file_format: barracuda
  innodb_force_recovery: 0
```

## Example Playbook

```yaml
- hosts: all
  vars_files:
    - vars/main.yml
  roles:
     - { role: sparknsh.mariadb }
```

## License

MIT

## Author Information

This role was created in 2019 by [sparknsh](https://www.sparknsh.com) at [Rebel Media, Inc.](https://www.rebelmedia.io/)
