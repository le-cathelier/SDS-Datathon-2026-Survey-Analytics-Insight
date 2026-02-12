Readme

1\. Environment Setup

To run this notebook and reproduce the results, you will need to set up a Python environment with the following libraries:

\*   \`pandas\`  
\*   \`numpy\`  
\*   \`seaborn\`  
\*   \`matplotlib\`  
\*   \`scikit-learn\` (sklearn)  
\*   \`sentence-transformers\`  
\*   \`transformers\`  
\*   \`scipy\`

\`\`\`

2\. How to Run Notebook

1\. Load Data: 

- The notebook starts by loading the \`sds\_datathon\_gradsingapore.xlsx\` dataset into a pandas DataFrame named \`grad\`.

2\.  Data Cleaning/Preparation: 

- Unused columns are dropped, duplicate rows are removed, and column names are standardized for easier access. A \`time\_taken\` column is calculated.

3\.  Exploratory Data Analysis (EDA):

- Proportions and counts of 'Complete', 'Disqualified', and 'Partial' survey statuses are calculated and displayed.  
- Descriptive statistics and a box plot visualize the time taken to complete the survey across different statuses.  
- Numerical and categorical summaries (describe, value\_counts) are generated for the cleaned dataset.  
- Bar plots show the distribution of survey statuses across various categorical variables like \`country\`, \`year\_of\_Study\`, \`highest\_qualification\`, \`major\`, \`gender\`, and \`perception\`.  
- Analysis of \`perception\` vs. \`scale(1-10)\` (attractiveness rating) is performed, including statistical tests (Kruskal-Wallis H-test) and visualizations (barplot, violin plot).  
- Cramér's V is used for pairwise categorical associations, and Mutual Information (MI) scores are calculated to understand feature importance relative to the \`status\` column.

4\.  Similarity Analysis using NLP:

- Survey questions are transformed into numerical embeddings using a \`SentenceTransformer\` model.  
- A similarity matrix is computed using cosine similarity to identify redundant questions based on a threshold.  
- Questions are clustered into themes using K-Means clustering, and the identified themes are presented.

5\.  Demographic and Behavioural Segmentation: 

- Demographic and behavioural features are extracted based on the NLP analysis.  
- K-means clustering algorithm is applied to segment respondents based on demographic and behavioural features separately.

Simply run all cells in the notebook sequentially to reproduce the analysis and results.

3\. Specific Instructions for Executing the Model

This notebook primarily focuses on exploratory data analysis, feature engineering (time taken), statistical analysis (Kruskal-Wallis, Cramér's V, Mutual Information), and Natural Language Processing (NLP) for survey question analysis (similarity and clustering). It does not include a traditional predictive machine learning model that requires explicit 'execution' beyond running the cells. The NLP parts use pre-trained \`sentence-transformers\` and \`transformers\` models, which are loaded automatically upon cell execution.

4\. Key Insights and Findings

General survey engagement:

- Approximately 70.7% of survey responses were completed, 17.8% disqualified, and 11.5% partial.  
- Complete surveys generally took longer (average of 4 hours, though with a wide range suggesting outliers) compared to partial (average 27 minutes) or disqualified (average 2 hours) surveys.

Factors influencing attractiveness:

- There is a statistically significant difference in attractiveness ratings across different perception categories (p-value \< 0.001). Respondents who are already familiar with the organization and consider it a potential employer give consistently higher attractiveness ratings.  
- People who are more familiar or have a positive impression of the organization tend to rate its attractiveness higher. Conversely, those unfamiliar tend to give lower or more varied ratings.  
- Mutual Information analysis indicates that survey completion status is more strongly correlated with engagement signals like the attractiveness rating (\`scale(1-10)\`) and \`time\_taken\` rather than demographic variables. The presence of a \`scale(1-10)\` value is a strong indicator of a complete survey.

Survey question structure (NLP Analysis):

- Several survey questions are highly similar (e.g., questions asking about 'types of roles', 'career progression', 'compensation', 'interview process', and 'other' write-in options were found to be redundant with each other). This suggests that some questions might be measuring very similar constructs.  
- The survey questions cluster into four distinct themes:

    1\.  General demography: Questions related to \`nationality\` and \`gender\`.  
    2\.  Applicant's expectation on employer: Questions about \`perception\`, \`types\_of\_roles\`, \`career\_progression\`, \`compensation\`, \`worklife\_balance\`, \`interview\_process\`, and \`other\` expectations.  
    3\.  Education status of applicant: Questions concerning \`university\`, \`year\_of\_Study\`, \`highest\_qualification\`, and \`major\`.  
    4\.  Employer attractiveness: Questions related to \`scale(1-10)\` rating, \`motivation\_factor\`, and \`other\` motivating factors.

Demographic and Behaviour Segmentation:

- Cluster analysis reveals missing demographic data (Cluster 0, Yale-NUS), distinct institutional and major-specific patterns (Clusters 1–2, NTU/NUS), and underrepresented groups (international students). Future surveys should ensure inclusive demographics, tailor questions by institution/discipline, and expand outreach for broader, more representative insights.  
- Behavioral segmentation indicates tailored strategies: Clusters 0 and 2 need targeted messaging to build awareness and clarify employer value, Cluster 3 benefits from reinforcing motivations, and Cluster 1’s size suggests survey design improvements. Insights from engaged respondents in Cluster 3 can guide broader recruitment and branding efforts.

