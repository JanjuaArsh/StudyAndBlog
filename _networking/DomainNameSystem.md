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
- A : maps domain to a IPV4
- AAAA : maps domain to a IPV6
- CNAME : specifies an alias for a name.

### DNS zone
-
