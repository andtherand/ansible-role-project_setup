# Ansible project_setup role

This role creates users, groups and folders specific to a project.

## Requirements

None.

## Role variables

The following variables are available:

```yaml
project_user: mychiara
```
String: The project user you want to be the owner of the folders and files you are using.
Creates a user with a home directory: e.g. ```/home/mychiara```.
No default, because it's highly project specific

```yaml
project_folder_group: 'www-data'
```
String: The group a specific folder is owned by. 
No default, because it's highly project specific

```yaml
project_user_groups: 
  - root
  - deploy
  - www-data
```
Array: The list of groups the above mentioned user is part of.
Again there are no defaults.

```yaml
project_folders: 
  - /home/mychiara/my_project
  - /home/mychiara/my_project_data
```
Array: List of project folders that are going to be created

## Tags

This role makes vivid use of tags.
The following tags are available:

- project-setup
- folders
- groups
- user

## Example playbook


```yaml
---
- name: create-project-structure
  hosts: all
  remote_user: root
  sudo: yes
  roles:
    - role: mychiara.project_setup
      project_user: mychiara
      project_groups:
        - deploy
        - root
        - www-data
      project_folder_group: www-data
      project_folders: 
        - /home/mychiara/my_project
        - /home/mychiara/my_project_data
```

## Contributing

In lieu of a formal styleguide, take care to maintain the existing coding style. Would be create if you added unit tests, that's on my todo list aswell :]

1. Fork it
2. Create your feature branch (git checkout -b feature/my-cool-new-feature)
3. Commit your changes (git commit -am 'Add some feature')
4. Push to the branch (git push origin feature/my-new-feature)
5. Create new Pull Request

## License

Copyright (c) mychiara | svs under the GPLv2 license.