# Writeup
# Tshark

## Objective
Get hands-on with TShark to interrogate packet captures—both offline and live—by verifying your version, enumerating interfaces, configuring continuous dumps, applying capture/display filters, slicing into traces to pull out TCP header fields, counting or locating specific packets (by IP, port, flags or duplicates), and validating your findings against lab questions.

### Skills Learned

-Discovery & setup

-Verified TShark version (tshark ‐v → 3.2.3) and listed 12 interfaces (tshark ‐D)

-Continuous capture

-Used ring buffers (‐b) and autostop together to roll live captures

-Filtering

-Applied BPF capture filters (‐f) and Wireshark-style display filters (‐Y)

-Offline trace slicing

-Read only N packets (tshark ‐r demo.pcapng ‐c 29) to extract TCP flags (PSH, ACK in #29), ACK numbers (#25 → 12421) and window sizes (#9 → 9660)

-Counted packets matching criteria via display filters + nl/wc (e.g. ACK packets, SYN handshakes, IP source/dest, TCP port 3371)

-Identified the duplicate-ACK packet (packet 37)

-Live capture & analysis

-Captured traffic to/from 10.10.10.10 (tshark -f "host 10.10.10.10" -w pcap.2) while generating traffic (curl /whoami)

-Re-opened the dump to enumerate handshake packets (SYN/SYN-ACK) and count how many packets went to 10.10.10.10 (7 total)

### Tools Used

-TShark (CLI) v3.2.3

-bash pipelines (grep, nl, wc)

-curl (to generate test traffic)

-demo.pcapng, pcap.2 (lab PCAPs)

-Terminal environment (Ubuntu VM)

## Steps
---
Ref.1: Question 1
<img width="329" alt="1- question 1" src="https://github.com/user-attachments/assets/dd2122cb-c7e8-434f-a3fa-d3635db1998c" />
---
Ref.2: Tshark -v showing version
<img width="476" alt="2- thark -v showing version" src="https://github.com/user-attachments/assets/5253bf1a-4bb7-40a3-8941-398f3e5a4ed7" />
---
Ref.3: Next question
<img width="296" alt="3- question 2" src="https://github.com/user-attachments/assets/344ce6ec-f190-4db0-90f7-19d29ec75c91" />
---
Ref.4: Tshark -D showing interfaces
<img width="488" alt="4- tshark -D showing interfaces" src="https://github.com/user-attachments/assets/c1195cfb-857e-442e-9ab7-7d751663e549" />
---
Ref.5: Questions answered
<img width="336" alt="5- question answers" src="https://github.com/user-attachments/assets/88e99964-4c8b-485b-a18c-53c0decf652d" />
---
Ref.6: Next question
<img width="637" alt="6-- quesion" src="https://github.com/user-attachments/assets/d5d868d4-baea-456f-b837-c7abdaad6b72" />
---
Ref.7: Did Tshark -r -c 29 and found the answer was PSH ACK 
<img width="839" alt="7- did tshark -r -c 29 and found the answer was PSH ACK" src="https://github.com/user-attachments/assets/95d62474-d3b1-4ec5-a57a-0944767282fa" />
---
Ref.8: I was able to answer all questions as they were shown in the packet analysis
<img width="404" alt="8- i was able to answer that and the other questoins as they were shown in that last packet analysis" src="https://github.com/user-attachments/assets/752074a2-3bf4-43f6-816c-282173f7cc81" />
---
Ref.9: Looping
<img width="989" alt="9- looping" src="https://github.com/user-attachments/assets/29c150b0-4b55-4fd0-9c17-24a075b56758" />
---
Ref.10: Tshark capture and display filters
<img width="1013" alt="10- thsark capture and display filters" src="https://github.com/user-attachments/assets/bc87abf7-3543-4b6d-a7ea-4814b950f957" />
---
Ref.11: Scenario
<img width="632" alt="11- scenario" src="https://github.com/user-attachments/assets/a1f74b70-01cb-4984-b656-65cea7f00b76" />
---
Ref.12: Top running Tshark -f host -1 pcap.2 and bottom running curl
<img width="913" alt="12- top running tshark -f host -1 pcap 2 and bottom running curl" src="https://github.com/user-attachments/assets/45c20924-c013-473d-93b5-57ab61ce7ac1" />
---
Ref.13: reading the created pcap file and grepping for syn
<img width="564" alt="13- reading the created pcap file and grepping for syn" src="https://github.com/user-attachments/assets/e80064f8-7ff7-4b45-86c6-b9b087de9643" />
---
Ref.14: Next question
<img width="320" alt="14- question" src="https://github.com/user-attachments/assets/f6b24ade-8a7f-48ce-9429-df57c1f7acf2" />
---
Ref.15: Reading through pcap andn counting all ones with ip as destination, recorded 7 instances
<img width="578" alt="15- reading through pcap and counting all ones with ip as destination, recorded 7 instances" src="https://github.com/user-attachments/assets/079ef717-e1c9-4a4b-99a3-a4a3c98f1aef" />
---
Ref.16: Next question
<img width="327" alt="16 - question" src="https://github.com/user-attachments/assets/b04e0918-699d-4671-a389-2dd21c1395d3" />
---
Ref.17: Saw 8 packets with ack bytes
<img width="929" alt="17- saw 8 packets with ack bytes" src="https://github.com/user-attachments/assets/dcd199d9-3154-4d48-a693-d7c477374806" />
---
Ref.18: Questions Answered
<img width="329" alt="18- questions" src="https://github.com/user-attachments/assets/09026e1e-61d4-4059-9315-6c4891c99ea7" />
---
Ref.19: Scenario
<img width="343" alt="19- scenario" src="https://github.com/user-attachments/assets/020daaf6-ebf0-46e5-9dbf-4eafa4f08264" />
---
Ref.20: Question
<img width="338" alt="20- question" src="https://github.com/user-attachments/assets/1fa17e7b-3227-4d29-829a-fa8af4186540" />
---
Ref.21: Scanned pcap by ip and piped to number lines and got 34 with ip
<img width="906" alt="21- scanned pcap by ip and piped to number lnies and got 34 with ip" src="https://github.com/user-attachments/assets/6a0798bc-9403-458b-9cf7-9d7290c9a50a" />
---
Ref.22: Question
<img width="349" alt="22- question" src="https://github.com/user-attachments/assets/a6270840-7fe6-429f-9210-6b9ef230dc6e" />
---
Ref.23: Scanned for the port and piped to nl getting 7 lines
<img width="903" alt="23- scanned for the port and piped to nl getting 7 lines" src="https://github.com/user-attachments/assets/865c1e57-d3a7-47f2-839c-8e02729a5d86" />
---
Ref.24: Next question
<img width="338" alt="24- question" src="https://github.com/user-attachments/assets/417e7766-00e6-4bf4-9e56-444197d726cf" />
---
Ref.25 Scanned for source of ip and piped to nl getting 20 instances
<img width="900" alt="25- scanned for ip source of ip and piped to nl getting 20 instances" src="https://github.com/user-attachments/assets/de9c8e48-0e02-4297-ac03-a8ee966247ea" />
---
Ref.26: Question
<img width="370" alt="26- question" src="https://github.com/user-attachments/assets/a735bc48-7610-4159-9599-771f26856aad" />
---
Ref.27: Packet 37 shows as dup packet
<img width="889" alt="27- packet 37 shows as the dup packet" src="https://github.com/user-attachments/assets/390e1b74-1bd6-4983-9015-c11898f11729" />
---
Ref.28: Questions answered
<img width="311" alt="28- answers" src="https://github.com/user-attachments/assets/be0b416a-5c6f-4166-8df3-7de44115f8af" />
---










































