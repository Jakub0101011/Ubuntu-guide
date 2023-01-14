# Commands ubuntu part 2 

## Writing a pipe at the end of the file
echo "test test" >> file

## Delete all contents of the file and add a stream
echo "test test" > file

---

**Users**

---

/etc/passwd - list of all users with their information

/etc/group - list of all groups in the system

/etc/shadow - user passwords (password protected)

## Create new users
adduser

## Switch between users
su

## Checking the current user
whoami

## logout
exit

> ^ = Ctrl

> ^+d - same as exit, only that short (d)

## Delete user
deluser
- --remove-home (remove its homedir)

## Add a new system group
addgroup

## Delete a system group
delgroup

## View user groups
- groups

- groups name_user (displays the groups of another user)

- cat /etc/group | grep user

## Assign a user to a group
usermod -aG group user

> group operations require a log-in

## Delete a user from a group (specify groups without the group you are removing from)
usermod -G group1,group2 user

## Block a user account
usermod -L user
> A locked account prevents, for example, access via SSH (we will not log into the system using this account)

## Unlock a user account
usermod -U user

## Change the user password
passwd
> you can specify a user name as an argument

## Modify passwords
chage
- -l user (displays the user password information)

- -d 0 (will force the password to change)

- -M x (how long will the password be valid)

---

**Admin account = root**

---

## Perform the task as a regular user, but with root permissions
sudo

## Switches to quota account
sudo su

## Add a user to a sudo group
cat /etc/group | grep wheel or sudo

usermod -aG sudo user

sudo apt update

## Back to part 1
[Click](https://github.com/pokczampDev/Ubuntu-guide/blob/main/commands_part1/en/commands.md)

## Continue to part 3
[Click](https://github.com/pokczampDev/Ubuntu-guide/blob/main/commands_part3/en/commands.md)