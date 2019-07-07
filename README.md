# Ansible Role: ca-certificates

[![Build Status](https://img.shields.io/travis/arillso/ansible.ca-certificates.svg?branch=master&style=popout-square)](https://travis-ci.org/arillso/ansible.ca-certificates) [![license](https://img.shields.io/github/license/mashape/apistatus.svg?style=popout-square)](https://sbaerlo.ch/licence) [![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-ca_certificates-blue.svg?style=popout-square)](https://galaxy.ansible.com/arillso/ca_certificates) [![Ansible Role](https://img.shields.io/ansible/role/d/id.svg?style=popout-square)](https://galaxy.ansible.com/arillso/ca_certificates)

## Description

With this role you can install certificates from a file or url under Windows and Linux.

## Installation

```bash
ansible-galaxy install arillso.ca-certificates
```

## Requirements

none

## Role Variables

### ca_certificates_root_directory

Location where the certificates are stored under windows before
they are imported into the certificate memory of Windows.

```yml
ca_certificates_root_directory: '{{ ansible_env.TMP }}'
```

### ca_certificates_packages

Packages to be installed.

```yml
ca_certificates_packages:
  - ca-certificates
```

### ca_certificates_files

List of CA certificates that are to be added to the certificate memory of the system. Each list element is a configuration directory that defines the source (URL, Files or Inline as variable) of the certificate. It must contain a key'name' and one of the following keys in order to use the certificate:

| Option         | Comments                                                                                                                                                                                      |
| :------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| file           | Path to a file on the host running the Ansible playbook. Relative file paths are related to the role's `files/` directory.                                                                    |
| url            | URL to a PEM-formatted certificate file                                                                                                                                                       |
| content        | Certificate inline as PEM-formatted                                                                                                                                                           |
| store_name     | Optional in Windows. The store name to use when importing. See: [Ansible doc](https://docs.ansible.com/ansible/latest/modules/win_certificate_store_module.html#win-certificate-store-module) |
| store_location | Optional in Windows. See: [Ansible doc](https://docs.ansible.com/ansible/latest/modules/win_certificate_store_module.html#win-certificate-store-module)                                       |

```yml
ca_certificates_files: []
```

## Dependencies

None

## Example Playbook

```yml
- hosts: all
  roles:
    - arillso.ca-certificates
```

## Changelog

## Author

- [Simon Bärlocher](https://sbaerlocher.ch)

## License

This project is under the MIT License. See the [LICENSE](https://sbaerlo.ch/licence) file for the full license text.

## Copyright

(c) 2019, Arillso
