# Linux Cheat Sheet

## Directory Commands

```
> ls

Show all files in current directory

> ls -ah

Show all files + hidden files in current directory
```

```
> pwd

Show current location
```

```
> cd

change directory

> cd ..

go up one directory
```

```
> mkdir

Create a directory

> rmdir

Remove a directory
```

## File Commands

```
> touch [file name]

Create a file

> cat [file name]

Display content of a file

> cp [file name] [path]

copy a file to another path

> mv [file name] [path]

Move a file to another path

> rm [file name]

Remove a file

> rm -r [directory]

Remove a file/folder recursively

> rm -rf [directory]

Forcefully remove a file/folder recursively

> shred [file name]

Hide the content of a file
```

```
> grep "[search string]" [file name]

find the search string in a given file

> find / -name [file name]

find a given file in a directory

> chmod [permission number - 777] [file name]

Change file permission

> chown [user] [file]

Change ownership of the file

> ln -s [link name] [file name]

Create a soft link to another file

> zip [zip file name] [file to zip]

zips a file

> unzip [zip file name]

unzips a file
```

## System Commands

```
> echo "message"

Output to terminal
```

```
> whoami

Get current user

> clear

clear terminal messages

> free

Shows how much memory is used/available

> df -h

Shows disk usage

> ps -aux

Shows all processes

> htop

Shows processes that are using the most amount of resources

> kill -9 [pid]

Force kill a process

> pkill -f [name]

Force kill a process by name

> sudo systemctl [start | status | restart] [service name]

Runs a command on a given service such as apache/docker
```

## User Commands

```
> sudo [command]

Execute command with super user permissions

> sudo useradd [user name]

Adds a new user

> su [user name]

Switches to a new user

> exit

Exits current user and goes back to root

> passwd [user name]

Changes password of a user
```

## Installation

```
> sudo apt update

updates current libraries, typically run this before installing any packages

> sudo apt install [lib name]

Installs a new deb based library

> wget [url]

Downloads a file from the internet
```

## Network Commands

```
> ip a

Shows your current ip address

> cat /etc/resolv.conf

Shows your dns server

> ping [url]

Pings a server

> traceroute [url]

Shows route that a packet takes to get to a url

> netstat

Shows what ports are open

> ufw [port]

Update firewall for a given port
```
