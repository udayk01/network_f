# Connections:
1.	3 routers
2.	3 switches
3.	2 end devices per network
# Concepts: 
1.	Use RIP protocol to enable the communications between all the systems
2.	Use ACL to Block the traffic from one whole network (A) to an individual host (B1) in the other network(B). Except for the individual host(B1), other hosts (B2) from that network(B) should receive the traffic from the same source network(A). 
3.	Configure telnet connection on any one of the routers. After this configuration, all systems should be able to take telnet of that router. 
4.	Create an ACL rule to block any one network from accessing only the telnet protocol of that router. But all other devices from other networks should be able to take telnet after this rule. 

## Connections-

1,2 and 3

![image](https://github.com/udayk01/network_f/assets/52235763/088a1812-e6c4-4ec6-b95b-d880c24dc0af)

## Concepts-

### 1)- Using RIP protocol, similar to the given screenshot all the routers are set up and communications are sent through them sucessfully.

![Screenshot 2023-09-12 105315](https://github.com/udayk01/network_f/assets/52235763/31dea07d-909d-4739-955d-d59c9c22ba80)

![image](https://github.com/udayk01/network_f/assets/52235763/542fc01f-1aa4-4729-9ce8-976a4280643b)

### 2)-

![Screenshot 2023-09-12 203256](https://github.com/udayk01/network_f/assets/52235763/07937199-494c-474c-9f0d-091f67a1f34d)

Here, PC0 is blocked from accessing PC2 and Laptop0 that is connected to the router 1.

![Screenshot 2023-09-12 203348](https://github.com/udayk01/network_f/assets/52235763/d68004c0-ef28-4f0d-9d69-c88a081ab893)

As we can see when PC0 is sending a message to PC2 the message sending is failed.

### 3)-

![image](https://github.com/udayk01/network_f/assets/52235763/fe4ad14c-fe4d-473f-9a88-f2899a1aca9c)

Here, telnet configured for router 2 and its accessed  from PC3. Password is set as 1234 for accessing . 

### 4)-

![image](https://github.com/udayk01/network_f/assets/52235763/8cec103c-9870-4139-bc6d-175d6fc690b1)

Here, we are blocking 192.168.20.0 from accessing the telnet configured in 192.168.40.1.







 
