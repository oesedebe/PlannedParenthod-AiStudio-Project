# PPFA AI Studio 2025

---

## 👥 **Team Members**

| Name             | GitHub Handle | Contribution                                                             |
|------------------|---------------|--------------------------------------------------------------------------|
| Emma Lin    | @elinCSs28 | Data exploration & visualization, Decision Tree Model Training, overall project coordination          |
| Ryan Mbouombouo   | @iryanmb |  Data Augmentation & Code, Gradient Boosting Training, Data Preprocessing             |
| Ogechika Esedebe     | @oesedebe |  Data exploration & visualization, Data preparation and augmentation, Logistic Regression and Random forest Training & Testing             |
| Camila Lightfoot      | @CamilaLightfoot |  Data Augmentation, dataset augmentation, Exploratory Data Analysis & Decision Tree Model Training             |
| Zerlyne Nandwani-Simons       | @Z-Nsimons | Data preparation and augmentation, visualization, Logistic Regression and Random Forest training and testing, liaison between team and coach/CAs          |

---

## 🎯 **Project Highlights**

- Developed a machine learning model using Random Forest with TF-IDF and BERT to identify what patterns and choices Roo, the Planned Parenthood Chatbot, would use to decide whether to elevate the conversation to a human expert.
- Achieved ~77% accuracy and a 0.77 weighted F1 score with Random Forest, demonstrating reliable performance in identifying high-risk responses for Planned Parenthood Federation of America’s chatbot Roo.
- Generated actionable insights to inform business decisions at Planned Parenthood Federation of America.
- Implemented hyperparameter tuning alongside ethical AI practices, including bias evaluation and fairness metrics, to ensure the model aligned with industry expectations for reliability, performance, and responsible use in healthcare data environments.

---

## 👩🏽‍💻 **Setup and Installation**

### Cloning repository

To clone a repository from GitHub, use the following command:

```bash
git clone https://github.com/plannedparenthood/ai-studio-2025-1d.git
```
### Docker

You'll be using Jupyter and Python, but in order to make the process of getting set up a little simpler, we're suggesting that you use Docker. Docker is a containerization tool for bundling code and dependencies together.

First, install [Docker Desktop](https://docs.docker.com/compose/install/).

Once that's done, open up a terminal, change to the directory containing this README file, and run

```
    docker-compose up
```

The first time you do this, you'll see a lot of output text (it will be faster the subsequent times you run it). Eventually you will see some startup text followed by output that looks like:

```
    jupyter-1  | [I 2025-08-20 15:57:21.257 ServerApp]     http://127.0.0.1:8888/lab?token=211394ed0b20bf0e21ea1e85bbdf6ff9d1bc69ad18496b2e
    jupyter-1  | [I 2025-08-20 15:57:21.257 ServerApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
```

Open up the URL starting with http://127.0.0.1:8888/ in your browser. The "token" value above is just an example -- yours will be something different!

### Credentials

We will send you a file called `credential.json`. This is your permission for downloading the conversational data from our data store. Put it in the same directory as this file. Please do not share this file with anyone please, thank you!

### Adding libraries

If you need additional libraries you can install them via Jupyter. If you want to install scikit-learn, for instance, create a new cell and input:

```
    !cd config && uv add scikit-learn
```
---

## 🏗️ **Project Overview**
### **Connection to the Break Through Tech AI Program**
This project was completed through the **Break Through Tech AI Program**, which provides training in machine learning, hands-on industry projects, and year-long mentorship. Skills gained in the summer Machine Learning Foundations curriculum—such as data analysis, model building, and responsible AI—were directly applied in this real-world challenge.
### **AI Studio Host Company, Project Objective, and Scope**
Our AI Studio host company is the **Planned Parenthood Federation of America (PPFA)**. As Team **PPFA 1D**, we worked to improve the performance of **Roo**, PPFA’s sexual and reproductive health (SRH) chatbot.
Our goals were to:
Analyze and augment a dataset of real and generated chatbot conversations
Evaluate Roo’s input/output accuracy and identify weak points
Build a predictive model to flag conversations that need human educator involvement
Use tools such as confusion matrices to assess and improve classification accuracy
The project involved full end-to-end ML work, from data exploration to modeling, evaluation, and recommendations.
### **Real-World Significance and Business Impact**
Reliable digital SRH information is crucial, especially for users who rely on private, accessible online tools. Improving Roo supports PPFA’s mission by strengthening how users receive timely, trustworthy guidance.
### Our work highlights **three key business impacts**:
**1. Enhanced User Experience**
Identifying where Roo’s responses fall short helps improve accuracy and reduce misinformation, leading to clearer, faster support for users.
**2. Better Resource Management**
A classification model helps route difficult conversations to human educators, allowing staff to focus on complex cases while routine questions are handled automatically.
**3. Risk Reduction**
More accurate predictions reduce the chances of Roo giving unsafe or incorrect advice, helping protect both users and PPFA’s reputation.

---

## 📊 **Data Exploration**

The dataset used was real and generated chat data with 2086 rows x 18 columns before the preparation, and 2234 rows x 9 columns after the preparation. The dataset originated from PPFA’s records of chats.

### **Data Exploration and Preprocessing**

Our data exploration and preprocessing pipeline focused on understanding the structure of the dataset, improving data quality, and preparing the text for modeling. The key steps included:

**1. Initial Data Exploration**  
Examined the size, shape, and data types of all columns.  
Identified irrelevant or redundant features.  
Detected columns with excessive missing values.

**2. Column Cleaning and Consolidation**  
Dropped irrelevant columns and those with significant missing values.  
Merged overlapping columns that represented the same underlying information to reduce redundancy and simplify the dataset structure.

**3. Text Cleaning and Normalization**  
To ensure consistency across all text fields, we performed:  
Lowercasing all strings.  
Removing non-alphanumeric characters.  
Stripping leading and trailing whitespaces.  
Correcting spelling errors using automated spell-checking.

**4. Addressing Class Imbalance**  
Introduced synthetic chat data for underrepresented categories.  
Visualized class distributions before and after augmentation to confirm improved balance.

**5. Tokenization and Lemmatization**  
Tokenized each message into individual words.  
Applied lemmatization to convert words to their base form, reducing vocabulary size and improving generalization.

**6. Feature Engineering**  
Converted cleaned and lemmatized text into numerical representations using TF-IDF vectorization, allowing machine learning models to capture the importance of each word relative to the dataset.

### **Insights from Exploratory Data Analysis (EDA)**

During the exploratory analysis phase, we examined the structure, distribution, and quality of the dataset to understand how the chatbot conversations were labeled and how users engaged with different topics. Key insights include:

**1. Strong Class Imbalance Across Labels**  
Several important classes had very few examples, making the dataset highly imbalanced.  
This imbalance directly motivated the use of data augmentation, class weights, and macro F1 as our main evaluation metric.

**2. Inconsistent Text Formatting**  
Our initial inspection revealed patterns such as:  
Mixed casing (upper/lowercase inconsistencies)  
Extra whitespace  
Non-alphanumeric characters  
This confirmed the need for a robust text cleaning pipeline before modeling.

**3. Duplicate and Overlapping Columns**  
Multiple columns contained similar or redundant information.  
Merging these columns helped simplify the data structure and reduce noise.  
Some columns had high missingness, making them unsuitable for modeling.

**4. Vocabulary Patterns**  
From token frequency analysis:  
Many prompts used slang, abbreviations, or misspellings, confirming the need for spell-checking and normalization.  
Certain topic-specific keywords strongly aligned with specific labels.

**5. BERT Revealed Deeper Semantic Structure**  
Using BERT embeddings exposed overlaps between classes that appeared textually similar but semantically different.  
Some labels were very close in representation space, indicating the inherent difficulty of the classification task.

### **Challenges and Assumptions**

Throughout the development of this project, we encountered several challenges related to data quality, class structure, and the nature of user-generated text.

**1. Class Imbalance**  
**Challenge:**  
Some labels had significantly fewer examples than others, leading to skewed class distributions.

**Assumptions:**  
Synthetic data generated from similar chat patterns would help balance the dataset without harming model performance. We assumed that lightly-augmented text would preserve the intent and semantic meaning of each class.

**2. Inconsistent and Noisy Text**  
**Challenge:**  
The dataset contained spelling mistakes, inconsistent casing, punctuation issues, and general noise common in conversational data.

**Assumptions:**  
Text normalization, including lowercase, spelling correction, and removing non-alphanumeric characters, would not distort the original meaning or remove important context.

**3. Synthetic Data Quality**  
**Challenge:**  
Generating synthetically augmented chat prompts introduced the risk of creating unrealistic or overly repetitive samples.

**Assumptions:**  
By keeping augmentation lightweight and semantically consistent, synthetic examples would provide additional variety without introducing bias or noise.

Figure 1: Counts for unique values of the label after data augmentation has been implemented

![LABEL_BAR_GRAPH](images/LABEL_AUG_POST.png)

Figure 2: Word cloud of common words before stop word removal

![WORD_CLOUD](images/WORD_CLOUD_PRE_SWR.png)

Figure 3: Token length of response label relative to the frequency post tokenization

![TOKEN_RESPONSE](images/DIST_TOKEN_RESPONSE.png)

Figure 4: Token length of prompt label relative to the frequency post tokenization

![TOKEN_PROMPT](images/DIST_TOKEN_PROMPT.png)

Figure 5: Bar chart showing the top 20 most common bigrams in user prompts, highlighting frequent question-oriented phrases such as “how long,” “birth control,” and “how much,” which reflect information-seeking behavior related to reproductive health topics.

![BIGRAM](images/PROMPT_BIGRAMS.png)

---

## 🧠 **Model Development** 

The base model for the project was Logistic Regression, and the comparison models were Decision Trees, Random Forest, and Gradient Boosting.

### **Feature Selection**

To build an effective model for classifying chatbot messages, we focused on selecting features that captured meaningful semantic structure while avoiding unnecessary noise.

**Approaches Used:**
**TF-IDF Vectorization:**
We used TF-IDF as the primary feature representation, which allowed us to encode word importance while down-weighting common stopwords.

### **Hyperparameter Tuning**

We experimented with different model families (e.g. Logistic Regression, Random Forest, Gradient Boosting, Decision Trees) and conducted systematic tuning using:

**Examples of Tuned Parameters:**
Logistic Regression: C (regularization), penalty type
Random Forest: number of trees, max depth
Gradient Boosting: max depth
Decision Trees: max depth, min samples split

### **Training Setup**

**Train/Test Split**
We followed a standard ML workflow:
Training: 70%
Testing: 30%

**Evaluation Metrics**
Because this is a multi-class text classification problem with imbalanced data, we evaluated performance using:
Macro F1-Score: primary metric; treats all classes equally
Accuracy: secondary metric
Confusion Matrix: to understand per-class performance
Precision and Recall: to assess over-prediction vs. under-prediction

**Baseline Performance**
Before implementing advanced preprocessing and augmentation, we trained a simple baseline:

**Baseline Model:**
TF-IDF + Logistic Regression
Default hyperparameters

---

## 📈 **Results & Key Findings**

### Logistic Regression

* Model using a **sigmoid function** to predict class probabilities.
    * 
* Performance metrics:
    * Accuracy: $0.68 - 0.74$
    * Log Loss: $0.80$
    * Weighted F1: $0.65 - 0.74$
    * Weighted Precision: $0.70 - 0.74$
    * Weighted Recall: $0.66 - 0.68$

* **Observations:** The model struggled with complex patterns in text data, leading to more false negatives. Useful as a baseline model.

### Decision Trees

* Non-linear, rule-based model that splits data into branches using feature importance from TF-IDF vectors.
* Performance metrics:
    * Accuracy: $0.70 - 0.735$
    * Weighted F1: $0.69 - 0.743$
    * Weighted Precision: $0.70 - 0.737$
    * Weighted Recall: $0.69 - 0.737$
* **Observations:** Highly interpretable, but slightly weaker than ensemble methods in overall predictive performance.

### Gradient Boosting Classifier

* Ensemble of decision trees where each new tree corrects the errors of the previous one.
    * 
* Performance metrics:
    * Accuracy: $0.77$
    * Weighted F1: $0.76$
    * Weighted Precision: $0.77$
    * Weighted Recall: $0.77$
* **Observations:** Performed well, particularly for minority classes, but slightly less stable than Random Forest across different splits.

### Random Forests

* Ensemble model that builds many decision trees and aggregates results for robust predictions.
    * 
* Performance metrics:
    * Accuracy: $0.74 - 0.77$
    * Log Loss: $0.53 - 0.70$
    * Weighted F1: $0.74 - 0.75$
    * Weighted Precision: $0.75 - 0.79$
    * Weighted Recall: $0.75 - 0.77$
* **Observations:**
    * Outperformed all other models in both accuracy and F1 score.
    * Balanced performance across all classes, reducing false negatives and false positives.
    * **Selected as the final model** for its strong, reliable predictions and ability to handle complex, high-dimensional text embeddings.


Key Insights
* Random Forest was the most effective model, providing the best balance between accuracy and class-wise performance.
* Logistic Regression underperformed due to its linear nature and inability to capture complex relationships in text embeddings.
* Decision Trees were interpretable but less powerful than ensemble methods.
* Gradient Boosting improved accuracy on some subsets but was slightly less consistent than Random Forest.
* Overall models trained with Sentence-BERT embeddings benefited from high-quality, semantic text representations in comparison to models trained with TF-IDF.
* Data balancing, hyperparameter tuning, and model evaluation were crucial to achieve strong performance.

Gradient Boosting (S-BERT) confusion matrix.
FP has recall 0.75 and precision 0.72, meaning it finds about three quarters of the true FP interactions while keeping most of its FP flags correct.

![RAND_FOR_GRIDCV_CM.png](images/RAND_FOR_GRIDCV_CM.png)

Random Forest (GridSearchCV) confusion matrix.
The model correctly identifies 188 of 259 FP cases (FP recall 0.73), but its main failure mode is confusing FP with TP, where 62 true FP interactions are predicted as TP

![RAND_FOR_GRIDCV_CM.png](images/RAND_FOR_GRIDCV_CM.png)

---

## 🚀 **Next Steps**

* Expand dataset to include more balanced and diverse samples (more TN/FN)
* Improve model interpretability to understand why certain predictions were made for debugging purposes
* Try out using other vectorization methods to improve synonym and idiom recognition such as word-to-vec
* Experiment with more models and tune the hyperparameters further of our current models

---

## 📝 **License**

This project is licensed under the Apache 2.0 License.
https://www.apache.org/licenses/LICENSE-2.0 

---

## 📄 **References**

https://scikit-learn.org/stable/modules/tree.html
https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html
https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingClassifier.html

---

## 🙏 **Acknowledgements** 

We would like to express our gratitude to everyone who supported this project:
**Challenge Advisors Michael O’Keefe and Rosette Diaz:** Thank you for your guidance, feedback, and mentorship throughout the project.
**Planned Parenthood Federation of America Representatives:** Thank you for providing resources and insights that helped shape this project.
**Coach Ananya Devarakonda:** Thank you for your encouragement, advice, and support throughout the entire process.

Your guidance and support were invaluable in making this project possible.
