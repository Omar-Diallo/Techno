<!--
  Fichier : Jour1_IA_ML_Notions_fondamentales.md
  Cours   : IA / Machine Learning — notions fondamentales
  Date    : 14 décembre 2026
  Durée   : 60 à 90 minutes
-->

# 🟣 IA / Machine Learning — Jour 1

> **Thème :** comprendre l’IA, le Machine Learning, le Deep Learning, les données, les variables et la cible.
>
> **Objectif :** savoir expliquer ces notions et reconnaître les éléments d’un problème simple de prédiction.

---

## 🎯 À la fin du cours, tu sauras

- distinguer intelligence artificielle, Machine Learning et Deep Learning ;
- expliquer à quoi servent les données dans l’apprentissage ;
- différencier les **variables d’entrée** et la **cible** ;
- formuler un exemple de problème de prédiction.

## 1. Intelligence artificielle (IA)

L’**intelligence artificielle** est un vaste domaine qui vise à créer des systèmes capables d’effectuer des tâches qui demandent habituellement certaines capacités humaines : reconnaître une image, comprendre une question, recommander un film ou prendre une décision à partir d’informations.

L’IA n’est pas une seule technologie. Elle regroupe plusieurs approches et méthodes.

## 2. Machine Learning (ML)

Le **Machine Learning**, ou apprentissage automatique, est une branche de l’IA. Au lieu d’écrire une règle précise pour chaque situation, on entraîne un modèle à repérer des régularités dans des données, puis à produire une prédiction ou une décision sur de nouvelles données. [web:238]

### Exemple : prédire un prix

Au lieu d’écrire une règle fixe comme « toutes les maisons coûtent le même prix », on donne au modèle des exemples de maisons et leurs prix. Il apprend des relations entre les caractéristiques des maisons et leur prix, puis estime le prix d’une maison qu’il n’a pas vue.

## 3. Deep Learning (DL)

Le **Deep Learning**, ou apprentissage profond, est une partie du Machine Learning qui utilise des réseaux de neurones avec plusieurs couches. Il est souvent utilisé pour traiter des données complexes comme des images, du son et du texte. [web:237][web:239]

### La relation entre les notions

```text
Intelligence artificielle (IA)
└── Machine Learning (ML)
    └── Deep Learning (DL)
```

Donc, le Deep Learning est une forme de Machine Learning, et le Machine Learning est une partie de l’IA. [web:239]

> **Image mentale :** l’IA est la grande boîte ; le Machine Learning est une boîte à l’intérieur ; le Deep Learning est une boîte plus spécialisée à l’intérieur du Machine Learning.

## 4. Qu’est-ce qu’une donnée ?

Une **donnée** est une information enregistrée. Elle peut être un nombre, un texte, une date, une image, un son ou une mesure.

Exemples pour des logements :

- surface : `75 m²` ;
- nombre de chambres : `3` ;
- quartier : `Plainpalais` ;
- année de construction : `2005` ;
- prix : `650000 CHF`.

Un ensemble de données organisé en lignes et colonnes est souvent appelé un **jeu de données** (*dataset*).

## 5. Variables d’entrée et cible

Dans un problème de Machine Learning supervisé, on cherche généralement à prédire une information à partir d’autres informations.

- Les **variables d’entrée**, aussi appelées *features* ou caractéristiques, sont les informations fournies au modèle pour l’aider à faire sa prédiction.
- La **cible**, aussi appelée *target* ou *label*, est l’information que le modèle doit apprendre à prédire.

### Exemple : prix d’un logement

| Surface | Chambres | Quartier | Année | Prix |
|---:|---:|---|---:|---:|
| 75 | 3 | Plainpalais | 2005 | 650000 |
| 48 | 2 | Carouge | 1998 | 470000 |
| 100 | 4 | Eaux-Vives | 2018 | 920000 |

Si l’objectif est de **prédire le prix** :

- les variables d’entrée sont `surface`, `chambres`, `quartier` et `année` ;
- la cible est `prix`.

On peut noter cela simplement :

```text
Entrées (X) : surface, chambres, quartier, année
Cible (y)   : prix
```

Dans de nombreux outils Python, on appelle souvent les entrées `X` et la cible `y`.

## 6. Autre exemple : prédire le risque de débordement

Supposons qu’une commune veut prévoir si une poubelle risque de déborder demain.

| Quartier | Niveau actuel (%) | Jour | Collectes précédentes | Débordement demain ? |
|---|---:|---|---:|---|
| Centre | 82 | Lundi | 4 | Oui |
| Nord | 35 | Lundi | 2 | Non |
| Sud | 91 | Mardi | 5 | Oui |

Si l’objectif est de prédire **« Débordement demain ? »** :

- les variables d’entrée sont le quartier, le niveau actuel, le jour et les collectes précédentes ;
- la cible est `Débordement demain ?`.

Ce type de cible est une catégorie (`Oui` ou `Non`) : on parle d’un problème de **classification**. Si la cible était un nombre, comme le volume de déchets attendu, on parlerait plutôt de **régression**.

## 7. Comment le modèle apprend-il ?

Dans un apprentissage supervisé, on donne au modèle des exemples comprenant les variables d’entrée et la bonne réponse attendue, la cible. Le modèle ajuste ses paramètres pour mieux produire la cible à partir des entrées. Ensuite, on vérifie s’il réussit sur des exemples qu’il n’a pas utilisés pour apprendre. [web:236][web:243]

```text
Données d’exemple
       ↓
Variables d’entrée + cible connue
       ↓
Entraînement du modèle
       ↓
Modèle entraîné
       ↓
Prédiction sur une nouvelle observation
```

Le modèle ne « comprend » pas nécessairement le problème comme une personne. Il repère des relations dans les données ; ses résultats dépendent notamment de la qualité et de la pertinence des exemples.

## 8. Erreurs fréquentes

- **Confondre IA et ML :** le ML est une partie de l’IA, pas un synonyme de toute l’IA.
- **Confondre variable et cible :** les variables servent à prédire ; la cible est ce qu’on veut prédire.
- **Choisir une cible qui n’est pas définie clairement :** il faut savoir exactement ce que le modèle doit produire.
- **Croire que plus de données garantit un bon modèle :** les données doivent aussi être pertinentes, suffisamment fiables et représentatives.
- **Utiliser par erreur une information indisponible au moment de la prédiction :** cela peut donner une évaluation trompeuse. Tu étudieras plus tard cette fuite de données (*data leakage*).

## ✍️ Exercices

### Exercice 1 — reconnaître X et y

On veut prédire si un client va renouveler son abonnement à partir de son ancienneté, de son type d’abonnement, de son nombre de connexions et de sa réponse : `Renouvelle ?`.

- Variables d’entrée (X) : ancieneté , type, reponses , nombre de connections 
- Cible (y) : *Renouvelle*
- Classification ou régression ? classification

### Exercice 2 — proposer un problème

Choisis un problème simple dans un domaine qui t’intéresse et complète :

- **Ce que je veux prédire :** je veux prédire si l'unige me prendra en doctorat
- **Variables qui pourraient aider :** Directeur de thèse , Notes , Projets
- **La cible est-elle un nombre ou une catégorie ?** Catégorie

### Corrigé de l’exercice 1

<details>
<summary>Afficher les réponses</summary>

- **X :** ancienneté, type d’abonnement, nombre de connexions.
- **y :** `Renouvelle ?`.
- **Type :** classification, car la réponse est une catégorie (oui/non).

</details>

## ✅ Vérification rapide

- [ ] Je peux expliquer la différence entre IA, ML et Deep Learning.
- [ ] Je peux distinguer les variables d’entrée et la cible.
- [ ] Je sais dire si une cible correspond à une classification ou une régression.
- [ ] Je peux proposer un exemple de prédiction dans un domaine concret.

## 📝 Mon bilan

**L’idée la plus importante retenue :** ___________________________  
**Un exemple de cible que je pourrais prédire :** _________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources

- [Google Machine Learning Crash Course — cadrer un problème ML](https://developers.google.com/machine-learning/problem-framing/ml-framing)
- [IBM — Machine Learning](https://www.ibm.com/think/topics/machine-learning)
- [IBM — Deep Learning](https://www.ibm.com/think/topics/deep-learning)

> **À retenir en une phrase :** en Machine Learning, on fournit des données et des variables d’entrée à un modèle pour lui apprendre à prédire une cible ; le Deep Learning est une approche particulière de ML fondée sur des réseaux de neurones multicouches. [web:236][web:237][web:238]
