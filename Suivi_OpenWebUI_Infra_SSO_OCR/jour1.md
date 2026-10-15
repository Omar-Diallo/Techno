<!--
  Fichier : Jour1_OpenWebUI_Architecture_CasUsage.md
  Cours   : OpenWebUI — comprendre les cas d’usage et l’architecture
  Durée   : 60 à 90 minutes
-->

# 🟢 OpenWebUI — Jour 1

> **Thème :** comprendre OpenWebUI, ses cas d’usage et son architecture.
>
> **Objectif :** savoir ce qu’est OpenWebUI, quels composants peuvent intervenir dans une installation et comment une question arrive jusqu’au modèle puis revient à l’utilisateur.

---

## 🎯 À la fin du cours, tu sauras

- expliquer ce qu’est OpenWebUI ;
- citer quelques cas d’usage pratiques ;
- reconnaître les principaux composants d’une architecture simple ;
- distinguer l’interface, le modèle, les documents et les outils ;
- décrire les limites et précautions de base.

## 1. Qu’est-ce qu’OpenWebUI ?

**OpenWebUI** est une interface web auto-hébergeable pour interagir avec des modèles d’intelligence artificielle. Elle peut se connecter à Ollama et à des API compatibles avec les formats d’API courants. Elle permet notamment de discuter avec des modèles, gérer des conversations, ajouter des fichiers, utiliser des bases de connaissances et connecter des outils. [web:332][web:324]

> **Important :** OpenWebUI est principalement l’interface et la plateforme qui relie l’utilisateur à des modèles et fonctions. Le modèle (par exemple Ollama ou un fournisseur d’API) peut être un composant distinct.

## 2. Cas d’usage

| Cas d’usage | Exemple |
|---|---|
| Assistant personnel ou de travail | Poser des questions, reformuler ou résumer du texte |
| Assistant documentaire | Interroger des PDF, guides ou procédures avec une base de connaissances (RAG) |
| Aide à la programmation | Demander une explication ou une proposition de code à un modèle connecté |
| Comparaison de modèles | Comparer les réponses de plusieurs modèles, si la configuration le permet |
| Assistant avec outils | Autoriser le modèle à utiliser des outils ou fonctions configurés |
| Interface privée d’équipe | Donner à plusieurs utilisateurs une interface contrôlée vers des modèles |

OpenWebUI propose notamment la gestion des conversations, la connexion à différents fournisseurs, les fichiers et les bases de connaissances. Les fonctions disponibles dépendent de la version, des modèles connectés et de la configuration déployée. [web:324][web:330]

## 3. Architecture simple

Une installation de base peut être représentée ainsi :

```text
┌───────────────────┐
│ Utilisateur       │
│ navigateur web    │
└─────────┬─────────┘
          │ question / réponse
          ▼
┌───────────────────┐
│ OpenWebUI         │
│ interface +       │
│ gestion des chats │
└─────────┬─────────┘
          │ requête au modèle
          ▼
┌───────────────────┐       ┌───────────────────────┐
│ Fournisseur /     │──────▶│ Modèle IA             │
│ service de modèle │       │ local ou distant      │
└───────────────────┘       └───────────────────────┘

      Composants optionnels : fichiers/RAG, base de données,
      stockage, outils, authentification, proxy et observabilité.
```

### Rôle des composants

- **Utilisateur et navigateur** : affichent l’interface et envoient la question.
- **OpenWebUI** : gère l’interface, les conversations et certaines fonctions de plateforme.
- **Fournisseur de modèle** : service auquel OpenWebUI transmet les requêtes, par exemple Ollama ou une API compatible.
- **Modèle IA** : génère une réponse à partir de la demande et du contexte qui lui est transmis.
- **Base de connaissances** (facultative) : contient des documents que l’application peut rechercher pour fournir du contexte (RAG). OpenWebUI décrit un flux où les documents sont découpés, représentés sous forme de vecteurs et où des passages pertinents peuvent être récupérés pour répondre. [web:328][web:330]
- **Outils et fonctions** (facultatifs) : ajoutent des capacités, comme appeler un service ou transformer une requête. OpenWebUI distingue les outils utilisables par le modèle et les fonctions qui modifient le comportement de la plateforme. [web:328]
- **Stockage et base de données** : conservent les informations nécessaires à l’instance ; la configuration dépend de l’usage et de l’échelle.

## 4. Que se passe-t-il quand tu poses une question ?

1. Tu écris un message dans le navigateur.
2. OpenWebUI prépare la requête selon le modèle choisi, les instructions et le contexte disponible.
3. Si une base de connaissances ou un outil est configuré, des informations peuvent être recherchées ou des actions déclenchées selon les règles et autorisations.
4. Le fournisseur transmet la requête au modèle.
5. Le modèle produit une réponse.
6. OpenWebUI affiche la réponse et peut conserver la conversation selon sa configuration.

Cette description est volontairement simplifiée. Les chemins exacts dépendent du fournisseur, du modèle, des outils et des réglages utilisés.

## 5. Local, distant et auto-hébergement

- **Modèle local** : le modèle tourne sur une machine ou un serveur que tu contrôles, souvent via un service comme Ollama. Il faut vérifier les ressources matérielles et gérer les mises à jour.
- **Modèle distant** : la requête est envoyée à un fournisseur externe via une API. Il faut tenir compte des coûts, des règles de confidentialité et des conditions du fournisseur.
- **OpenWebUI auto-hébergé** : tu déploies l’interface sur ta propre infrastructure. Cela donne du contrôle sur le déploiement, mais tu dois assurer les mises à jour, les sauvegardes, l’accès et la sécurité.

La documentation présente OpenWebUI comme une plateforme auto-hébergeable et extensible, conçue pour fonctionner avec différents fournisseurs. « Auto-hébergé » ne signifie pas automatiquement que tout est hors ligne ou sécurisé : cela dépend du modèle, des connexions et de la configuration choisie. [web:332][web:338]

## 6. Exemple de cas d’usage : assistant de cours

Un étudiant charge des notes de cours et demande : « Explique-moi la différence entre TCP et UDP avec un exemple simple. »

- OpenWebUI fournit l’interface de chat.
- Une base documentaire peut fournir un passage pertinent des notes (RAG).
- Le modèle connecté formule une explication à partir de la question et du passage retrouvé.
- L’étudiant vérifie la réponse par rapport au cours.

Le RAG aide à fournir des informations issues de documents sélectionnés, mais ne garantit pas à lui seul que chaque réponse sera exacte. Il faut tester les réponses et vérifier les sources utilisées.

## 7. Précautions importantes

- **Confidentialité :** ne charge pas de documents personnels ou confidentiels sans autorisation et sans connaître où ils sont traités.
- **Clés API :** ne les partage pas et ne les place pas dans un dépôt GitHub public.
- **Accès :** si l’instance est accessible à d’autres personnes, configure l’authentification et les droits appropriés.
- **Mises à jour :** une instance auto-hébergée doit être maintenue et sauvegardée.
- **Réponses :** un modèle peut produire une réponse fausse ou incomplète ; vérifie les informations importantes.
- **Fonctions et outils :** n’active que ce que tu comprends et limite les permissions nécessaires.

## ✍️ Exercices

### Exercice 1 — identifier les composants

Pour un OpenWebUI connecté à Ollama et à un dossier de documents, complète :

- Interface utilisée par l’étudiant : ___________________________
- Fournisseur/service qui expose le modèle : ____________________
- Modèle qui génère la réponse : ______________________________
- Source de contexte documentaire : ___________________________

### Exercice 2 — dessiner ton architecture

Dessine ou écris les composants d’un assistant documentaire que tu aimerais tester. Indique :

1. qui utilise l’assistant ;
2. où OpenWebUI est exécuté ;
3. quel modèle est connecté ;
4. quels documents ou outils sont nécessaires ;
5. comment tu limites l’accès aux données.

### Corrigé indicatif

<details>
<summary>Afficher une réponse possible</summary>

- Interface : OpenWebUI dans le navigateur.
- Fournisseur/service : Ollama.
- Modèle : le modèle choisi dans Ollama.
- Contexte : documents ajoutés dans une base de connaissances OpenWebUI.

</details>

## ✅ Vérification de compréhension

- [ ] Je peux expliquer la différence entre OpenWebUI et le modèle IA.
- [ ] Je peux dessiner le trajet question → OpenWebUI → modèle → réponse.
- [ ] Je sais qu’une base documentaire et des outils sont optionnels.
- [ ] Je comprends qu’auto-hébergement ne garantit pas à lui seul la sécurité ou le fonctionnement hors ligne.
- [ ] Je connais au moins deux précautions : confidentialité, accès, sauvegardes, mises à jour ou clés API.

## 📝 Mon bilan

**Cas d’usage qui m’intéresse :** _________________________________  
**Composant que je comprends le mieux :** ________________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources officielles

- [Documentation OpenWebUI](https://docs.openwebui.com/)
- [Fonctionnalités OpenWebUI](https://docs.openwebui.com/features/)
- [Essentiels OpenWebUI : outils, fonctions et RAG](https://docs.openwebui.com/getting-started/essentials/)
- [Bases de connaissances et discussion documentaire](https://docs.openwebui.com/features/workspace/knowledge/)
- [FAQ OpenWebUI : déploiement et architecture](https://docs.openwebui.com/faq/)

> **À retenir :** OpenWebUI est l’interface et la plateforme ; un fournisseur donne accès au modèle, et des composants optionnels comme le RAG, les outils, le stockage et l’authentification complètent l’architecture. [web:324][web:328][web:332][web:334]
