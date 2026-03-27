# 🚀 CI/CD Pipeline with GitLab - Java App

## Description

Ce projet met en place un pipeline CI/CD complet pour une application Java basée sur Maven.

Le pipeline automatise les étapes suivantes :

- Installation des outils nécessaires
- Tests unitaires
- Analyse de sécurité
- Analyse de qualité du code (SonarQube)
- Build de l'application
- Création et push d'une image Docker
- Déploiement sur Kubernetes

## Technologies

☕ Java 17
📦 Maven
🔍 Trivy (scan de vulnérabilités)
📊 SonarQube (analyse qualité)
🐳 Docker
☸️ Kubernetes
🔁 GitLab CI/CD

## etapes du pipeline

Le pipeline est structuré en plusieurs stages :
stages:
  - install_tools
  - test
  - security
  - build
  - docker
  - deploy

## Détails des Jobs

## 1. 🛠️ Installation des outils

Installe toutes les dépendances nécessaires :
Java
Maven
Trivy
Docker
Kubectl

## 2. ✅ Tests unitaires

Exécute les tests avec Maven :
mvn test

## 3. 🔐 Analyse de sécurité

🔍 Scan filesystem avec Trivy
trivy fs --format table -o fs.html .

📊 Analyse SonarQube

Analyse du code
Détection des bugs et vulnérabilités

## 4. 🏗️ Build de l'application

mvn package

## 5. 🐳 Docker

Build de l'image :

docker build -t adildal/boardgitlab:latest .

Push vers Docker Hub :

docker push adildal/boardgitlab:latest

## 6. ☸️ Déploiement Kubernetes

Déploiement avec :
kubectl apply -f deployment-service.yaml

🔐 Variables d'environnement requises

Dans GitLab CI/CD, configure les variables suivantes :
DOCKER_USERNAME
DOCKER_PASSWORD
KUBECONFIG_CONTENT (base64 du fichier kubeconfig)

📁 Structure du projet
.
├── .gitlab-ci.yml
├── Dockerfile
├── deployment-service.yaml
├── src/
└── pom.xml

🚀 Déploiement
Le déploiement est automatiquement déclenché sur la branche :
master

📈 Améliorations possibles
- Ajouter des tests d'intégration
- Mettre en place Helm pour Kubernetes
- Ajouter monitoring (Prometheus / Grafana)
- Sécuriser les secrets avec Vault


