# 1- TCP
## a:  What is the IP address and TCP port number used by the client computer (source) that is transferring the file to gaia.cs.umass.edu?

IP: 192.168.1.102

TCP Port No.: 1161

![image](https://github.com/udayk01/network_f/assets/52235763/20461b5f-dc44-4ef1-98c1-dfdb459588a2)

## b:  What is the IP address of gaia.cs.umass.edu? On what port number is it sending and receiving TCP segments for this connection?

IP: 128.119.245.12

TCP Port No.: 80

![image](https://github.com/udayk01/network_f/assets/52235763/2d57dff3-a7fe-428e-909e-2cf32eda6a22)

## c:  What is the sequence number of the TCP SYN segment that is used to initiate the TCP connection between the client computer and gaia.cs.umass.edu? What is it in the segment that identifies the segment as a SYN segment?

[Sequence Number: 0]  [Sequence number (Raw): 232129012]

SYN FLAG SET is used to identify the segment as a SYN segment, ie the SYN flag is set to 1 and it indicates that this segment is a SYN segment.

![image](https://github.com/udayk01/network_f/assets/52235763/8fd9e531-737d-4fe4-b7cf-cd35c944aa80)

## d:  What is the sequence number of the SYNACK segment sent by gaia.cs.umass.edu to the client computer in reply to the SYN? What is the value of the Acknowledgement field in the SYNACK segment? How did gaia.cs.umass.edu determine that value? What is it in the segment that identifies the segment as a SYNACK segment?

[Sequence Number: 0]   [Sequence number (Raw): 883061785]

[Acknowledgment Number: 1]  [Acknowledgement Number (Raw): 232129013]

The value of the Acknowledgement field in the SYNACK segment is determined by gaia.cs.umass.edu by adding 1 to the initial sequence number of SYN segment from the client computer

The SYN flag and Acknowledgement flag in the segment are set to 1 and they indicate that this segment is a SYNACK segment.

![image](https://github.com/udayk01/network_f/assets/52235763/a9267af2-1191-4999-a761-2ba02d7bd2a0)

## e:  What is the sequence number of the TCP segment containing the HTTP POST command? Note that in order to find the POST command, you’ll need to dig into the packet content field at the bottom of the Wireshark window, looking for a segment with a “POST” within its DATA field.

[Sequence Number: 1]  [Sequence Number (Raw): 232129013]

![image](https://github.com/udayk01/network_f/assets/52235763/2445cad7-d7a0-4ae9-ad04-3fec6e862ecd)

## f:  Plot the RTT graph using Wireshark.

![image](https://github.com/udayk01/network_f/assets/52235763/b177be1c-79b7-45fd-a980-a58275f7be3d)

## g:  What is the length of each of the first six TCP segments (HTTP POST)?

![image](https://github.com/udayk01/network_f/assets/52235763/0536c385-1ed2-4318-8d45-442d15c108b9)

## h:  Are there any retransmitted segments in the trace file? What did you check for (in the trace) in order to answer this question?

NO, there are no retransmitted segments in the trace file. For checking the retransmission status we check the iRTT Field since they there is no change in the iRTT field of any packet so we can say that there no packet retransmission.

![image](https://github.com/udayk01/network_f/assets/52235763/12c88251-2311-4475-b837-149a59d44667)

## i:  What is the throughput (bytes transferred per unit time) for the TCP connection? Explain how you calculated this value.

We can calculate throughput by using the following equation = (Total_bytes_transferred)/time.

First note down the time and ACK of the first file upload, (ie when SEQ=1 ACK=1 and len>0) .

Time (t1):- 19:14:20.596858 

ACK(1):- 1

![image](https://github.com/udayk01/network_f/assets/52235763/a2fee50d-467d-465e-9b46-2d61fbb73741)

Now, note down the time and ACK of the final packet.

Time (t2):- 19:14:26.026211

ACK(2):- 164091 

![image](https://github.com/udayk01/network_f/assets/52235763/a7c4e920-39c8-4a3d-9545-0fb3eaefb9a6)

from above details:-

Total bytes transferred = ACK(2)-ACK(1) = 164091-1 = 164090 bytes

Time = t2-t1 = 19:14:26.026211-19:14:20.596858 = 5.429353 s

Throughput = (Total_bytes_transfered)/time = 16490/5.429353 bytes/s

ie: 30222.75 bytes/s

# 2- UDP
## j:  Select one UDP packet from your trace. From this packet, determine how many fields the are in the UDP header. Name these fields. 

There are 4 fields.

-Source Port

-Destination Port

-Length

-Checksum

![image](https://github.com/udayk01/network_f/assets/52235763/5a7c9f4a-0871-48dc-bf50-a6684521ba8f)

## k:  By consulting the displayed information in Wireshark’s packet content field for this packet, determine the length (in bytes) of each of the UDP header fields.

Source Port: 2 Bytes

![image](https://github.com/udayk01/network_f/assets/52235763/eda9a1d2-2a9d-4224-a04b-2b62bc897fac)

Destination Port: 2 Bytes

![image](https://github.com/udayk01/network_f/assets/52235763/153f4e5f-1e37-45f5-adbe-31c0696cf1fc)

Length: 2 Bytes

![image](https://github.com/udayk01/network_f/assets/52235763/fb10dc07-baa7-4906-96b3-084988d2f2ed)

Checksum: 2 Bytes

![image](https://github.com/udayk01/network_f/assets/52235763/1a81ab1a-1314-402a-a29e-f493ab1b22fb)

## l:  The value in the Length field is the length of what? Verify your claim with your captured UDP packet.

The value in the length field is the sum of the 8 header bytes, plus the 51 encapsulated data bytes.

![image](https://github.com/udayk01/network_f/assets/52235763/1ae1827f-bfa8-4ce6-825e-7b149d55445d)

## m:  What is the protocol number for UDP? Give your answer in both hexadecimal and decimal notation.

UDP protocol number-

     -Decimal: 17

     -Hexadecimal: 11

![image](https://github.com/udayk01/network_f/assets/52235763/47e5bf2f-efe4-4205-b1d5-c0851e2d5cab)

## n:  Examine a pair of UDP packets in which your host sends the first UDP packet and the second UDP packet is a reply to this first UDP packet. (Hint: for a second packet to be sent in response to a first packet, the sender of the first packet should be the destination of the second packet). Describe the relationship between the port numbers in the two packets

The source port of the UDP packet sent by the host is the same as the destination port of the reply packet, and conversely the destination port of the UDP packet sent by the host is the same as the source port of the reply packet.

![image](https://github.com/udayk01/network_f/assets/52235763/4f1db4bc-37c5-4138-9b22-6319e95f47eb)

![image](https://github.com/udayk01/network_f/assets/52235763/31bb49ab-13a8-4283-b708-ed0a6bc0eb80)
























 



