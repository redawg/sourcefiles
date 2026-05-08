# sourcefiles

Configuration source files used by Ansible playbooks. Contains system configuration templates and reference files deployed to managed hosts.

---

## Contents

| File | Description |
|---|---|
| `ansible.cfg` | Ansible configuration file (connection defaults, callbacks, etc.) |
| `hosts` | Static inventory file for lab/demo environments |
| `passwd` | Reference passwd file template |
| `resolv.conf` | DNS resolver configuration template |

---

## Usage

These files are typically referenced by playbooks using `src:` in `ansible.builtin.copy` or `ansible.builtin.template` tasks. Source this repository as a project in AAP Controller and reference files by their path relative to the project root.

```yaml
- name: Deploy resolv.conf
  ansible.builtin.copy:
    src: resolv.conf
    dest: /etc/resolv.conf
    owner: root
    mode: '0644'
```

> Store only non-sensitive configuration templates here. Passwords and secrets belong in AAP Controller credential types or an external vault.
