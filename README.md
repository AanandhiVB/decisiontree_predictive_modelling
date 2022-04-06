# decisiontree_predictive_modelling

## Problem Statement

An insurance provider (US based) offers health insurance to customers. The provider assigns a PCP (primary care physician) to each customer. The PCP addresses most health concerns of the customers assigned to them.  For various reasons, customers want change of PCP. It involves significant effort for the provider whenever the customer makes a change of PCP.

You will find a subset of the insurance provider data along with PCP changes. The provider likes to understand why are members likely to leave the recommended provider. Further, they like to recommend a provider to them that they are less likely to leave.

The dataset consists of following fields:
| Columns | Description |
|--|--|
| Id | Column identification field |
| Outcome | Member changed to his/her preferred primary care provider instead of auto assigned to. <ul><li>0: Member keeps the auto assigned provider.</li><li>1: Member changed to this provider by calling customer service.</li></ul>
| Distance | Distance between member and provider in miles
| Visit_count | Number of claims between member and provider
| Claims_days_away | Days between member changed to/assigned to the provider and latest claim between member and provider |
| Tier | Provider Tier from service, values - 1, 2, 3, 4. Tier 1 is highest benefit level and most cost-effective level |
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
 - Select a method for performing analytics
 - Preprocess the data to enhance quality
 - Carry out descriptive summarization of data and make observations
 - Identify relevant, irrelevant attributes for building model
 - Perform appropriate data transformations with justifications
 - Generate new features if needed
 - Carry out the chosen analytic task. Show results including intermediate results, as needed
 - Evaluate the solutions
 - Look for refinement opportunities


## Inferences


**Objective**

An health insurance provider (US based) offers health insurance to customers. The provider assigns a PCP (primary care physician) to each customer. The PCP addresses most health concerns of the customers assigned to them.  For various reasons, customers want change of PCP. It involves significant effort for the provider whenever the customer makes a change of PCP. You will find a subset of the insurance provider data along with PCP changes. The provider likes to understand why members are likely to leave the recommended provider. Further, they like to recommend a provider to them that they are less likely to leave.

**Exploratory Data analysis (EDA)** 

 - Read the data from “*DataSet_PCP_Change.csv*” csv file

 - **Data Summary:** 

	 - **Summary of Healthcare Insurance Enrolled Members (Auto PCP/Switched PCP)** – Total 3,130 members have enrolled to Healthcare insurance benefits, of that 127 (4%) members have switched from assigned Auto PCP and interestingly 96% members are on Auto PCP
	
		<table>
		      <tr>
		        <th></th>
		        <th colspan="2" align="middle">Enrolled Members</th>
		      </tr>
		      <tr>
		        <th>Category</th>
		        <td><b>Count</b></td> 
		        <td><b>Percentage</b></td>
		      </tr>
		       <tr>
		        <th>Auto PCP</th>
		        <td>3,003</td> 
		        <td>96%</td>
		      </tr>
		       <tr>
		        <th>Switched PCP</th>
		        <td>127</td> 
		        <td>4%</td>
		      </tr>
		       <tr>
		        <th>Total</th>
		        <td>3130</td> 
		        <td>100%</td>
		      </tr>
		    </table>

	- **Summary of Gender - Enrolled Members (127 Members) Who Switched PCP** – Total 127 members have switched PCP, of that 62 (48%) are kids and 65 (52%) are adults
	   <table>
		      <tr>
		        <th></th>
		        <th colspan="2" align="middle">Switched PCP Members</th>
		      </tr>
		      <tr>
		        <th>Gender</th>
		        <td><b>Count</b></td> 
		        <td><b>Percentage</b></td>
		      </tr>
		       <tr>
		        <th>Kids</th>
		        <td>62</td> 
		        <td>48%</td>
		      </tr>
		       <tr>
		        <th>Adults</th>
		        <td>65</td> 
		        <td>52%</td>
		      </tr>
		       <tr>
		        <th>Total</th>
		        <td>127</td> 
		        <td>100%</td>
		      </tr>
		    </table>

	 -  **Summary of Pediatric PCP/Non-Pediatric PCP Vs Switched PCP Members (127 Members)** – There are 127 members who have switched PCP (pediatric and non-pediatric), of that 12% of members among Tier-1, 13% of members among Tier-2, 6% of members among Tier-3 are treated by non-pediatrician (assumption here being switched PCP members are not assigned the appropriate physician, so there's high possibility that they will request further to get new PCP assigned. Therefore, here there is an opportunity to improve the model)
		<table>
		  <thead>
		    <tr>
		    <th colspan="2" align="middle">Tier</th>
		    <th colspan="2" align="middle">Tier-1</th>
		    <th colspan="2" align="middle">Tier-2</th>
		    <th colspan="2" align="middle">Tier-3</th>
		    <th colspan="2" align="middle">Tier-4</th>
		    </tr>
		    <tr>
		    <th>Pediatric/Non-Pediatric</th>
		    <th>Adult/Kid</th>
		    <th>Count</th>
		    <th>Percentage</th>
		    <th>Count</th>
		    <th>Percentage</th>
		    <th>Count</th>
		    <th>Percentage</th>
		    <th>Count</th>
		    <th>Percentage</th>
		   </tr>
		  </thead>
		  <tbody>
		    <tr>
		     <td>Non-Pediatric PCP</td> 
		      <td>Adult</td>
		      <td>35</td> 
		      <td>54%</td>
		      <td>8</td>
		      <td>27%</td>
		      <td>10</td>
		      <td>63%</td>
		      <td>11</td>
		      <td>69%</td>
		   </tr>
		   <tr>  
		  <td>Non-Pediatric PCP</td> 
		      <td>Kid</td>
		      <td>8</td> 
		      <td>12%</td>
		      <td>4</td>
		      <td>13%</td>
		      <td>1</td>
		      <td>6%</td>
		      <td>-</td>
		      <td>0%</td>
		  </tr>
		 <tr>  
		  <td>Pediatric PCP</td> 
		      <td>Adult</td>
		  <td>-</td> 
		  <td>0%</td>
		  <td>-</td>
		  <td>0%</td>
		  <td>1</td>
		  <td>6%</td>
		  <td>-</td>
		  <td>0%</td>
		</tr>
		<tr> 
		 <td>Pediatric PCP</td> 
		      <td>Kid</td>
		  <td>22</td> 
		 <td>34%</td> 
		  <td>18</td> 
		  <td>60%</td> 
		 <td>4</td> 
		  <td>25%</td> 
		  <td>5</td> 
		  <td>31%</td> 
		</tr>
		<tr>
		<td colspan="2" align="middle"><b>Total</b></td> 
		  <td>65</td> 
		 <td>100%</td> 
		  <td>30</td> 
		  <td>100%</td> 
		 <td>16</td> 
		  <td>100%</td> 
		  <td>16</td> 
		  <td>100%</td> 
		</tr>
		</tbody>
		</table>

**Model Building**

 - Used the Decision Tree Regressor to recommend the appropriate PCP to members - 30% of PCP Dataset was used for testing and 70% of PCP Dataset was used for training

 - Achieved a model accuracy of 96%
