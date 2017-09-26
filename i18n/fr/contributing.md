## Assurance qualité
- Voir notre guide d'[Assurance Qualité](https://github.com/monero-project/kovri/blob/master/doc/QUALITY_ASSURANCE.md) pour en savoir plus.



## Conformité
- Nous ésperons compléter la conformité C++11/14; n'hésitez pas à l'utiliser pour vous faciliter la tâche dans votre travail
- Il est aussi vivement recommandé d'utiliser la librairie standard et les bibliothèques de dépendances si vous le pouvez

## Envoyer votre travail
Pour mettre à contribution votre travail, veuillez procéder de la façon suivante:

1. Fork Kovri
2. Lisez notre [style guide](https://github.com/monero-project/kovri/blob/master/doc/STYLE.md)
3. Creez une [branche pour le sujet concerné](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
4. [**Signez**](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work) votre ou vos commit(s)
5. Envoyez une pull-request à la branche ```master```
   - Nous n'avons pas encore de tags du au fait que nous soyons en pré-alpha. Donc pour l'instant vous pouvez directement travailler dans la branche master.
   - Les messages de commmit doivent être détaillés par défaut, accompagné d'un message court d'environ 50 caractères à propos du sujet, une ligne blanche, et d'un texte détaillé expliquatoire constitué d'un ou plusieurs paragraphe(s) séparés - à moins que le titre explique à lui même le commit.
   - Le titre du commit doit préciser la class ou l'aspect du projet concerné. Par exemple, "HTTPProxy: implement User-Agent scrubber. Fixes #193." ou "Garlic: fix uninitialized padding in ElGamalBlock".
   - Si un commit particulier se réfère à un autre problème, veuillez dans ce cas ajouter une réference. Par exemple "Voir #123", ou "#123 résolu". Cela nous aidera à résoudre les tickets quand nous mergerons dans ```master```.
   - En géneral, les commits doivent être [atomic](https://en.wikipedia.org/wiki/Atomic_commit#Atomic_commit_convention) et les différences doivent être facile à distinguer. C'est pour cette raison que je vous demande d'essayer de ne pas mélanger les problèmes totalement résolus des commits qui ne résolvent pas totalement l'erreur.
   - Le corps de la pull request doit contenir une description précise de ce que le patch fait and fournir une justifcation/ un raisonnement pour le patch (si nécessaire). Vous devez inclure les réferences aux discussions telles que les autres tickets ou chats sur IRC. 

## Propositions
Pour contribuer à une proposition, veuillez vérifier sur nos [problèmes existants](https://github.com/monero-project/kovri/issues) pour les problèmes déjà évoqués. Si ce que vous proposez n'est pas déjà évoqué ici, alors [Ouvez un nouveau problème](https://github.com/monero-project/kovri/issues/new).

Même si notre C4 dit que nous mergeons tout, nous demandions que vous ouvriez une proposition pour les raisons suivantes:

1. Une proposition permet une communication
2. Une proposition montre que le contributeur respecte les potentielles aides des autres collaborateurs du projet
3. Une proposition permet l'aide facile d'un collaborateur dans un forum ouvert
4. Une proposition économise du temps si un collaborateur est entrain de travailler sur la même fonctionnalité ou le même problème
5. Une proposition évite les catrastophes et les mésaventures ou permet aux collaborateurs de les prévoir et de les éviter

Ne *pas* ouvrir une proposition ne va *pas* vous empêcher d'y contribuer; nous mergerons votre pull request - mais une proposition est fortement recommandée.

## A faire
- Faire une recherche rapide dans le codebase pour  ```TODO(unassigned):``` and/ou prendre un ticket and commencer à patcher!
- Si vous créez une TODO, assignez là à vous même ou écrivez dans ```TODO(unassigned):```

# [Code de Conduite (22/C4.1)](http://rfc.zeromq.org/spec:22)

## Licence

Droits d'auteur (c) 2009-2015 Pieter Hintjens.

Cette Spécification est un logiciel gratuit; vous pouvez la redistribuer et/ou la modifier sous les  termes de la Licence génerale publique GNU comme publiée par la Fondation de Logiciel Gratuit; ou la 3ème version de la Licence, ou autre version ultérieures.

Cette Specification est distribuée dans l'espoir qu'elle sera utile, but SANS AUCUNES GARANTIE; sans même l'implicite garantie d'être COMMERCIALISABLE or qu'elle ait une APTITUDE A UN USAGE PARTICULIER. Voir la Licence génerale publique GNU pour plus de détails.

## Langues
Les mots clés "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" dans ce document doivent être interprétés comme décrit dans RFC 2119.

## Buts

C4 is  a reusable optimal collaboration model for open source software projects. It has these specific goals:
C4 is déstiné à fournir un modèle de collaboration optimale réutilisable pour d'autre projets open source. Il a pour but:

- De maximiser la taille et la diversité de la communité autour du projet, en réduisant les fictions for les nouveaux contributeurs et en créant un modèle de participation à l'échelle avec de forts retours positifs.
- De soulager les bibliothèques sur des personnes clés en séparant les différents sets de compétences de sorte qu'il y ait un plus large choix de compétences disponibles dans les domaines choisis.
- De permettre au projet de se développer plus vite and plus précisément, en augmentant la diversité du processus de prise de décision.
- De soutenir le cycle naturel de vie des versions de projets, de l'expérimental au stable, en permettant des expériences sans risque, des échecs rapides, et l'isolation du code stable.
- De réduire la complexité interne  des dépôts de projet, permettant ainsi aux contributeurs de participer and réduisant ainsi la portée des erreurs possibles.
- De renforcer la proprieté collective du projet, qui augmente l'incitation économique des contributeurs and réduit le risque de détournement par des entités hostiles. 


## Design

### Préliminaires

- The project SHALL use the git distributed revision control system.
- The project SHALL be hosted on github.com or equivalent, herein called the "Platform".
- The project SHALL use the Platform issue tracker.
- The project SHOULD have clearly documented guidelines for code style.
- A "Contributor" is a person who wishes to provide a patch, being a set of commits that solve some clearly identified problem.
- A "Maintainer" is a person who merges patches to the project. Maintainers are not developers; their job is to enforce process.
- Contributors SHALL NOT have commit access to the repository unless they are also Maintainers.
- Maintainers SHALL have commit access to the repository.
- Everyone, without distinction or discrimination, SHALL have an equal right to become a Contributor under the terms of this contract.

- Le projet UTILISE le système de révision de contrôle fourni par GIT.
- Le projet EST HERBERGÉ par github.com ou l'équivalent, ci-après appelé la "Plateforme".
- Le projet UTILISE le tracker de problème fourni pour la Platerforme.
- Le projet doit avoir documenté clairmement l'éthique pour le style de code (codestyle).
- Un "Contributeur" est une personne qui souhaiterait fournir un patch, étant un ensemble de commits résolvent des problèmes clairement identifiés.
- Un "Mainteneur" est une personne qui merge les patchs pour le projet. Les mainteneurs ne sont pas des développeurs; leur travail consiste à mettre en vigueur le processus.
- Les contributeurs ne PEUVENT PAS commit le répertoire à moins d'être aussi Mainteneurs.
- Les mainteneurs PEUVENT commit le répertoire.
- Tout le monde, sans distinction ou discrimination, ONT un droit égal de devenir un Contributeur sous les termes de ce contrat.

### Licences et Possessions

- Le projet UTILISE une licence partagée, comme GPLv3 ou une variante de celui-ci (LGPL, AGPL), ou MPLv2.
- Toutes les contributions au code source du projet ("patchs") UTILISENT la même licence que le projet.
- Toutes les patchs appartiennent à leur auteur. Il n'Y A PAS de processus d'attribution du droit d'auteur
- Les droits d'auteurs de ce projet SONT détenus collectivement par tout ses Contributeurs.
- Chaque Contributeur EST responsable de leur identification dans la liste des Contributeur du projet.

### Patch Requirements

- Les mainteneurs and les Contributeurs ONT un compte Plateforme and doivent utiliser leur vrais noms ou un alias habituel.
- Un patch EST une réponse minîme et précise à précisement un problème identifié et défini.
- Un patch ADHERE au code de style du projet si celui-ci est défini.
- Un patch ADHERE à l'"Evolution de contrats publiques" défini ci-dessous.
- Un patch n'INCLUT PAS du code non-trivial d'autres projets à moins que le Contributeur est l'auteur original de ce code.
- Un patch COMPILE proprement and réussit les tests déstinés à celui-ci pour au moins la platerforme cible principale.
- Un message de commit d'un patch doit consister en un résumé bref (moins de 50 caractères) des changements, pouvant être suivi d'une ligne blanche et ensuite d'un descriptif plus détaillé.
- Un "Patch correcte" remplit les conditions énnoncées ci-dessus.

### Procédure de développement

- Les changements du projet SONT GOURVERNÉS par le principe d'identifier précisement les problèmes et d'y appliquer des solutions minimales et précises.
- Pour proposer des changements, un utilisateur doit créer une issue dans le tracker de problèmes du projet Plateforme.
- L'utilisateur ou le Contributeur doit écrire l'issue en décrivant le problème observé.
- L'utilisateur ou le Contributeur doit estimer la précision de leur observation et la valeur de la résolution de leur problème.
- Les utilisateurs ne CRÉENT PAS de requêtes de fonctionnalités, idées, suggestions ou quelconque solutions aux problèmes qui ne sont pas explicitement documentés et founis.
- Ainsi, la sortie finale du projet EST une liste de problèmes observés puis fixés.
- Pour travailler sur un problème, un Contributeur FORK le répertoire du projet and travaille ensuite sur leur répertoire fork.
- Pour soumettre un patch, un Contributeur CRÉE une requête Plateforme pour le projet.
- Un contributeur ne COMMIT PAS directement les changements sur le projet.
- Si Platerforme intérpréte les requêtes comme des problèmes, alors un Contributer peut directement envoyé une requête sans crée un problème séparé.
- Pour discuter à propos d'un patch, les gens doivent commenter la requête Plateforme, sur le commit ou autre part.
- Pour accepter ou rejeter un patch, un Mainteneur UTILISE l'interface Platerforme.
- Les mainteneurs ne doivent pas merge leur propre patchs excepté dans des cas spéciaux, comme une non réaction de la part des autre Mainteneurs pendant une période supérieur à un ou deux jours.
- Mainteneurs ne FONT PAS de jugement de valeur sur les patchs corrects.
- Mainteneurs MERGENT les patchs corrects des autres Contributeurs rapidement.
- Le Contributeur est prié de taggé le problème comme "Prêt" après avoir fait une requête le concernant.
- L'utilisateur qui a crée le problème doit fermé le problème après avoir verifié que le patch a bien corrigé celui-ci.
- Les mainteneurs doivent demander des améliorations pour les patchs incorrects and doivent rejeter les patchs incorrects si le Contributeur ne répond pas de façon constructive.
- N'importe quel Contributeur qui a un jugement de valeur sur un patch correct devrait s'exprimer en créant son propre patch.
- Les mainteneurs sont priés de commit les changements appliqués aux documentations non-sourcé directement au projet.
- 

### Créer des sorties stables

- Le projet POSSEDE une branche ("master") qui possède toujours la dernière version en progrès and doit l'avoir build.
- Le projet n'UTILISE PAS les branches de sujet pour n'importe quelle raison. Les forks personnels doivent utilisés ces branches de sujet.
- Pour faire une sortie stable quelqu'un FORK le répertoire en le copiant and ainsi devient mainteneur de ce répertoire.
- Fork un projet pour le stabiliser doit être fait unilatéralement and sans accord des mainteneurs du projet.
- Un projet stable doit être maintenu par le même processus que le projet principal.
- Un patch appliqué à un projet stabilisé, déclaré "stable", EST ACCOMPAGNÉ d'un cas de test reproductible.



### Evolution des contrats publiques

- Tous les contrats publiques (APIs ou protocoles) SONT DOCUMENTÉS.
- Tous les contrats publiques doivent avoir un espace pour une extension et pour des expérimentations.
- Un patch qui modifie un contrat publique stable ne doit pas faire disfonctionner les applications existantes à moins que qu'il y ait un consensus d'effacement pour faire ça.
- Un patch qui introduit de nouvelles fonctionnalitées pour un contrat publique doit utiliser de nouveau noms.
- Les vieux noms doivent être dépréciés de façon systématique en marquants ces nouveau noms du terme "expérimental" jusqu'à ce qu'ils soient stables, pour ensuite marquer les vieux noms du termes "déprécié".
- Quand suffisamment de temps a passé, les vieux noms doivent être marqués "héritage" et éventuellement supprimés.
- Les vieux noms ne SONT PAS RÉUTILISÉS par des nouvelles fonctionnalités.
- Quand les vieux noms sont supprimés, leur implémentaions PROVOQUENT une exception si ils sont utilisés par les applications.

### Administration du projet

- The project founders SHALL act as Administrators to manage the set of project Maintainers.
- The Administrators SHALL ensure their own succession over time by promoting the most effective Maintainers.
- A new Contributor who makes a correct patch SHALL be invited to become a Maintainer.
- Administrators MAY remove Maintainers who are inactive for an extended period of time, or who repeatedly fail to apply this process accurately.
- Administrators SHOULD block or ban "bad actors" who cause stress and pain to others in the project. This should be done after public discussion, with a chance for all parties to speak. A bad actor is someone who repeatedly ignores the rules and culture of the project, who is needlessly argumentative or hostile, or who is offensive, and who is unable to self-correct their behavior when asked to do so by others.

- Les fondateurs du projet SE COMPORTENT comme des Admin pour gérer l'ensemble des Mainteneurs du projet.
- Les Admins ASSURENT leur propre succession en promouvant les Mainteneurs les plus efficaces.
- Un nouveau contributeur qui fait un patch correct EST INVITÉ à devenir Mainteneur.
- Les admins sont priés de supprimer les Mainteneurs qui sont inactifs pendant une période trop longue, ou n'appliquent pas le processus répétivement.
- Les admins doivent blocker ou bannir "les mauvais acteurs" qui causent du stress et de la douleur aux autres dans le projet. Cela doit être fait après une discussion génerale, avec une chance pour tous les partis de parler. Un mauvais acteur est quelqu'un qui ignore plusieurs fois les règlent and la culture du projet, qui est sans arguments ou hostile, ou qui est offensant, and qui est incapable de se comporter de façon correct quand les autres lui demandent.


# Processus de gouvernance.

![Processus de gouvernance](https://getmonero.org/blog/assets/2015-year-in-review/governance-process.jpg)