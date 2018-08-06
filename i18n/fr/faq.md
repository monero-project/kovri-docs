# Foire Aux Qestions

## Table des matières
- Questions générales
    - Qu'est-ce que Kovri ?
    - Qui développe Kovri ?
    - En quoi Kovri va-t-il aider Monero ?
    - Pourquoi devrais-je utiliser Kovri plutôt que I2P ?
    - Qu'est-ce que Kovri permet ?
    - Qu'est-ce que Kovri permettra dans le futur ?
    - Qu'est-ce que Kovri ne permettra pas ?
    - Quel est l'état actuel de développement de Kovri ?
    - Quand sera disponible la version alpha ?
    - Sur quoi se focalise en ce moment l'équipe de développement ?
    - Kovri est-il déjà utilisable et quel niveau de vie privée propose-t-il actuellement ?
    - Comment puis-je contacter les développeurs de Kovri ?
- Kovri vs i2pd
    - Pourquoi devrais-je utiliser Kovri plutôt que i2pd ?
    - Quelles sont les principales différences entre Kovri et i2pd ?
    - Pourquoi avez-vous créé une fourche à partir d'i2pd ?
    - Quels sont les principaux facteurs qui ont amené à créé une fourche i2pd ? (Et pourquoi y a-t-il deux repos i2pd, un sur Bitbucker et un sur GitHub ?)
- Utiliser Kovri
    - J'ai trouvé une vulnérabilité, j'ai trouvé un bug, que dois-je faire ?
    - Pourquoi mes logs montrent une heure différente de mon fuseau horaire ?

## Questions générales

### Qu'est-ce que Kovri ?

[Kovri](https://getmonero.org/resources/moneropedia/kovri.html) est une technologie gratuite et décentralisée pour garantir l'anonymat sur internet. Elle est développée par [Monero](https://getmonero.org).

Basé sur les spécifications d'[I2P](https://getmonero.org/resources/moneropedia/i2p.html), Kovri utilise les technologies [chiffrement en ail](https://getmonero.org/resources/moneropedia/garlic-encryption.html) et [routage en ail](https://getmonero.org/resources/moneropedia/garlic-routing.html) pour créer une surcouche à internet à la fois privée et protégée.

Kovri *recouvre* le trafic internet d'une application pour le rendre anonyme sur le réseau.

Kovri est un routeur léger et axé sur la sécurité. Il est totalement compatible avec le réseau I2P. La version alpha de Kovri est en cours de développement.

### Qui développe Kovri ?
Kovri est un projet open-source, ce qui veut dire qu'il est entièrement dépendant des contributions de la communauté. Le développeur principal du projet est [anonimal](https://github.com/anonimal), que vous pouvez contacter via les canaux IRC [#kovri](irc://chat.freenode.net/#kovri) et [#kovri-dev](irc://chat.freenode.net/#kovri-dev), et via son [compte Twitter](https://twitter.com/0x914409F1).

Kovri est développé sous l'égide du [Projet Monero](https://github.com/monero-project). C'est un autre projet open-source, qui développe la [Pièce Monero](https://getmonero.org) et [Open Alias](https://openalias.org). La relation entre le Projet Monero et Kovri est mutuellement bénéfique dans le sens où Kovri va s'intégrer dans le réseau Monero et Monero contribue au projet Kovri en fournissant des développeurs et des ressources.

### En quoi Kovri va-t-il aider Monero ?
Le Monero est une crypto-monnaie sécurisée, privée, intraçable, fongible et confidentielle par défaut. Il utilise les technologies suivantes pour cacher respectivement le destinataire, la quantité envoyée et l'expéditeur : des adresses furtives, signatures confidentielles de cercle (*RingCT*) et les signatures de cercle (*Ring Signatures*). Des vulnérabilités potentielles de Monero pourraient laisser fuiter l'adresse IP qui émet la transaction.

C'est là que Kovri intervient. Kovri sera implémenté dans le portefeuille officiel de Monero, donc toutes les transactions passeront par le réseau anonyme Kovri et les adresses IP par lesquelles les transactions sont émises seront donc cachées. Dans le futur, toutes les transactions transiteront par défaut par Kovri. Cependant, pour des raisons d'efficacité, le téléchargement de la blockchain se fera toujours par le *clearnet* (le réseau internet classique).

### Pourquoi devrais-je utiliser Kovri plutôt que I2P ?
[I2P](https://geti2p.net) est un bon projet mais certaines choses devaient être adaptées pour pouvoir intégrer sa technologie dans Monero. Premièrement, I2P est développé en Java et nous pensions que développer un router en C++ aiderait pour un code plus léger et plus rapide à faire tourner.

Deuxièmement, bien que l'implémentation en Java soit bonne, elle s'accompagne de nombreuses fonctionnalités qui ne nous semblaient pas nécessaires pour l'application Monero. Nous avons donc décidé de recommencer à partir de zéro et de faire un routeur qui est JUSTE un routeur. Cette approche simplifiée est parfaite pour Monero et représente aussi une bonne nouvelle pour tous les autres qui veulent développer des applications I2P. Ils ont la possibilité d'utiliser un routeur léger sans le superflu. Et pour ceux qui ont besoin des fonctionnalités supplémentaires, ils peuvent utiliser l'implémentation Java. C'est gagnant-gagnant pour tout le monde.

### Qu'est-ce que Kovri permet ?
- De devenir un nœud sur le réseau I2P
- De cacher votre localisation physique pour les sites que vous visitez
- De vous anonymiser sur IRC et vous permet d'envoyer des e-mails de manière anonyme
- D'héberger des sites et services anonymes
- De fournir du financement à des développeurs, hackers et chercheurs via FFS et HackerOne
- Il vise les standards les plus rigoureux en terme de développement et qualité de code

### Qu'est-ce que Kovri permettra dans le futur ?
- Émettre des transactions Monero à travers I2P
- Une GUI pour une utilisation et une configuration améliorées
- Une bibliothèque d'APIs pour des apps/libs externes
- Une extension Firefox pour accéder facilement aux *eepsites* (les websites hébergés sur le réseau I2P)
- Le site internet de Kovri ([getkovri.org](getkovri.org) / [kovri.i2p](kovri.i2p))
- Une documentation exhaustive

### Qu'est-ce que Kovri ne permettra pas ?
- De sacrifier votre sécurité et vie privée pour des arrière-pensées
- De fournir une interface web compliquée et pénible
- D'avoir besoin des autorités pour arriver à un consensus sur le réseau
- D'accéder à des sites internet via un "outproxy"
- D'avoir besoin d'une machine virtuelle Java ultra-performante
- De promener votre chien et de payer vos impôts

### Quel est l'état actuel de développement de Kovri ?
Nous travaillons activement sur le développement de Kovri et celui-ci est en phase Alpha. Kovri *n'est pas encore* intégré dans Monero, mais, en plus de certaines fonctionnalités de base, nous sommes en train de développer un [client](https://github.com/monero-project/kovri/issues/351) et une [API cœur](https://github.com/monero-project/kovri/issues/350) visant à être utilisés par Monero ou d'autres applications.

Mais le fait que nous soyons en Alpha ne veut pas dire que vous ne pouvez pas utiliser Kovri. Vous pouvez déjà utiliser Kovri pour vous connecter au réseau I2P, surfer sur les *eepsites*, vous connecter sur IRC et faire tourner des *tunnels client* et *tunnels serveur*.

### Quand sera disponible la version alpha ?
La version alpha sera disponible (nous l'espérons !!) avant fin 2017. Une fois que nous serons en alpha, le travail commencera immédiatement sur la version beta, qui nécessitera : une API complètement implémentée, la résolution des problèmes principaux d'assurance qualité et la résolution des différents bugs.

### Sur quoi se focalise en ce moment l'équipe de développement ?
Nous travaillons actuellement sur tous les points listés sur notre [système de suivi](https://github.com/monero-project/kovri/issues/). La plupart de ce qui doit être achevé avant de sortir la version alpha officielle y est listé.

### Kovri est-il déjà utilisable et quel niveau de vie privée propose-t-il actuellement ?
Kovri est utilisable. Sur `./kovri --help`, vous pouvez voir tout ce que Kovri offre actuellement. Kovri n'a pour le moment aucune interaction avec Monero. En ce qui concerne la vie privée, nous avons résolu de nombreux problèmes depuis le début, mais nous vous demandons de garder en tête que nous ne sommes qu'en Alpha.

Il y a encore beaucoup de code à écrire et à tester, donc ne vous attendez pas encore à une garantie d'anonymité telle qu'offerte par Tor ou par I2P Java. Ces projets ont plus de 10 ans derrière eux de recherche, d'implémentation et d'utilisation. A contrario, nous n'en sommes qu'au début.

N'hésitez pas à vous mettre dans le rôle d'un développeur et à jouer avec Kovri, mais seulement si *ne pas* être anonyme ne peut pas vous mettre en danger, étant donné que le risque de ne pas être complètement anonyme existe comme nous ne sommes qu'en Alpha (ce n'est pas unique à Kovri).

### Comment puis-je contacter les développeurs de Kovri ?
Visitez notre [README](https://github.com/monero-project/kovri/blob/master/README.md).

## Kovri vs i2pd

### Pourquoi devrais-je utiliser Kovri plutôt que i2pd ?

- La sécurité : Nous nous focalisons sur la sécurisation de notre logiciel ; nous ne voulons pas nous [précipiter](https://github.com/monero-project/kovri/issues/65) juste pour sortir une version au plus vite.
- La qualité : Vous soutenez un projet dont la qualité du code résistera à l'épreuve du temps. Cela inclut tous les aspects de la maintenabilité du code.
- Monero : Vous soutiendrez une crypto-monnaie qui se focalise sur le respect de la vie privée et de l'anonymat.

### Quelles sont les principales différences entre Kovri et i2pd ?

- Nous avons un [Forum de financements](https://forum.getmonero.org/8/funding-required) pour le développement et l'ajout de fonctionnalités.
- Nous nous focalisons sur la création d'un routeur I2P qui est [sécurisé par défaut](http://www.openbsd.org/security.html), facile à maintenir et qui a de grandes chances d'être examiné et vérifié par la communauté. Cela a le désavantage que nous supprimons les fonctionnalités les moins utilisées par rapport aux autres routeurs, mais les fonctionnalités principales et l'API seront complètes et intactes. En créant un routeur plus léger, simple et efficace, les développeurs et chercheurs auront plus de temps pour auditer la sécurité et pour questionner le design I2P et les spécifications.
- Nous implémentons une API intuitive et facile à utiliser pour n'importe quelle application qui veut se connecter et utiliser le réseau I2P. C'est notamment le cas pour Monero.
- Nous fournissons à la fois aux utilisateurs et aux développeurs une [assurance qualité](https://github.com/monero-project/kovri/issues/58) et un [modèle de développement](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/contributing.md) dans le but de fournir des meilleurs logiciels pour tout le monde.
- Nous allons implémenter des options alternatives de *reseeding* pour que les utilisateurs puissent utiliser les [Pluggable Transports](https://www.torproject.org/docs/pluggable-transports.html.en) au lieu d'HTTPS pour le *reseed*.
- Nous comptons implémenter des fonctionnalités avancées (*mode caché* et *trafic entrant désactivé*) pour fournir l'anonymat à ceux qui vivent dans des pays aux conditions extrêmes ou ceux qui sont derrière un firewall de type NAT ou DS-Lite.
- Nous créerons toujours un environnement prône à la collaboration.
- Nous écouterons toujours vos retours et nous ferons de notre mieux pour améliorer Kovri !

### Pourquoi avez-vous créé une fourche à partir d'i2pd ?

Nous avons créé une fourche pour plusieurs raisons :

- Nous souhaitions une implémentation C++ d'I2P qui soit à la fois robuste, sécurisée et fiable ; et i2pd ne répondait pas à ces exigences ou ne fournissait pas ce qu'attendu.
- Nous voulions une communauté positive qui encourage la collaboration, pas une communauté négative et narcissique.
- Nous voulions un lead développeur avec une vision, et pas quelqu'un qui ignore les demandes de divulgation ou qui s'encourt au moindre conflit entre contributeurs.

### Quels sont les principaux facteurs qui ont amené à créé une fourche d'i2pd ? (Et pourquoi y a-t-il deux repos i2pd, un sur Bitbucker et un sur GitHub ?)

*Voici comment ont commencé les drames autour d'i2pd*.

Début 2015, un des développeurs d'i2pd avec les privilèges *push* sur Github a poussé un *commit* que l'auteur initial d'i2pd n'a pas apprécié. Au lieu de travailler ensemble pour résoudre le problème, l'auteur initial à déplacé i2pd sur Bitbucket, a supprimé **tous** l'historique git et s'est mis comme seul contributeur. Il a ensuite proclamé qu'il ne retournerait plus jamais sur Irc2P.

Ces actions ont offensé de nombreuses personnes dans la communauté I2P, y compris les développeurs, et cela a presque mis fin au projet C++.

À l'automne 2015, anominal est arrivé et, ne voulant pas voir le travail de tout le monde gaspillé, il a relancé le projet en contribuant et en le reprenant en main. Une invitation ouverte pour se rencontrer a été envoyée à tous les développeurs encore actifs pour discuter du futur d'i2pd. L'auteur initial d'i2pd ne s'est pas présenté mais le fait de se réunir lui a tellement déplu qu'il a [riposté](https://github.com/PurpleI2P/i2pd/issues/279) et recommencé à travailler sur GitHub - mais cette fois sur une branche `openssl` (qui s'est avérée être le repo Bitbucket) au lieu de la branche `master` sur laquelle le reste de la communauté travaillait.

En se rendant compte que ce type de comportement ne ferait que nuire au réseau I2P et au projet, les autres développeurs ont continué à tenir des [réunions importantes](https://github.com/monero-project/kovri/issues/47) et à mettre en place les fondements de ce qu'est maintenant Kovri.

## Utiliser Kovri

### J'ai trouvé une vulnérabilité, j'ai trouvé un bug, que dois-je faire ?
- Vulnérabilité : visitez notre [README](https://github.com/monero-project/kovri/blob/master/README.md)
- Bugs : visitez notre [Guide de développement](https://github.com/monero-project/kovri-docs/blob/master/i18n/fr/developer_guide.md)

### Pourquoi mes logs montrent une heure différente de mon fuseau horaire ?
Les logs sont enregistrés en UTC pour protéger votre anonymat. En utilisant UTC, vous êtes dans une meilleure position pour uploader vos logs et les partager avec les développeurs et la communauté sans porter atteinte à votre anonymat.