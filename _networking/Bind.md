---
layout: post
title:  "Bind"
date:   2024-04-11
order: 7
---

# Bind

## BIND9 (Berkeley Internet Name Domain version 9)
BIND is a widely used open-source Domain Name System (DNS) server software. Here's what BIND9 can do:
- BIND9 primarily functions as a DNS server, which translates human-readable domain names (like example.com) into IP addresses (like 192.0.2.1) and vice versa. 
- BIND9 can act as an authoritative DNS server, meaning it hosts and serves the DNS records for specific domains. 
- BIND9 can operate as a caching resolver, storing DNS information locally after resolving requests. 
- BIND9 provides logging capabilities, allowing administrators to monitor DNS activity, track queries, and diagnose issues. 
-A secondary server is used in addition to a primary server, serving as a copy of the zone(s) configured on the primary server. Secondary servers are recommended on large networks. These ensure the availability of the DNS zone , even if the primary server is offline.
-A BIND9 server can be configured as both a cache server and a primary server, as a cache server and secondary server, or even as a cache server, primary server and secondary server. 
-Master stealth server and slave stealth server. They are identical to the master and slave servers, but with a slightly different organization: they are only visible inside the domain.  the passive server is not queried from the internet. It can thus be reserved for local use.
-BIND9 servers can be recursive, that is to say querying the necessary DNS servers in turn until obtaining the answer, and transmitting it to their client. Otherwise (by default), the DNS server delegates domain name resolution to another DNS server .

## Configuration
- BIND9 configuration files are stored under: /etc/bind/
- The main configuration of BIND9 is carried out in the following files:
>> /etc/bind/named.conf
>> /etc/bind/named.conf.options
>> /etc/bind/named.conf.local

### recursive resolver.
In this case, BIND is configured to only respond to requests from the PC on which it is installed. It takes care of name resolution itself, without going through your ISP 's DNS servers. This configuration implies that you are directly responsible for domain name resolution. You no longer benefit from the DNS cache of your access provider, and you therefore use more of the root servers, but you will not be subject to filtering (or sometimes to the lying DNS ) of your access provider.
 - In order to make BIND inaccessible from the outside, edit the file " /etc/bind/named.conf.options ", set the options " listen-on " to 127.0.0.1 " and " listen-on-v6 " to " : :1 " 
- Then still in this same file, comment on the “ forwarders ” option . Just put a # in front of each line:
