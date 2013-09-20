---
layout: post
title: "This Week in Skynet #23"
date: 2011-11-23 15:33
comments: true
categories: updates  
author: Matthew Casperson
---

This week we upgraded to using HTTPS on the server and continued to extend the Zanata support.

<!-- MORE -->

### HTTPS Login

The login page now uses HTTPS. The certificate is not signed, so you will have to add the certificate in Firefox, or ignore the security warning in Chrome.

### Continued Work on Zanata Integration

Work has continued on providing integration with Zanata. After a meeting with the Zanata guys I have had to expand Skynet's role to address the following decisions:

* Skynet will be responsible for maintaining the state of a translation at a point in time (equivalent to downloading a PO file and checking it into an SVN repo)
* Skynet will provide the interface used by translators to view, sort and compare topics that have been translated
* Zanata will provide a fixed URL for editing a specific topic, which will appear in Skynet to allow translators to do the actual translations.

Snapshots can now only be created from the main search screen. The tags and topic field filters are selected (as if you were going to build a DocBook ZIP file) and then a Snapshot is created, essentially freezing the state of the topics returned by the search fields.

<img src="/images/uploads/Screenshot-at-2011-11-29-17-46-42.png" alt="Creating new snapshots from search" class="img-responsive img-thumbnail"> 


Once created, Snapshots can be queried from their own search page.

<img src="/images/uploads/Screenshot-at-2011-11-29-17-47-09.png" alt="Snapshots can be queried from their own search page" class="img-responsive img-thumbnail"> 


The snapshot topics (either belonging to a specific revision, or just in the working state) can be queried just like regular topics, complete with grouping. In future it is likely that there will be a number of tags to represent translation priorities, which translators can use to organise their workflow.

<img src="/images/uploads/Screenshot-at-2011-11-29-17-40-56.png" alt="Zanata IDs in Tags" class="img-responsive img-thumbnail"> 

Snapshots now have the concept of a revision. A revision is kind of like a snapshot for a snapshot. When created, a revision will save the translation strings and the translated XML, allowing books to be recreated at a later point with a known translation set. When a snapshot is first created, an initial revision named "Initial Untranslated Revision" is created that reflects the untranslated state of the topics.

In addition to revisions, translations can be pulled down into a working state. The working state represents the topics translated against the latest strings in Zanata. This gives translators the ability to view and compare translated documents without having to create a snapshot revision.

There is still more work to be done, but I am hoping that I can get a working example uploaded by the end of the week, or maybe early next week.

