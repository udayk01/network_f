# 1
## a

![image](https://github.com/udayk01/network_f/assets/52235763/e8f3001a-7f5b-4e20-b52b-c45de9888cb3)

## b,c,d,e,f,g

![image](https://github.com/udayk01/network_f/assets/52235763/fe8b5bcd-fb8e-44a8-a86d-06e8dd8ce094)

![image](https://github.com/udayk01/network_f/assets/52235763/eace8ac9-2693-4657-9416-d7d297c49f1c)

# 2
## a

DHCP messages are sent over UDP.

![image](https://github.com/udayk01/network_f/assets/52235763/9abcf20f-38e0-4909-923d-d3d400cd626c)

## b

![image](https://github.com/udayk01/network_f/assets/52235763/eadcd44e-e20c-453e-8d82-8f25c7bc407c)

![image](https://github.com/udayk01/network_f/assets/52235763/42eedfda-02d6-493f-a259-6a79a181bd14)

## c

The link layer address is 00:08:74:4f:36:23

![image](https://github.com/udayk01/network_f/assets/52235763/13452f30-4b5d-417f-bc29-d2421ce43228)

## d

 The values which differentiate the Discover message from the Request message are in “Option: (53) DHCP Message Type (Discover)"

![image](https://github.com/udayk01/network_f/assets/52235763/8fb9d005-9c35-4a88-a75d-919a3c42c3fd)

![image](https://github.com/udayk01/network_f/assets/52235763/cc9b492a-aa2a-4699-8047-68c042bc3734)

## e

Set 1

Discover - Transaction ID 0x3e5e0ce3

Offer    - Transaction ID 0x3e5e0ce3

Request - Transaction ID 0x3e5e0ce3

ACK      - Transaction ID 0x3e5e0ce3

![image](https://github.com/udayk01/network_f/assets/52235763/58989db6-5c0b-44ad-849d-6cf876646811)

Set 2

Request - Transaction ID 0x257e55a3

ACK      - Transaction ID 0x257e55a3

![image](https://github.com/udayk01/network_f/assets/52235763/7c45419a-744e-4669-8c08-7e9916b42672)

Transaction ID is the number that keeps track of a domain query and it's corresponding response

## f

The DCHP client and server both use 255.255.255.255 as the destination address. The client uses source IP address 0.0.0.0, while the server uses its actual IP address as the source.

![image](https://github.com/udayk01/network_f/assets/52235763/e7f79abd-7134-4e2b-becd-e02eb11ac742)

## g

IP : 192.168.190.138

![image](https://github.com/udayk01/network_f/assets/52235763/c0ee5f34-0133-4ccd-a6b9-c90fa8c2bd6a)

## h

IP: 192.168.1.101

![image](https://github.com/udayk01/network_f/assets/52235763/cb15b611-f4c9-4c1c-96cd-36d2db3c70f6)

![image](https://github.com/udayk01/network_f/assets/52235763/eb2c49cf-f16b-4cea-8f79-ab9f5488c298)

## i

There is no relay agent in both the experiments.

![image](https://github.com/udayk01/network_f/assets/52235763/799a0d26-2817-429e-94a6-5912776a8433)

## j

The router line indicates to the client what its default gateway should be. The subnet mask line tells the client which subnet mask it should use.

![image](https://github.com/udayk01/network_f/assets/52235763/4373030b-1261-41e5-a74c-4be2488817ad)

## k

The client accepts the IP address given in the oﬀer message within the request message. After being oﬀered the IP address 192.168.1.110 in the oﬀer message, my client sent back a message further requesting that speciﬁc IP address.

## l

The lease time is the amount of time the DHCP server assigns an IP address to a client. During the lease time, the DHCP server will not assign the IP given to the client to another client, unless it is released by the client. Once the lease time has expired, the IP address can be reused by the DHCP server to give to another client. In my experiment, the lease time is 1 day.

![image](https://github.com/udayk01/network_f/assets/52235763/192aff8b-1ec5-459f-a0bf-c8d813da1014)

## m

The client sends a DHCP Release message to cancel its lease on the IP address given to it by the DHCP server. The DHCP server does not send a message back to the client acknowledging the DHCP Release message. If the DHCP Release message from the client is lost, the DHCP server would have to wait until the lease period is over for that IP address until it could reuse it for another client.

## n

Yes, the DHCP server will issue ARP requests. Before offering an IP address to a client, the DHCP server issues an ARP request to ensure that the offered IP address is not taken by another workstation.

![image](https://github.com/udayk01/network_f/assets/52235763/4782feeb-ef4b-42f7-b160-952ace33f435)










