If your current messaging system only supports IMAP connections, the IMAP migration process may provide the proper solution to migrate to Exchange Online. It’s important to note that an IMAP migration simply migrates emails and the folder structure. It doesn't migrate any other objects, such as calendar items or contacts.

### Requirements for an IMAP migration

You need two things to migrate the contents of users' mailboxes from an IMAP messaging system to their Exchange Online mailboxes:

 -  A CSV file that lists all the mailboxes to be migrated.
 -  The IMAP Migration wizard that’s located in the Exchange Admin Center.

Supported IMAP servers include Google Mail or other IMAP-based messaging systems.

### Limitations of the IMAP migration process

There are several limitations that you must consider before running an IMAP migration, including:

 -  You can only migrate message items in a user's mailbox. You can' migrate contacts, calendar items, or tasks.
 -  You can migrate a maximum of 500,000 mail items from a user’s mailbox (emails are migrated from newest to oldest).
 -  The maximum size of a single message item that can be migrated is 35 MB.
 -  If you had previously limited the connections to your source email system, you should consider increasing them to improve migration performance. Common connection limits include client/server total connections, per-user connections, and IP address connections on either the server or the firewall.

### The effect of an IMAP migration on users

To migrate email, you need access to the user mailboxes in your source email system. If you know the user passwords or can access their mailboxes by using administrative credentials, there won’t be any effect on users until you shut down your source email system.

If you can’t access user mailboxes, you’ll have to reset your users’ passwords. By resetting their passwords, you can access the user mailboxes by using a new password that you know. Since your users won’t know the new password, they'll be unable to access their old mailboxes during the email migration. As a best practice, you should provide your users with their new Microsoft 365 credentials so they can sign into their mailbox in Exchange Online.
