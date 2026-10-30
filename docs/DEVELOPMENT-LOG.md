# Journal de développement

Ce document résume les expérimentations connues. Il distingue le démarrage d'un composant de la validation d'une fonctionnalité complète.

## Environnement

- Poste Windows 11 avec GPU NVIDIA.
- LM Studio pour exécuter des modèles de langage localement.
- Serveur applicatif Python et interface web locale.
- PowerShell pour l'orchestration sous Windows.
- Docker pour les expérimentations de services isolés.

## Serveur et interface

Le projet comprend un serveur Python et une interface accessible depuis un navigateur. Les fichiers de travail incluent notamment `server.py` et une variante `server_com_memoria.py`. Le serveur a été lancé et l'interface locale ouverte pendant les essais.

## Modèles locaux

LM Studio a été utilisé pour charger et exposer des modèles localement. Plusieurs modèles ont été explorés, notamment dans la famille Qwen. Gemma a également été envisagé. Le modèle actif peut varier selon les essais.

## Reconnaissance vocale

Un service Whisper a été lancé avec le modèle large-v3. Les journaux ont confirmé le chargement du modèle, l'utilisation de CUDA et le calcul en float16. Des essais avec le microphone ont été effectués, mais la chaîne complète jusqu'à une réponse audible doit encore être stabilisée.

## Synthèse vocale

Un service Kokoro a d'abord rencontré un problème de démarrage lié à la compatibilité de l'environnement logiciel et du GPU. Un lancement ultérieur a réussi : CUDA était disponible, le modèle était chargé et les ressources vocales étaient détectées. La lecture audio depuis l'application doit encore être validée de bout en bout.

## Docker et OpenHands

Des images OpenHands et runtime ont été testées avec Docker. L'interface web a démarré. L'objectif était d'évaluer un environnement d'assistance au développement, avec un accès limité et contrôlé aux fichiers d'un projet.

## Automatisation

Des scripts PowerShell ont été utilisés ou préparés pour faciliter le lancement des composants. Le statut d'un installateur complet n'est pas confirmé ; le projet ne présente donc pas l'installation comme entièrement automatisée.

## Difficultés rencontrées

- Détection du microphone sans fil.
- Différence entre transcription réussie et réponse audio réellement audible.
- Compatibilité de certains composants audio avec CUDA et PyTorch.
- Coordination du démarrage de plusieurs services.
- Nécessité de tester chaque composant et le flux complet séparément.

## Prochaines étapes

1. Reproduire une conversation textuelle complète.
2. Vérifier séparément la capture microphone et la transcription.
3. Vérifier séparément la génération et la lecture audio.
4. Valider le flux vocal complet.
5. Tester le démarrage après redémarrage du système.
6. Définir les permissions avant tout accès aux fichiers ou exécution de commandes.
7. Ajouter des tests reproductibles et des journaux expurgés de toute information sensible.
