<h1>$${\color{red}Sendip} \space {\color{Goldenrod}Tool } $$</h1>

SendIP is a command-line tool to send arbitrary IP packets. It has a large number of options to specify the content of every header of a RIP, RIPng, BGP, TCP, UDP, ICMP, or raw IPv4/IPv6 packet. It also allows any data to be added to the packet. Checksums can be calculated automatically, but if you wish to send out wrong checksums, that is supported too.

#### Install sendip on ubuntu

```
sudo apt-get install sendip
```

************

Using Sendip (Syntax)

  > sendip [-v] [-d data] [-h] [-f datafile] [-p module] [module options] hostname

*********

```
-d data -- add this data as a string to the end of the packet Data can be: rN to generate N random(ish) data bytes; 0x or 0X followed by hex digits; 0 followed by octal digits; any other stream of bytes

-f datafile -- read packet data from file

-h -- print this message

-p module -- load the specified module (see below)

-v -- be verbose

Available modules at the moment as follows

ipv4 ipv6 icmp tcp udp bgp rip ntp

I am going to provide TCP,UDP,ICMP and IPV4 available options

ICMP

-ct x -ICMP message type Default: ICMP_ECHO

-cd x -- ICMP code Default: 0

-cc x -- ICMP checksum Default: Correct

IPV4

-is x -- Source IP address Default: 127.0.0.1

-id x -- Desitnation IP address Default: Correct

-ih x -- IP header length Default: Correct

-iv x -- IP version Default: 4

-iy x -- IP type of service Default: 0

-il x -- Total IP packet length Default: Correct

-ii x -- IP packet ID Default: Random

-ifr x -- IP reservced flag Default: 0 (options are 0,1,r)

-ifd x -- IP don't fragment flag Default: 0 (options are 0,1,r)

-ifm x -- IP more fragments flag Default: 0 (options are 0,1,r)

-if x -- IP fragment offset Default: 0

-it x -- IP time to live Default: 255

-ip x -- IP protcol Default: 0, or set by underlying protocol

-ic x -- IP checksum Default: Correct

-ionum x -- IP option as string of hex bytes

-ioeol -- IP option: end of list

-ionop -- IP option: no-op

-iorr x -- IP option: record route. Format: pointer:addr1:addr2:...

-iots x -- IP option: timestamp. Format: pointer:overflow:flag:(ip1:)ts1:(ip2:)ts2:...

-iolsr x -- IP option: loose source route. Format: pointer:addr1:addr2:...

-iosid x -- IP option: stream identifier

-iossr x -- IP option: strict source route. Format: pointer:addr1:addr2:...

TCP

-ts x -- TCP source port Default: 0

-td x -- TCP destination port Default: 0

-tn x -- TCP sequence number Default: Random

-ta x -- TCP ack number Default: 0

-tt x -- TCP data offset Default: Correct

-tr x -- TCP header reserved field EXCLUDING ECN and CWR bits Default: 0

-tfe x -- TCP ECN bit Default: 0 (options are 0,1,r)

-tfc x -- TCP CWR bit Default: 0 (options are 0,1,r)

-tfu x -- TCP URG bit Default: 0, or 1 if -tu specified (options are 0,1,r)

-tfa x -- TCP ACK bit Default: 0, or 1 if -ta specified (options are 0,1,r)

-tfp x -- TCP PSH bit Default: 0 (options are 0,1,r)

-tfr x -- TCP RST bit Default: 0 (options are 0,1,r)

-tfs x -- TCP SYN bit Default: 1 (options are 0,1,r)

-tff x -- TCP FIN bit Default: 0 (options are 0,1,r)

-tw x -- TCP window size Default: 65535

-tc x -- TCP checksum Default: Correct

-tu x -- TCP urgent pointer Default: 0

-tonum x -- TCP option as string of hex bytes

-toeol -- TCP option: end of list

-tonop -- TCP option: no op

-tomss x -- TCP option: maximum segment size

-towscale x -- TCP option: window scale

-tosackok -- TCP option: allow selective ack

-tosack x -- TCP option: selective ack (rfc2018), format is l_edge1:r_edge1,l_edge2:r_edge2...

-tots x -- TCP option: timestamp (rfc1323), format is tsval:tsecr

UDP

-us x -- UDP source port Default: 0

-ud x -- UDP destination port Default: 0

-ul x -- UDP packet legnth Default: Correct

-uc x -- UDP checksum Default: Correct

You can check manpage for more details and available options

```

# Sendip Examples

### UDP Packet

```
sendip -p ipv4 -is 192.168.1.21 -p udp -us 5070 -ud 5060 -d "UDP Test" -v 192.168.1.21
```

### ICMP Packet

```
sendip 192.168.2.12 -p icmp -is 192.168.2.22
```

### TCP Packet

```
sendip 192.168.2.12 -p tcp -ts 2 -td 80 -tn -is 192.168.2.22
```





