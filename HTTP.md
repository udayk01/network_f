# 1
  1- Is your browser running HTTP version 1.0 or 1.1? What version of HTTP is the server running?
     
The browser and the server seems to be running in HTTP 1.1 as per my observation.
![image](https://github.com/udayk01/network_f/assets/52235763/caa79b08-5d59-450b-9322-d99be69a1ba1)

  2- What languages (if any) do your browser indicate that it can accept to the server? 

Languages used:-  en-US
![image](https://github.com/udayk01/network_f/assets/52235763/546adbc9-ad98-4a94-be8a-ff2641889778)

  3- What is the IP address of your computer? Of the gaia.cs.umass.edu server? 

MY IP- 192.168.190.138 
Destination IP (gaia.cs.umass.edu)- 128.119.245.12
![image](https://github.com/udayk01/network_f/assets/52235763/5700deca-cfc6-41df-a678-05d63e1c070a)

  4- What is the status code returned from the server to your browser? 

Status Code- 200
![image](https://github.com/udayk01/network_f/assets/52235763/8d4cb713-1b3f-441d-8478-cab9d2963747)

  5- When was the HTML file that you are retrieving last modified at the server?

Last Modified- Sat, 05 Aug 2023 05:59:02 GMT
![image](https://github.com/udayk01/network_f/assets/52235763/c0ff7964-f97b-4971-8528-12ed6c83bea6)

  6- How many bytes of content are being returned to your browser?

Data Bytes- 128 Bytes
![image](https://github.com/udayk01/network_f/assets/52235763/e90cfc12-2236-4077-a664-bfdf9731898b)

  7- By inspecting the raw data in the packet content window, do you see any headers within the data that are not displayed in the packet-listing window? If so, name one.

No, as the content displayed in both the line based header and webpage are similar, we can say that all contents are displayed and none of them are encrypted. 
![image](https://github.com/udayk01/network_f/assets/52235763/fa82c169-e77e-4b8c-b669-8ba6f82d83df)


# 2
  8- Inspect the contents of the first HTTP GET request from your browser to the server. Do you see an “IF-MODIFIED-SINCE” line in the HTTP GET? 

NO,
![image](https://github.com/udayk01/network_f/assets/52235763/67a92789-8b7d-47af-aefd-a8b18d240324)

  9- Inspect the contents of the server response. Did the server explicitly return the contents of the file? How can you tell? 

Yes, the server returned all the contents, since the content is visible in the Line-Based text data. 
![image](https://github.com/udayk01/network_f/assets/52235763/b7b31845-eb48-4cf2-8c23-28f0535b7da8)

  10- Now inspect the contents of the second HTTP GET request from your browser to the server. Do you see an “IF-MODIFIED-SINCE:” line in the HTTP GET? What information follows the “IF-MODIFIED-SINCE:” header?

Yes, the information is "Sat, 05 Aug 2023 05:59:02 GMT\r\n"
![image](https://github.com/udayk01/network_f/assets/52235763/e7b75ca0-05a9-4c48-9a65-1fc22c1245bb)

  11- What is the HTTP status code and phrase returned from the server in response to this second HTTP GET? Did the server explicitly return the file’s contents? Explain.

Status Code- 304

Response Phrase- Not Modified

The server didn't return any  file's contents since the browser loaded it from cache.
![image](https://github.com/udayk01/network_f/assets/52235763/08bbe666-e293-46b8-a107-b81e81a38daa)

# 3

  12- How many HTTP GET request messages did your browser send? Which packet number in the trace contains the GET message for the Bill or Rights? 

No. of HTTP GET requests- 1
Packet No.1499 contains GET message for Bill.
![image](https://github.com/udayk01/network_f/assets/52235763/16bac260-e145-4b9a-b4c6-acaad5856573)


  13- Which packet number in the trace contains the status code and phrase associated with the response to the HTTP GET request? 

Packet no.1613 contains status code (200) and phrase (ok) associated with the response to the HTTP GET request.
![image](https://github.com/udayk01/network_f/assets/52235763/6f8084cd-a1cb-4650-b204-3cc8caca2014)

  14- What is the status code and phrase in the response? 

Status Code- 200

Phrase- OK

![image](https://github.com/udayk01/network_f/assets/52235763/dab0bce0-7e0a-4966-a738-6b65672cbfa5)

  15- How many data-containing TCP segments were needed to carry the single HTTP response and the text of the Bill of Rights?

![image](https://github.com/udayk01/network_f/assets/52235763/a8c59920-0831-4f0b-aa27-84ed9a88d70f)

# 4

 16- What is the server’s response (status code and phrase) in response to the initial HTTP GET message from your browser? 

Status Code- 401

Phrase- Unauthorized

![image](https://github.com/udayk01/network_f/assets/52235763/b084d62a-709f-4f6e-9d81-d660979334a7)

  17- When your browser sends the HTTP GET message for the second time, what new field is included in the HTTP GET message?

New Field- Authorization 
![image](https://github.com/udayk01/network_f/assets/52235763/1e31ab2b-5dc8-4413-aa08-3e33decdcd2e)

















