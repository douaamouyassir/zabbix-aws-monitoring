# Déploiement Zabbix conteneurisé sur AWS - Monitoring hybride Linux & Windows

Projet réalisé par **Douaa Mouyassir**  
Encadrant : Prof. Azeddine KHIAT  
Année universitaire : 2025/2026

## Objectif
Déployer une infrastructure de supervision centralisée sur AWS avec Zabbix en conteneurs Docker, pour monitorer un parc hybride (1 serveur Ubuntu + 1 client Linux + 1 client Windows).

## Architecture
- 1 VPC avec subnet public
- 3 instances EC2 :
  - t3.large Ubuntu : Serveur Zabbix (Docker)
  - t3.medium Ubuntu : Client Linux
  - t3.large Windows Server 2022 : Client Windows
- Security Group autorisant ports 80/443, 10050/10051, 22, 3389

## Déploiement Zabbix
Fichier principal : `docker-compose.yml` (contenu ci-joint)

Résultat : Interface accessible sur http://IP-publique, monitoring actif des deux clients.

## Captures d'écran
- VPC et Security Group
- Instances EC2
- Dashboard Zabbix avec clients Linux et Windows monitorés
- Statut ZBX vert et métriques CPU/RAM

## Conclusion
Projet fonctionnel avec monitoring en temps réel du parc hybride. Difficultés principales : initialisation MySQL (résolue avec `--log-bin-trust-function-creators=1`) et configuration agents avec IP privée.
