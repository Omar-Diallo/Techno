<!--
  Fichier : Jour3_SQL_WHERE_Filtres.md
  Cours   : SQL — Jour 3 : filtrer par ville, prix, date, statut
  Durée   : 45 à 75 minutes
  Mode    : adapté à l’aperçu sombre de VS Code
-->

<div style="background:#0b2e13; border-left:8px solid #66bb6a; padding:16px 20px; border-radius:10px; color:#e8f5e9;">
  <h1 style="color:#81c784; margin:0;">🟢 SQL — Jour 3</h1>
  <p style="margin:8px 0 0; color:#e8f5e9;"><b>Thème :</b> filtrer les données avec <code>WHERE</code> : ville, prix, date et statut.</p>
</div>

<br>

<div style="background:#1b3a1f; border:1px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>🎯 Objectif :</b> savoir afficher seulement les lignes qui correspondent à une condition.</p>
</div>

---

## 🎯 À la fin du cours, tu sauras

- <span style="color:#81c784;"><b>✅ utiliser</b></span> <code>WHERE</code> pour filtrer ;
- <span style="color:#81c784;"><b>✅ filtrer</b></span> par ville, prix, date et statut ;
- <span style="color:#81c784;"><b>✅ combiner</b></span> plusieurs conditions avec <code>AND</code> et <code>OR</code> ;
- <span style="color:#81c784;"><b>✅ éviter</b></span> les erreurs fréquentes de syntaxe.

---

## 1. Rappel : SELECT et FROM

Avant de filtrer, on choisit la table et les colonnes.

```sql
SELECT prenom, ville, prix, date_commande, statut
FROM commandes;
```

Ici, on affiche les colonnes `prenom`, `ville`, `prix`, `date_commande` et `statut` de la table `commandes`.

## 2. Filtrer avec WHERE

La clause `WHERE` permet de ne garder que les lignes qui respectent une condition.

```sql
SELECT *
FROM commandes
WHERE ville = 'Genève';
```

Cette requête affiche uniquement les commandes dont la ville est `Genève`.

> [!NOTE]
> Les valeurs texte doivent être entre guillemets simples : `'Genève'`.

## 3. Filtrer par ville

```sql
SELECT prenom, ville
FROM commandes
WHERE ville = 'Genève';
```

Tu peux aussi filtrer sur plusieurs villes avec `IN` :

```sql
SELECT prenom, ville
FROM commandes
WHERE ville IN ('Genève', 'Lausanne');
```

## 4. Filtrer par prix

Pour un nombre, on utilise les opérateurs de comparaison :

| Opérateur | Signification |
|---|---|
| `=` | égal à |
| `>` | supérieur à |
| `<` | inférieur à |
| `>=` | supérieur ou égal |
| `<=` | inférieur ou égal |
| `<>` ou `!=` | différent de |

Exemples :

```sql
-- Commandes de plus de 100 CHF
SELECT *
FROM commandes
WHERE prix > 100;

-- Commandes entre 50 et 200 CHF
SELECT *
FROM commandes
WHERE prix BETWEEN 50 AND 200;
```

## 5. Filtrer par date

Pour une date, on utilise aussi les opérateurs de comparaison.

```sql
-- Commandes après une date
SELECT *
FROM commandes
WHERE date_commande > '2026-01-01';

-- Commandes entre deux dates
SELECT *
FROM commandes
WHERE date_commande BETWEEN '2026-01-01' AND '2026-12-31';
```

> [!NOTE]
> Le format de date dépend du système de gestion de base de données. Le format ISO `AAAA-MM-JJ` est le plus courant.

## 6. Filtrer par statut

Si `statut` est une colonne texte, on filtre avec `=` ou `IN`.

```sql
-- Commandes livrées
SELECT *
FROM commandes
WHERE statut = 'Livrée';

-- Commandes en attente ou annulées
SELECT *
FROM commandes
WHERE statut IN ('En attente', 'Annulée');
```

## 7. Combiner plusieurs conditions

### ET logique : AND

Toutes les conditions doivent être vraies.

```sql
SELECT *
FROM commandes
WHERE ville = 'Genève'
  AND prix > 100;
```

### OU logique : OR

Au moins une condition doit être vraie.

```sql
SELECT *
FROM commandes
WHERE ville = 'Genève'
   OR ville = 'Lausanne';
```

### Mélanger AND et OR

Utilise des parenthèses pour clarifier.

```sql
SELECT *
FROM commandes
WHERE (ville = 'Genève' OR ville = 'Lausanne')
  AND prix > 100;
```

## 8. Tableau récapitulatif

| Besoin | Clause | Exemple |
|---|---|---|
| Ville précise | `WHERE ville = 'Genève'` | Filtre une ville |
| Plusieurs villes | `WHERE ville IN (...)` | Plusieurs valeurs |
| Prix supérieur | `WHERE prix > 100` | Nombre |
| Intervalle de prix | `WHERE prix BETWEEN ... AND ...` | Intervalle |
| Date précise ou plage | `WHERE date_commande ...` | Date |
| Statut précis | `WHERE statut = 'Livrée'` | Texte |
| Plusieurs conditions | `AND`, `OR`, parenthèses | Combinaison |

## 9. Erreurs fréquentes

<div style="background:#4e1c1c; border-left:6px solid #ef5350; padding:12px 16px; border-radius:8px; color:#ffebee;">
  <p style="margin:0;"><b>⚠️ Attention :</b> les valeurs texte doivent être entre guillemets simples.</p>
</div>

- **Oublier les guillemets** pour une ville ou un statut :

```sql
-- Incorrect
WHERE ville = Genève

-- Correct
WHERE ville = 'Genève'
```

- **Confondre `=` et `IN`** : `=` pour une valeur, `IN` pour plusieurs.
- **Oublier les parenthèses** quand on mélange `AND` et `OR`.

## ✍️ Exercices

### Exercice 1 — filtrer par ville

Écris une requête pour afficher les commandes de `Genève`.

### Exercice 2 — filtrer par prix

Écris une requête pour afficher les commandes de plus de `150` CHF.

### Exercice 3 — filtrer par date

Écris une requête pour afficher les commandes après le `1er janvier 2026`.

### Exercice 4 — combiner

Écris une requête pour afficher les commandes de `Genève` ou `Lausanne` avec un prix supérieur à `100`.

### Corrigé

<details>
<summary>Afficher les réponses</summary>

```sql
-- Exercice 1
SELECT * FROM commandes WHERE ville = 'Genève';

-- Exercice 2
SELECT * FROM commandes WHERE prix > 150;

-- Exercice 3
SELECT * FROM commandes WHERE date_commande > '2026-01-01';

-- Exercice 4
SELECT * FROM commandes
WHERE (ville = 'Genève' OR ville = 'Lausanne')
  AND prix > 100;
```

</details>

## ✅ Vérification de compréhension

- [ ] Je sais utiliser `WHERE`.
- [ ] Je sais filtrer par ville, prix, date et statut.
- [ ] Je sais combiner avec `AND` et `OR`.
- [ ] Je sais utiliser les guillemets pour le texte.

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**La clause la plus utile retenue :** ____________________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources officielles

- [PostgreSQL — SELECT et WHERE](https://www.postgresql.org/docs/current/sql-select.html)
- [SQLBolt — Requêtes avec contraintes](https://sqlbolt.com/lesson/select_queries_with_constraints)

<div style="background:#1b3a1f; border-left:6px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>✅ À retenir en une phrase :</b> <code>WHERE</code> filtre les lignes selon une condition ; combine avec <code>AND</code>, <code>OR</code> et <code>IN</code> pour des filtres plus précis.</p>
</div>
