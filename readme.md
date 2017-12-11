# nexus_upload_binaries

## Description:

This role uploads binaries from a folder into Nexus.

## Behaviour:

**Feature:** Uploads binaries to Nexus
- **Given** a Nexus repository server
- **Given** a folder containing binaries
- **When** the upload is executed
- **Then** a repository is created in Nexus
- **Then** the binaries are uploaded to the repository

## Configuration:

| Variable  | Description  | Example  | 
|---|---|---|
| **tool_name**  | Name of tool binaries belong to  | GOGS |
| **cache_folder**  | Folder containing tool binaries  |  `/var/cache/{{ tool_name }}` |
| **nexus_user** | Nexus user | `deployment` |
| **nexus_user_pwd** | Nexus user password | `deployment123` |
| **nexus_repo_url** | Nexus repository URL |  |

## Usage:

How to invoke the role from a playbook:

```yaml
- name: Upload binaries to Nexus
  hosts: localhost
  connection: local
  vars:
    tool_name: 'prometeo'
    cache_folder: '/var/cache/{{ tool_name }}'
    nexus_user: 'deployment'
    nexus_user_pwd: 'deployment123'
    nexus_repo_url: 'http://nexus.repo:8081/content/repositories/{{ tool_name }}/1.0.0"'
  roles:
    - nexus_upload_binaries
```
