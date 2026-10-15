<!--
  Fichier : Jour2_Deploiement_Couches_Encapsulation_Routage_Adressage.md
  Cours   : Déploiement — Jour 2 : couches, encapsulation, routage et adressage
  Durée   : 60 à 90 minutes
  Mode    : adapté à l’aperçu sombre de VS Code
-->

<div style="background:#0d1b2a; border-left:8px solid #4fc3f7; padding:16px 20px; border-radius:10px; color:#e3f2fd;">
  <h1 style="color:#4fc3f7; margin:0;">🌐 Déploiement — Jour 2</h1>
  <p style="margin:8px 0 0; color:#e3f2fd;"><b>Thème :</b> comprendre les couches, l’encapsulation, le routage et l’adressage.</p>
</div>

<br>

<div style="background:#1b3a1f; border:1px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>🎯 Objectif :</b> comprendre comment les données traversent les couches réseau, comment elles sont encapsulées, routées et adressées.</p>
</div>

---

## 🎯 À la fin du cours, tu sauras

- <span style="color:#81c784;"><b>✅ expliquer</b></span> le modèle en couches (OSI / TCP-IP) ;
- <span style="color:#81c784;"><b>✅ décrire</b></span> l’encapsulation des données ;
- <span style="color:#81c784;"><b>✅ comprendre</b></span> le rôle du routage ;
- <span style="color:#81c784;"><b>✅ distinguer</b></span> adressage IP privé et public.

---

## 1. Le modèle en couches

Les réseaux sont organisés en **couches**, chacune ayant un rôle précis. Le modèle OSI comporte 7 couches ; le modèle TCP/IP en regroupe souvent 4 ou 5.

| Modèle OSI | Modèle TCP/IP simplifié | Rôle principal |
|---|---|---|
| 7 Application | Application | HTTP, DNS, e-mail |
| 6 Présentation | — | Format, chiffrement |
| 5 Session | — | Sessions, dialogues |
| 4 Transport | Transport | TCP, UDP, ports |
| 3 Réseau | Internet | IP, routage |
| 2 Liaison | Accès réseau | Ethernet, Wi-Fi |
| 1 Physique | Accès réseau | Câbles, signaux |

> [!NOTE]
> Pour ce cours, retiens surtout 4 couches : **Application**, **Transport**, **Internet** et **Accès réseau**.

## 2. Encapsulation : emballer les données

Quand tu envoies une requête HTTP, les données traversent les couches et sont **encapsulées** : chaque couche ajoute ses propres informations d’en-tête.

```text
Données applicatives (HTTP)
        ↓
Segment TCP/UDP
        ↓
Paquet IP
        ↓
Trame Ethernet/Wi-Fi
```

### Exemple simplifié

1. Le navigateur crée une requête HTTP.
2. TCP ajoute des informations de transport (ports, séquence).
3. IP ajoute les adresses source et destination.
4. La couche liaison ajoute les adresses MAC et prépare la trame.

> **Image mentale :** c’est comme emballer une lettre dans une enveloppe, puis dans un colis, puis dans un camion.

## 3. Routage : trouver le chemin

Le **routage** consiste à choisir le chemin que suivront les paquets pour aller d’un réseau à un autre. Les routeurs lisent l’adresse IP de destination et consultent leurs tables de routage.

```text
Ton ordinateur → routeur local → FAI → Internet → serveur
```

Chaque routeur prend une décision locale : vers quel prochain saut envoyer le paquet. Le chemin peut varier selon l’état du réseau.

> **À retenir :** le routage utilise principalement les adresses IP pour acheminer les paquets entre réseaux.

## 4. Adressage : IP privée et publique

| Type d’adresse | Rôle | Exemple |
|---|---|---|
| **IP privée** | Identifier un appareil dans un réseau local | `192.168.1.25` |
| **IP publique** | Identifier ton réseau sur Internet | Attribuée par le FAI |

### Plages privées courantes

- `10.0.0.0/8`
- `172.16.0.0/12`
- `192.168.0.0/16`

Ces plages ne sont pas routables directement sur Internet ; elles servent aux réseaux locaux.

### NAT : traduire les adresses

Le **NAT** (*Network Address Translation*) permet à plusieurs appareils d’un réseau local de partager une adresse publique pour accéder à Internet.

```text
Appareils du réseau local (IP privées)
        ↓
Routeur / NAT
        ↓
Adresse publique unique
        ↓
Internet
```

## 5. Exemple complet

Quand tu visites `https://exemple.com` :

1. Le navigateur demande au DNS l’adresse IP du site.
2. Ton ordinateur crée une requête HTTP.
3. TCP ajoute les ports et la gestion de connexion.
4. IP ajoute les adresses source et destination.
5. Le routeur local envoie le paquet vers Internet.
6. Le serveur reçoit le paquet, décapsule les couches et répond.

## 6. Tableau récapitulatif

| Notion | Rôle | Exemple |
|---|---|---|
| Couches | Organiser les responsabilités réseau | Application, Transport, Internet, Accès |
| Encapsulation | Ajouter des en-têtes à chaque couche | HTTP → TCP → IP → Ethernet |
| Routage | Choisir le chemin des paquets | Routeur, table de routage |
| Adressage | Identifier les interfaces réseau | IP privée, IP publique |
| NAT | Partager une IP publique | Plusieurs appareils derrière un routeur |

## 7. Erreurs fréquentes

<div style="background:#4e1c1c; border-left:6px solid #ef5350; padding:12px 16px; border-radius:8px; color:#ffebee;">
  <p style="margin:0;"><b>⚠️ Attention :</b> ne confonds pas adresse MAC et adresse IP.</p>
</div>

- **Adresse MAC** : identifiant matériel de la carte réseau, utilisé dans la couche liaison.
- **Adresse IP** : adresse logique utilisée pour le routage.
- **Port** : identifie un service sur une machine, pas une machine.
- **NAT** : traduit les adresses privées vers une adresse publique.

## ✍️ Exercices

### Exercice 1 — ordonner les couches

Remets dans l’ordre du haut vers le bas : Transport, Application, Accès réseau, Internet.

### Exercice 2 — encapsulation

Ordonne : Paquet IP, Données HTTP, Trame Ethernet, Segment TCP.

### Exercice 3 — adressage

Indique si ces adresses sont privées ou publiques :

- `192.168.1.10` : ______________
- `8.8.8.8` : ___________________
- `10.0.0.5` : __________________
- `172.16.4.2` : ________________

### Corrigé

<details>
<summary>Afficher les réponses</summary>

**Exercice 1 :** Application → Transport → Internet → Accès réseau.

**Exercice 2 :** Données HTTP → Segment TCP → Paquet IP → Trame Ethernet.

**Exercice 3 :** `192.168.1.10` privée ; `8.8.8.8` publique ; `10.0.0.5` privée ; `172.16.4.2` privée.

</details>

## ✅ Vérification de compréhension

- [ ] Je peux citer les 4 couches TCP/IP simplifiées.
- [ ] Je peux expliquer l’encapsulation avec mes mots.
- [ ] Je comprends le rôle du routage.
- [ ] Je sais distinguer IP privée et publique.
- [ ] Je comprends le rôle du NAT.

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**La notion la plus utile retenue :** ____________________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources fiables

- [Cloudflare — Internet Protocol et adressage](https://www.cloudflare.com/learning/network-layer/internet-protocol/)
- [Cloudflare — Ports réseau](https://workers.cloudflare.com/learning/network-layer/what-is-a-computer-port)
- [Microsoft Learn — Networking fundamentals](https://learn.microsoft.com/en-us/training/modules/network-fundamentals/)

<div style="background:#1b3a1f; border-left:6px solid #66bb6a; padding:12px 16px; border-radius:8px; color:#e8f5e9;">
  <p style="margin:0;"><b>✅ À retenir en une phrase :</b> les couches organisent les responsabilités, l’encapsulation ajoute des en-têtes à chaque étape, le routage choisit le chemin, et l’adressage identifie les interfaces réseau.</p>
</div>
