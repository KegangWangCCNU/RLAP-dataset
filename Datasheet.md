# Datasheet for RLAP Dataset  
## Motivation  
1. **For what purpose was the dataset created?** *(Was there a specific task in mind? Was there a specific gap that needed to be filled? Please provide a description.)*

    In order to solve the problem that existing datasets cannot train rPPG models well, its purpose is to provide a highly synchronized, lossless compressed dataset and provide the corresponding evaluation framework PhysBench and recording tool PhysRecorder.

1. **Who created this dataset (e.g., which team, research group) and on behalf of which entity (e.g., company, institution, organization)?**

    Master's student Kegang Wang developed the dataset collection program, with guidance from his supervisor Yantao Wei. Other graduate students in the team collaborated on the data collection process; for more information, please refer to the nutrition label. All researchers are from Central China Normal University (CCNU).  

1. **Who funded the creation of the dataset?** *(If there is an associated grant, please provide the name of the grantor and the grant name and number.)*

    The funding for data collection is provided by Central China Normal University (CCNU).  

1. **Any other comments?**  

    None  
    
## Composition  
1. **What do the instances that comprise the dataset represent (e.g., documents, photos, people, countries)?** *(Are there multiple types of instances (e.g., movies, users, and ratings; people and interactions between them; nodes and edges)? Please provide a description.)*

    The dataset contains videos and documents in different formats. They record the facial images and physiological signals of various subjects, as well as the timestamps required to process this data.
    
1. **How many instances are there in total (of each type, if appropriate)?**  

    A total of 58 participants, all of whom were students.  
    
1. **Does the dataset contain all possible instances or is it a sample (not necessarily random) of instances from a larger set?** *(If the dataset is a sample, then what is the larger set? Is the sample representative of the larger set (e.g., geographic coverage)? If so, please describe how this representativeness was validated/verified. If it is not representative of the larger set, please describe why not (e.g., to cover a more diverse range of instances, because instances were withheld or unavailable).)*

    Yes, the dataset contains all the data we collected, with no concealment.  
    
1. **What data does each instance consist of?** *(``Raw'' data (e.g., unprocessed text or images)or features? In either case, please provide a description.)*
    
    Each instance contains several different formats of videos (RAW RGB, MJPG compression, H264 compression) and the corresponding physiological signals.
    
1. **Is there a label or target associated with each instance? If so, please provide a description.**  

    Each instance has video frames with timestamps and BVP waveforms.  
    
1. **Is any information missing from individual instances?** *(If so, please provide a description, explaining why this information is missing (e.g., because it was unavailable). This does not include intentionally removed information, but might include, e.g., redacted text.)*  

    Yes, some instances may lack a portion of frames or physiological signals, which is due to the stuttering of the equipment used for collection. All missing data are marked in missed_frames.csv, and for instances with too much missing data, the fold is set to -1 and not included in training and testing experiments.  
    
1. **Are relationships between individual instances made explicit (e.g., users' movie ratings, social network links)?** *( If so, please describe how these relationships are made explicit.)*  

    No, there may be relationships, but it is not the research goal. To protect individual privacy, all unnecessary information is hidden.  
    
1.  **Are there recommended data splits (e.g., training, development/validation, testing)?** *(If so, please provide a description of these splits, explaining the rationale behind them.)*
    
    Yes, we divide the dataset into 5 folds randomly according to the subjects, with 0 for validation, 4 for testing, and 1, 2, and 3 for training. The division is random but will provide relevant data in nutritional labels and PhysBench framework.
    
1. **Are there any errors, sources of noise, or redundancies in the dataset?** *(If so, please provide a description.)*
    
    None.
    
1. **Is the dataset self-contained, or does it link to or otherwise rely on external resources (e.g., websites, tweets, other datasets)?** *(If it links to or relies on external resources, a) are there guarantees that they will exist, and remain constant, over time; b) are there official archival versions of the complete dataset (i.e., including the external resources as they existed at the time the dataset was created); c) are there any restrictions (e.g., licenses, fees) associated with any of the external resources that might apply to a future user? Please provide descriptions of all external resources and any restrictions associated with them, as well as links or other access points, as appropriate.)*
    
    Self-contained.
    
1. **Does the dataset contain data that might be considered confidential (e.g., data that is protected by legal privilege or by doctor-patient confidentiality, data that includes the content of individuals' non-public communications)?** *(If so, please provide a description.)*
    
    None.
    
1. **Does the dataset contain data that, if viewed directly, might be offensive, insulting, threatening, or might otherwise cause anxiety?** *(If so, please describe why.)*
    
    None.
    
1. **Does the dataset relate to people?** *(If not, you may skip the remaining questions in this section.)*
    
    Yes.
    
1. **Does the dataset identify any subpopulations (e.g., by age, gender)?** *(If so, please describe how these subpopulations are identified and provide a description of their respective distributions within the dataset.)*

    The dataset includes 58 subjects of different ages and genders, with a very concentrated age distribution of approximately 20-24 years old, including 16 males and 42 females.  
    
1. **Is it possible to identify individuals (i.e., one or more natural persons), either directly or indirectly (i.e., in combination with other data) from the dataset?** *(If so, please describe how.)*
    
    Yes, the dataset contains facial images that can directly identify individuals, but it does not contain more identity information.  
    
1. **Does the dataset contain data that might be considered sensitive in any way (e.g., data that reveals racial or ethnic origins, sexual orientations, religious beliefs, political opinions or union memberships, or locations; financial or health data; biometric or genetic data; forms of government identification, such as social security numbers; criminal history)?** *(If so, please provide a description.)*
   
   The dataset contains individual BVP waveforms, but this is not sensitive data.
   
1.  **Any other comments?**

    None.
    
## Collection Process
1. **How was the data associated with each instance acquired?** *(Was the data directly observable (e.g., raw text, movie ratings), reported by subjects (e.g., survey responses), or indirectly inferred/derived from other data (e.g., part-of-speech tags, model-based guesses for age or language)? If data was reported by subjects or indirectly inferred/derived from other data, was the data validated/verified? If so, please describe how.)*
    
    Collect raw data from a webcam and pulse oximeters using PhysRecorder.
  
1. **What mechanisms or procedures were used to collect the data (e.g., hardware apparatus or sensor, manual human curation, software program, software API)?** *(How were these mechanisms or procedures validated?)*
    
    The program written by Kegang Wang directly reads raw data from Logitech C930c webcam and Contec CMS50E pulse oximeter.  

1. **If the dataset is a sample from a larger set, what was the sampling strategy (e.g., deterministic, probabilistic with specific sampling probabilities)?**
    
    The dataset is not a subset.  
    
1. **Who was involved in the data collection process (e.g., students, crowdworkers, contractors) and how were they compensated (e.g., how much were crowdworkers paid)?**
   
    The dataset includes 5 experimenters and 58 participants. Experimenters will receive a subsidy of 400 to 600 CNY from the funding, and each participant will be provided with a reward of 40 CNY.  
    
1. **Over what timeframe was the data collected?** *(Does this timeframe match the creation timeframe of the data associated with the instances (e.g., recent crawl of old news articles)?  If not, please describe the timeframe in which the data associated with the instances was created.)*

    It is the summer of 2022, and all precise times are recorded in the dataset.  
    
1. **Were any ethical review processes conducted (e.g., by an institutional review board)?** *(If so, please provide a description of these review processes, including the outcomes, as well as a link or other access point to any supporting documentation.)*
    
    Yes, the dataset collection has undergone ethical review. Please check https://github.com/KegangWangCCNU/RLAP-dataset  
    
1. **Does the dataset relate to people?** *(If not, you may skip the remaining questions in this section.)*
    
    Yes.
    
1. **Did you collect the data from the individuals in question directly, or obtain it via third parties or other sources (e.g., websites)?**

    Direct collection.  
    
1. **Were the individuals in question notified about the data collection?** *(If so, please describe (or show with screenshots or other information) how notice was provided, and provide a link or other access point to, or otherwise reproduce, the exact language of the notification itself.)*

    Yes, all participants signed informed consent forms. To obtain a copy of the document, please contact kegangwang@mails.ccnu.edu.cn.
    
1. **Did the individuals in question consent to the collection and use of their data?** *(If so, please describe (or show with screenshots or other information) how consent was requested and provided, and provide a link or other access point to, or otherwise reproduce, the exact language to which the individuals consented.)*

    Yes, consistent with the previous one.
    
1. **If consent was obtained, were the consenting individuals provided with a mechanism to revoke their consent in the future or for certain uses?** *(If so, please provide a description, as well as a link or other access point to the mechanism (if appropriate).)*
   
    The participants can contact the institution later to withdraw their consent, and the dataset will be updated accordingly.

1. **Has an analysis of the potential impact of the dataset and its use on data subjects (e.g., a data protection impact analysis) been conducted?** *(If so, please provide a description of this analysis, including the outcomes, as well as a link or other access point to any supporting documentation.)*
    
    None.
    
1. **Any other comments?**

    None.
## Preprocessing/cleaning/labeling  
1. **Was any preprocessing/cleaning/labeling of the data done (e.g., discretization or bucketing, tokenization, part-of-speech tagging, SIFT feature extraction, removal of instances, processing of missing values)?** *(If so, please provide a description. If not, you may skip the remainder of the questions in this section.)*

    No.
    
1. **Was the "raw" data saved in addition to the preprocessed/cleaned/labeled data (e.g., to support unanticipated future uses)?** *(If so, please provide a link or other access point to the "raw" data.)*
    
    All provided data are raw data.
    
1. **Is the software used to preprocess/clean/label the instances available?** *(If so, please provide a link or other access point.)*
    
    See https://github.com/KegangWangCCNU/PhysBench
    
1. **Any other comments?**  

    None.
    
## Uses
1. **Has the dataset been used for any tasks already?** *(If so, please provide a description.)*

    The dataset is used for training the rPPG model, and experiments show that it is a good training set, which can improve the performance of the model compared to existing training sets.

1. **Is there a repository that links to any or all papers or systems that use the dataset?** *(If so, please provide a link or other access point.)*
  
    Not yet.  
    
1. **What (other) tasks could the dataset be used for?**
    
    The dataset can be used for spontaneous emotion detection and learning engagement detection. However, some related data is private and not included in the publicly released version.
    
1. **Is there anything about the composition of the dataset or the way it was collected and preprocessed/cleaned/labeled that might impact future uses?** *(For example, is there anything that a future user might need to know to avoid uses that could result in unfair treatment of individuals or groups (e.g., stereotyping, quality of service issues) or other undesirable harms (e.g., financial harms, legal risks)  If so, please provide a description. Is there anything a future user could do to mitigate these undesirable harms?)*

    Without these possibilities.
    
1. **Are there tasks for which the dataset should not be used?** *(If so, please provide a description.)*
   
    None.
    
1. **Any other comments?**  

    None.
## Distribution
1. **Will the dataset be distributed to third parties outside of the entity (e.g., company, institution, organization) on behalf of which the dataset was created?** *(If so, please provide a description.)*
 
    Yes, it can only be used for academic research purposes.
    
1. **How will the dataset will be distributed (e.g., tarball  on website, API, GitHub)?** *(Does the dataset have a digital object identifier (DOI)?)*

    Refer to https://github.com/KegangWangCCNU/RLAP-dataset
    
1. **When will the dataset be distributed?**

    Already publicly available, need to fill out the agreement.
    
1. **Will the dataset be distributed under a copyright or other intellectual property (IP) license, and/or under applicable terms of use (ToU)?** *(If so, please describe this license and/or ToU, and provide a link or other access point to, or otherwise reproduce, any relevant licensing terms or ToU, as well as any fees associated with these restrictions.)*

    https://creativecommons.org/licenses/by-nc-nd/4.0/legalcode
    
1. **Have any third parties imposed IP-based or other restrictions on the data associated with the instances?** *(If so, please describe these restrictions, and provide a link or other access point to, or otherwise reproduce, any relevant licensing terms, as well as any fees associated with these restrictions.)*

    Yes, the download link for the dataset will be verified, and only authorized entities can download it with a 14-day validity period.

1. **Do any export controls or other regulatory restrictions apply to the dataset or to individual instances?** *(If so, please describe these restrictions, and provide a link or other access point to, or otherwise reproduce, any supporting documentation.)*

    None.
    
1. **Any other comments?**

    None.
    
## Maintenance
1. **Who is supporting/hosting/maintaining the dataset?**
    
    Central China Normal University (CCNU) and Kegang Wang jointly maintain it, hosted by Tencent Cloud.  
    
1. **How can the owner/curator/manager of the dataset be contacted (e.g., email address)?**

    kegangwang@mails.ccnu.edu.cn  
    
1. **Is there an erratum?** *(If so, please provide a link or other access point.)*

    No, the dataset will not be updated, and any issues will be addressed through updates to the PhysBench framework.
    
1. **Will the dataset be updated (e.g., to correct labeling errors, add new instances, delete instances')?** *(If so, please describe how often, by whom, and how updates will be communicated to users (e.g., mailing list, GitHub)?)*
    
    Same as previous.
    
1. **If the dataset relates to people, are there applicable limits on the retention of the data associated with the instances (e.g., were individuals in question told that their data would be retained for a fixed period of time and then deleted)?** *(If so, please describe these limits and explain how they will be enforced.)*

    No, the participants were informed that their data sets would be permanently retained, but they could request the institution to delete their data if necessary.
    
1. **Will older versions of the dataset continue to be supported/hosted/maintained?** *(If so, please describe how. If not, please describe how its obsolescence will be communicated to users.)*

    The dataset will not be updated.
    
1. **If others want to extend/augment/build on/contribute to the dataset, is there a mechanism for them to do so?** *(If so, please provide a description. Will these contributions be validated/verified? If so, please describe how. If not, why not? Is there a process for communicating/distributing these contributions to other users? If so, please provide a description.)*

    They need to obtain written permission from Central China Normal University (CCNU) before they can release the extended dataset.
    
1. **Any other comments?**

    None.
