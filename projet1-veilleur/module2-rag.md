# Module 2 : Enrichissement du contexte (RAG basique sur criticité CVE)

Ce fichier documente la configuration RAG appliquée au Veilleur Cyber pour automatiser le calcul de criticité des alertes en fonction du référentiel officiel des scores CVSS (v3).

## 📁 Référentiel Technique Intégré (Base de Connaissances)
```text
[RÉFÉRENTIEL CRITICITÉ CVE / CVSS v3]
- CRITIQUE (Score 9.0 à 10.0) : Permet une exécution de code à distance (RCE) sans authentification, ou un Ransomware automatisé sur un système d'exploitation majeur.
- ÉLEVÉ (Score 7.0 à 8.9) : Permet une élévation de privilèges (devenir admin) mais nécessite d'être déjà connecté sur le réseau.
- MOYEN (Score 4.0 à 6.9) : Faille d'affichage, déni de service local (faire planter un logiciel) ou fuite d'informations mineure.

Rôle : Tu es un analyste Threat Intelligence senior. Ton travail est de filtrer un flux d'actualités pour en extraire la criticité technique.

CONSIGNE STRICTE : Analyse l'alerte fournie. Tu dois utiliser UNIQUEMENT les critères du référentiel ci-dessus pour attribuer le statut. Réponds EXCLUSIVEMENT au format JSON.

est de Validation
Alerte brute en entrée :

    Alerte : Une vulnérabilité a été découverte dans le système de gestion des routeurs Cisco. Un attaquant qui possède déjà un compte invité sur le réseau peut exploiter cette faille pour devenir administrateur total de la machine.

Résultat JSON calculé par l'IA :
JSON

[
  {
    "logiciel": "Cisco",
    "cve_score": "8.0",
    "statut": "ÉLEVÉ",
    "raison": "La vulnérabilité permet une élévation de privilèges pour devenir administrateur mais nécessite d'être déjà connecté sur le réseau avec un compte invité."
  }
]
