# DNS-BailiWicked-Host-Attack Name: DNS BailiWicked Host Attack
     Module: auxiliary/spoof/dns/bailiwicked_host
    License: Metasploit Framework License (BSD)
       Rank: Normal
  Disclosed: 2008-07-21

Provided by:
  I)ruid <druid@caughq.org>
  hdm <x@hdm.io>

Check supported:
  Yes

Basic options:
  Name       Current Setting                   Required  Description
  ----       ---------------                   --------  -----------
  HOSTNAME   www1.ipage.com/secure/login.html  yes       Hostname to hijack
  INTERFACE                                    no        The name of the interface
  NEWADDR    192.168.43.20                     yes       New address for hostname
  RECONS     208.67.222.222                    yes       The nameserver used for reconnaissance
  RHOSTS     192.168.43.185                    yes       The target host(s), see https://github.com/rapid7/metasploit-fra
                                                         mework/wiki/Using-Metasploit
  SNAPLEN    65535                             yes       The number of bytes to capture
  SRCADDR    Real                              yes       The source address to use for sending the queries (Accepted: Rea
                                                         l, Random)
  SRCPORT    53                                yes       The target server's source query port (0 for automatic)
  TIMEOUT    500                               yes       The number of seconds to wait for new data
  TTL        46010                             yes       The TTL for the malicious host entry
  XIDS       50                                yes       The number of XIDs to try for each query (0 for automatic)

Description:
  This exploit attacks a fairly ubiquitous flaw in DNS implementations 
  which Dan Kaminsky found and disclosed ~Jul 2008. This exploit 
  caches a single malicious host entry into the target nameserver by 
  sending random hostname queries to the target DNS server coupled 
  with spoofed replies to those queries from the authoritative 
  nameservers for that domain. Eventually, a guessed ID will match, 
  the spoofed packet will get accepted, and due to the additional 
  hostname entry being within bailiwick constraints of the original 
  request the malicious host entry will get cached.

References:
  https://nvd.nist.gov/vuln/detail/CVE-2008-1447
  OSVDB (46776)
  https://www.kb.cert.org/vuls/id/800113
  http://www.caughq.org/exploits/CAU-EX-2008-0002.txt
/home/krushna/Documents/resolver.rb
/home/krushna/Documents/bailiwicked_host.rb
/home/krushna/Documents/resolver (1).rb
/home/krushna/Documents/resolver (2).rb
/home/krushna/Documents/resolver (3).rb
