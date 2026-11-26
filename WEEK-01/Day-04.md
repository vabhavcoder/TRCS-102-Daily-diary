# Day 04 – Linux Fundamentals and Commands

## Objective
Develop familiarity with the Linux terminal, filesystem and basic administrative commands.

## Linux Filesystem

| Directory | Purpose |
|---|---|
| / | Root of the filesystem |
| /home | Regular user home directories |
| /etc | System configuration files |
| /var/log | System and application logs |
| /tmp | Temporary files |
| /usr | Installed programs and shared resources |

## Essential Commands

| Command | Purpose |
|---|---|
| pwd | Display current working directory |
| ls -la | List files, including hidden files and permissions |
| cd | Change directory |
| mkdir | Create a directory |
| touch | Create an empty file or update timestamps |
| cat | Display file contents |
| cp | Copy files |
| mv | Move or rename files |
| grep | Search text for a pattern |
| find | Search for files and directories |
| ps | Display process information |

## Practical Activity – File Management

```bash
mkdir -p ~/cyber-lab/week1
cd ~/cyber-lab/week1
pwd
printf 'Cybersecurity learning notes\n' > notes.txt
ls -la
cat notes.txt
cp notes.txt backup.txt
mv backup.txt notes-backup.txt
grep -in 'cybersecurity' notes.txt
find . -name '*.txt'
ps aux | head
```

## Expected Results
The lab directory should contain the original notes file and its renamed backup. The search commands should identify matching text and files.

## Practical Evidence
Attach an actual terminal screenshot and record any errors encountered and their solutions.

## Learning Outcomes
- Navigate the Linux filesystem using terminal commands.
- Create, copy, rename and search files.
- Understand the role of terminal commands in security administration.

## Conclusion
Linux command-line knowledge is essential for security testing, automation, system administration and log analysis.

*Status: Self-study notes and proposed practical; record completion and actual date after performing the activity.*
