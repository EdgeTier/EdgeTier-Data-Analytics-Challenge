# EdgeTier Data Analyst Challenge

**Note**: Please do not put your solution in a public repository (GitHub etc.). We are sending this to multiple candidates and do not want anyone to have an unfair advantage.

## Challenge Description

Travel Helpers are a company which specialises in assisting people with booking extras such as car rental, hotels, dinners, and theme park passes when travelling abroad. When booking, customers will usually browse their website before making a booking through their internal booking system.

In order to support any customers who encounter difficulties using the website, or, on the day of their booking, Travel Helpers operate a live chat contact centre with over 200 employees (agents). Recently Travel Helpers have found it hard to keep track of what is going on in the contact centre and which agents are under performing.

To get back on top of things, Travel Helpers have asked you to query their database (described below) and report on three things:

1. Which agents are performing the best, and worst when it comes to the length of time it takes to handle a chat?

2. What contact reasons are driving the lowest contact resolution rates?

3. Which agents are causing customers to recontact within 3 hours most often?

Your challenge is to query the database provided using PostgreSQL and/or Python (or another language) and to answer the three questions above, presenting your findings in a way someone with a limited knowledge of data would understand.

## Submission

Please submit your queries/code along with any supporting documentation describing your findings via email to paul.minogue[at]edgetier.com.

If you wish to perform this task using Python, there is a sample Jupyter notebook provided in this repo (`sample_notebook.ipynb`) that demonstrates how you can access the raw data from our database using the database connection information.

If you wish to perform the task using PostgreSQL, I would recommend downloading [DataGrip](https://www.jetbrains.com/datagrip/) or [DBeaver](https://dbeaver.io/) as these tools make it very easy to connect to the database using the connection details you will receive via email.

## Database Description

The database provided as part of this task contains 5 tables which are summarised below:

- **interactions**: This is the base table which contains information such as start time, the agent ID, the contact reason ID about each chat over a 3 month period.

- **interaction_metrics**: This table provides handling times and query resolution information for each interaction

- **contact_reasons**: Provides a mapping of each contact_reason_id to a contact reason

- **agents**: Provides first and last name information for each agent who works at the contact centre

- **customers**: Provides the email addresses for each customer who contacts the contact centre
