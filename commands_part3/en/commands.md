# Commands ubuntu part 3

## List file / directory permissions
ls -l

## The description of the permissions
- rwx r-x r-x

file/catalog - permissions for the owner (u) 

permissions for group (g) 

permissions for others (o)

owner(u-ser) group(g-roup) other(o-ther) + -

all (a-ll)

| right to access        | digital value           | numerical value |
|-------------|:-------------:|:-------------:|
| read      | r | 4 |
|record| w | 2 |
|execution| x | 1 |

## Change of owner
chown
- user

- :group

- user:group

## Change permissions
chmod
- 000 file

- 777 file

- o+wx,g+r

- ugo+w

- g-r

---

**System**

---

## Check how long the system is operating
uptime

## Check local disks are busy
df
- -h

## Check disk usage
du
- -sh (summarized per directory)

## Check RAM usage
free
- -h

---

**Manage software**

---

Linux has its own software repositories, from which we can easily install software on your system.

Repositories are special servers that store all packages (programs, packages, installations).


## apt tool
apt
- update - update the repository (check for latest versions of packages)

- upgrade - update packages installed on the system

> update recommended first

> ! We will separate each command with a semicolon: apt update; apt upgrade

- search - searches for the package in the repository

- install - (htop, mc)

- remove - will uninstall

- list --installed - lists the packages installed on the system
	
## Install htop package

[Click](https://github.com/pokczampDev/Ubuntu-guide/tree/main/installation-htop)

## Back to part 2
[Kliknij](https://github.com/pokczampDev/Ubuntu-guide/blob/main/commands_part2/en/commands.md)

## Continue to part 4
[Kliknij](https://github.com/pokczampDev/Ubuntu-guide/blob/main/commands_part4/en/commands.md)