# Time Clash

Jeu mobile PvP de stratégie en temps réel (iOS + Android, portrait). Des unités de 5 époques — Préhistoire, Médiéval, Far West, Ère industrielle, Futur — s'affrontent sur une arène en forme de cadran d'horloge. La carte signature **Paradoxe** rembobine les 5 dernières secondes de l'adversaire.

## Structure

| Dossier | Contenu |
|---|---|
| `src/` | Solution .NET : simulation partagée, serveur de match, API |
| `unity/` | Projet Unity (URP) |
| `art/raw`, `art/blender`, `art/export` | Modèles 3D bruts (Meshy), sources Blender, exports FBX |
| `tools/` | Scripts (génération Meshy, etc.) |
| `docs/` | GDD, journal de progression, captures de référence (`docs/ref`) |

## Démarrage

Voir [CLAUDE.md](CLAUDE.md) pour la stack, les conventions et les commandes, et [docs/PROGRESS.md](docs/PROGRESS.md) pour l'avancement.

Les binaires (modèles, textures, sons) sont suivis par **Git LFS** : lancez `git lfs install` avant de cloner.
