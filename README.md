Role Name
=========

Ansible-coding-env is a development environment especially designed for proper writing Ansible playbooks. It sets up a lean, 
keyboard-driven workflow centered around Vim, ansible-dev-tools, and Lazygit, providing a smooth experience for automation engineers 
who prefer a terminal-based setup as a replacement for Visual Studio Code.

Requirements
------------

The playbook is tested on RHEL 9 & 10 and Fedora 43.


Dependencies
------------

- [Ansible-core](https://docs.ansible.com/core.html)
- [community.general](https://docs.ansible.com/ansible/latest/collections/community/general/index.html)

Example Playbook
----------------

You can use below example to run the playbook. The playbook takes care of the installation of software and the configuration of vim.

```
---
- name: Deploy Anisble Coding Environment
  hosts: <servers>
  pre_tasks:
    - name: Gather facts
      ansible.builtin.setup:
        gather_subset: distribution
  roles:
    - role: ansible-coding-env
```
After the playbook has ran successfully, you have to perform some manual options:
```
# This triggers the first initialization whereby the plugins are cloned and installed
vim ~/.vim/vimrc
```

Key Bindings
------------

| Key | Action |
|-----|--------|
| `ZZ` | Save and quit |
| `ZQ` | Quit without saving |
| `<space>ff` | Fuzzy find files |
| `<space>fb` | Fuzzy find buffer |
| `<space>fo` | Fuzzy find history |
| `<space>fh` | Fuzzy find helptags |
| `<space>cd` | Open netrw file explorer |
| `Cntl + .` | Next buffer |
| `Cntl + ,` | Previous buffer |
| `<space>fs` | Grep current string |
| `<space>fg` | Grep input string |
| `<space>fc` | Grep for current file name (without extension) |
| `<space>fi` | Find files in your Vim config |
| `<C-/` | Comment / Uncomment line |
| `<space>nu` | Toggle between relative and absolute line numbers |

Terminal aliases
----------------
| Key | Action |
|-----|--------|
| lg | Start lagygit |
| gcb | Initiate command `git branch --show-current` |
| gab | Initiate command `git branch --all` |

Software
--------
- [Ansible-dev-tools](https://github.com/ansible/ansible-dev-tools)
- [Vim](https://github.com/vim/vim)
- [Lazygit](https://github.com/jesseduffield/lazygit)
- [Fzf](https://github.com/junegunn/fzf)
- [Ripgrep](https://github.com/BurntSushi/ripgrep)
