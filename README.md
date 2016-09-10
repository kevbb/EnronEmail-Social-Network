# EnronEmails-Social-Network

When Enron collapsed in 2001, about 500.000 internal emails were made public. There are already some publications based on the data (also to be found in the former link). Jitesh Shetty and Jafar Adibi cleaned the data and put it in a MySQL database. The dump is no longer online, but was created under MySQL 4 anyway and cannot be imported in MySQL 5 without changes in the dump-file. Additionally they tried to identify the former position of the employees.

The tables/dataframes contain the following coloumns:

**Employeelist**

- eid: Employee-ID
- firstName: First name
- lastName: Last name
- Email_id: Email address (primary). This one can be found in the other tables/dataframes and is useful for matching.
- Email2: Additional email address that was replace by the primary one.
- Email3: See above
- Email4: See above
- folder: The user’s folder in the original data dump.
- status: Last position of the employee. “N/A” are unknown.

**Message**

- mid: Message-ID. Refers to the rows in recipientinfo and referenceinfo.
- sender: Email address (updated)
- date: Date.
- message_id: Internal message-ID from the mailserver.
- subject: Email subject
- body: Email body. Can be truncated in the R-Version!
- folder: Exact folder of the e-mail inclusing subfolders.

**Recipientinfo**
(Note: If an email is sent to multiple recipients, there is a new row for every recipient!)

- rid: Reference-ID
- mid: Message-ID from the message-table/-dataframe
- rtype: Shows if the reciever got the email normally (“to”), as a carbon copy (“cc”) or a blind carbon copy (“bcc”).
- rvalue: The recipient’s email address.

**Referenceinfo**

- rfid: referenceinfo-ID
- mid: Message-ID
- reference: Contains the whole email with shortend headers.
