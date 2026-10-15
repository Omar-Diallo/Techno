<!--
  Fichier : Jour2_Python_Data_Types_Variables_Affichage.md
  Cours   : Python pour la data — types de base et affichage
  Durée   : 60 à 90 minutes
-->

# 🐍 Python pour la data — Jour 2

> **Thème :** utiliser `int`, `float`, `str`, `bool` et afficher des résultats.
>
> **Objectif :** créer des variables, reconnaître leurs types et afficher des résultats propres avec `print()` et les f-strings.

---

## 🎯 À la fin du cours, tu sauras

- créer des variables avec `int`, `float`, `str` et `bool` ;
- vérifier le type d’une valeur avec `type()` ;
- utiliser `print()` pour afficher un résultat ;
- écrire des phrases avec des f-strings ;
- éviter les erreurs courantes de types.

## 1. Qu’est-ce qu’une variable ?

Une **variable** est un nom qui permet de conserver une valeur dans le programme. On crée une variable avec le signe `=`.

```python
age = 25
```

Ici :

- `age` est le nom de la variable ;
- `=` signifie « reçoit la valeur » ;
- `25` est la valeur stockée.

Python reconnaît automatiquement le type de la valeur : tu n’as pas besoin de déclarer le type avant. [web:375][web:378]

## 2. Les quatre types à connaître

| Type | Nom complet | Exemples | Usage courant |
|---|---|---|---|
| `int` | Nombre entier | `25`, `-8`, `0` | Âge, quantité, année |
| `float` | Nombre décimal | `3.14`, `-2.5`, `0.75` | Prix, taux, mesure |
| `str` | Chaîne de caractères | `"Genève"`, `'Python'` | Nom, texte, message |
| `bool` | Booléen | `True`, `False` | Vrai/faux, état, condition |

En Python, les nombres entiers sont de type `int`, les nombres avec une partie décimale sont de type `float`, le texte est de type `str`, et les valeurs de vérité sont `True` ou `False`. [web:374][web:375]

## 3. Créer des variables

```python
age = 25
prix = 12.50
ville = "Genève"
etudiant = True
```

Tu peux vérifier les types avec `type()` :

```python
print(type(age))
print(type(prix))
print(type(ville))
print(type(etudiant))
```

Résultat attendu :

```text
<class 'int'>
<class 'float'>
<class 'str'>
<class 'bool'>
```

## 4. Afficher avec `print()`

La fonction `print()` affiche une valeur ou un message à l’écran.

```python
print("Bonjour")
print(age)
print(prix)
```

Résultat :

```text
Bonjour
25
12.5
```

Tu peux afficher plusieurs valeurs séparées par des virgules :

```python
print("J’ai", age, "ans et je vis à", ville)
```

Résultat :

```text
J’ai 25 ans et je vis à Genève
```

## 5. Les f-strings : afficher proprement

Une **f-string** est une chaîne de caractères précédée de la lettre `f`. Elle permet d’insérer directement la valeur d’une variable entre accolades `{}`. [web:376]

```python
nom = "Omar"
ville = "Genève"
age = 25

print(f"Je m’appelle {nom}, j’ai {age} ans et je vis à {ville}.")
```

Résultat :

```text
Je m’appelle Omar, j’ai 25 ans et je vis à Genève.
```

Les f-strings sont utiles pour créer des messages clairs sans mélanger trop de virgules.

## 6. Faire des calculs

Avec les nombres, tu peux utiliser :

```python
a = 10
b = 3

print(a + b)   # addition
print(a - b)   # soustraction
print(a * b)   # multiplication
print(a / b)   # division
```

Résultat :

```text
13
7
30
3.3333333333333335
```

En Python, la division avec `/` renvoie toujours un `float`, même si le résultat est un nombre entier. [web:375]

## 7. Attention aux erreurs de type

Tu ne peux pas additionner directement un texte et un nombre :

```python
age = 25

# Cette ligne provoquera une erreur :
# print("J’ai " + age + " ans")
```

Erreur possible :

```text
TypeError: can only concatenate str (not "int") to str
```

Utilise plutôt une f-string :

```python
print(f"J’ai {age} ans")
```

## 8. Convertir un type

Tu peux convertir une valeur avec `int()`, `float()`, `str()` ou `bool()`.

```python
texte_age = "25"
age = int(texte_age)

prix_texte = "12.50"
prix = float(prix_texte)

nombre = 25
texte = str(nombre)

print(age, type(age))
print(prix, type(prix))
print(texte, type(texte))
```

Résultat :

```text
25 <class 'int'>
12.5 <class 'float'>
25 <class 'str'>
```

## 9. Exemple complet

```python
nom = "Omar"
ville = "Genève"
age = 25
prix_transport = 2.50
etudiant = True

print(f"Bonjour {nom}.")
print(f"Tu vis à {ville} et tu as {age} ans.")
print(f"Le prix d’un ticket est de {prix_transport} CHF.")
print(f"Statut étudiant : {etudiant}")
```

Résultat :

```text
Bonjour Omar.
Tu vis à Genève et tu as 25 ans.
Le prix d’un ticket est de 2.5 CHF.
Statut étudiant : True
```

## ✍️ Exercices

### Exercice 1 — créer des variables

Crée quatre variables :

- `prenom` : ton prénom ;
- `ville` : ta ville ;
- `age` : ton âge ;
- `taille` : ta taille en mètres.

Puis affiche une phrase avec une f-string.

### Exercice 2 — types

Pour chaque valeur, indique le type :

- `42` : ______________
- `3.14` : ____________
- `"Python"` : ________
- `False` : ___________

### Exercice 3 — corriger le code

Ce code contient une erreur :

```python
age = 25
print("J’ai " + age + " ans")
```

Corrige-le avec une f-string.

### Corrigé

<details>
<summary>Afficher les réponses</summary>

**Exercice 2 :** `42` est un `int` ; `3.14` est un `float` ; `"Python"` est un `str` ; `False` est un `bool`.

**Exercice 3 :**

```python
age = 25
print(f"J’ai {age} ans")
```

</details>

## ✅ Vérification de compréhension

- [ ] Je peux créer une variable avec `=`.
- [ ] Je connais la différence entre `int`, `float`, `str` et `bool`.
- [ ] Je peux vérifier un type avec `type()`.
- [ ] Je sais utiliser `print()` et une f-string.
- [ ] Je sais éviter l’erreur entre texte et nombre.

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**La notion la plus utile retenue :** ____________________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources officielles

- [Python — Types intégrés : int, float, str et bool](https://docs.python.org/3/library/stdtypes.html)
- [Python — Introduction aux types numériques et variables](https://docs.python.org/3/tutorial/introduction.html)
- [Python — Entrées et sorties, f-strings](https://docs.python.org/3/tutorial/inputoutput.html)

> **À retenir en une phrase :** `int` stocke un entier, `float` un nombre décimal, `str` du texte et `bool` une valeur vrai/faux ; utilise `print()` et les f-strings pour afficher des résultats clairs. [web:374][web:375][web:376]
