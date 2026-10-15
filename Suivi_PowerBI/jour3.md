<!--
  Fichier : Jour3_PowerBI_PowerQuery_Renommer_Types.md
  Cours   : Power BI — Jour 3 : Power Query, renommer colonnes, gérer les types
  Durée   : 60 à 90 minutes
  Mode    : adapté à l’aperçu sombre de VS Code
-->

<div style="background:#102a43; border-left:8px solid #ffb74d; padding:16px 20px; border-radius:10px; color:#fff3e0;">
  <h1 style="color:#ffb74d; margin:0;">🟠 Power BI — Jour 3</h1>
  <p style="margin:8px 0 0; color:#fff3e0;"><b>Thème :</b> ouvrir Power Query, renommer des colonnes et gérer les types de données.</p>
</div>

<br>

<div style="background:#1b3a1f; border:1px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>🎯 Objectif :</b> préparer tes données dans Power Query : renommer les colonnes pour plus de clarté et vérifier que chaque colonne a le bon type.</p>
</div>

---

## 🎯 À la fin du cours, tu sauras

- <span style="color:#81c784;"><b>✅ ouvrir</b></span> Power Query Editor depuis Power BI Desktop ;
- <span style="color:#81c784;"><b>✅ renommer</b></span> une colonne de plusieurs façons ;
- <span style="color:#81c784;"><b>✅ identifier</b></span> le type de données d’une colonne ;
- <span style="color:#81c784;"><b>✅ changer</b></span> le type d’une colonne ;
- <span style="color:#81c784;"><b>✅ appliquer</b></span> les transformations avec **Close & Apply**.

---

## 1. Qu’est-ce que Power Query ?

**Power Query** est l’outil intégré à Power BI Desktop qui permet de **nettoyer et transformer** les données avant de les charger dans le modèle. Tu peux y renommer des colonnes, changer les types, filtrer, supprimer des lignes, etc.

> **À savoir :** chaque transformation effectuée dans Power Query est enregistrée comme une étape. Lors de l’actualisation des données, Power Query rejoue automatiquement ces étapes. [web:456][web:457]

## 2. Ouvrir Power Query Editor

1. Ouvre Power BI Desktop.
2. Charge un fichier Excel ou CSV (voir Jour 2).
3. Dans le ruban **Accueil**, clique sur **Transformer les données**.
4. La fenêtre **Power Query Editor** s’ouvre.

Tu peux aussi cliquer sur **Transformer les données** directement après avoir sélectionné une source dans la fenêtre du navigateur. [web:456][web:457]

## 3. Renommer une colonne

Il existe plusieurs façons de renommer une colonne dans Power Query :

| Méthode | Étapes |
|---|---|
| **Double-clic** | Double-clique sur l’en-tête de la colonne, tape le nouveau nom, valide. |
| **Clic droit** | Clic droit sur l’en-tête → **Renommer**. |
| **Ruban Transformer** | Sélectionne la colonne → onglet **Transformer** → **Renommer**. |

La documentation Microsoft indique ces trois méthodes et précise que les noms de colonnes doivent être uniques dans une table. [web:465]

### Exemple

Renomme `ProductID` en `Product ID` :

1. Clic droit sur la colonne `ProductID`.
2. Choisis **Renommer**.
3. Tape `Product ID`.
4. Appuie sur Entrée. [web:457]

## 4. Comprendre les types de données

Chaque colonne dans Power Query a un **type de données**. Le type est affiché par une icône à gauche du nom de la colonne. [web:460]

| Icône / type | Signification | Exemple |
|---|---|---|
| `123` | Nombre entier | `25`, `-8`, `0` |
| `1.2` | Nombre décimal | `12.50`, `-2.5` |
| `ABC` | Texte | `Genève`, `Produit A` |
| Calendrier | Date | `2026-01-15` |
| Horloge | Heure | `14:30` |
| Vrai/Faux | Booléen | `True`, `False` |

## 5. Changer le type d’une colonne

Il existe plusieurs façons de changer le type :

| Méthode | Étapes |
|---|---|
| **Icône dans l’en-tête** | Clique sur l’icône à gauche du nom de colonne → choisis le type. |
| **Ruban Transformer** | Sélectionne la colonne → onglet **Transformer** → **Type de données** → choisis. |
| **Ruban Accueil** | Sélectionne la colonne → onglet **Accueil** → **Type de données** → choisis. |
| **Clic droit** | Clic droit sur la colonne → **Modifier le type** → choisis. |

La documentation Microsoft décrit ces méthodes et précise que le changement de type est enregistré comme une étape **Changed Type** rejouée à chaque actualisation. [web:460][web:461]

### Exemple

Change le type de `Quantité` en nombre entier :

1. Clique sur l’icône à gauche de `Quantité`.
2. Choisis **Nombre entier**.
3. Si une fenêtre s’ouvre, choisis **Ajouter une nouvelle étape** pour conserver l’historique. [web:458][web:461]

## 6. Appliquer les transformations

Quand tu as terminé :

1. Dans le ruban **Accueil**, clique sur **Fermer & appliquer**.
2. Power Query ferme et applique toutes les transformations au modèle Power BI.

Tu peux vérifier les étapes appliquées dans le panneau **Paramètres d’une requête** à droite : chaque action (renommage, changement de type, suppression, etc.) y apparaît comme une étape. [web:456][web:457]

## 7. Exemple complet

1. Charge un fichier Excel `ventes.xlsx`.
2. Ouvre Power Query.
3. Renomme `ProductID` en `Product ID`.
4. Change le type de `Quantité` en **Nombre entier**.
5. Change le type de `Prix` en **Nombre décimal**.
6. Change le type de `Date` en **Date**.
7. Clique sur **Fermer & appliquer**.

## 8. Erreurs fréquentes

<div style="background:#4e1c1c; border-left:6px solid #ef5350; padding:12px 16px; border-radius:8px; color:#ffebee;">
  <p style="margin:0;"><b>⚠️ Attention :</b> vérifie toujours le type avant de créer des visuels ou des mesures.</p>
</div>

- **Type incorrect :** une colonne de prix en texte ne permettra pas les calculs.
- **Nom de colonne dupliqué :** Power Query affichera une erreur de conflit de nom. [web:465]
- **Oublier de cliquer sur Fermer & appliquer :** les transformations ne seront pas appliquées au modèle.
- **Supprimer une étape par erreur :** dans le panneau des étapes, tu peux supprimer une étape précise sans tout refaire.

## ✍️ Exercices

### Exercice 1 — renommer

1. Charge un fichier Excel avec des colonnes mal nommées.
2. Renomme au moins 3 colonnes.
3. Vérifie les étapes dans le panneau de droite.

### Exercice 2 — changer les types

1. Identifie les colonnes qui ont un mauvais type.
2. Change-les en type correct (entier, décimal, date, texte).
3. Applique avec **Fermer & appliquer**.

### Corrigé indicatif

<details>
<summary>Afficher un exemple</summary>

- Renommer `ProductID` → `Product ID`
- Renommer `CustName` → `Customer Name`
- Type `Quantité` → Nombre entier
- Type `Prix` → Nombre décimal
- Type `Date` → Date
- Fermer & appliquer

</details>

## ✅ Vérification de compréhension

- [ ] Je sais ouvrir Power Query Editor.
- [ ] Je sais renommer une colonne de 3 façons.
- [ ] Je sais identifier le type d’une colonne.
- [ ] Je sais changer le type d’une colonne.
- [ ] Je sais appliquer avec **Fermer & appliquer**.

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**La transformation la plus utile retenue :** ____________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources officielles

- [Microsoft Learn — Shape and combine data in Power BI Desktop](https://learn.microsoft.com/en-us/power-bi/connect-data/desktop-shape-and-combine-data)
- [Microsoft Learn — Rename columns in Power Query](https://learn.microsoft.com/en-us/power-query/rename-column)
- [Microsoft Learn — Data types in Power Query](https://learn.microsoft.com/en-us/power-query/data-types)
- [Microsoft Learn — Evaluate and change column data types](https://learn.microsoft.com/en-us/training/modules/clean-data-power-bi/4-column-data-types)

<div style="background:#1b3a1f; border-left:6px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>✅ À retenir en une phrase :</b> Power Query permet de renommer les colonnes et de corriger les types avant le chargement ; chaque transformation est enregistrée comme une étape rejouée à l’actualisation.</p>
</div>
