# Foire Aux Qestions

## Table des matières
- Questions générales
    - Qu'est-ce que Kovri ?
    - Qui développe Kovri ?
    - En quoi Kovri va-t-il aider Monero ?
    - Pourquoi devrais-je utiliser Kovri plutôt que I2P ?
    - Qu'est-ce que Kovri permet ?
    - Qu'est-ce qui est en cours de développement ?
    - Qu'est-ce que Kovri ne permettra pas ?
    - Quel est l'état actuel de développement de Kovri ?
    - Quand sera disponible la version alpha ?
    - Sur quoi se focalise en ce moment l'équipe de développement ?
    - Kovri est-il déjà utilisable et quel niveau de vie privée propose-t-il actuellement ?
    - Comment puis-je contacter les développeurs de Kovri ?
- Kovri vs i2pd
    - Pourquoi devrais-je utiliser Kovri plutôt que i2pd ?
    - Quelles sont les principales différences entre Kovri et i2pd ?
    - Pourquoi avez-vous forké à partir d'i2pd ?
    - Quels sont les principaux facteurs qui ont amené à forker i2pd ? (Et pourquoi y a-t-il deux repos i2pd, un sur Bitbucker et un sur GitHub ?)
- Utiliser Kovri
    - J'ai trouvé une vulnérabilité, j'ai trouvé un bug, que dois-je faire ?
    - Pourquoi mes logs montrent une heure différente de mon fuseau horaire ?

## Questions générales

### Qu'est-ce que Kovri ?

[Kovri](https://getmonero.org/resources/moneropedia/kovri.html) est une technologie gratuite et decentralisée pour garantir l'anonymat sur internet. Elle est développée par [Monero](https://getmonero.org).

Basé sur les spécifications d'[I2P](https://getmonero.org/resources/moneropedia/i2p.html), Kovri utilise les technologies [garlic encryption](https://getmonero.org/resources/moneropedia/garlic-encryption.html) et [garlic routing](https://getmonero.org/resources/moneropedia/garlic-routing.html) pour créer une surcouche à internet à la fois privée et protégée.

Kovri *recouvre* le trafic internet d'une application pour le rendre anonyme sur le réseau.

Kovri est un routeur léger et axé sur la sécurité. Il est totalement compatible avec le réseau I2P. La version alpha de Kovri est en cours de développement.

### Qui développe Kovri ?

Kovri est un projet open-source, ce qui veut dire qu'il est entièrement dépendant des contributions de la communauté.

Le lead développeur du projet est [anonimal](https://github.com/anonimal), que vous pouvez contacter via les channels IRC [#kovri](irc://chat.freenode.net/#kovri) et [#kovri-dev](irc://chat.freenode.net/#kovri), et via son [compte Twitter](https://twitter.com/0x914409F1).

Kovri est développé sous l'égide du [Monero Project](https://github.com/monero-project). C'est un autre projet open-source, qui développé le [Monero coin](https://getmonero.org) et [Open Alias](https://openalias.org). La relation entre le Monero Project et Kovri est mutuellement bénéfique dans le sens où Kovri va s'intégrer dans le réseau Monero et Monero contribue au projet Kovri en fournissant des développeurs et des ressources.

### En quoi Kovri va-t-il aider Monero ?

Le Monero est une crypto-monnaie sécurisée, privée, intraçable, fongible et confidentielle par défaut. Il utilise les technologies suivantes pour cacher respectivement le destinataire, la quantité envoyée et l'expéditeur : des adresses furtives, *RingCT* et les *Ring Signatures*. Des vulnérabilités potentielles de Monero pourraient laisser fuiter l'adresse IP qui émet la transaction.

C'est là que Kovri intervient. Kovri sera implémenté dans le wallet officiel de Monero, donc toutes les transactions passeront par le réseau anonyme Kovri et les adresses IP par lesquelles les transactions sont émises seront donc cachées. Dans le futur, toutes les transactions transiteront par défaut par Kovri. Cependant, pour des raisons d'efficacité, le téléchargement de la blockchain se fera toujours par le *clearnet* (le réseau internet classique).

### Pourquoi devrais-je utiliser Kovri plutôt que I2P ?

[I2P](https://geti2p.net) est un bon projet mais certaines choses devaient être adaptées pour pouvoir intégrer sa technologie dans Monero.

Premièrement, I2P est développé en Java et nous pensions que développer un router en C++ aiderait pour un code plus léger et plus rapide à faire tourner.

Deuxièmement, malgré que l'implémentation en Java soit bonne, elle s'accompagne de nombreuses fonctionnalités qui ne nous semblaient pas nécessaires pour l'application Monero. Nous avons donc décidé de recommencer à partir de zéro et de faire un routeur qui est JUSTE un routeur. Cette approche simplifiée est parfaite pour Monero et représente aussi une bonne nouvelle pour tous les autres qui veulent développer des applications I2P. Ils ont la possibilité d'utiliser un routeur léger sans le superflu. Et pour ceux qui ont besoin des fonctionnalités supplémentaires, ils peuvent utiliser l'implémentation Java. C'est gagnant-gagnant pour tout le monde.

### Qu'est-ce que Kovri permet déjà ?

- De devenir un nœud sur le réseau I2P
- De cacher votre localisation physique pour les sites que vous visitez
- De vous anonymiser sur IRC et vous permet d'envoyer des e-mails de manière anonyme
- D'héberger des sites et services anonymes
- De fournir du financement à des développeurs, hackers et chercheurs via FFS et HackerOne
- Il vise les standards les plus rigoureux en terme de développement et qualité de code

### Qu'est-ce qui est en cours de développement ?

- Émettre des transactions Monero à travers I2P
- Une GUI pour une utilisation et une configuration améliorées
- Une bibliothèque d'APIs pour des apps/libs externes
- Une extension Firefox pour accéder facilement aux *eepsites* (les websites hébergés sur le réseau I2P)
- Le site internet de Kovri ([getkovri.org](getkovri.org) / [kovri.i2p](kovri.i2p))
- Une documentation ehaustive

### Qu'est-ce que Kovri ne permettra pas ?

- De sacrifier votre sécurité et vie privée pour des arrière-pensées
- De fournir une interface web compliquée et pénible
- D'avoir besoin des autorités pour arriver à un consensus sur le réseau
- D'accéder à des sites internet via un "outproxy"
- D'avoir besoin d'une machine virtuelle Java ultra-performante
- De promener votre chien et de payer vos taxes

### Quel est l'état actuel de développement de Kovri ?

Nous travaillons activement sur le développement de Kovri et celui-ci est en phase pre-alpha. Kovri *n'est pas encore* intégré dans Monero, mais, en plus de certaines fonctionnalités de base, nous sommes en train de développer un [client](https://github.com/monero-project/kovri/issues/351) et une [core API](https://github.com/monero-project/kovri/issues/350) pour être utilisés par Monero ou d'autres applications.

Mais le fait que nous soyons en pre-alpha ne veut pas dire que vous ne pouvez pas utiliser Kovri. Vous pouvez déjà utiliser Kovri pour vous connecter au réseau I2P, surfer sur les *eepsites*, vous connecter sur IRC et faire tourner des *client tunnels* et *server tunnels*.

### Quand sera disponible la version alpha ?

La version alpha sera disponible (nous l'espérons !!) avant fin 2017. Une fois que nous serons en alpha, le travail commencera immédiatement sur la version beta, qui nécessitera : une API complètement implémentée, la résolution des problèmes principaux d'assurance qualité et la résolution des différents bugs.

### Sur quoi se focalise en ce moment l'équipe de développement ?

Nous travaillons actuellement sur tous les points listés sur notre [système de suivi](https://github.com/monero-project/kovri/issues/). La plupart de ce qui doit être achevé avant de sortir la version alpha officielle y est listé.

### Kovri est-il déjà utilisable et quel niveau de vie privée propose-t-il actuellement ?

Kovri est utilisable. Sur ```./kovri --help```, vous pouvez voir tout ce que Kovri offre actuellement. Kovri n'a pour le moment aucune interaction avec Monero. En ce qui concerne la vie privée, nous avons résolu de nombreux problèmes depuis le début, mais nous vous demandons de garder en tête que nous ne sommes qu'en pre-alpha.

Il y a encore beaucoup de code à écrire et à tester, donc ne vous attendez pas encore à une garantie d'anonymité telle qu'offerte par Tor ou par I2P Java. Ces projets ont plus de 10 ans derrière eux de recherche, d'implémentation et d'utilisation. A contrario, nous n'en sommes qu'au début.

N'hésitez pas à vous mettre dans le rôle d'un développeur et à jouer avec Kovri, mais seulement si *ne pas* être anonyme ne peut pas vous mettre en danger, étant donné que le risque de ne pas être complètement anonyme existe comme nous ne sommes qu'en pre-alpha (ce n'est pas unique à Kovri).

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




- Nous nous concentrons sur l'application d'un API qui peut être utilisé par n'importe quel développeur pour que n'importe quelle application peut se connecter au réseau I2P; oui, Monero aussi.
- Nous assurerons [la qualité de ce project à tous](https://github.com/monero-project/kovri/issues/58) et nous présenterons [le but de ce projet](https://github.com/monero-project/kovri-docs/blob/master/i18n/fr/contributing.md) à tous pour créer un bon logicel pour tout le monde.
- Nous appliquerons des options alternatives d'obtenir un nouveau graine pour qu'on peut utiliser [Pluggable Transports](https://www.torproject.org/docs/pluggable-transports.html.en) au lieu de HTTPS pour obtenir un nouveau graine.
- Nous appliquerons plus de fonctionnalité *(hidden mode + disabled inbound)* pour donner l'anonymat à ceux qui habitent à des pays avec des conditions extrêmes ou ceux qui sont bloqués par un pare-feu qui utilise carrier-grade NAT ou DS-Lite.
- Nous encouragerons toujours de la collaboration.
- Nous écouterons toujours à vos avis pour améliorer Kovri!

### Pourquoi avez-vous forké à partir d'i2pd ?

Nous avons forké à cause de plusieurs de raisons:

- Nous voulions application du réseau I2P en C++ qui est sécurisé et viable; Malheureusement, i2pd ne faisait plus ça.
- Nous voulions une communauté positif qui encourage de la collaboration pour améliorer le projet.
- Nous voulions un chef développeur qui peut vraiment mener.

### Quels sont les principaux facteurs qui ont amené à forker i2pd ? (Et pourquoi y a-t-il deux repos i2pd, un sur Bitbucker et un sur GitHub ?)

*Alors, les drames ont commencé*.

Au début de 2015  un développeur qui avait le droite de pusher avait pushé un commit qui le développeur original de i2pd n'a pas aimé. Ces développeurs n'int pas travaillé ensemble pour résoudre ce problème. Le développeur original avait décidé à déménager i2pd à BitBucket, et puis il a supprimé toute l'histoire sur GitHub, pour qu'il serait le seul 'contributor' du logiciel. Après ça, il disait qu'il reviendrait jamais à IRC2P.

Ces action ont offensé beaucoup de personnes de la communauté de I2P, des développeurs inclus. Ces drames ont presque terminé le projet.

En automne 2015, anonimal ne voulait pas voir que le travail de tout le monde est devenu gaspillé. Du coup, anonimal a sauvé le projet après avoir fait plusieurs de contributions et par mené le projet. Un invitaton à se rencontrer et discuter l'avenir de i2pd a été donné aux développeurs qui ont été encore actifs. Le développeur original de i2pd n'était jamais venu, mais cette réunion a apperement fait peur au développeur original de i2pd au point qu'il a [riposté](https://github.com/PurpleI2P/i2pd/issues/279) et a recommencé de travailler sur GitHub - mais avec un branche ```openssl``` (c'était simplement un dépôt BitBucket) plutôt qu'avoir utilisé le branche ```master``` qui est le branche original.

Cette genre de conduite ne fairait que mal au projet I2P. Il ne restait que quelques développeurs qui ont continué d'avoir [plusieurs de réunions](https://github.com/monero-project/kovri/issues/47). Ces réunions ont fait la fondation pour ce qui est maintenant connu comme Kovri.

## Utiliser Kovri

### J'ai trouvé une vulnérabilité, j'ai trouvé un bug, que dois-je faire ?

- Vulnérabilité: visitez notre [README](https://github.com/monero-project/kovri/blob/master/README.md)
- Bugs : visitez notre [Contributing Guide](https://github.com/monero-project/kovri-docs/blob/master/i18n/fr/contributing.md)

### Pourquoi mes logs montrent une heure différente de mon fuseau horaire ?

Logs sont enregistré en GMT pour que vous restez privé. Quand les logs sont enregistré comme ça, on peut partager ces logs sans perdre l'anonymat.