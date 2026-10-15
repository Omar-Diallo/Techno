<!--
  Fichier : Jour2_OpenWebUI_Installation_Docker.md
  Cours   : OpenWebUI — installer avec Docker et accéder à l’interface
  Durée   : 45 à 75 minutes
-->

# 🟢 OpenWebUI — Jour 2 : installation avec Docker

> **Objectif :** lancer OpenWebUI dans un conteneur Docker, accéder à son interface dans le navigateur et créer ton compte administrateur.

---

## 🎯 À la fin du cours, tu sauras

- vérifier que Docker fonctionne ;
- lancer OpenWebUI avec une commande Docker ;
- comprendre le port, le volume et le nom du conteneur ;
- ouvrir l’interface dans le navigateur ;
- arrêter, redémarrer et supprimer le conteneur si nécessaire.

## 1. Prérequis

Avant de commencer, vérifie que :

- Docker Desktop est installé et démarré ;
- tu peux exécuter `docker --version` sans erreur ;
- Docker Desktop indique que le moteur est démarré ;
- tu as une connexion Internet pour télécharger l’image OpenWebUI.

Dans PowerShell, exécute :

```powershell
docker --version
docker info
```

Si `docker info` affiche une erreur de connexion au moteur, reviens d’abord à la résolution du problème de démarrage de Docker Desktop. OpenWebUI recommande Docker comme méthode de démarrage rapide et indique que Docker Desktop est le chemin le plus simple sous Windows. [web:341][web:345]

## 2. Commande officielle recommandée

Dans PowerShell, exécute :

```powershell
docker run -d `
  -p 3000:8080 `
  --add-host=host.docker.internal:host-gateway `
  -v open-webui:/app/backend/data `
  -e WEBUI_SECRET_KEY="change-moi-avec-une-longue-phrase-secrete" `
  --name open-webui `
  --restart always `
  ghcr.io/open-webui/open-webui:main
```

Cette commande correspond au déploiement Docker documenté par OpenWebUI. Elle publie l’interface sur le port 3000 de ton ordinateur et conserve les données dans un volume Docker nommé `open-webui`. [web:340][web:341]

> ⚠️ **Avant de lancer :** remplace `change-moi-avec-une-longue-phrase-secrete` par une phrase longue et unique. Ne partage pas cette clé et ne la publie pas sur GitHub.

## 3. Comprendre la commande

| Élément | Rôle |
|---|---|
| `docker run -d` | Lance le conteneur en arrière-plan. |
| `-p 3000:8080` | Publie le port 3000 de Windows vers le port 8080 du conteneur. |
| `--add-host=host.docker.internal:host-gateway` | Aide le conteneur à joindre des services exécutés sur ton ordinateur hôte. |
| `-v open-webui:/app/backend/data` | Conserve les données dans un volume nommé `open-webui`. |
| `-e WEBUI_SECRET_KEY=...` | Fournit une valeur secrète de configuration à l’application. |
| `--name open-webui` | Donne un nom simple au conteneur. |
| `--restart always` | Relance le conteneur automatiquement après un arrêt ou un redémarrage, selon la configuration Docker. |
| `ghcr.io/open-webui/open-webui:main` | Image officielle à télécharger depuis le registre GitHub. |

OpenWebUI indique que `-p 3000:8080` rend l’interface accessible sur le port 3000 de ta machine ; si le port 3000 est déjà utilisé, change le nombre de gauche. [web:341]

## 4. Vérifier le lancement

Après avoir exécuté la commande, Docker télécharge l’image si elle n’est pas déjà présente. Cela peut prendre quelques minutes selon ta connexion.

Vérifie ensuite que le conteneur tourne :

```powershell
docker ps
```

Tu dois voir une ligne contenant :

- le nom `open-webui` ;
- l’image `ghcr.io/open-webui/open-webui`;
- une correspondance de ports proche de `0.0.0.0:3000->8080/tcp`.

Pour voir les journaux du conteneur :

```powershell
docker logs -f open-webui
```

Appuie sur **Ctrl+C** pour arrêter l’affichage des journaux sans arrêter le conteneur.

## 5. Accéder à l’interface

Ouvre ton navigateur et va à :

```text
http://localhost:3000
```

La documentation OpenWebUI indique que l’interface est accessible à cette adresse après le démarrage du conteneur. [web:340][web:341]

À la première ouverture, crée le compte administrateur :

- choisis un nom ;
- utilise une adresse e-mail que tu contrôles ;
- choisis un mot de passe long et unique ;
- conserve ces informations dans un gestionnaire de mots de passe.

> ⚠️ **Ne mets pas de vraie clé API, de mot de passe personnel ou de document confidentiel dans une instance exposée à d’autres personnes.** Pour un usage local, garde l’accès limité à ton ordinateur.

## 6. Arrêter, redémarrer ou supprimer

| Action | Commande |
|---|---|
| Voir les conteneurs actifs | `docker ps` |
| Voir tous les conteneurs, y compris arrêtés | `docker ps -a` |
| Voir les journaux | `docker logs -f open-webui` |
| Arrêter le conteneur | `docker stop open-webui` |
| Redémarrer le conteneur | `docker start open-webui` |
| Supprimer le conteneur | `docker rm -f open-webui` |
| Supprimer aussi le volume de données | `docker volume rm open-webui` |

⚠️ La suppression du volume efface les données locales conservées dans `open-webui`, notamment les comptes et les données de l’application selon la configuration. Ne le supprime pas sans sauvegarde si tu veux conserver ton travail.

## 7. Problèmes fréquents

### Le port 3000 est déjà utilisé

Change le port de gauche, par exemple :

```powershell
-p 3001:8080
```

Puis ouvre :

```text
http://localhost:3000
```

La documentation OpenWebUI indique explicitement que le nombre de gauche peut être modifié si le port 3000 est pris. [web:341]

### Le conteneur ne démarre pas

Affiche les journaux :

```powershell
docker logs --tail 100 open-webui
```

Cherche un message d’erreur, par exemple un port déjà utilisé, un problème de téléchargement d’image ou une configuration invalide.

### Docker n’est pas démarré

Lance Docker Desktop, attends que le moteur soit démarré, puis réessaie. OpenWebUI indique que Docker Desktop doit être ouvert et fonctionnel avant de lancer le conteneur. [web:341][web:342]

### Tu as supprimé le conteneur

Le volume `open-webui` peut conserver les données si tu ne l’as pas supprimé. Tu peux recréer le conteneur avec la même commande et le même volume.

## ✍️ Exercice pratique

1. Vérifie que Docker fonctionne.
2. Lance OpenWebUI avec la commande officielle.
3. Vérifie le conteneur avec `docker ps`.
4. Ouvre `http://localhost:3000`.
5. Crée ton compte administrateur.
6. Note le nom du conteneur et le port utilisé.

**Nom du conteneur :** `____________________________________________`

**Adresse de l’interface :** `____________________________________`

**Port utilisé sur mon ordinateur :** `____________________________`

## ✅ Checklist

- [ ] Docker Desktop est démarré.
- [ ] L’image OpenWebUI a été téléchargée.
- [ ] Le conteneur `open-webui` est en cours d’exécution.
- [ ] L’interface s’ouvre dans le navigateur.
- [ ] J’ai créé mon compte administrateur.
- [ ] Je sais arrêter et redémarrer le conteneur.

## 📝 Mon bilan

**Ce que j’ai réussi :** _________________________________________  
**Erreur rencontrée :** _________________________________________  
**Commande la plus utile retenue :** _____________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources officielles

- [OpenWebUI — Quick Start](https://docs.openwebui.com/getting-started/quick-start/)
- [OpenWebUI — Installation Docker sous Windows avec WSL](https://docs.openwebui.com/getting-started/quick-start/install-methods/windows-wsl/)
- [OpenWebUI — Documentation principale](https://docs.openwebui.com/)
- [Docker — Get Started](https://docs.docker.com/get-started/)

> **À retenir :** `-p 3000:8080` publie l’interface sur `http://localhost:3000`, et `-v open-webui:/app/backend/data` conserve les données dans un volume Docker.
