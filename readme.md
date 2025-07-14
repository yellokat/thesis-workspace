# Workflow
The workflow below has been applied to two sources of Google Scholar Search results.

<b>Search A</b> :
- Regular Google Scholar Search.
- Search term used is `(mamba OR "state space" OR "state-space" OR "state-spaces") AND (recomend OR recommender OR recommendation)`.

<b>Search B</b> : 
- I only search within articles that cite `Mamba: Linear-time sequence modeling with selective state spaces`.
- Search term used is `recommendation`.

## 1. Search for papers in Google Scholar.
> I tried crawling Google Scholar automatically but have failed due to automation detection, so I have resorted to downloading HTML files manually.

I use python to write code to extracts article data when given an html file representing a Google Scholar search result page. Each page of Google Scholar search results contains 20 records of publication.

<b>Search A</b> and <b>Search B</b> results in 48 and 21 pages, respectively. \
977 papers were found in <b>Search A</b>. \
420 papers were found in <b>Search B</b>.

I arrange the search results in tabular format, with the following columns:
- Title
- List of authors
- Link to publication, if available
- Abstract
- Number of citations, if available

Steps to reproduce this can be found in `notebooks/1-google-scholar-crawl.ipynb`.

## 2. Categorize search results

<b>Search A</b> :

Collected papers are manually categorized by the criteria below, starting from the top results.

- `Concrete-RecSys`
- `Concrete-RecSys-Related`
- `Concrete-Non-RecSys`
- `Survey-RecSys`
- `Survey-RecSys-Related`
- `Survey-Non-RecSys`
- `Non-Mamba`
- `Completely Irrelevant`

After categorizing 300 papers, I stop the manual work because no more papers relevant to the topic (Concrete method attempts to utilize Mamba in Recommender Systems) were to be found. Data visualzation to back up this logic can be found in `notebooks/2-eda.ipynb`.

Tabular data after manual categorization can be found in `notebooks/processed-data`.

<b>Search B</b> :

I manually assign boolean fields to the papers collected:

- Is the paper related to AI/ML research?
  - Theses, dissertations, technical reports, etc. are excluded.
- Is the paper a survey paper?
  - `True` if the paper is a survey paper.
  - `False` if the paper proposes a concrete method.
- Is the paper's primary interest Recommender Systems?
- Is the paper's primary interest relevant to `mamba`?

After categorizing the top 100 papers, I stop the manual work because no more papers relevant to the topic (Concrete method attempts to utilize Mamba in Recommender Systems) were to be found. Data visualzation to back up this logic can be found in `notebooks/2-eda.ipynb`. 

Tabular data after manual categorization can be found in `notebooks/processed-data`.

## 3. Find out where papers were submitted/published

I manually search the web to find where the relevant papers were submitted to.

<b>Search A</b> : 22 concrete method papers concerning mamba application in recommender systems were found in top 300 articles. Among those articles, 12 papers were accepted to significant journals and conferences.

<b>Search B</b> : 35 concrete method AI/ML research papers concerning mamba application in recommender systems were found in top 100 articles. Among those articles, 26 papers were accepted to significant journals and conferences.

11 papers of <b>Search A</b> and <b>Search B</b> overlap. After removing the duplicates, a total of 40 papers featured concrete methods of mamba application in recommender systems. Among those 40 papers, 27 papers were accepted to recognized journals and conferences.
