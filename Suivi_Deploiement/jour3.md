<!--
  Fichier : Jour3_Deploiement_HTTP_Methodes_Statuts_Headers_Cookies_TLS.md
  Cours   : Déploiement — Jour 3 : méthodes, statuts, en-têtes, cookies et TLS
  Durée   : 60 à 90 minutes
  Mode    : adapté à l’aperçu sombre de VS Code
-->

<div style="background:#0d1b2a; border-left:8px solid #4fc3f7; padding:16px 20px; border-radius:10px; color:#e3f2fd;">
  <h1 style="color:#4fc3f7; margin:0;">🌐 Déploiement — Jour 3</h1>
  <p style="margin:8px 0 0; color:#e3f2fd;"><b>Thème :</b> comprendre les méthodes HTTP, les statuts, les en-têtes, les cookies et TLS.</p>
</div>

<br>

<div style="background:#1b3a1f; border:1px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>🎯 Objectif :</b> comprendre comment un navigateur et un serveur échangent des informations via HTTP/HTTPS.</p>
</div>

---

## 🎯 À la fin du cours, tu sauras

- <span style="color:#81c784;"><b>✅ distinguer</b></span> les méthodes HTTP (GET, POST, PUT, DELETE, PATCH) ;
- <span style="color:#81c784;"><b>✅ interpréter</b></span> les codes de statut (200, 301, 404, 500…) ;
- <span style="color:#81c784;"><b>✅ comprendre</b></span> le rôle des en-têtes HTTP ;
- <span style="color:#81c784;"><b>✅ expliquer</b></span> ce qu’est un cookie et son utilité ;
- <span style="color:#81c784;"><b>✅ comprendre</b></span> le rôle de TLS dans HTTPS.

---

## 1. HTTP : le langage du web

**HTTP** (*HyperText Transfer Protocol*) est le protocole utilisé par les navigateurs et les serveurs pour échanger des informations. Il fonctionne selon un modèle **client-serveur** : le client (navigateur) envoie une requête, le serveur renvoie une réponse. [web:524][web:527]

HTTP est un protocole **sans état** (*stateless*) : par défaut, le serveur ne garde pas de mémoire entre deux requêtes. Les cookies permettent d’ajouter un état à certaines interactions. [web:524]

## 2. Méthodes HTTP

Les **méthodes HTTP** indiquent l’action souhaitée sur une ressource. [web:532]

| Méthode | Rôle | Exemple |
|---|---|---|
| `GET` | Récupérer une ressource | Charger une page web |
| `POST` | Envoyer des données au serveur | Soumettre un formulaire |
| `PUT` | Remplacer une ressource existante | Mettre à jour un profil complet |
| `PATCH` | Modifier partiellement une ressource | Changer seulement l’e-mail |
| `DELETE` | Supprimer une ressource | Supprimer un compte |
| `HEAD` | Comme GET mais sans le corps de la réponse | Vérifier qu’une ressource existe |
| `OPTIONS` | Décrire les options de communication | Vérifier les méthodes autorisées |

> [!NOTE]
> `GET` ne doit pas modifier de données côté serveur ; `POST`, `PUT`, `PATCH` et `DELETE` peuvent avoir des effets de bord. [web:532]

## 3. Codes de statut HTTP

Les **codes de statut** sont des nombres à 3 chiffres qui indiquent le résultat d’une requête. Ils sont regroupés en 5 classes. [web:523][web:531]

| Classe | Signification | Exemples |
|---|---|---|
| `1xx` | Informationnel | `100 Continue` |
| `2xx` | Succès | `200 OK`, `201 Created`, `204 No Content` |
| `3xx` | Redirection | `301 Moved Permanently`, `302 Found` |
| `4xx` | Erreur client | `400 Bad Request`, `401 Unauthorized`, `403 Forbidden`, `404 Not Found` |
| `5xx` | Erreur serveur | `500 Internal Server Error`, `502 Bad Gateway`, `503 Service Unavailable` |

### Codes à connaître absolument

- `200 OK` : requête réussie.
- `201 Created` : ressource créée avec succès.
- `301` : redirection permanente.
- `400` : requête malformée.
- `401` : non authentifié.
- `403` : accès refusé.
- `404` : ressource introuvable.
- `500` : erreur interne du serveur.

## 4. En-têtes HTTP

Les **en-têtes** (*headers*) sont des métadonnées envoyées avec la requête ou la réponse. Ils décrivent le contenu, les préférences, la sécurité, etc. [web:527][web:529]

### En-têtes courants côté requête

| En-tête | Rôle | Exemple |
|---|---|---|
| `Host` | Nom du serveur demandé | `Host: exemple.com` |
| `User-Agent` | Informations sur le navigateur | `User-Agent: Mozilla/5.0...` |
| `Accept` | Formats acceptés | `Accept: text/html` |
| `Content-Type` | Type de contenu envoyé | `Content-Type: application/json` |
| `Authorization` | Informations d’authentification | `Authorization: Bearer <token>` |
| `Cookie` | Cookies envoyés au serveur | `Cookie: session=abc123` |

### En-têtes courants côté réponse

| En-tête | Rôle | Exemple |
|---|---|---|
| `Content-Type` | Type de contenu renvoyé | `Content-Type: text/html` |
| `Content-Length` | Taille du corps | `Content-Length: 1024` |
| `Set-Cookie` | Envoyer un cookie au client | `Set-Cookie: session=abc123` |
| `Cache-Control` | Politique de cache | `Cache-Control: no-cache` |
| `Strict-Transport-Security` | Forcer HTTPS | `Strict-Transport-Security: max-age=31536000` |

## 5. Cookies : ajouter un état

Un **cookie** est une petite donnée envoyée par le serveur au navigateur via l’en-tête `Set-Cookie`. Le navigateur le stocke et le renvoie au serveur lors des requêtes suivantes via l’en-tête `Cookie`. [web:524][web:528]

### À quoi servent les cookies ?

- Maintenir une session connectée.
- Mémoriser des préférences.
- Suivre une navigation (avec consentement).

### Exemple

```text
Réponse du serveur :
Set-Cookie: session=abc123; HttpOnly; Secure

Requête suivante du navigateur :
Cookie: session=abc123
```

> [!WARNING]
> Les cookies peuvent contenir des informations sensibles. Utilise toujours `Secure` (HTTPS uniquement) et `HttpOnly` (inaccessible en JavaScript) pour les cookies de session.

## 6. TLS et HTTPS

**TLS** (*Transport Layer Security*) est le protocole qui chiffre les communications entre un client et un serveur. **HTTPS** est HTTP protégé par TLS. [web:525][web:530]

### Les 3 garanties de TLS

| Garantie | Rôle |
|---|---|
| **Chiffrement** | Les données ne peuvent pas être lues par un attaquant pendant le transit. |
| **Intégrité** | Les données ne peuvent pas être modifiées sans détection. |
| **Authentification** | Le client vérifie l’identité du serveur via son certificat. [web:525] |

### Fonctionnement simplifié

1. Le client se connecte au serveur sur le port 443.
2. Le serveur présente son certificat.
3. Le client vérifie le certificat.
4. Ils échangent des clés pour établir une session chiffrée.
5. Toutes les données HTTP sont ensuite chiffrées. [web:525]

> [!TIP]
> Vérifie toujours que l’URL commence par `https://` avant d’entrer des informations sensibles.

## 7. Exemple complet

Quand tu te connectes à un site :

1. Le navigateur envoie `GET https://exemple.com/login`.
2. Le serveur répond `200 OK` avec la page de connexion.
3. Tu envoies `POST /login` avec tes identifiants.
4. Le serveur répond `302 Found` avec un `Set-Cookie: session=...`.
5. Le navigateur stocke le cookie et le renvoie à chaque requête suivante.
6. Toutes les communications sont chiffrées via TLS (HTTPS).

## 8. Erreurs fréquentes

<div style="background:#4e1c1c; border-left:6px solid #ef5350; padding:12px 16px; border-radius:8px; color:#ffebee;">
  <p style="margin:0;"><b>⚠️ Attention :</b> ne confonds pas HTTP et HTTPS.</p>
</div>

- **HTTP** : non chiffré, port 80 par défaut.
- **HTTPS** : chiffré avec TLS, port 443 par défaut.
- **401 vs 403** : 401 = non authentifié ; 403 = authentifié mais accès refusé.
- **Cookie sans `Secure`** : peut être envoyé en HTTP, risque de fuite.

## ✍️ Exercices

### Exercice 1 — associer méthode et action

Associe chaque méthode à son action :

- GET : ________________________________________________
- POST : _______________________________________________
- PUT : ________________________________________________
- DELETE : _____________________________________________
- PATCH : ______________________________________________

### Exercice 2 — interpréter les statuts

Indique la signification :

- `200` : ______________
- `301` : ______________
- `404` : ______________
- `500` : ______________
- `403` : ______________

### Exercice 3 — cookies et TLS

1. Quel en-tête le serveur utilise-t-il pour envoyer un cookie ?
2. Quel en-tête le navigateur utilise-t-il pour renvoyer un cookie ?
3. Quel protocole chiffre les communications HTTPS ?

### Corrigé

<details>
<summary>Afficher les réponses</summary>

**Exercice 1 :** GET = récupérer ; POST = créer/envoyer ; PUT = remplacer ; DELETE = supprimer ; PATCH = modifier partiellement.

**Exercice 2 :** 200 = OK ; 301 = redirection permanente ; 404 = introuvable ; 500 = erreur serveur ; 403 = accès refusé.

**Exercice 3 :**  
1. `Set-Cookie` ;  
2. `Cookie` ;  
3. TLS.

</details>

## ✅ Vérification de compréhension

- [ ] Je connais les méthodes HTTP principales.
- [ ] Je sais interpréter les codes de statut.
- [ ] Je comprends le rôle des en-têtes.
- [ ] Je sais ce qu’est un cookie et comment il fonctionne.
- [ ] Je comprends le rôle de TLS dans HTTPS.

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**La notion la plus utile retenue :** ____________________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources fiables

- [MDN — HTTP overview](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Overview)
- [MDN — HTTP methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods)
- [MDN — HTTP status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status)
- [MDN — HTTP headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers)
- [MDN — TLS](https://developer.mozilla.org/en-US/docs/Web/Security/Defenses/Transport_Layer_Security)

<div style="background:#1b3a1f; border-left:6px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>✅ À retenir en une phrase :</b> les méthodes HTTP indiquent l’action, les statuts le résultat, les en-têtes les métadonnées, les cookies l’état, et TLS le chiffrement dans HTTPS.</p>
</div>
