# From Norms to Neuropsychopathology: Exploring Neuroanatomical & Neuropsychiatric Variation in Alzheimer’s Disease Through Normative Modeling

This study extends analyses conducted by [Verdi et al. (2023)](https://www.neurology.org/doi/10.1212/WNL.0000000000207298), who utilized normative modeling techniques to delineate neuroanatomical heterogeneity in Alzheimer's disease. We employ a similar methodological framework to supplement these insights by integrating both structural MRI data and neuropsychiatric symptom profiles. This integration allowed us to explore more deeply the neuroanatomical and neuropsychiatric underpinnings of Alzheimer's disease across different phenotypes within our ADNI subset. This study was conducted by the [Applied Neuroimaging Statistics Research Laboratory](https://www.mcleanmri.org/ansl.html) at McLean Hospital & Harvard Medical School.

## Project Overview

### Analytic Background
Our study data were a subset derived from the Alzheimer's Disease Neuroimaging Initiative (ADNI) ADNI3 wave data bank. This was due to the harmonization of scanner sequence protocols across data collection sites that began during this wave. We only included subjects that had both structural MRI and PET (amyloid) data collected, followed by QA of these data. This analysis leveraged a normative model developed by the Predictive Clinical Neuroscience Group at the Donders Institute and Radboud UMC, which aims to predict and stratify brain disorders on the basis of neuroimaging data. Specifically, we used 'HBR_lifespan_36K_79sites', which makes use of the Hierarchical Bayesian Regression algorithm trained on 37,128 subjects from 79 different collection sites, across the human lifespan.

Please refer to the Group's [Normative Modeling Graphical User Interface (GUI)](https://pcnportal.dccn.nl/) for more information. For reference to the template Python code used to calculate the deviation scores, please look at the Group's [Braincharts GUI](https://pcntoolkit.readthedocs.io/en/latest/pages/apply_normative_models.html).

### Considerations
Ideally, both adaptation and testing sets would be balanced by age, sex, and site (covariates) following something like a 60/40 or 70/30 split of healthy controls. **However**, given our limited sample size, we decided to keep all of our healthy control and patient data **isolated**.

**In our analysis**: The **adaptation set** is used to calibrate for site (**only** healthy controls) while the **testing set** is used **exclusively** for patient-phenotyped data. Healthy control phenotypes include 'A-C-' (amyloid *negative*, cognitive impairment *negative*) & 'A+C-' (amyloid *positive*, cognitive impairment *negative*).

Patient-phenotypes include 'A+C+' (amyloid *positive*, cognitive impairment *positive*) & 'A-C+' (amyloid *negative*, cognitive impairment *positive*). As a consequence of both a smaller sample size & larger site numbers (59 sites), our group elected to utilize the MRI manufacturer (3 total) of the subject's imaging data to act as a pseudo `site` variable thus giving more power to viably calibrate for potential "site" influences:
- `1` = `GE`
- `2` = `Philips`
- `3` = `Siemens`
