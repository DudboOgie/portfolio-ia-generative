# Module 2 : Connexion à la documentation de référence (Playbook SOC) via RAG

Ce fichier documente l'intégration d'une base de connaissances de remédiation (Playbook Incident) permettant à l'assistant SOC d'associer automatiquement des mesures défensives à un log suspect détecté.

## 📁 Playbook Interne Intégré (Base de Connaissances)
```text
[PLAYBOOK DE RÉPONSE AUX INCIDENTS - SOC]
- Cas A : Attaque Force Brute (Tentatives répétées échouées) -> Procédure : 1. Bloquer l'IP source sur le pare-feu. 2. Forcer la réinitialisation du mot de passe de l'utilisateur. 3. Alerter l'équipe de garde.
- Cas B : Connexion Conforme -> Procédure : Aucune action requise. Archiver le log.
- Cas C : Activité suspecte hors profil (ex: connexion à heure inhabituelle) -> Procédure : 1. Activer une surveillance accrue sur le compte. 2. Contacter l'utilisateur pour confirmation de l'activité.

Rôle : Tu es un expert analyste en cybersécurité au sein d'un SOC. Ton travail est d'analyser les lignes de logs et de fournir la procédure de réponse aux incidents.

CONSIGNE STRICTE : Analyse le log fourni par l'utilisateur. Tu dois obligatoirement déterminer le statut (CONFORME ou SUSPECT) et ajouter la "Procédure à appliquer" en te basant EXCLUSIVEMENT sur le Playbook ci-dessus.

Test de Validation
Log brut en entrée :
Plaintext

2026-05-29 21:55:01 UTC - Failed password for user j.dupont from IP 185.220.101.5 port 49152 ssh2 (Attempt 12 of 50)

Résultat de l'analyse et remédiation :
Plaintext

STATUT : SUSPECT
ANALYSE : Le journal indique une tentative de connexion échouée pour l'utilisateur j.dupont via SSH. Le message mentionne explicitement qu'il s'agit de la 12ème tentative sur 50 ("Attempt 12 of 50"), ce qui caractérise des scientifiques tentatives répétées échouées typiques d'une attaque par force brute (Cas A).
PROCÉDURE INTERNE : 
1. Bloquer l'IP source (185.220.101.5) sur le pare-feu.
2. Forcer la réinitialisation du mot de passe de l'utilisateur j.dupont.
3. Alerter l'équipe de garde.
