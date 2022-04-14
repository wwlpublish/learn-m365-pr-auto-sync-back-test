Deciding on the best migration path of your users' email to Microsoft 365 can be difficult. Your migration performance will vary based on your network, mailbox size, migration speed, and so on. Before you start an email migration, review the limits and migration performance and best practices for Exchange Online. By doing so, you can ensure that you get the performance and behavior you expect after migration.

For migrations from an existing on-premises Exchange Server environment, you can migrate all email, calendar, and contacts from user mailboxes to Microsoft 365. Microsoft 365 provides a [Mail Migration Advisor](https://aka.ms/MailSetupAdvisorFromEDA) to help you move mailboxes from your current mail system to Exchange Online in Microsoft 365 with automated tools and step-by-step guidance. The advisor will ask you questions about your existing on-premises Exchange environment. It will then recommend the best migration path for your organization. It makes its recommendation based on:

 -  Your current mail system.
 -  The number of mailboxes you want to migrate.
 -  How you plan to manage users and user access.<br>

For migration recommendations, refer to the following section that matches your source system.<br>

### Your source system is Exchange 2003 or Exchange 2007

If your source system is Exchange 2003 or Exchange 2007, consider the following options.<br>

> [!WARNING]
> The cutover migration supports moving up to 2000 mailboxes. However, due to length of time it takes to create and migrate 2000 users, it's more reasonable to migrate 150 users or less.<br>

:::row:::
  :::column:::
    **Number of mailboxes**
  :::column-end:::
  :::column:::
    **How quickly do you want to migrate?**
  :::column-end:::
  :::column:::
    **Use**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Fewer than 150
  :::column-end:::
  :::column:::
    Over a weekend or a few days.
  :::column-end:::
  :::column:::
    **Cutover migration**

  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Fewer than 150
  :::column-end:::
  :::column:::
    Slowly, by migrating a few users at a time.
  :::column-end:::
  :::column:::
    **Staged migration**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Over 150
  :::column-end:::
  :::column:::
    Over a weekend or a few days.
  :::column-end:::
  :::column:::
    **Staged migration**

If your organization has more than 150 mailboxes, the best method to use is staged migration. This option enables you to migrate a limited number of users at a time. This option is recommended because cutover migration performance suffers when you try to migrate more than 150 mailboxes.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Over 150
  :::column-end:::
  :::column:::
    Slowly, by migrating a few users at a time.
  :::column-end:::
  :::column:::
    **Staged migration**
  :::column-end:::
:::row-end:::


If the mailboxes you're migrating contain a large amount of data, you can also use the Import service in the Microsoft 365 compliance center to import PST files to Microsoft 365. You can use the Microsoft 365 Import Service to either ship the files or to import them across the network.

> [!TIP]
> If you have a large number of mailboxes (5,000+), you may want to hire a partner to help you migrate your email data. You can search for partners on the [Microsoft solution providers](https://www.microsoft.com/solution-providers/) page.

### Your source system is Exchange 2010, 2013 or 2016

If your source system is Exchange 2010, Exchange 2013, or Exchange Server 2016, consider the following options.<br>

> [!WARNING]
> The cutover migration supports moving up to 2000 mailboxes. However, due to length of time it takes to create and migrate 2000 users, it's more reasonable to migrate 150 users or less.

:::row:::
  :::column:::
    **Number of mailboxes**
  :::column-end:::
  :::column:::
    **How quickly do you want to migrate?**
  :::column-end:::
  :::column:::
    **Use**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Fewer than 150
  :::column-end:::
  :::column:::
    Over a weekend or a few days.
  :::column-end:::
  :::column:::
    **Cutover migration** or **Express migration**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Fewer than 150
  :::column-end:::
  :::column:::
    Slowly, by migrating a few users at a time.
  :::column-end:::
  :::column:::
    **Exchange Hybrid migration**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Over 150
  :::column-end:::
  :::column:::
    Over a weekend or a few days.
  :::column-end:::
  :::column:::
    **Exchange Hybrid migration**

If your organization has more than 150 mailboxes, the best method is to use an Exchange hybrid migration. This option enables you to migrate a limited number of users at a time. This option is recommended because cutover migration performance suffers when you try to migrate more than 150 mailboxes.
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    Over 150
  :::column-end:::
  :::column:::
    Slowly, by migrating a few users at a time.
  :::column-end:::
  :::column:::
    **Exchange Hybrid migration**
  :::column-end:::
:::row-end:::


If the mailboxes you're migrating contain a large amount of data, you can also use the Import service in the Microsoft 365 compliance center to import PST files to Microsoft 365. You can use the Microsoft 365 Import Service to either ship the files or to import them across the network.

> [!TIP]
> If you have a large number of mailboxes (5,000+), you may want to hire a partner to help you migrate your email data. You can search for partners on the [Microsoft solution providers](https://www.microsoft.com/solution-providers/) page.

### Your source system is Exchange Server 2000 or earlier

For earlier versions of Exchange server, you have no choice but to use an I**MAP migration.**<br>

### Your source system is another email system

For other email systems that support IMAP, you can use I**MAP migrations**.<br>

Depending on your source system, see one of the following articles for assistance:

 -  [Migrate Google Workspace (formerly G Suite) mailboxes to Microsoft 365 or Office 365](/exchange/mailbox-migration/migrating-imap-mailboxes/migrate-g-suite-mailboxes).
 -  [Migrate other types of IMAP mailboxes to Microsoft 365 or Office 365](/exchange/mailbox-migration/migrating-imap-mailboxes/migrate-other-types-of-imap-mailboxes).
    
    This article includes the instructions for the migration of CSV files for Exchange, Mirapoint, Dovecoat, and Courier IMAP.
 -  [IMAP migration in the Microsoft 365 admin center](/exchange/mailbox-migration/migrating-imap-mailboxes/imap-migration-in-the-admin-center).

If the mailboxes you're migrating contain a large amount of data, you can also use the [Import service](/microsoft-365/compliance/importing-pst-files-to-office-365) to import PST files to Microsoft 365. You can use the Import Service to either ship the files or to import them across the network.
