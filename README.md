# Generative AI Practicum Project - GWU MSBA Fall 2023 Model Card
## Generating datasets for validating complaint-classification NLP Models

### Basic Information

* **Person or organization developing model**: GWU Wells Fargo Generative AI Team (Stephanie Palanca, Joon Kyu Hong, Kathleen McQuiddy, Ian Kang) 
* **Model date**: December, 2023
* **Model version**: 1.0
* **License**: MIT
* **Model implementation codes**: [final_codes](final_codes)

### Intended Use

* **Business Value**: Improving the accuracy of complaint classification models, enabling financial institutions and regulators to better understand and address consumer concerns.
* **Objective**: Providing practical experience in LLMs and Prompt Engineering projects for educational purposes.
* **Intended Users** : Wells Fargo Team, Patrick Hall, and GWU Students in DNSC 6317
* **Additional Information** : Valuable educational resource for GWU students.

### Background :
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
* **Software used to implement the model**:
* **Version of the modeling software**: 

#### Type of model 2: Llama 2 7B (Chat)
* **Software used to implement the model**: Python, Together, langchain , Llama 2 7B
* **Version of the modeling software**: 3.10.2, 1.0.0 , 0.0.327, 2.7b

#### Type of model 3: Falcon
* **Software used to implement the model**: 
* **Version of the modeling software**: 

#### Type of model 4: Red Pajama
* **Software used to implement the model**: 
* **Version of the modeling software**: 

#### Type of model 5: Red Pajama
* **Software used to implement the model**: 
* **Version of the modeling software**:

#### Type of model 6: Mistral
* **Software used to implement the model**: 
* **Version of the modeling software**: 

#### Type of model 7: GPT 3.5 Turbo
* **Software used to implement the model**: Python, openai
* **Version of the modeling software**: 3.10.2, 3.5
  
### Exploratory Data Analysis 

#### Table of sample complaints
* **An example of complaints dataset with issues and consumer complaint narrative.**
  
![Sample Complaints dataset](images/sample_dataset.png)

#### Bar Chart 
* **It highlights the ten most prevalent issues identified within complaints filed against banks.**
  
![BarChart](images/Top10MostCommonIssues.png)

#### Pie Chart
* **It illustrates the distribution of complaints among the top five banks.**
  
![Pie Chart](images/DistributionofComplaintsAmongTop5Banks.png)

#### Common Words from Complaints
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


#### Type of model 4: Red Pajama


#### Type of model 5: Red Pajama


#### Type of model 6: Mistral


#### Type of model 7: GPT 3.5 Turbo

* **Original complaint**:
"I have two recent inquires one from XX/XX/2021 and one from XX/XX/2021 from a place called CBNA. This was not done nor authorized by me. When I XXXX this place, its states this place is in New York, I'm in XXXX XXXX, there's nothing this company can do for me. Also, when I called XXXX when I noticed the first inquiry they said this was a credit card inquiry. I have a bank as well as a bank card, if I wanted a credit card I would just go through my bank, I wouldn't even go through the trouble of going somewhere else, let alone applying twice within 2 weeks of the first time. That's just nonsense. A few years ago I filed a police report for identity thief and if needed I can do it again for this. I have been working really hard on my credit and the last thing I need is false / fraudulent information on my report. I would've contacted CBNA but honestly I don't even know where to start, or what to say. What do you say to a company you've never spoke too? However, I will do what needs to be done to get this removed."

* **Equal Complaint Synthesis**:
“I received unauthorized inquiries from CBNA on XX/XX/2021 and XX/XX/2021. They claim to be in New York, but I'm in XXXX XXXX. I already have a bank and a bank card, so I don't need a credit card. I filed a police report for identity theft before and will do it again if necessary. I don't know how to contact CBNA, but I'll take action to remove this.”

* **Less Harsh**:
“I recently noticed two unauthorized inquiries on my credit report from CBNA on XX/XX/2021 and XX/XX/2021. I'm concerned about false information affecting my hard-earned credit. Unsure how to approach CBNA, but determined to resolve this issue promptly.”


* **More Harsh**:
“This unauthorized inquiry from CBNA on XX/XX/2021 is unacceptable. I have diligently worked on my credit, and false information like this is detrimental. I will not hesitate to take legal action against identity theft. Remove this immediately"

### Model Evaluation 

### Ethical Concerns 

### Risk Considerations 
* **Describe potential negative impacts of using your group’s best model** : 
  *  Consider math or software problems:

  * Consider real-world risks: who, what, when and how?: 

* **Describe potential uncertainties relating to the impacts of using your group’s best model**:
  * Consider math or software problems: 

   * Consider real-world risks: who, what, when and how? 
    
* **Describe any unexpected or results encountered during training**:
  
