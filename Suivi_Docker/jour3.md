<!--
  Fichier : Jour3_Docker_En_Ligne_HelloWorld.md
  Cours   : Docker — Jour 3 : lancer hello-world et explorer les commandes de base (en ligne)
  Durée   : 45 à 75 minutes
  Mode    : adapté à l’aperçu sombre de VS Code
-->

<div style="background:#0b2545; border-left:8px solid #4fc3f7; padding:16px 20px; border-radius:10px; color:#e3f2fd;">
  <h1 style="color:#4fc3f7; margin:0;">🔵 Docker — Jour 3 (en ligne)</h1>
  <p style="margin:8px 0 0; color:#e3f2fd;"><b>Thème :</b> lancer un conteneur <code>hello-world</code> et explorer les commandes de base, sans Docker Desktop.</p>
</div>

<br>

<div style="background:#1b3a1f; border:1px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>🎯 Objectif :</b> utiliser GitHub Codespaces pour lancer Docker dans le navigateur, exécuter <code>hello-world</code> et pratiquer les commandes essentielles.</p>
</div>

---

## 🎯 À la fin du cours, tu sauras

- <span style="color:#81c784;"><b>✅ créer</b></span> un Codespace GitHub ;
- <span style="color:#81c784;"><b>✅ vérifier</b></span> que Docker fonctionne en ligne ;
- <span style="color:#81c784;"><b>✅ lancer</b></span> le conteneur <code>hello-world</code> ;
- <span style="color:#81c784;"><b>✅ utiliser</b></span> les commandes <code>docker images</code>, <code>docker ps -a</code>, <code>docker run -it</code> ;
- <span style="color:#81c784;"><b>✅ nettoyer</b></span> conteneurs et images.

---

## 1. Pourquoi GitHub Codespaces ?

**GitHub Codespaces** est un environnement de développement dans le cloud, accessible depuis le navigateur. Docker y est déjà installé, ce qui permet de pratiquer sans Docker Desktop local. [web:492][web:494][web:495]

> [!NOTE]
> **Play with Docker** (labs.play-with-docker.com) était une option populaire, mais son dépôt indique une fin de disponibilité à partir de mars 2026 ; évite de compter dessus aujourd’hui. [web:506]

## 2. Créer un Codespace

1. Connecte-toi à [github.com](https://github.com).
2. Clique sur le **+** en haut à droite → **New repository**.
3. Nomme-le `docker-formation`, choisis **Public** ou **Private**, puis clique sur **Create repository**.
4. Sur la page du dépôt, clique sur **Code** → onglet **Codespaces** → **Create codespace on main**.
5. Attends que le VS Code dans le navigateur s’ouvre avec un terminal en bas. [web:494][web:499]

## 3. Vérifier Docker

Dans le terminal du Codespace, exécute :

```bash
docker --version
docker info
```

Tu dois voir une version de Docker et des informations sur le moteur, sans erreur. [web:492]

## 4. Lancer hello-world

```bash
docker run hello-world
```

Résultat attendu :

```text
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

L’image officielle `hello-world` affiche ce message et explique les étapes effectuées par Docker. [web:502]

## 5. Explorer les commandes de base

### A. Voir les images téléchargées

```bash
docker images
```

Tu verras `hello-world` dans la liste.

### B. Voir les conteneurs

```bash
docker ps -a
```

L’option `-a` affiche aussi les conteneurs arrêtés. Tu verras le conteneur `hello-world` avec le statut `Exited`.

### C. Lancer un conteneur interactif

```bash
docker run -it ubuntu bash
```

Cette commande lance un conteneur Ubuntu et ouvre un shell Bash à l’intérieur. Tu peux ensuite taper :

```bash
ls
cat /etc/os-release
exit
```

`exit` quitte le conteneur.

## 6. Nettoyer

```bash
docker ps -a
docker rm <ID_du_conteneur>
docker rmi hello-world
```

Remplace `<ID_du_conteneur>` par l’identifiant affiché par `docker ps -a`.

## 7. Résumé des commandes

| Commande | Rôle |
|---|---|
| `docker --version` | Affiche la version du client Docker |
| `docker info` | Vérifie que le moteur fonctionne |
| `docker run hello-world` | Lance le conteneur de test |
| `docker images` | Liste les images locales |
| `docker ps -a` | Liste tous les conteneurs |
| `docker run -it ubuntu bash` | Lance un conteneur Ubuntu interactif |
| `docker rm <ID>` | Supprime un conteneur |
| `docker rmi <image>` | Supprime une image |

## 8. Erreurs fréquentes

<div style="background:#4e1c1c; border-left:6px solid #ef5350; padding:12px 16px; border-radius:8px; color:#ffebee;">
  <p style="margin:0;"><b>⚠️ Attention :</b> si Docker n’est pas disponible dans le Codespace, vérifie que tu es bien dans un Codespace GitHub et non dans un simple dépôt.</p>
</div>

- **`docker: command not found`** : tu n’es pas dans un Codespace, ou Docker n’est pas installé dans l’environnement.
- **Erreur de connexion au daemon** : relance le Codespace ou vérifie que Docker est démarré dans l’environnement.
- **Image non trouvée** : vérifie l’orthographe (`hello-world`, pas `helloworld`).

## ✍️ Exercice pratique

1. Crée un Codespace sur GitHub.
2. Exécute `docker --version` et `docker info`.
3. Lance `docker run hello-world`.
4. Lance `docker run -it ubuntu bash`, explore avec `ls` et `cat /etc/os-release`, puis `exit`.
5. Liste les conteneurs avec `docker ps -a`.
6. Supprime le conteneur hello-world avec `docker rm`.

**Version Docker affichée :** ____________________________________

**Résultat de `docker run hello-world` :**

> À compléter.

## ✅ Checklist

- [ ] Codespace créé et ouvert.
- [ ] Docker vérifié avec `docker --version` et `docker info`.
- [ ] `hello-world` lancé avec succès.
- [ ] Conteneur Ubuntu interactif testé.
- [ ] Conteneurs et images nettoyés.

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**La commande la plus utile retenue :** __________________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources officielles

- [GitHub Codespaces — Documentation](https://docs.github.com/en/codespaces)
- [GitHub Codespaces — Deep dive](https://docs.github.com/en/codespaces/about-codespaces/deep-dive)
- [Docker — hello-world official image](https://hub.docker.com/_/hello-world)
- [Docker — Get Started](https://docs.docker.com/get-started/)

<div style="background:#1b3a1f; border-left:6px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>✅ À retenir en une phrase :</b> GitHub Codespaces permet de pratiquer Docker dans le navigateur sans Docker Desktop ; lance <code>hello-world</code>, explore avec <code>docker ps -a</code> et nettoie avec <code>docker rm</code>.</p>
</div>
