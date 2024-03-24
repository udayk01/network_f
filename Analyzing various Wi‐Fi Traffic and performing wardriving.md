# 1.Capture various Wi-Fi traffic as per the below instructions 

## a) Open Wi-Fi (No Password) -Personal

![image](https://github.com/udayk01/network_f/assets/52235763/1cb3da4a-3d65-4f74-a84f-80406418a9aa)

b) Wi-Fi with WPA2 –Personal (As an insider)

![image](https://github.com/udayk01/network_f/assets/52235763/ee46ba73-722c-48eb-ac15-fc7f47f25589)

c) Wi-Fi with WPA2 –Personal (As an outsider)

![image](https://github.com/udayk01/network_f/assets/52235763/6af0d8a1-208e-4243-a482-d0da65399808)

d) Wi-Fi with WPA3 –Personal

e) Wi-Fi with WPA2 –Enterprise

![image](https://github.com/udayk01/network_f/assets/52235763/6fbb8102-0893-4690-976a-30eacb7a7e29)

# 2. Analyze the given parameters for each of the traffic files captured.

## a) Analyze the Wi-Fi header parameters for each of the traffic files captured.

**- Open Wi-Fi (No Password) -Personal**

![image](https://github.com/udayk01/network_f/assets/52235763/d6efc48b-0c9b-4321-a5de-9a7a5c49ba51)

**- Wi-Fi with WPA2 –Personal (As an insider)**

**Probe Request**

![image](https://github.com/udayk01/network_f/assets/52235763/ebf45214-c507-4993-896d-0e4100c9d199)

**Probe Response**

![image](https://github.com/udayk01/network_f/assets/52235763/f130d6a6-c740-44df-be28-3ec0d63fbc81)

**Authentication Request**

![image](https://github.com/udayk01/network_f/assets/52235763/86800088-038c-47f2-8521-4eb2ce4e31c8)

**Authentication Response** 

![image](https://github.com/udayk01/network_f/assets/52235763/af8aa008-1e11-47a1-8883-1b88ff1917ba)

**Association Request**

![image](https://github.com/udayk01/network_f/assets/52235763/d5f65da3-5ccf-4a1b-be6e-7ac80bd98db5)

**Association Response**

![image](https://github.com/udayk01/network_f/assets/52235763/7cfdca20-4c74-421b-82d7-9fc3074c3dca)

**- Wi-Fi with WPA2 –Enterprise**

**Beacon Frame**

![image](https://github.com/udayk01/network_f/assets/52235763/d1641c7b-3c8c-4aa7-845e-e06665f7aed4)

**Probe Response**

![image](https://github.com/udayk01/network_f/assets/52235763/468fd0fc-8db4-44e8-9827-39eb95c580ec)

**Acknowledgement**

![image](https://github.com/udayk01/network_f/assets/52235763/35a9e224-8361-43be-a13d-a4ba174f9f68)

**Authentication**

![image](https://github.com/udayk01/network_f/assets/52235763/89b50a36-1171-4fda-b53a-4a8873af1f00)

**Request Identify**

![image](https://github.com/udayk01/network_f/assets/52235763/7271a50c-5c45-4bf4-ab96-b5cc3263f956)

**Response Identify**

![image](https://github.com/udayk01/network_f/assets/52235763/9a5f73f6-836e-40b7-bee7-a6353b06145e)

**Start**

![image](https://github.com/udayk01/network_f/assets/52235763/faa85e17-5f3b-405d-8fce-2ba9810041b0)

## b) Capture the 4-way handshake of wpa2 and analyze the various keys transmitted during the process. 

- Wi-Fi with WPA2 –Personal (As an insider)

![image](https://github.com/udayk01/network_f/assets/52235763/a12e24bb-956e-45a4-8660-a980a8079cf7)

4-way handshake which has EAPOL protocol.

- Wi-Fi with WPA2 –Personal (As an outsider)

Since we are an outsider we are not able to capture the handshake process.

- Wi-Fi with WPA2 –Enterprise

![image](https://github.com/udayk01/network_f/assets/52235763/e61018ec-9ad9-439e-bdb1-b68582c1e9ec)

## c) After capturing the traffic as an outsider, with the available information, try to identify the Wi-Fi header details.

**- Wi-Fi with WPA2 –Personal (As an outsider)**

**Beacon Frame**

![image](https://github.com/udayk01/network_f/assets/52235763/c8764400-5b39-4275-a8dd-cd28c2cfc019)

**Probe Request**

![image](https://github.com/udayk01/network_f/assets/52235763/2fc17b31-6855-4bda-a33a-e9122ffe8ee6)

**Probe Response**

![image](https://github.com/udayk01/network_f/assets/52235763/d495918b-d95d-4021-8a24-92886c06218f)

**Acknowledgement**

![image](https://github.com/udayk01/network_f/assets/52235763/995b676c-617c-4dfb-84c3-8cf35cb365cd)

**Client making HTTPS request using web browser**

![image](https://github.com/udayk01/network_f/assets/52235763/e7de34cd-b756-4477-8f83-bc56c60ed736)

## e) Capture other devices' traffic in open Wi-Fi and try to find its risks. 

![image](https://github.com/udayk01/network_f/assets/52235763/413c608e-43f3-4e04-b2af-e64129a9df15)

we were able to monitor the packet send by another person in the same network

## f) Mark your observations on the difference between wpa2 personal and wpa2 enterprise on the protocol level using the traffic captured. 

Main difference is the credentials used.

**WPA-2 Personal**

![image](https://github.com/udayk01/network_f/assets/52235763/642aaa66-13ca-49c1-b23c-c0302087daf7)

**WPA-2 Enterprise**

![image](https://github.com/udayk01/network_f/assets/52235763/b743646a-d572-43b7-9956-101c8ec0bd2b)

# 3. Perform wardriving using Wigile (Mobile application)and record your observations on various technical and sensitive details related to Wi-Fi which are available public.

[3. WigleWifi_20231116102324.csv](https://github.com/udayk01/network_f/files/13380510/3.WigleWifi_20231116102324.csv)

We are able to see the latitude and longitude location of the Access Point.

We are also able to see the Channel in which the Access Point is broadcasting the beacons.

We are able to see the AuthMode and MAC address of the Access Point.

The KML file was imported to Google Earth and the location of the different access points were seen in the map.

![image](https://github.com/udayk01/network_f/assets/52235763/53e1f411-9c41-44a7-bd17-bfe06ce679ba)





