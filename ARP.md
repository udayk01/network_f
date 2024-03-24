# 1 - Answer the following questions based on the contents of the Ethernet frame containing the HTTP GET message.

## a- What is the 48-bit Ethernet address of your computer?

48 bit Ethernet address is 00:d0:59:a9:3d:68

![image](https://github.com/udayk01/network_f/assets/52235763/8756ed20-5dd2-4b53-94e7-7fc8c7237c5e)

## b- What is the 48-bit destination address in the Ethernet frame? Is this the Ethernet address of gaia.cs.umass.edu? What device has this as its Ethernet address?

The 48-bit destination address in the Ethernet frame is 00:06:25:da:af:73. This is not the Ethernet address of gaia.cs.umass.edu.  It is the mac address for my router or internet gateway address.

![image](https://github.com/udayk01/network_f/assets/52235763/233f282d-416f-4eab-ad00-55d419aae9df)

## c- Give the hexadecimal value for the two-byte Frame type field. What upper layer protocol does this correspond to?

Type: IPv4 (0x0800)

![image](https://github.com/udayk01/network_f/assets/52235763/049747c9-8ce3-45d7-93d1-5466f2b5ef8a)

# 2 - Answer the following questions based on the contents of the Ethernet frame containing the first byte of the HTTP response message.

## a- What is the value of the Ethernet source address?

Source: LinksysG_da:af:73 (00:06:25:da:af:73)

![image](https://github.com/udayk01/network_f/assets/52235763/834c5b1d-5fad-45c0-b81f-7a07f9996fea)

## b- What is the destination address in the Ethernet frame? Is this the Ethernet address of your computer?

Destination: AmbitMic_a9:3d:68 (00:d0:59:a9:3d:68), Yes this is the Ethernet address of my computer.

![image](https://github.com/udayk01/network_f/assets/52235763/3173ca30-0694-409a-9a3a-6a82025588f5)

## c- Give the hexadecimal value for the two-byte Frame type field. What upper layer protocol does this correspond to?

Type: IPv4 (0x0800)

![image](https://github.com/udayk01/network_f/assets/52235763/03692a87-b2bb-4a6b-8ec4-22c689acda79)

# 3 - Answer the following questions based on the contents of the ARP Request packets.

## a- What are the hexadecimal values for the source and destination addresses in the Ethernet frame containing the ARP request message?

Source: AmbitMic_a9:3d:68 (00:d0:59:a9:3d:68), Destination: Broadcast (ff:ff:ff:ff:ff:ff)

![image](https://github.com/udayk01/network_f/assets/52235763/c46c22aa-53cb-48eb-84f0-c4b487a5ac4d)

## b- Give the hexadecimal value for the two-byte Ethernet Frame type field. 

Type: ARP (0x0806)

![image](https://github.com/udayk01/network_f/assets/52235763/4f7dc33e-b432-4df4-b9c2-dc55cdb65d35)

## c- How many bytes from the very beginning of the Ethernet frame does the ARP opcode field begin?

It begins 20 bytes from the beginning of the Ethernet frame

## d- What is the value of the opcode field within the ARP-payload part of the Ethernet frame in which an ARP request is made?

![image](https://github.com/udayk01/network_f/assets/52235763/5e85d2ea-9a60-4830-b370-bae300f26d50)

## e- Does the ARP message contain the IP address of the sender?

Yes, it contains the IP address of the sender.

![image](https://github.com/udayk01/network_f/assets/52235763/5af5d904-a91c-4373-8db3-a7967f92a36e)

## f- Where in the ARP request does the “question” appear –the Ethernet address of the machine whose corresponding IP address is being queried? 

The field “Target MAC address” is set to 00:00:00:00:00:00 to question the machine whose corresponding IP address (192.168.1.1) is being queried.

![image](https://github.com/udayk01/network_f/assets/52235763/5cd086dc-9583-429f-bbcd-62abd545cc01)

# 4 - Answer the following questions based on the contents of the ARP Reply packets.

## a- How many bytes from the very beginning of the Ethernet frame does the ARP opcode field begin?

The ARP opcode field begins 20 bytes from the very beginning of the Ethernet frame.

## b- What is the value of the opcode field within the ARP-payload part of the Ethernet frame in which an ARP response is made?

![image](https://github.com/udayk01/network_f/assets/52235763/8412d909-f836-4662-be03-1f56795b87c3)

## c- Where in the ARP message does the “answer” to the earlier ARP request appear –the IP address of the machine having the Ethernet address whose corresponding IP address is being queried?

Sender MAC address: LinksysG_da:af:73 (00:06:25:da:af:73)

![image](https://github.com/udayk01/network_f/assets/52235763/084a08a2-250b-49ea-b352-f1386e26f394)

## d- What are the hexadecimal values for the source and destination addresses in the Ethernet frame containing the ARP reply message?

Destination: AmbitMic_a9:3d:68 (00:d0:59:a9:3d:68)

Source: LinksysG_da:af:73 (00:06:25:da:af:73)

![image](https://github.com/udayk01/network_f/assets/52235763/9546ae34-7176-4fa9-84b3-b2f2ba57b157)

## e- There is yet another computer on this network, as indicated by packet 6 –another ARP request. Why is there no ARP reply (sent in response to the ARP request in packet 6) in the packet trace?

There is no reply in this trace, because we are not at the machine that sent the request. The ARP request is broadcast, but the ARP reply is sent back directly to the sender’s Ethernet address


















