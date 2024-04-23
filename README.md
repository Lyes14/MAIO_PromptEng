# MAIO Prompt Engineering Task - Group 2
This directory documents the methodological approach and the results obtained for the prompt engineering task of the group work for the course Management of AI in Organizations.
There are three distinct sections. The first section pertains to the data used, the second deals with the construction of our prompt, and the last addresses the analysis of our results. For each of these parts, you will find a folder in the repository containing the code, prompts, analyses, etc.

----
## Données:


Based on the notebook provided in the Kaggle project data, we made a strategic decision to focus exclusively on tweets classified with negative sentiment using the same method as in the Kaggle data notebook with vaderSentiment. This approach aligns with our research question, which concerns the public's concerns regarding large language models (LLMs), making it pertinent to concentrate solely on negatively sentimented tweets.

After selecting the relevant tweets, we proceeded with data cleaning by removing entries with empty features and retaining only the columns necessary for our analysis. This process resulted in a refined dataset comprising 26,237 rows and 7 columns.

For our prompt engineering task, we consulted resources on the maximum context window size that GPT Turbo 0125 can handle, which is 16,000 tokens. To comply with this limitation, we opted to sample our dataset down to only 200 lines. Although this reduction may seem substantial, it was necessary because maintaining most of the original features in the dataset substantially increases the token count. Consequently, we managed to reduce the number of tokens in our combined request (data + final prompt) to just under 14,000 tokens, leaving a buffer of approximately 2,000 tokens for GPT's response.

Please refer to the Data folder to access our "sample_data.csv" file, the original "tweets.csv" dataset, and the "data_processing.ipynb" notebook for detailed information on our data preparation process.


Prompt:
La construction de notre prompt s'est déroulée en plusieurs étapes. Au départ, nous avons fais quelques essais sans balises et sans persona, simplement en donnant le contexte et les instructions à GPT. Les résultats n'étaient pas très satisfaisants, notamment en termes de structure pusique les réponses étaient assez courtes et peu détaillées (Version 1). Par la suite, grâce aux précieux conseils donnés par Henri Jamet, nous avons affiné notre prompt en incluant des balises et en améliorant le détail de nos instructions. Les résultats ont été alors plus satisfaisants, notamment en terme de contenu, cependant, le problème lié au format était encore là (Version 2). Pour y remédier, nous avons inclus des exemples et un balise format à la fin, obligeant GPT à écrire en Markdown et à respecter un une certaine longueur dans sa réponse (Version 3). Pour documenter ce processus itératif, nous avons décidé de montrer les 3 versions ainsi qu'un exemple de réponse pour chacune dans le répértoire prompt. Veuillez trouver dans le dossier Prompt les 3 versions différentes du prompt accompagnées d'un  


Analysis:
La partie la plus intéressante de notre travail est celle de l'analyse de nos résultats. Notre méthodologie à été la suivante: nous avons itéré 15 fois la requète à GPT avec le prompt final (Version 3), le but était ensuite de pouvoir analyser les réponses les plus récurrentes que GPT nous donnait et c'est ces dernières que nous allons garder comme résultats. Ainsi en suivant cette approche nous espérons pouvoir mitigate l'existence d'un biais potentiel. Ainsi, pour chacune des réponses aux instructions (sept instructions au total) nous avons compté le nombre d'occurence de réponses similaires. Par exemple, si GPT affirme douze fois sur quinze que la Data Privacy est un des concerns les plus souvent exprimé dans les tweets, nous allions tirer la conclusion que ce concern est bel est bien exprimé dans les tweets. Nous avons conscience que le nombre très limité de tweets de notre dataset pose problème pour pouvoir conclure sur nos résultats et généraliser, cependant on croit que cette analyse est tout de même pertinente afin d'avoir un insight si cela vaudrait la peine de conduire une analyse plus poussée dans la même direction.

