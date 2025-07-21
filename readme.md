# List of relevant papers

| Title | Published in | Conference |
|----------|----------|----------|
|Auto Encoding Neural Process for Multi-interest Recommendation|Conference|AAAI 2025|
|GeoMamba: Towards Multi-granular POI Recommendation with Geographical State Space Model|Conference|AAAI 2025|
|SIGMA: Selective Gated Mamba for Sequential Recommendation|Conference|AAAI 2025 Poster Session|
|Behavior-Dependent Linear Recurrent Units for Efficient Sequential Recommendation|Conference|CIKM 2024|
|Train once, deploy anywhere: Matryoshka representation learning for multimodal recommendation|Conference|Findings of EMNLP 2024|
|Judge a Book by its Cover: A Multimodal Approach to Book Genre Prediction|Conference|ICWR 2025|
|F2MSA2: Integrating Mamba and Self-Attention for Sequential Recommendation|Conference|IEEE ICAIRC 2025|
|M3Rec: Selective State Space Models with Mixture-of-Modality Experts for Multi-Modal Sequential Recommendation|Conference|IEEE ICASSP 2025|
|Fine-grained global modeling learning for personalized federated sequential recommender|Conference|IEEE ICASSP 2025|
|Test-Time Alignment for Tracking User Interest Shifts in Sequential Recommendation|Conference|RecSys 2025|
|STAR-Rec: Making Peace with Length Variance and Pattern Diversity in Sequential Recommendation|Conference|SIGIR 2025|
|PatchRec: Multi-Grained Patching for Efficient LLM-based Sequential Recommendation|Conference|SIGIR 2025|
|Mitigating Distribution Shifts in Sequential Recommendation: An Invariance Perspective|Conference|SIGIR 2025|
|Linear recurrent units for sequential recommendation|Conference|WSDM 2024|
|Hyperbolic Variational Graph Auto-Encoder for Next POI Recommendation|Conference|WWW 2025 Poster Session|
|Frequency-Augmented Mixture-of-Heterogeneous-Experts Framework for Sequential Recommendation|Conference|WWW 2025 Poster Session 3|
|Covariance Attention Guidance Mamba Hashing for cross-modal retrieval|Journal|Engineering Applications of Artificial Intelligence|
|Coformer for session-based recommendation with dual positional information|Journal|Expert Systems with Applications (2025.07)|
|GeoMamba: Towards Efficient Geography-aware Sequential POI Recommendation|Journal|IEEE Access 2025|
|A Local context enhanced Consistency-aware Mamba-based Sequential Recommendation model|Journal|Information Processing & Management (2025)|
|EMK-KEN: A high-performance approach for assessing knowledge value in citation network|Journal|Knowledge-Based Systems|
|Mamba4rec: Towards efficient sequential recommendation with selective state space models|Workshop|RelKD@KDD 2024|
|A Novel Mamba-based Sequential Recommendation Method|Pre-print|Huawei|
|EchoMamba4Rec: Harmonizing Bidirectional State Space Models with Spectral Filtering for Advanced Sequential Recommendation|Pre-print|N/A|
|Gated Rotary-Enhanced Linear Attention for Long-term Sequential Recommendation|Pre-print|N/A|
|Graph-Mamba 기반 POI 추천 시스템|Pre-print|N/A|
|HMamba: Hyperbolic Mamba for Sequential Recommendation|Pre-print|N/A|
|M2Rec: Multi-scale Mamba for Efficient Sequential Recommendation|Pre-print|N/A|
|MMM4Rec: An Transfer-Efficient Framework for Multi-modal Sequential Recommendation|Pre-print|N/A|
|MUFM: A Mamba-Enhanced Feedback Model for Micro Video Popularity Prediction|Pre-print|N/A|
|Mamba for Scalable and Efficient Personalized Recommendations|Pre-print|N/A|
|Matrrec: Uniting mamba and transformer for sequential recommendation|Pre-print|N/A|
|Mlsa4rec: Mamba combined with low-rank decomposed self-attention for sequential recommendation|Pre-print|N/A|
|PARSE-Ego4D: Toward Bidirectionally Aligned Action Recommendations for Egocentric Videos|Pre-print|N/A|
|SS4Rec: Continuous-Time Sequential Recommendation with State Space Models|Pre-print|N/A|
|Ssd4rec: a structured state space duality model for efficient sequential recommendation|Pre-print|N/A|
|TTT4Rec: A Test-Time Training Approach for Rapid Adaption in Sequential Recommendation|Pre-print|N/A|
|TiM4Rec: An Efficient Sequential Recommendation Model Based on Time-Aware Structured State Space Duality Model|Pre-print|N/A|
|Uncovering Selective State Space Model's Capabilities in Lifelong Sequential Recommendation|Pre-print|N/A|


# Data collection workflow
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

<b>Search A</b> : 21 concrete method papers concerning mamba application in recommender systems were found in top 300 articles. Among those articles, 11 papers were accepted to significant journals and conferences.

<b>Search B</b> : 33 concrete method AI/ML research papers concerning mamba application in recommender systems were found in top 100 articles. Among those articles, 21 papers were accepted to significant journals and conferences.

Finally, paper lists from <b>Search A</b> and <b>Search B</b> are merged. After removing duplicate rows, a total of 38 papers featured concrete methods of mamba application in recommender systems. Among those 38, 22 papers were accepted to recognized journals and conferences.
