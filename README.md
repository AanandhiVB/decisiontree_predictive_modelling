# decisiontree_predictive_modelling

## Problem Statement

An insurance provider (US based) offers health insurance to customers. The provider assigns a PCP (primary care physician) to each customer. The PCP addresses most health concerns of the customers assigned to them. For various reasons, customers want change of PCP. It involves significant effort for the provider whenever the customer makes a change of PCP.

You will find a subset of the insurance provider data along with PCP changes. The provider likes to understand why are members likely to leave the recommended provider. Further, they like to recommend a provider to them that they are less likely to leave.

The dataset consists of following fields:
| Columns | Description |
|--|--|
| Id | Column identification field |
| Outcome | Member changed to his/her preferred primary care provider instead of auto assigned to. <ul><li>0: Member keeps the auto assigned provider.</li><li>1: Member changed to this provider by calling customer service.</li></ul>
| Distance | Distance between member and provider in miles | Column identification field
| Visit_count | Number of claims between member and provider| Column identification field
| Claims_days_away | Days between member changed to/assigned to the provider and latest claim between member and provider |
| Tier| Provider Tier from service, values - 1, 2, 3, 4. Tier 1 is highest benefit level and most cost-effective level |
| Fqhc | Value 0 or 1 <ul><li>1: Provider is a certified Federally Qualified Health Center</li></ul>
| Pcp_lookback | Value 0 or 1 <ul><li>1: The provider was the member's primary care provider before</li></ul>
| Family_Assignment | Value 0 or 1 <ul><li>1: The provider is the pcp of the member in the same family</li></ul>
| Kid | Value 0 or 1 <ul><li>1: Member is a kid. (under 18 for state of New York)</li></ul>
| Is_Ped | Value 0 or 1 <ul><li>1: Provider is a pediatrician</li></ul>
| Same_gender| Value 0 or 1 <ul><li>1: Provider and member are the same gender</li></ul>
| Same_language | Value 0 or 1 <ul><li>1: Provider and member speak the same language</li></ul>
| Same_address | Value 0 or 1 <ul><li>1: The re-assigned provider has the same address as the provider pre-assigned</li></ul>

**Aim:**
-   Build a Predictive Model 
-   Evaluate the model
-   Refine the model, as appropriate

**Perform the following tasks:**
 - Select a method for performing the analytic task
 - Preprocess the data to enhance quality
 - Carry out descriptive summarization of data and make observations
 - Identify relevant, irrelevant attributes for building model
 - Perform appropriate data transformations with justifications
 - Generate new features if needed
 - Carry out the chosen analytic task. Show results including intermediate results, as needed
 - Evaluate the solutions
 - Look for refinement opportunities
