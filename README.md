# Ansible Role: Bacula Client

Ansible role for Bacula client (aka file daemon) (Gentoo). 

## Requirements

None.

## Role Variables

    # Name of the client (aka file daemon).
    bacula_client_name: "{{ inventory_hostname }}"

    # Port to listen for the directory.
    bacula_client_port: 9102

    # Maximal number of concurrent jobs that is client allowed to run.
    bacula_client_max_concurrent_jobs: 20

    bacula_director_name: 'bacula-dir'
    bacula_director_port: 9101
    bacula_director_address:
    bacula_director_password:

    bacula_monitor_name: "{{ bacula_director_name }}"
    bacula_monitor_password: "{{ bacula_director_password }}"

    # The user to run bacula-fd as.
    bacula_user: bacula

    # Allow bacula-fd to keep readall permission (CAP_DAC_READ_SEARCH) when
    # dropping privileges. If you run bacula-fd as a non-root user, this allows to
    # bypass file and directory read permission checks, so Bacula will be able to
    # backup even files which the bacula user has no permission to read.
    bacula_fd_allow_read_all: "{{ bacula_user != 'root' }}"

## Dependencies

None.

## Example Playbook

    - hosts: front
      roles:
        - { role: steamulo.bacula-client }

## License

MIT

## Author Information

Steamulo - www.steamulo.com

Forked from [gentoo-ansible](https://github.com/gentoo-ansible)