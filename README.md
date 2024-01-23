# EdgeTier Data Analyst Challenge

**Note**: Please do not put your solution in a public repository (GitHub etc.). We are sending this to multiple candidates and do not want anyone to have an unfair advantage.

## Challenge Description

### Part 1

Travel Helpers are a company which specialises in assisting people with booking extras such as car rental, hotels, dinners, and theme park passes when travelling abroad. When booking, customers will usually browse their website before making a booking through their internal booking system.

In order to support any customers who encounter difficulties using the website, or, on the day of their booking, Travel Helpers operate a live chat contact centre with over 200 employees (agents). Recently Travel Helpers have found it hard to keep track of what is going on in the contact centre and which agents are under performing.

To get back on top of things, Travel Helpers have asked you to query their database (described below) and report on following:

1. Which agents are performing the best, worst, and who are the most consistent when it comes to the length of time it takes to handle a chat?

2. What contact reasons are driving the lowest contact resolution rates?

3. Which agents are causing customers to recontact within 3 hours most often?

4. Which agent uses each contact reason the most (as a % of their total chats) and what is that %?

5. For a week of data of your choice, how often was each agent handling more than 1 chat at a time (as a % of their overall number of chats)? e.g. Contact reason X was used by Agent A the most, Contact reason Y was used by Agent B the most, etc.

Your challenge is to query the database provided using PostgreSQL answer the questions above, presenting your findings in a way someone with a limited knowledge of data would understand.

### Part 2

Travel Helpers have recently hired a junior data analyst to help them get more insights from the data made available to them via EdgeTier. The analyst has written following SQL query to calculate the number of contacts per reason per day, however the team in Travel Helpers have asked could we take a look at the query and speed it up as it is currently taking too long to run for them:

```sql
with totals_per_day as (
    select date(end_date_time) as date, interaction_id, count(*) as total
    from interactions
    join contact_reasons using (contact_reason_id)
    group by date(end_date_time), interaction_id
)
select date(start_date_time), contact_reason, count(*)
from interactions
join contact_reasons using (contact_reason_id)
join customers using (customer_id)
join totals_per_day on date = date(start_date_time)
group by date(start_date_time), contact_reason
```

How would you optimse the above query and what feedback would you give Travel Helpers' new hire for writing similar kinds of queries in the future?

## Submission

Please submit your queries/code along with any supporting documentation describing your findings via email to paul.minogue[at]edgetier.com.

## Database Description

The database provided as part of this task contains 5 tables which are summarised below:

- **interactions**: This is the base table which contains information such as start time, the agent ID, the contact reason ID about each chat over a 3 month period.

- **interaction_metrics**: This table provides handling times and query resolution information for each interaction

- **contact_reasons**: Provides a mapping of each contact_reason_id to a contact reason

- **agents**: Provides first and last name information for each agent who works at the contact centre

- **customers**: Provides the email addresses for each customer who contacts the contact centre
