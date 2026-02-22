## Dataset Dictionary and Statistical Interpretation of Variables

**Study Population Definition**
The population consists of adult individuals undergoing blood testing, including healthy blood donors and patients with varying degrees of liver disease related to Hepatitis C. The dataset represents a clinical observational sample, not a randomized cohort. As such, observed associations reflect correlations rather than causal relationships.

We'll start first of this study by exploring what each column represents and also what it's clinical relevance is in the context of Hepatitis C.

### **Reference Variable not used for training**

**Category** or the Diagnostic Status.
* Type: Categorical variable (ordinal)
* Categories :  0 = Blood Donor, 1 = Suspect Blood Donor, 2 = Hepatitis,  3 = Fibrosis and 4 = Cirrhosis
* Statistical role: External reference variable / post hoc validation label
* Purpose: Diagnostic category indicating the clinical status of the individual.  Used to assess whether clusters discovered through unsupervised learning align with known clinical disease stages.
* Note: Excluded from clustering to avoid label leakage.

#### The different Categories, clinical and statistical significance

* 0 = Blood Donor
<br>
Individuals classified as blood donors exhibit laboratory values within normal reference ranges and show no clinical or biochemical evidence of liver disease. This group serves as a reference population representing healthy liver function.
<br>
This category represents a control group with laboratory values largely confined within normal reference ranges. Statistically, it defines the baseline multivariate distribution of biomarkers against which deviations in other categories can be compared. Variance is typically low, and extreme values are rare. This group anchors the healthy region of the feature space and serves as a benchmark for normal physiological variability.


* 1 = Suspect Blood Donor
<br>
This category includes individuals who are generally healthy but present minor laboratory abnormalities or borderline values that prevent definitive classification as healthy blood donors. These abnormalities are not sufficient to confirm liver disease but warrant further clinical investigation or monitoring.
<br>
This category corresponds to individuals whose biomarker values lie near the boundaries of normality, often overlapping with both the healthy and diseased populations. From a statistical standpoint, it represents a high-variance, overlapping class that may not form a well-separated cluster. Its presence introduces distributional ambiguity and highlights the continuous nature of biological measurements rather than strict class separability.

* 2 = Hepatitis
<br>
Patients in this category show biochemical evidence of active liver inflammation, typically reflected by elevated liver enzymes such as ALT and AST. This stage corresponds to ongoing hepatocellular injury associated with Hepatitis C infection but without established structural liver damage.
<br>
This group is characterized by systematic shifts in the distribution of inflammation-related biomarkers (e.g., elevated ALT and AST) relative to the baseline population. Variance increases and distributions become more skewed. Statistically, this category occupies a region of feature space distinct from healthy donors but still overlapping with more advanced disease states, reflecting early pathological deviation without structural collapse.


* 3 = Fibrosis
<br>
This group represents individuals with chronic liver injury leading to the development of fibrotic tissue within the liver. Fibrosis reflects a progression from inflammation to structural damage and is often associated with altered synthetic liver function and persistent enzyme abnormalities.
<br>
This category represents a population with persistent multivariate deviation across several biomarkers, including liver enzymes and synthetic function markers. From a statistical view, fibrosis often corresponds to clusterable structure, with reduced overlap with healthy controls and increased separation along latent dimensions capturing chronic damage. Distributions show increased heterogeneity due to varying progression levels.

* 4 = Cirrhosis
<br>
Cirrhosis is the most advanced stage of chronic liver disease, characterized by extensive fibrosis, architectural distortion of the liver, and impaired hepatic function. Patients in this category often present with significant abnormalities across multiple laboratory markers, including reduced albumin and cholinesterase levels and elevated bilirubin.
<br>
Cirrhosis corresponds to the tail of the multivariate distribution, characterized by pronounced shifts across multiple biomarkers and increased occurrence of extreme values. Variance is high, and distributions are often heavily skewed. Statistically, this group tends to form distinct clusters or outliers in feature space, driven by severe impairment of liver function and systemic effects.


### **Demographic Variables**
These variables describe the underlying dataset structure and may act as confounders.

**Age**
* Type: Continuous
* Unit: Age of the patient in years.
* Statistical role: Baseline variable / potential confounder
* Purpose: Age is an important factor in Hepatitis C progression, as longer infection duration is associated with increased risk of fibrosis and cirrhosis.

**Sex**
* Type: Categorical (binary)
* Categories : Biological sex of the patient (male or female).
* Statistical role: Baseline variable / stratification variable
* Purpose: Sex-related differences exist in liver enzyme levels and disease progression, with males often exhibiting more severe liver damage.


### **Biochemical Laboratory Markers**
These variables capture physiological variation and are the main drivers of structure in unsupervised learning.

#### Markers of Hepatic Injury and Inflammation

**ALT (Alanine Aminotransferase)**
* Type : Continuous
* Unit :
* Statistical role: Explanatory variable
* Pupose : A liver-specific enzyme released into the bloodstream following hepatocellular injury. ALT elevation is a key marker of liver inflammation and is commonly increased in active Hepatitis C infection.
* Interpretation: Reflects acute hepatocellular injury; often right-skewed.
Statistical note: Sensitive to outliers; log transformation may be appropriate.

**AST (Aspartate Aminotransferase)**
* Type : Continuous
* Unit :
* Statistical role: Explanatory variable
* Pupose :An enzyme found in liver and other tissues. AST is often elevated in liver injury; an increased AST/ALT ratio may indicate advanced fibrosis or cirrhosis.
* Interpretation: Indicates liver injury but is less liver-specific than ALT.
Statistical note: Correlated with ALT; multicollinearity expected.

### Markers of Cholestasis and Hepatobiliary Function

**ALP (Alkaline Phosphatase)**
* Type : Continuous
* Unit :
* Statistical role: Explanatory variable
* Pupose : An enzyme associated with bile duct function. Elevated levels may suggest cholestasis or biliary involvement, which can occur in advanced liver disease.
* Interpretation: Interpretation: Reflects bile duct function and cholestasis.
* Statistical note: Elevated in multiple conditions; moderate specificity.

**GGT (Gamma-Glutamyl Transferase)**
* Type : Continuous
* Unit :
* Statistical role: Explanatory variable
* Pupose :An enzyme involved in glutathione metabolism and bile duct function. GGT is frequently elevated in chronic liver disease and is sensitive to hepatobiliary damage and alcohol-related liver injury.
* Interpretation: Sensitive marker of hepatobiliary stress.
* Statistical note: Highly skewed; often dominates distance-based clustering if not scaled.


### Markers of Liver Synthetic Function

**ALB (Albumin)**
* Type : Continuous
* Unit :
* Statistical role: Explanatory variable
* Pupose : A protein synthesized by the liver that reflects hepatic synthetic function. Decreased albumin levels may indicate chronic liver disease, advanced fibrosis, or cirrhosis.
* Interpretation: Indicates liver’s protein synthesis capacity.
* Statistical note: Lower variance but strong discriminative power for advanced disease.

**CHE (Cholinesterase)**
* Type : Continuous
* Unit :
* Statistical role: Explanatory variable
* Pupose : An enzyme synthesized by the liver and used as a marker of liver synthetic capacity. Reduced levels are commonly observed in chronic liver disease and cirrhosis.
* Interpretation: Sensitive indicator of chronic liver dysfunction.
* Statistical note: Useful for separating fibrosis and cirrhosis stages.

**PROT (Total Protein)**
* Type : Continuous
* Unit :
* Statistical role: Secondary explanatory variable
* Pupose : Total concentration of serum proteins, including albumin and globulins. Altered protein levels may reflect impaired liver synthesis or chronic inflammation.
* Interpretation: Captures combined protein synthesis and inflammatory activity.
* Statistical note: May partially overlap with ALB; redundancy possible.


### Markers of Metabolic and Systemic Function

**CHOL (Cholesterol)**
* Type : Continuous
* Unit :
* Statistical role:  Explanatory variable / metabolic marker
* Pupose : Total serum cholesterol concentration. Liver disease can disrupt lipid metabolism, often leading to reduced cholesterol levels in advanced stages of Hepatitis C.
* Interpretation: Reflects hepatic lipid metabolism.
* Statistical note: Decreases in advanced liver disease; moderate variance.

**BIL (Bilirubin)**
* Type : Continuous
* Unit :
* Statistical role: Explanatory variable
* Pupose : A breakdown product of hemoglobin processed by the liver. Elevated bilirubin reflects impaired hepatic clearance and is associated with jaundice and advanced liver dysfunction.
* Interpretation: Indicates impaired hepatic clearance.
* Statistical note: Highly skewed; strong indicator of severe disease.

**CREA (Creatinine)**
* Type : Continuous
* Unit :
* Statistical role: Confounding / control variable
* Pupose : A marker of renal function. Although not liver-specific, creatinine is clinically relevant as advanced liver disease can be associated with renal impairment (e.g., hepatorenal syndrome).
* Interpretation: Reflects renal function rather than liver function.
* Statistical note: Important for detecting systemic illness; may introduce noise in liver-focused clustering.


