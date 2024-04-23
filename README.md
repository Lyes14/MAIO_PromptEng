# MAIO Prompt Engineering Task - Group 2
This directory documents the methodological approach and the results obtained for the prompt engineering task of the group work for the course Management of AI in Organizations.
There are three distinct sections. The first section pertains to the data used, the second deals with the construction of our prompt, and the last addresses the analysis of our results. For each of these parts, you will find a folder in the repository containing the code, prompts, analyses, etc.

----
Données: 
En se basant sur le notebook fourni en donnée du projet sur kaggle, nous avons premièrement fais le choix de ne garder que les tweets ayant été classifé avec un sentiment négatif. Pour se faire, nous avons utilisé l'exacte même méthode que dans le notebook de donnée sur Kaggle avec vaderSentiment. En effet, étant donné que notre question de recherche concerne les préoccupation du public vis-à-vis des LLM, il nous a semblé pertinent de traiter ainsi uniquement les tweet à sentiment negatif. Suite à cela, nous avons procédé au nettoyage de nos données en supprimant les entrées avec des features vide et également en ne gardant que les colonnes qui nous intéressent pour notre analyse. Ainsi, en suivant ce plan, nous nous sommes retrouvés avec un dataset de 26237 lignes et 7 colonnes. Pour procéder à notre tâche de prompt engineering, nous nous sommes documenté sur la taille maximal du contexte (context window) qu'est capable d'avoir en request+repsonse de gpt turbo 0125 est de 16k token. Ainsi, pour respecter cette limite, nous avons décidé d'échantilloner notre dataset à 200 lignes seulement. Cela peu paraitre peu mais nous avons été contraint de faire ce choix étant donné que pour répondre à notre quesiton de recherche, nous avions besoin de garder la plupart des features présents initialement dans le dataset ce qui augmente considérablement le nombre de tokens. Ce faisant nous avons pu réduire le nombre de token de notre requête (data + prompt final) a un peu moins de 14'000 tokens, ce qui laisse un marge de 2'000 token estimée suffisante pour la réponse de GPT. (Veuillez ouvrir le dossier Data pour trouver notre fichier csv "sample_data.csv", le dataset de base "tweets.csv" et le notebook pour la préparation de nos données "data_processing.ipynb")


Prompt:
La construction de notre prompt s'est déroulée en plusieurs étapes. Au départ, nous avons fais quelques essais sans balises et sans persona, simplement en donnant le contexte et les instructions à GPT. Les résultats n'étaient pas très satisfaisants, notamment en termes de structure pusique les réponses étaient assez courtes et peu détaillées (Version 1). Par la suite, grâce aux précieux conseils donnés par Henri Jamet, nous avons affiné notre prompt en incluant des balises et en améliorant le détail de nos instructions. Les résultats ont été alors plus satisfaisants, notamment en terme de contenu, cependant, le problème lié au format était encore là (Version 2). Pour y remédier, nous avons inclus des exemples et un balise format à la fin, obligeant GPT à écrire en Markdown et à respecter un une certaine longueur dans sa réponse (Version 3). Pour documenter ce processus itératif, nous avons décidé de montrer les 3 versions ainsi qu'un exemple de réponse pour chacune dans le répértoire prompt. Veuillez trouver dans le dossier Prompt les 3 versions différentes du prompt accompagnées d'un  


Analysis:
La partie la plus intéressante de notre travail est celle de l'analyse de nos résultats. Notre méthodologie à été la suivante: nous avons itéré 15 fois la requète à GPT avec le prompt final (Version 3), le but était ensuite de pouvoir analyser les réponses les plus récurrentes que GPT nous donnait et c'est ces dernières que nous allons garder comme résultats. Ainsi en suivant cette approche nous espérons pouvoir mitigate l'existence d'un biais potentiel. Ainsi, pour chacune des réponses aux instructions (sept instructions au total) nous avons compté le nombre d'occurence de réponses similaires. Par exemple, si GPT affirme douze fois sur quinze que la Data Privacy est un des concerns les plus souvent exprimé dans les tweets, nous allions tirer la conclusion que ce concern est bel est bien exprimé dans les tweets. Nous avons conscience que le nombre très limité de tweets de notre dataset pose problème pour pouvoir conclure sur nos résultats et généraliser, cependant on croit que cette analyse est tout de même pertinente afin d'avoir un insight si cela vaudrait la peine de conduire une analyse plus poussée dans la même direction.

