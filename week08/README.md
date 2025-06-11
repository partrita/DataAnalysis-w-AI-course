# AI as Research companion

# **Finding instrumental variables (IVs)**
- The prompting approaches and examples below are adapted from and motivated by [Sukjin Han (2024) “Mining Causality: AI-Assisted Search for Instrumental Variables](Https://arxiv.org/pdf/2409.14202)

## **Recap (10 mins)**

- What are instrumental variables? What are they good for?
- List examples?

### **IV assumptions**

Hint: get AI to explain these 3 assumptions!

1. **Relevance (REL)**

$$
Cov(Z_i, D_i \mid X_i) \neq 0
$$

1. **Exclusion (EX)**

$$
Y_i(D,1) = Y_i(D,0) \quad \text{for all} \quad D = 0,1
$$

1. **Independence (IND)**

$$
(Y_i(1), Y_i(0), D_i(1), D_i(0)) ⊥ Z_i|X_i
$$



## **Prompt construction**

- Finding IVs using AI is not just about asking the model for a list. That usually gives you textbook examples with no connection to your actual setting. Instead, we can guide the model through a more structured reasoning process, one that mimics how we would think about instruments ourselves.
- Prompt Chaining is a good approach to find possible IVs
    - Prompt Chaining means breaking down a complex question (like finding an IV) into smaller steps that help the AI reason its way through the problem
    - Instead of asking for an instrument directly, we start by mapping out the relationships between variables, then gradually narrow down which ones could work as instruments.
    - Goal: 1) avoid generic answers and 2) get the AI to reason more like we would starting from the setting and building up to the econometrics.

### The 2-step approach
We will use Prompt Chaining to find IVs with two consecutive prompts.

**Step 1: Look for IVs that satisfies the verbal description of REL and EX**

> 🤖 **Prompt 1 (Search for IVs).** You are [agent] who needs to make a [treatment] decision in [scenario]. What are factors that can determine your decision but do not directly affect your [outcome], except through [treatment] (that is, factors that affect your [outcome] only through [treatment])? list [K 0] factors that are quantifiable. Explain the answers.



- Which parts of the prompt satisfy **REL** and **EX**?

**Step 2: Refine by choosing from the IVs in Step 1 that satisfy a verbal description of IND**

> 🤖 **Prompt 2 (Refine IVs).** You are [agent] in [scenario], as previously described. Among the [K 0] factors listed above, choose [K] factors that are most likely to be unassociated with [confounders], which
determine your [outcome]. the chosen factors can still influence your [treatment]. for each chosen factor, explain your reasoning.


- Which parts of the prompt satisfy **IND**?

### **Why we don’t tell the AI we’re looking for IVs**

If we say from the start that we're looking for instrumental variables, the AI often jumps to textbook examples, things like *weather shocks* or *distance to school*, without really thinking through the context. These are generic and not always helpful.

- We risk getting **shallow suggestions** that ignore the specifics of our data or setting.
- Some variables might sound like good instruments but **don’t actually satisfy the IV assumptions**
- It also introduces **bias from training data:** the model might overuse popular examples instead of reasoning from first principles.

So instead of asking directly for IVs, it’s better to guide the model **step-by-step** through the structure of the problem. 


## Examples on finding IVs

Let’s try out the prompts below and review the results together. As we go through them, think about the following:

- Does it seem like the AI believes we’re just asking a regular question, or does it seem to realize we’re testing something deeper?
- Are the IVs it gives us realistic? Which ones make sense, and which ones don’t seem believable?

**Important:** Before running the prompts, turn off the option that lets the AI remember your chat history.

### **Example 1: Demand estimation**

> 🤖 **Prompt 1** You are a bar owner at the Copacabana Beach. You need to set the price of draft beer. What would be factors that can determine your decision but that do not directly affect the customers’ demand for draft beer, except through the price you set (that is, that affect the demand only through the price of draft beer).
> 
> List forty factors that are quantifiable. Explain your answer for each factor and present these in a table.

> 🤖 **Prompt 2** Suppose you are a bar owner at the Copacabana Beach and is setting the price of draft beer on a day of the week. Among the factors listed above, choose all factors are not influenced by market conditions of draft beer or customers’ characteristics that determine demand for draft beer. For each factor chosen, explain your reasoning.


### **Example 2: Peer effects on microfinance adoption**

> 🤖 **Prompt 1** You live in a village in rural India. You recently joined a microfinance program and started using small loans to invest in your household or business. You want to influence others in your village to also join the program.
What would be factors (about yourself, your household, or the village) that determine your influence on peers, but that do not directly affect your peers’ decisions to join microfinance, except through your influence? That is, factors that affect your peers’ adoption only through your influence.
>
> List twenty factors that are quantifiable. Explain your answer.

> 🤖 **Prompt 2** Suppose you are a 40-year-old female resident of the village using small loans from the microfinance program. 
Among the factors you listed above, which ones are not influenced by the same factors (e.g., shared background, preferences, or location) that brought you and your peers into the same social network or neighborhood in the first place?
For each factor you choose, explain your reasoning.




## **Work together: Find an IV for a research question**

- Form groups of 3-4.
- We want to answer the research question: **What is the effect of migration on wages in the target country?**
- Think about context: which country (from $\rightarrow$ to), which industry (from $\rightarrow$ to), which type of people, what period in time, what kind of migration, skill characteristics, etc.
- Prepare **Prompt 1** and **Prompt 2**
    - **Run Prompt 1**
        
        Which one would you keep? Collect them in a separate table.
        
    - **Run Prompt 2**
        
        See which ones AI kept - are they the same? If not, ask why it didn’t include the ones you did/ why it in included the ones you didn’t. 
        

# Looking for controls - a different approach
    
Now we’re going to try something different. This time, we’ll ask the AI to act like a researcher and help us find control variables for estimating a simple relationship.
    
But here’s the twist: we’ll run **two sessions** (or use two different models). One will give us a list of controls, and the other will act as a kind of “adversarial LLM” that pushes back and questions those choices. Think of it like a debate between two AIs: one helpful, one suspicious.
    
## Recap
    
Discuss: confounders, bad controls: what are they? how to treat them?
    
We will use the [World Management Survey data](https://osf.io/t6zdp/files/osfstorage) and explore this question:
> Do firms with better management export more of their production?
    
    
## Prompt construction
    
Again, let’s try to run the following prompts: the first and the last in the same session, and the middle in a separate session. But first, let’s look at the [codebook](https://osf.io/emh5u) together.
As you run the prompts, think about:  
  - How do the answers differ from the previous prompting approach?
  - What do you think of the proposed variables? Would you include them all? Are there any left out.

> 🤖 **Prompt 1.** You are a researcher who wants to find control variables to estimate the association between percent of production exported and management quality. Production exported is your outcome variable and management quality is your variable of interest. Attached is a codebook of variables that we have access to. Choose variables that could be included in a multivariate OLS regression.
>
> Return a list of variables and explanation, including the expected direction of associations. At the end of your response, include a plain list of variable names in a copyable format (no bullets, no numbers, just one variable per line).

    
> 😈 **Prompt 2. Adversarial LLM in a separate session**
Below are a list of variables that I want to include in a regression to estimate the relationship between percent of production exported and management quality. Argue for each variable why I should not include it in the regression.
> [list of variables by Original LLM]


> 🤖 **Prompt 3. Feed Adversarial LLM’s response back to Original LLM** Below are counter-arguments for each of your previous answers. Based on these arguments, revise your selection and provide a list: [the arguments by Adversary LLM]

    

# Assignment

Political communication on social media is ever-increasing, but does it actually have an effect on overall political activation? Are more people voting because of social media, or does it only affect incumbent voters? In this assignment, you will examine the relationship between social media use and political participation.

**Tasks:** 

1. Take the [World Values Survey codebook (7th wave)](https://osf.io/9wp2z) and come up with a regression model that describes this relationship and controls for all possible confounders. Think in terms of demographics, socioeconomic variables, and any relevant attitudes and values in the **Core Variables section** of the codebook.
2. Use AI to help come up with the model. Write prompts based on what we learned and make notes of your experience with them. 
    1. Extra points will be given if you experimented with both approaches learned in class.

**Note:** you should not run any regressions for this assignment!

**To submit:**

- **1-page document** (maximum length for full points) that includes:
    - Your complete regression equation
    - Detailed reasoning for each variable included in the model
    - Specific justification for each confounder with:
        - Concrete examples of how the variable might influence the relationship
        - Expected direction of association (positive/negative)
        - Theoretical basis for inclusion
- Link to the chat(s) you used to get the variables.

**Note**: Extra points will be awarded for particularly insightful examples and well-reasoned predictions about the direction of associations between variables.
