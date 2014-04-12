VDIR
====

This document describes a storage format for vCalendars and vCards, with
the main goal of being easy to implement.

Basic Folder Structure
----------------------

The main folder (root) contains an arbitrary number of subfolders
(collections), which contain only files (items).

Synonyms for "collection" may be "addressbook" or "calendar".

An item is:

  - A [vCard](https://tools.ietf.org/html/rfc6350) file, in which case
    the file extension *must* be `.vcf`, *or*
  - An [iCalendar](https://tools.ietf.org/html/rfc5545) file, in which
    case the file extension *must* be `.ics`.

An item's filename *must* end with the mentioned file extension and *should*
contain only the UID and the file extension.

This is basically very similar to CalDAV and CardDAV.

Implementation
--------------

[vdirsyncer](https://github.com/untitaker/vdirsyncer) is the reference
implementation.
