<!--
  Fichier : Jour3_Chatbots_IA_Cle_API_Environnement.md
  Cours   : Chatbots et assistants IA — Jour 3 : créer un compte, générer une clé API et la stocker en variable d’environnement
  Durée   : 45 à 75 minutes
  Mode    : adapté à l’aperçu sombre de VS Code
-->

<div style="background:#2e1065; border-left:8px solid #ba68c8; padding:16px 20px; border-radius:10px; color:#f3e5f5;">
  <h1 style="color:#ce93d8; margin:0;">🤖 Chatbots et assistants IA — Jour 3</h1>
  <p style="margin:8px 0 0; color:#f3e5f5;"><b>Thème :</b> créer un compte, générer une clé API et la stocker en variable d’environnement.</p>
</div>

<br>

<div style="background:#1b3a1f; border:1px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>🎯 Objectif :</b> créer un compte OpenAI, générer une clé API, la stocker en variable d’environnement et vérifier qu’elle est accessible depuis Python.</p>
</div>

---

## 🎯 À la fin du cours, tu sauras

- <span style="color:#81c784;"><b>✅ créer</b></span> un compte OpenAI ;
- <span style="color:#81c784;"><b>✅ générer</b></span> une clé API depuis le dashboard ;
- <span style="color:#81c784;"><b>✅ stocker</b></span> la clé en variable d’environnement (Windows, macOS/Linux, Colab) ;
- <span style="color:#81c784;"><b>✅ vérifier</b></span> que la clé est accessible depuis Python ;
- <span style="color:#81c784;"><b>✅ appliquer</b></span> les bonnes pratiques de sécurité.

---

## 1. Qu’est-ce qu’une clé API ?

Une **clé API** est un code unique qui identifie tes requêtes auprès d’un service (ici OpenAI). Elle permet à ton application d’accéder aux modèles et fonctionnalités de l’API. [web:507][web:515]

> ⚠️ **Ne partage jamais ta clé API** et ne la publie pas dans un dépôt GitHub public. [web:519]

## 2. Créer un compte OpenAI

1. Va sur [platform.openai.com](https://platform.openai.com/).
2. Clique sur **Sign up** (ou **Get started**).
3. Crée un compte avec ton e-mail ou via Google/Microsoft.
4. Vérifie ton e-mail si demandé.
5. Connecte-toi au dashboard.

## 3. Générer une clé API

1. Dans le dashboard, va dans **API keys** (ou **Settings → API keys**).
2. Clique sur **Create new secret key**.
3. Donne un nom à la clé, par exemple `chatbot-formation`.
4. Choisis les permissions si proposées (par défaut **All** pour débuter).
5. Clique sur **Create secret key**.
6. **Copie immédiatement la clé** : elle ne sera plus affichée après. [web:516][web:517][web:518]

> [!WARNING]
> La clé complète n’est affichée qu’une seule fois. Si tu la perds, tu devras en créer une nouvelle. [web:516][web:517]

## 4. Stocker la clé en variable d’environnement

Une **variable d’environnement** est une variable définie au niveau du système d’exploitation, accessible depuis ton application sans être écrite dans le code. OpenAI recommande fortement cette pratique pour éviter d’exposer la clé dans le code ou les dépôts publics. [web:510][web:513][web:514]

### A. Windows (PowerShell)

```powershell
setx OPENAI_API_KEY "ta_cle_api_ici"
```

Puis **ferme et rouvre PowerShell** pour que la variable soit prise en compte. Vérifie avec :

```powershell
echo $env:OPENAI_API_KEY
```

### B. macOS / Linux (bash ou zsh)

```bash
echo "export OPENAI_API_KEY='ta_cle_api_ici'" >> ~/.zshrc
source ~/.zshrc
echo $OPENAI_API_KEY
```

(ou `~/.bashrc` selon ton shell)

### C. Google Colab

Dans Colab, utilise le panneau **Secrets** (icône 🔑 à gauche) :

1. Clique sur l’icône 🔑 dans la barre latérale gauche.
2. Clique sur **Add a new secret**.
3. Nom : `OPENAI_API_KEY`
4. Valeur : ta clé API
5. Active **Notebook access**.

Puis dans une cellule :

```python
from google.colab import userdata
import os

os.environ["OPENAI_API_KEY"] = userdata.get('OPENAI_API_KEY')
```

## 5. Vérifier depuis Python

```python
import os

api_key = os.environ.get("OPENAI_API_KEY")

if api_key:
    print("Clé API trouvée.")
else:
    print("Clé API non trouvée.")
```

Si tu vois **Clé API trouvée.**, c’est bon. Sinon, vérifie que la variable est bien définie et que le terminal/notebook a été redémarré.

## 6. Bonnes pratiques de sécurité

- **Ne mets jamais la clé dans le code** ou dans un fichier `.py`/`.ipynb` versionné.
- **Ne la publie pas** sur GitHub, même dans un dépôt privé si tu n’es pas sûr.
- **Utilise une date d’expiration** si proposée lors de la création de la clé. [web:510][web:513]
- **Fais une rotation régulière** : crée une nouvelle clé, mets-la à jour dans tes applications, puis révoque l’ancienne. [web:510][web:513]
- **Utilise un gestionnaire de secrets** en production (Docker secrets, AWS Secrets Manager, etc.).

## 7. Erreurs fréquentes

<div style="background:#4e1c1c; border-left:6px solid #ef5350; padding:12px 16px; border-radius:8px; color:#ffebee;">
  <p style="margin:0;"><b>⚠️ Attention :</b> si tu perds la clé, tu ne pourras pas la récupérer ; crée-en une nouvelle.</p>
</div>

- **Clé non trouvée en Python** : variable non définie ou terminal/notebook non redémarré.
- **Clé exposée dans le code** : révoque immédiatement la clé et crée-en une nouvelle.
- **Mauvais nom de variable** : OpenAI recommande `OPENAI_API_KEY` comme nom standard. [web:513][web:514]
- **Espace ou guillemets en trop** : vérifie la syntaxe exacte de la commande.

## ✍️ Exercices

### Exercice 1 — créer et stocker

1. Crée un compte OpenAI.
2. Génère une clé API.
3. Stocke-la en variable d’environnement selon ton système.
4. Vérifie avec `echo` ou depuis Python.

### Exercice 2 — vérifier depuis Python

Écris un petit script qui affiche si la clé est trouvée ou non.

### Corrigé indicatif

<details>
<summary>Afficher un exemple</summary>

```python
import os

api_key = os.environ.get("OPENAI_API_KEY")
print("Clé trouvée." if api_key else "Clé non trouvée.")
```

</details>

## ✅ Vérification de compréhension

- [ ] Je sais créer un compte OpenAI.
- [ ] Je sais générer une clé API.
- [ ] Je sais stocker la clé en variable d’environnement.
- [ ] Je sais vérifier depuis Python.
- [ ] Je connais les bonnes pratiques de sécurité.

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**Ma méthode de stockage :** ____________________________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources officielles

- [OpenAI — API Overview et création de clés](https://platform.openai.com/docs/api-reference)
- [OpenAI — Developer quickstart : créer et exporter une clé](https://platform.openai.com/docs/quickstart)
- [OpenAI — Best Practices for API Key Safety](https://help.openai.com/en/articles/5112595-best-practices-for-api-key-safety)
- [OpenAI — Où trouver ma clé API ?](https://help.openai.com/en/articles/4936850-where-do-i-find-my-openai-api-key)

<div style="background:#1b3a1f; border-left:6px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>✅ À retenir en une phrase :</b> crée la clé dans le dashboard OpenAI, stocke-la en variable d’environnement (jamais dans le code), et vérifie son accès depuis Python avec <code>os.environ.get()</code>.</p>
</div>
