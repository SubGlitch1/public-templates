# Needle

## Introduction
Preface: This is my first time making a box for a platform. Even though i followed the best practises that were outlined on your forum and playing through my box in a number of ways i am sure that there are some issues and i would appreciate honest feedback

I made this machine because most of the machines that i have played on htb that are windows dont seem to have a good defender detection. In most writeups and videos that i have watched of playthroughs even basic rev shells go through even though realistically defender should block them. I do not know however if these were exceptions. This machine is the newest (not beta) build with the most up to date defender signatures
I feel like it would be refreshing for most players while also posing a challenge.

For players who dont want to get into that i have made a insecure scheduled task that can be exploited to gain a SYSTEM shell.
Users that are more confident in their skills in AV bypass/obfuscation/crypting can load a tool like mimikatz into memory to dump the SAM and decrypt the hashes.
## Info for HTB

### Access

Passwords:

| User  | Password                            |
| ----- | ----------------------------------- |
| joseph | 1997Cats1234asdf |
| Administrator  | ijustlovecatsasd |

### Key Processes

Disclaimer: Ideally i wanted to run a full microsoft ecosystem so that users could exploit microsoft SQLs xp functions to get a shell but i wasnt able to do that because of the htb limitation that forced me to only use a max of 20gbs for the machine (even the smallest sqlserver instance is 8GB by itself). But that is more than fine ill try to get your permission to go over the limit for my next machine for which i have a really nice idea.

Running on this machine is xampp with php,mysql and apache. I havent installed anything else that isnt native to windows. 

### Automation / Crons

[Describe any automation on the box:

-The only background service that i have configured is the one that runs the "cleanup.ps1" script in c:/cleanupscripts. That service runs on startup and following that repeats every 60 seconds.
- Why? (necessary for exploit step, clean up, etc) Its the way to get SYSTEM on this machine. A user can hjack this process by injecting a rev shell into the script that gets run by SYSTEM in order to get the Admin shell
- How does it do it? I configured it over Task Scheduler

]

### Firewall Rules

Only port 80 is accesible for inbound traffic.

### Docker

Not used

### Other

[Include any other design decisions you made that the HTB staff should know about]



# Writeup

We start by opening the machine on needle.htb
There really isnt anything other than placeholder html other then the login page at needle.htb/login.php.
By trying to induce a SQL injection by trying to include a ' in the username or password parameter the user can find out the absolute path of the webdir which is:
'''
C:/xampp/htdocs/
'''
Some further heuristic tests let us know that UNION is usable. Nice this means that we can write content to arbitary files (if we have permissions).
We do

# Enumeration

[Describe the steps that describe the box's enumeration. Typically, this includes a sub-heading for the Nmap scan, HTTP/web enumeration, etc.]

# Foothold

[Describe the steps for obtaining an initial foothold (shell/command execution) on the target.]

# Lateral Movement (optional)

[Describe the steps for lateral movement. This can include Docker breakouts / escape-to-host, etc.]

# Privilege Escalation

[Describe the steps to obtaining root/administrator privileges on the box.]
