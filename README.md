# Mini Company Server on AWS EC2

I treated my Ubuntu EC2 server like a small office: users are employees, a group is a department, and a shared folder is the department's locked cabinet.

## Part 1: Users and group
Created users `sameer`, `masum` and `guest`, then a group called `Linux` with only `sameer` and `masum` as members.

Commands: `useradd`, `passwd`, `groupadd`, `gpasswd -M`, `cat /etc/passwd`, `grep Linux /etc/group`

![Users and groups]

## Part 2: Locked shared folder
Created `/home/shared`, gave it to the group with `chown`, and set `chmod 770` so only the owner and the group can enter.

Result: `sameer` (group member) could create a file. `guest` (outsider) got "can't cd to /home/shared".

Commands: `mkdir`, `chown`, `chmod 770`, `ls -ld`, `su`, `touch`

![Permission test]

## Part 3: Backup and restore
Compressed the shared folder in two formats, then restored it to prove the backup works.

Commands: `tar -czvf`, `zip -r`, `tar -xzvf`, `ls -lh`

![Backup files]
![Restore test]

## What I learned
- `770` keeps outsiders out of a folder completely
- A group is the easiest way to give several people the same access
- A backup is only useful if you test the restore

## Tools
Linux CLI, user and group management, file permissions, tar, zip, AWS EC2
