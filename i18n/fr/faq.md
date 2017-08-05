# La FAQ (et des reponses)

## Qu'est-ce que Kovri?
Kovri est une application du réseau anonyme I2P en C++ qui est sécurisé, privée, et inretrouvable. C'était un fork de i2pd au début, mais Kovri est devenu un projet unique qui est développé activement par la communauté. Ce nouveu projet a beaucoup d'améliorations. Il y a surtout des améliorations de sécurité et aussi des nouvelles fonctionnalités.

Lire la suite à [Moneropedia](https://getmonero.org/resources/moneropedia/kovri.html).

## Qu'est-ce que c'est l'état de Kovri actuallment?
L'equipe de développment travaille activement sur une version pre-alpha. Kovri **n'est pas** intégré avec Monero en ce moment mais, avec plusieurs d'autre fonctionnalité, nous développons un [client](https://github.com/monero-project/kovri/issues/351) et [core](https://github.com/monero-project/kovri/issues/350) API pour Monero et des autres applications.

Actuallment, on peut utiliser Kovri pour se connecter à (et participer au) réseau I2P: naviguer des eepsites, se connecter à IRC, et plus.

## Quand est-ce que la première version de Kovri va sortir?
Nous allons essayer de sortir une version alpha pendant 2017. Après d'avoir confirmé le qualité du projet et d'avoir complètement implémenté un API, nous sortirons une version beta.

## Pourquoi est-ce que mes logs montre un fuseau horaire différent du fuseau horaire chez moi?
Logs sont enregistré en GMT pour que vous restez privé. Quand les logs sont enregistré comme ça, on peut partager ces logs sans perdre l'anonymat.

## L'equipe de développment travaille sur quoi actuallment?
Actuallment, nous travillons sur tous les problèms sur notre [issues tracker](https://github.com/monero-project/kovri/issues/). Ils sont sur tous ce qu'il faut être fini avant de sortir une version (alpha, beta, ou meilleur) officielle.

## Est-ce qu'on peut vraiment utiliser Kovri en ce moment?
On peut utiliser ce que ```./kovri --help``` offre. Actuallment, Kovri n'est pas intégré avec Monero. Nous avons réparé plusieurs de problèms de sécurité depuis le début, mais le projet est toujours une version pre-alpha.

Ce projet est encore en cours de développment, donc nous ne pouvons pas garantir qu'il y aura toujours du anonymat qui est aussi fort que Tor ou même java I2P. Ces projets ont été recherché depuis 10+ ans - Nous sommes en cours de commencer juste maintenant.

N'hésitez pas à expérimenter avec Kovri, mais seulement si vous **n'avez pas** besion d'être anonyme pour rester en sécurité - car il y aura toujours possible que vous serez de-anonymé parce que Kovrie est encore une versions pre-alpha (tous les projets sont comme ça).

## Informations de contact?
Visitez notre [README](https://github.com/monero-project/kovri/blob/master/README.md).

## Pourquoi est-ce que je devrais utiliser Kovri au lieu de i2pd?

- La sécurité: Nous voulons un logicel sécurisé; nous ne voulons pas [précipiter](https://github.com/monero-project/kovri/issues/65) justement pour sortir un projet.
- La qualité: Vous soutiendrez un projet qui va durer longtemps.
- Monero: Vous soutiendrez un crypto-monnaie qui reste privé et anonyme.

## Qu'est-ce qui différencie Kovri de i2pd?

- Nous fournissons un [Forum de financements](https://forum.getmonero.org/8/funding-required) pour le développement de nouvelles fonctionnalités.
- Nous nous concentrons sur la création d'un logicel qui est ["secure by default"](http://www.openbsd.org/security.html), et plus à maintenir.
- Nous nous concentrons sur l'application d'un API qui peut être utilisé par n'importe quel développeur pour que n'importe quelle application peut se connecter au réseau I2P; oui, Monero aussi.
- Nous assurerons [la qualité de ce project à tous](https://github.com/monero-project/kovri/issues/58) et nous présenterons [le but de ce projet](https://github.com/monero-project/kovri-docs/blob/master/i18n/fr/contributing.md) à tous pour créer un bon logicel pour tout le monde.
- Nous appliquerons des options alternatives d'obtenir un nouveau graine pour qu'on peut utiliser [Pluggable Transports](https://www.torproject.org/docs/pluggable-transports.html.en) au lieu de HTTPS pour obtenir un nouveau graine.
- Nous appliquerons plus de fonctionnalité *(hidden mode + disabled inbound)* pour donner l'anonymat à ceux qui habitent à des pays avec des conditions extrêmes ou ceux qui sont bloqués par un pare-feu qui utilise carrier-grade NAT ou DS-Lite.
- Nous encouragerons toujours de la collaboration.
- Nous écouterons toujours à vos avis pour améliorer Kovri!

## Pourquoi est-ce que vous avez forké de i2pd?

Nous avons forké à cause de plusieurs de raisons:

- Nous voulions application du réseau I2P en C++ qui est sécurisé et viable; Malheureusement, i2pd ne faisait plus ça.
- Nous voulions une communauté positif qui encourage de la collaboration pour améliorer le projet.
- Nous voulions un chef développeur qui peut vraiment mener.

## Que sont-ils les plus grandes raisons pour lesquelles vous avez forké (et pourquoi est-ce qu'il y a 2 dêpots de i2pd: 1 dépôt sur BitBucket et 1 dépôt sur GitHub)?

*Alors, les drames ont commencé*.

Au début de 2015  un développeur qui avait le droite de pusher avait pushé un commit qui le développeur original de i2pd n'a pas aimé. Ces développeurs n'int pas travaillé ensemble pour résoudre ce problème. Le développeur original avait décidé à déménager i2pd à BitBucket, et puis il a supprimé toute l'histoire sur GitHub, pour qu'il serait le seul 'contributor' du logiciel. Après ça, il disait qu'il reviendrait jamais à IRC2P.

Ces action ont offensé beaucoup de personnes de la communauté de I2P, des développeurs inclus. Ces drames ont presque terminé le projet.

En automne 2015, anonimal ne voulait pas voir que le travail de tout le monde est devenu gaspillé. Du coup, anonimal a sauvé le projet après avoir fait plusieurs de contributions et par mené le projet. Un invitaton à se rencontrer et discuter l'avenir de i2pd a été donné aux développeurs qui ont été encore actifs. Le développeur original de i2pd n'était jamais venu, mais cette réunion a apperement fait peur au développeur original de i2pd au point qu'il a [riposté](https://github.com/PurpleI2P/i2pd/issues/279) et a recommencé de travailler sur GitHub - mais avec un branche ```openssl``` (c'était simplement un dépôt BitBucket) plutôt qu'avoir utilisé le branche ```master``` qui est le branche original.

Cette genre de conduite ne fairait que mal au projet I2P. Il ne restait que quelques développeurs qui ont continué d'avoir [plusieurs de réunions](https://github.com/monero-project/kovri/issues/47). Ces réunions ont fait la fondation pour ce qui est maintenant connu comme Kovri.

## J'ai découvert un vulnérabilité! J'ai trouvé un bug! Qu'est-ce qu'il faut faire?
- Vulnérabilité: visitez notre [README](https://github.com/monero-project/kovri/blob/master/README.md)
- Bugs : visitez notre [Contributing Guide](https://github.com/monero-project/kovri-docs/blob/master/i18n/fr/contributing.md)
