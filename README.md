# HepatitisC_Unsupervides_Learning_Study

## Project Abstract

### Introduction to the topic of Hepatitis C and motivation for the analysis

Hepatitis C is a chronic viral infection, caused by the Hepatitis C virus. This virus primarely affects the liver, becoming chronic 70% of times at an initial infection. It can progress silently over the years and lead to sever complications such as fibrosis, cirrhosis, or hepatocellular carcinoma.<a link= "https://www.who.int/news-room/fact-sheets/detail/hepatitis-c">[1]</a>
<br>
The primary methode of infection is through pericutaneous contact with contaminaded blood (this includes the shared usage of a sirenge for drug use, unscreened blood transfusions, etc). As Hepatitis C is a blood born disease, diagnosis can be done throught blood testing. Many patients are asymptomatic in the initial phases, thus making early detection and staging of the disease remain challenges. Through laboratory biomarkers reflecting liver function and metabolic activity we can assess disease presence and severity.<a link= "https://en.wikipedia.org/wiki/Hepatitis_C">[2]</a>
<br>

### Description of the purpose of the study
The purpose of this study is to apply unsupervised learning techniques to clinical laboratory data. We will analyze correlations and similarities among liver-related biomarkers, the project aims to identify latent patient profiles that may correspond to different physiological or pathological states. Dimensionality reduction and clustering methods are used to explore data organization, detect outliers, and highlight meaningful groupings within the patient population.

### Data used to perform the analysis
For our analysis we'll draw upon a publicly available  <a link= " https://archive.ics.uci.edu/dataset/571/hcv+data"> Hepatitis C dataset  </a> from the UCI Machine Learning Repository. The dataset consists of anonymized patient records described by demographic variables (age and sex) and biochemical laboratory measurements, including albumin (ALB), alkaline phosphatase (ALP), alanine aminotransferase (ALT), aspartate aminotransferase (AST), bilirubin (BIL), cholinesterase (CHE), cholesterol (CHOL), creatinine (CREA), gamma-glutamyl transferase (GGT), and total protein (PROT). Although diagnostic categories are available in the dataset, they are not used during model training and are reserved solely for post hoc interpretation of the discovered clusters. <a link= " https://archive.ics.uci.edu/dataset/571/hcv+data">[3]</a>


### Clinical Relevance for Unsupervised Learning
These biomarkers collectively capture **hepatic injury**, **synthetic liver function**, **cholestasis**, and **systemic effects** of chronic liver disease. Their joint analysis through unsupervised learning enables the identification of latent patient profiles that may correspond to different stages or phenotypes of Hepatitis C without relying on predefined diagnostic labels.


### Methodology

1. **Dataset Dictionary and Statistical Interpretation of Variables**  <br><br>
   We start by analyzing what each data column represents.We classify the different categories in what role each will play in our study. We decice if the data is catogirical or continuous, what the categories are or the units used, what kind of variable it is with the context of our study and what are the physiological behaviours and importants within the context of Hepatits C.

### References

* [1] https://www.who.int/news-room/fact-sheets/detail/hepatitis-c
* [2] https://en.wikipedia.org/wiki/Hepatitis_C
* [3] https://archive.ics.uci.edu/dataset/571/hcv+data
