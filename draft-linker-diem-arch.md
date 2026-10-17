---
title: "Digital Emblems Architecture Document"
category: info

docname: draft-linker-diem-arch-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: "Applications and Real-Time"
workgroup: "Digital Emblems"
keyword:
venue:
  group: "Digital Emblems"
  type: "Working Group"
  mail: "diem@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/diem"
  github: "felixlinker/diem-arch"
  latest: "https://felixlinker.github.io/diem-arch/draft-linker-diem-arch.html"

author:
 -
    fullname: Felix Linker
    email: linkerfelix@gmail.com

normative:

informative:

...

--- abstract

TODO Abstract


--- middle

# Introduction {#intro}

The Digital Emblems (diem) WG works on the digitization of physical emblems as *digital emblems*.
Emblems convey some information about a subject that must be interpreted in context of some normative framework, for example, a law, a treaty, a convention, a government agency's procedures, or a customary law.
One famous example of an emblem is that of the Red Cross, which conveys that its bearer serves a medical purpose and thus enjoys specific protections under International Humanitarian Law (IHL).
Digital emblems are systems and standards that convey the relevant information by digital means, e.g., by storing it in DNS resource records.

Different use cases have been discussed at the diem WG, for example, the labelling of goods in transport by reference to the World Customs Organization's classification, conveying that a wetland is designated as protected under the Convention on Wetlands of International Importance, or the marking of digital services as enjoying specific protections under IHL.
(For more details, see {{?I-D.ietf-diem-requirements}}.)

Intuition suggests that one design ought to be able to address all use cases, and many use cases share some requirements, e.g., authenticating an emblem's information.
Discussions on the various use cases, though, have revealed that many use cases have conflicting requirements or have
different flavours of requirements that may upon first glance appear to be the same.
Thus, it seems to be the most sensible way forward to distinguish different profiles of Digital Emblems, which can address different groups of use cases that share relevant requirements.

In this document, we present these different emblem profiles and groups of use cases, outline their domain model and relevant parties, and sketch which drafts will comprise a profile.
This document is meant to evolve in parallel to the referenced protocol documents.
It serves as an overview of the DIEM WG work.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

# Digital Emblem Profiles

## Profile 1: External Registry Emblems

This profile currently comprises the following drafts:

 - {{?I-D.woodcock-faltstrom-external-registry-rrtypes}}

In the external registry profile, emblems convey information that is codified by an external registry.
For example, the United Nations Economic Commission for Europe (UNECE) defines standardized means to encode data, e.g., areas, time and dates, types of cargo, and much more.
This profile provides means to associate such externally codified information with domain names.

The domain model of this profile is the following.
A validator learns about an asset's associated domain name out-of-band.
Using this profile, the validator can query for different groups of codified information by querying for relevant resource record types associated with that domain name.
How this information is processed then depends on the use case and application context.

Information is published in the DNS by the party controlling the asset with which information is associated.
Integrity of the data can be provided straightforward by signing the relevant zones using DNSSEC {{?RFC4033}} {{?RFC4034}} {{?RFC4035}}.

## Profile 2: Protective Emblems

This profile currently comprises the following drafts:

- {{?I-D.linker-diem-adem-core}}
- {{?I-D.linker-diem-adem-dns}}

The protective emblems use case provides digital means to convey the protective emblems defined in Geneva Conventions, their Additional Protocols, and the 1954 Hague Convention.
These emblems include the Red Cross, Red Crystal, and Red Crescent for medical, humanitarian infrastructure.

In this profile, an emblem issuer can signal to a validator that the services associated with a domain name enjoy the specific protections under International Humanitarian Law (IHL), which, for example, implies that they should not be disrupted.
To use the emblem on a domain name, this domain name must only be used for purposes that enjoy the specific protections under IHL.
We assume that the emblem issuer controls the domain name, though, they may have outsourced its operation to a service provider.

The audience of such emblems are validators; all parties who would generally disrupt digital services but respect services marked with an emblem.
We can thus assume that validators obtain a service's domain name out-of-band during the reconnaissance phase of their operations.

The use of the emblem requires authorization by a competent authority, typically by a state.
How is authorization is obtained is out-of-scope of this profile for now.

# Security Considerations {#security}

TODO Security


# IANA Considerations {#iana}

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
