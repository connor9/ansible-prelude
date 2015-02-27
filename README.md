# Prelude (`prelude`)

**Part of the BAS Ansible Role Collection (BARC)**

Performs pre-configuration for provisioning a project on a host computer

## Overview

* Copies your public key to relevant directory in the project to ensure it used by bootstrapping roles.
* Installs required ansible roles from either internal or external sources based on their availability.

## Availability

This role is designed for internal use but if useful can be shared publicly.

## Usage

### Requirements

#### BAS Ansible Role Collection (BARC)

None.

### Variables

* `prelude_internal_resource_check`
    * A URL only available internally (i.e. within the NERC firewall) used to determine if such resources are available
    * This variable **MUST** be a valid URL or hostname that will NOT be reachable if external, i.e. blocked by a firewall
    * Default: "stash.ceh.ac.uk"
* `prelude_public_key_source`
    * The full path (including filename) to a public key file to be copied into the project for use by bootstrapping roles
    * This variable **MUST** be the path to a public key file, see 
    [these instructions](https://help.github.com/articles/generating-ssh-keys/) for details on how to create one.
    * Default: "~/.ssh/id_rsa.pub"
* `prelude_public_key_destination_name`
    * The filename the copied key will have by copying the public key specified by `prelude_public_key_source`
    * This variable **MUST** be a valid UNIX filename and **MUST NOT** already exist (if the key is different)
    * This variable **SHOULD** be unique to you, i.e. named after your username (this is what the default value does)
    * Default: "{{ ansible_env.USER }}.pub" where "{{ ansible_env.USER }}" is your username on your host computer.
* `prelude_roles_directory_path`
    * The file name (and optionally relative path) to the directory that will hold ansible roles, usually "roles"
    * You **SHOULD NOT** change this value unless you have a good reason
    * This path is relative to the playbook calling this role (i.e. `provisioning/prelude.yml`)
    * Default: "roles"
* `prelude_roles_file_path`
    * The relative path to the directory that contains the `prelude_roles_file_internal` and `prelude_roles_file_external` files
    * This path is relative to the playbook calling this role (i.e. `provisioning/prelude.yml`)
    * These files **SHOULD** be stored in the project root meaning you **SHOULD NOT** need to change this variable
    * You **MUST NOT** include a trailing slash, as this will be added automatically
    * Default: ".."
* `prelude_roles_file_internal`
    * The file name for the file listing ansible roles required if internal resources are to be used
    * This file **SHOULD** be stored in the project root meaning you **SHOULD NOT** need to change this variable
    * Default: "ansible-roles-internal.yml"
* `prelude_roles_file_external`
    * The file name for the file listing ansible roles required if external resources are to be used
    * This file **SHOULD** be stored in the project root meaning you **SHOULD NOT** need to change this variable
    * Default: "ansible-roles-external.yml"

## Contributing

This project welcomes contributions, see `CONTRIBUTING` for our general policy.

## Developing

### Committing changes

The [Git flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow/) workflow is used to 
manage development of this package.

Discrete changes should be made within *feature* branches, created from and merged back into *develop* 
(where small one-line changes may be made directly).

When ready to release a set of features/changes create a *release* branch from *develop*, update documentation as 
required and merge into *master* with a tagged, [semantic version](http://semver.org/) (e.g. `v1.2.3`).

After releases the *master* branch should be merged with *develop* to restart the process. High impact bugs can be 
addressed in *hotfix* branches, created from and merged into *master* directly (and then into *develop*).

### Issue tracking

Issues, bugs, improvements, questions, suggestions and other tasks related to this package are managed through the 
BAS Web & Applications Team Jira project ([BASWEB](https://jira.ceh.ac.uk/browse/BASWEB)).

## License

Copyright 2015 NERC BAS. Licensed under the MIT license, see `LICENSE` for details.
