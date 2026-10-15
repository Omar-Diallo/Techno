<!--
  Fichier : Jour2_Docker_Conteneur_Image_Registre_Dockerfile_Daemon.md
  Cours   : Docker — notions fondamentales
  Durée   : 60 à 90 minutes
-->

# 🔵 Docker — Jour 2 : les notions essentielles

> **Thème :** comprendre conteneur, image, registre, Dockerfile et daemon.
>
> **Objectif :** savoir expliquer le rôle de chaque élément et suivre le chemin d’une application depuis son code jusqu’à son exécution.

---

## 🎯 À la fin du cours, tu sauras

- distinguer une image et un conteneur ;
- expliquer le rôle d’un registre ;
- comprendre ce qu’est un Dockerfile ;
- savoir ce que fait le daemon Docker ;
- relier ces notions dans un exemple simple.

## 1. Docker en une phrase

Docker permet de **packager une application avec ses dépendances**, puis de l’exécuter de manière isolée dans un conteneur. Cela aide à obtenir un environnement plus reproductible entre le développement et le déploiement. [web:363]

## 2. Image : le modèle de départ

Une **image Docker** est un modèle en lecture seule contenant les instructions et les éléments nécessaires pour créer un conteneur. Elle peut inclure un système de base, un runtime, du code, des bibliothèques et une configuration de démarrage. [web:363]

> **Image mentale :** l’image est comme une recette figée et prête à l’emploi ; le conteneur est le plat préparé à partir de cette recette.

Une image est donc :

- **en lecture seule** ;
- réutilisable ;
- versionnable grâce à des tags ;
- la base à partir de laquelle on crée des conteneurs.

## 3. Conteneur : l’application en exécution

Un **conteneur** est une instance exécutable d’une image. À partir d’une même image, tu peux lancer plusieurs conteneurs indépendants. [web:363]

### Exemple

```text
Image OpenWebUI
       ├── Conteneur OpenWebUI n°1
       ├── Conteneur OpenWebUI n°2
       └── Conteneur OpenWebUI n°3
```

Chaque conteneur est une instance séparée. Il peut avoir son propre processus, son propre réseau et son propre système de fichiers modifiable pendant son exécution, tout en restant basé sur la même image.

## 4. Registre : où stocker et partager les images

Un **registre Docker** est un service qui stocke et distribue des images. Docker Hub est le registre public par défaut, mais il existe aussi des registres privés. [web:363][web:364]

### Registre et dépôt

- **Registre** : lieu central qui stocke les images.
- **Dépôt** (*repository*) : collection d’images liées à un même projet ou service.
- **Tag** : étiquette qui identifie une version ou une variante d’une image.

Exemple :

```text
ghcr.io/open-webui/open-webui:main
└──────┬──────┘ └────────┬────────┘ └─┬─┘
   Registre          Dépôt           Tag
```

Docker Hub est le registre public par défaut de Docker, mais tu peux aussi utiliser un registre privé. [web:363][web:364]

## 5. Dockerfile : la recette de construction

Un **Dockerfile** est un fichier texte qui décrit les étapes nécessaires pour construire une image. Chaque instruction peut créer une couche dans l’image. [web:363][web:365]

Exemple simplifié pour une application Python :

```dockerfile
FROM python:3.12-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python", "app.py"]
```

### Lecture du Dockerfile

| Instruction | Rôle |
|---|---|
| `FROM` | Choisit l’image de base. |
| `WORKDIR` | Définit le dossier de travail dans le conteneur. |
| `COPY` | Copie des fichiers depuis ton projet vers l’image. |
| `RUN` | Exécute une commande pendant la construction de l’image. |
| `CMD` | Indique la commande par défaut exécutée au démarrage du conteneur. |

## 6. Daemon : le moteur Docker

Le **daemon Docker**, appelé `dockerd`, est le processus qui exécute les tâches principales : construire, exécuter et distribuer les conteneurs. Il gère aussi les images, les réseaux et les volumes. [web:363][web:372]

Quand tu tapes une commande comme `docker run`, le client Docker envoie une requête au daemon, qui effectue l’action. [web:363]

```text
PowerShell / Terminal
        │
        ▼
Client Docker (docker)
        │
        ▼
Daemon Docker (dockerd)
        │
        ▼
Image, conteneur, volume, réseau
```

C’est pour cela que `docker info` peut échouer si Docker Desktop n’est pas démarré : le client existe, mais il ne peut pas joindre le daemon.

## 7. Le chemin complet

```text
Dockerfile
   ↓
docker build
   ↓
Image
   ↓
docker run
   ↓
Conteneur
```

### Exemple concret

1. Tu écris un `Dockerfile` pour une application Python.
2. Tu construis une image avec `docker build`.
3. Tu donnes un nom et un tag à l’image.
4. Tu peux pousser l’image vers un registre avec `docker push`.
5. Tu lances un conteneur avec `docker run`.
6. Le conteneur exécute ton application.

Les commandes `docker pull`, `docker run` et `docker push` utilisent les registres configurés pour récupérer ou publier des images. [web:363][web:367][web:370]

## 8. Tableau récapitulatif

| Notion | Rôle | Exemple |
|---|---|---|
| Image | Modèle en lecture seule pour créer un conteneur | `ghcr.io/open-webui/open-webui:main` |
| Conteneur | Instance exécutable d’une image | Ton OpenWebUI en cours d’exécution |
| Registre | Lieu de stockage et de distribution des images | Docker Hub, GitHub Container Registry |
| Dockerfile | Fichier de recette pour construire une image | `FROM`, `COPY`, `RUN`, `CMD` |
| Daemon | Processus qui gère les objets Docker | `dockerd` |
| Client Docker | Outil qui envoie les commandes au daemon | `docker run`, `docker ps` |

## 9. Erreurs fréquentes

- **Confondre image et conteneur :** l’image est le modèle ; le conteneur est l’instance qui tourne.
- **Confondre registre et dépôt :** le registre stocke les images ; le dépôt regroupe les images liées à un même projet.
- **Penser que le Dockerfile est l’image :** le Dockerfile décrit comment construire l’image.
- **Confondre client et daemon :** le client envoie les commandes ; le daemon les exécute.
- **Utiliser le tag `latest` sans vérifier :** il ne garantit pas une version stable ou compatible avec ton projet.

## ✍️ Exercices

### Exercice 1 — associer

Associe chaque élément à son rôle :

- Image : ______________________________________________
- Conteneur : __________________________________________
- Registre : ___________________________________________
- Dockerfile : _________________________________________
- Daemon : _____________________________________________

### Exercice 2 — vrai ou faux ?

1. Une image est un modèle en lecture seule. ⬜ Vrai ⬜ Faux
2. Un conteneur est une instance exécutable d’une image. ⬜ Vrai ⬜ Faux
3. Le Dockerfile est le fichier qui stocke les images. ⬜ Vrai ⬜ Faux
4. Le daemon exécute les commandes reçues du client Docker. ⬜ Vrai ⬜ Faux
5. Docker Hub est un registre d’images. ⬜ Vrai ⬜ Faux

### Corrigé

<details>
<summary>Afficher les réponses</summary>

**Exercice 1 :** image = modèle en lecture seule ; conteneur = instance exécutable ; registre = service de stockage/distribution ; Dockerfile = recette de construction ; daemon = processus qui gère les objets Docker.

**Exercice 2 :** 1 Vrai ; 2 Vrai ; 3 Faux ; 4 Vrai ; 5 Vrai.

</details>

## ✅ Vérification de compréhension

- [ ] Je peux expliquer la différence entre image et conteneur.
- [ ] Je sais à quoi sert un registre.
- [ ] Je peux décrire le rôle d’un Dockerfile.
- [ ] Je comprends le rôle du daemon.
- [ ] Je peux expliquer le chemin Dockerfile → image → conteneur.

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**La différence image/conteneur avec mes mots :** _________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources officielles

- [Docker — What is Docker?](https://docs.docker.com/get-started/docker-overview/)
- [Docker — What is a Registry?](https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-registry/)
- [Docker — Build, tag and publish an image](https://docs.docker.com/get-started/docker-concepts/building-images/build-tag-and-publish-an-image/)
- [Docker — Docker Engine](https://docs.docker.com/engine/)

> **À retenir en une phrase :** le Dockerfile décrit comment construire une image ; le registre stocke l’image ; le conteneur est l’instance exécutable de cette image ; le daemon Docker gère ces objets. [web:363][web:364][web:365]
