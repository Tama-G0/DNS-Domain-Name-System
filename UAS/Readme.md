## UAS Komunikasi Jaringan 2024
Question below are based on the trace file tcp-ethereal-trace-1
in http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip

Answer the following questions for the TCP segments:
### 1.	What is the IP address and TCP port number used by your client computer (source) to transfer the file to gaia.cs.umass.edu?
Answers:
This solution involves the client computer as the source, with an IP address of 192.168.1.102 and using TCP port number 1161 to connect or send data as per the needs of the regulated network.

![image](https://github.com/user-attachments/assets/9e8c704e-4f9e-4347-83d2-30a950e10bfe)


Figure 1: IP addresses and TCP port numbers of the client computer (source) and gaia.cs.umass.edu

### 2.	What does gaia.cs.umass.edu use the IP address and port number to receive the file. (Attach the screenshot of your Wireshark's display)
Answers:
The destination computer in this process is gaia.cs.umass.edu, with an IP address of 128.119.245.12 and uses TCP port 80 to accept connections or data transfers according to the network configuration.

![image](https://github.com/user-attachments/assets/ed269d29-a3fa-4c02-b83e-8b861b78ca5b)

Figure 2: IP addresses and destination port numbers of the gaia.cs.umass.edu

###  3.	What is the sequence number of the TCP SYN segment that is used to initiate the TCP connection between the client computer and gaia.cs.umass.edu? What is it in the segment that identifies the segment as a SYN segment? (Attach the screenshot of your Wireshark's display)
Answers:
In this trace, the sequence number of the TCP SYN segment used to initiate the TCP connection between the client computer and gaia.cs.umass.edu is 0. The SYN flag set to 1 indicates that this segment serves as the SYN segment to initiate the three-way handshake process, which is the first step in establishing a reliable TCP connection.

![image](https://github.com/user-attachments/assets/82246846-2e00-499a-bb17-82426963165c)

Figure 3: Sequence number of the TCP SYN segment

### 4.	What is the sequence number of the SYNACK segment sent by gaia.cs.umass.edu to the client computer in reply to the SYN? What is the value of the ACKnowledgement field in the SYNACK segment? How did gaia.cs.umass.edu determine that value? What is it in the segment that identifies the segment as a SYNACK segment? (Attach the screenshot of your Wireshark's display)

![image](https://github.com/user-attachments/assets/3654f4b7-2a3e-41d9-ad3f-8de4b8d8ecf6)

Figure 4: Sequence number and Acknowledgement number of the SYNACK segment

### 5.	What is the sequence number of the TCP segment containing the HTTP POST command? Note that in order to find the POST command, you’ll need to dig into the packet content field at the bottom of the Wireshark window, looking for a segment with a “POST” within its DATA field.(Attach the screenshot of your Wireshark's display)
Answers:
Segment number 4 in this communication trace is a TCP segment containing the HTTP POST command, which is used to send data from the client to the server in the HTTP protocol. The sequence number in this segment has a value of 1, indicating that the data being sent starts from the second byte in the TCP data stream, as the initial sequence number of the SYN segment is usually 0. This indicates that this segment is part of a data stream that has successfully gone through the TCP connection initialization process.

![image](https://github.com/user-attachments/assets/4a479ae5-a364-4bca-81f9-d8833777f754)

Figure 5: Sequence number of the TCP segment containing the HTTP POST command

### 6.	Consider the TCP segment containing the HTTP POST as the first segment in the TCP connection. What are the sequence numbers of the first six TCP connection segments (including the HTTP POST segment)? At what time was each segment sent? When was the ACK for each segment received? Given the difference between when each TCP segment was sent, and when its acknowledgement was received, what is the RTT value for each of the six segments? What is the EstimatedRTT value (see page 237 in textbook) after the receipt of each ACK? Assume that the value of the EstimatedRTT is equal to the measured RTT for the first segment, and then is computed using the EstimatedRTT equation on page 237 for all subsequent segments.
Note: Wireshark has a nice feature that allows you to plot the RTT for each of the TCP segments sent. Select a TCP segment in the “listing of captured packets” window that is being sent from the client to the gaia.cs.umass.edu server. Then select: Statistics->TCP Stream Graph->Round Trip Time Graph.

Answers:
The HTTP POST segment is considered as the first segment. Segments 1 – 6 are No. 4, 5, 7, 8, 10, and 11 in this trace respectively. The ACKs of segments 1 – 6 are No. 6, 9, 12, 14, 15, and 16 in this trace.
Segment 1 sequence number: 1 
Segment 2 sequence number: 566 
Segment 3 sequence number: 2026 
Segment 4 sequence number: 3486
Segment 5 sequence number: 4946 
Segment 6 sequence number: 6406

![image](https://github.com/user-attachments/assets/af3379d5-130b-43ef-a214-1b7dd64419cb)

EstimatedRTT = 0.875 * EstimatedRTT + 0.125 * SampleRTT
EstimatedRTT after the receipt of the ACK of segment 1:
EstimatedRTT = RTT for Segment 1 = 0.02746
EstimatedRTT after the receipt of the ACK of segment 2:
EstimatedRTT = 0.875 * 0.02746 + 0.125 * 0.035557 = 0.0285
EstimatedRTT after the receipt of the ACK of segment 3:
EstimatedRTT = 0.875 * 0.0285 + 0.125 * 0.070059 = 0.0337
EstimatedRTT after the receipt of the ACK of segment 4:
EstimatedRTT = 0.875 * 0.0337+ 0.125 * 0.11443 = 0.0438
EstimatedRTT after the receipt of the ACK of segment 5:
EstimatedRTT = 0.875 * 0.0438 + 0.125 * 0.13989 = 0.0558
EstimatedRTT after the receipt of the ACK of segment 6:
EstimatedRTT = 0.875 * 0.0558 + 0.125 * 0.18964 = 0.0725

![image](https://github.com/user-attachments/assets/bce8582a-acc6-4249-ac85-472d4c079114)

Figure 6: Round Trip Time Graph

### 7.	What is the length of each of the first six TCP segments?(Attach the screenshot of your Wireshark's display)
Answers:
The length of the first TCP segment, which contains the HTTP POST command, is 565 bytes. This segment is smaller than the following segments because in addition to containing the application data, it also contains the TCP header used to continue communication. After that, there are five additional TCP segments, each with a length of 1460 bytes, which correspond to the Maximum Segment Size (MSS) agreed upon during TCP connection negotiation. MSS is used to ensure that the segment size does not exceed the maximum limit that can be handled by the network, thus avoiding data fragmentation and improving delivery efficiency in the network.

![image](https://github.com/user-attachments/assets/5320e244-b1fc-440d-8d91-4866273028d7)

Figure 7: Lengths of segments
