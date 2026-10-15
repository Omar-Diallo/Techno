<!--
  Fichier : Jour1_Python_Environnement_Notebook.md
  Cours   : Python pour la data — installation et premier notebook
  Date    : 2 novembre 2026
  Durée   : environ 60 à 90 minutes
-->

# 🐍 Python pour la data — Jour 1

> **Thème :** installer Python/Anaconda ou utiliser Google Colab, puis créer un premier notebook.
>
> **Objectif :** choisir un environnement, ouvrir un notebook, exécuter quelques cellules et enregistrer son travail.

---

## 🎯 À la fin du cours, tu sauras

- choisir entre Google Colab et une installation locale ;
- reconnaître un notebook Jupyter (`.ipynb`) ;
- créer des cellules Markdown et Python ;
- exécuter et enregistrer un premier notebook.

## 1. Qu’est-ce qu’un notebook ?

Un **notebook Jupyter** est un document interactif composé de cellules. On peut y mélanger du texte explicatif, du code Python et les résultats obtenus (texte, tableaux ou graphiques). Le fichier utilise généralement l’extension `.ipynb`.

Un notebook est pratique pour apprendre et analyser des données : tu peux expliquer une étape, exécuter le code juste en dessous, puis commenter le résultat.

## 2. Choisir son environnement

| Option | Avantages | À choisir si… |
|---|---|---|
| **Google Colab** | Fonctionne dans le navigateur, sans installation locale ; notebooks enregistrés dans Google Drive | Tu veux commencer rapidement ou ton ordinateur a peu de ressources |
| **Anaconda** | Installation locale avec Python, Jupyter et des outils de science des données | Tu veux travailler hors ligne ou gérer plusieurs environnements localement |
| **VS Code + Python/Jupyter** | Éditeur de code, notebooks et fichiers d’un même projet dans un dossier | Tu veux organiser ton portfolio et travailler sur plusieurs types de fichiers |

Google présente Colab comme un service Jupyter hébergé qui ne demande pas de configuration locale. Les notebooks Colab peuvent être conservés dans Google Drive ou chargés depuis GitHub. [web:209][web:213]

Anaconda Distribution fournit Python et plusieurs outils de data science, dont Jupyter ; Miniconda est une installation plus légère qui permet d’ajouter les paquets dont tu as besoin. [web:198][web:201][web:205]

### ✅ Conseil pour démarrer

Commence avec **Google Colab** si tu veux écrire tes premières cellules tout de suite. Choisis **Anaconda ou VS Code** si tu souhaites garder l’environnement sur ton ordinateur et organiser tes fichiers localement. Tu peux passer de l’un à l’autre plus tard : le format `.ipynb` est prévu pour les notebooks Jupyter.

## 3. Créer un notebook dans Google Colab

1. Connecte-toi à ton compte Google.
2. Ouvre [Google Colab](https://colab.research.google.com/).
3. Crée un nouveau notebook depuis le menu **File → New notebook** (ou l’option équivalente affichée dans l’interface).
4. Clique sur le nom du notebook pour le renommer, par exemple `Python_Data_Jour_01.ipynb`.
5. Vérifie que le notebook est enregistré dans Google Drive. Tu peux aussi télécharger une copie `.ipynb` depuis le menu **File**. Les notebooks Colab sont enregistrés dans Drive et peuvent être partagés comme d’autres documents Google. [web:208][web:213]

## 4. Créer un notebook dans VS Code

1. Installe Python sur ton ordinateur ou installe Anaconda/Miniconda.
2. Dans VS Code, installe les extensions **Python** et **Jupyter**.
3. Ouvre ton dossier de cours, par exemple `02_Python_Data`.
4. Crée un nouveau fichier avec l’extension `.ipynb`, par exemple `2026-11-02_Python_Data_Jour_01.ipynb`.
5. Choisis un **kernel** Python dans le coin supérieur droit du notebook.
6. Ajoute une cellule, écris du code, puis lance-la avec le bouton ▶ ou **Shift+Enter**.

VS Code permet de créer et d’exécuter des notebooks Jupyter, mais il faut sélectionner un environnement ou un kernel Python compatible. [web:156][web:158][web:161]

## 5. Créer un notebook avec Anaconda

1. Télécharge l’installateur correspondant à ton système d’exploitation depuis la page officielle d’Anaconda.
2. Installe Anaconda Distribution ou Miniconda en suivant les consignes de l’installateur.
3. Ouvre JupyterLab depuis Anaconda Navigator, ou lance Jupyter depuis l’environnement installé.
4. Crée un nouveau notebook Python et enregistre-le sous `Python_Data_Jour_01.ipynb`.

Anaconda recommande de choisir l’installateur correspondant au système et à la méthode souhaitée ; sa distribution complète inclut plusieurs outils, tandis que Miniconda est minimale. [web:198][web:201]

## 6. Ton premier notebook

Un notebook alterne généralement **cellules Markdown** et **cellules de code**. Markdown sert aux titres, objectifs et explications ; une cellule de code exécute Python.

### Cellule Markdown — titre et objectif

```markdown
# Mon premier notebook Python

Aujourd’hui, je découvre l’environnement et j’exécute mes premières instructions.
```

### Cellule de code — afficher un message

```python
print("Bonjour, je commence Python pour la data !")
```

Clique sur ▶ ou appuie sur **Shift+Enter**. Le résultat attendu est :

```text
Bonjour, je commence Python pour la data !
```

### Cellule de code — calcul simple

```python
heures_etude = 2
jours = 5
print("Heures prévues cette semaine :", heures_etude * jours)
```

Résultat attendu : `Heures prévues cette semaine : 10`.

## 7. Vérifier et enregistrer

Avant de terminer, vérifie que :

- le notebook porte un nom explicite ;
- les cellules s’exécutent sans erreur ;
- les résultats apparaissent sous les cellules de code ;
- le fichier est bien enregistré dans Drive (Colab) ou dans ton dossier de cours (local) ;
- tu peux fermer puis rouvrir le notebook sans perdre ton travail.

## ⚠️ Erreurs fréquentes

- **Aucun kernel sélectionné dans VS Code :** sélectionne un environnement Python dans le menu du notebook.
- **Le code ne s’exécute pas :** vérifie que tu as sélectionné une cellule de code et non une cellule Markdown.
- **Le fichier n’est pas enregistré où tu pensais :** vérifie le dossier ouvert ou l’emplacement Drive.
- **Tu utilises plusieurs environnements Python :** assure-toi que le kernel choisi contient les bibliothèques nécessaires.

## ✍️ Exercice pratique

Dans ton nouveau notebook :

1. ajoute un titre Markdown ;
2. écris une courte phrase sur ton objectif d’apprentissage ;
3. exécute `print("Mon premier notebook fonctionne !")` ;
4. crée deux variables `nom` et `ville`, puis affiche une phrase avec ces informations ;
5. enregistre, ferme et rouvre le notebook.

Exemple :

```python
nom = "Omar"
ville = "Genève"
print(f"{nom} apprend Python à {ville}.")
```

## 📝 Mon bilan

**Environnement choisi :** ⬜ Google Colab  ⬜ Anaconda/Jupyter  ⬜ VS Code  
**Nom du notebook :** __________________________________________  
**Ce que j’ai réussi à faire :** _________________________________  
**Difficulté rencontrée :** _____________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources officielles

- [Google Colab — présentation et notebooks](https://developers.google.com/colab)
- [Installer conda (Miniconda ou Anaconda Distribution)](https://docs.conda.io/projects/conda/en/stable/user-guide/install/index.html)
- [Installation d’Anaconda Distribution](https://www.anaconda.com/docs/getting-started/installation)
- [Notebooks Jupyter dans VS Code](https://code.visualstudio.com/docs/datascience/jupyter-notebooks)

> **À retenir :** Google Colab permet de commencer dans le navigateur sans installation locale ; Anaconda et VS Code permettent de travailler localement. Dans les trois cas, crée un notebook `.ipynb`, ajoute du texte et du code, exécute les cellules et vérifie où ton travail est enregistré.
