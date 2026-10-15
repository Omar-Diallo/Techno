<!--
  Fichier : Jour3_Python_Data_Comparaisons_If_Elif_Else.md
  Cours   : Python pour la data — comparaisons, if, elif et else
  Durée   : 60 à 90 minutes
  Mode    : adapté à l’aperçu sombre de VS Code
-->

<div style="background:#0d1b2a; border-left:8px solid #4fc3f7; padding:16px 20px; border-radius:10px; color:#e3f2fd;">
  <h1 style="color:#4fc3f7; margin:0;">🐍 Python pour la data — Jour 3</h1>
  <p style="margin:8px 0 0; color:#e3f2fd;"><b>Thème :</b> utiliser les comparaisons, <code>if</code>, <code>elif</code> et <code>else</code>.</p>
</div>

<br>

<div style="background:#1b3a1f; border:1px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>🎯 Objectif :</b> prendre des décisions dans un programme selon des conditions.</p>
</div>

---

## 🎯 À la fin du cours, tu sauras

- <span style="color:#81c784;"><b>✅ comparer</b></span> des valeurs avec <code>==</code>, <code>!=</code>, <code>&gt;</code>, <code>&lt;</code>, <code>&gt;=</code>, <code>&lt;=</code> ;
- <span style="color:#81c784;"><b>✅ utiliser</b></span> <code>if</code> pour exécuter du code si une condition est vraie ;
- <span style="color:#81c784;"><b>✅ ajouter</b></span> <code>elif</code> pour plusieurs cas ;
- <span style="color:#81c784;"><b>✅ utiliser</b></span> <code>else</code> pour le cas par défaut ;
- <span style="color:#81c784;"><b>✅ éviter</b></span> les erreurs d’indentation et de syntaxe.

---

## 1. Les comparaisons

En Python, on compare des valeurs avec des opérateurs :

| Opérateur | Signification |
|---|---|
| `==` | égal à |
| `!=` | différent de |
| `>` | supérieur à |
| `<` | inférieur à |
| `>=` | supérieur ou égal |
| `<=` | inférieur ou égal |

Exemples :

```python
a = 10
b = 3

print(a == b)  # False
print(a != b)  # True
print(a > b)   # True
print(a < b)   # False
```

> [!NOTE]
> `=` sert à affecter une valeur ; `==` sert à comparer deux valeurs.

## 2. La structure if

La structure `if` exécute un bloc de code seulement si la condition est vraie.

```python
age = 20

if age >= 18:
    print("Tu es majeur.")
```

Résultat :

```text
Tu es majeur.
```

> [!TIP]
> En Python, l’indentation (les espaces au début de la ligne) est obligatoire pour définir le bloc de code.

## 3. Ajouter elif

`elif` signifie « sinon si ». Il permet de tester plusieurs conditions dans l’ordre.

```python
note = 14

if note >= 16:
    print("Très bien")
elif note >= 12:
    print("Bien")
elif note >= 10:
    print("Passable")
```

Résultat :

```text
Bien
```

Python teste les conditions de haut en bas et exécute le premier bloc vrai.

## 4. Ajouter else

`else` s’exécute si aucune condition précédente n’est vraie.

```python
note = 8

if note >= 10:
    print("Réussi")
else:
    print("Échoué")
```

Résultat :

```text
Échoué
```

## 5. Structure complète

```python
note = 14

if note >= 16:
    print("Très bien")
elif note >= 12:
    print("Bien")
elif note >= 10:
    print("Passable")
else:
    print("Échoué")
```

Résultat :

```text
Bien
```

## 6. Combiner des conditions

Tu peux combiner des conditions avec `and`, `or` et `not`.

```python
age = 20
ville = "Genève"

if age >= 18 and ville == "Genève":
    print("Majeur et à Genève")

if age < 18 or ville != "Genève":
    print("Condition alternative")
```

## 7. Exemple appliqué : statut d’une commande

```python
prix = 120
statut = "Livrée"

if statut == "Livrée":
    print("Commande livrée.")
elif statut == "En attente":
    print("Commande en attente.")
else:
    print("Statut inconnu.")
```

Résultat :

```text
Commande livrée.
```

## 8. Erreurs fréquentes

<div style="background:#4e1c1c; border-left:6px solid #ef5350; padding:12px 16px; border-radius:8px; color:#ffebee;">
  <p style="margin:0;"><b>⚠️ Attention :</b> l’indentation est obligatoire en Python.</p>
</div>

- **Oublier les deux-points** après `if`, `elif` ou `else` :

```python
# Incorrect
if age >= 18
    print("Majeur")

# Correct
if age >= 18:
    print("Majeur")
```

- **Confondre `=` et `==`** :

```python
# Incorrect pour comparer
if age = 18:
    print("Majeur")

# Correct
if age == 18:
    print("Majeur")
```

- **Mauvaise indentation** :

```python
# Incorrect
if age >= 18:
print("Majeur")

# Correct
if age >= 18:
    print("Majeur")
```

## ✍️ Exercices

### Exercice 1 — majeur ou mineur

Écris un programme qui affiche « Majeur » si l’âge est supérieur ou égal à 18, sinon « Mineur ».

### Exercice 2 — note

Écris un programme qui affiche :
- « Très bien » si la note est ≥ 16
- « Bien » si la note est ≥ 12
- « Passable » si la note est ≥ 10
- « Échoué » sinon

### Exercice 3 — statut

Écris un programme qui affiche le statut d’une commande selon la valeur de `statut`.

### Corrigé

<details>
<summary>Afficher les réponses</summary>

```python
# Exercice 1
age = 20
if age >= 18:
    print("Majeur")
else:
    print("Mineur")

# Exercice 2
note = 14
if note >= 16:
    print("Très bien")
elif note >= 12:
    print("Bien")
elif note >= 10:
    print("Passable")
else:
    print("Échoué")

# Exercice 3
statut = "Livrée"
if statut == "Livrée":
    print("Commande livrée.")
elif statut == "En attente":
    print("Commande en attente.")
else:
    print("Statut inconnu.")
```

</details>

## ✅ Vérification de compréhension

- [ ] Je connais les opérateurs de comparaison.
- [ ] Je sais utiliser `if`, `elif` et `else`.
- [ ] Je comprends l’importance de l’indentation.
- [ ] Je sais combiner des conditions avec `and`, `or`, `not`.

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**La structure la plus utile retenue :** _________________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources officielles

- [Python — Tutoriel officiel : conditions](https://docs.python.org/3/tutorial/controlflow.html)
- [Python — Comparaisons et booléens](https://docs.python.org/3/library/stdtypes.html)

<div style="background:#1b3a1f; border-left:6px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>✅ À retenir en une phrase :</b> les comparaisons produisent un booléen ; <code>if</code>, <code>elif</code> et <code>else</code> permettent d’exécuter du code selon les conditions, avec une indentation obligatoire.</p>
</div>
