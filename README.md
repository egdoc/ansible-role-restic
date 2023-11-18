Ansible role: borgmatic
------------

This role installs restic and creates a systemd service and timer to schedule
backups to local, sftp, or rest-server repositories.

Requirements
------------

None

Role Variables
--------------

| Variable | Description | Type | Default | Required |
|----------|-------------|------|---------|----------|
| restic_repository | The URL/Path of the restic repository | str |  | yes
| restic_password   | The password of the restic resository | str |  | yes
| restic_files | List of files to be included in the backup | list | | yes
| restic_exclude_patterns | List of patterns to be excluded form the backup | list | [] | no
| restic_one_file_system | Whether restic should avoid crossing filesystems | bool | false | no
| restic_keep_hourly | Last n hourly snapshots to keep when pruning the repository | int | 0 | no
| restic_keep_daily  | Last n daily snapshots to keep when pruning the repository | int | 0 | no
| restic_keep_weekly | Last n weekly snapshots to keep when pruning the repository | int | 0 | no
| restic_keep_monthly | Last n monthly snapshots to keep when pruning the repository | int | 0 | no
| restic_keep_yearly | Last n yearly snapshots to keep when pruning the repository | int | 0 | no
| restic_backup_timer | Systemd timer OnCalendar value | str | "daily" | no
| restic_home | Home of the restic user | path | /var/lib/restic | no
| restic_config_dir | Directory containing service configuration | path | /etc/restic | no

Dependencies
------------
None.

Example Playbook
----------------

```yaml
- hosts: all
  roles:
    - role: egdoc.restic
      restic_repository: /mnt/restic
      restic_password: test
      restic_files:
        - /etc
```

License
-------

GPLv3

Author Information
------------------
Role created by Egidio Docile
