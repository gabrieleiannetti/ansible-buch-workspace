# Workspace for ansible-Buch

A workspace for learning and practicing based on the book [ansible-buch](https://github.com/ansible-buch/ansible-buch) by Axel Miesen

## Overview of Useful Commands with Options

### ansible-playbook

See `ansible-playbook -h` for more options...

| Option                          | Description                                                                                                |
| --------------------------------| -----------------------------------------------------------------------------------------------------------|
| `-l SUBSET`                     | Further limit selected hosts to an additional pattern                                                      |
| `--list-hosts`                  | Outputs a list of matching hosts                                                                           |
| `--list-tasks`                  | List all tasks that would be executed                                                                      |
| `--start-at-task START_AT_TASK` | Start the playbook at the task matching this name                                                          |
| `-i INVENTORY`                  | Specify inventory host path or comma separated host list                                                   |
| `-v, --verbose`                 | verbose mode (-vvv for more, -vvvv to enable connection debugging)                                         |
| `-f FORKS`                      | specify number of parallel processes to use (default=2)                                                    |
| `--syntax-check`                | Perform a syntax check on the playbook, but do not execute it                                              |
| `-C, --check`                   | Don't make any changes; instead, try to predict some of the changes that may occur                         |
| `-D, --diff`                    | when changing (small) files and templates, show the differences in those files; works great with `--check` |
| `--step`                        | One-step-at-a-time: confirm each task before running                                                       |
| `-t TAGS`                       | Only run plays and tasks tagged with these values                                                          |
| `--skip-tags SKIP_TAGS`         | Only run plays and tasks whose tags do not match these values                                              |
| `-e EXTRA_VARS`                 | set additional variables as key=value or YAML/JSON, if filename prepend with \@                            |

## Notes

* `direnv` (p. 42) - Ansible accesses config files when current path is within the project directory
