# Task 1: Network Setup

![image](https://github.com/udayk01/network_f/assets/52235763/4aa13ee2-c941-4a2f-b4c1-f9bbf8cb5f25)

In, the above we can see that CLIENT is successfully able to ping SERVER and vice-versa. 

![image](https://github.com/udayk01/network_f/assets/52235763/3a6603af-7df6-4959-94ef-172b73cb9e88)

In, the above we can see that HOST_V is successfully able to ping SERVER and vice-versa. 

![image](https://github.com/udayk01/network_f/assets/52235763/69c7313f-6c78-4376-8209-e850e2e28580)

Here, CLIENT cant ping HOST_V and HOST_V can't ping CLIENT.

# Task 2: Create and Configure TUN Interface.

## 2a- Name of the Interface

```
#!/usr/bin/python3
import fcntl
import struct
import os
import time
from scapy.all import *
TUNSETIFF = 0x400454ca
IFF_TUN = 0x0001
IFF_TAP = 0x0002
IFF_NO_PI = 0x1000
# Create the tun interface
tun = os.open("/dev/net/tun", os.O_RDWR)
ifr = struct.pack(’16sH’, b’tun%d’, IFF_TUN | IFF_NO_PI)
ifname_bytes = fcntl.ioctl(tun, TUNSETIFF, ifr)
# Get the interface name
ifname = ifname_bytes.decode(’UTF-8’)[:16].strip("\x00")
print("Interface Name: {}".format(ifname))
while True:
time.sleep(10)
```
![image](https://github.com/udayk01/network_f/assets/52235763/39e4ec37-893d-4160-b847-c13d4e8eb3ee)

![image](https://github.com/udayk01/network_f/assets/52235763/c1de3fa4-56f1-4d7f-a036-a0fb75d05343)

## 2b- Set up the TUN Interface

![image](https://github.com/udayk01/network_f/assets/52235763/146f8e1d-6821-44e4-a1f2-7afff7bbe408)

![image](https://github.com/udayk01/network_f/assets/52235763/8d735070-1709-4729-84c5-ac1452320674)

```
#!/usr/bin/python3

import fcntl
import struct
import os
import time
from scapy.all import *

TUNSETIFF = 0x400454ca
IFF_TUN = 0x0001
IFF_TAP = 0x0002
IFF_NO_PI = 0x1000

# Create the tun interface
tun = os.open("/dev/net/tun", os.O_RDWR)
ifr = struct.pack('16sH', b'uk%d', IFF_TUN | IFF_NO_PI)
ifname_bytes = fcntl.ioctl(tun, TUNSETIFF, ifr)

# Get the interface name
ifname = ifname_bytes.decode('UTF-8')[:16].strip("\x00")
print("Interface Name: {}".format(ifname))

os.system("ip addr add 192.168.53.99/24 dev {}".format(ifname))
os.system("ip link set dev {} up".format(ifname))

while True:
    time.sleep(10)
```
After running the two commands,run the "ip address" command again we can notice that ip address are assigned.

![image](https://github.com/udayk01/network_f/assets/52235763/c4ba212c-8c0a-49f4-a6ed-4c5267ffe415)

## 2c- Read from the TUN Interface

```
#!/usr/bin/python3

import fcntl
import struct
import os
import time
from scapy.all import *

TUNSETIFF = 0x400454ca
IFF_TUN = 0x0001
IFF_TAP = 0x0002
IFF_NO_PI = 0x1000

# Create the tun interface
tun = os.open("/dev/net/tun", os.O_RDWR)
ifr = struct.pack('16sH', b'uk%d', IFF_TUN | IFF_NO_PI)
ifname_bytes = fcntl.ioctl(tun, TUNSETIFF, ifr)

# Get the interface name
ifname = ifname_bytes.decode('UTF-8')[:16].strip("\x00")
print("Interface Name: {}".format(ifname))

os.system("ip addr add 192.168.53.99/24 dev {}".format(ifname))
os.system("ip link set dev {} up".format(ifname))

while True:
    # Get a packet from the tun interface
    packet = os.read(tun, 2048)
    if True:
        ip = IP(packet)
        print(ip.summary())
```

![image](https://github.com/udayk01/network_f/assets/52235763/7ddf1136-4175-413e-bea5-ab1778827971)

![image](https://github.com/udayk01/network_f/assets/52235763/45ff1dab-b08f-4895-8902-f549154d7cef)

• On Client, ping a host in the 192.168.53.0/24 network. What are printed out by the tun.py program? What has happened? Why?

The tun interface 192.168.53.99 is sending ICMP packets to the host queried 192.168.53.1. This happens because when the host is pinged, the ICMP packet would be sent through the TUN interfaceas it is in the same subnet.

• On Client, ping a host in the internal network 192.168.60.0/24, Does tun.py print out anything? Why?

Nothing is printed when ping is invoked to the 192.168.60.1. This is because the host is in an internal network, and the sent packets would not be passed to the tun interface. Since tun.py only prints when the packets are received, tun.py did not print anything in this scenario.

## 2d- Write to the TUN Interface

After getting a packet from the TUN interface, if this packet is an ICMP echo request packet, construct a corresponding echo reply packet and write it to the TUN interface. Please provide evidence to show that the code works as expected.

```
#!/usr/bin/python3

import fcntl
import struct
import os
import time
from scapy.all import *

TUNSETIFF = 0x400454ca
IFF_TUN = 0x0001
IFF_TAP = 0x0002
IFF_NO_PI = 0x1000

# Create the tun interface
tun = os.open("/dev/net/tun", os.O_RDWR)
ifr = struct.pack('16sH', b'uk%d', IFF_TUN | IFF_NO_PI)
ifname_bytes = fcntl.ioctl(tun, TUNSETIFF, ifr)

# Get the interface name
ifname = ifname_bytes.decode('UTF-8')[:16].strip("\x00")
print("Interface Name: {}".format(ifname))

os.system("ip addr add 192.168.53.99/24 dev {}".format(ifname))
os.system("ip link set dev {} up".format(ifname))

def checkIcmpReq(bytesIn):
  pktIn = IP(bytesIn)
  # check for ICMP packet
  # check for echo request type
  if (
    ICMP in pktIn and
    pktIn[ICMP].type == 8
  ):
    return True
  return False

def createIcmpReply(bytesIn):
  pktIn = IP(bytesIn)
  ipOut = IP(src=pktIn.dst, dst=pktIn.src)
  pktOut = ipOut / pktIn.payload
  # set ICMP packet type as echo reply
  pktOut[ICMP].type = 0
  return bytes(pktOut)

while True:
    # Get a packet from the tun interface
    packet = os.read(tun, 2048)
    if checkIcmpReq(packet):
        os.write(tun, createIcmpReply(packet))
```

![image](https://github.com/udayk01/network_f/assets/52235763/885cea4a-ccd8-440b-9dd1-3ab232020829)
After running the code again, the ping does not receive a valid ICMP reply, and hence shows 0 received as shown in the below screenshot.
![image](https://github.com/udayk01/network_f/assets/52235763/cb30a007-8d5a-4829-b273-c7fbe3667897)







