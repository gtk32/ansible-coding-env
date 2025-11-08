Role Name
=========

Ansible-coding-env is a development environment especially designed for proper writing Ansible playbooks. It sets up a lean, 
keyboard-driven workflow centered around Vim, ansible-dev-tools, and Lazygit, providing a smooth experience for automation engineers 
who prefer a terminal-based setup as a replacement for Visual Studio Code.

Requirements
------------

The playbook is tested on RHEL 9 & 10 and Fedora 43. Please be aware that additional LSP functionallity is not supported by RHEL 9. This lies in the fact that RHEL 9 doesn't have vim >= 9 in the repositories. For LSP support and specifically ansible-language-server support, the LSP plugin coc.nvim is needed which works only for vim version >= 9.


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
# Installation of coc.nvim LSP
cd ~/.vim/vimrc/plugged/coc.nvim && npm ci # Installation of coc.nvim LSP

# In vim
:CocInstall @yaegassy/coc-ansible
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
| `L` | Next buffer |
| `H` | Previous buffer |
| `<space>fs` | Grep current string |
| `<space>fg` | Grep input string |
| `<space>fc` | Grep for current file name (without extension) |
| `<space>fi` | Find files in your Vim config |
| `<C-/=` | Comment / Uncomment line |
| `K` | Show documentation in preview window |
| `P` | Show all diagnostics |

Software
--------
- [Ansible-dev-tools](https://github.com/ansible/ansible-dev-tools)
- [Ansible language server](https://github.com/yaegassy/coc-ansible)
- [Vim](https://github.com/vim/vim)
- [Lazygit](https://github.com/jesseduffield/lazygit)
