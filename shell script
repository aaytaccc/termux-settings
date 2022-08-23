#!/usr/local/bin/expect -f
# Password change shell script, tested on Linux and FreeBSD
# ----------------------------------
# It need expect tool. If you are using Linux use following command
# to install expect
# apt-get install expect
# FreeBSD user can use ports or following command:
# pkg_add -r -v expect
# ----------------------------------
# If you are using linux change first line
# From:
#!/usr/local/bin/expect -f
# To:
#!/usr/bin/expect -f
# -----------------------------------------------
# Copyright (c) 2006 nixCraft project 
# This script is licensed under GNU GPL version 2.0 or above
# -------------------------------------------------------------------------
# This script is part of nixCraft shell script collection (NSSC)
# Visit http://bash.cyberciti.biz/ for more information.
# -------------------------------------------------------------------------
# display usage
if {$argc!=2} {
   send_user "usage: $argv0 username password \n"
   exit
}
# script must be run by root user
set whoami [exec id -u]
if {$whoami!=0} {
   send_user "You must be a root user to run this script\n"
   exit
}
#
set timeout -1
match_max 100000
# stopre password
set password [lindex $argv 1]
# username
set user [lindex $argv 0]
# opem shell
spawn $env(SHELL)
# send passwd command
send -- "passwd $user\r"
expect "assword:"
send "$password\r"
expect  "assword:"
send "$password\r"
send "\r"
expect eof
