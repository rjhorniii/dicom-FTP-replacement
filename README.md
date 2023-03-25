# DICOM FTP replacement
 various documents related to replacing FTP for DICOM shared files/archive

## Procedures for this repository

1. Git based delta can be used for puml, md, adoc, html, etc. documents that are line oriented text only files.  Versioned files is also permitted.
2. New files with new version numbers shall be used for ms word, xls, xml, and other similar documents that are not line oriented text only files.  Git based delta coding shall not be used.
3. Filenaming shall comply with the DICOM rules for any `supxxx.docx` or `cpxxx.docx` files.  This means filenames like `sup123_short-name_nnn.docx` where nnn increments by one for each new version.
4. For other non-text files, file naming shall be of the form basename-nnn.docx.  nnn shall start at 000 and increment by one for each new version.  E.g., `example-file-003.docx`
5. For puml (plantuml) files the puml shall be in the repository but the derived graphics files shall not.  Github can display puml diagrams in some circumstances, and after checkout to a local filesystem plantuml can be used to generate graphics files.  Exception, if a graphics file is separately edited so that it is not the same as the plantuml generated graphic, it can be added as a new file with version numbering.

## What should be a repository?

Reasonable considerations were:
1.  One big repository for all of DICOM.  (This fails the size test.  DICOM is much bigger than 1Gbyte)
2.  One repository per working group.  (This works maybe.  WG-06 would have a size problem.  The distribution of the full DICOM standard would have a problem.  We've solved the distribution by using the NEMA web server.)
3.  One repository per supplement, and some other path for dealing with meeting folders and CPs.

Given what I've seen so far, I conclude:

* There should be a different repository per supplement.  

    * If a working group generates 25 versions (internal, wg-06 shared, PC, LB, FT) and over ten year period they generate 40 supplements we hit the 1 GB limit if they are all in one repository.  A few working groups exceed 1GB on the FTP server.  WG-06 greatly exceeds that limit.

    * It's hard to manage many authorized writers for one repository over a long period of time unless we pay for enterprise accounts, and then get all the working group participants to become members of the enterprise account.  This looks expensive and burdensome for NEMA staff.

    * It's easy to manage pull requests from many free/personal/other accounts as an authorized editor for a single supplement.  But, the clone and pull become burdensome if each clone and pull copies the entire 10+ year history for a working group.  It's reasonable and not too burdensome to clone and pull the entire history of one supplement.  Some supplements have been monsters, but those are the ones where you are most often going to need to see the entire history.  There are things that can be done to optimize pull, but clone will always copy the whole repository.

* The approach for CPs and meeting folders needs more thought.  Those can involve lots of editors.  Separating out the supplements may simplify dealing with CPs and meeting folders.  (Working group 6 has it's own special major headaches.)

## Access Control

The free/personal accounts are limited to a simple access control model, but it appears to be adequate.  There are other more capable alternatives at Github but they involve paid accounts and user membership through the paying organization.  This is certainly feasible, but it probably involves too much cost and time burden on the secretariat.  There may also be corporate prohibitions on that kind of membership for their representatives.  It's unlikely that there are corporate restrictions on basic public access.  (Members who already have corporate Github membership may have to take some special steps to set up a supplement directory with the right public access.  It may be easiest for them to just set up a personal account for use as a DICOM editor.)

I've set this up as:

* unlimited public read access to the repository

* The public can clone if they want. 

* Any registered github account can make pull requests if they want to make suggestions.  I expect most DICOM members to follow this path.

* The owner and designated other editors have write access.  The other editors can either make pull requests or modify the repository directly.  Getting write permission as an editor requires manual intervention by the owner, but it's quite simple.

This fits the typical supplement development pattern where people send comments and marked up documents to an editor, and the editor then updates the supplement.

This access control is somewhat better than our current FTP access control.  The changes to the repository and the pull requests are tagged with the identity of the user.  Github now requires all users to have MFA authentication if they want to write anything, send a pull request, etc.

This structure might break down or need changing for meetings and CPs, which is why this setup is just for supplements at the moment.

## Why continue using the filename for version management?

1. It minimizes the change to procedures.  We use the same rules right now with FTP.  As a next step we can legitimately argue that all we are doing is replacing FTP with `git`.  Using the additional capabilities of `git` can be a second step after we're familiar with basic `git`.

2. The delta management tools for `git` break down for binary files like Word and Powerpoint documents.  They don't save any space or provide useful information.  They just hide the older versions, which might be counterproductive.  It's certainly an extra change for not much value.

3. For text files (which are not often used in supplement development) we would use the `git` delta management tools.  That's a path for people to become familiar.  The `git` tools are much more useful for text files.

This choice is not obviously the best choice.  There might me some hidden capability for dealing with binary files that makes the extra effort of modifying procedures for filenames worthwhile.

## What about all the proprietary extra capabilities of Github? or other `git` server vendors?

For now, we should not depend upon them.  Vendors go out of business and drop product lines.  Github is owned and operated by Microsoft, so the risk is more that Microsoft decides to drop the free product. Both Microsoft and Google have dropped products that were in widespread use at the time.  They decided it was not needed as part of their business.  

By limiting our significant dependencies to `git` capabilities we remain in a position to switch to one of the dozens of other vendors if we need to.  This doesn't mean proprietary features can't be used by individual contributors.  It does mean we don't introduce a requirement that other contributors have access to those proprietary features.  (This also means that if some DICOM member has a corporate problem with depending on Microsoft they can still use the public `git` access to clone copies for use and for making suggestions to editors.)
