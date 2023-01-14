# Commands ubuntu part 1

## Link to directory structures:
[structures](http://www.mtitek.com/tutorials/linux/filemgmt_path.php) or [structures 2](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

## Help
man

--help

## Navigate through the directory tree

cd - change directory
- /

- /var/log

- . (that is the directory in which you are located)

- .. (directory up)

- ~ (returning to home)

pwd - displays the current directory

## Catalog Content Listings

ls
- l (as a list)

- la (shows hidden files - starting with **.**)

- lA (shows the hidden files but hides the tedious **.** directory and the directory above **.**)

- lR (shows the list recursively - displays the contents of the directories inside)

## View and search the contents of files
cat - displays the contents of the files

grep (word) (file) - searches for the word in the files you specify

- -i (does not draw attention to case)

cat file | grep word - searches for a word in the pipeline containing the contents of the files

grep "phrase*" "*/*" - searches for a phrase that starts with "phrase" in all files in this directory (inside the directories)

head - displays the first lines of the file
- -n (the number of rows specified)

tail - displays the last lines of the file

- -n (the number of rows specified)

- -f (refreshes as soon as something jumps into the file)

> Useful for keeping track of logs

more - interactive file browsing

## Create directories
mkdir
- -p (whole tree)

- several directories are separated by a space

## Create or edit files
nano - text editor

touch

## Copy and move files and directories
cp (source) (destination) - copy files or directories

- -r (recursively, whole directory)

mv (source or old file name) (destination or new file name) - move files or directories and rename the file or directories
- -r (recursively, whole directory)

## Delete files and directories
rm
- -r (used for catalogs)

rm -r catalog/* (will erase all catalog content)

## Search files
find (where) -name (file name)

> e.g. find /home/ubuntu --name file_1

## Host

Disable / turn off:

- shutdown -h now

Restart:

- reboot

System operating time / uptime:

- uptime

##

^ = Ctrl

^+l - clear the screen / terminal (small L)

Tab - auto fill

We label one letter parameters -,
longer parameters are marked --

> e.g. -r, --name

## Continue to part 2
[Click](https://github.com/pokczampDev/Ubuntu-guide/blob/main/commands_part2/en/commands.md)