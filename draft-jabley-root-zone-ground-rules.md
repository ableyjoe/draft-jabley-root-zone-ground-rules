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
    fullname: Joe Abley
    organization: Cloudflare
    email: jabley@cloudflare.com

normative:

informative:

...

--- abstract

The root zone of the DNS is, in almost all ways, a DNS zone like
any other.  However, there are a small number of ways in which the
root zone has special requirements, for reasons relating to DNS
protocol or operational considerations.  This document describes
the ways in which the root zone is special and the corresponding
technical requirements on the contents of the root zone. These
requirements form a minimal starting point for other policies that
relate to the root zone of the DNS, many of which are developed and
implemented outside the IETF.

--- middle

# Introduction

TODO Introduction


# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
