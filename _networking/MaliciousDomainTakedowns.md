---
layout: post
title:  "Malicious Domain Takedowns"
date:   2024-04-11
order: 8
---
# Malicious Domain Takedowns
---
>ref:  "Cracking the Wall of Confinement: Understanding and Analyzing Malicious Domain Take-downs"
# Domain take-down: 
The process of repossessing a domain name from its currently registered owner due to a
violation of the Acceptable Use Policies (AUPs) defined by
ICANN, registries and registrars, which are involved in the
domain registration process.
- The take-down process is initiated by a take-down requester who essentially reports the domain’s violations and
submits a request to suspend its operation.
- Take-down authorities are third-party services specializing in
domain take-down, such as brand-name protection companies.
- Take-down executors carry out the
take-down operation by modifying the Internet name system
to reflect the changes specified in the court order.

# Domain sinkholing: 
Sinkholing is a way to redirect the takendown domain’s traffic to a new destination, a sinkhole. Technically, domain sinkholing is performed by changing
the configuration of a domain’s DNS records. Done  by either changing the ns record or the a record of the ns reocrd. 

# Domain delisting: 
Domain delisting is essentially the process
of deactivating a domain by removing it from DNS and
responding with nonexistence (i.e., NXDomain) to any DNS
queries. 
- However, removal from DNS is not enough to delist
a domain, as it may return to the pool of available domains
at the registries. 
- Delisting goes a step further by modifying
the WHOIS records of the domain and placing a hold on the
domain, thus stopping it from being released back to registries
until it either expires or the hold is removed.

#  Reserved domains
Reserved domains are the ones
locked by their TLD registry. These domains are not included
in the public pool of available domains. Reserved domains are
locked for different reasons (e.g., due to name collision, or due
to short domain name) and not necessarily because of a takedown process.

# domain hopping
“Top-level domain hopping” is when a site (e.g. 'badsite.ru') keeps its second-level domain name ('badsite') but changes its top-level domain ('. ru'), creating a whole new website with different hosting details but retaining its 'name brand'.

# SERVER HOLD VS CLIENT HOLD
A WHOIS record includes domain Extensible
Provisioning Protocol (EPP) status codes [12], which define
how a domain’s registration can be managed. EPP codes can
indicate if a domain is active or whether it can be transferred,
modified, or deleted. For example, an OK EPP code indicates
a normal state. There are two types of EPP codes: client
and server codes. Registrars are allowed to set client EPP status codes, while server EPP status codes can only be set by
registries when necessary to override other EPP codes that may
be set by the registrar (i.e., client EPP codes). In the process
of domain take-down, registries and registrars may delist a
domain by setting its EPP status code to SERVERHOLD and
CLIENTHOLD, respectively. Placing a domain on hold in this
way causes it to be nonexistent in the DNS and unavailable
for purchase through registrars. Typically, domains taken down
in this way remain delisted until their old registration records
expire.
 - When a domain is taken down by the registry, its EPP
status code is set to SERVERHOLD. Similarly, when a domain
is taken down by the registrar, a hold will be placed using
a CLIENTHOLD EPP status code, essentially removing the
domain from the registry’s DNS zone file, and therefore it will
not be resolved.

#  Identifying Delisted Domains
- If either REDEMPTIONPERIOD or PENDINGDELETE appeared in the domain’s status
field, which indicates deletion. We then looked for a sign for
auto renewal (i.e., AUTORENEWPERIOD). If any of these codes
were set along with a hold flag, this strongly indicated that the
hold was not caused by the take-down action. 

- Further, the registry requires a newly created WHOIS record
to be verified by its registrant within 15 days. After that,
CLIENTHOLD is set for unverified ones. We checked whether
the hold was placed within 15 days of the creation of a domain.
If so, we did not consider it as a delisted domain.

-  A renewed domain
would be placed on CLIENTHOLD, pending for the payment
from the owner. 

- Note that some other EPP status codes have been observed in take-down operations, such as TRANSFERPROHIBITED, DELETEPROHIBITED, and UPDATEPROHIBITED. 

- These EPP codes do not affect
the resolution of the domain; actually the take-down action that
set these records must be accompanied by DNS redirection
(i.e., a sinkholing).
