<!--
  Fichier : Jour2_Chatbots_IA_Tokens_Contexte_Temperature.md
  Cours   : Chatbots et assistants IA — tokens, contexte, température et rôles
  Durée   : 60 à 90 minutes
-->

# 🤖 Chatbots et assistants IA — Jour 2

> **Thème :** comprendre les tokens, la fenêtre de contexte, la température, les instructions système et utilisateur.
>
> **Objectif :** comprendre comment un LLM reçoit une demande, quelles limites il a et comment régler le style de ses réponses.

---

## 🎯 À la fin du cours, tu sauras

- expliquer ce qu’est un token ;
- comprendre le rôle de la fenêtre de contexte ;
- choisir une température adaptée à une tâche ;
- distinguer les instructions système et utilisateur ;
- écrire un prompt plus précis.

## 1. Token : l’unité de texte du modèle

Un **token** est une petite unité de texte que le modèle lit et génère. Selon la langue et le modèle, un token peut correspondre à un mot, une partie de mot, un caractère ou une ponctuation.

Exemples possibles :

- `Bonjour` peut être découpé en un ou plusieurs tokens ;
- `apprentissage` peut être découpé en plusieurs parties ;
- un emoji, un chiffre ou un signe de ponctuation peut aussi correspondre à un token.

La documentation OpenAI indique que les modèles lisent et écrivent le texte par morceaux appelés tokens ; la taille exacte varie selon la langue et le modèle. [web:354]

> **Image mentale :** un token est une petite brique de texte. Le modèle ne lit pas forcément un mot complet : il lit et produit ces briques.

## 2. Fenêtre de contexte

La **fenêtre de contexte** est la quantité maximale d’informations, mesurée en tokens, que le modèle peut traiter dans une requête. Elle inclut généralement les entrées, la sortie générée et, pour certains modèles, les tokens de raisonnement. [web:355]

Si tu ajoutes trop de texte, de documents ou de messages, une partie peut être tronquée ou ne pas être prise en compte.

### Exemple simple

Tu demandes :

```text
Explique SQL à un débutant.
```

Puis tu ajoutes plusieurs pages de cours. Si le total dépasse la fenêtre de contexte du modèle, une partie des informations peut ne pas être utilisée.

> **À retenir :** une grande fenêtre de contexte permet de traiter davantage d’informations, mais elle ne garantit pas que le modèle comprendra ou utilisera correctement chaque détail.

## 3. Température : régler la variabilité

La **température** est un réglage qui influence le degré de variabilité des réponses. Une température plus élevée rend les réponses plus variées ; une température plus basse les rend plus concentrées et prévisibles. [web:352][web:361]

| Température | Effet général | Exemple d’usage |
|---|---|---|
| Basse, par exemple 0 | Réponses plus concentrées et prévisibles | Extraction de données, questions factuelles, réponses structurées |
| Moyenne | Équilibre entre précision et variation | Explication, reformulation, assistance générale |
| Élevée | Réponses plus variées et créatives | Brainstorming, idées de noms, rédaction créative |

La documentation OpenAI précise qu’une température élevée rend la sortie plus aléatoire, mais pas nécessairement plus juste ; pour des usages factuels, une température de 0 est souvent recommandée. [web:356]

> **Attention :** la température ne rend pas un modèle plus intelligent ni plus fiable. Elle influence surtout la variabilité des formulations.

## 4. Instructions système et utilisateur

Dans une conversation avec un LLM, les messages peuvent avoir différents rôles. Les rôles courants sont **système**, **utilisateur** et **assistant**. [web:361]

### Instructions système

Les **instructions système** définissent le comportement général de l’assistant : son rôle, ses limites, sa langue et son format de réponse. Elles sont traitées avant les messages utilisateur et aident à établir la personnalité, les contraintes et les préférences de sortie. [web:362]

Exemple :

```text
Tu es un assistant pédagogique pour étudiants en informatique.
Réponds uniquement en français simple.
Explique chaque notion avec un exemple court.
Si tu ne connais pas une information, dis-le clairement.
```

### Message utilisateur

Le **message utilisateur** est la demande concrète de la personne qui utilise l’assistant.

Exemple :

```text
Explique-moi la différence entre TCP et UDP avec un exemple simple.
```

### Réponse de l’assistant

La réponse est le texte généré par le modèle. Dans une application, elle est ensuite affichée dans l’interface du chatbot.

## 5. Exemple complet

```text
Instructions système :
Tu es un assistant pédagogique en français.
Réponds de façon simple, avec un exemple concret.
Ne donne pas de fausse information : indique quand tu n’es pas sûr.

Utilisateur :
Explique-moi les tokens et la fenêtre de contexte.

Assistant :
Les tokens sont les petites unités de texte que le modèle traite.
La fenêtre de contexte est la quantité maximale de tokens
que le modèle peut traiter dans une requête.
```

## 6. Tableau récapitulatif

| Notion | Rôle | Exemple |
|---|---|---|
| Token | Unité de texte lue ou produite par le modèle | Un mot, une partie de mot ou un caractère |
| Fenêtre de contexte | Quantité maximale de tokens traitables dans une requête | Question, historique, documents et réponse |
| Température | Degré de variabilité des réponses | 0 pour une réponse plus concentrée, valeur plus élevée pour plus de variété |
| Instructions système | Définissent le comportement général | « Réponds en français simple et cite tes limites » |
| Message utilisateur | Demande concrète de l’utilisateur | « Explique-moi les tokens » |
| Réponse assistant | Texte généré par le modèle | Explication ou réponse affichée dans le chat |

## 7. Bonnes pratiques

- Écris des instructions système claires et brèves.
- Précise la langue, le public, le ton et le format attendu.
- Ne confonds pas créativité et exactitude : une température élevée ne rend pas une réponse vraie.
- Vérifie les informations importantes, même si la réponse paraît fluide.
- Pour les données sensibles, évite de les coller dans un service sans connaître ses règles.
- Change un paramètre à la fois pour comprendre son effet sur la réponse. [web:356][web:361]

## ✍️ Exercices

### Exercice 1 — identifier les rôles

Pour cette conversation, indique le rôle de chaque message :

```text
Tu es un assistant qui aide à réviser SQL.
Explique-moi les jointures avec un exemple simple.
```

- Instruction système : ________________________________________
- Message utilisateur : _______________________________________

### Exercice 2 — choisir la température

Pour chaque tâche, propose une température adaptée :

1. Extraire des données d’un document : ________________________
2. Trouver des idées de noms pour une startup : ________________
3. Répondre à une question technique précise : __________________
4. Écrire une histoire courte : _______________________________

### Corrigé indicatif

<details>
<summary>Afficher les réponses</summary>

**Exercice 1 :** la première phrase est une instruction système ; la deuxième est le message utilisateur.

**Exercice 2 :** pour l’extraction et les questions techniques, privilégie une température basse ; pour les idées et l’écriture créative, une température plus élevée peut être adaptée, selon le résultat recherché.

</details>

## ✅ Vérification de compréhension

- [ ] Je peux expliquer ce qu’est un token.
- [ ] Je comprends que la fenêtre de contexte a une limite.
- [ ] Je sais que la température influence la variabilité, pas la véracité.
- [ ] Je peux distinguer les instructions système et utilisateur.
- [ ] Je peux écrire un prompt plus précis.

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**Un exemple de tâche à faible température :** ___________________  
**Un exemple de tâche à température plus élevée :** ______________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources fiables

- [OpenAI — Advanced usage : tokens, température et limites](https://developers.openai.com/api/docs/guides/advanced-usage)
- [OpenAI — Conversation state et fenêtre de contexte](https://developers.openai.com/api/docs/guides/conversation-state)
- [OpenAI — Température et top_p](https://help.openai.com/en/articles/6654000-how-to-use-temperature-and-top-p)
- [Google — Glossaire IA générative : contexte et température](https://developers.google.com/machine-learning/glossary/generative)
- [Microsoft — Prompt engineering et rôles](https://learn.microsoft.com/en-us/azure/foundry/openai/concepts/prompt-engineering)

> **À retenir en une phrase :** les tokens sont les unités de texte, la fenêtre de contexte fixe la quantité traitable dans une requête, la température règle la variabilité, et les rôles système/utilisateur organisent les instructions et la demande. [web:352][web:354][web:355][web:356]
