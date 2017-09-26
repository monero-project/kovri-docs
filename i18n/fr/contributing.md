## Assurance qualité
- Voir notre guide d'[Assurance Qualité](https://github.com/monero-project/kovri/blob/master/doc/QUALITY_ASSURANCE.md) pour en savoir plus.



## Conformité
- Nous visons une complète conformité C++11/14; n'hésitez pas à l'utiliser pour vous faciliter la tâche dans votre travail
- Il est aussi vivement recommandé d'utiliser la bibliothèque standard et les bibliothèques de dépendances autant que possible

## Envoyer votre travail
Pour soumettre vos contributions, veuillez procéder de la manière suivante:

1. Fork Kovri
2. Lisez notre [style guide](https://github.com/monero-project/kovri/blob/master/doc/STYLE.md)
3. Créez une [branche thématique](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
4. [**Signez**](https://git-scm.com/book/fr/v2/Utilitaires-Git-Signer-votre-travail) votre ou vos commit(s)
5. Envoyez une *pull request* à la branche ```master```
   - Nous n'avons pas encore de tag comme nous sommes en pré-alpha. Donc pour l'instant vous pouvez fonder votre travail sur la branche master.
   - Les messages de commmit doivent être détaillés par défaut, accompagnés d'un message court d'environ 50 caractères à propos du sujet, d'une ligne blanche, et d'une explication détaillée constituée d'un ou plusieurs paragraphe(s) séparé(s) - à moins que le titre soit assez clair de lui-même.
   - Le titre du commit doit préciser la classe ou l'aspect du projet concerné. Par exemple, "HTTPProxy: implement User-Agent scrubber. Fixes #193." ou "Garlic: fix uninitialized padding in ElGamalBlock".
   - Si un commit se réfère à un autre commit ou à une *issue*, une réference doit être incluse. Par exemple "See #123", ou "Fixes #123". Cela nous aidera à résoudre les tickets quand nous mergerons dans ```master```.
   - En géneral, les commits doivent être [atomic](https://en.wikipedia.org/wiki/Atomic_commit#Atomic_commit_convention) et les différences doivent être facile à distinguer. Essayez donc de ne pas mélanger les corrections de mise en forme avec les corrections d'erreurs.
   - Le corps de la *pull request* doit contenir une description précise du but du patch et doit fournir une justifcation / un raisonnement (si nécessaire). Incluez les références aux discussions, comme les tickets ou chats IRC. 

## Propositions
Pour contribuer à une proposition, veuillez d'abord vérifier notre [liste d'*issues* existantes](https://github.com/monero-project/kovri/issues). Si ce que vous proposez n'y est pas encore, alors [ouvez une nouvelle *issue*](https://github.com/monero-project/kovri/issues/new).

Même si notre C4 nous dicte de tout merger, nous vous demandons d'ouvrir une proposition pour les raisons suivantes :

1. Une proposition permet une meilleure communication
2. Une proposition montre que le contributeur respecte les opinions des autres collaborateurs du projet
3. Une proposition permet l'apport d'autres collaborateurs dans une collaboration ouverte
4. Une proposition permet d'économiser du temps si un collaborateur est déjà en train de travailler sur une fonctionnalité ou un problème similaire
5. Une proposition permet d'éviter les catrastophes et les mésaventures ou permet aux collaborateurs de les prévoir et de s'y préparer

Ne **pas** ouvrir de proposition ne vous empêchera **pas** de contribuer ; nous mergerons votre *pull request* - mais une proposition est fortement recommandée.

## À faire
- Faire une recherche rapide dans le codebase pour ```TODO(unassigned):``` et/ou choisir un ticket et commencer à patcher !
- Si vous créez un TODO, assignez-le vous ou mettez-le dans ```TODO(unassigned):```

# [Code de Conduite (22/C4.1)](http://rfc.zeromq.org/spec:22)

## Licence

Droits d'auteur (c) 2009-2015 Pieter Hintjens.

Cette Spécification est un logiciel gratuit ; vous pouvez la redistribuer et/ou la modifier sous les termes de la *GNU General Public License* comme publiée par la *Free Software Foundation* ; version 3 ou ultérieure.

Cette Spécification est distribuée dans l'espoir qu'elle sera utile, mais SANS AUCUNE GARANTIE ; sans même l'implicite garantie d'être COMMERCIALISABLE or qu'elle ait une APTITUDE A UN USAGE PARTICULIER. Voir la *GNU General Public License* pour plus de détails.

Vous devriez avoir reçu une copie de la *GNU General Public License* avec ce code ; si ce n'est pas le cas, rendez-vous sur <http://www.gnu.org/licenses>.

## Langues

Les mots clé "DOIT", "NE DOIT PAS", "EXIGE", "DEVRAIT", "NE DEVRAIT PAS", "DEVRA", "NE DEVRA PAS", "RECOMMANDÉ", "PEUT", et "FACULTATIF" dans le présent document sont à interpréter comme décrit dans la RFC 2119.

## Buts

C4 est déstiné à fournir un modèle de collaboration optimal et réutilisable pour les projets open source. Il a pour but de :

- Maximiser la taille et la diversité de la communauté autour d'un projet, en réduisant les frictions pour les nouveaux contributeurs et en créant un modèle de participation avec des retours positifs importants ;
- Soulager les dépendances à l'égard des personnes clés en séparant les différents ensembles de compétences de sorte qu'il y ait un plus large choix de compétences disponibles dans n'importe quel domaine requis ;
- Permettre au projet de se développer plus vite et de manière plus précise, en augmentant la diversité dans le processus de prise de décision ;
- Soutenir l'évolution naturelle des différentes versions d'un projet, d'expérimental à stable, en permettant des tests sans risque, des échecs contrôlés, et l'isolation du code stable ;
- Réduire la complexité interne des dépôts de projet, rendant ainsi la contribution plus facile et réduisant la portée des erreurs éventuelles ;
- Renforcer la proprieté collective du projet, ce qui augmente l'incitation économique des contributeurs and réduit le risque de détournement par des entités hostiles. 

## Design

### Préliminaires

- Le projet DEVRAIT utiliser le système de révision de contrôle GIT.
- Le projet DEVRAIT être hébergé sur github.com ou équivalent, ci-après appelé la "Plateforme".
- Le projet DEVRAIT utiliser le tracker d'*issues* fourni par la Platerforme.
- Le projet DEVRA avoir documenté clairement l'éthique pour le style de code (*code style*).
- Un "Contributeur" est une personne qui souhaiterait fournir un patch, c-à-d un ensemble de commits qui résolvent des problèmes clairement identifiés.
- Un "Mainteneur" est une personne qui merge les patchs pour le projet. Les Mainteneurs ne sont pas des développeurs ; leur travail consiste à garantir le process.
- Les Contributeurs NE DEVRAIENT PAS avoir la permission de commit sur le dépôt à moins d'être aussi Mainteneurs.
- Les mainteneurs DEVRAIENT avoir le droit de commit sur le dépôt.
- Tout le monde, sans distinction ou discrimination, DEVRAIENT avoir un droit égal de devenir Contributeur sous les termes de ce contrat.

### Licence et Propriété

- Le projet DEVRAIT utiliser une licence partagée, comme GPLv3 ou une variante de celle-ci (LGPL, AGPL), ou MPLv2.
- Toutes les contributions au code source du projet ("patchs") DEVRAIENT utiliser la même licence que le projet.
- Tous les patchs appartiennent à leur auteur. Il NE DEVRAIT PAS y avoir de processus d'attribution du droit d'auteur.
- Les droits d'auteurs de ce projet DEVRAIENT être détenus collectivement par tous ses Contributeurs.
- Chaque Contributeur DEVRAIT être responsable de leur identification dans la liste des Contributeurs du projet.

### Exigences pour les patchs

- Les Mainteneurs et les Contributeurs DOIVENT avoir un compte sur la Plateforme et DEVRONT utiliser leurs vrais noms ou un alias habituel.
- Un patch DEVRA être une réponse minimale et répondant précisement à un problème identifié et convenu.
- Un patch DOIT se conformer au code de style du projet si celui-ci est défini.
- Un patch DOIT se conformer aux lignes directrices "Évolution des contrats publiques" définies ci-dessous.
- Un patch NE DEVRAIT PAS inclure de code non-trivial appartenant à un autre projet à moins que le Contributeur soit l'auteur original de ce code.
- Un patch DOIT compiler proprement et passer les tests qui lui sont destinés au moins sur la plateforme cible principale.
- Un message de commit d'un patch DEVRA consister en un bref résumé des changements (moins de 50 caractères), qui peut éventuellement être suivi d'une ligne blanche puis d'un descriptif plus détaillé.
- Un "Patch Correct" est un patch qui remplit les conditions énoncées ci-dessus.

### Procédure de développement

- Les changements sur le projet DEVRAIENT être gouvernés par le principe d'identifier précisement les problèmes et d'y appliquer des solutions minimales et précises.
- Pour proposer un changement, un utilisateur DEVRA créer une *issue* dans le *tracker* d'*issues* de la Plateforme.
- L'utilisateur ou le Contributeur DEVRA écrire l'*issue* en décrivant le problème observé.
- L'utilisateur ou le Contributeur DEVRA chercher à atteindre un consensus sur la précision de leur observation et la valeur ajoutée de la résolution du problème.
- Les utilisateurs NE DEVRAIENT PAS créer de requêtes de fonctionnalités, idées, suggestions ou solutions à des problèmes qui ne sont pas explicitement documentés et démontrables.
- Ainsi, l'historique du projet DEVRAIT être une liste d'*issues* listées et résolues.
- Pour travailler sur une *issue*, un Contributeur DEVRAIT forker le dépôt du projet et travailler sur sa fork.
- Pour soumettre un patch, un Contributeur DEVRAIT créer une *pull request* sur le dépôt du projet sur la Plateforme.
- Un contributeur NE DEVRAIT PAS commit ses changements directement sur le projet.
- Si la Platerforme implémente les *pull requests* comme des *issues*, un Contributer PEUT directement envoyer une *pull request* sans créer une *issue* supplémentaire.
- Pour discuter à propos d'un patch, les gens PEUVENT commenter sur la *pull request*, sur le commit ou autre part.
- Pour accepter ou rejeter un patch, un Mainteneur DEVRAIT utiliser l'interface de la Plateforme.
- Les Mainteneurs NE DEVRONT PAS merger leurs propres patchs à part dans des cas exceptionnels, comme par exemple la non réaction de la part des autre Mainteneurs pendant une durée supérieure à un ou deux jours.
- Les Mainteneurs NE DEVRAIENT PAS faire de jugement de valeur sur des patchs corrects.
- Les Mainteneurs DEVRAIENT merger rapidement les patchs corrects des autres Contributeurs.
- Le Contributeur PEUT tagger une *issue* "*Ready*" après avoir fait une *pull request* la concernant.
- L'utilisateur qui a créé une *issue* DEVRA la fermer après avoir verifié que le patch l'a bien corrigée.
- Les mainteneurs DEVRONT demander des améliorations pour les patchs incorrects et DEVRONT les rejeter si le Contributeur ne répond pas de façon constructive.
- Si un Contributeur a un jugement de valeur sur un patch correct, il DEVRA s'exprimer en créant son propre patch.
- Les mainteneurs PEUVENT commit directement les changements qui ont trait à de la documentation non liée à du code source.

### Créer des versions stables

- Le projet DEVRAIT avoir une branche ("master") qui possède toujours la dernière version en développement et qui DEVRA toujours build.
- Le projet NE DEVRAIT PAS utiliser de branche thématique. Les forks personnelles PEUVENT utiliser des branches thématiques.
- Pour faire une version stable quelqu'un DEVRAIT forker le dépôt en le copiant et ainsi devenir mainteneur de ce dépôt.
- Forker un projet pour le stabiliser PEUT être fait unilatéralement et sans accord des mainteneurs du projet.
- Un projet de stabilisation DEVRA être maintenu par le même processus que le projet principal.
- Un patch appliqué à un projet stabilisé déclaré "stable", DEVRAIT être accompagné par un cas de test reproductible.

### Évolution des contrats publiques

- Tous les Contrats Publiques (APIs ou protocoles) DEVRAIENT être documentés.
- Tous les Contrats Publiques DEVRONT avoir un espace pour être étendus et pour des expérimentations.
- Un patch qui modifie un Contrat Publique stable NE DEVRA PAS casser les applications existantes à moins qu'il y ait un consensus sur la valeur ajoutée que cela apporterait.
- Un patch qui introduit de nouvelles fonctionnalitées pour un Contrat Publique DEVRA utiliser de nouveau noms.
- Les vieux noms DEVRONT être *deprecated* de façon systématique en marquant les nouveau noms du terme "*experimental*" jusqu'à ce qu'ils soient stables, pour ensuite marquer les vieux noms comme "*deprecated*".
- Quand suffisamment de temps a passé, les noms *deprecated* DEVRONT être marqués "*legacy*" et seront finalement supprimés.
- Les noms *deprecated* NE DEVRAIENT PAS être utilisés dans des nouvelles fonctionnalités.
- Quand les noms *deprecated* sont supprimés, leurs implémentations DOIVENT provoquer une exception (*assertion*) si ils sont utilisés par les applications.

### Administration du projet

- Les fondateurs du projet DEVRAIENT se comporter comme des administrateurs pour gérer l'ensemble des Mainteneurs du projet.
- Les administrateurs DEVRAIENT assurer leur propre succession en promouvant les Mainteneurs les plus efficaces.
- Un nouveau Contributeur qui fait un patch correct DEVRAIT être invité à devenir Mainteneur.
- Les administrateurs PEUVENT supprimer les Mainteneurs qui sont inactifs pendant une longue période, ou qui n'appliquent pas le processus correctement de manière répétée.
- Les admins DEVRONT bloquer ou bannir "les mauvais acteurs" qui causent du stress et de la difficulté aux autres dans le projet. Cela doit être fait à la suite d'une discussion publique, avec la possibilité pour chacun d'exprimer son point de vue. Un mauvais acteur est quelqu'un qui ignore de manière répétée les règles et la culture du projet, qui est inutilement chicanier et hostile, ou qui est offensant, et qui est incapable de se comporter de façon correct même quand les autres le lui demandent.

# Processus de gouvernance.

![Processus de gouvernance](https://getmonero.org/blog/assets/2015-year-in-review/governance-process.jpg)