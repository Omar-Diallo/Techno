<!--
  Fichier : Jour1.md
  Cours   : SQL — notions fondamentales
  Date    : 12 octobre 2026
  Thème   : Base de données, table, ligne, colonne et clé primaire
-->

# 🟢 SQL — Jour 1 : comprendre les bases

> **Objectif du jour :** comprendre comment une base de données organise l’information et savoir reconnaître une table, une ligne, une colonne et une clé primaire.
>
> **Durée conseillée :** 45 à 60 minutes  
> **Niveau :** débutant / révision  
> **Statut :** ⬜ À faire · 🟡 En cours · ✅ Terminé

---

## 🎯 À la fin de ce cours, tu sauras

- expliquer ce qu’est une base de données ;
- différencier une table, une ligne et une colonne ;
- comprendre le rôle d’une clé primaire ;
- lire un petit tableau comme une table de base de données.

## 1. Qu’est-ce qu’une base de données ?

Une **base de données** est un ensemble organisé d’informations que l’on peut consulter, modifier et gérer. Elle sert à conserver des données de façon structurée.

Par exemple, une université peut utiliser une base de données pour enregistrer les étudiants, les cours, les inscriptions et les résultats. Une boutique peut y enregistrer ses clients, ses produits et ses commandes.

On peut imaginer la base de données comme un classeur numérique contenant plusieurs tableaux liés entre eux.

## 2. Qu’est-ce qu’une table ?

Une **table** est une partie de la base de données consacrée à un type d’information.

Exemples :

- une table `etudiants` contient des informations sur les étudiants ;
- une table `cours` contient les informations sur les cours ;
- une table `inscriptions` contient les inscriptions aux cours.

Chaque table possède des **colonnes** et des **lignes**.

## 3. Colonnes et lignes

- Une **colonne** décrit un type d’information, par exemple `nom`, `email` ou `date_inscription`.
- Une **ligne** regroupe les informations concernant un seul élément, par exemple un étudiant.

Exemple de table `etudiants` :

| id_etudiant | prenom | nom | ville |
|---:|---|---|---|
| 101 | Awa | Ndiaye | Dakar |
| 102 | Omar | Diallo | Genève |
| 103 | Mariama | Fall | Saint-Louis |

Dans cet exemple :

- la table s’appelle `etudiants` ;
- `prenom`, `nom` et `ville` sont des colonnes ;
- la ligne contenant `Omar`, `Diallo` et `Genève` décrit un étudiant ;
- la valeur `Genève` est une donnée située dans une cellule.

### 🧠 Astuce pour retenir

Pense à une feuille Excel :

- **table** = la feuille organisée ;
- **colonne** = une catégorie d’information ;
- **ligne** = un enregistrement complet ;
- **cellule** = une valeur précise.

## 4. Qu’est-ce qu’une clé primaire ?

Une **clé primaire** (*primary key*) est une colonne — ou parfois un groupe de colonnes — qui identifie chaque ligne de manière unique.

Dans l’exemple, `id_etudiant` est la clé primaire. Chaque étudiant possède un identifiant différent, même si deux étudiants ont le même prénom ou le même nom.

Une clé primaire doit être :

1. **unique** : aucune ligne ne doit avoir le même identifiant ;
2. **non nulle** : chaque ligne doit avoir une valeur d’identifiant.

La documentation PostgreSQL précise qu’une clé primaire identifie de façon unique les lignes et impose des valeurs uniques et non nulles. Une table ne possède qu’une seule clé primaire, qui peut être composée de plusieurs colonnes. [web:180]

### Pourquoi ne pas utiliser le nom comme clé ?

Deux personnes peuvent s’appeler de la même façon, et un nom peut changer. Un identifiant dédié, comme `id_etudiant`, est donc généralement plus fiable.

## 5. Petit exemple SQL

Voici une instruction qui crée une table `etudiants` :

```sql
CREATE TABLE etudiants (
    id_etudiant INTEGER PRIMARY KEY,
    prenom      TEXT NOT NULL,
    nom         TEXT NOT NULL,
    ville       TEXT
);
```

Lecture de la structure :

- `CREATE TABLE etudiants` : créer une table appelée `etudiants` ;
- `id_etudiant INTEGER PRIMARY KEY` : créer un identifiant numérique unique ;
- `prenom TEXT` et `nom TEXT` : stocker du texte ;
- `NOT NULL` : exiger une valeur pour ce champ ;
- `ville TEXT` : stocker le nom d’une ville, si la valeur est connue.

Pour l’instant, retiens surtout la structure. Tu pratiqueras bientôt les commandes pour ajouter et consulter les données.

## 6. Erreurs fréquentes à éviter

- **Confondre table et base de données** : une base peut contenir plusieurs tables.
- **Confondre ligne et colonne** : une ligne représente un enregistrement ; une colonne représente un attribut.
- **Utiliser une valeur non unique comme identifiant** : deux étudiants peuvent avoir le même nom.
- **Penser que `NULL` signifie zéro** : `NULL` indique généralement qu’une valeur est absente ou inconnue.

## ✍️ Exercices rapides

### Exercice 1
Dans la table ci-dessus, indique :

1. le nom de la table ;
2. le nombre de colonnes ;
3. le nombre d’étudiants ;
4. la clé primaire ;
5. la ville de l’étudiant dont l’identifiant est `102`.

### Exercice 2
Pour une table `produits`, propose quatre colonnes et choisis une clé primaire.

**Ma réponse :**

- Colonnes : `____________________________________________`
- Clé primaire : `________________________________________`

### Corrigé à consulter après avoir essayé

<details>
<summary>Afficher les réponses</summary>

**Exercice 1 :**

1. `etudiants` ;
2. 4 colonnes ;
3. 3 étudiants ;
4. `id_etudiant` ;
5. Genève.

**Exercice 2 — exemple possible :** `id_produit`, `nom`, `prix`, `categorie`. La clé primaire est `id_produit`.

</details>

## ✅ Vérification de compréhension

Coche ce qui est vrai :

- [ ] Une base de données peut contenir plusieurs tables.
- [ ] Une colonne représente généralement un type d’information.
- [ ] Une ligne représente généralement un enregistrement.
- [ ] Une clé primaire peut être répétée sur plusieurs lignes.

**Réponses :** les trois premières affirmations sont vraies ; la dernière est fausse.

## 📝 Mon bilan du jour

**Ce que j’ai compris :**

> À compléter avec tes propres mots.

**Ce qui reste difficile :**

> À compléter.

**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5

**Statut du cours :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

### 📚 Ressources

- [Documentation PostgreSQL en français — Contraintes et clés primaires](https://docs.postgresql.fr/current/ddl-constraints.html)
- [SQLBolt — leçons interactives SQL](https://sqlbolt.com/)

> **À retenir en une phrase :** une base de données contient des tables, les tables contiennent des lignes et des colonnes, et la clé primaire identifie chaque ligne de façon unique.
