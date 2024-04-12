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

## Dns message
- header 
- question
- answer
- authority
- additional

## DNS -over-Transport Layer Security (TLS)
it was the first protocol to be  standardised by the ITEF. "It uses port 853 instead of
port 53 and it enables clients to set up long-lived TLS sessions
to resolvers and then send multiple DNS queries over that encrypted connection (Opportunistic DoT)."

## DNS -over-HTTPS
directly make doh queries using browser instead of using the  os stub resolver.

## QNAME minimization
When the resolver sends the query to the root server it sends the entire
query name. That means that every authoritative server in the recursion
path (and any eavesdroppers on that part of the network) can see
the full set of query names that the clients of each resolver send,
unnecessarily leaking data. To address this a reccursive resolution method QNAME minimization was specified where the
resolvers ask for just the part of the query name they actually
need for that resolution step.
 
## DNSSEC - DNS security
- DNSSEC adds extra data to DNS messages in the form of digital signatures.
- DNSSEC relies on the so-called Extension Mechanisms for DNS, know as ‘‘EDNS0’’
-The EDNS0 specification adds a way for DNS clients and servers to signal to each other that they have additional capabilities. This is done by including a pseudo resource record in the additional section of DNS queries and responses, the so-called OPT resource record.
-DNSSEC signing is performed by the owner of a domain, and is done at the zone level.
-  DNSSEC is designed to establish a chain of trust between parent and child zones. This chain of trust extends all the way from the root of the DNS down to an individually signed record. The chain of trust is established by creating a reference in the parent to a public key in the signed zone. This is done using the DS record type. The parent zone contains one or more DS records, that each reference a public key in the child zone that is a so-called secure entry point.

## Nsec - next secure
In the DNS, name servers return a non-existent
domain (NXDOMAIN) response if a record does not exist, but how
can we trust that this is the case? DNSSEC also addresses this
problem through a mechanism called authenticated denial of existence. NSEC records are used for this purpose.
## Attacks on DNS

### domain shadowing
When an attacker adds a subdomain under an existing domain.

### domain registration hijack
An attacker compromising an account of a registration provider (Registry, Registrar,
or Reseller), for instance by using usernames and passwords
obtained from other compromised sites.

### zone poisoning
an attack on the zone
file stored in a name server rather than on the registration system. 

### domain squatting
The practice of registering domains which closely resemble
well-known domains.
>> The DNS facilitates cybersquatting attacks, because registering
domains which closely resemble other domains is not prohibited.
- Typosquatting
- Bitsquatting
- Combosquatting
- Homophone-Based squatting _ audibally similar
- Homograph-Based squatting _ visually similar
-  IDN Homograph-Based Squatting (renders to yout.ube[.]com) _ use unicode characters in place to acsii and are sometimes impossible to distinguish

## Distribute the zone
- Zones are distributed in-band using the
DNS protocol and out of band using other Internet protocols or
non-standardized APIs and user interfaces.
-Traditionally there
exist two ways to distribute a zone to other name servers inband: Authoritative Transfer (AXFR) and Incremental Transfer
(IXFR)
-With AXFRs it is necessary to transfer the whole
zone, whereas IXFRs transfer only the changes since the last
transfer.
- Both transfers are initiated by the server that wants to
fetch the latest version of the zone, the so called secondary.
- NOTIFY announcements are DNS queries
that include the SOA record of the updated zone, allowing a
secondary to determine if it indeed needs to fetch an update
-Often, zone transfers should be limited to trusted name servers
only. Therefore, primary and secondary name servers can share
a secret key used for mutual authentication using the TSIG protocol

#### Referance paper:
Addressing the challenges of modern DNS a comprehensive tutorial - Olivier van der Toorn