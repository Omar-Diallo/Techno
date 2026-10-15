<!--
  Fichier : Jour3_OpenWebUI_Configurer_Modele_LLM_Tester_Conversation.md
  Cours   : Open WebUI — Jour 3 : configurer un modèle LLM et tester une conversation
  Durée   : 45 à 75 minutes
  Mode    : adapté à l’aperçu sombre de VS Code
-->

<div style="background:#0f172a; border-left:8px solid #38bdf8; padding:16px 20px; border-radius:10px; color:#e0f2fe;">
  <h1 style="color:#38bdf8; margin:0;">🧠 Open WebUI — Jour 3</h1>
  <p style="margin:8px 0 0; color:#e0f2fe;"><b>Thème :</b> configurer un modèle LLM et tester une conversation.</p>
</div>

<br>

<div style="background:#1b3a1f; border:1px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>🎯 Objectif :</b> connecter un modèle LLM (Ollama local ou API OpenAI-compatible) à Open WebUI, le sélectionner et lancer une première conversation de test.</p>
</div>

---

## 🎯 À la fin du cours, tu sauras

- <span style="color:#81c784;"><b>✅ comprendre</b></span> qu’Open WebUI n’inclut pas de modèle LLM par défaut ;
- <span style="color:#81c784;"><b>✅ connecter</b></span> un modèle local via Ollama ;
- <span style="color:#81c784;"><b>✅ connecter</b></span> un modèle distant via une API OpenAI-compatible ;
- <span style="color:#81c784;"><b>✅ sélectionner</b></span> un modèle dans l’interface ;
- <span style="color:#81c784;"><b>✅ tester</b></span> une conversation et vérifier que le modèle répond.

---

## 1. Rappel : Open WebUI et les modèles

**Open WebUI** est une interface web pour interagir avec des modèles de langage (LLM). Elle ne fournit pas elle-même les modèles : elle se connecte à des fournisseurs comme **Ollama** (local) ou **OpenAI / OpenRouter / vLLM / LM Studio** (API compatible). [web:341][web:345][web:542]

> [!NOTE]
> Sans connexion à un fournisseur, Open WebUI ne pourra pas répondre : il faut d’abord ajouter une connexion. [web:341][web:536]

## 2. Option A — connecter un modèle local avec Ollama

Si tu as Ollama installé sur ta machine :

1. Ouvre Open WebUI dans ton navigateur.
2. Va dans **Settings → Admin → Connections**.
3. Sous **Manage Ollama API Connections**, vérifie que l’URL est :
   - `http://localhost:11434` si Open WebUI tourne en local ;
   - `http://host.docker.internal:11434` si Open WebUI tourne dans Docker. [web:341][web:543]
4. Clique sur **Manage** (icône de téléchargement) pour voir et gérer les modèles disponibles. [web:543]
5. Dans le sélecteur de modèle d’un nouveau chat, tape le nom d’un modèle (ex. `llama3`, `mistral`, `qwen2`) et confirme le téléchargement si proposé. [web:341][web:543]

### Vérifier qu’Ollama tourne

```bash
ollama list
```

Cette commande liste les modèles déjà téléchargés localement.

## 3. Option B — connecter un modèle via API (OpenAI-compatible)

Si tu utilises une clé API (OpenAI, OpenRouter, etc.) :

1. Va dans **Settings → Admin → Connections**.
2. Sous **Manage OpenAI API Connections**, clique sur **+** (Ajouter une connexion).
3. Renseigne :
   - **Base URL** : `https://api.openai.com/v1` (ou l’URL de ton fournisseur) ;
   - **API Key** : ta clé API.
4. Clique sur **Save**. [web:341][web:536][web:544][web:545]

### Exemple de configuration

| Champ | Valeur |
|---|---|
| Provider | `OpenAI` |
| Base URL | `https://api.openai.com/v1` |
| API Key | `sk-...` (ta clé) |

> [!WARNING]
> Ne partage jamais ta clé API et ne la publie pas dans un dépôt public.

## 4. Sélectionner un modèle

1. Crée un nouveau chat.
2. En haut de la zone de saisie, clique sur le **sélecteur de modèle**.
3. Choisis le modèle que tu viens de connecter.
4. Si tu veux le définir par défaut, va dans **Settings → Admin → Models**, trouve le modèle, clique sur **⋯** puis **Set as Selected Model** ou **Set as Pinned Model**. [web:537]

## 5. Tester une conversation

1. Dans le chat, tape un message simple, par exemple :

```text
Bonjour, présente-toi en une phrase.
```

2. Envoie le message.
3. Vérifie que le modèle répond.
4. Pose une deuxième question pour tester la continuité :

```text
Peux-tu reformuler ta réponse plus simplement ?
```

5. Si le modèle répond correctement aux deux messages, la configuration est validée. [web:536]

## 6. Personnaliser le modèle (optionnel)

Dans **Workspace → Models**, tu peux créer un **preset** : choisir un modèle de base, ajouter un **system prompt**, des connaissances, des outils ou des paramètres spécifiques. [web:537][web:540]

### Exemple de system prompt

```text
Tu es un assistant pédagogique. Réponds de façon simple, claire et structurée.
```

## 7. Erreurs fréquentes

<div style="background:#4e1c1c; border-left:6px solid #ef5350; padding:12px 16px; border-radius:8px; color:#ffebee;">
  <p style="margin:0;"><b>⚠️ Attention :</b> si aucun modèle n’apparaît, vérifie d’abord la connexion au fournisseur.</p>
</div>

- **Aucun modèle dans le sélecteur** : connexion Ollama ou API mal configurée.
- **Erreur de connexion Ollama** : mauvaise URL (localhost vs host.docker.internal).
- **Erreur 401 / clé invalide** : vérifie la clé API.
- **Modèle ne répond pas** : vérifie que le modèle est bien téléchargé (Ollama) ou disponible côté fournisseur.

## ✍️ Exercices

### Exercice 1 — connecter un modèle

1. Choisis Ollama ou une API OpenAI-compatible.
2. Ajoute la connexion dans **Settings → Admin → Connections**.
3. Vérifie que le modèle apparaît dans le sélecteur.

### Exercice 2 — tester une conversation

1. Crée un nouveau chat.
2. Sélectionne ton modèle.
3. Envoie : `Bonjour, présente-toi en une phrase.`
4. Envoie une deuxième question pour tester la continuité.

### Exercice 3 — personnaliser (bonus)

1. Va dans **Workspace → Models**.
2. Crée un preset avec un system prompt simple.
3. Teste-le dans un nouveau chat.

### Corrigé indicatif

<details>
<summary>Afficher un exemple de test réussi</summary>

```text
Utilisateur : Bonjour, présente-toi en une phrase.
Modèle : Bonjour ! Je suis un assistant IA conçu pour répondre à vos questions et vous aider dans vos tâches.

Utilisateur : Peux-tu reformuler plus simplement ?
Modèle : Bien sûr : je suis une IA qui répond à vos questions.
```

</details>

## ✅ Vérification de compréhension

- [ ] Je sais qu’Open WebUI a besoin d’une connexion à un fournisseur.
- [ ] Je sais connecter Ollama ou une API OpenAI-compatible.
- [ ] Je sais sélectionner un modèle dans l’interface.
- [ ] Je sais tester une conversation.
- [ ] Je sais créer un preset avec un system prompt (bonus).

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**Modèle connecté :** ___________________________________________  
**Test réussi :** ⬜ Oui  ⬜ Non  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources officielles

- [Open WebUI — Quick Start](https://docs.openwebui.com/getting-started/quick-start/)
- [Open WebUI — Connect a Provider](https://docs.openwebui.com/getting-started/quick-start/connect-a-provider/)
- [Open WebUI — Connect a model (API keys and Ollama)](https://docs.openwebui.com/ecosystem/computer/ai/connect-a-model/)
- [Open WebUI — Models workspace](https://docs.openwebui.com/features/workspace/models/)
- [Open WebUI — Chat features](https://docs.openwebui.com/features/chat-conversations/chat-features/)

<div style="background:#1b3a1f; border-left:6px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>✅ À retenir en une phrase :</b> connecte d’abord un fournisseur (Ollama local ou API OpenAI-compatible) dans <b>Settings → Admin → Connections</b>, sélectionne le modèle dans le sélecteur, puis teste avec un message simple.</p>
</div>
