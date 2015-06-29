"archive" Top-Level Media Type
==============================

> The “archive” top level media type is proposed for file archives:
> formats that package files and file metadata into a single data
> stream.  This BoF will cover use cases, types of archives, common
> semantics (fragment identifiers, facets), parameters for unambiguous
> interchange, and potential RFC outputs.


Current draft source can be found in the `arcmedia` directory.


NOTE WELL
---------

Any submission to the [IETF](https://www.ietf.org/) intended by the
Contributor for publication as all or part of an IETF Internet-Draft or
RFC and any statement made within the context of an IETF activity is
considered an "IETF Contribution". Such statements include oral
statements in IETF sessions, as well as written and electronic
communications made at any time or place, which are addressed to:

 * The IETF plenary session
 * The IESG, or any member thereof on behalf of the IESG
 * Any IETF mailing list, including the IETF list itself, any working
   group or design team list, or any other list functioning under IETF
   auspices
 * Any IETF working group or portion thereof
 * Any Birds of a Feather (BOF) session
 * The IAB or any member thereof on behalf of the IAB
 * The RFC Editor or the Internet-Drafts function
 * All IETF Contributions are subject to the rules of
   [RFC 5378](https://tools.ietf.org/html/rfc5378) and
   [RFC 3979](https://tools.ietf.org/html/rfc3979)
   (updated by [RFC 4879](https://tools.ietf.org/html/rfc4879)).

Statements made outside of an IETF session, mailing list or other
function, that are clearly not intended to be input to an IETF activity,
group or function, are not IETF Contributions in the context of this
notice.

Please consult [RFC 5378](https://tools.ietf.org/html/rfc5378) and [RFC
3979](https://tools.ietf.org/html/rfc3979) for details.

A participant in any IETF activity is deemed to accept all IETF rules of
process, as documented in Best Current Practices RFCs and IESG
Statements.

A participant in any IETF activity acknowledges that written, audio and
video records of meetings may be made and may be available to the
public.


Contributing
============

These drafts should be discussed on the IETF Arcmedia discussion list
<arcmedia@ietf.org>.  Pull requests are welcome.

Please try to ensure that pull requests update the `draft.md`
documents.


Tool Chain
----------

    markdown --> xml --> txt

The ultimate source file for each draft is `draft.md`

It is interpreted using the [kramdown-rfc2629][] parser to produce a
standard [RFC 2629][rfc2629] XML file.

The XML file is transformed using [xml2rfc][] to produce a plain text
internet draft, and a beautiful HTML document.

There is a Makefile in the same directory as each draft to automate
the process.

The entire toolchain was copied from <https://github.com/mnot/I-D/>


[kramdown-rfc2629]: https://github.com/cabo/kramdown-rfc2629
[rfc2629]: https://tools.ietf.org/html/rfc2629
[xml2rfc]: http://xml2rfc.ietf.org/

