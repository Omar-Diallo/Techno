<!--
  Fichier : Jour3_IA_ML_Dataset_Features_Target_Missing.md
  Cours   : IA / Machine Learning — Jour 3 : dataset, features, target et valeurs manquantes
  Durée   : 60 à 90 minutes
  Mode    : adapté à l’aperçu sombre de VS Code
-->

<div style="background:#2e1065; border-left:8px solid #ba68c8; padding:16px 20px; border-radius:10px; color:#f3e5f5;">
  <h1 style="color:#ce93d8; margin:0;">🟣 IA / Machine Learning — Jour 3</h1>
  <p style="margin:8px 0 0; color:#f3e5f5;"><b>Thème :</b> charger un dataset, identifier les features, la target et les données manquantes.</p>
</div>

<br>

<div style="background:#1b3a1f; border:1px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>🎯 Objectif :</b> importer un jeu de données avec Pandas, distinguer les variables d’entrée (features) et la cible (target), puis repérer les valeurs manquantes.</p>
</div>

---

## 🎯 À la fin du cours, tu sauras

- <span style="color:#81c784;"><b>✅ charger</b></span> un dataset CSV avec <code>pd.read_csv()</code> ;
- <span style="color:#81c784;"><b>✅ distinguer</b></span> les features (X) et la target (y) ;
- <span style="color:#81c784;"><b>✅ inspecter</b></span> les premières lignes et les types avec <code>head()</code> et <code>info()</code> ;
- <span style="color:#81c784;"><b>✅ repérer</b></span> les valeurs manquantes avec <code>isnull()</code> et <code>sum()</code> ;
- <span style="color:#81c784;"><b>✅ séparer</b></span> X et y pour un modèle supervisé.

---

## 1. Rappel : features et target

Dans un problème supervisé :

- Les **features** (variables d’entrée) sont les colonnes utilisées pour prédire.
- La **target** (cible) est la colonne que le modèle doit apprendre à prédire.

En scikit-learn, on note souvent :

```text
X = features (variables d’entrée)
y = target (cible)
```

La documentation scikit-learn précise que les données sont stockées dans `.data` (features) et `.target` (cible) pour les datasets intégrés. [web:475][web:476]

## 2. Charger un dataset CSV

```python
import pandas as pd

df = pd.read_csv("donnees.csv")
```

La fonction `pd.read_csv()` lit un fichier CSV et le charge dans un DataFrame. [web:469][web:470]

### Exemple de dataset

```csv
surface,chambres,quartier,annee,prix
45,2,Plainpalais,2005,480000
70,3,Carouge,1998,690000
95,4,Eaux-Vives,2018,920000
```

Si l’objectif est de prédire `prix` :

- **Features (X)** : `surface`, `chambres`, `quartier`, `annee`
- **Target (y)** : `prix`

## 3. Explorer le dataset

### A. Voir les premières lignes

```python
df.head()
```

Affiche les 5 premières lignes par défaut.

### B. Voir les types et les valeurs manquantes

```python
df.info()
```

Affiche le nombre de lignes, de colonnes, les types et le nombre de valeurs non nulles.

### C. Statistiques descriptives

```python
df.describe()
```

Affiche count, mean, std, min, quartiles et max pour les colonnes numériques.

## 4. Identifier les valeurs manquantes

### A. Compter les valeurs manquantes par colonne

```python
df.isnull().sum()
```

Affiche le nombre de valeurs manquantes (`NaN`) pour chaque colonne.

### B. Pourcentage de valeurs manquantes

```python
(df.isnull().sum() / len(df)) * 100
```

Affiche le pourcentage de valeurs manquantes par colonne.

### C. Voir les lignes avec des valeurs manquantes

```python
df[df.isnull().any(axis=1)]
```

Affiche uniquement les lignes contenant au moins une valeur manquante.

Pandas interprète par défaut plusieurs chaînes comme valeurs manquantes (`NaN`, `N/A`, `NULL`, chaîne vide, etc.). [web:469][web:474]

## 5. Séparer X et y

```python
X = df.drop("prix", axis=1)  # features
y = df["prix"]               # target
```

- `X` contient toutes les colonnes sauf `prix`.
- `y` contient uniquement la colonne `prix`.

## 6. Exemple complet

```python
import pandas as pd

# Charger le dataset
df = pd.read_csv("logements.csv")

# Explorer
print(df.head())
print(df.info())
print(df.describe())

# Valeurs manquantes
print(df.isnull().sum())

# Séparer X et y
X = df.drop("prix", axis=1)
y = df["prix"]

print(X.shape)
print(y.shape)
```

## 7. Que faire des valeurs manquantes ?

| Situation | Action possible |
|---|---|
| Peu de valeurs manquantes | Supprimer les lignes concernées |
| Colonne numérique | Remplacer par la moyenne ou la médiane |
| Colonne catégorielle | Remplacer par le mode ou une catégorie « Inconnu » |
| Colonne très incomplète | Supprimer la colonne si elle n’est pas utile |

Tu apprendras plus tard à gérer ces cas avec Pandas et scikit-learn (imputation).

## 8. Erreurs fréquentes

<div style="background:#4e1c1c; border-left:6px solid #ef5350; padding:12px 16px; border-radius:8px; color:#ffebee;">
  <p style="margin:0;"><b>⚠️ Attention :</b> vérifie toujours que la target est bien identifiée avant de séparer X et y.</p>
</div>

- **Oublier de retirer la target de X** : le modèle apprendrait sur la réponse.
- **Confondre feature et target** : la target est ce qu’on veut prédire.
- **Ne pas vérifier les valeurs manquantes** : cela peut fausser l’entraînement.
- **Mauvais chemin de fichier** : vérifie le nom et l’emplacement du CSV.

## ✍️ Exercices

### Exercice 1 — charger et explorer

1. Crée un fichier `logements.csv` avec 5 lignes.
2. Charge-le dans un DataFrame.
3. Affiche `head()`, `info()` et `describe()`.

### Exercice 2 — identifier X et y

Pour le dataset ci-dessus, indique :
- les features ;
- la target ;
- le type de problème (régression ou classification).

### Exercice 3 — valeurs manquantes

1. Ajoute volontairement une valeur manquante dans le CSV.
2. Utilise `isnull().sum()` pour la repérer.
3. Calcule le pourcentage de valeurs manquantes.

### Corrigé indicatif

<details>
<summary>Afficher les réponses</summary>

**Exercice 2 :**  
- Features : `surface`, `chambres`, `quartier`, `annee`  
- Target : `prix`  
- Type : régression (la cible est un nombre).

**Exercice 3 :**

```python
df.isnull().sum()
(df.isnull().sum() / len(df)) * 100
```

</details>

## ✅ Vérification de compréhension

- [ ] Je sais charger un dataset avec Pandas.
- [ ] Je peux distinguer features et target.
- [ ] Je sais repérer les valeurs manquantes.
- [ ] Je sais séparer X et y.
- [ ] Je connais au moins une stratégie pour gérer les valeurs manquantes.

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**Mon dataset d’exemple :** _____________________________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources officielles

- [Pandas — read_csv](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html)
- [scikit-learn — Introduction au Machine Learning](https://scikit-learn.org/stable/tutorial/basic/tutorial.html)
- [Kaggle — Intro to Machine Learning : exploration des données](https://www.kaggle.com/learn/intro-to-machine-learning)

<div style="background:#1b3a1f; border-left:6px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>✅ À retenir en une phrase :</b> charge le dataset avec Pandas, identifie les features (X) et la target (y), puis vérifie les valeurs manquantes avant de préparer le modèle.</p>
</div>
