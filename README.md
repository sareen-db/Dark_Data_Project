# Dark_Data_Project
Group Project for Columbia and FNL. 
Analyze clinical trials in oncology. 

## Clinical trials in oncology can be terminated and suspended for various reasons, among which business related ones have the most potential to resume. This project intends to analyze terminated oncology cilnical trials and find out the real reasons behind their closure. The compounds that ended because of financial and businness operations will be selected and further analyzed for possible resumption or secondary usage. 

### 1. Download clinical trials data from https://clinicaltrials.gov. 
Select criteria. Here we selected "Supended", "Terminated","Withdrawn" for "Recruitment" and showed all the columns. 

### 2. Scrape the termination reasons reported to FDA for each trial on https://clinicaltrials.gov and filter out ones with safety concerns and new sponsors. 
#### 2.1 Scrape termination reasons 
Visit each trial's page and scrape the reasons in parenthesis from "Recruitment Status". 
Required files:
	Data Preparation_Clinical.ipynb 
	clinical trials . csv 
Output: clinial trials .csv (with a new "Reasons" column)
#### 2.2 Produce a filtered list
Delete ones that ended because of safety. Search on google and delete ones that are already FDA approved (with a real drug name) or have a new sponsor. 
Output: clinical trials filtered .csv 

### 3. Find the real termination reasons for each trial from various sources by Google Search. 
The termination reasons reported to FDA may be different from the true reasons. Most often, companies tell their investors the real reasons, which can be found on financial news articles, company news, SEC filings, etc. 
#### 3.1 Form NLP corpus. 
- Search on google using keywords "drug name" + "company name " + "keyword". (common keywords related to trial termination: abandon, terminate, discontinue, close/closure) 
- Go into each article on the first page of serach result and take out sentences that contain these keywords, which are the most likely to include explanations for termination. 
Required files: 
	GetReasons.ipynb (Section 1 & 2)
	Filtered Listclinicaltrials_data_0_2000_labeled_final.xls

Output: clinicaltrials_trialsRangeStart_trialsRangeEnd_selected_reasons.csv


#### 3.2 Produce wordclouds. 
Form word clouds using the corpus of sentences. Visualize words that are linked to this trial that appeared most frequently. This helps us understand what is talked about and the corpus vocabularies to prepare for designing generic and task-specific alogrithms. 
Required files: 
	GetReasons.ipynb (Section 3)

Output: word cloud files titled "trial#_ drugname.png", in folder "wordclouds" 

### 4. Future Work
This algorithm produces an NLP corpus containing sentences related to the trial termination. Word clouds aid with visualizing the most frequently present words, to help us design more suitable algorithms. We need further processing on the corpus to dig out useful information, or more targeted scraping to get better sources for reasons. 
