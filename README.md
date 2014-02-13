VDIR
====

This document describes a storage format for VEVENTS, VTODOs and VCARDs, with the main goal of being easy to implement.

Basic Folder Structure
----------------------

The main folder (root) contains an arbitrary number of subfolders (collections), which contain only files (items).

Synonyms for "collection" may be "addressbook" or "calendar".

An item is:

  - A VCARD file, in which case the file extension must be `.vcf`, *or*
  - A VCALENDAR file containing exactly one VEVENT or VTODO component (and, optionally, a VTIMEZONE component), in which case the file extension must be `.ics`.

An item's name contains the UID of the VTODO, VEVENT or VCARD component inside the file, followed by the mentioned file extension.

This is basically very similar to CalDAV and CardDAV.

Implementation ideas
--------------------

Similarly to the popular combination of offlineimap, mutt and notmuch, a toolchain to manage, modify and display VDIRs could consist of three programs working independently from each other:

  - A syncronization tool
  - A CLI-program which lets the user modify the data directly
  - An indexing or caching tool to allow for faster search than is possible with a linear scan through all items

### Syncronization

See http://blog.ezyang.com/2012/08/how-offlineimap-works/ for a good solution for *immutable* items. The syncronization tool can use the algorithm described to handle new and deleted items, and then run a *second* algorithm that can be roughly described with this Venn-Diagram:

![img](http://i.imgur.com/YbjYMth.png)
