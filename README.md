# Ansible Role: Copy Files

[![Build Status](https://api.travis-ci.org/fourforbusiness/ansible-role-copy-files.svg?branch=master)](https://api.travis-ci.org/fourforbusiness/ansible-role-copy-files)

Ensures files and templates exist on the target machine.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

`project_files`     
A list of files and/or templates to copy, each file has to have the properties
* `src` (string)
* `dst` (string)
* `mode` (symbolic and octal form)
* `force` (if the file should be overwritten if it already exists)

## Dependencies

None.

## Example Playbook

    - hosts: all
      become: yes
      vars_files:
        - vars/main.yml
      roles:
        - fourforbusiness.copy-files

*Inside `vars/main.yml`*:

    ---
    template_var: 'I am a text.'
    project_files:
      files:
        - src: "example.txt"
          dst: "~/test/example.txt"
          mode: '0755'
          force: false
      templates:
        - src: "example_template.txt.j2"
          dst: "~/test/example_from_template.txt"
          mode: '0755'
          force: false

## License

MIT / BSD

## Author Information

This role was created in 2018 by [four for business AG](https://www.4fb.de/).
