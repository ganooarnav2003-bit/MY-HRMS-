# ARCHITECTURE.md  (you write this; get it signed off before any code)

## Stack
Framework, hosting, database, auth, email. Why each? One alternative you rejected and why.

## System diagram
Browser, app server, database, auth provider, email service, AI model API. Arrows between them. Mark where EVERY role check happens.

## Data model
Final tables, keys, relationships, constraints (unique, foreign key, check). Draw an ER diagram.
Questions to answer:
- Why are statutory and bank details in separate tables from employees? (hint: row-level security)
- Should "available balance" be stored or calculated? What goes wrong if stored?
- What stops two attendance rows for the same employee on the same date?

## Access control
How does a signed-in user map to an employee row and role? Which tables have RLS and what is each rule?

## Business logic location
Where do balance, working-day count and day-status rules live (DB function, server code, or both) and why?

## AI agent
Model and library. Tool list with inputs and outputs. What data the model can and cannot see. How writes are confirmed.

## Folder structure
By module: employees, attendance, leave, reports, agent.

## Dates and time zone
How IST is enforced from database to screen.

## Risks
The three things most likely to break and how you will test each.

## Decision log
| Date | Change | Reason |
|---|---|---|
