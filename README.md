# M3UAScan

A Scanner for the M3UA protocol to detect Sigtran supporting nodes

M3UA stands for MTP Level 3 (MTP3) User Adaptation Layer as defined by the IETF SIGTRAN working group in RFC 4666. M3UA enables the SS7 protocol's User Parts (e.g. ISUP, SCCP and TUP) to run over IP instead of telephony equipment like ISDN and PSTN. It is recommended to use the services of SCTP to transmit M3UA.

M3UA uses a complex state machine to manage and indicate states it's running. Several M3UA messages are mandatory to make a M3UA association or peering fully functional (ASP UP, ASP UP Acknowledge, ASP Active, ASP Active Acknowledge).

# Why Use M3UAScan
M3UA scan is simple scanner that aims to help pentesters to identify nodes that has sctp ports opened with m3ua on top of it.

Detecting a node with M3UA is an indication that this is a  core node in a telecom infrastructure that provides signaling. This scanner could be helpful to identify signaling nodes exposed on the internet, that could be compromised and used as a gateway into the SS7 network.

One benefit could be testing if telecom nodes are hardened and only form sctp associations with the nodes that they are suppose to connect to and testing if there is some filtering done on the nodes to prevent anyone from performing sctp associations with them.

# Requirements

git clone https://github.com/L-iot/M3UAScan.git

cd in to the M3UAScan directory

then

sudo ./setup.py install

if you get an error message try

sudo python setup.py install


# Usage

Usage: m3uascan.py -l [sctp listening IP] -p [sctp listening port]-r [Remote subnet/mask] -P [Remote sctp port]-o [Output filename] 


Example: ./m3uascan.py -l 192.168.1.1 -p 2905 -r 179.0.0.0/16 -P 2906 -o output.txt

Or you can leave out "-P" and use the built-in sctp ports in the script

Disclaimer: sctp ports were taken from the SCTPscanner provided by P1Security. Along with pysctp.py. Credit goes to P1Security on both 

