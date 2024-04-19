<p align="center">
<img src="https://i.imgur.com/CtGfsq8.png" alt="osTicket logo"/>
</p>

<h1>Building Intuition for DNS</h1>
In this lab we will be experimenting with DNS. This lab will help us have a better understanding of DNS.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Active Directory Virtual Machine
- Client Machine joined to your domain

<h2>Lab Steps</h2>
<p>
</p>
<p>
I created an A record on DC-1 for "mainframe" and had it point to DC-1's private IP address. If we try to ping "mainframe" without setting the DNS record, it will not work at all. When we ping "mainframe" Client-1 is checking the DNS cache, the local host file as well as the DNS server. An A record is a hostname to IP address mapping. If I go back to the client machine and ping mainframe, it will actually reply. 


![image](https://github.com/MatthewTulloch/dns/assets/165750459/4435f35d-e0bb-41a4-a5e4-9f2d588705cf)

![image](https://github.com/MatthewTulloch/dns/assets/165750459/711b2b19-bc99-402e-b70b-35c3e9da4156)





After this, I changed the record address of "mainframe" to 8.8.8.8. Despite this though I went back to the client machine, it still kept pinging the old address. That is because I had to flush the DNS with the command ipconfig /flushdns. This flushes/clears the DNS cache, when I attempted to ping mainframe again the address of the new record worked this time. 

![image](https://github.com/MatthewTulloch/dns/assets/165750459/07316c9a-6dff-44e8-9426-b728cab1b203)

![image](https://github.com/MatthewTulloch/dns/assets/165750459/d992f744-ddd1-4dc2-aa8d-e8ec3a1d0e6d)




Finally, I configured a CNAME record that points the host "search" to "www.google.com". If I were to just ping "search", ping will not be able to find the host. I have to go back into the DNS tool on DC-1 and make the CNAME record "search". Now that this has been created, the CNAME record is here and if I were to ping "search" it will resolve to www.google.com's IP Address.

![image](https://github.com/MatthewTulloch/dns/assets/165750459/8d5f2bd5-749a-4d7d-b266-390c4306f5dc)

![image](https://github.com/MatthewTulloch/dns/assets/165750459/160de2f4-c9f7-4849-8879-3a1cdb5efc54)



<p>
