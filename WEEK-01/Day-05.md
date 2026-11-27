# Day 05 – Linux Permissions and User Management

## Objective
Understand Linux access control, file ownership and the principle of least privilege.

## Linux File Permissions
Linux defines permissions for the owner, group and other users.

| Permission | Symbol | Numeric value |
|---|---|---|
| Read | r | 4 |
| Write | w | 2 |
| Execute | x | 1 |

For regular files, read allows viewing contents, write allows modification, and execute allows execution. Directory permissions have different semantics: read lists names, write permits changing entries subject to other permissions, and execute permits traversal.

## Common Permission Modes

| Mode | Owner | Group | Others |
|---|---|---|---|
| 600 | rw- | --- | --- |
| 644 | rw- | r-- | r-- |
| 700 | rwx | --- | --- |
| 755 | rwx | r-x | r-x |

## User Management Commands
- `whoami`: Display current username.
- `id`: Display user and group identifiers.
- `groups`: Display group memberships.
- `chmod`: Change file permissions.
- `chown`: Change ownership, subject to privileges.
- `sudo`: Run an authorized command with elevated privileges.
- `passwd`: Change a user password.

## Practical Activity – Access Control

```bash
mkdir -p ~/cyber-lab/week1
cd ~/cyber-lab/week1
printf 'Private lab notes\n' > private.txt
ls -l private.txt
chmod 600 private.txt
ls -l private.txt
stat private.txt
whoami
id
groups
```

**Expected result:** After applying mode 600, the permission field should begin with `-rw-------`. Only the owner has ordinary read and write permissions, subject to privileged access and other system controls.

## Principle of Least Privilege
Users and applications should receive only the permissions necessary for their tasks. Avoid unnecessary root access and overly permissive settings such as mode 777.

## Practical Evidence
Record the actual permissions before and after the change and attach a terminal screenshot.

## Learning Outcomes
- Interpret Linux permission strings and numeric modes.
- Modify permissions on personally owned files.
- Understand user identity, group membership and least privilege.

## Conclusion
Linux permissions and appropriate privilege management reduce unauthorized access and support secure system administration.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*
[← Previous Day](Day-04.md) | [Next Week →](../Week-02/Day-06.md)
