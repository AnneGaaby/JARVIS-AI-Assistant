# Configuration et paramètres

Le code et les fichiers de configuration internes ne sont pas publiés. Cette page donne une structure de référence pour documenter un environnement local similaire, sans divulguer les valeurs privées du prototype.

## Paramètres à documenter

| Catégorie | Exemples de paramètres | Bonne pratique |
|---|---|---|
| Application | Mode de lancement, adresse d'écoute | Écouter en local par défaut |
| Modèle local | Adresse API, identifiant du modèle | Vérifier que le modèle est chargé avant l'appel |
| Audio entrant | Modèle STT, format audio, langue | Tester avec un fichier audio connu |
| Audio sortant | Modèle TTS, voix, format de sortie | Tester génération et lecture séparément |
| Services | Adresse locale, port, délai d'attente | Éviter les ports exposés publiquement sans raison |
| Mémoire | Emplacement et politique de conservation | Définir durée, suppression et confidentialité |
| Outils | Dossiers autorisés et commandes permises | Appliquer le moindre privilège |
| Journaux | Niveau de détail et destination | Ne jamais journaliser de secrets |

## Fichier d'environnement

Pour un projet public, utiliser un fichier d'exemple tel que `.env.example` avec des valeurs fictives ou vides. Le vrai fichier `.env` doit rester ignoré par Git.

Exemple de structure uniquement — ces noms ne sont pas les variables réelles de J.A.R.V.I.S. :

```dotenv
APP_ENV=development
APP_HOST=127.0.0.1
APP_PORT=
LLM_API_BASE=
LLM_MODEL=
STT_SERVICE_URL=
TTS_SERVICE_URL=
LOG_LEVEL=INFO
```

Ne jamais ajouter de mot de passe, clé API, jeton, adresse privée sensible ou donnée personnelle dans un dépôt public.

## Versions et reproductibilité

Pour chaque environnement, enregistrer :
- version de Python ;
- version de LM Studio et identifiant exact du modèle ;
- versions de Whisper, Kokoro et dépendances audio ;
- versions du pilote NVIDIA, CUDA et PyTorch ;
- version de Docker et image OpenHands utilisée ;
- système d'exploitation et date du test.

Une configuration ne doit être qualifiée de reproductible qu'après avoir été testée depuis un environnement propre.
