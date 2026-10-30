# Politique de sécurité

Ce dépôt est une documentation publique d'un prototype personnel. Le code source interne et les configurations privées ne sont pas publiés.

## Ne pas publier

- mots de passe, clés API, jetons et certificats privés ;
- adresses IP privées, identifiants réseau ou liens d'accès personnels ;
- fichiers de configuration réels contenant des secrets ;
- données personnelles, conversations privées ou fichiers de travail ;
- scripts qui exposent des chemins personnels ou des informations sensibles.

## Accès aux fichiers et exécution de commandes

Toute fonction qui permet à un assistant IA de lire, modifier ou supprimer des fichiers, ou d'exécuter des commandes, doit appliquer :
- le principe du moindre privilège ;
- une liste explicite de dossiers et d'actions autorisés ;
- une confirmation humaine pour les actions sensibles ou destructives ;
- une isolation des processus lorsque cela est possible ;
- une journalisation sans secrets ;
- une stratégie de sauvegarde et de récupération.

## Dépendances et services locaux

- utiliser des sources officielles pour installer les dépendances ;
- vérifier les images et versions des conteneurs ;
- ne pas exposer les interfaces locales sur Internet sans protection ;
- conserver les secrets hors du dépôt ;
- mettre à jour les composants selon leur politique de sécurité.

## Signaler un problème

Ne publiez jamais de secret ou de donnée privée dans une issue publique. Pour signaler un problème lié à ce dépôt, contactez l'autrice via son profil GitHub : https://github.com/AnneGaaby
