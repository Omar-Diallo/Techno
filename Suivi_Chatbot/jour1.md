<!--
  Fichier : Jour1_Chatbots_IA_Notions_fondamentales.md
  Cours   : Chatbots et assistants IA — notions fondamentales
  Durée   : 60 à 90 minutes
-->

# 🤖 Chatbots et assistants IA — Jour 1

> **Thème :** comprendre chatbot, assistant IA, LLM, prompt, contexte et cas d’usage.
>
> **Objectif :** distinguer ces notions et savoir décrire simplement le fonctionnement d’un assistant conversationnel.

---

## 🎯 À la fin du cours, tu sauras

- différencier un chatbot classique et un assistant IA basé sur un LLM ;
- expliquer ce qu’est un LLM ;
- écrire un prompt plus précis ;
- comprendre ce qu’on appelle le contexte d’une conversation ;
- identifier un cas d’usage adapté.

## 1. Qu’est-ce qu’un chatbot ?

Un **chatbot** est un logiciel qui échange avec une personne sous forme de conversation, généralement par écrit. Il peut répondre à des questions, guider l’utilisateur ou exécuter certaines actions.

Un chatbot peut être très simple : il suit des règles écrites à l’avance, par exemple :

```text
Si l’utilisateur écrit « horaires » → afficher les horaires.
Si l’utilisateur écrit « contact » → afficher le numéro de téléphone.
```

Ce type de chatbot est prévisible, mais il comprend mal les demandes qui ne correspondent pas à ses règles.

## 2. Qu’est-ce qu’un assistant IA ?

Un **assistant IA** est une application conçue pour aider l’utilisateur à accomplir une tâche : répondre, résumer, expliquer, rechercher dans des documents ou préparer du contenu.

Il peut utiliser un LLM, des instructions, des informations fournies pendant la conversation et, selon sa configuration, des outils ou une base documentaire. Le terme « assistant » décrit donc le rôle de l’application ; il ne désigne pas forcément un modèle particulier.

### Chatbot classique et assistant IA

| Chatbot à règles | Assistant IA basé sur un LLM |
|---|---|
| Suit des scénarios ou règles prédéfinis | Génère des réponses à partir d’instructions et du contexte |
| Répond bien aux demandes prévues | Peut traiter des formulations variées |
| Peut échouer hors de son arbre de règles | Peut produire une réponse incorrecte ou inventée |
| Utile pour un menu ou une FAQ courte | Utile pour expliquer, résumer ou dialoguer de manière souple |

Un assistant IA n’est pas automatiquement exact : il faut vérifier ses réponses, surtout pour les sujets importants.

## 3. Qu’est-ce qu’un LLM ?

Un **LLM** (*Large Language Model*, ou grand modèle de langage) est un modèle entraîné sur une grande quantité de données textuelles. Il peut notamment générer du texte, répondre à des questions, résumer ou traduire. [web:320]

Pour répondre, un LLM produit du texte en fonction de l’entrée qu’il reçoit et de son entraînement. Il ne consulte pas forcément Internet et ne connaît pas automatiquement les informations privées d’une entreprise.

> **À retenir :** chatbot = interface conversationnelle ; assistant IA = application d’aide ; LLM = modèle de langage pouvant alimenter cette application.

## 4. Qu’est-ce qu’un prompt ?

Un **prompt** est la demande ou l’ensemble d’instructions transmis au modèle. La précision du prompt influence souvent la forme et l’utilité de la réponse. [web:310][web:321]

### Prompt vague

```text
Parle-moi des déchets.
```

La demande ne précise ni le public, ni l’objectif, ni la longueur ou le format.

### Prompt plus utile

```text
Tu es un assistant pédagogique.
Explique à un étudiant débutant la différence entre déchets recyclables et non recyclables.
Réponds en français simple, en 5 points maximum, puis donne 2 exemples à Genève.
Si une information locale n’est pas certaine, indique-le clairement.
```

Un prompt efficace précise souvent :

- **le rôle** : qui doit répondre ?
- **la tâche** : que doit faire le modèle ?
- **le contexte** : quelles informations doit-il utiliser ?
- **les contraintes** : longueur, ton, langue, limites ;
- **le format attendu** : liste, tableau, étapes ou paragraphe.

OpenAI recommande notamment de donner des instructions claires et de séparer les consignes du contexte fourni. [web:309][web:321]

## 5. Qu’est-ce que le contexte ?

Le **contexte** est l’information disponible au modèle au moment où il génère sa réponse. Cela peut inclure la demande actuelle, des messages précédents, des instructions et des documents ajoutés à la conversation.

Les modèles ont une limite de contexte, souvent appelée **fenêtre de contexte**. Elle correspond à la quantité d’information que le modèle peut traiter pour une génération donnée. [web:309][web:319]

### Exemple

Tu demandes :

```text
Je prépare un entretien pour un poste de data analyst.
Explique-moi SQL avec un exemple simple.
```

Si tu ajoutes ensuite :

```text
Explique maintenant les jointures avec le même exemple.
```

L’assistant peut utiliser le contexte précédent si l’historique lui est toujours transmis. Mais une application doit gérer cet historique : le modèle ne se souvient pas nécessairement de toutes les conversations passées.

## 6. Cas d’usage d’un assistant IA

| Cas d’usage | Ce que l’assistant peut faire | Précaution |
|---|---|---|
| FAQ d’une école | Répondre à partir d’informations validées | Indiquer quand il ne trouve pas la réponse |
| Support client | Expliquer les étapes de résolution d’un problème | Transférer les cas complexes à une personne |
| Assistant documentaire | Résumer des documents et retrouver des passages | Respecter les droits d’accès et la confidentialité |
| Tuteur d’apprentissage | Expliquer une notion et proposer des exercices | Vérifier les corrections et les sources importantes |
| Assistant administratif | Aider à comprendre ou classer des informations | Ne pas lui confier une décision critique sans contrôle |

Un bon cas d’usage répond à un besoin précis, dispose d’informations fiables et prévoit quoi faire lorsque l’assistant ne sait pas répondre.

## 7. Mini-scénario : assistant de cours

Imaginons un assistant qui aide les étudiants à réviser SQL :

1. L’étudiant pose une question.
2. L’application transmet les instructions et la question au LLM.
3. Le modèle reçoit aussi un contexte utile, par exemple le niveau de l’étudiant ou un extrait du cours.
4. Le modèle génère une réponse.
5. L’application affiche la réponse et peut demander à l’étudiant s’il souhaite un exercice.

```text
Utilisateur → prompt + contexte → LLM → réponse → interface du chatbot
```

Plus tard, tu apprendras à connecter le chatbot à des documents (RAG), à des outils et à une interface web.

## 8. Limites et bonnes pratiques

- Un LLM peut produire une réponse fluide mais fausse ; vérifie les faits importants.
- Une consigne vague entraîne souvent une réponse trop générale.
- Le modèle n’a que le contexte qui lui est fourni et qui tient dans sa fenêtre de contexte.
- Ne colle pas de données personnelles, confidentielles ou secrets d’API dans un service sans vérifier ses règles.
- Pour un cas d’usage important, définis les limites de l’assistant et prévois une vérification humaine.

## ✍️ Exercices

### Exercice 1 — améliorer le prompt

Améliore ce prompt :

```text
Aide-moi pour mon CV.
```

**Mon prompt amélioré :**

> À compléter : indique le rôle, le contexte, la tâche, le format et les contraintes.

### Exercice 2 — choisir un cas d’usage

Choisis un cas d’usage d’assistant IA :

- **Utilisateur cible :** ______________________________________
- **Problème à résoudre :** ___________________________________
- **Informations nécessaires :** _______________________________
- **Que doit faire l’assistant s’il ne sait pas ?** _______________

### Corrigé indicatif

<details>
<summary>Afficher un exemple</summary>

« Tu es un conseiller de rédaction de CV pour un étudiant en informatique. À partir du CV que je colle ci-dessous, propose une version plus claire pour un stage de data analyst à Genève. N’invente aucune expérience, garde une page et liste les changements effectués. »

</details>

## ✅ Vérification de compréhension

- [ ] Je peux expliquer la différence entre chatbot, assistant IA et LLM.
- [ ] Je peux identifier le rôle d’un prompt.
- [ ] Je peux expliquer simplement le contexte d’une conversation.
- [ ] Je sais qu’un assistant IA peut se tromper.
- [ ] Je peux proposer un cas d’usage précis et une précaution associée.

## 📝 Mon bilan

**Ce que j’ai retenu :** _________________________________________  
**Mon cas d’usage :** ____________________________________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources fiables

- [Google Cloud — Grands modèles de langage (LLM)](https://cloud.google.com/ai/llms?hl=fr)
- [OpenAI — Prompting](https://developers.openai.com/api/docs/guides/prompting)
- [OpenAI — Ingénierie de prompts](https://developers.openai.com/api/docs/guides/prompt-engineering)
- [OpenAI — Bonnes pratiques de prompting en français](https://help.openai.com/fr-fr/articles/6654000-bonnes-pratiques-pour-ling%C3%A9nierie-de-prompts-avec-lapi-openai)

> **À retenir en une phrase :** un assistant IA est une application conversationnelle qui peut utiliser un LLM ; le prompt lui donne la tâche, et le contexte lui fournit les informations utiles pour répondre. [web:309][web:310][web:320]
