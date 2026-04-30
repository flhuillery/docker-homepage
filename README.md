# 🏠 Homepage — Tableau de Bord Serveur

Dashboard centralisé pour tous les services du serveur home (192.168.1.31), basé sur [gethomepage.dev](https://gethomepage.dev).

## Services intégrés

| Catégorie | Service | Port |
|-----------|---------|------|
| **Automatisation** | Home Assistant | 8023 |
| | Zigbee2MQTT | 7070 |
| | Frigate (NVR) | 5000 |
| | Matterbridge | — |
| **Médias** | Jellyfin | 8096 |
| | Sonarr | 8989 |
| | Radarr | 7880 |
| | Lidarr | 8686 |
| | Jackett | 9117 |
| | Transmission (VPN) | 9095 |
| **Cloud & Partage** | Nextcloud | (proxy) |
| | Immich | 2283 |
| | Pingvin Share | 3010 |
| **Monitoring** | Grafana | 3000 |
| | Prometheus | 9090 |
| | Portainer | 9000 |
| | Dockhand | 3009 |
| | cAdvisor | 8080 |
| **Sécurité & Réseau** | Vaultwarden | (proxy) |
| | Nginx Proxy Manager | 82 |
| | Fail2ban | — |
| **Outils** | IT Tools | 7474 |
| | phpMyAdmin | 8082 |
| | KMS Server | 1688 |
| | MQTT Mosquitto | 1883 |
| **Mes Apps** | MuscuApp | 3080 |
| | WordPress | 3001 |

## Démarrage rapide

```bash
# 1. Copier et remplir les variables d'environnement
cp .env.example .env
nano .env

# 2. Lancer le conteneur
docker compose up -d

# 3. Accéder au dashboard
open http://192.168.1.31:3003
```

## Configuration des clés API

Remplir le fichier `.env` avec les clés API de chaque service.  
Voir [.env.example](.env.example) pour la liste complète avec les instructions d'obtention.

| Service | Où trouver la clé |
|---------|-------------------|
| Home Assistant | Profil → Sécurité → Jeton d'accès longue durée |
| Sonarr / Radarr / Lidarr | Paramètres → Général → Clé API |
| Jackett | Tableau de bord → Clé API (en haut) |
| Jellyfin | Administration → Clés API |
| Portainer | Mon compte → Clés d'accès |
| Immich | Compte → Clés API |

## Structure des fichiers

```
homepage/
├── docker-compose.yml      # Définition du conteneur
├── .env                    # Variables secrètes (non versionné)
├── .env.example            # Modèle de variables
├── README.md               # Ce fichier
├── .gitignore
├── .github/
│   └── copilot-instructions.md  # Instructions Copilot
└── config/
    ├── settings.yaml       # Thème, layout
    ├── services.yaml       # Liste des services
    ├── widgets.yaml        # Widgets barre supérieure
    ├── bookmarks.yaml      # Marque-pages rapides
    ├── docker.yaml         # Connexion socket Docker
    └── custom.css          # CSS personnalisé
```

## Mise à jour

```bash
docker compose pull
docker compose up -d
```

## Convention Git

> **Toujours committer après chaque modification** (voir `.github/copilot-instructions.md`).

```bash
git add -A
git commit -m "feat: description de la modification"
git push
```
