---
layout: post
title:  "Domain Name System"
date:   2024-04-07
order: 3
---

# Domain Name System
***

## Domain Name
It is a structured ASCII (American Standard Code for Information Interchange) character string. It is build up of labels seperated by dots.

>> Label: Each label is limited to 63 characters in length, are case insensitive and may contain letters A-Z, a-z, the digits 0-9 and the hyphen (-). They are encoded with a single byte value that indicates the length of the label, then followed by the label characters.

>>Root Label: It is an empty label, that terminates the domain. In DNS the root label is represented by a single bye value of  0 × 00. It is the top of the DNS hierarchy.

>>Hostname: The leftmost label.

>>Fully qualified domain name (FQDN): The whole domain name containing all the labels.

>>Top level domain (TLD): domains directly below the root. they can be country code (cc) or generic (g).

>> Public Suffix: Some TLDs divide the namespace under their control into separate branches. Public suffix is the combination of branch label and the TLD. -there is a public list of such suffixes available.


The root is managed by the ICANN, further they delegate the responsibility for maintenance of TLDs to registries. Reistries may further divide the name space into publix suffixes. ex: .co.uk for commercial domains and .ac.uk for academic institutions.
>> This allows seperate companies called registrars to sell domain names to people. The owner of the domain name is called the regisrant.

##  Base DNS Protocol
### Message format
DNS message consists of a header, followed by the sections Question, Answer, Authority and Additional. Each section is filled with resource record.
### Query/response protocol
- The DNS messages are usually transported using UDP but in some cases messages are exchanged over TCP.
- maximim size of the payload for DNS messages of 512 bytes.
- Client sends query -> Server sends response —> (optional) Fallback to TCP [incase responce cannot be fitted in a single DNS message]

### Record types
- A : maps domain to a IPV4 (A stands for address)
- AAAA : maps domain to a IPV6( quad a)
- CNAME : specifies an alias for a name.( canonical name)
- NS : specifies the the name of a authorative name server for a domain.
- MX : mail exchanger record points to the server to which the email needs to be delivdered for the given domain.
- SOA : Start of authority record stores the administrative information about a dns zone.
- SRV : servive record points to a service.
- PTR : pointer record resolves ip to domain names.
### DNS zone
-Data for domains is organised into zones (zone files).

### Domain name servers
Two server roles:
- authoriative name server
- dns resolver or the caching name server.

### Resolver
- Most OSes have a built in stub resolver. These cannot perform resurrsion, they send the query to the DNS resolvers.

>> stub Resolver(os) -> recursive resolver -> root name server -> recursive resolver -> TLD authoritative servers -> so on.

apart from local resolvers there are remote resolvers like the Google Public DNS - global DNS resolution service operating on 8.8.8.8

###  Authoritative name servers
Zone files are distributed among several Authoritative name servers.

## measuring the DNS
>> passive measurements : " in passive measurements, DNS traffic
is collected at one or more measurement points and observes
traffic that is the result of DNS queries by real end users. "
>> active measurements : an active measurement precisely controls which queries
are executed and collects results for these.

#### Referance paper:
Addressing the challenges of modern DNS a comprehensive tutorial - Olivier van der Toorn