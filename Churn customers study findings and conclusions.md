# **Retrospective Observational Study for The Bank's Customers Churn**


## **Introduction**

![lost](https://github.com/hayasalman/Qualitative-Research-Observational-Study-Causal-Inference/assets/71796909/a0171be3-c30e-4b3f-b70a-aba1f1823434)


Churning is a common problem that we see in every industry, at the end of the day, companies always aim for the ultimate goal of increasing their revenue. Therefore, churn analysis plays a very important role in every organization. Churn analysis helps businesses to identify the reason behind customer churn and helps in reducing it through incentivized offers by reminding churned customers about the new updates, giving limited-time access to Premium services or Plans, proactively engaging with them, notifying them about loyalty points expiration and so on.

Bank customer churn, also known as customer attrition, refers to the phenomenon where customers stop doing business with a bank or switch to another bank. Churn is a critical metric for banks as it directly impacts their customer base and revenue. Customer churn can occur due to various reasons, such as dissatisfaction with services, better offers from competitors, changes in financial needs, or poor customer experiences.



## **Exploaraty Data Analysis (EDA) Insights**

![corr_matrix](https://github.com/hayasalman/Qualitative-Research-Observational-Study-Causal-Inference/assets/71796909/b66e9489-f8cd-4a12-bd25-c56874eebf18)


- Exited is perfectly positively correlated with the Complains.
- Exited has a very weak correlation with whether a customer is an active member or not, the amount in customers' balance, and customers' gender.
- Also, Exited is correlated with the Customer Age.


*As we observed from the correlation matrix above, there are many possible factors that are associated with the customers' decision to leave or stay with the bank. We can study these variables more closely to conclude if they are confounders/causal links to the customer churn.*


**Complained Vs. Non-complained Customers Churn Rate**

- The churn rate of the cusomers who complained before: **37.02%**
- The churn rate of the cusomers who didn't complained before: **0.073%**

**Females Vs Males Churn Rate**

- The churn rate of the female cusomers: **20.37%**
- The churn rate of the male cusomers: **16.73%**

**Active Vs. Inactive Customers Churn Rate**

- The churn rate of the non-active member cusomers: **23.72%**
- The churn rate of the active member cusomers: **13.38%**

**Over 37 Years Old Vs. Below 37 Years Old Customers Churn Rate**

- The churn rate of age category over +37 years old: **25.66%**
- The churn rate of age category younger than 37 years old: **7.52%**

**Over 100K USD Vs. Below 100K USD Customers Churn Rate**

- The churn rate of balance category over 100K USD : **19.71%**
- The churn rate of balance category less 100K USD : **13.46%**


### **Key Observations**

- Almost every customer in the bank's customer base who complained before ended up churn, in fact the churn rate of those customers who complained before is **37.02%**, which is the highest churn rate compared to all other churn rates.


- As we observed the churn rate of the female customers is slightly higher than the churn rate of the male customers by **+4.26%**.


- The customers who are active members are less likely to churn compared to those customers who are non-active members.


- By looking at customers' ages we can say that when they are **above 37 years old**, they tend to have a high churn rate compared to those who are **younger than 37 years old**.


- The customers who have an account balance of **over 100k USD** are more likely to churn.

### **The Design Of The Study : Retrospective Case Control Observational Study**


- Unlike the Randomized Control Trials (RCTs), it's known that in observational studies, fate will decide which participants will be assigned to the treatment and whom won't. Such a study of the churned customers where in the real world scenario, no business would agree to deliberately upset their customers to measure the response since it will come with the cost of losing the customers, therefore retrospective observational research becomes handy and perfect for such a situation.

- We sampled the original dataset in which each group size (N) will be as same as possible, and to eliminate any systematic biases.

- **Cases**: churned customers.
- **Controls** : customers who didn't churn.
- **The response**: customer churn.

- The study aims to determine if the associations between the groups of interest and the outcome are really meaningful in a casual way, and if this phenomenon of these interactions between the group of interest and the outcome that we observed has happened due to these relationships, or instead, we might say we suspect that other factors were absent play a certain role in causing the outcome or at least affect this outcome in an indirect path, which is a potential confounding or perhaps an effect modification.


**Fisher Exact Test For The Dependency**

At the significant level of (0.05), the fisher exact hypotheses:

- **H0** : the relationship between the independent and the dependent variable is statistically insignificant.
- **Ha** : the relationship between the independent and the dependent variable is statistically significant.


**Cochran Mantel Haenszel Chi² Test For The Stratification**


Whereas, at the significant level of (0.05), the Cochran Mantel Haenszel Chi² test hypotheses:

- **H0**: the individual stratum odds ratios are all equal to one.
- **Ha**: that at least one odds ratio is different from unity.


### **Assumption 1**

Based on the customer gender, we may say it is absolutely that simple the bank must expect the female customers to churn as they are more likely to leave the bank than the male customers as observed. As a gesture, the bank must start gaining more male customers.

Hypothetically saying the customer's gender determines if the customer decides to stay or churn in which the female customer's churn rate is higher than male customers' churn rate as observed. Therefore, the research question is: did the customer's gender increase the risk of churn, what's the nature of the interaction between the customers' gender and churn, and are there any other potential confounding variables or effect modifiers that affect the customer's decision by staying or leaving besides the gender?

**Fisher exact test results show that:**

- The female customers have **1.7x** times the odds of churn than the male customers.
- The association between the customers' gender and customer churn is statistically significant.

### **Stratification**

**Stratified by complaints, and based on cochran mantel haenszel chi² test results:**

- With the common-odds ratio of **0.54**, the odds of churn are almost equal for males and females, and the p-value of **0.1274** indicates that: although customers' gender and customer churn seem to be associated, by controlling the complaint reveals that customers' gender and customer churn are independent. Whereas, the true differences in churn patterns might exist due to whether the customers complained or not.

- Stratify analysis focuses on the effect that complaints on both male and female customers and their decision whether to stay or leave the bank according to this CMH test the effect of customers' gender is not statistically significant in which this interaction between the customers' gender and churn is not in the causal pathway which implies that customers' gender shouldn't be the reason for the churn.

- It doesn't matter what the customers' gender, the adjusted odd ratios for both female and male customers will be very close if they did complain before.

- The magnitude of confounding by the complaints is **70%** which is much higher than the cutoff percentage of 10%, where there's no doubt that the confounder is mixing up the true relationship between customers' gender with the customers' churn.


### **Assumption 2**

Based on what is observed, we can assume that: the active- member plays a certain role in knowing about the customer's decision to stay with the bank when he/she is an active member as they have less chance of churn than the customer who is a non-active member. As a solution, the bank should take a proactive approach by starting to convert all the customers into active members which should help to reduce the churn.

In other words, the customers' status determines if the customers will stay or churn as the non-active members seem to have a higher likelihood to churn than active members as observed. Therefore, the research question is: Whether the activeness of the customers's status increase the risk of churn, or are there any other potential confounding variables or effect modifiers that mix up the customer churn besides their status?


**Fisher exact test results show that:**

- The inactive customers have **2.2x** times the odds of churn than the active customers.
- The association between the activeness of the customers' status and customer churn is statistically significant.


### **Stratification**

**Stratified by complaints, and based on cochran mantel haenszel chi² test results:**

- With a p-value of **0.0006** and pooled odds ratio of **11.77**, this is a clue that the complaint is acting as an effect modifier,  as the association between the activeness of customers' status and customers' churn varies according to the strata of the covariable.


- By adding the 3rd party which is the complaints, the interaction between the activeness of the customers and the customers' churn, and the odd ratios are modified (adjusted) accordingly as well.

- Due to this effect modification, the odd ratio of the active customers dropped significantly, and it turns out the inactive customers who did complain before have **6.69x** times the odds of churn. In comparison, the active customers who did complain before have **0.05x** times the odds to churn.

### **Assumption 3**

We assume that the customers' decision to churn depends on their age. In addition, when we compared the churn rates of those who are younger or over 37 years old we found that: when the customer is above 37 years old, then he/she is more likely to end up churned in which seems the +37 age range at more risk of churn compared to the younger ages, alternatively we might say that it just happens casually and the real reason is some another factor besides the customer's age that affects the response (customers' churn). Therefore, the research question is: Whether the customer's age increase the risk of churn, or are there any other potential confounding variables or effect modifiers that mix up the customer churn besides the age?

**Fisher exact test results show that:**

- Customers who are over 37 years old have **4.9x** times the odds of churn than those who are below 37 years old.
- The association between the customers' age and customer churn is statistically significant.


### **Stratification**

**Stratified by complaints, and based on cochran mantel haenszel chi² test results:**

- The common odd ratio is **7.06** and the p-value of **0.0079** is statistical evidence of the presence of the effect modification.
- The customers who were over 37 years old and complained before have **3.1x** times the odds of churn compared to the customers who aged below 37 years old and complained before have **0.68x** times the odds of churn.
- Therefore, the complaint modifies the association between the customers' age and the customers' churn as we noticed from the adjusted odd ratios where they vary among the different customers' age groups.

## **Assumption 4**

The bank may hypothesize that no matter what, if the customer's balance is over 100K USD then they are probably gonna leave the bank in the end, and maybe it's the truth according to what we observed as the customers with a balance over 100K USD are more likely to churn than those with a balance below 100K. Therefore, the research question is: did the customer's balance increase the risk of churn, or are there any other potential confounding variables or effect modifiers that affect the customer's decision by staying or leaving besides the balance?

**Fisher exact test results show that:**

- Customers with a balance over 100K USD have **1.8x** times the odds of churn than those with a balance below 100K USD.
- The relationship between the customers' balance and customer churn is statistically significant.


### **Stratification**

**Stratified by complaints, and based on cochran mantel haenszel chi² test results:**

- A p-value of **0.2535** and pooled odds ratio of **1.3** suggest that: although the association between the customers' balance and the churn is statistically significant, we found out the significance of this correlation disappears in the presence of complaints.
- Unless we consider the 3rd party which is complaints that have a causal effect on both the balance and the churn, we may assume the true effects happen due to the customers' balance alone.
- Regardless of the amount in the customers' balance, the adjusted odd ratios for both customers with over 100K USD and below 100K USD balance will be approximately the same odds of churn if they did complain before.

- The magnitude of confounding is **30%**  which is evidence of the confoundedness existing in the relationship between the customers' balance and the churn.


## **Final Assumption**


Based on what we observed, it's reasonable to assume that every customer who complained before is gonna end up leaving the bank due to the fact those customers who did complain before have the highest churn rate. We would say that: the customers by themself ain't the cause of the problem, it's probably something about the bank's services that needs optimization, and as a solution, the bank needs to take action regarding these complaints to reduce the churn of the customers.

As observed from these assumptions above complaints always play a critical role in determining the nature of any relationship between the groups of interest and the outcome whether as a confounder or effect modifier. Therefore, the research question here is: do the complaints increase the risk of churn? and did the complaints truly have causal effects on the customers' churn?


**Fisher exact test results show that:**

- Customers who did complain before have **13x** times the odds of churn than those who didn't complain before.
- The association between the customers' complaints and customer churn is statistically significant.
- It seems the complaints have a causal effect on the outcome (customers' churn).

### **Instrumental Variables (IV)**

**We need to verify these assumptions to call any variables an instrumental variable:**

1. It's correlated with the outcome variable.
2. It doesn't have a direct causal effect on the outcome variable.
3. The correlation that we see between the instrument and the outcome is not because the instrument has a causal effect on the outcome variable. Instead, the correlation is picking up the effect of some confounding variables.
4. It's does have a causal effect on the treatment variable and that the instrument is randomly assigned to units(or "As-If").
5. By step 4, the causal effect of the instrument on the treatment is their correlation in the data.
6. It's not correlated with any other possible confounder except for the treatment.


**Instrumental Variables (IV)**

- Gender.
- Age.
- Balance.
- Activeness Status.

**The Treatment Variable**

- Complaints

Where there is a causal effect of the treatment on the outcome, which is what we are trying to get at (the treatment effect the outcome).

## **Causal Inference**

### **Directed Acyclic Graphs (DAGs)**

Based on what we found from our earlier analysis we assume the causal relationships in this dataset are represented in these graphs below:

**1. When the customers' activeness and age are modified by complaints**

![DAGs_multi-treatment_0](https://github.com/hayasalman/Qualitative-Research-Observational-Study-Causal-Inference/assets/71796909/75e1f7ea-c1f0-411c-9e5f-3706d1417077)


**2. When the customers' balance and gender are confounded by complaints**

![DAGs_multi-treatment_](https://github.com/hayasalman/Qualitative-Research-Observational-Study-Causal-Inference/assets/71796909/8224aa4d-c143-46d5-acb8-824fcbdf631c)


**3. When the customers' complaints linked to the customers' churn in causal path**

![DAGs_Causal_](https://github.com/hayasalman/Qualitative-Research-Observational-Study-Causal-Inference/assets/71796909/6a308b9d-4d1e-456e-b998-e4316a243ab3)


### **Causal Inference Assumptions**


- **Stable unit treatment value assumption (SUTVA)** :
    - **No interference**: no interventions between the group participants.
    - **Consistency**: potential outcomes should link effectively to observed data, it will be difficult to isolate the
        effect of any one version of the treatment.

  However, we brushed those assumptions aside, contenting ourselves with the assertion that they hold whenever the treatment     variable was randomized.

  We will present and verify the two fundamental assumptions of **ignorability** and **positivity**.


- **Positivity**: refers to the idea that everybody has some chance of getting either treatment.There are no positivity violations, each sample has a positive probability of belonging to both treatment groups.


- **Ignorability**: no unmeasured confounders assumption, this is done via sensitivity analysis.


### **Measuring Average Treatment Effect (ATE)**

### **conclusions**

**1. Customers' Gender and Customers' Churn Model**

   - Once we controlled for the complaints variable, the estimated average treatment effect **ATE** or the causal effect size       is **-0.000229** which is a really weak effect, as it is close to zero to the customers' gender to consider as a strong         reason for the churn.
       
**2. Customers' Activeness Status and Customers' Churn Model**

   - This estimated average treatment effect **ATE** or the effect size is **-0.0035** suggesting that the activeness of            customers' status can't be a strong candidate reason for the churn either.
   
**3. Customers' Age and Customers' Churn Model**

   - The average treatment effect **ATE** or the causal effect size is **0.0031** which is small enough to influence the            customers' decision of churn.
   
**4. Customers' Balance and Customers' Churn Model**

   - By unconfoundedness, on average the causal effect size is 0.0012 is a small effect in which the amount of the balance          could cause the churn.
    
**5. Customers' Complaints and Customers' Churn Model**

   - This estimated average treatment effect **ATE** value of **0.993** suggests that the customers' complaints increase the        probability of churn by **99%**.
   
   
 As we expected all the other variables excluding the complaints have a small influence on the outcome. Whereas complaints have the most influence, thus we say the treatment (complaints) has a causal effect on the outcome (customers' churn).


### **Refution And Sensitivity Analysis**

*We can refute the estimate to check its robustness to assumptions*


**Rufution Hypotheses**

- **H0**: There's no difference between the estimated effect and the new effect.
- **Ha**: There's a difference between the estimated effect and the new effect.

**1. Random Common Causes**

*Snapshoot for Customers' Complaints and Customers' Churn Model*

![random_common_causes](https://github.com/hayasalman/Qualitative-Research-Observational-Study-Causal-Inference/assets/71796909/ad4d5795-a039-4332-bf09-baa4407eb034)


**2. Random (Placebo) Variable**

*Snapshoot for Customers' Complaints and Customers' Churn Model*

![Screenshot 2024-01-13 190534](https://github.com/hayasalman/Qualitative-Research-Observational-Study-Causal-Inference/assets/71796909/d93e4365-ba75-46e1-94be-83c4dcd70746)


**3. Data Subset Refuter**

*Snapshoot for Customers' Complaints and Customers' Churn Model*

![use_subset_data](https://github.com/hayasalman/Qualitative-Research-Observational-Study-Causal-Inference/assets/71796909/7010908b-91f7-41a9-ac49-78b0a3d32a55)


**4. Add Unobserved Common Causes**

*Snapshoot for Customers' Complaints and Customers' Churn Model*

![unobserved_common_cause](https://github.com/hayasalman/Qualitative-Research-Observational-Study-Causal-Inference/assets/71796909/bd58c949-7ecb-408f-acf7-feb85f3877e4)


**Conclusion**: all the p-values for all models are larger than the significance level of 0.05 which means the estimated effect and the new effect are statistically not different.
