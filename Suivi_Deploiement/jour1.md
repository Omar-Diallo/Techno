<!--
  Fichier : Jour1_Reseaux_Notions_fondamentales.md
  Cours   : Réseaux — IP, DNS, HTTP/HTTPS, ports, TCP/UDP
  Durée   : 60 à 90 minutes
-->

# 🌐 Réseaux — Jour 1 : les notions essentielles

> **Objectif :** comprendre le rôle des adresses IP, du DNS, des ports, de TCP/UDP et de HTTP/HTTPS quand tu visites un site web.

---

## 🎯 À la fin du cours, tu sauras

- expliquer à quoi sert une adresse IP ;
- décrire le rôle du DNS ;
- distinguer HTTP et HTTPS ;
- comprendre ce qu’est un port réseau ;
- comparer simplement TCP et UDP.

## 1. Le voyage d’une requête web

Quand tu écris `https://exemple.com` dans ton navigateur, plusieurs étapes ont lieu :

```text
Nom de domaine → DNS trouve une adresse IP
                 → l’appareil contacte l’adresse et un port
                 → TCP ou UDP transporte les données
                 → HTTPS protège l’échange avec du chiffrement TLS
                 → le serveur renvoie la page
```

C’est une représentation simplifiée : les détails changent selon la version du protocole et la configuration du réseau.

## 2. Adresse IP : où envoyer les données ?

Une **adresse IP** identifie une interface réseau afin que les données puissent être acheminées vers la bonne destination. Elle joue un rôle comparable à une adresse postale pour le réseau.

Exemples :

- IPv4 : `192.168.1.25` ;
- IPv6 : `2001:db8::25` (exemple de documentation).

Ton ordinateur peut avoir une adresse privée dans ton réseau local et utiliser une adresse publique pour communiquer sur Internet. L’IP aide à acheminer les paquets ; elle ne désigne pas à elle seule le programme qui doit recevoir les données. [web:301]

## 3. DNS : retrouver l’adresse IP

Le **DNS** (*Domain Name System*) associe des noms lisibles, comme `exemple.com`, à des informations réseau, notamment des adresses IP. Cela évite de devoir mémoriser l’adresse numérique de chaque site.

Analogie : tu recherches le nom d’un contact dans ton téléphone ; le DNS joue un rôle de répertoire qui aide à retrouver où joindre le service.

> Le DNS ne transporte pas la page web : il aide d’abord ton appareil à trouver la destination.

## 4. Ports : quel service sur cette machine ?

Une **adresse IP** identifie la destination réseau ; un **port** aide à préciser le service ou l’application visé sur cette destination. Les ports sont utilisés avec des protocoles de transport comme TCP ou UDP. [web:298][web:294]

Exemples courants :

| Service courant | Port habituel | Transport courant |
|---|---:|---|
| HTTP | 80 | TCP |
| HTTPS | 443 | TCP pour HTTP/1.1 et HTTP/2 ; HTTP/3 utilise QUIC sur UDP |
| DNS | 53 | UDP le plus souvent ; TCP également dans certains cas |
| SSH | 22 | TCP |

Ce sont des ports d’usage courant, pas une garantie que chaque serveur est configuré ainsi. L’IANA maintient le registre officiel des noms de services et numéros de port. [web:294][web:298][web:306]

## 5. TCP et UDP : deux façons de transporter les données

### TCP

**TCP** établit une connexion et fournit des mécanismes pour livrer les données de manière fiable et dans l’ordre. C’est utile lorsque la perte ou le désordre des données serait problématique, par exemple pour beaucoup d’échanges web traditionnels. [web:301][web:306]

### UDP

**UDP** envoie des datagrammes sans établir la même connexion ni garantir à lui seul la livraison et l’ordre. Il peut être adapté aux usages sensibles au délai, où attendre une retransmission serait moins utile. Des protocoles comme QUIC ajoutent leurs propres mécanismes au-dessus d’UDP. [web:301]

| TCP | UDP |
|---|---|
| Connexion et livraison fiable gérées par le protocole | Pas de garantie de livraison ou d’ordre fournie par UDP |
| Utile quand l’exactitude et l’ordre comptent | Utile quand la rapidité et le délai sont prioritaires, selon l’application |
| Exemple : HTTP/1.1 et HTTP/2 généralement sur TCP | Exemple : DNS courant et QUIC/HTTP/3 sur UDP |

> **À retenir :** UDP n’est pas automatiquement « meilleur » ou « plus rapide » dans toutes les situations ; le choix dépend du protocole et de l’application.

## 6. HTTP et HTTPS : comment le navigateur parle au site

**HTTP** est un protocole de la couche application utilisé pour échanger des requêtes et des réponses entre un client (par exemple un navigateur) et un serveur. [web:306]

**HTTPS** désigne HTTP protégé par TLS. TLS chiffre les échanges et aide le navigateur à vérifier l’identité du serveur au moyen de son certificat. Cela protège les données pendant leur transit, mais ne rend pas automatiquement un site fiable ou sans vulnérabilité.

Ports usuels : HTTP utilise généralement le port 80 et HTTPS le port 443. [web:298][web:294]

### Exemple simplifié

1. Tu demandes `https://exemple.com`.
2. Le DNS aide à obtenir une adresse IP pour `exemple.com`.
3. Le navigateur contacte généralement le service HTTPS sur le port 443.
4. Le transport et TLS sont établis selon les protocoles utilisés.
5. Le navigateur envoie une requête HTTP et reçoit une réponse.

HTTP/1.1 et HTTP/2 utilisent habituellement TCP ; HTTP/3 utilise QUIC, qui fonctionne sur UDP. [web:306]

## 7. Résumé visuel

| Élément | Question à laquelle il répond | Exemple de rôle |
|---|---|---|
| DNS | « Quelle adresse correspond à ce nom ? » | Trouver l’adresse associée à un domaine |
| Adresse IP | « Quel appareil/interface doit recevoir les paquets ? » | Acheminer les paquets vers une destination |
| Port | « Quel service sur cette destination ? » | Distinguer le serveur web d’autres services |
| TCP ou UDP | « Comment transporter les données ? » | Fiabilité/ordre ou transport par datagrammes |
| HTTP/HTTPS | « Quel échange entre navigateur et serveur web ? » | Demander et recevoir une page ou une ressource |

## ✍️ Exercices rapides

### Exercice 1 — associer

Associe chaque élément à son rôle :

- DNS : ________________________________________________
- Adresse IP : _________________________________________
- Port : _______________________________________________
- HTTPS : _____________________________________________
- TCP : ________________________________________________

### Exercice 2 — vrai ou faux ?

1. Le DNS aide à retrouver une adresse à partir d’un nom de domaine. ⬜ Vrai ⬜ Faux
2. Un port remplace l’adresse IP. ⬜ Vrai ⬜ Faux
3. TCP fournit des mécanismes de fiabilité et d’ordre. ⬜ Vrai ⬜ Faux
4. HTTPS protège l’échange HTTP avec TLS. ⬜ Vrai ⬜ Faux
5. UDP garantit toujours que chaque paquet arrive dans l’ordre. ⬜ Vrai ⬜ Faux

### Corrigé

<details>
<summary>Afficher les réponses</summary>

**Exercice 1 :** DNS associe noms et informations réseau ; IP adresse une interface pour acheminer les paquets ; le port distingue un service ; HTTPS protège HTTP avec TLS ; TCP fournit une livraison fiable et ordonnée.

**Exercice 2 :** 1 Vrai ; 2 Faux ; 3 Vrai ; 4 Vrai ; 5 Faux.

</details>

## 📝 Mon bilan

**Ce que j’ai compris :** ________________________________________  
**La différence TCP/UDP avec mes mots :** ________________________  
**Ce qui reste flou :** _________________________________________  
**Confiance (1 à 5) :** ⬜ 1  ⬜ 2  ⬜ 3  ⬜ 4  ⬜ 5  
**Statut :** ⬜ À faire  ⬜ En cours  ⬜ Terminé

---

## 📚 Ressources fiables

- [Cloudflare — Internet Protocol et adressage](https://www.cloudflare.com/learning/network-layer/internet-protocol/)
- [Cloudflare — Ports réseau](https://workers.cloudflare.com/learning/network-layer/what-is-a-computer-port)
- [MDN — Vue d’ensemble de HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Overview)
- [IANA — Registre des services et numéros de port](https://www.iana.org/assignments/service-names-port-numbers)

> **À retenir en une phrase :** le DNS aide à trouver une IP, l’IP dirige les paquets vers une destination, le port désigne le service, TCP ou UDP transporte les données, et HTTP/HTTPS décrit les échanges web. [web:294][web:298][web:301][web:306]
