- Identifier assets techniques (T0, ...)
- Adopter la vision groupe mssp
- Revoir les tags
- Documenter en mode groupe
- Intégrer les alertes dans IRIS
- info vs alertes vs conformity

---

# Tasks
- [ ] Establish a communication plan with the other countries
- [ ] Establish a clear process for asset management in our technologies (Tags, alerts, ...) 
- [ ] Establish a RACI with the countries
- [ ] Establish a clear operational documentation for the group 
- [ ] Establish COMOP between countries and the group
- [ ] Separate the alerts between : 
	- [ ] Low signal rules
	- [ ] Malicious
	- [ ] Conformity
- [ ] Review the tags in SentinelOne/Varonis/O365 (identify assets)
- [ ] Import knowledge from my MSSP background
- [ ] Upgrade the IRIS configuration
- [ ] Create a Git repo for the security team
- [ ] Make the script/image for the audit workstation
- [ ] Integrate the tools in WSL on our workstations ? 

---
# Tags
## SentinelOne
- VIP-Workstation
- Server
- Workstation

## MSSP
Creating a new team with a planner for each country
vs
using excels sheets

---
Purple AI use case
Traduction de log windows en SentinelOne (typiquement 4624)
# SentinelOne Point sur la conf
Mettre des ACLs : demander pour qu'ils ouvrent un ticket et mettre des ACLs (IP filtering pour la console)
Mettre des tags mais sans valeur pour les cessions d'étabs, ... (dynamiques)
Status non vérifier sur la console user management
Rôle C-level : dashboarding, ...
Role SOC : action de remédiation, search, ...
Reco de mettre en place le SSO, si on a une techno pour, mais c'est intéressant.
Activation de notifs mails
- rule has expired
- Rule status has changed

Device control
1ere étape : visibilité de l'environnement
Pareil pour le firewall control

Cocher le quarantine
``Reco comme Onebox de cocher les accounts ???``
token généré + token révoqué
Service user created, deleted, api regenerated, ...
site expiré
because expired account
site réactivé
api permission token change

DSI qui gère les rôles = bonne pratique
Si autonomie des entités, envisageable
Deleted exclusions

Marketplace -> Azure
10go par jour en ingestion dans le marketplace
On peux prendre de l'ingestion, mais moins de 10 go obligatoire
Policies and settings
ai siem
data ingestion
``moyenne`` sur 30j

# Policy
process en mémoire :
injection de dll par l'agent, créer une storyline
kill la menace : kill le process tree malicieux (storyline)
agent a en visibilité toutes les modifs système faite par une storyline (registre, tâche planifiée, ...) et va réparer via le remediate
Rollback : restaurer les fichiers altérer pendant l'attaque (ransomware).
Automatiquement, l'agent kill et met en quarantaine.
Si des choses en plus, on le fait automatiquement.

Remediate prends du temps
Peut restaurer des fichiers légitimes et supprimer le taff d'un collab par exemple.

Remediate : modification du système, tâches planifiées, registre, ...
Rollback : restaurer des fichiers chiffrer.

Le rollback se base sur les VSS (par défaut, l'agent fait un snapshot VSS toutes les 4h pour 10% du volume)
Si atteint les 10%, rotation.
Capable de l'ajuster.
mécanisme d'anti-tamper pour protéger les VSS de l'agent.
Toujours en mesure de faire un rollback.
detect interactive threats : génère des FP.
Nécessite un gros travail de config, sur des scopes, etc.
il faudrait éviter les admins, devs, ... car détecte les déplacement latéraux.

application control container only
Application control peut gêner pendant le déploiement de kube car conçu pour les images immuables.
Si pas d'image immuable, ne pas activer

Ne surtout pas activer le network quarantine
Isole instant dès qu'une menace est détecté
Malicious macro : supprime les macros dans les fichiers.

Wayfinder threat hunting / vigilance
Offre modifiée
En fonction de la licence vigilance, une équipe de threat hunting

Pas de scans régulier car pas besoin.
Dès qu'une opération sur un fichier arrive, il y a un scan de l'agent plus le scan d'origine, pas besoin de plus.

Custom la support page - contact info

Limite de temps, il va regarder.
Si mis en quarantaine, peut récupérer le fichier malicieux

Ingestion de certains events logs
La quantité est négligeable
Collecter un certain nombre de windows event logs
Collecter tout les chanels
Tout les ID
mais seulement le critical et error + provider Microsoft
Activer par groupe, granulaire
Si trop vaste, on peut l'affiner avec des policies override

Devrais collecter a partir du moment ou une machine est déplacé dans un groupe
Utile pour des règles de détections.
Dans détection, chercher la data source windows event log
