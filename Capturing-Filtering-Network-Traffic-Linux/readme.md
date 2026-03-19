# Activity Overview: Capturing and Filtering Network Traffic in Linux

As a security analyst, it’s important to understand how to capture and filter network traffic in a Linux environment. This also requires knowledge of the basic concepts associated with network interfaces.

This README documents the tasks I performed while using **tcpdump** to capture network traffic as part of the Google Cybersecurity Professional Certificate. The captured data is stored in a packet capture (p-cap) file, focusing on specific types of traffic before examining the contents.

---

## Tasks Overview
1. Identify network interfaces to capture packet data.  
2. Use **tcpdump** to filter live network traffic.  
3. Capture network traffic using **tcpdump**.  
4. Filter the captured packet data.  

---

## Task 1: Identify Network Interfaces

In this task, I identified the network interfaces that can be used to capture packet data.

### 1. Using `ifconfig`
Run the following command to list available interfaces:

```bash
sudo ifconfig
```

This command returns output similar to the following:

```bash
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1460
        inet 172.17.0.2  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:ac:11:00:02  txqueuelen 0  (Ethernet)
        RX packets 784  bytes9379957 (8.9 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 683  bytes 56880 (55.5 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0 collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 400  bytes 42122 (041.1 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 400  bytes 42122 (041.1 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0 collisions 0
```

The Ethernet network interface is identified by the entry with the eth prefix.

eth0 will be the interface to capture network packet data from in the following tasks.

### 2. Use `tcpdump` to identify the interface options available for packet capture:

```bash
sudo tcpdump -D
```

This command can also identify which network interfaces are available. This may be useful on systems that do not include the ifconfig command.


## Task 2: Inspect the network traffic of a network interface with `tcpdump`

In this task, tcpdump must be used to filter live network packet traffic on an interface.

Filter live network packet data from the eth0 interface with tcpdump:

```bash
sudo tcpdump -i eth0 -v -c5
```

This command will run tcpdump with the following options:

-i eth0: Capture data specifically from the eth0 interface.

-v: Display detailed packet data.

-c5: Capture 5 packets of data.

A detailed look at the packet information that this command will return can be similar to the following:

```bash
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
10:57:33.427749 IP (tos 0x0, ttl 64, id 35057, offset 0, flags [DF], protot TCP (6), length 134)
  7acb26dc1f44.5000 > nginx-us-east1-c.c.qwiklabs-terminal-vms-prod-00.internal.59788: Flags [P.], cksum 0x5851 (incorrect > 0x30d3), seq 1080713945:1080714027, ack 62760789, win 501, options [nop,nop,TS val 1017464119 ecr 3001513453], length 82
10:57:33.427954 IP (tos 0x0, ttl 64, id 21812, offset 0, flags [DF], protot TCP (6), length 52)
  nginx-us-east1-c.c.qwiklabs-terminal-vms-prod-00.internal.59788 > 7acb26dc1f44.5000: Flags [.], cksum 0x9122 (correct), ack 82, win 510, options [nop,nop,TS val 3001513453 ecr 1017464119], length 0
2 packets captured
4 packets received by filter
0 packets dropped by kernel
```

The specific packet data in different labs can be different due to many reasons like the different types of network traffic.
The specific details such as system names, ports, and checksums will also be different. This command can be run again to get
different snapshots to outline how data changes between packets.

### Exploring network packet details
In the following example, you’ll identify some of the properties that tcpdump outputs for the packet capture data you’ve just seen.

1. In the example data at the start of the packet output, tcpdump reported that it was listening on the eth0 interface, and it provided information on the link type and the capture size in bytes:

```bash
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
```

2. On the next line, the first field is the packet's timestamp, followed by the protocol type, IP:

```bash
22:24:18.910372 IP
```

3. The verbose option, -v, has provided more details about the IP packet fields, such as TOS, TTL, offset, flags, internal protocol type (in this case, TCP (6)), and the length of the outer IP packet in bytes:

```bash
(tos 0x0, ttl 64, id 5802, offset 0, flags [DF], proto TCP (6), length 134)
```

The specific details about these fields are beyond the scope of this lab. But you should know that these are properties that relate to the IP network packet.

4. In the next section, the data shows the systems that are communicating with each other:

```bash
7acb26dc1f44.5000 > nginx-us-east1-c.c.qwiklabs-terminal-vms-prod-00.internal.59788:
```

By default, tcpdump will convert IP addresses into names, as in the screenshot. The name of your Linux virtual machine, also included in the command prompt, appears here as the source for one packet and the destination for the second packet. In your live data, the name will be a different set of letters and numbers.

The direction of the arrow (>) indicates the direction of the traffic flow in this packet. Each system name includes a suffix with the port number (.5000 in the screenshot), which is used by the source and the destination systems for this packet.

5. The remaining data filters the header data for the inner TCP packet:

```bash
Flags [P.], cksum 0x5851 (incorrect > 0x30d3), seq 1080713945:1080714027, ack 62760789, win 501, options [nop,nop,TS val 1017464119 ecr 3001513453], length 82
```

The flags field identifies TCP flags. In this case, the P represents the push flag and the period indicates it's an ACK flag. This means the packet is pushing out data.

The next field is the TCP checksum value, which is used for detecting errors in the data.

This section also includes the sequence and acknowledgment numbers, the window size, and the length of the inner TCP packet in bytes.

## Task 3: Capture network traffic with `tcpdump`
In this task, `tcpdump` will be used to save the captured network data to a packet capture file.

1. Capture packet data into a file called capture.pcap:

```bash
sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap &
```

Press the `ENTER` key to get the command prompt back after running this command.

This command will run `tcpdump` in the background with the following options:

-i eth0: Capture data from the eth0 interface.

-nn: Do not attempt to resolve IP addresses or ports to names.This is best practice from a security perspective, as the lookup data may not be valid. It also prevents malicious actors from being alerted to an investigation.

-c9: Capture 9 packets of data and then exit.

-port 80: Filter only port 80 traffic. This is the default HTTP port.

-w capture.pcap: Save the captured data to the named file.

-&: This is an instruction to the Bash shell to run the command in the background.

This command runs in the background, but some output text will appear in the terminal. The text will not affect the commands when steps are followed closely.

2. Use curl to generate some HTTP (port 80) traffic:

```bash
curl opensource.google.com
```

When the curl command is used like this to open a website, it generates some HTTP (TCP port 80) traffic that can be captured.

3. Verify that packet data has been captured:

```bash
ls -l capture.pcap
```

Note: The "Done" in the output indicates that the packet was captured.

## Task 4: Filter the captured packet data
In this task, use `tcpdump` to filter data from the packet capture file you saved previously.

1. Use the `tcpdump` command to filter the packet header data from the capture.pcap capture file:

```bash
sudo tcpdump -nn -r capture.pcap -v
```

This command will run `tcpdump` with the following options:

-nn: Disable port and protocol name lookup.

-r: Read capture data from the named file.

-v: Display detailed packet data.

You must specify the -nn switch again here, as you want to make sure tcpdump does not perform name lookups of either IP addresses or ports, since this can alert threat actors.

This returns output data similar to the following:

```bash
12345
reading from file capture.pcap, link-type EN10MB (Ethernet)
20:53:27.669101 IP (tos 0x0, ttl 64, id 50874, offset 0, flags [DF], proto TCP (6), length 60)
    172.17.0.2:46498 > 146.75.38.132:80: Flags [S], cksum 0x5445 (incorrect), seq 4197622953, win 65320, options [mss 1420,sackOK,TS val 610940466 ecr 0, nop,wscale 7], length 0
20:53:27.669422 IP (tos 0x0, ttl 62, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    146.75.38.132:80: > 172.17.0.2:46498: Flags [S.], cksum 0xc272 (correct)
```

As in the previous example, the IP packet information along with information about the data that the packet contains.

2. Use the tcpdump command to filter the extended packet data from the capture.pcap capture file:

```bash
sudo tcpdump -nn -r capture.pcap -X
```

This command will run tcpdump with the following options:

-nn: Disable port and protocol name lookup.

-r: Read capture data from the named file.

-X: Display the hexadecimal and ASCII output format packet data. Security analysts can analyze hexadecimal and ASCII output to detect patterns or anomalies during malware analysis or forensic analysis.

Note: Hexadecimal, also known as hex or base 16, uses 16 symbols to represent values, including the digits 0-9 and letters A, B, C, D, E, and F. American Standard Code for Information Interchange (ASCII) is a character encoding standard that uses a set of characters to represent text in digital form.

## Conclusion
Through this activity, I gained hands‑on experience with tcpdump in a Linux environment. I learned how to identify network interfaces, capture live traffic, apply filters, and save packet data for later analysis. By examining both header details and extended packet information, I built practical skills in interpreting network traffic and understanding how data flows between systems. These steps form a strong foundation for deeper network security analysis and prepare me for more advanced investigations.

