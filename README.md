# Paperless-NGX

Système de gestion de documents avec OCR, reconnaissance automatique et indexation.

## 📁 Fichiers de configuration

- **papreless-ngx.yml** : Configuration Docker Compose
- **paperless_metadata_backup_20260207_180257.json** : Sauvegarde des métadonnées
- **.volumes/paperless-ngx/** : Données de l'application
  - `data/` : Base de données et index
  - `media/` : Documents traités
  - `consume/` : Dossier d'import automatique
  - `export/` : Dossier d'export
- `data/pgdata/` : Base de données PostgreSQL

## 🚀 Démarrage

```bash
docker-compose -f papreless-ngx.yml up -d
```

## 🌐 Accès

- **Interface web** : http://localhost:8000
- **URL publique** : https://paperless.sparta.diskstation.me

## 📦 Services inclus

- **webserver** : Application Paperless-NGX
- **db** (PostgreSQL) : Base de données
- **broker** (Redis) : File d'attente pour le traitement

## 🔐 Configuration

```yaml
Base de données:
  - Nom: paperless
  - Utilisateur: paperless
  - Mot de passe: (voir compose file)

OCR:
  - Langues: français + anglais
  - Timezone: Europe/Paris
```

## 📄 Utilisation

1. Déposez des documents dans le dossier `consume/`
2. Paperless les traite automatiquement avec OCR
3. Les documents sont indexés et recherchables
4. Consultez-les via l'interface web

## 💾 Sauvegarde

Le fichier JSON contient une sauvegarde des métadonnées (tags, correspondants, types de documents, etc.). 

Pour restaurer :
```bash
docker exec -it <container_name> document_exporter ../export/
```

## ⚙️ Ports utilisés

| Port | Description |
|------|-------------|
| 8000 | Interface web Paperless-NGX |
