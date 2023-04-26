## List serve Requirements

The requirements for a DICOM list serve are described below.  The example of Mailman, the GNU Mailing List Manager, is used so that people can experiment and see what terminology means. (See https://www.gnu.org/software/mailman/)  This is not to indicate that Mailman is the only or best choice.  Mailman is a well known list serve manager that establishes a minimum capabilities bar.  Something better is not a problem.

An example of a web interface to Mailman can be found at https://lists.mailman3.org/archives/list/mailman-users@mailman3.org/  Some of the requirements below refer to this example.

- Support threading messages
  - The email generated must comply with the RFCs for email.  (This might seem obvious, but the discourse email service that we currently use does not.)  SMTP strongly suggests that all emails include a header with a unique ID for the email message.  (Discourse includes the Message-id header, but does not generate unique IDs.  As might be expected, this poses a significant burden on some email clients.)  We require the support of message-id.

    We require support for the "References" and "In-reply-to" headers, because without these linkages between related messages can be lost.  (Discourse does not do this.)  The RFC lists these as "should".
  - The list must accept new messages and replies by email, and should accept new messages by means of a web interface.  See the example for an example of web interface that displays recent threads and allows sending new messages.  Is it acceptable for the server to require the use of References or In-Reply-To headers for threaded replies?  Should it try to repair messages from clients that lack References or In-reply-to capability?
  - Web GUI shall generate threading headers when used to make a response.
  - Web GUI shall support threading for display.
- The server must allow a user to bulk download messages, and have access to the archives.  See the example, where download is a button near the top of the right hand column.
- Email security features must be tracked.  DKIM, DMARC, etc. are routinely evolving requirements used to eliminate fraud, forgery, spam, etc.  Unfortunately the attackers and defenders are intelligent humans and regularly change their methods.  Google mail is famous for aggressive interpretation of secret security policies that interfere with list serve operations.
- Access control should allow for a choice of at least:
    - Public read access
    - Member-only read access 
    - Member read/write access
    - List manager cleanup (for spam, fraud, etc.)
- We need both public read and private read lists.  Public read should have low effort signup with reasonable spam and fraud prevention features.  Private lists may require list manager approval.  The management effort needed for these should be low.
- Attachments, etc. must be allowed for messages.  These may be subject to screening for malware, spam, etc.  A suspect message can be rejected, but should not be modified and then sent to the list.
- Size limits may be placed on messages.  An oversize message can be rejected, but should not be modified and then sent to the list.  (Many organizations limit message size to be under 10 MB and reject oversize messages.)
- HTML-only email should be discouraged.  Clients that send HTML-only bodies are inevitable, so a means of dealing with such messages will be needed.  Web-based sending and regular mail sending should not introduce HTML-only messages, nor should it encourage HTML-only messages.

| Requirement | Mailman | 
|-------------|-------|
| Non-proprietary | yes |
| Threading responses | yes |
| Email responses | yes |
| Web GUI responses | yes |
| Threading Web display | yes |
| User download messages in bulk | yes |
| DKIM, DMARC, etc. security | yes |
| User access controls | yes |
| Public and private lists | yes |
| Attachments allowed | yes |
| Messages not modified | yes |
| Subject, user headers not modified | yes |