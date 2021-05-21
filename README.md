# role-downloader

### Master:
- Travis CI: ![TravisCI](https://travis-ci.com/osx-provisioner/role-downloader.svg?branch=master)
- Github Actions: [![role-downloader](https://github.com/osx-provisioner/role-downloader/actions/workflows/push.yml/badge.svg?branch=master)](https://github.com/osx-provisioner/role-downloader/actions/workflows/push.yml)

### Production:
- Travis CI: ![TravisCI](https://travis-ci.com/osx-provisioner/role-downloader.svg?branch=production)
- Github Actions: [![role-downloader](https://github.com/osx-provisioner/role-downloader/actions/workflows/push.yml/badge.svg?branch=production)](https://github.com/osx-provisioner/role-downloader/actions/workflows/push.yml)

Ansible role that fetches remote content and places it in a configurable location.

Requirements
------------

None


Role Variables
--------------

Each remote url can be specified in the following format:

```yaml
download_urls:
  - url: http://cdn.propellerheads.se/Reason10/Reason_1041_d4-Stable_164_10.dmg
    name: Reason10.dmg
  - url: https://fael-downloads-prod.focusrite.com/customer/prod/s3fs-public/downloads/Scarlett%20MixControl-1.10_0.dmg
    name: MixControl-1.10_0.dmg
  - url: https://www.sws-extension.org/download/featured/sws-v2.10.0.1.dmg
    name: sws-v2.10.0.1.dmg
```

The following variables are also configured:

- `download_save_user`:
    - The user to write downloaded content as.
- `download_save_location`:
    - The location to save the remote content to.
- `download_timeout`: 
    - The number of seconds of transfer inactivity before the connection is considered failed.
- `download_retries`: 
    - The number of attempts that will be made to download the file.

[See The Default Values](defaults/main.yml)

Dependencies
------------

None

Example Playbook
----------------

```yaml
- hosts: web
  roles:
  - role: osx_provisioner.downloader
    download_urls:
      - url: http://cdn.propellerheads.se/Reason10/Reason_1041_d4-Stable_164_10.dmg
        name: Reason10.dmg
      - url: https://fael-downloads-prod.focusrite.com/customer/prod/s3fs-public/downloads/Scarlett%20MixControl-1.10_0.dmg
        name: MixControl-1.10_0.dmg
      - url: https://www.sws-extension.org/download/featured/sws-v2.10.0.1.dmg
        name: sws-v2.10.0.1.dmg
```

License
-------

MPL-2

Author Information
------------------

Niall Byrne <niall@niallbyrne.ca>
