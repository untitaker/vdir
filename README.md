VDIR
====

This document describes a storage format for VEVENTS, VTODOs and VCARDs, with
the main goal of being easy to implement.

Basic Folder Structure
----------------------

The main folder (root) contains an arbitrary number of subfolders
(collections), which contain only files (items).

Synonyms for "collection" may be "addressbook" or "calendar".

An item is:

  - A VCARD file, in which case the file extension *must* be `.vcf`, *or*
  - A VCALENDAR file containing exactly one VEVENT or VTODO component (and,
    optionally, a VTIMEZONE component), in which case the file extension *must*
    be `.ics`.

An item's filename *must* end with the mentioned file extension and *should*
contain only the VCARD's, VEVENT's or VTODO's UID and the file extension.

This is basically very similar to CalDAV and CardDAV.

Implementation
--------------

[vdirsyncer](https://github.com/untitaker/vdirsyncer) is the reference
implementation.
