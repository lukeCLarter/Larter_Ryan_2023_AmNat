**Female preferences for more elaborate signals are an emergent outcome of male chorusing interactions in túngara frogs**

By L.C. Larter and M.J. Ryan


About the Study

In this study, we investigated call-timing interactions among male túngara frogs by recording calling patterns of 2-6 interacting males within experimental choruses and extracting interaction patterns. We also investigated the effects of observed interaction patterns on female preferences via phonotaxis tests, and investigated what aspects of male phenotypes influenced calling strategies. Below, the analysis tools used, and the folders and files in the data repository are described. At the end of this document, we describe how these different files fit into the work-flow of the article.


**Version Information and Packages Used** 

- RStudio v2021.09.0/351 running R v4.1.2. Packages used:
  - lme4_1.1-27.1
  - lmerTest_3.1-3
  - ggplot2_3.3.5
  - DHARMa_0.4.6
  - sjstats_0.18.1
  - tidyverse_1.3.1
  - vcd_1.4-10
  - sjPlot_2.8.10
  - smatr_3.4-8
  - sna_2.6
  - ggpubr_0.4.0 
  - jpeg_0.1-9
- Jupyter Notebook v6.3.0 running Python v3.8.8. Packages used:
  - pandas v1.2.4
  - numpy v1.20.1
  - matplotlib v3.3.4
  - joypy v0.2.6
  - seaborn v0.11.1
  - scipy v1.6.2.


**Folder ‘GLMMS’**

This folder contains sub-folders containing R markdown files and datasets to run all of the mixed models in the article. The different sub-folders and their contained files are described below:

Sub-Folder ‘IOI vs Chorus Size Model’:

- *IOI_vs_Chorus_Size_model_data.csv*: 100 randomly selected inter-onset intervals (IOI: the time elapsing between successive calls from a single calls) per male calling in experimental frog choruses of different size. ‘lag’ column is IOIs in seconds, ‘chorus_size’ is total number of males in that chorus, ‘chorus_name’ is the identifier of that particular chorus, and ‘toe_clip_number’ is the identifier of the particular male. Note, though automatically-generated timestamps were manually and visually verified as correct, there are some very precise duplicate values for the IOIs that were generated using these timestamps. These were verified as being accurate, and the high degree of duplicate precision is presumably due to the rounding occurring within the time-stamp detection process or the calculation of the IOIs from these timestamps. 
- *IOI_vs_Chorus_Size_Model_Code.rmd*: Code using *IOI_vs_Chorus_Size_model_data.csv* to build and evaluate a LMM linear regression model. More detail in code comments.

Sub-Folder ‘Model 1 (Logistic regression, chucks free from overlap)’:

- *free_chucks_model_data.csv*: Data on call complexity and the number of chucks left free of the detrimental intervals of chorus-mates for 10 randomly selected calls for each call complexity level produced per male calling in experimental frog choruses of different size. ‘call_complexity’ is the total number of chucks per call, and ‘chucks_free_rest’ is the number of chucks of that call that are not covered by the first 150ms (detrimental interval) of any chorus-mates whines, ‘chorus_size’ is total number of males in that chorus, ‘chorus_name’ is the identifier of that particular chorus, and ‘toe_clip_number’ is the identifier of the particular male.  
- *Model 1 Code.rmd*: Code using *free_chucks_model_data.csv* to build and evaluate a GLMM logistic regression model. More detail in code comments.

Sub-Folder ‘Model 2 (Logistic regression, more than 1 chuck)’:

- *complexity_vs_chorus_size_model_data.csv*: Call complexity for 100 randomly chosen calls per male calling in experimental frog choruses of different size. ‘call_complexity’ is number of chucks appended to that call, ‘mass’ is mass of that male in grams, ‘svl’ is the length of that male in mm, ‘chorus_size’ is total number of males in that chorus, ‘chorus_name’ is the identifier of that particular chorus, and ‘toe_clip_number’ is the identifier of the particular male.    
- *Model 2 Code.rmd*: Code using *complexity_vs_chorus_size_model_data.csv* to build and evaluate a GLMM logistic regression model. More detail in code comments.

Sub-Folder ‘Model 3 (Count of 3+ chuck calls)’:

- *complexity_vs_chorus_size_model_data.csv*: this file is identical to the identically-named file in the previous sub-folder.
- *Model 3 Code.rmd*: Code using *complexity_vs_chorus_size_model_data.csv* to build and evaluate a GLMM Poisson regression model. More detail in code comments.


**Folder ‘QAP’:**

Data and code to perform the quadratic assignment procedure for choruses of different sizes. 

Has 3 sub-folders; ‘QAP_files_six_males’, ‘QAP_files_five_males’, and ‘QAP_files_four_males’ which have data and code to run this analysis for choruses of 6, 5, and 4 males in size, respectively. Each sub-folder has versions of the same 3 files:

- *…_spike_tile_matrix.csv*: Matrices for different choruses (preceding numerical code is chorus identifier) that show the degree of call-overlap among different chorus-mates, as described by the modified spike tiling equation (Cutts and Eglen 2014) described in SI2 of the main text.
- *…_distance.csv*: Matrices for different choruses (preceding numerical code is chorus identifier) that describe the distance (m) between different chorus-mates in these experimental choruses.
- *QAP_#.rmd*: Code for implementing the QAP analysis for each different size of chorus (chorus size takes the place of the # in the file name). More details in code comments.

Cutts CS, Eglen SJ. 2014. Detecting pairwise correlations in spike trains: An objective comparison of methods and application to the study of retinal waves. Journal of Neuroscience. 34(43):14288-14303.


**Folder ‘Python_Figure_Code’:**

Data and code to create certain figures.

- *lags_relative_to_chorusmates_vs_chorus_size_data.csv*: Descriptions of the temporal relationship between the onset of calls and the call by a chorus-mate that directly preceded them. 100 randomly chosen calls per male calling in experimental frog choruses of different size. ‘lag’ is the delay in seconds between the onset of the focal call and the onset of the most recent call by any chorus-mate, and ‘size’ is the number of males in that chorus.
- *master_gap_spreadsheet.csv*: Descriptions of the duration (seconds) and time between (seconds) silent periods (i.e., when no other chorus-mate was calling) from the perspective of a randomly-chosen focal male in different choruses. ‘time_between’ is the time in seconds between two silent gaps, ‘duration’ is the duration in seconds of these silent gaps, ‘size’ is the number of males in that chorus, and ‘chorus_name’ is a unique identifier for that specific chorus.
- *Python_Figures_Code.ipynb*: Jupyter notebook that creates figures with this data. More details in code comments.

**Folder ‘Phonotaxis_Analysis’:**

Code for analyzing outcome of phonotaxis experiments described in the article.

- *Female_Preference_Function_Code.rmd*: Code to conduct binomial tests for preferences for temporal associations of leader/follower calls, and code to display the results as a preference function. Data for these tests is coded within the document itself.
- *Call_pic.jpg*: Picture of call to put in background of preference function figure.
- *Natural_Calls_Precedence_Effects_Code.rmd*: Code to conduct binomial tests for our experiments validating the effects of overlap with natural calls, and code to display the results as a figure. Data for these tests is coded within the document itself.
- *Preference_For_nonOverlapped_Calls_Code.rmd*: Code to conduct binomial tests for our experiments investigating the detrimental effects of call overlap when the overlapping calls come from different distances away. Code for figures displaying these results too. Data for these tests is coded within the document itself.
- *Preference_For_WCvsWCCC_Code.rmd*: Code to conduct binomial tests for our experiments investigating preferences for a whine+1chuck vs a whine+3chucks when both calls are overlapped. Code for figures displaying these results too. Data for these tests is coded within the document itself.


**Folder ‘Example_Chorus_Recordings’**:

Contains 5-minute excerpts of raw recordings from two 6-male choruses, to allow readers to hear the chorusing dynamics themselves, and to give them a view of the typical quality of these recordings, regarding cross-talk between microphones etc. Best visualized by dragging all tracks for a single chorus into an audio editor such as Audacity.

` `Sub-Folder ‘210927_001’:

- *210927_001_Tr1.wav*: The is a recording coming from the tie-clip mic positioned next to male 1 (Tr1) in the 6-male chorus designated as ‘210927_001’. Vertices of the chorus were labelled 1-6 clockwise around the hexagon. This nomenclature is the same for the remaining frogs in the chorus, e.g. *…Tr2.wav* is male 2, etc.

Sub-Folder ‘211001_002’:

- *211001_002_Tr1.wav*: The is a recording coming from the tie-clip mic positioned next to male 1 (Tr1) in the 6-male chorus designated as ‘210927_001’. Vertices of the chorus were labelled 1-6 clockwise around the hexagon. This nomenclature is the same for the remaining frogs in the chorus, e.g. *…Tr2.wav* is male 2, etc.



**Workflow**

The article is divided into 3 sections referred to as ‘Aims’ that deal with broad questions combining several analytical approaches. Here, I will orient the reader as to which of the above analyses, scripts, and data files belong to each question in each Aim.

**Aim 1: Investigate call-timing and overlap patterns at different chorus sizes.** 

General Call-Timing and Overlap Patterns by Chorus Size

- Sub-Folder ‘IOI vs Chorus Size Model’ within Folder ‘GLMMs’
- Folder ‘Python_Figure_Code’
- Folder ‘Example_Chorus_Recordings’, if readers want to see/hear chorusing interactions themselves.

Call Overlap Patterns by Distance 

- Folder ‘QAP’

**Aim 2: Investigate the influence of call-timing and overlap on female choice.**

Female Preference Function for Temporal Call Associations

- *Female_Preference_Function_Code.rmd* within Folder ‘**Phonotaxis_Analysis**’
- *Call_pic.jpg* within Folder ‘**Phonotaxis_Analysis**’ (for plot in *Female_Preference_Function_Code.rmd*)
- *Natural_Calls_Precedence_Effects_Code.rmd* within Folder ‘**Phonotaxis_Analysis**’ (verifying results in *Female_Preference_Function_Code.rmd* with natural calls; in Supplemental Information of article)

Influence of Distance on Attractiveness Costs of Call Overlap

- *Preference_For_nonOverlapped_Calls_Code.rmd*

**Aim 3: Investigate multiple chucks as a condition-dependent means of mitigating risks to attractiveness.** 

Benefits of Multiple Chucks for Avoiding Complete Chuck Overlap

- Sub-Folder ‘Model 1 (Logistic regression, chucks free from overlap)’ within Folder ‘GLMMs’

Preferences for Multiple Chucks in the Presence and Absence of Call Overlap

- *Preference_For_WCvsWCCC_Code.rmd* within Folder ‘**Phonotaxis_Analysis**’

Male Phenotype and Social Environment as Drivers of Call Elaboration

- Sub-Folder ‘Model 2 (Logistic regression, more than 1 chuck)’ within Folder ‘GLMMs’
- Sub-Folder ‘Model 3 (Count of 3+ chuck calls)’ within Folder ‘GLMMs’


