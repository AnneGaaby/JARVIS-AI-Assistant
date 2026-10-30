# Guide de mise en place — architecture similaire

> Ce guide décrit une démarche de construction, pas l'installation du J.A.R.V.I.S. privé. Le dépôt public ne contient ni son code source ni ses fichiers de configuration.

## 1. Préparer la machine

Avant de commencer, relever :
- système d'exploitation et version ;
- processeur, mémoire vive et espace disque disponible ;
- modèle de GPU ;
- version du pilote graphique ;
- disponibilité de CUDA si les composants choisis l'utilisent.

Ne pas supposer qu'un modèle ou un service fonctionnera sur toutes les configurations. Vérifier les prérequis publiés par chaque projet.

## 2. Définir les services

Séparer les responsabilités facilite les tests et le dépannage :

| Service | Responsabilité | Test initial |
|---|---|---|
| Modèle local | Générer une réponse à partir d'un prompt | Envoyer une requête à l'API locale |
| Serveur applicatif | Recevoir les demandes et coordonner les services | Tester une route simple |
| Interface web | Saisir et afficher les échanges | Ouvrir l'interface et envoyer un message |
| Reconnaissance vocale | Convertir l'audio en texte | Transcrire un fichier audio de test |
| Synthèse vocale | Convertir le texte en audio | Générer puis lire un court échantillon |
| Automatisation | Démarrer et arrêter les services | Tester chaque commande séparément |

## 3. Construire par étapes

1. Faire fonctionner le modèle local sans interface.
2. Écrire un petit serveur applicatif qui appelle ce modèle.
3. Tester le serveur avec une requête textuelle.
4. Relier une interface web au serveur.
5. Ajouter la transcription vocale sans encore intégrer la synthèse.
6. Ajouter la synthèse vocale et tester la lecture audio séparément.
7. Relier les étapes audio seulement lorsque chaque service fonctionne seul.
8. Ajouter la mémoire et mesurer son comportement entre les sessions.
9. Ajouter les outils après avoir défini les permissions et les confirmations nécessaires.

## 4. Documenter chaque installation

Pour chaque service, consigner :
- nom et version exacte ;
- système et matériel testés ;
- dépendances et versions ;
- méthode d'installation issue de la documentation officielle ;
- paramètres requis ;
- commande de démarrage et d'arrêt ;
- adresse locale et port, si nécessaire ;
- résultat attendu ;
- commande ou procédure de test ;
- erreurs connues et solution réellement vérifiée.

Ne pas publier de secrets, de jetons ou de configurations privées.

## 5. Critères de validation

Un service est « démarré » lorsque son processus se lance. Il est « testé » lorsqu'un test ciblé donne le résultat attendu. Il est « intégré » lorsque le flux entre les composants fonctionne. Il est « validé de bout en bout » lorsque le scénario complet fonctionne de façon répétable.

Ces niveaux ne doivent pas être confondus.

## 6. Limites de ce dépôt

Les versions exactes, les commandes privées, les variables d'environnement, les ports internes et les contrats d'API de J.A.R.V.I.S. ne sont pas publiés. Il n'est donc pas possible de garantir une reproduction identique à partir de cette documentation seule.
