# Assurance Qualité (QA)

Ce qui suit est une proposition de procédure pour la QA. Bien que linéaire de nature, chaque étape peut être effectuée de manière individuelle si besoin - à condition que chaque étape soit abordée au final.

## Étape 1 : Revue de base

- Passez en revue les *open issues* sur notre [*Tracker d'Issues*](https://github.com/monero-project/kovri/issues/)
- Lisez notre [Processus de Réponse à toute Vulnerabilité](https://github.com/anonimal/meta/blob/master/VULNERABILITY_RESPONSE_PROCESS.md)
- Le code doit respecter nos lignes directrices de contribution
- Notez les domaines qui doivent être améliorés (mentalement ou dans le code)
- Créez des TODOs et assignez-les dans la mesure du possible

## Étape 2 : Revue de specs / Implémentation / Documentation du code

- Faites une revue de specs complète par module, p.ex. Streaming, I2PControl, etc.
  - Le code doit être en ligne avec les parties essentielles des specs qui vont garantir le même (ou un meilleur) niveau d'anonymat que proposé par java I2P
  - Refactorez/implémentez/patchez quand et où c'est nécessaire
- Garantissez une implémentation conforme à C++11/14
  - Revoyez l'étape 2 si besoin
- Résolvez tous les TODOs liés
- Documentez le code autant que possible avec des commentaires dans le code et Doxygen
  - Le code doit être compréhensible pour les codeurs novices autant qu'expérimentés
  - Le code devrait amener le lecteur à mieux comprendre I2P
    - I2P est très complexe donc le code devrait se substituer à la doc et pas seulement la compléter (ça peut sembler être un objectif fastidieux mais il s'avérera gratifiant en terme de maintenance et de durée de vie)

## Étape 3 : Revue de la crypto / Audit de sécurité

- Garantissez que la crypto est à jour et bien implémentée
- Listez tous les vecteurs d'attaques connues
  - Gardez ces attaques en tête pendant que vous écrivez les tests
- Cassez Kovri par tous les moyens possibles
  - Résolvez ce que vous avez cassez
- Utilisez toujours des bibliothèques bien écrites et dignes de confiance
  - Évitez les types de code *homebrewed*, *ad-hoc* et *"Je suis sûr que je m'y connais plus que la communauté"*
- Essayez d'avoir l'opinion d'un collègue (ou plus) avant d'avancer à la phase suivante

## Étape 4 : Résolution de bugs / Tests / Performance

- Résolvez les bugs/*issues* prioritaires
- Écrivez des tests unitaires pour tous les modules
  - Lancez les tests. Lancez-les de nouveau
  - Faites une revue complète des résultats des tests. Patchez si nécessaire. Refactorez si nécessaire
- Assurez-vous régulièrement que l'automatisation fonctionne 
  - valgrind, doxygen, clang-format
  - Patchez si nécessaire, refactorez si nécessaire

## Étape 5 : Discussion

- Conversez avec des collègues de la communauté
  - Les discussions doivent se faire de manière publique via des *tickets*, des réunions, et/ou par chat sur IRC
- Acceptez tous les feedbacks et, en réponse, produisez des résultats tangibles
- Si c'est satisfaisant, avancez à l'étape suivante, ou bien répétez cette étape-ci (ou repartez d'une étape précédente)

## Étape 6 : Répétez le cycle depuis le début
