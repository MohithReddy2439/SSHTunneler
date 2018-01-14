											                              SSHTunneler


This is a  Linux Applications which tunnels your pc network traffic through SSH Server( if you have an account on ssh server and SSH Server has net connection )

Usage--> 

1)Make  sure httptunneler tunneler.sh httpstunneler tunneler install uninstall has executable permissions

2)Install SSHTunneler as sudo ./install  (Follow the steps)

3)Start Tunneler as "tunneler start" and stop tunneler as "tunneler stop"

4)After starting tunneler you see two messages printed on Screen which will be as follow
"Remote HTTP SOCK SERVER Running on port <port1> "

"Remote HTTPS SOCK SERVER Running on port <port2> "

note those port1 and port2 values 

5) Log into ssh server and for first time unpack remote.zip as unzip remote.zip

6) And Execute Following commands ./httpaccept <your local machine ip> <port1> &  ./httpsaccept <your local machine ip> <port2> & 

7) Local machine Ip is your pc ip which can be found using ifconfig  , and port1 and port2 values are those which are described in 4)

8) Once your work is completed stop programe as tunneler stop  , httpaccept httpsaccept programes will automatically tunrs off

9)To uninstall run sudo ./uninstall

If an error occurs check wether iptables is logging or not by looking at kernel log , check do you have any log in /var/log/iptables80.log /var/log/iptables443.log if not configure /etc/rsyslog.d/iptables*.conf while correctly and restart service 

How it works-->


1) Iptables is used to redirect pcs network traffic to server which is runned locally on a pc and packet is logged to know its true destination

2) Rsyslogd daemon is used to separate the iptables log messages from kernel log 

3) Fine now i have a server which collects my traffic and if i got an account on ssh server i can run a server to which i can send data and i can access net Hurray !!!!

4) But wait it is not that easy because you cant actually bind a port and listen to run a server on ssh logged in machine , How to get arround it ???

5) But we can connect to server from ssh logged in machine , Thats it we will run another server in our machine to which ssh server is going to connect and we will  be sending port numbers of newly opened serveron your machine ,

6) So to breif the things , If client is going to browse , we will redirect traffic to server1(say),which running on your local pc  , we will open new server  and send the port of new sever to ssh machine from server2( say ) running on local machine to which ssh machine is connected ( which I described in 5)  

7) And Thats it we have sucessfull net connection , I did this to  unblock the blocked site , we have a web filter which blocks the sites , but by luck I discovered that ssh server network traffic is not passing through web filter and this programee works there , Really to be honest if i did a google search instead of writing this I would found sshuttle programe ;(
