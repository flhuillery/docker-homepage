# Instructions GitHub Copilot — docker-homepage

## Règle absolue : Toujours committer après chaque modification

Après **chaque modification** apportée à ce dépôt, tu dois systématiquement :

```bash
git add -A
git commit -m "<type>: <description courte>"
git push
```

### Convention de commit (Conventional Commits)

| Préfixe | Usage |
|---------|-------|
| `feat:` | Nouvelle fonctionnalité ou nouveau service |
| `fix:` | Correction d'un bug ou d'une mauvaise configuration |
| `config:` | Modification de fichiers de configuration |
| `docs:` | Mise à jour de la documentation |
| `chore:` | Maintenance (mise à jour d'image, nettoyage) |

**Exemples :**
```
feat: ajout du service Nextcloud avec widget
fix: correction URL Radarr (port 7880)
config: mise à jour du thème en dark mode
docs: mise à jour README avec nouvelle clé API
```

## Contexte du projet

Dashboard Homepage (gethomepage.dev) centralisé pour le serveur home `192.168.1.31`.

### Services configurés

- **Automatisation** : Home Assistant (8023), Zigbee2MQTT (7070), Frigate (5000), Matterbridge
- **Médias** : Jellyfin (8096), Sonarr (8989), Radarr (7880), Lidarr (8686), Jackett (9117), Transmission (9095)
- **Cloud** : Nextcloud, Immich (2283), Pingvin Share (3010)
- **Monitoring** : Grafana (3000), Prometheus (9090), Portainer (9000), Dockhand (3009), cAdvisor (8080)
- **Sécurité** : Vaultwarden, Nginx Proxy Manager (82), Fail2ban
- **Outils** : IT Tools (7474), phpMyAdmin (8082), KMS (1688), MQTT (1883)
- **Apps** : MuscuApp (3080), WordPress (3001)

### Fichiers clés

- `config/services.yaml` — Définition de tous les services et widgets
- `config/settings.yaml` — Thème et layout
- `.env` — Variables secrètes (ne JAMAIS commit ce fichier)
- `.env.example` — Modèle de variables (toujours à jour)

### Règles de sécurité

- Ne **jamais** committer le fichier `.env`
- Toujours utiliser `{{HOMEPAGE_VAR_XXX}}` pour les secrets dans les configs YAML
- Le fichier `.env.example` doit toujours refléter toutes les variables nécessaires

## Workflow standard

1. Modifier le(s) fichier(s) nécessaire(s)
2. Tester localement : `docker compose up -d && open http://192.168.1.31:3003`
3. **Committer immédiatement** avec un message conventionnel
4. Pousser sur GitHub : `git push`
