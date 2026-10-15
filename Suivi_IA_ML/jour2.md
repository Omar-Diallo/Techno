<!--
  Fichier : Jour2_IA_ML_Regression_Classification_Clustering.md
  Cours   : IA / Machine Learning — régression, classification et clustering
  Durée   : 60 à 90 minutes
-->

<div style="background:#f3e5f5; border-left:8px solid #7b1fa2; padding:16px 20px; border-radius:10px;">
  <h1 style="color:#4a148c; margin:0;">🟣 IA / Machine Learning — Jour 2</h1>
  <p style="margin:8px 0 0; color:#4a148c;"><b>Thème :</b> distinguer régression, classification et clustering avec des exemples.</p>
</div>

<br>

<div style="background:#ede7f6; border:1px solid #b39ddb; padding:12px 16px; border-radius:8px;">
  <p style="margin:0;"><b>🎯 Objectif :</b> savoir choisir le type de problème selon la question posée et la nature de la réponse attendue.</p>
</div>

---

## 🎯 À la fin du cours, tu sauras

- <span style="color:#2e7d32;"><b>✅ expliquer</b></span> la différence entre <u>régression</u>, <u>classification</u> et <u>clustering</u> ;
- <span style="color:#2e7d32;"><b>✅ reconnaître</b></span> si une cible est un nombre ou une catégorie ;
- <span style="color:#2e7d32;"><b>✅ donner</b></span> un exemple concret pour chaque type ;
- <span style="color:#2e7d32;"><b>✅ comprendre</b></span> pourquoi le clustering est non supervisé.

---

## 1. Trois questions différentes

En Machine Learning, on choisit souvent le type de tâche selon la question :

| Question | Type de tâche | Réponse attendue |
|---|---|---|
| « Combien ? » | <span style="color:#1565c0;"><b>Régression</b></span> | Un nombre continu |
| « Quelle catégorie ? » | <span style="color:#e65100;"><b>Classification</b></span> | Une classe ou un label |
| « Quels groupes naturels ? » | <span style="color:#6a1b9a;"><b>Clustering</b></span> | Des groupes d’observations |

> [!NOTE]
> La régression et la classification sont <b>supervisées</b> : elles apprennent à partir de données étiquetées, avec une cible connue. Le clustering est <b>non supervisé</b> : il cherche des groupes sans cible fournie.

---

## 2. Régression : prédire un nombre

<div style="background:#e3f2fd; border-left:6px solid #1565c0; padding:12px 16px; border-radius:8px;">
  <p style="margin:0;"><b>🔵 Régression :</b> prédire une valeur numérique continue, par exemple un prix, une température, une durée ou une quantité.</p>
</div>

### Exemple : prix d’un appartement

| Surface | Chambres | Quartier | Prix |
|---:|---:|---|---:|
| 45 | 2 | Plainpalais | 480000 |
| 70 | 3 | Carouge | 690000 |
| 95 | 4 | Eaux-Vives | 940000 |

Si la question est :

```text
Quel sera le prix d’un appartement de 60 m² à Carouge ?
```

La réponse est un nombre, par exemple `610000 CHF`. C’est donc une **régression**.

> **Mots-clés :** combien, quel prix, quelle quantité, quelle durée, quelle température.

---

## 3. Classification : prédire une catégorie

<div style="background:#fff3e0; border-left:6px solid #e65100; padding:12px 16px; border-radius:8px;">
  <p style="margin:0;"><b>🟠 Classification :</b> prédire à quelle catégorie appartient un exemple. La réponse est un label, pas un nombre continu.</p>
</div>

### Exemple : e-mail spam ou non spam

| Sujet | Expéditeur inconnu | Liens suspects | Catégorie |
|---|---:|---:|---|
| Gagnez 10 000 CHF | Oui | Oui | Spam |
| Réunion projet demain | Non | Non | Non spam |
| Facture à valider | Oui | Non | Non spam |

Si la question est :

```text
Ce nouvel e-mail est-il un spam ?
```

La réponse est une catégorie : `Spam` ou `Non spam`. C’est donc une **classification**.

### Deux types de classification

- **Binaire** : deux catégories possibles, par exemple `Spam` / `Non spam`.
- **Multiclasse** : plusieurs catégories possibles, par exemple `Recyclable`, `Compostable` ou `Déchet résiduel`.

> **Mots-clés :** spam ou non, oui ou non, recyclable ou non, quelle catégorie.

---

## 4. Clustering : découvrir des groupes

<div style="background:#f3e5f5; border-left:6px solid #7b1fa2; padding:12px 16px; border-radius:8px;">
  <p style="margin:0;"><b>🟣 Clustering :</b> regrouper des observations similaires sans utiliser de cible connue. On ne demande pas au modèle de prédire une catégorie déjà définie : on lui demande de trouver des groupes dans les données.</p>
</div>

### Exemple : clients d’une boutique

| Client | Dépenses annuelles | Nombre de visites |
|---|---:|---:|
| A | 1200 | 18 |
| B | 150 | 2 |
| C | 1100 | 15 |
| D | 180 | 3 |

Un algorithme de clustering peut découvrir deux groupes :

```text
Groupe 1 : clients fréquents et dépensiers
Groupe 2 : clients occasionnels
```

Tu ne donnes pas au modèle les noms des groupes. Tu observes ensuite les groupes obtenus et tu les interprètes.

> **Mots-clés :** segmenter, regrouper, découvrir des profils, trouver des groupes.

---

## 5. Tableau comparatif

| Critère | <span style="color:#1565c0;"><b>Régression</b></span> | <span style="color:#e65100;"><b>Classification</b></span> | <span style="color:#7b1fa2;"><b>Clustering</b></span> |
|---|---|---|---|
| Question typique | Combien ? | Quelle catégorie ? | Quels groupes ? |
| Réponse | Nombre continu | Label ou catégorie | Groupe d’appartenance |
| Apprentissage | Supervisé | Supervisé | Non supervisé |
| Cible connue | Oui | Oui | Non |
| Exemple | Prédire un prix | Détecter un spam | Segmenter des clients |
| Algorithme courant | Régression linéaire | Régression logistique, arbre, Random Forest | K-means, DBSCAN |

---

## 6. Exemple appliqué : gestion des déchets

| Problème | Type | Cible |
|---|---|---|
| Prédire le volume de déchets collecté demain | <span style="color:#1565c0;"><b>Régression</b></span> | Volume en litres |
| Prédire si un conteneur débordera | <span style="color:#e65100;"><b>Classification</b></span> | `Oui` / `Non` |
| Regrouper les quartiers selon leurs habitudes de tri | <span style="color:#7b1fa2;"><b>Clustering</b></span> | Groupes de quartiers |

Pour le clustering, tu ne donnes pas au modèle les noms des groupes. Tu pourrais ensuite interpréter les groupes comme « quartiers très actifs », « quartiers moyens » ou « quartiers à accompagner ».

---

## 7. Comment choisir ?

Pose-toi ces questions :

1. **Qu’est-ce que je veux prédire ?**
2. **La réponse est-elle un nombre ou une catégorie ?**
3. **Ai-je des exemples avec la bonne réponse connue ?**

### Arbre de décision simple

```text
Je veux prédire une valeur numérique ?
├── Oui → Régression
└── Non
    ├── Je connais les catégories à l’avance ?
    │   ├── Oui → Classification
    │   └── Non → Clustering
```

---

## 8. Erreurs fréquentes

<div style="background:#ffebee; border-left:6px solid #c62828; padding:12px 16px; border-radius:8px;">
  <p style="margin:0;"><b>⚠️ Attention :</b> ne confonds pas classification et clustering. La classification utilise des labels connus ; le clustering découvre des groupes.</p>
</div>

- **Confondre régression et classification :** un prix est une régression ; `cher` ou `pas cher` est une classification.
- **Utiliser le clustering pour prédire une catégorie connue :** si tu as déjà les labels, c’est plutôt un problème de classification.
- **Croire que le clustering donne automatiquement des noms utiles :** après le clustering, il faut interpréter les groupes.

---

## ✍️ Exercices

### Exercice 1 — identifier le type

Pour chaque problème, indique s’il s’agit de régression, classification ou clustering :

1. Prédire le prix d’un billet d’avion : régression
2. Détecter si un e-mail est un spam : classification
3. Regrouper des clients selon leurs achats : clustering
4. Prédire si un étudiant réussira un examen : classification
5. Estimer la consommation d’énergie d’un bâtiment : régression

### Exercice 2 — créer ton exemple

Choisis un problème dans un domaine qui t’intéresse et complète :

- **Question :** _______________________________________________
- **Type :** régression / classification / clustering
- **Variables d’entrée :** ____________________________________
- **Cible ou résultat attendu :** _____________________________

### Corrigé

<details>
<summary>Afficher les réponses</summary>

**Exercice 1 :**  
1. Régression ;  
2. Classification ;  
3. Clustering ;  
4. Classification ;  
5. Régression.

</details>

---

## ✅ Vérification de compréhension

- [ ] Je peux expliquer la régression avec un exemple.
- [ ] Je peux expliquer la classification avec un exemple.
- [ ] Je peux expliquer le clustering avec un exemple.
- [ ] Je sais que régression et classification sont supervisées.
- [ ] Je sais que le clustering est non supervisé.

---

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**Un exemple de régression :** __________________________________  
**Un exemple de classification :** ______________________________  
**Un exemple de clustering :** __________________________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources fiables

- [Google Machine Learning Crash Course — Classification](https://developers.google.com/machine-learning/crash-course/classification)
- [IBM — Classification vs Regression](https://www.ibm.com/think/topics/classification-vs-regression)
- [scikit-learn — Apprentissage supervisé et non supervisé](https://scikit-learn.org/stable/user_guide.html)
- [scikit-learn — Clustering](https://scikit-learn.org/stable/unsupervised_learning.html)

<div style="background:#e8f5e9; border-left:6px solid #2e7d32; padding:12px 16px; border-radius:8px;">
  <p style="margin:0;"><b>✅ À retenir en une phrase :</b> la régression prédit un nombre, la classification prédit une catégorie connue, et le clustering découvre des groupes sans cible fournie.</p>
</div>
