# Dark_Data_Project
This is a group oroject for Columbia and FNL. Here we try to analyze clinical trials in oncology. 

Clinical trials in oncology can be terminated and suspended for various reasons, among which business related ones have the most potential to resume. This project intends to analyze terminated oncology cilnical trials and find out the real reasons behind their closure. The compounds that ended because of financial and businness operations will be selected and further analyzed for possible resumption or secondary usage. 

# 1. Download clinical trials data. 
Go to https://clinicaltrials.gov. Select criteria. Here we selected "Supended", "Terminated","Withdrawn" for "Recruitment" and showed all the columns. 
Output: clinicaltrials_data_direct_download.csv

# 2. Data Cleaning and Filtering 
## 2.1 Scrape termination reasons reported to FDA
Visit each trial's page and scrape the reasons in parenthesis from "Recruitment Status". <br /><br />
Required files:<br />
	> Data Preparation_Clinical.ipynb <br />
	> clinicaltrials_data_direct_download.csv <br />
Output: clinicaltrials_data.csv (with a new "Reasons" column) <br />

## 2.2 Produce a filtered list
Delete ones that ended because of safety. Search on google and delete ones that are already FDA approved (with a real drug name) or have a new sponsor. <br />
Output: clinicaltrials_data_labelled.csv 

# 3. Find the real termination reasons for each trial from various sources by Google Search. 
The termination reasons reported to FDA may be different from the true reasons. Most often, companies tell their investors the real reasons, which can be found on financial news articles, company news, SEC filings, etc. 
## 3.1 Form NLP corpus. 
* Search on google using keywords "drug name" + "company name " + "keyword". (common keywords related to trial termination: abandon, terminate, discontinue, close/closure) <br />
* Go into each article on the first page of serach result and take out sentences that contain these keywords, which are the most likely to include explanations for termination. <br /><br />
Required files: <br />
	> GetReasons.ipynb (Section 1 & 2) <br />
	> Filtered List: clinicaltrials_data_0_2000_labelled.xls <br />

Output: clinicaltrials_trialsRangeStart_trialsRangeEnd_selected_reasons.csv <br />

## 3.2 Produce wordclouds. 
Form word clouds using the corpus of sentences. Visualize words that are linked to this trial that appeared most frequently. This helps us understand what is talked about and the corpus vocabularies to prepare for designing generic and task-specific alogrithms. <br /><br />
Required files: <br />
	> GetReasons.ipynb (Section 3) <br />

Output: word cloud files titled "trial#_ drugname.png", in folder "wordclouds" 

### 4. Future Work
This algorithm produces an NLP corpus containing sentences related to the trial termination. Word clouds aid with visualizing the most frequently present words, to help us design more suitable algorithms. We need further processing on the corpus to dig out useful information, or more targeted scraping to get better sources for reasons. 
