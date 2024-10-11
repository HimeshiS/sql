# Assignment 1: Design a Logical Model

## Question 1
Create a logical model for a small bookstore. 📚

At the minimum it should have employee, order, sales, customer, and book entities (tables). Determine sensible column and table design based on what you know about these concepts. Keep it simple, but work out sensible relationships to keep tables reasonably sized. Include a date table. There are several tools online you can use, I'd recommend [_Draw.io_](https://www.drawio.com/) or [_LucidChart_](https://www.lucidchart.com/pages/).

![SQL assignment 1_ERD_Q1](https://github.com/user-attachments/assets/0337e2a8-08b8-4d30-b0b8-272a8524c0df)


## Question 2
We want to create employee shifts, splitting up the day into morning and evening. Add this to the ERD.

![SQL assignment 1 ERD](https://github.com/user-attachments/assets/86d5dc51-4f85-418a-aab9-3a2f1bc619c6)


## Question 3
The store wants to keep customer addresses. Propose two architectures for the CUSTOMER_ADDRESS table, one that will retain changes, and another that will overwrite. Which is type 1, which is type 2?

_Hint, search type 1 vs type 2 slowly changing dimensions._

Bonus: Are there privacy implications to this, why or why not?
```
1) Overwriting changes: With Type 1 Slowly Changing Dimensions (SCD), changes are not tracked. The old address is overwritten with the new one, so only the current address is stored.
2) Retain changes: In Type 2 Slowly Changing Dimensions (SCD), changes are tracked by storing a new record for each address change. Historical addresses are retained along with the current address which will be added as a new row to the customer_addresses table.

Privacy implications:
There are several privacy implications to consider, particularly for Type 2:
- Data Retention: Type 2 architecture retains all past addresses, which may raise privacy concerns. 
- Data Breach Risk: Retaining multiple addresses increases the risk of exposing more customer data if a data breach occurs. 
- Regulations: Depending on the jurisdiction, laws like GDPR in the EU or PIPEDA in Canada may require customer data to be deleted or anonymized after a certain period. 
- Customer Consent: It is important to gain customer consent with Type 2 architecture where older addresses are retained.
In summary, all these factors need to be considered when making a decision on whether to choose Type I vs. Type II SCD architecture for sensitive information, such as customer address, storage. 

```

## Question 4
Review the AdventureWorks Schema [here](https://imgur.com/a/u0m8fX6)

Highlight at least two differences between it and your ERD. Would you change anything in yours?
```
1) Granularity
The small bookstore ERD is a much simpler logical model compared to the AdventureWorks schema which contains a lot more detail on customers, employees and sales, split across multiple tables. In my ERD, there is only one table per employee and customer personal details. A bookstore typically sells products other than just books such as stationary, mugs, throw rugs, etc. which my ERD does not consider. 

2) Inventory tracking
In my ERD, I did not create a separate inventory table to track quantities of products in the store whereas the AdventureWorks schema does. With my ERD, you have to extract data across different tables to compile information on inventory.

Taking these considerations into account, I would change my ERD in the following ways:
- Add a separate inventory table
- Add a more general product table that could include products other than just books. 
```

# Criteria

[Assignment Rubric](./assignment_rubric.md)

# Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `September 28, 2024`
* The branch name for your repo should be: `model-design`
* What to submit for this assignment:
    * This markdown (design_a_logical_model.md) should be populated.
    * Two Entity-Relationship Diagrams (preferably in a pdf, jpeg, png format).
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sql/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `model-design`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-4-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
