# Feuille de route

Cette feuille de route décrit les étapes envisagées. Elle ne signifie pas que les fonctions listées sont déjà disponibles.

## 1. Stabilisation des services

- [ ] Définir les versions des dépendances.
- [ ] Vérifier le démarrage individuel de chaque service.
- [ ] Ajouter des contrôles de disponibilité.
- [ ] Définir une procédure propre d'arrêt et de redémarrage.
- [ ] Tester le démarrage après redémarrage de Windows.

## 2. Conversation textuelle

- [ ] Décrire précisément le contrat entre l'interface et le serveur.
- [ ] Tester les erreurs de connexion au modèle.
- [ ] Vérifier les réponses longues et les délais d'attente.
- [ ] Ajouter des journaux expurgés des données privées.

## 3. Chaîne vocale

- [ ] Stabiliser la détection du microphone.
- [ ] Tester la transcription sur des fichiers audio de référence.
- [ ] Tester la synthèse vocale indépendamment.
- [ ] Valider la lecture audio depuis l'interface.
- [ ] Tester le flux complet microphone → transcription → modèle → synthèse → lecture.

## 4. Mémoire et contexte

- [ ] Définir les données à conserver.
- [ ] Définir la durée de conservation et la suppression.
- [ ] Tester la continuité entre sessions.
- [ ] Éviter de stocker des informations sensibles sans nécessité.

## 5. Outils et permissions

- [ ] Définir les dossiers accessibles.
- [ ] Définir une liste de commandes autorisées.
- [ ] Demander confirmation avant une action destructive.
- [ ] Isoler les tâches dans un environnement dédié.
- [ ] Journaliser les actions et leurs résultats.

## 6. Documentation et qualité

- [ ] Enregistrer les versions exactes.
- [ ] Ajouter des tests reproductibles.
- [ ] Documenter les API et les formats de données.
- [ ] Publier une démonstration sans secrets ni données personnelles.

## Critères de maturité

Une fonctionnalité doit être considérée comme terminée seulement lorsqu'elle dispose d'un scénario de test reproductible, d'un résultat attendu, d'un résultat observé et d'une description de ses limites.
