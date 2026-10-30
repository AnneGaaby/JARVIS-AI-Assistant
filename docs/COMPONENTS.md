# Composants et responsabilités

Ce document explique le rôle des technologies étudiées dans le prototype. Les versions exactes ne sont pas indiquées lorsqu'elles ne sont pas confirmées.

## Serveur applicatif Python

**Rôle visé :** recevoir les demandes de l'interface, préparer le contexte, appeler le modèle local et coordonner les services.

**Éléments connus :** le projet comprend notamment les variantes de serveur `server.py` et `server_com_memoria.py`. Les fichiers ne sont pas inclus dans ce dépôt public.

**À documenter lors d'une future publication technique :** routes API, format des requêtes/réponses, gestion des erreurs, journalisation et authentification locale si nécessaire.

## LM Studio et modèles locaux

**Rôle :** charger un modèle de langage sur la machine et l'exposer au serveur applicatif.

**Expérimentations connues :** LM Studio et plusieurs modèles locaux, notamment de la famille Qwen, ont été utilisés. Gemma a également été envisagé.

**Validation connue :** chargement et utilisation de modèles pendant les essais. Le modèle exact peut varier d'une session à l'autre.

## Whisper large-v3

**Rôle :** reconnaissance vocale (speech-to-text), c'est-à-dire convertir la parole en texte.

**Validation connue :** serveur démarré, modèle large-v3 chargé, CUDA détecté et calcul float16 observé.

**À poursuivre :** fiabilité du microphone, format audio, latence, gestion des erreurs et transmission stable de la transcription au serveur applicatif.

## Kokoro

**Rôle :** synthèse vocale (text-to-speech), convertir du texte en parole.

**Validation connue :** service démarré avec CUDA et ressources vocales détectées.

**À poursuivre :** vérifier la génération audio, le format de sortie, la lecture depuis l'interface et le flux complet après la réponse du modèle.

## PowerShell

**Rôle :** automatiser certaines opérations de lancement sous Windows.

**Élément connu :** le script privé `Automacao_JARVIS.ps1` a été utilisé ou préparé pendant les expérimentations.

Les scripts ne sont pas publiés. Les futures versions devraient gérer les erreurs, vérifier la disponibilité des services et éviter d'inscrire des secrets dans les journaux.

## Docker et OpenHands

**Rôle étudié :** isoler des composants et explorer un environnement d'assistance au développement.

**Validation connue :** images Docker testées et interface OpenHands démarrée.

**À poursuivre :** documenter les limites du runtime, les volumes montés, les permissions, le réseau et les conditions d'exécution. Ne jamais monter un dossier personnel complet sans nécessité.

## CUDA et GPU NVIDIA

**Rôle :** accélérer les composants compatibles.

**Validation connue :** CUDA a été utilisé par les services Whisper et Kokoro pendant les essais.

La compatibilité dépend des versions des pilotes, de CUDA, de PyTorch et des dépendances propres à chaque projet. Toujours relever les versions exactes dans un environnement reproductible.
