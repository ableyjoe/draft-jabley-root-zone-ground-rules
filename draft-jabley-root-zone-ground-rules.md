---
title: "Base Protocol Requirements for the Root Zone of the DNS"
category: std

docname: draft-jabley-root-zone-ground-rules-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: Operations
workgroup: Network Working Group
keyword:
 - dns
 - root zone
venue:
  group: dnsop
  type: Working Group
  mail: dnsop@ietf.org
  arch: https://datatracker.ietf.org/wg/dnsop/about/
  github: "ableyjoe/draft-jabley-root-zone-ground-rules"
  latest: "https://ableyjoe.github.io/draft-jabley-root-zone-ground-rules/draft-jabley-root-zone-ground-rules.html"

author:
 -
    ins: J. Abley
    name: Joe Abley
    org: Cloudflare
    city: Amsterdam
    country: NL
    email: jabley@cloudflare.com

normative:

informative:

...

--- abstract

The root zone of the DNS is, in almost all ways, a DNS zone like
any other, and shares the same DNS protocol requirements.  However,
there are a small number of ways in which the root zone is special,
in some cases as a consequence of the wider DNS protocol protocol
or for operational reason.  This document describes some ways in
which the root zone is special and imposes corresponding technical
requirements on the contents of the root zone. These requirements
form a minimal starting point for other policies that relate to the
root zone of the DNS, many of which are developed and implemented
outside the IETF.

--- middle

# Introduction

The Domain Name System (DNS), originally specified in {{!RFC1034}}
and {{!RFC1035}}, implements a namespace that is distributed
structurally as a collection of zones, connected together as a tree.
The root zone in the DNS is the ancestor of all other zones and
has no parent.

From the perspective of the DNS protocol, all zones in the DNS share
the same essential properties.  However, the root zone is special
in some ways by virtue of its location within the namespace. For
example, as the ancestor of all other zones, a chain of trust to a
key used to generate signatures in other zones relies upon secure
delegations being used from the root zone for direct children.

This document describes a minimal set of technical constraints for
the construction of the root zone. This document specifically does
not aim to encapsulate a complete or sufficient set of policies for
the root zone to meet the wider requirements of the DNS, for all
of which this document defers to other competent authorities.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

This document assumes a familiarity with the DNS terminology described
in {{!RFC9499}}.

# Technical, Protocol Constraints on Root Zone Generation

## Constraints Commnon to All Zones

The root zone MUST include exactly one SOA resource record with
empty owner name and class IN. This is a consequence of the
requirements for DNS zones described in {{!RFC1034}} and
{{!RFC1035}}.

The root zone MUST include an NS resource record set with
empty owner name and class IN, as described in {{!RFC1034}} and
{{!RFC1035}}. This is a consequence of the requirements for
DNS zones described in {{!RFC1034}} and {{!RFC1035}}.

This document does not specify particular values for the SOA
parameters included in the SOA resource record RDATA, the NS record
targets, the number of NS resource records in the NS RRSet or the
TTL of any of the RRSets described above. All such policy decisions
are instead deferred to the appropriate competent authorities.

## Special Constraints for the Root Zone

The root zone MUST NOT include A or AAAA resource records with empty
owner name and class IN. Multiple specifications make use of an
empty domain name to mean "not available", including {{?RFC2782}},
{{?RFC7505}} and {{?RFC9460}}. However, some naive DNS clients are
observed to misinterpret such signals, with the result that queries
with empty QNAME, QCLASS="IN" and QTYPE="A" or "AAAA" are observed
at root servers. Positive responses to such queries would have poor
security characteristics and are therefore prohibited.

DNSSEC MUST be deployed in the root zone, as specified in
{{!RFC9364}}.

This document does not specify practices around key management,
signature generation, algorithm choice or any other parameter
choices.

It is acknowledged that correct and proper management of DNSSEC in
the root zone includes making pragmatic, operational decisions, and
this document specifically does not specify how DNSSEC should be
deployed in any particular circumstance or at any particular time.
All such policy decisions are instead deferred to the appropriate
competent authorities.

# Security Considerations

This document aims to provide certainty for fundamental, technical
protocol aspects of the root zone of the DNS, including the deployment
of DNSSEC in the root zone.

This document does not present any new risks to the Internet.

# IANA Considerations

This document describes technical, protocol constraints on the
generation of the DNS root zone which should be incorporated as
appropriate into the root zone management responsibilities of the
IANA.

--- back

# Acknowledgments
{:numbered="false"}

Your! Name! Here!

