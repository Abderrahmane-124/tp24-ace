# 🏠 Smart Home - Application Conteneurisée

Application Smart Home composée d'un backend **Spring Boot**, d'un frontend **Angular**, d'une base de données **MySQL** et d'une interface **phpMyAdmin**, le tout orchestré avec **Docker Compose**.

## 📋 Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     Docker Compose                          │
├─────────────┬─────────────┬─────────────┬──────────────────┤
│   Frontend  │   Backend   │    MySQL    │    phpMyAdmin    │
│   (Angular) │ (Spring Boot)│  (Database) │    (Admin UI)    │
│   Port: 80  │  Port: 8085 │  Port: 3306 │    Port: 8081    │
└─────────────┴─────────────┴─────────────┴──────────────────┘
```

## 🚀 Démarrage Rapide

### Prérequis
- [Docker](https://www.docker.com/get-started) installé
- [Docker Compose](https://docs.docker.com/compose/install/) installé

### Lancer l'application

```bash
# Construire les images Docker
docker-compose build

# Démarrer tous les services en arrière-plan
docker-compose up -d

# Vérifier l'état des conteneurs
docker-compose ps
```

### Arrêter l'application

```bash
docker-compose down
```

## 🌐 Accès aux Services

| Service | URL | Description |
|---------|-----|-------------|
| **Frontend** | http://localhost | Interface utilisateur Angular |
| **Backend API** | http://localhost:8085 | API REST Spring Boot |
| **phpMyAdmin** | http://localhost:8081 | Administration MySQL |
| **MySQL** | localhost:3306 | Base de données |

### Credentials phpMyAdmin
- **Utilisateur**: `root`
- **Mot de passe**: `root`

## 📁 Structure du Projet

```
smarthouse/
├── Smart_Home_back/          # Backend Spring Boot
│   ├── src/
│   ├── pom.xml
│   └── Dockerfile
├── smartHome-front/          # Frontend Angular
│   ├── src/
│   ├── package.json
│   └── Dockerfile
└── docker-compose.yml        # Orchestration Docker
```

## 🐳 Services Docker

### MySQL
- Image: `mysql:latest`
- Base de données: `smart-house`
- Port exposé: `3306`

### Backend (Spring Boot)
- Build multi-stage avec Maven
- Image de base: `eclipse-temurin:17-jdk-alpine`
- Port exposé: `8085`

### Frontend (Angular)
- Build multi-stage avec Node.js
- Serveur: Nginx Alpine
- Port exposé: `80`

### phpMyAdmin
- Image: `phpmyadmin/phpmyadmin`
- Port exposé: `8081`

## 🔧 Commandes Utiles

```bash
# Voir les logs de tous les services
docker-compose logs

# Voir les logs d'un service spécifique
docker-compose logs backend
docker-compose logs frontend

# Reconstruire un service spécifique
docker-compose build backend

# Redémarrer un service
docker-compose restart backend
```

## 📝 Notes

- Le backend attend que MySQL soit démarré avant de se lancer (dependency)
- Le frontend attend que le backend soit démarré
- Les données MySQL sont persistées dans un volume Docker

## Captures
<img width="1654" height="1100" alt="image" src="https://github.com/user-attachments/assets/ea3ed19e-e36a-4a70-b8dd-d25249d12306" />
<img width="892" height="614" alt="image" src="https://github.com/user-attachments/assets/28e12702-05e5-46ac-953b-cb15fd436587" />
