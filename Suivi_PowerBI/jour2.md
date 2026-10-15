<!--
  Fichier : Jour2_PowerBI_Charger_Fichiers_Navigateur.md
  Cours   : Power BI — Jour 2 : charger Excel/CSV et comprendre le navigateur
  Durée   : 60 à 90 minutes
  Mode    : adapté à l’aperçu sombre de VS Code
-->

<div style="background:#102a43; border-left:8px solid #ffb74d; padding:16px 20px; border-radius:10px; color:#fff3e0;">
  <h1 style="color:#ffb74d; margin:0;">🟠 Power BI — Jour 2</h1>
  <p style="margin:8px 0 0; color:#fff3e0;"><b>Thème :</b> charger des fichiers Excel/CSV et comprendre le navigateur de données.</p>
</div>

<br>

<div style="background:#1b3a1f; border:1px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>🎯 Objectif :</b> importer un fichier Excel ou CSV dans Power BI Desktop, puis explorer les données dans les vues Table et Modèle.</p>
</div>

---

## 🎯 À la fin du cours, tu sauras

- <span style="color:#81c784;"><b>✅ importer</b></span> un fichier Excel dans Power BI Desktop ;
- <span style="color:#81c784;"><b>✅ importer</b></span> un fichier CSV dans Power BI Desktop ;
- <span style="color:#81c784;"><b>✅ naviguer</b></span> entre les vues Rapport, Table et Modèle ;
- <span style="color:#81c784;"><b>✅ inspecter</b></span> les colonnes et les types de données ;
- <span style="color:#81c784;"><b>✅ enregistrer</b></span> ton fichier `.pbix`.

---

## 1. Power BI et les sources de données

**Power BI Desktop** permet de se connecter à plusieurs types de sources : Excel, CSV, bases de données, services en ligne, etc. Une fois les données chargées, elles apparaissent dans le modèle et peuvent être utilisées pour créer des visuels.

> **À savoir :** Power BI Desktop ne modifie pas automatiquement le fichier source. Il crée une connexion et charge une copie des données dans le modèle, selon la configuration.

## 2. Charger un fichier Excel

1. Ouvre Power BI Desktop.
2. Dans le ruban, clique sur **Obtenir les données**.
3. Choisis **Excel**.
4. Sélectionne ton fichier `.xlsx`.
5. Dans la fenêtre du navigateur, coche la ou les feuilles à importer.
6. Clique sur **Charger** ou **Transformer les données**.

### Charger ou transformer ?

| Option | Quand l’utiliser |
|---|---|
| **Charger** | Les données sont déjà propres et prêtes à l’emploi |
| **Transformer les données** | Tu veux nettoyer, filtrer ou restructurer avant le chargement |

## 3. Charger un fichier CSV

1. Dans le ruban, clique sur **Obtenir les données**.
2. Choisis **Texte/CSV**.
3. Sélectionne ton fichier `.csv`.
4. Vérifie l’aperçu : séparateur, encodage et types détectés.
5. Clique sur **Charger** ou **Transformer les données**.

> ⚠️ Si les accents s’affichent mal, vérifie l’encodage du fichier (souvent UTF-8 ou Windows-1252).

## 4. Comprendre le navigateur de données

Après le chargement, Power BI affiche les données dans différentes vues :

| Vue | Rôle |
|---|---|
| **Rapport** | Créer les visuels et les pages du rapport |
| **Table** | Voir les lignes et colonnes des tables chargées |
| **Modèle** | Voir et gérer les relations entre les tables |

### A. Vue Table

Dans la **vue Table**, tu peux :

- voir toutes les lignes et colonnes ;
- vérifier les types de données ;
- repérer les valeurs vides ou incohérentes ;
- trier et filtrer les colonnes.

### B. Vue Modèle

Dans la **vue Modèle**, tu peux :

- voir les tables chargées ;
- créer ou modifier des relations ;
- vérifier les clés et les liens entre les tables.

### C. Vue Rapport

Dans la **vue Rapport**, tu peux :

- ajouter des visuels ;
- glisser des champs dans les visuels ;
- créer des pages et des filtres.

## 5. Exemple pratique

1. Crée un fichier Excel `ventes.xlsx` avec une feuille `Ventes`.
2. Ajoute des colonnes : `Date`, `Produit`, `Quantité`, `Prix`.
3. Ouvre Power BI Desktop.
4. Clique sur **Obtenir les données → Excel**.
5. Sélectionne `ventes.xlsx`.
6. Coche la feuille `Ventes`.
7. Clique sur **Charger**.
8. Va dans la vue **Table** pour vérifier les données.
9. Va dans la vue **Modèle** pour voir la table chargée.
10. Enregistre le fichier sous `PowerBI_Jour_02.pbix`.

## 6. Vérifier les types de données

Dans la vue Table ou dans Power Query, vérifie que chaque colonne a le bon type :

| Colonne | Type attendu |
|---|---|
| Date | Date |
| Produit | Texte |
| Quantité | Nombre entier |
| Prix | Nombre décimal |

Si un type est incorrect, tu peux le modifier dans Power Query ou dans la vue Table.

## 7. Erreurs fréquentes

<div style="background:#4e1c1c; border-left:6px solid #ef5350; padding:12px 16px; border-radius:8px; color:#ffebee;">
  <p style="margin:0;"><b>⚠️ Attention :</b> vérifie toujours le chemin du fichier, le séparateur et l’encodage avant de charger.</p>
</div>

- **Fichier introuvable :** vérifie le chemin ou déplace le fichier dans un dossier simple.
- **Accents mal affichés :** vérifie l’encodage du CSV.
- **Types incorrects :** modifie le type dans Power Query ou la vue Table.
- **Feuille Excel introuvable :** vérifie le nom exact de la feuille.

## ✍️ Exercices

### Exercice 1 — charger un Excel

1. Crée un fichier `ventes.xlsx` avec une feuille `Ventes`.
2. Charge-le dans Power BI Desktop.
3. Va dans la vue Table et note le nombre de lignes et de colonnes.
4. Enregistre le fichier `.pbix`.

### Exercice 2 — charger un CSV

1. Crée un fichier `ventes.csv`.
2. Charge-le dans Power BI Desktop.
3. Vérifie le séparateur et l’encodage.
4. Va dans la vue Table et note les types détectés.

### Corrigé indicatif

<details>
<summary>Afficher un exemple</summary>

- Fichier : `ventes.xlsx`
- Feuille : `Ventes`
- Colonnes : `Date`, `Produit`, `Quantité`, `Prix`
- Vue Table : vérifier les types
- Vue Modèle : voir la table chargée
- Fichier enregistré : `PowerBI_Jour_02.pbix`

</details>

## ✅ Vérification de compréhension

- [ ] Je sais charger un Excel avec **Obtenir les données → Excel**.
- [ ] Je sais charger un CSV avec **Obtenir les données → Texte/CSV**.
- [ ] Je connais les vues Rapport, Table et Modèle.
- [ ] Je sais vérifier les types de données.
- [ ] Je sais enregistrer un fichier `.pbix`.

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**La vue la plus utile retenue :** ______________________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources officielles

- [Microsoft Learn — Get data in Power BI Desktop](https://learn.microsoft.com/en-us/power-bi/fundamentals/desktop-getting-started)
- [Microsoft Learn — Connect to data sources](https://learn.microsoft.com/en-us/power-bi/connect-data/desktop-connect-to-data)
- [Microsoft Learn — Power BI Desktop views](https://learn.microsoft.com/en-us/power-bi/transform-model/desktop-query-overview)

<div style="background:#1b3a1f; border-left:6px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>✅ À retenir en une phrase :</b> utilise <b>Obtenir les données</b> pour charger Excel ou CSV, puis explore les données dans les vues Table et Modèle avant de créer des visuels.</p>
</div>
