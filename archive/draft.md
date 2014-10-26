---
title: The Archive Primary Content Type for Multipurpose Internet Mail Extensions
abbrev: archive
docname: draft-kerwin-archive-00
date: 2014
category: info

ipr: trust200902
area: General
workgroup: 
keyword: Internet-Draft

stand_alone: yes
pi: [toc, tocindent, sortrefs, symrefs, strict, compact, comments, inline]

author:
 -
    ins: M. Kerwin
    name: Matthew Kerwin
    organization: 
    email: matthew@kerwin.net.au
    uri: http://matthew.kerwin.net.au/

normative:
  RFC2045:
  RFC2119:

informative:


--- abstract

This document defines a new primary content-type to be known as
"archive", which defines a fundamental type of content with unique
presentational, hardware, and processing aspects.

--- middle

# Introduction

The purpose of this memo is to propose an update to {{RFC2045}}
to include a new primary content-type to be known as "model".
{{RFC2045}} describes mechanisms for specifying and describing the
format of Internet Message Bodies via content-type/subtype pairs. We
believe that "model" defines a fundamental type of content with
unique presentational, hardware, and processing aspects.  Various
subtypes of this primary type are immediately anticipated but will be
covered under separate documents.


## Overview

This document will outline what an archive is, show examples of
archives, and discuss the benefits of grouping archives together.

This document is a discussion document for an agreed definition,
intended eventually to form a standard accepted extension to
{{RFC2045}}.


## Notational Conventions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in {{RFC2119}}.


# Definition of an archive  {#definition}

An archive primary MIME type is a file that is composed of one or more
files along with metadata.  Archive files are used to collect multiple
data files together into a single file for easier portability and
storage, or simple to compress files to use less storage space.


# Consultation Mechanisms  {#consultation}

Before proposing a subtype for the archive/* primary type, it is
suggested that the subtype author examine the definition (above) of
what an archive/* is and the listing (below) of what an archive/* is
not.  Additional consultations with the authors of the existing
archive/* subtypes is also suggested.


# Encoding and Transport  {#encoding}

Unrecognized subtypes of archive SHOULD at a minimum be treated
as "application/octet-stream".  Implementations MAY optionally
elect to pass subtypes of archive that they do not specifically
recognize to a robust general-purpose archive viewing application, if
such an application is available.

Unless noted in the subtype registration, subtypes of model SHOULD be
assumed to contain binary data, implying a content encoding of base64
for email and binary transfer for ftp and http.

The formal syntax for the subtypes of the model primary type SHOULD
look like this:

Media type name:
: archive

Media subtype name:
: xxxxxxxx

Required parameters:
: none

Optional parameters:
: TBD

Encoding considerations:
: base64 encoding is recommended when transmitting archive/* documents
  through MIME electronic mail.

Security considerations:
: see {{security}} below

Published specification:
: This document.
: See {{subtypes}} for references to some of the expected subtypes.

Person and email address to contact for further information:
: TBD
{: vspace="0"}

The optional parameters consist of starting conditions and variable
values used as part of the subtypes.


# Security Considerations  {#security}

TBD

--- back

# Expected Subtypes  {#subtypes}

TBD
