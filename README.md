# cyber_range
This repo is for recording and documenting my process of simulating a cyber range of 4 VMs(2 targets, 1 attacker, 1 defender/monitor).

My incident report is in this google docs link: [https://docs.google.com/document/d/11zqablkXLJ31hPv3jlnzW7BKXyux5P6-SkmAGkRYXf8/edit?usp=sharing](url) 
I will be attaching the incident report file in this repo as well.

I spun up 4 VMs via UTM. The attacker uses Kali LInux, the defender runs Splunk, Suricata(open-source IDS), and Wireshark for packet capture via Ubuntu, one target is a DVWA, and the other target is a vulnerable Linux Server(MetaSploitable 2. I would say this took up almost half the time of the whole duration of this project.

  <img width="782" height="364" alt="image" src="https://github.com/user-attachments/assets/f82e5ea5-0c5d-4822-96c4-4f558980e398" />
  <img width="643" height="394" alt="image" src="https://github.com/user-attachments/assets/28e15541-fae8-4896-8994-d72df5b34f17" />

Started off the attacks with a network scan to see what hosts are up. After identifying my target device(the metasploitable2), I do a port scan of the target, then I do a vulnerability scan on it.
  <img width="560" height="162" alt="image" src="https://github.com/user-attachments/assets/7a4940cb-a66a-41fc-b3b0-6ce49315f7f9" />
  <img width="629" height="193" alt="image" src="https://github.com/user-attachments/assets/fff987df-e6d9-43f1-8ca7-499d3abe4c64" />

Every scan I do can be seen on the Suricata Terminal(left), and the wireshark terminal(right).
  <img width="1186" height="383" alt="image" src="https://github.com/user-attachments/assets/290ef2d8-e3e0-463d-99b0-2d329c05c168" />

Set up a firefox proxy based on loopback address and set up Burp Suite for monitoring.
  <img width="1279" height="835" alt="image" src="https://github.com/user-attachments/assets/be4a2672-d0dc-4389-970d-3391c4d81c9b" />
  <img width="766" height="589" alt="image" src="https://github.com/user-attachments/assets/661c7597-5c0e-4c0c-88fe-4c4140279293" />

Performing SQL injection here
  <img width="264" height="97" alt="image" src="https://github.com/user-attachments/assets/62911645-210c-4647-918d-9bdc4079093e" />
  <img width="308" height="115" alt="image" src="https://github.com/user-attachments/assets/ad3a33ee-e3c2-4735-bb35-c03755e65b45" />
  <img width="459" height="497" alt="image" src="https://github.com/user-attachments/assets/c102c323-8ed9-46f2-9093-8b7a191cea32" />
  What happened in the SQL injection? The injection prompt made the underlying WHERE clause always true, which dumps every user records in the database.
  In this screenshot, we could see the info on the GET SQL command. The part where it says ID, is where the prompt injection took place. 

Exploited the metaploit on easy dvwa security.(didnt work properly for some reason)
<img width="865" height="646" alt="image" src="https://github.com/user-attachments/assets/21739e08-166c-41df-8399-0a4d6173e8ac" />

Exploited the samba service, and gained root shell access.
  <img width="868" height="288" alt="image" src="https://github.com/user-attachments/assets/a384f73c-de24-4914-afd1-74aed5b75b63" />


Detected activity
  <img width="1266" height="768" alt="image" src="https://github.com/user-attachments/assets/b866aa21-8f55-4b8d-aba6-f414c9849365" />
