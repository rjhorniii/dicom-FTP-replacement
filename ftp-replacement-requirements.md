# FTP Replacement Required/Desirable Features

## FTP Features (required in a replacement)

* Non-proprietary 

   * Participants will face organizational restrictions on the use of software, especially proprietary software.  
   * Proprietary systems can vanish on short notice (Google and Microsoft have both cancelled major services with only 3 months notice.  Smaller vendors have vanished more quickly)
   * Multiple sources usually improves implementation options
   * We're a standards organization.  We should avoid using proprietary solutions ourselves.

* Usable from a browser 
    The removal of FTP support from browsers is one major factor behind the need to replace FTP.
    * Read access and ability to copy one file
    * able to navigate a directory tree

* Access control  (minimum features)
    * Public read access
    * Private read/write access
    * Reasonably flexible so that it does not interfere with security policies of participating organizations.
    * MFA, role support are desirable.

* Able to mirror 
    * Required for command line and client tools.  The ability to mirror a repository/directory from the server copy onto a client is vital.  A "mirror" will find and download all the "new" files since the previous copy, without downloading the entire repository (unless a full new copy is requested).  The GUI and command line FTP clients on MacOS, Windows, and Linux have this feature.
    * Desireable for browser. 
    * More structured change management clustering is a desirable extension, but not at the cost of mirroring.

* Able to be scripted
    * A command line version must exist that allows the download/upload to be embedded into scripts and run from other programs. (FTP has this for MacOS, Windows, Linux).

* Directory/File structure model is supported.  

    While wiki's, etc., can be useful, the existing tooling is directory/filename structured.  Most of the word processing and software development tooling on Windows, MacOS, and Linux are directory/filename structured.  Sticking with directory/file structure enables the local use of a wide variety of tooling on clients without burdening the server with all the demands of supporting all possible features available on the clients.

* Not viewed as a cybersecurity hazard.  

    Whether deserved or not, FTP is increasingly viewed as a security hazard by IT organizations and is blocked.  This is a change from when we first used FTP.  This problem is not unique to FTP.  Many file sharing services (e.g., Google Drive, IPFS, One Drive, iCloud) are being viewed as security hazards and are being restricted to various degrees depending upon the threat model of the IT organizations.

* Storage for documents

    These are text or binary files that are typically less than 10MB in size.

* Storage for large files

    Some method must exist for dealing with large files.  This could be separate from the FTP solution for documents and meetings, in which case some form of links within the FTP replacement are needed.  These links should be usable from both the browser and the client software.
    * Sample DICOM files are potentially large binary files up to 2GB in size.
    * Some people want to store video or audio recordings that are routinely 100MB or larger

* Actively multi-user.

    Typical meeting directory use has multiple persons reading and writing to the meeting directory during the meeting. This should not be the source of problems.

* Limited Internet

    Useable for travelers on airplanes, trains, waiting rooms, hotels, etc. that have intermittent or otherwise limited Internet access.  This also addresses those with limited infrastructure access.


## FTP Gaps and missing desireable features

* Read access and ability to copy a version in time (i.e., the database as of dd-mm-yyyy), 
* Ability to preserve history of changes (who, what, when)
* Ability to support various industry common change management workflows, such as branch/merge.
* Redundant independent servers
* MFA authentication of users, at least for any form of writing or modification.  (This may become a legal requirement in the United States.)
* Integrity and source verification of contents.  (This would link the MFA authentication with the copies and digital signatures provided by the servers.)

| Requirement | | FTP | Git | Confluence |
|-------------|-------|-----|-----|-----|
| Non-proprietary | | yes | yes | no |
| Browser support | | no (previously yes) | yes | yes | 
| Command line support | | yes | yes | no? |
| GUI support (non-browser) | | yes | yes | ? |
| Access Control | | minimal | 2FA+ | ?|
| Mirror | | yes | yes | no |
| Hierarchical model (directory/file) | | yes | yes | no |
| Not viewed as security hazard | | no (previously yes) | yes | ? |
| Storage for documents | | yes | yes | yes |
| Storage for large files | | yes | optional extension | ? |
| Multiple active users | | yes | yes | yes ?|
| Useable from limited Internet | | yes | yes | ? |


| Desirable | | FTP | Git | Confluence |
|-----------|-------|-----|-----|---|
| Historical view | | no | yes | no |
| Metadata for changes | | no | yes | yes |
| Integration with change management workflows | | no | yes | ? | 
| Redundant servers | | no | yes | ? |
| Change authentication | | no | yes | no |
| Integrity verification tools | | no | yes | ? |