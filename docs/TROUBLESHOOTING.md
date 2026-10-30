# Dépannage et diagnostic

Cette page regroupe les difficultés observées pendant le développement et une méthode de diagnostic. Elle ne présente pas une solution comme vérifiée si elle n'a pas été testée.

## Le microphone n'est pas détecté

**Contexte observé :** des difficultés ont été rencontrées avec un microphone sans fil Logitech.

À vérifier :
1. confirmer que Windows détecte le périphérique d'entrée ;
2. sélectionner le bon périphérique dans les paramètres audio ;
3. vérifier les autorisations microphone de l'application ;
4. effectuer un enregistrement indépendant de J.A.R.V.I.S. ;
5. vérifier le format et la fréquence d'échantillonnage attendus par le service audio ;
6. consulter les journaux du serveur de reconnaissance.

Tester le microphone séparément permet de savoir si le problème vient de Windows, du périphérique, de l'application ou du service Whisper.

## Whisper démarre, mais la conversation vocale ne fonctionne pas

Un service qui indique que le modèle est chargé ne prouve pas que le flux complet fonctionne.

Tester séparément :
- capture d'un fichier audio ;
- transcription de ce fichier ;
- réception du texte par le serveur applicatif ;
- envoi du texte au modèle ;
- retour de la réponse à l'interface.

## Kokoro démarre, mais aucune réponse audio n'est entendue

Vérifier indépendamment :
1. que le service est actif ;
2. que le modèle et les ressources vocales sont chargés ;
3. qu'une requête de synthèse produit un fichier ou un flux audio ;
4. que le format audio est pris en charge par le lecteur ;
5. que le périphérique de sortie correct est sélectionné.

Le démarrage du service Kokoro avec CUDA a été observé pendant les essais. La chaîne complète jusqu'à la lecture dans l'interface reste à valider.

## Problèmes CUDA, PyTorch ou GPU

Les incompatibilités peuvent provenir des versions des pilotes, de CUDA, de PyTorch ou des dépendances du modèle.

Méthode :
- relever les versions exactes ;
- consulter les journaux complets de démarrage ;
- vérifier que le GPU est détecté par l'environnement concerné ;
- comparer les versions avec les prérequis officiels du composant ;
- modifier un seul élément à la fois et refaire le même test.

Ne pas copier une combinaison de versions provenant d'une autre machine sans vérifier sa compatibilité.

## Un service ne démarre pas

- vérifier la commande et le répertoire de travail ;
- lire le premier message d'erreur, pas seulement les dernières lignes ;
- vérifier les dépendances et les variables nécessaires ;
- vérifier qu'un autre processus n'utilise pas déjà le port ;
- démarrer le service seul avant de tester l'orchestration.

## Docker ou OpenHands ne fonctionne pas comme prévu

- vérifier l'état du moteur Docker ;
- vérifier l'image et sa version ;
- lire les journaux du conteneur ;
- vérifier les volumes et les permissions ;
- limiter les dossiers montés et les accès réseau.

Ne pas donner à un environnement d'exécution des droits administrateur ou un accès complet au système sans justification.

## Règle de diagnostic

Toujours isoler le composant, reproduire le problème, conserver les journaux utiles en supprimant les secrets, corriger une variable à la fois et refaire le même test. Documenter le résultat réel.
