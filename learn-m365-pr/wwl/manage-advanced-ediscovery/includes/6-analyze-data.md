It can be difficult for organizations to review all the collected documents in a review set when a large number of documents are involved. Advanced eDiscovery provides a set of tools to make the review process more manageable, efficient, and effective. These tools help organizations analyze documents, and ultimately reduce the volume of documents to be reviewed without any loss in information. They can also help organize the documents in a coherent manner. Three of the more popular tools include:

 -  Near duplicate detection
 -  Email threading
 -  Themes

### Near duplicate detection

Consider a set of documents to be reviewed in which a subset is based on the same template and has mostly the same boilerplate language, with a few differences here and there. If a reviewer could identify this subset, review one of them thoroughly, and review the differences for the rest, they wouldn't have missed any unique information. They would have also taken only a fraction of the time to complete this process as compared to the time needed to read all the documents cover to cover. Near duplicate detection groups textually similar documents together to help make the review process more efficient.

When near duplicate detection is run, the system parses every document with text. Then, it compares every document against each other to determine whether their similarity is greater than the set threshold. If it is, the documents are grouped together.

Once all documents have been compared and grouped, a document from each group is marked as the "pivot". When reviewing your documents, you can review a pivot first and review the other documents in the same near duplicate set. This process enables you to focus on the difference between the pivot and the document that's in review.

### Email threading

Consider an email conversation that has been going on for a while. In most cases, the last email on the thread will include the contents of all the preceding emails. By reviewing the last email, you'll receive complete context of the conversation that happened in the thread. Email threading identifies such emails so that reviewers can review a fraction of the collected documents without losing any context.

Each email is a chain of individual messages. Email threading parses each email and deconstructs it down to the individual messages. It then analyzes all emails in the working set to determine whether an email has unique content or if the chain is wholly contained in a different email. At the end of the process, emails are divided into four categories:

 -  **Inclusive.** The last message in the email has unique content, and the email has all of the attachments that were included in other emails of which the content is wholly contained in this email.
 -  **Inclusive minus.** The last message in the email has unique content, but the email doesn't contain some of the attachments that were included in other emails of which the content is wholly contained in this email.
 -  **Inclusive copy.** An exact copy of an **inclusive** email or an **inclusive minus** email.
 -  **None.** The content of this email is wholly contained in at least one email that's marked as either **inclusive** or **inclusive minus**.

At a glance, this process sounds similar to conversation groupings in Outlook. However, there are some important distinctions. Consider an email conversation that got forked into two conversations. For example, someone responded to an email that isn't the latest in the conversation. As a result, the last two emails in the conversation both have unique content.

Outlook would still group the emails into a single conversation. Reading only the last email would mean missing the context of the second-to-last email, which also contains unique content. Because email threading parses out each email into individual components and compares them, email threading would mark both of the last two emails as inclusive, ensuring that you won't miss any context as long as you read all emails marked as inclusive.

### Themes

How does a person write a document? They generally start with one or more ideas they want to convey in the document, and compose using words that align with the ideas. The more prevalent an idea is, the more frequent the words that are related to that idea tend to be. This process informs how people consume documents as well. The important thing to understand from reading a document is the ideas that the document is trying to convey, which ideas appear where, and what the relationships between the ideas are.

This concept can be extended to how a person wants to consume a set of documents. They want to see which ideas are present in the sets, and which documents are talking about those ideas. Also, if they find a particular document of interest, they want to see documents that discuss similar ideas.

The Themes functionality in Advanced eDiscovery attempts to mimic how humans reason about documents. It analyzes the *themes* that are discussed in a review set and assigns a theme to documents in the review set. In Advanced eDiscovery, Themes goes one step further and identifies the *dominant theme* in each document. The dominant theme is the one that appears the most often in a document.

The Themes functionality analyzes documents with text in a review set to parse out common themes that appear across all the documents in the review set. Advanced eDiscovery assigns those themes to the documents in which they appear. It also labels each theme with the words used in the documents that are representative of the theme. Because a document can contain various types of subject matter, Advanced eDiscovery often assigns multiple themes to documents. The theme that appears most prominently in a document is identified as its dominant theme.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”