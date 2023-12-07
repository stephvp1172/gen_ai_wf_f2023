# Generative AI Practicum Project - GWU MSBA Fall 2023 Model Card
## Generating datasets for validating complaint-classification NLP Models

### Basic Information

* **Person or organization developing model**: GWU Wells Fargo Generative AI Team (Stephanie Palanca, Joon Kyu Hong, Kathleen McQuiddy, Ian Dongyun Kang) 
* **Model date**: December, 2023
* **Model version**: 1.0
* **License**: Licenses for all our codes
* **Model implementation codes**: [final_codes](final_codes)

### Intended Use

* **Business Value**: Improving the accuracy of complaint classification models, enabling financial institutions and regulators to better understand and address consumer concerns.
* **Objective**: Providing practical experience in LLMs and Prompt Engineering projects for educational purposes.
* **Intended Users** : Wells Fargo Team, Patrick Hall, and GWU Students in DNSC 6317
* **Additional Information** : Valuable educational resource for GWU students.

### Background
Enhancing customer service within financial institutions involves a comprehensive understanding of customer complaints. An integral aspect of this comprehension is ensuring the accurate categorization and directed resolution of written complaints through effective routing to the relevant teams. Employing Natural Language Processing (NLP) models for the classification of potential customer complaints, such as distinguishing between "Serious Complaints," "Minor Complaints," or instances categorized as "Not a Complaint," is a valuable strategy. However, validating the functionality of these models poses a challenge, given the manual and time-intensive nature of the process, compounded by potential limitations in the dataset.

### Data

* Data dictionary: This dataset captures consumer complaints submitted to the Consumer Financial Protection Bureau (CFPB), detailing information such as the date received, type of financial product involved, specific issues raised, and the company's response. It provides insights into consumer experiences with financial products and services, aiding in the analysis of industry trends and regulatory oversight.

| Field name                   | Description                                                                                                                                                                                | Measurement Level   |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| Date received                | The date the CFPB received the complaint. For example, “05/25/2013.”                                                                                                                      | Ordinal             |
| Product                      | The type of product the consumer identified in the complaint. For example, “Checking or savings account” or “Student loan.”                                                                 | Nominal             |
| Sub-product                  | The type of sub-product the consumer identified in the complaint. For example, “Checking account” or “Private student loan.”                                                                 | Nominal             |
| Issue                        | The issue the consumer identified in the complaint. For example, “Managing an account” or “Struggling to repay your loan.”                                                                   | Nominal             |
| Sub-issue                    | The sub-issue the consumer identified in the complaint. For example, “Deposits and withdrawals” or “Problem lowering your monthly payments.”                                              | Nominal             |
| Consumer complaint narrative | Consumer complaint narrative is the consumer-submitted description of “what happened” from the complaint. Consumers must opt-in to share their narrative.                                    | Text                |
| Company public response      | The company’s optional, public-facing response to a consumer’s complaint. Companies can choose to select a response from a pre-set list of options that will be posted on the public database. | Nominal             |
| Company                      | The complaint is about this company. For example, “ABC Bank.”                                                                                                                               | Nominal             |
| State                        | The state of the mailing address provided by the consumer.                                                                                                                                  | Nominal             |
| ZIP code                     | The mailing ZIP code provided by the consumer. This field may: i) include the first five digits of a ZIP code; ii) include the first three digits of a ZIP code (if the consumer consented to publication of their complaint narrative); or iii) be blank (if ZIP codes have been submitted with non-numeric values, if there are less than 20,000 people in a given ZIP code, or if the complaint has an address outside of the United States). | Numeric             |
| Tags                         | Data that supports easier searching and sorting of complaints submitted by or on behalf of consumers. For example, complaints where the submitter reports the age of the consumer as 62 years or older are tagged “Older American.” Complaints submitted by or on behalf of a servicemember or the spouse or dependent of a servicemember are tagged “Servicemember.” Servicemember includes anyone who is active duty, National Guard, or Reservist, as well as anyone who previously served and is a veteran or retiree. | Nominal             |
| Consumer consent provided?  | Identifies whether the consumer opted in to publish their complaint narrative. We do not publish the narrative unless the consumer consents, and consumers can opt-out at any time.              | Binary              |
| Submitted via                | How the complaint was submitted to the CFPB. For example, “Web” or “Phone.”                                                                                                                 | Nominal             |
| Date sent to company         | The date the CFPB sent the complaint to the company.                                                                                                                                       | Ordinal             |
| Company response to consumer | This is how the company responded. For example, “Closed with explanation.”                                                                                                                  | Nominal             |
| Timely response?             | Whether the company gave a timely response. For example, “Yes” or “No.”                                                                                                                     | Binary              |
| Consumer disputed?           | Whether the consumer disputed the company’s response.                                                                                                                                      | Binary              |
| Complaint ID                 | The unique identification number for a complaint.                                                                                                                                          | Nominal             |


* **Source of training data**: Consumer Finance Protection Beauru (suggested by the Wells Fargo team)
* **Number of rows in training data**:
  * training  rows: 176029 rows after removing null values.

* **Column(s) used as target(s) in the final model**: 'Consumer complaint narrative'
  
### Model Details 

#### Type of model 1: Llama 2 7B (API) - Main Model
* **Software used to implement the model**: Python, AWS SageMaker, Llama 2 7b - Instruct
* **Version of the modeling software**: 3.10.2, 1.0.0 , 0.0.327, 2.7b

#### Type of model 2: Llama 2 7B (Chat)
* **Software used to implement the model**: Python, Together, langchain , Llama 2 7B
* **Version of the modeling software**: 3.10.2, 1.0.0 , 0.0.327, 2.7b

#### Type of model 3: Falcon
* **Software used to implement the model**: Python, AWS SageMaker, Falcon 7B BF16 - HuggingFace
* **Version of the modeling software**: 3.10.2, 1.0, 1.7b

#### Type of model 4: PaLM
* **Software used to implement the model**: Python, PaLM, Google Colab
* **Version of the modeling software**: 3.10.2, 2.0, 2.340b

#### Type of model 5: Mistral
* **Software used to implement the model**: Python, AWS SageMaker, Mistral 7.5B 
* **Version of the modeling software**: 3.10.2, 1.0, 1.7.3b

#### Type of model 6: GPT 3.5 Turbo
* **Software used to implement the model**: Python, openai
* **Version of the modeling software**: 3.10.2, 3.5
  
### Exploratory Data Analysis 

#### Figure 1
* **An example of complaints dataset with issues and consumer complaint narrative.**
  
![Sample Complaints dataset](images/sample_dataset.png)

#### Figure 2
* **It highlights the ten most prevalent issues identified within complaints filed against banks.**
  
![BarChart](images/Top10MostCommonIssues.png)

#### Figure 3
* **It illustrates the distribution of complaints among the top five banks.**
  
![Pie Chart](images/DistributionofComplaintsAmongTop5Banks.png)

#### Figure 4
* **A visual representation using a word cloud of randomly sampled consumer complaint narratives.**
  
![Word Cloud](images/Word_Cloud.png)

### Methodology 

* **Basic process of complaint generation using a large language model**:

  * Tokenization: The text is broken down into individual words or subwords.
  * Embeddings: Each token is converted into a vector that represents its meaning.
  * Encoding: The embeddings are fed into a series of transformer layers, which use self-attention mechanisms to analyze the input sequence and produce a continuous representation of the text.
  * Decoding: The decoder generates the output text one token at a time, using a probability distribution generated by the encoder.
  * Generation: The output text is generated one token at a time, and the model selects the most likely token to add to the sequence.
  * Training: The model is trained on a large corpus of text data, and it learns to predict the next token in a sequence.

* **Distinctive Advantages  of LLaMA 2**:
  * A combination of a transformer encoder and a recurrent neural network (RNN) decoder
  * LLaMA-2 has a smaller model size than other LLMs
  * LLaMA-2 is more general-purpose and can be fine-tuned for a wide range of NLP tasks, such as text classification, sentiment analysis, question answering, and more.
  * LLaMA-2 is designed to be flexible and adaptable, allowing it to be fine-tuned for a wide range of NLP tasks and domains, making it a powerful tool for a variety of applications.
  
* **The Main Goal - Synthesize Complaints**:
   * The initial exploratory analysis identified three types of complaints:
      * Complaints that are generally well written - DESIRABLE
      * Complaints with very poor grammar and punctuation - PROBLEMATIC
      * Complaints with frivolous, unrelated information - PROBLEMATIC

   * Different types of prompts we experimented:
       Prompt for Robustness Testing, Prompt for Equal Complaint Synthesis (MFT), Prompt for Harshness Modification (Direction)

### Model Performance 

**Examples of generated complaints by each large language model**

#### Type of model 1: Llama 2 7B (API) - Main Model
* **Original complaint**:
'Please refer my previous CFPB complainat " XXXX \'\' on XX/XX/2021. \nI have Citibank \'s Interest checking account. Got an email from Citigroup which stated that for any direct deposits, I will get upto 2 % cash back ( up to {$100.00} ). I have direct deposit of my salary two times of {$2500.00} each duringXX/XX/2021 ( one on XX/XX/XXXX and another one on XX/XX/2021 - both {$2500.00} ) on after following this promotion all the conditions. But I haven\'t received {$100.00} for these direct deposit activities. I can not keep this account open forever to get this {$100.00} as during pandemic my money ( {$5000.00} ) in this account is blocked ( very low interest rates ). Dealing with totally inefficient Citibank customer service is good for nothing. Already talked to them for at least 3 times via chat regarding the same issue. This bank is so large and inefficient that left hand doesn\'t know what right hand is doing. Customer service is just looking to pass the buck from one team/person to another. \nCiti just want to block the money for dubious promotions plus terms and conditions. Citi will keep on moving the goal post like this. \n\n\nCiti stated in their response that : However, if you would like to continue participating in this promotion please complete two additional direct deposits, one in the month of XXXX, and one in XXXX. Thereafter, if the remaining terms and conditions are met the 2 % cash back bonus ( up to {$100.00} ) would be applied to your account ending in XXXX on or before XX/XX/2021. \n\nEven after meeting that condition I haven\'t got {$100.00} cash back bonus.',

* **Equal Complaint Synthesis**:
1 {'generated_text': " Complaint:\n\nI have been a customer of Citibank for over a year now and have been a loyal member of their customer base. However, I recently received an email from Citigroup stating that for any direct deposits made into my interest checking account, I would receive up to 2% cash back (up to $100). I have made two direct deposits of my salary, each amounting to $2500, during the month of XX/XX/2021 (one on XX/XX/2021 and another one on XX/XX/2021). Despite meeting all the conditions, I have not received the $100 cash back bonus.\n\nI have tried to contact Citibank's customer service multiple times, but the response has been inadequate. They have simply passed the buck from one team to another without resolving the issue. It is unacceptable that I have been left with a checking account that is blocked due to low interest rates, and I have not received the cash back bonus that I was promised.\n\nI am extremely disappointed in the inefficiency and lack of transparency shown by Citibank"}

* **Less Harsh**:
{'generated_text': " Complaint 1: Less Harsh\n\nI'm writing to express my disappointment with Citibank's interest checking account. I received an email about a 2% cash back promotion, but after making two direct deposits of my salary, I haven't received the bonus. Despite my multiple attempts to contact customer service, I haven't received a resolution. I'm frustrated with the bank's inefficiency and lack of communication.

* **More Harsh**:
Complaint 2: More Harsh\n\nI can't believe that Citibank would intentionally mislead their customers about a promotion. I made two direct deposits of my salary to receive a 2% cash back bonus, but I haven't received a dime. The bank's customer service is incompetent and unresponsive. I've tried to resolve this issue multiple times, but the bank's bureaucracy is slow and inefficient. I'm fed up with Citibank and will never do business with them again.


#### Type of model 2: Llama 2 7B (Chat)

* **Original complaint**:
"I have two recent inquires one from XX/XX/2021 and one from XX/XX/2021 from a place called CBNA. This was not done nor authorized by me. When I XXXX this place, its states this place is in New York, I'm in XXXX XXXX, there's nothing this company can do for me. Also, when I called XXXX when I noticed the first inquiry they said this was a credit card inquiry. I have a bank as well as a bank card, if I wanted a credit card I would just go through my bank, I wouldn't even go through the trouble of going somewhere else, let alone applying twice within 2 weeks of the first time. That's just nonsense. A few years ago I filed a police report for identity thief and if needed I can do it again for this. I have been working really hard on my credit and the last thing I need is false / fraudulent information on my report. I would've contacted CBNA but honestly I don't even know where to start, or what to say. What do you say to a company you've never spoke too? However, I will do what needs to be done to get this removed."

* **Equal Complaint Synthesis**:
“I received unauthorized inquiries from CBNA on XX/XX/2021 and XX/XX/2021. They claim to be in New York, but I'm in XXXX XXXX. I already have a bank and a bank card, so I don't need a credit card. I filed a police report for identity theft before and will do it again if necessary. I don't know how to contact CBNA, but I'll take action to remove this.”

* **Less Harsh**:
“I recently discovered two inquiries on my credit report from CBNA, which I did not authorize or initiate. I understand that this can be a frustrating experience, and I want to work with you to resolve this issue. I would appreciate your assistance in removing these inquiries from my report, as they are not accurate and may be affecting my credit score. Please let me know the steps I can take to resolve this matter."

* **More Harsh**:
"I am outraged and appalled by the recent inquiries made on my credit report by CBNA, despite my explicit denial of any authorization. Not only is this a blatant violation of my privacy and security, but it also undermines my hard-earned credit score. I demand immediate action to remove these fraudulent inquiries and protect my personal information. I will not hesitate to take legal action if necessary, and I expect a prompt resolution to this matter. How dare you attempt to sully my good name and creditworthiness? I will not be ignored!"

#### Type of model 3: Falcon
* **Original complaint**:
'Sent letters to the three major bureaus asking to investigate and provide verification of debt per FCRA. Company failed to validate the debt belongs to me. 
Letters sent on XX/XX/XXXX, XX/XX/XXXX, XX/XX/XXXX and XX/XX/XXXX I am attaching the paper trail with Certified mail receipt.'

* **Equal Complaint Synthesis**:
'I am writing to request a validation of the debt from the three major bureaus as per the Fair Credit Reporting Act (FCRA). Unfortunately, I have not received any response or verification from the company regarding the validity of the debt. This is causing me significant distress and financial difficulty.'
Letters sent on XX/XX/XXXX, XX/XX/XXXX, XX/XX/XXXX and XX/XX/XXXX, I am attaching

* **Less Harsh**:
'I have been attempting to contact the three major credit bureaus regarding a potential fraudulent debt. I have yet to receive any response or verification from your company regarding the legitimacy of the debt claimed. This is highly concerning, and I kindly request your assistance in resolving this matter.'
Letters sent on XX/XX/XXXX and XX/XX/XXXX with Certified mail receipts included.'

* **More Harsh**:
'I recently experienced unethical and illegal practices by the company in question. They have continuously failed to validate my debt and have been deliberately deceptive in their communication. Please investigate the matter as soon as possible to ensure that justice is served.'


#### Type of model 3: PaLM
* **Original complaint**:
 'XXXX XXXX, Financial Sales, XXXX XXXX, XXXX XXXX XXXX XXXX, XXXX XXXX, CA ; Telephone # ( XXXX ) XXXX, allegedly submitted vehicle loan applications without my authorization to CapitalOne Auto Finance ( reference number XXXX ) and XXXX XXXX XXXX XXXX ( # XXXX ). I had already purchased a car with my own financing. XXXX XXXX mislead me by stating " it is the company policy to run a credit check on every customer purchasing a vehicle, even though they do not need financing assistance from us \'\' to allow them to run my credit. XXXX XXXX, 2016, I became aware of the problem because the denial letters from the financing agencies arrived. I met with the Sales Manager, XXXX XXXX regarding this matter, requesting that the credit bureau agencies are notified and inquires removed. I am seeking your assistance with this fraudulent activity. I want the damage to my credit score from inquiries to be immediately removed. I did not authorize these transactions.'

* **Equal Complaint Synthesis**:
You have not given me proof that your office is compliant with the FCRA. Show me proof that the inquiries in Exhibit C are compliant. All items in Exhibit B are fraudulent, invalid, and not supported by evidence. You are damaging my creditworthiness by listing these fraudulent inquiries.

* **Less Harsh**:
Your report contains fraudulent inquiries and inaccurate information. Please fix it.

* **More Harsh**:
Your report is full of fraudulent inquiries and inaccurate information. You are damaging my character and creditworthiness. Fix it now!

#### Type of model 4: Mistral
* **Original complaint**:
'This is a follow-up of complaint XXXX. FIA Card Services has never sent me their definition of " cash equivalent '' or anything else. In addition, to harass me further, the last statement included a " minimum interest charge '' of {$1.00}. I owe them nothing and that charge was so absurd that their automated line took it off. FIA cheat and lies and is totally irresponsible. There should be some penalties or they should at least tell the truth. They record their calls so al this can be easily verified.''

* **Equal Complaint Synthesis**:
1. I am writing to follow up on my previous complaint about FIA Card Services. Despite repeated attempts, they have not provided me with their definition of "cash equivalent." Furthermore, their last communication included a "minimum interest charge" of $1.00, which I find unjustified. I owe them nothing, and this charge was so unreasonable that their automated system removed it. FIA is dishonest and untrustworthy, and they need to be held accountable. There should be consequences for their actions, and they should be transparent about their practices.
   
* **Less Harsh**:
Less Harsh: FIA Card Services could improve their communication by sending a clearer definition of "cash equivalent." I appreciate their efforts to minimize further harassment by taking off the incorrect minimum interest charge.

* **More Harsh**:
FIA Card Services is truly irresponsible for their actions in this matter. Their lack of transparency and honesty is unacceptable. I demand penalties for their actions and hope that they will take steps to prevent similar situations from happening in the future.

#### Type of model 5: GPT 3.5 Turbo

* **Original complaint**:
"I have two recent inquires one from XX/XX/2021 and one from XX/XX/2021 from a place called CBNA. This was not done nor authorized by me. When I XXXX this place, its states this place is in New York, I'm in XXXX XXXX, there's nothing this company can do for me. Also, when I called XXXX when I noticed the first inquiry they said this was a credit card inquiry. I have a bank as well as a bank card, if I wanted a credit card I would just go through my bank, I wouldn't even go through the trouble of going somewhere else, let alone applying twice within 2 weeks of the first time. That's just nonsense. A few years ago I filed a police report for identity thief and if needed I can do it again for this. I have been working really hard on my credit and the last thing I need is false / fraudulent information on my report. I would've contacted CBNA but honestly I don't even know where to start, or what to say. What do you say to a company you've never spoke too? However, I will do what needs to be done to get this removed."

* **Equal Complaint Synthesis**:
“I received unauthorized inquiries from CBNA on XX/XX/2021 and XX/XX/2021. They claim to be in New York, but I'm in XXXX XXXX. I already have a bank and a bank card, so I don't need a credit card. I filed a police report for identity theft before and will do it again if necessary. I don't know how to contact CBNA, but I'll take action to remove this.”

* **Less Harsh**:
“I recently noticed two unauthorized inquiries on my credit report from CBNA on XX/XX/2021 and XX/XX/2021. I'm concerned about false information affecting my hard-earned credit. Unsure how to approach CBNA, but determined to resolve this issue promptly.”


* **More Harsh**:
“This unauthorized inquiry from CBNA on XX/XX/2021 is unacceptable. I have diligently worked on my credit, and false information like this is detrimental. I will not hesitate to take legal action against identity theft. Remove this immediately"

### Model Evaluation 

#### Model Evaluation Methodology 
Our aim was to gauge the reliability and consistency of our measurement system when assessing complaints generated by the LLMs. The results of the Gage R&R analysis allowed us determine the extent to which variations in assessments can be attributed to the measurement system and guide any necessary improvements in our evaluation processes. We have attached the necessary steps we took below, as well as our analysis of the ANOVA models we used for Gage R&R. 

##### Step 1: Complaint Generation 
* Generated 10 "Harsher" complaints from our existing dataset using the model we deemed to be best at responding to prompts and generating synthesized complaints.
* We repeated this process 10 times to ensure diversity in generated complaints

##### Step 2: Individual Evaluation 
* Each team member (also known as appraiser) evaluated a set of 20 complaints in total. Each person assessed 10 complaints from the first generated dataset, and 10 from the second generated dataset. Each complaint evaluated was compared to the original complaint from the original dataset. 
* Factors that were considered were Sensibility, Truthfulness, Tone/Harshness, and Evidence.
* Sensibility was defined as whether or not a generated complaint from the model was coherent, while tone/harshness was determined by whether or not a complaint was harsh enough/too harsh. Evidence was defined as whether or not the generated complaint has evidence to back up the claims it was making, while truthfulness was defined as whether or not the generated complaint included information that was/was not included in the original complaint. 
* To quantify the assessment, we used a scale ranging from 0 to 1 (with options being 0, 0.5, and 1). Each team member applied this scoring criteria based on the established guidelines. 

##### Step 3: Data Entry 
* Each team member will recorded the evaluation scores in a designated spreadsheet.

##### Step 4: Calculate Repetability and Reproducability 
* We proceeded to calculate repetability (within the same evaluator) and reproducability (between different evaluators) using an analysis of variance (ANOVA) method. We used Minitab, which is a statistical software). 


#### Model Evaluation: Sensibility 
![alt text](https://github.com/stephvp1172/wells_fargo/blob/c85e05a991810967eacc6d07814756432e33ea69/images/Sensibility_GageR%26R.png)
* Since the majority of the variation comes from Repeatability (components of variation chart), our system of measurement may not be reliable. In an ideal scenario, the variation of our ANOVA would mostly come from part-to-part, and not any other factor. 
* May be an issue with repeatability since there isn't much range with the R chart. 
* The number of complaints appears not to affect each appraiser's ability to measure sensibility, as we see a normal variation in the sensibility of complaints chart.
* Variability in interquartile range for only one appraiser shows that there may be inconsistency in the way that one of the appraisers measured sensibility. 

#### Model Evaluation: Evidence
![alt text](https://github.com/stephvp1172/wells_fargo/blob/150bb0415131299271a31a7ad6e2996861673519/images/Evidence_GageR%26R.png)
* Like truthfulness, repeatability makes up for a lot of the variation, which shows us that there may be a problem with our measurement system.
* Consistent measurement precision among different subgroups because, for the most part, appraisers ranges are within control limits.
* Quantity of complaints does not alter evidence measurement since, similarly to sensibility, we see a relative range within the evidence by complaints chart.
* There may be a bias with how two appraisers measure evidence compared to others, since we see a median that is higher than the other appraisers in the evidence by appraiser chart.
* The relationship between number of complaints and evidence is not consistent among appraisers since we see a lot of interaction effects in the interaction plot (bottom right).

#### Model Evaluation: Tone/Harshness
![alt text](https://github.com/stephvp1172/wells_fargo/blob/51e4c5782c72d0f2e57dcb5c5bdf3b7b23477c92/images/Tone_GageR%26R.png)
* There may be a flaw in our measurement system since we also see most of the variation in our ANOVA model for tone/harshness coming from repetability.
* The variation among measurement system for tone/harshness is consistent since datapoints are within control limits, as shown in the R Chart. 
* Though datapoints are within control limits in the R chart, there is a clear spread between appraisers so it shows that the way we assess tone/harshness may be different from one another.
* The Tone/Harshness by Complaints chart shows consistent results despite number of complaints.
* There are clear interaction effects in the Complaints * by Appraiser Interaction chart, which shows that number of effects may influence/bias different appraisers.

#### Model Evaluation: Truthfulness
![alt text](https://github.com/stephvp1172/wells_fargo/blob/150bb0415131299271a31a7ad6e2996861673519/images/Truthfulness_Gage%26R.png)
* There may be inconsistent measurement because repeatability makes up for most of the variation.
* There are no significant issues with repeatability and appraisers appear to be consistent with measurement.
* There may be a difference in the way that appraisers interpret and measure truthfulness.
* Truthfulness scores are consistent and stable with the number of complaints, meaning that the number of complaints does not affect how well each appraiser is able to evaluate their set of complaints.
* All appraisers have medians within a similar range but  one appraiser's measurements are less consistent.

### Ethical Concerns 
**Potential negative impacts of using Llama 2 7b** :


* **Potential uncertainties relating to the impacts of using Llama 2 7b** :
 *  Enhancing your model's robustness should only help the model perform better.
  * The model needs to be monitored for fairness and robutness.

**Any unexpected results encountered during training**: Understanding how to properly shut down the model

### Ethical and Risk Considerations 
 *  The model is not fine-tuned enough to deliver completely unique complaints without changing the meaning of the original complaint
 * Llama 2 7b focuses solely on the English language, so any complaint in another language would not work
 * Llama 2 7b can be costly to run
 * Computational Resources for training and fine-tuning LLMs
 * The financial risk of deploying the model incorrectly
   * **Any unexpected results encountered during training**: Understanding how to properly shut down the model.
 * Smooth and efficient server setup
 * Data Quality and Bias 
    * Ensuring that the synthesized complaints are representative of real customer complaints
 * **Potential uncertainties relating to the impacts of using Llama 2 7b** :
    * Enhancing your model's robustness should only help the model perform better.
    * The model needs to be monitored for fairness and robutness.
    
 ### Potential Next Steps
 * Using both API and chat versions of  Llama 2 7 b.
 * Investing more time on time tuning the model.
 * Gathering more datasets for model validation.
 * Developing more comprehensive and diverse benchmarks.
 * Incorporating metrics that measure unintended biases and ethical considerations.
 * Including more diverse and representative datasets to reduce biases.
 * Evaluating models in various real-world scenarios to ensure robustness and generalization.
  
