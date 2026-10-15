<!--
  Fichier : Jour2_SQL_SELECT_Colonnes.md
  Cours   : SQL — Jour 2 : sélectionner toutes ou certaines colonnes
  Durée   : 45 à 75 minutes
  Mode    : adapté à l’aperçu sombre de VS Code
-->

<div style="background:#0b2e13; border-left:8px solid #66bb6a; padding:16px 20px; border-radius:10px; color:#e8f5e9;">
  <h1 style="color:#81c784; margin:0;">🟢 SQL — Jour 2</h1>
  <p style="margin:8px 0 0; color:#e8f5e9;"><b>Thème :</b> sélectionner toutes ou certaines colonnes avec <code>SELECT</code>.</p>
</div>

<br>

<div style="background:#1b3a1f; border:1px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>🎯 Objectif :</b> savoir lire une table et choisir les colonnes à afficher avec <code>SELECT</code>.</p>
</div>

---

## 🎯 À la fin du cours, tu sauras

- <span style="color:#81c784;"><b>✅ utiliser</b></span> <code>SELECT *</code> pour afficher toutes les colonnes ;
- <span style="color:#81c784;"><b>✅ choisir</b></span> certaines colonnes avec leurs noms ;
- <span style="color:#81c784;"><b>✅ renommer</b></span> une colonne avec <code>AS</code> ;
- <span style="color:#81c784;"><b>✅ éviter</b></span> les erreurs fréquentes de syntaxe.

---

## 1. Rappel : table, ligne et colonne

Une **table** contient des données organisées en lignes et colonnes.

| id_etudiant | prenom | nom | ville |
|---:|---|---|---|
| 101 | Awa | Ndiaye | Dakar |
| 102 | Omar | Diallo | Genève |
| 103 | Mariama | Fall | Saint-Louis |

- La table s’appelle `etudiants`.
- `id_etudiant`, `prenom`, `nom` et `ville` sont des colonnes.
- Chaque ligne représente un étudiant.

## 2. Sélectionner toutes les colonnes

Pour afficher **toutes les colonnes** d’une table, utilise `SELECT *`.

```sql
SELECT *
FROM etudiants;
```

Lecture :

- `SELECT` : je veux afficher des données ;
- `*` : toutes les colonnes ;
- `FROM etudiants` : depuis la table `etudiants`.

### Résultat attendu

| id_etudiant | prenom | nom | ville |
|---:|---|---|---|
| 101 | Awa | Ndiaye | Dakar |
| 102 | Omar | Diallo | Genève |
| 103 | Mariama | Fall | Saint-Louis |

> [!NOTE]
> `SELECT *` est pratique pour découvrir une table, mais en production on préfère souvent lister les colonnes nécessaires.

## 3. Sélectionner certaines colonnes

Pour afficher seulement certaines colonnes, écris leurs noms après `SELECT`, séparés par des virgules.

```sql
SELECT prenom, nom
FROM etudiants;
```

### Résultat attendu

| prenom | nom |
|---|---|
| Awa | Ndiaye |
| Omar | Diallo |
| Mariama | Fall |

Tu peux choisir les colonnes dans n’importe quel ordre :

```sql
SELECT ville, nom, prenom
FROM etudiants;
```

## 4. Renommer une colonne avec AS

Pour donner un autre nom à une colonne dans le résultat, utilise `AS`.

```sql
SELECT prenom AS prenom_etudiant, ville AS ville_de_residence
FROM etudiants;
```

### Résultat attendu

| prenom_etudiant | ville_de_residence |
|---|---|
| Awa | Dakar |
| Omar | Genève |
| Mariama | Saint-Louis |

> [!TIP]
> `AS` ne change pas le nom de la colonne dans la table : il change seulement le nom affiché dans le résultat.

## 5. Exemple complet

```sql
-- Afficher toutes les colonnes
SELECT *
FROM etudiants;

-- Afficher seulement le prénom et la ville
SELECT prenom, ville
FROM etudiants;

-- Afficher avec des noms personnalisés
SELECT nom AS nom_famille, ville AS ville_actuelle
FROM etudiants;
```

## 6. Erreurs fréquentes

<div style="background:#4e1c1c; border-left:6px solid #ef5350; padding:12px 16px; border-radius:8px; color:#ffebee;">
  <p style="margin:0;"><b>⚠️ Attention :</b> vérifie toujours l’orthographe exacte des noms de colonnes et de tables.</p>
</div>

- **Oublier la virgule** entre deux colonnes :

```sql
-- Incorrect
SELECT prenom nom FROM etudiants;

-- Correct
SELECT prenom, nom FROM etudiants;
```

- **Oublier le `FROM`** :

```sql
-- Incorrect
SELECT prenom, nom;

-- Correct
SELECT prenom, nom FROM etudiants;
```

- **Utiliser un nom de colonne inexistant** :

```sql
-- Incorrect si la colonne n’existe pas
SELECT prenom, adresse FROM etudiants;
```

## ✍️ Exercices

### Exercice 1 — afficher toutes les colonnes

Écris une requête pour afficher toutes les colonnes de la table `etudiants`.

### Exercice 2 — afficher certaines colonnes

Écris une requête pour afficher seulement `prenom` et `ville`.

### Exercice 3 — renommer

Écris une requête pour afficher `nom` sous le nom `nom_famille` et `ville` sous le nom `ville_actuelle`.

### Corrigé

<details>
<summary>Afficher les réponses</summary>

```sql
-- Exercice 1
SELECT * FROM etudiants;

-- Exercice 2
SELECT prenom, ville FROM etudiants;

-- Exercice 3
SELECT nom AS nom_famille, ville AS ville_actuelle FROM etudiants;
```

</details>

## ✅ Vérification de compréhension

- [ ] Je sais utiliser `SELECT *`.
- [ ] Je sais choisir certaines colonnes.
- [ ] Je sais utiliser `AS` pour renommer.
- [ ] Je sais éviter les erreurs de syntaxe.

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**La requête la plus utile retenue :** ___________________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources officielles

- [PostgreSQL — SELECT](https://www.postgresql.org/docs/current/sql-select.html)
- [SQLBolt — SELECT queries](https://sqlbolt.com/lesson/select_queries_introduction)

<div style="background:#1b3a1f; border-left:6px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>✅ À retenir en une phrase :</b> utilise <code>SELECT *</code> pour toutes les colonnes, liste les colonnes pour un affichage ciblé, et <code>AS</code> pour renommer dans le résultat.</p>
</div>
