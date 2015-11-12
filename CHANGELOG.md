# Prelude (`prelude`) - Change log

All notable changes to this role will be documented in this file.
This role adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [Unreleased][unreleased]

## 1.0.0 - 12/11/2015

### Changed - BREAKING!

* Support for different role lists depending on whether internal resources are available, only a single, public, list
 is now supported
* Ansible roles are now installed using the '--force' option to override existing roles, this replaces previous tasks
 to list and remove roles from roles directory

### Removed - BREAKING!

* Support for resolving whether internal resources are available, it is now assumed all resources will be public
* Dependencies on NMap
* Support for specifying the roles directory, this should be set in an `ansible.cfg` file using the `roles_path` option.

### Added

* New variables to control whether aspects of this role are executed
* BARC standardised tags

### Changed

* Updated README, licensing and change log formatting and content to latest conventions

## 0.1.2 - August 2015

* Fixing support for missing a public keys directory by ensuring it exists before copying keys into it

## 0.1.1 - June 2015

* Fixing support for determining if internal resources are available to prevent failures if external
* Improving documentation

## 0.1.0 - February 2015

* Initial version
