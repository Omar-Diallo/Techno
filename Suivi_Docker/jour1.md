<!--
  Fichier : Jour1_Docker_Installation_Verification.md
  Cours   : Docker — installer Docker et vérifier la commande
  Date    : 2 novembre 2026
  Durée   : 45 à 75 minutes
-->

# 🔵 Docker — Jour 1 : installation et vérification

> **Objectif :** installer Docker Desktop (Windows/macOS) ou Docker Engine (Linux), démarrer Docker et vérifier l’installation avec `docker --version`.

---

## 🎯 À la fin du cours, tu sauras

- distinguer Docker Desktop et Docker Engine ;
- télécharger l’installateur depuis le site officiel ;
- ouvrir un terminal et vérifier la version du client Docker ;
- tester que Docker peut lancer un conteneur.

## 1. Docker Desktop ou Docker Engine ?

- **Docker Desktop** est l’application la plus simple pour commencer sur Windows ou macOS. Elle fournit une interface graphique et les outils Docker nécessaires. Docker Desktop est également disponible pour Linux. [web:253]
- **Docker Engine** s’installe directement sur un serveur ou un poste Linux. Il comprend le moteur qui construit et exécute les conteneurs. [web:252]

> **Choix conseillé :** Windows ou macOS → Docker Desktop. Linux → Docker Desktop ou Docker Engine selon ton besoin. Pour ce premier exercice, ne cherche pas à installer les deux en même temps.

## 2. Avant l’installation

1. Identifie ton système : Windows, macOS ou Linux.
2. Utilise un compte disposant des droits nécessaires pour installer un logiciel.
3. Télécharge Docker uniquement depuis la documentation ou le site officiels.
4. Ferme les programmes d’installation en cours avant de lancer Docker.

## 3. Installation sur Windows

1. Ouvre le guide officiel [Installer Docker Desktop sur Windows](https://docs.docker.com/desktop/setup/install/windows-install/).
2. Télécharge `Docker Desktop Installer.exe` depuis la page officielle.
3. Lance l’installateur et suis les étapes affichées.
4. Si l’installateur propose WSL 2 ou Hyper-V, suis les prérequis indiqués par Docker pour ton système. WSL 2 est une option courante, mais les prérequis dépendent de ta configuration. [web:250][web:257]
5. Termine l’installation, puis démarre **Docker Desktop** depuis le menu Démarrer.
6. Attends que Docker Desktop indique que le moteur est démarré.

## 4. Installation sur macOS

1. Ouvre le guide officiel [Installer Docker Desktop sur Mac](https://docs.docker.com/desktop/setup/install/mac-install/).
2. Télécharge la version adaptée à l’architecture de ton Mac (Apple silicon ou Intel).
3. Ouvre le fichier `.dmg`.
4. Fais glisser Docker vers le dossier **Applications**, selon les instructions de l’installateur.
5. Lance Docker Desktop et accepte les demandes de permissions nécessaires. [web:256]

## 5. Installation sur Linux

Sur Linux, tu peux installer Docker Desktop ou Docker Engine. Pour apprendre l’administration d’un serveur, Docker Engine est souvent le choix direct. Les commandes d’installation changent selon la distribution : suis le guide Docker officiel correspondant à Ubuntu, Debian, Fedora ou à ta distribution. [web:252][web:249]

> ⚠️ **Ne copie pas une commande d’installation Linux au hasard.** Les étapes dépendent de ta distribution et de sa version. Les instructions officielles Docker sont la référence.

## 6. Vérifier avec `docker --version`

Ouvre un terminal :

- **Windows** : PowerShell ou Windows Terminal ;
- **macOS** : Terminal ;
- **Linux** : ton application Terminal.

Tape cette commande et appuie sur Entrée :

```bash
docker --version
```

### Résultat attendu

Tu dois voir une ligne similaire à :

```text
Docker version XX.Y.Z, build abcdef
```

Le numéro exact changera selon la version installée. Cette commande confirme que la commande `docker` est accessible. Elle ne garantit pas, à elle seule, que le moteur Docker est démarré.

### Vérifier que le moteur fonctionne

Essaie ensuite :

```bash
docker info
```

Si Docker fonctionne, tu verras des informations sur le client et le serveur Docker. Si un message indique que le daemon ou le moteur n’est pas accessible, ouvre Docker Desktop et attends son démarrage, ou vérifie le service Docker sur Linux.

Enfin, lance le conteneur de test officiel :

```bash
docker run hello-world
```

Docker doit télécharger l’image si nécessaire puis afficher un message confirmant que l’installation fonctionne. Le guide de démarrage Docker propose ce type de première exécution pour valider l’environnement. [web:108][web:118]

## 7. Résumé des commandes

| Commande | Rôle |
|---|---|
| `docker --version` | Affiche la version de la commande Docker. |
| `docker info` | Vérifie l’état général et la communication avec le moteur. |
| `docker run hello-world` | Lance un conteneur de test. |

## ⚠️ Problèmes fréquents

### « docker n’est pas reconnu » ou « command not found »

Docker n’est peut-être pas installé correctement, ou le terminal n’a pas été rouvert après l’installation. Vérifie l’installation, puis ferme et rouvre le terminal.

### « Cannot connect to the Docker daemon »

Le client existe, mais le moteur n’est probablement pas démarré. Lance Docker Desktop ou vérifie le service Docker de ta distribution Linux.

### Problème de droits sur Linux

La commande peut nécessiter `sudo` selon la configuration. Ne modifie pas les permissions de sécurité sans comprendre leurs conséquences ; consulte la documentation officielle de ta distribution et de Docker.

### Windows demande WSL 2

Suis le message de l’installateur et le guide Docker pour activer ou mettre à jour WSL si ta configuration l’exige. [web:250][web:257]

## ✍️ Exercice pratique

1. Installe Docker Desktop ou Docker Engine.
2. Ouvre un terminal.
3. Exécute `docker --version` et copie le résultat ci-dessous.
4. Exécute `docker info`.
5. Exécute `docker run hello-world`.
6. Note le résultat et toute erreur rencontrée.

**Ma version Docker :** __________________________________________

**Résultat de `docker run hello-world` :**

> À compléter.

## ✅ Checklist

- [ ] J’ai choisi Docker Desktop ou Docker Engine selon mon système.
- [ ] J’ai téléchargé Docker depuis une source officielle.
- [ ] Docker est démarré.
- [ ] `docker --version` affiche une version.
- [ ] `docker info` communique avec le moteur.
- [ ] `docker run hello-world` s’exécute correctement.

## 📝 Mon bilan

**Système utilisé :** ⬜ Windows  ⬜ macOS  ⬜ Linux  
**Solution installée :** ⬜ Docker Desktop  ⬜ Docker Engine  
**Difficulté rencontrée :** _____________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Documentation officielle

- [Docker — Get Started](https://docs.docker.com/get-started/)
- [Installer Docker Desktop sur Windows](https://docs.docker.com/desktop/setup/install/windows-install/)
- [Installer Docker Desktop sur Mac](https://docs.docker.com/desktop/setup/install/mac-install/)
- [Installer Docker Engine sur Linux](https://docs.docker.com/engine/install/)
- [Guide pratique Docker — premier conteneur](https://docs.docker.com/guides/lab-container-getting-started/)

> **À retenir :** `docker --version` vérifie que le client Docker est accessible ; `docker info` et `docker run hello-world` aident à confirmer que le moteur fonctionne réellement.
