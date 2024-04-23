# :computer: MAIO Prompt Engineering Task - Group 2
This directory documents the methodological approach and the results obtained for the prompt engineering task of the group work for the course Management of AI in Organizations.
There are three distinct sections. The first section pertains to the data used, the second deals with the construction of our prompt, and the last addresses the analysis of our results. For each of these parts, you will find a folder in the repository containing the code, prompts, analyses, etc.

----
## :floppy_disk: Data


Based on the notebook provided in the Kaggle project data, we made a strategic decision to focus exclusively on tweets classified with negative sentiment using the same method as in the Kaggle data notebook with vaderSentiment. This approach aligns with our research question, which concerns the public's concerns regarding large language models (LLMs), making it pertinent to concentrate solely on negatively sentimented tweets.

After selecting the relevant tweets, we proceeded with data cleaning by removing entries with empty features and retaining only the columns necessary for our analysis. This process resulted in a refined dataset comprising 26,237 rows and 7 columns.

For our prompt engineering task, we consulted resources on the maximum context window size that GPT Turbo 0125 can handle, which is 16,000 tokens. To comply with this limitation, we opted to sample our dataset down to only 200 lines. Although this reduction may seem substantial, it was necessary because maintaining most of the original features in the dataset substantially increases the token count. Consequently, we managed to reduce the number of tokens in our combined request (data + final prompt) to just under 14,000 tokens, leaving a buffer of approximately 2,000 tokens for GPT's response.

Please refer to the Data folder to access our "sample_data.csv" file, the original "tweets.zip" dataset, and the "data_processing.ipynb" notebook for detailed information on our data preparation process.


## :clipboard: Prompt
The development of our prompt unfolded in several stages. Initially, we conducted trials without tags or a persona, simply providing GPT with the context and instructions. The outcomes were not very satisfying, particularly in terms of structure, as the responses were quite short and lacked detail (Version 1). Following valuable advice from Henri Jamet, we refined our prompt by incorporating tags and enhancing the detail of our instructions. The results then improved, especially in terms of content, though issues related to the format persisted (Version 2). To address this, we added examples and a format tag at the end, compelling GPT to write in Markdown and maintain a certain length in its response (Version 3).

To document this iterative process, we decided to display all three versions along with an example response for each in the prompt directory. Please refer to the Prompt folder to find the three different versions of the prompt ("version1.txt", "version2.txt", "version3.txt"), each accompanied by an example of the results.


## :bar_chart: Analysis
The most interesting part of our project is the analysis of our results. Our methodology was as follows: we iterated the query to GPT with the final prompt (Version 3) fifteen times. The aim was then to analyze the most recurrent responses provided by GPT, and these are the ones we decided to keep as our results. By following this approach, we hope to mitigate the existence of potential bias. For each of the responses to the instructions (seven instructions in total), we counted the number of occurrences of similar responses. For example, if GPT asserted twelve times out of fifteen that Data Privacy is one of the most frequently expressed concerns in tweets, we would conclude that this concern is indeed expressed in the tweets. We acknowledge that the very limited number of tweets in our dataset poses a problem for conclusively generalizing our results; however, we believe this analysis is still relevant to gain insight into whether it would be worthwhile to conduct a more thorough analysis in the same direction. Please refer to the Analysis folder to find the analysis notebook "analysis.ipynb".

Further improvements could be to extract multiple times a sample dataset with the data_processing.ipynb notebook with no random_state parameter at the moment of the sampling. Then the idea would be to conduct the same analysis that in the analysis.ipynb notebook but with different instances of sample_data.csv. This approach could help us to mitigate the biases. For doing this implement automation for the analysis part with NLP libraries would be mandatory as the number of iterations we would have to analyze would be greater.

