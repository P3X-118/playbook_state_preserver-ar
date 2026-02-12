# Ansible playbook state preserver role

This is an Ansible role which preserves (backs up) the `vars.yml` file and playbook git commit hash to the server. It supersedes the `com.devture.ansible.role.vars_preserver` role which only did the former.

This role *implicitly* depends on the `com.devture.ansible.role.playbook_runtime_messages` role.

## Usage

Example playbook:

```yaml
- hosts: servers
  roles:
    - when: playbook_state_preserve | bool
      role: galaxy/com.devture.ansible.role.playbook_state_preserver
      # Uncomment to make it run on some tags only, not always
      # tags:
      #  - setup-all
```

Example configuration (see `defaults/main.yml` for more):

```yaml
playbook_state_preserve_uid: 1000
playbook_state_preserve_gid: 1000

playbook_state_var_dst: /path/on-server/to/vars.yml

playbook_state_commit_hash_dst: /path/on-server/to/git_hash.yml
```
