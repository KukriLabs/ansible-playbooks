Restic
=========

[Restic](https://restic.net/) uses encrypted back-ups to keep a system safe in case of data loss. With remote backends supported (S3, Backblaze, Google Cloud etc.) it is recommended to keep an off-site backup or backups.

This role installs Restic system wide, creates a non-privileged user and schedules backup and cleanup jobs in Cron. It is also possible to restore files from provided repositories with experimental support to validate known SHA256 checksums of the restored files. Be aware this feature is un-tested and should not be relied upon in production.

Requirements
------------

Some files to be backed up.

Role Variables
--------------

See all variables defined in `defaults/main.yml` which can be overwritten as necessary.

Dependencies
------------

_None_

Example Playbook
----------------

    - hosts: monitoring
      roles:
        - restic
      vars:
        restic_repo: s3:s3.amazonaws.com/backup_bucket_name
        restic_repo_friendly_name: s3-configuration
        restic_password: !vault |
            $ANSIBLE_VAULT;1.1;AES256 [....]
        restic_repo_credential_env_vars:
          AWS_ACCESS_KEY_ID: !vault |
            $ANSIBLE_VAULT;1.1;AES256 [....]
          AWS_SECRET_ACCESS_KEY: !vault |
            $ANSIBLE_VAULT;1.1;AES256 [....]

License
-------

The MIT License (MIT)

Copyright (c) 2018 Ewan Jones of Kukri Labs

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

Author Information
------------------

Ewan Jones for Kukri Labs

https://keybase.io/ejones
