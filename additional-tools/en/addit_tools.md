# Additional tools for Linux

## Find and kill the process in question
pgrep -fl **process_name**
pkill -f **process_name**

## Htop
F5 - this shortcut shows the process tree, then all you need to do is slaughter the parent process

## MTR (extended ping)
shows us ping + traceroute

> that is, it pings all the hops along the way and checks what happens during communication

## SOCAT (terminal communicator)
we start the server: 
        
    socat TCP4-LISTEN:81 STDOUT

> any port

connect with the client:

    socat - TCP4:1.1.1.1:81

> enter the IP and Port of the server

## iptraf/iftop (network connection statistics)

## | pipe (passes standard output)

3>&1 1>&2 2>&3 3>&-

> 1 - stdout

> 2 - stderr

> (-) closing descriptor

> & = descriptor, i.e. pointing to something (e.g. terminal)

> ^ - swap the order of stdout and stderror

take what is showing 1 (i.e. stdout) and make it 3 (i.e. nothing) show the same thing
take the 2 (i.e. stderr) and make it so that the 1 (i.e. stdout) shows what the 2 shows 
take what the three (our old stdout) is pointing to and make it point to what the two (stderr) is pointing to
finally, do a clean up and close descriptor three

echo "test" 1>/dev/null = send standard output (stdout) to null

## Run command after reboot in cron
instead of * specify @reboot and command