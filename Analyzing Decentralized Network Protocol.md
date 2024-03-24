# 1.Download the BitTorrent software from the given link https://www.bittorrent.com/. 

![image](https://github.com/udayk01/network_f/assets/52235763/f4feb477-8747-49ba-ad88-d23528b241a8)

# 2.Then download any one Torrent file and then save it on your device. 

![image](https://github.com/udayk01/network_f/assets/52235763/0369f240-5c9f-46d2-ad27-c2eb3a14d1ba)

# 3.Open Wireshark in the background by choosing the appropriate interface.

![image](https://github.com/udayk01/network_f/assets/52235763/d01bd43a-4c99-40e0-8000-9e7bc8d472a2)

# 4.Then open your torrent file and start the download at least 20%. Stop the capture and document the answers to the following questions:

## a. Give a detailed study about the working of BitTorrent in your downloading scenario. and b. Working of BitTorrent.

The user's BitTorrent client contacts the tracker server and registers itself as a peer wanting to download/upload the file. The tracker server responds with a list of peers and seeds who are currently sharing the file or downloading it. The downloading peer selects a few peers from the list and establishes connections with them. The downloading peer requests specific pieces of the file from the connected peers. Peers respond by sending the requested pieces to the downloading peer. While downloading, the peer also starts uploading the pieces it has to other peers.

## c. Protocol Level Analysis

Handshake: Initiating communication, peers exchange handshake messages containing protocol identifiers, info_hash, and peer_id. 

Keep-Alive: Empty message sent to maintain the connection.

Choke/Unchoke: Used for flow control. Peers can stop sending or resume sending to specific peers. Interested/Not Interested: Indicate whether a peer is interested in the pieces another peer has. 

Have: Sent when a peer has downloaded a specific piece. 

Bitfield: Indicates which pieces a peer has.

Request: Sent to request a specific piece from another peer.

Piece: Contains a piece of the file requested by another peer. 

Cancel: Sent to cancel a request previously made. Port: Sent by a peer to inform about its listening port for incoming connections

## d. Tracker’s status.

![image](https://github.com/udayk01/network_f/assets/52235763/38eeb8ad-eb60-4827-9f4a-511fa67230dc)

## e. DHT status

![image](https://github.com/udayk01/network_f/assets/52235763/710cbb2c-0e83-4e4e-b063-fad41b2aa930)

DHT Status : Working.

## f. Identify other peers involved in the communication 

![image](https://github.com/udayk01/network_f/assets/52235763/a6bfce0e-774a-42f0-9902-f5ec1b9f953f)

![image](https://github.com/udayk01/network_f/assets/52235763/49f975df-48c3-42e8-91b1-65b7f50169ca)

## g. Try to identify the name of the file downloaded.

![image](https://github.com/udayk01/network_f/assets/52235763/19a33fc1-d983-49d9-83c3-81a37ad7cc4c)

File name: Ragna Crimson.......

# 5 Try to export the 20% of data you have captured as traffic in Wireshark while downloading files in Torrent.

![image](https://github.com/udayk01/network_f/assets/52235763/84419b4b-698b-47c8-a21c-cd648b8ef111)


# 6. After the Download completes and when it starts seeding, open the Wireshark and analyze the information being transferred in that traffic. Document the difference in Network traffic. 

![image](https://github.com/udayk01/network_f/assets/52235763/4186f3ca-e45f-4827-ae51-33e786cee8e3)

When the Torrent Client had not reached the Downloading state, the length of the packets with the Destination IP Address as our IP address is larger. When the Torrent Client had completed the Downloading and in the Seeding state, the length of the packets with the Source IP address as our IP address is larger.

Downloading involves more varied requests for different pieces of the file. Seeding - Seeders mainly upload pieces of the file to other peers, and the uploading traffic is usually more consistent.

