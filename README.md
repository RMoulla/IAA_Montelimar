# Formation IAA — GCATRANS, Montélimar

**L’IAG pour chefs de projets, analystes, développeurs et architectes SI**

**1er et 2 octobre 2026 · Redha Moulla**

Vous trouverez ici le support de cours, les exercices de la session et les ressources pour poursuivre vos essais. Les TP RAG et Agents sont inclus dans ce dépôt et peuvent être exécutés dans Google Colab.

## Accès rapide

| Ressource | Accès |
| --- | --- |
| Support de cours de Montélimar | [Ouvrir le PDF](IAA_GCATRANS_Montelimar.pdf) |
| Infographie : les principaux concepts des LLM | [Ouvrir le PDF](principaux_concepts_des_llm.pdf) |
| TP Prompting : rédaction, extraction et analyse de données | [Lire les exercices](TP_Prompting.ipynb) · [Ouvrir dans Colab](https://colab.research.google.com/github/RMoulla/IAA_Montelimar/blob/main/TP_Prompting.ipynb) |
| Données pour l’exercice d’analyse immobilière | [selogerdata.csv](selogerdata.csv) |
| Skill : passer d’un besoin aux spécifications | [SKILL.md](SKILL.md) |
| Workflow n8n : évaluer la qualité d’une user story | [US_Quality_IAA.json](US_Quality_IAA.json) |
| TP RAG : comprendre chaque étape | [Lire le notebook](TP_RAG_Github.ipynb) · [Ouvrir dans Colab](https://colab.research.google.com/github/RMoulla/IAA_Montelimar/blob/main/TP_RAG_Github.ipynb) |
| TP RAG avec interface Gradio : interroger des documents PDF | [Ouvrir dans Colab](https://colab.research.google.com/github/RMoulla/IAA_Montelimar/blob/main/RAG_Gradio.ipynb) |
| TP Agents : assistant e-commerce avec MCP | [Ouvrir dans Colab](https://colab.research.google.com/github/RMoulla/IAA_Montelimar/blob/main/Copie_de_TP_Agent_LLM.ipynb) |
| Catalogue utilisé par le TP Agents | [products.csv](products.csv) |

## 1. Télécharger les supports et les données

1. Cliquez sur le fichier souhaité dans le tableau ci-dessus.
2. Sur sa page GitHub, cliquez sur **Download raw file**, l’icône de téléchargement située au-dessus du fichier. Pour certains fichiers texte, le bouton **Raw** affiche le contenu brut, que vous pouvez enregistrer.
3. Conservez l’extension et le nom du fichier, notamment `products.csv` et `selogerdata.csv`.

Le cours peut aussi être [ouvert directement en PDF](https://raw.githubusercontent.com/RMoulla/IAA_Montelimar/main/IAA_GCATRANS_Montelimar.pdf), puis enregistré avec le bouton de téléchargement du navigateur. Si GitHub n’affiche pas l’aperçu, le téléchargement reste possible.

## 2. Refaire les exercices de la session

### Prompting et analyse de données

Le [TP Prompting](TP_Prompting.ipynb) contient quatre exercices : rédiger un post LinkedIn, comparer l’effet du ton d’un prompt, extraire des informations en JSON et analyser un jeu de données.

Ce notebook contient des **consignes à lire et à copier dans votre assistant IA** : il n’y a pas de code à exécuter ni de clé API à configurer pour ce TP. Vous pouvez le lire directement dans GitHub ou dans Colab.

Pour l’exercice d’analyse, téléchargez [selogerdata.csv](selogerdata.csv), joignez-le à la conversation dans un assistant capable d’analyser des fichiers, puis copiez le prompt de l’exercice 4.

### Du besoin aux spécifications avec un Skill

Le fichier [SKILL.md](SKILL.md) décrit un entretien de cinq questions maximum pour préciser un besoin et produire une spécification avec des critères d’acceptation. Utilisez-le dans un outil prenant en charge les Skills, ou joignez son contenu à la conversation avec votre assistant en lui demandant d’appliquer cette méthode.

### Audit de user stories avec n8n

Le fichier [US_Quality_IAA.json](US_Quality_IAA.json) est un workflow n8n à importer. Il reçoit une user story dans un formulaire, l’évalue avec un LLM et affiche un diagnostic selon cinq critères : persona, format, description, critères d’acceptation et granularité.

1. Téléchargez le fichier JSON, puis importez-le dans votre espace n8n.
2. Dans le nœud **Appel API LLM**, sélectionnez vos propres identifiants OpenAI. La référence aux identifiants du formateur ne configure pas votre compte.
3. Lancez une exécution de test et ouvrez le formulaire du nœud **Formulaire US**.
4. Saisissez le titre et la description d’une user story, puis consultez le score et les suggestions.

Ce workflow utilise `gpt-4o-mini` via l’API OpenAI : une clé API active et un quota disponible sont nécessaires. La note produite sert de point de départ à une revue humaine.

## 3. Préparer Google Colab pour les TP RAG et Agents

Un *notebook* (`.ipynb`) alterne explications et cellules de code. **GitHub permet de le consulter ; Colab permet de l’exécuter sans installer Python sur votre ordinateur.**

1. Connectez-vous à votre compte Google et ouvrez le lien Colab du TP choisi.
2. Sélectionnez **Fichier → Enregistrer une copie dans Drive** pour conserver votre travail.
3. Cliquez sur **Se connecter** et gardez un environnement **Python 3 avec CPU** : aucun GPU n’est nécessaire pour ces exemples.
4. Ouvrez **Secrets**, l’icône en forme de clé dans la barre latérale de Colab.
5. Ajoutez un secret nommé exactement `OPENAI_API_KEY`, renseignez votre clé et activez **Accès au notebook** pour votre copie.
6. Exécutez les cellules **de haut en bas**, une à une, avec le bouton ▶ ou **Maj + Entrée**.

Les deux TP utilisent `gpt-4o` via l’API OpenAI. Il faut une clé valide, l’accès au modèle et un quota disponible ; les appels API peuvent être facturés. Un abonnement ChatGPT ne fournit pas à lui seul cet accès API. Vous pouvez gérer votre clé sur la [page des clés API](https://platform.openai.com/api-keys). Gardez-la dans les secrets Colab, sans l’inscrire dans une cellule ou dans GitHub.

## 4. Faire tourner les TP RAG

### RAG étape par étape : `TP_RAG_Github.ipynb`

[**Ouvrir le TP RAG étape par étape dans Colab**](https://colab.research.google.com/github/RMoulla/IAA_Montelimar/blob/main/TP_RAG_Github.ipynb)

Ce TP présente successivement l’extraction du texte d’un PDF, sa segmentation, le calcul des embeddings, la recherche des passages similaires et la génération d’une réponse avec `gpt-4o`.

1. Téléchargez le [support de Montélimar](IAA_GCATRANS_Montelimar.pdf), puis importez-le dans les fichiers de votre session Colab en conservant son nom.
2. Configurez le secret `OPENAI_API_KEY` comme indiqué à la section 3.
3. Exécutez toutes les cellules dans l’ordre : extraction, embeddings et recherche, puis génération de la réponse.
4. Modifiez la variable `query` pour poser une autre question, puis relancez les cellules de recherche et de génération.

Utilisez une session Colab dédiée à ce notebook : il conserve la version `openai==0.28` du TP d’origine. Les étapes d’extraction et de recherche fonctionnent sans clé OpenAI ; la dernière étape l’utilise pour générer la réponse.

### RAG avec interface Gradio

[**Ouvrir le TP RAG dans Colab**](https://colab.research.google.com/github/RMoulla/IAA_Montelimar/blob/main/RAG_Gradio.ipynb)

**Objectif :** poser des questions sur un PDF. Le programme recherche les passages pertinents dans le document et les transmet au modèle pour construire sa réponse.

1. Téléchargez le [support de cours de Montélimar](IAA_GCATRANS_Montelimar.pdf).
2. Dans votre copie Colab, exécutez la cellule d’installation, puis celle sous **Setup OpenAI API Key**.
3. Ouvrez **Fichiers** dans la barre latérale, puis **Importer**, et sélectionnez le PDF. Attendez qu’il apparaisse dans `/content/`.
4. Exécutez **1. Load and Process PDFs**. Le message `Loaded … raw PDF pages and split into … chunks` doit afficher des valeurs supérieures à zéro.
5. Exécutez **2. Create Embeddings and Vector Store**, puis **3. RAG Function**, puis **4. Gradio Interface**.
6. Dans l’interface affichée, posez par exemple : « Comment le cours explique-t-il le fonctionnement du RAG ? »

**Ouvrir le notebook depuis GitHub n’importe pas automatiquement le PDF.** Utilisez un document dont le texte est sélectionnable : ce TP ne fait pas de reconnaissance de texte sur les scans.

La dernière cellule reste active pour maintenir l’interface ouverte. Si vous ajoutez un autre PDF, arrêtez cette cellule, puis relancez les sections 1 à 4. Comparez les réponses avec le cours. Les passages sélectionnés et votre question sont transmis à l’API OpenAI.

## 5. Faire tourner le TP Agents

[**Ouvrir le TP Agents dans Colab**](https://colab.research.google.com/github/RMoulla/IAA_Montelimar/blob/main/Copie_de_TP_Agent_LLM.ipynb)

**Objectif :** construire Buddy, un assistant qui recherche des produits, les ajoute à un panier et consulte ce panier grâce aux outils fournis par un serveur MCP.

Téléchargez d’abord [products.csv](products.csv). Dans votre copie Colab, exécutez les sections dans l’ordre :

| Section | Action ou résultat attendu |
| --- | --- |
| 1. Installation des bibliothèques | Attendre la fin ; redémarrer la session si Colab le demande. |
| 2. Chargement des données et création de la base SQLite | Choisir `products.csv` lorsque le sélecteur apparaît. Le TP utilise les 1 000 premiers produits. |
| 3. Vectorisation des titres et indexation avec FAISS | Attendre le message `Index prêt : 1000 produits.` |
| 4. Création du serveur MCP | Exécuter la cellule qui crée `server.py`. |
| 5. Connexion au serveur et découverte des outils | Vérifier l’affichage de `search_products`, `add_to_cart` et `view_cart`. |
| 6. Configuration de l’agent | Attendre `Agent prêt.` ; une saisie masquée de la clé est proposée si le secret n’est pas accessible. |
| 7. Conversation avec l’agent | Exécuter la fonction de conversation, puis la dernière cellule pour saisir une demande. |

Essayez successivement, en réexécutant **uniquement la dernière cellule** entre chaque demande :

- « Je cherche un pantalon de sport noir pour homme. »
- « Ajoute deux exemplaires du premier produit au panier. »
- « Montre-moi mon panier. »

Les lignes **[Appel MCP]**, **[Résultat]** et **Buddy :** montrent les étapes de l’interaction. Le panier est une simulation. Réexécuter la section 2 vide le panier ; réexécuter la section 6 réinitialise la mémoire de conversation.

## 6. En cas de difficulté

| Problème | Que faire ? |
| --- | --- |
| Secret introuvable ou accès refusé | Vérifier `OPENAI_API_KEY` et activer l’accès au notebook dans la copie utilisée. |
| Erreur d’authentification ou de quota | Vérifier la clé, le quota API et l’accès au modèle indiqué dans le notebook. |
| Le RAG affiche zéro page ou zéro passage | Importer le PDF dans `/content/`, puis reprendre le chargement et l’indexation. |
| `products.csv` est introuvable | Réimporter le fichier avec son nom exact, sans suffixe `(1)` ni extension `.txt`. |
| Variable inconnue ou erreur d’import | Reprendre les cellules dans l’ordre à partir de la première erreur ; redémarrer la session si l’installation le demande. |
| Le lien Gradio ne fonctionne plus | Relancer le TP et utiliser le nouveau lien produit par votre exécution. |

Votre copie du notebook reste dans Drive, mais les fichiers importés et les bibliothèques installées dépendent de la session temporaire Colab. Après une réinitialisation, réimportez les fichiers et réexécutez les cellules.

Pour toute question : **redha.moulla@axia-conseil.com**.

Pour poursuivre la veille en IA : [Courants de fond](https://redhamoulla.substack.com).
