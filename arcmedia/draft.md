---
title: The Archive Top-Level Media Type for File Archives
abbrev: arcmedia
docname: draft-seantek-kerwin-arcmedia-type-01
date: 2015
category: info

ipr: trust200902
area: General
workgroup: 
keyword: Internet-Draft

updates:
 - 2045
 - 6838

stand_alone: yes
pi: [toc, tocindent, sortrefs, symrefs, strict, compact, comments, inline]

author:
 -  ins: S. Leonard
    name: Sean Leonard
    org: Penango, Inc.
    street:
    - 5900 Wilshire Boulevard
    - 21st Floor
    city: Los Angeles
    region: CA
    code: 90036
    country: USA
    email: dev+ietf@seantek.com
    uri: http://www.penango.com/
 -
    ins: M. Kerwin
    name: Matthew Kerwin
#    street: "-"
#    city: Brisbane
#    region: QLD
#    country: Australia
    email: matthew@kerwin.net.au
    uri: http://matthew.kerwin.net.au/

normative:
  RFC2045:
  RFC2119:
  RFC6838:

informative:
  ISO10646:
    title: Information Technology - Universal Multiple-Octet Coded Character Set (UCS)
    author:
    - organization: International Organization for Standardization
    date: 2003-12
    seriesinfo:
      ISO/IEC: 10646:2003
  CP437:
    title: Code Page 437 MS-DOS Latin US
    author:
    - organization: Microsoft Developer Network
    date: 2015-04-20
    target: https://msdn.microsoft.com/en-us/library/cc195060.aspx
  ZIP:
    title: application/zip registration at IANA
    author:
    - ins: P. Lindner
      name: Paul Lindner
      email: lindner@mudhoney.mico.umn.edu
    date: 1993-06-19
    target: http://www.iana.org/assignments/media-types/application/zip

--- abstract

This document defines a new top-level media type to be known as
"archive", which defines a fundamental type of media with unique
presentational, hardware, and processing aspects.

--- middle

# Introduction

The purpose of this memo is to update {{RFC2045}} and {{RFC6838}} to
include a new top-level media type to be known as "archive".
{{RFC6838}} describes mechanisms for specifying and describing the
format of Internet Message Bodies via media type/subtype pairs.
"archive" defines a fundamental type of media with unique
presentational, hardware, and processing aspects.  Various subtypes
of this top-level type are immediately anticipated, and will be covered
under separate documents.


## Notational Conventions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in {{RFC2119}}.


# Definition of an archive  {#definition}

The archive top-level media type identifies a container of one or
more data objects and metadata about them.  Archives are used to
collect multiple data objects together into a single object for easier
portability and storage.  Archive formats can provide many optional
services, including:

1. compression

2. encryption

3. authentication

4. backup and restoration

5. filesystem imaging

6. software packaging and distribution

7. volume-splitting (archive split into multiple objects)

8. block storage

Formats and techniques that support one or more of these services
already exist under separate registrations.  For example, the
Content-Encoding header can be used to signal compressed Internet
message content.
{::comment}
The fact that they already exists invites a concern that this might
create some confusion.  The draft probably should be proactive and
address this possibility. -- Dave Crocker
{:/comment}
The distinguishing feature of the archive top-level type is that these
services are integrated into the format itself, along with the
inclusion of object-specific metadata.

Formats contemplated under this top-level type are designed to
concatenate multiple objects into a single data stream, along with
names and other metadata.  When an Internet-facing application handles
content labeled with this type, it SHOULD treat the archive as a
discrete data item.  For example, an Internet mail user agent might
display an archive-labeled type with an archive icon, possibly with a
preview of the objects contained therein, as opposed to automatically
extracting its contents.


# Encoding and Transport  {#encoding}

Unrecognized subtypes of archive SHOULD be treated as "archive/file".
Like "application/octet-stream", the purpose of the "archive/file" type
is to provide default handling;  it does not represent a particular
archive format.  Implementations SHOULD defer handling of unrecognized
subtypes of archive to a robust general-purpose archive processing
application, if such an application is available.

If default archive handling is not supported, the archive MAY be
treated as if it were "application/octet-stream".

Unless noted in the subtype registration, subtypes of archive MUST
be assumed to contain binary data, implying the use of base64 content
encoding for email and binary transfer for ftp and http.


# Registration Template  {#template}

The formal syntax for the subtypes of the archive top-level type SHOULD
look like this:

> Type name:
> : archive
>
> Subtype name:
> : xxxxxxxx
>
> Required parameters:
> : none
>
> Optional parameters:
> : TBD
>
> Encoding considerations:
> : base64 encoding is recommended when transmitting archive/* documents
>    through MIME electronic mail.
>
> Security considerations:
> : see {{security}} below
>
> Published specification:
> : TBD
>
> Applications that use this media type:
> : TBD
>
> Fragment identifier considerations:
> : The considerations of this document, plus any extra syntaxes
>    not inconsistent with this document.
>
> Additional information:
> : Deprecated alias names for this type:
>    : (Include non-archive alias names, such as those in application.)
> : Magic number(s): TBD
> : File extension(s): TBD
> : Macintosh file type code(s): TBD
> {: vspace="0"}
>
> See {{subtypes}} for references to some of the expected subtypes.
>
> Person and email address to contact for further information:
> : TBD
>
> Intended usage:
> : TBD (COMMON will be the most common)
>
> Restrictions on usage:
> : TBD
>
> Author:
> : TBD
>
> Change controller:
> : TBD
>
> Provisional registration? (standards tree only):
> : (Yes/No)
> {: vspace="0"}
>
> (Any other information that the author deems interesting may be
> added below this line.)

The optional parameters consist of starting conditions and variable
values used as part of the subtypes.


# Common Required and Optional Parameters  {#parameters}

Archive formats usually include parameteric meta-data within the
format.  Consequently, subtypes of archive SHOULD NOT specify
the same information as parameters to the type.

Some archive formats are very old, or are designed to be
backwards-compatible with older formats, and as such might not have
been designed with transport across the Internet in mind.  For example,
modern versions of the ZIP file format {{ZIP}} include support for the
Universal Character Set {{ISO10646}}, however the default encoding of
filenames within a ZIP archive has always been Code Page 437 {{CP437}}.
Due to the historical nature of archives, and to support
interoperability with older implementations, sometimes it is preferable
to communicate the archive as-is, rather than updating it to a more
modern or universal format.
{::comment}
Is this paragraph necessary? --MK
{:/comment}

Implementations that are archive-type aware MUST support the
following parameters for maximum compatibility.  At the same time, new
archive types SHOULD NOT rely on these parameters for disambiguation;
new archive types SHOULD be designed in such a way that "universal"
interoperability is achieved using information contained within the
archive format itself.

\[\[TODO: write this list\]\]

 * Code Page -- like charset but only applies to certain strings
   in the archive, when the archive format is ambiguous.  Do not
   attempt to apply this parameter as one would apply charset to text/*

 * Endianness?

 * Time/Y2K representation issues?

 * Anything else?


# Split Archives  {#splitarchives}

Several archive formats (notably RAR and ZIP) support split archives.
A "split archive" can be stored in multiple files, or more generally,
across multiple storage media.

For example, the ZIP format supports two types of splits: "split
archive" and "spanned archive".  A "split archive" is a standard ZIP
archive split over multiple files using file extensions .z01, .z02,
etc.; the final file in the sequence uses the .zip file extension.
The "spanned archive" was designed for use on floppy disks with
restrictive space limitations;  all archive files have the same
filename, and volume labels (presumably on floppy disks) are used to
store sequence information.  Neither sub-format is merely a naive
division of the octet stream: each ZIP file is parseable in its own
right, and contains its own offset values.

The TAR format (or family of formats, including cpio and ustar) was
originally designed for streaming to and from tape devices, so
splitting is accomplished differently.

\[\[TODO: Consider how to label this content. archive/zip^01?
archive/zip; split=01? Something else? How shall 01 be associated
with 02, 03, etc., when the Content-Disposition: ; filename=""
parameter is "presentation-information" and may be separated from the
Content-Type header information?\]\]

{::comment}
Are "split archives" really enough of a thing to warrant mention here, as
opposed to just handling it in the individual registrations for the types that
have the capability? If they are then this section will actually have to
provide clear guidelines on how split arvhives must be labelled. And you might
want to look at message/partial for one approach to that. (In particular, a
file name is definintely not an acceptable means of tying parts of a particular
instance together. You need a unique identifier of some sort, and it needs to
be part of the content-type, not the content-disposition.)
  -- Ned Freed
{:/comment}


# Fragment Identifier Syntax  {#fragments}

As archives usually store objects in hierarchical structures similar to
filesystems, archives can serve as virtual
filesystems. Respondents have noted that the objects stored in an archive can be
addressed by a fragment syntax that resembles a filesystem path. At
the same time, archives can store objects in different ways (along
with different types of metadata), suggesting that a common baseline
with flexible extension points is more appropriate than a fixed
universal syntax. \[\[TODO: This will be explored in future drafts.
Note the similarities with this and the file: URI...\]\]

\[\[TODO: consider how to provide a fragment for content in the
archive. NB: most archives do NOT provide Content-Type/media type
information! So /foo.html being an HTML file is just an *assumption*,
and possibly a very wrong one at that. There is no IETF registry for
file extensions.\]\]


# Piped-Composite Type Suffix Syntax

\[\[TODO: discuss tar piped through bzip2, gzip, etc. as a distinct
file format, rather than an application of the Content-Encoding:
header. Suggest common suffix like archive/tar|bzip2, where \| is some
useful character but not \+ since \+ is for structured syntaxes.\]\]


# Security Considerations  {#security}

Archives can store files, file metadata, and even entire filesystems; thus,
security issues loom large because archives can contain just about
anything. These concerns are magnified by the arbitrary transport of
such data across the Internet. \[\[TODO: complete.\]\]


--- back

# Expected Subtypes  {#subtypes}

The following archive formats will be explored for registration as
subtypes along with this effort:

Archiving Only
: TAR

Multipurpose (archiving, compression, encryption)
: ZIP, ACE, RAR, 7-Zip, StuffIt, FreeArc

Software Packaging
: MSI, RPM, JAR, XPI, CAB, CRX, APK

Disk Imaging
: ISO, NRG, BIN/CUE, VMDK, WIM, PartImage, IMG/IMA/IMZ, DMG

