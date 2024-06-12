# analyzing_network_attacks
Analyzing a Network Attack Using WireShark TCP/HTTP Logs

# Scenario:

You work as a security analyst for a travel agency that advertises sales and promotions on the company’s website. The employees of the company regularly access the company’s sales webpage to search for vacation packages their customers might like. 

One afternoon, you receive an automated alert from your monitoring system indicating a problem with the web server. You attempt to visit the company’s website, but you receive a connection timeout error message in your browser.

You use a packet sniffer to capture data packets in transit to and from the web server. You notice a large number of TCP SYN requests coming from an unfamiliar IP address. The web server appears to be overwhelmed by the volume of incoming traffic and is losing its ability to respond to the abnormally large number of SYN requests. You suspect the server is under attack by a malicious actor. 

You take the server offline temporarily so that the machine can recover and return to a normal operating status. You also configure the company’s firewall to block the IP address that was sending the abnormal number of SYN requests. You know that your IP blocking solution won’t last long, as an attacker can spoof other IP addresses to get around this block. You need to alert your manager about this problem quickly and discuss the next steps to stop this attacker and prevent this problem from happening again. You will need to be prepared to tell your boss about the type of attack you discovered and how it was affecting the web server and employees.

**Wireshark TCP/HTTP Log:**
<img src="https://github.com/AxelVx1/analyzing_network_attacks/blob/main/Log1.png?raw=true" alt="App Screenshot" width="600">
<img src="https://github.com/AxelVx1/analyzing_network_attacks/blob/main/Log2.png?raw=true" alt="App Screenshot" width="600">
<img src="https://github.com/AxelVx1/analyzing_network_attacks/blob/main/Log3.png?raw=true" alt="App Screenshot" width="600">
<img src="https://github.com/AxelVx1/analyzing_network_attacks/blob/main/Log4.png?raw=true" alt="App Screenshot" width="600">

# Goal:
- Identify the cause of the attack resulting in the network interruption
- Explain how the attack is causing the website malfunction

# Response:

| Identify the type of attack that may have caused this network interruption |
| -------------------------------------------------------------------------- |
|One reason the website had a connection timeout error message is that it is experiencing a high volume of traffic. The log shows an increase in activity from a specific IP address, eventually resulting in the web server overloading with SYN packet requests. This event looks to be a certain type of DoS attack called SYN flooding.  |

| Explain how the attack is causing the website to malfunction |
| ------------------------------------------------------------ |
| Normally when website visitors try to establish a connection with the web server, a three-way handshake occurs using the TCP protocol. The handshake consists of three steps:

1. First, the source sends a SYN (or synchronize) packet to the destinationto request to establish a connection

2. Then, the destination responds a SYN/ACK packet to accept the initial request and, the destination will reserve resources for the source to connect

3. Finally, the source responds with a ACK (or acknowledgment) packet to let the server now it got the permission to connect

For a SYN flood attack, a threat actor will send a large amount of SYN packets all at once. This takes ups all of the servers available resources it reserves for other connections. Then, the server can no longer accept legitimate TCP connection requests.
At first the log shows the server works by proccesing the requests from the threat actor and legitimate users. However, once the server is flooded with mailicios SYN packets it quickly overloads and is unable to open any new connections. Eventually leaving only the threat actor’s SYN packets in the log and other users receive a connection timeout message. |


