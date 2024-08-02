# Social Triangle Using Apache Spark

The goal of this notebook is to implement a Social Triangle algorithm using Spark. For example, given the email dataset, we will list all "reciprocal" relationships in the company. More specifically:

If A emails B and B emails A, then A and B is *reciprocal*.

If A emails B but B doesn’t email A, then A and B is *directed*.

**Dataset:** We will use a subset of the open [Enron Email Dataset](https://www.cs.cmu.edu/~./enron/ "Enron Email Dataset"), which contains approximately 10,000 simplified email headers from the Enron Corporation. A subset of the data is available as **enron_mails_small.csv**

The file contains 3 columns *Date*, *From*, and *To*. Their description is as follows:

|Column name|Description|
|--|--|
|Date |The date and time of the email, in the format YYYY-MM-DD hh-mm-ss, <br />e.g. "1998-10-30 07:43:00" |
|From |The sender email address, <br />e.g. "mark.taylor@enron.com" |
|To | A list of recipients' email addresses separated by semicolons ';', <br />e.g. "jennifer.fraser@enron.com;jeffrey.hodge@enron.com" |

Note that, we only care about users employed by Enron, i.e. only relationships where email addresses end with *'@enron.com'*.

The expected output is also provided below. For each reciprocal relationship, please output a tuple consisting of two strings. The first one is always **'reciprocal'**. And the second one is a string showing the name of the two person in the following format: **'Jane Doe : John Doe'**. The names should be presented in the lexical order, i.e. there will not be a 'John Doe : Jane Doe' since 'Jane' is ordered before 'John.

Though the dataset only contains email addresses, not actual names, we're assuming that the email aliases were created based on their name. For example:

|Email Address|Converted Name|
|--|--|
|mark.taylor@enron.com|Mark Taylor|
|alan.aronowitz@enron.com|Alan Aronowitz|
|marc.r.cutler@enron.com|Marc R Cutler|
|hugh@enron.com|Hugh|
