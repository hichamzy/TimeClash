# CLAUDE.md — Time Clash

Mémoire du projet pour Claude Code. À lire en début de session, avec `docs/PROGRESS.md` (journal) et `docs/GDD.md` (design de base).

## Projet
- **Time Clash** : jeu mobile PvP de stratégie en temps réel (iOS + Android, portrait). Unités de 5 époques (Préhistoire, Médiéval, Far West, Ère industrielle, Futur) sur une arène en cadran d'horloge. Carte signature **Paradoxe** : rembobine les 5 dernières secondes de l'adversaire.
- Chemin local : `C:\Users\HICHAMZYADNI\OneDrive - ALEXSYS SOLUTIONS\Documents\CODE\TimeClash` (contient des espaces → toujours entre guillemets).
- Dépôt : https://github.com/hichamzy/TimeClash (branche `main`).
- Priorité : la section **Direction du jeu (V2)** ci-dessous l'emporte sur le GDD en cas de conflit.

## Direction du jeu (V2 — Arène Horloge)
- Arène circulaire = cadran d'horloge, vue de dessus, portrait.
- Tours : adversaire à 10 h, 12 h (Horloge Maîtresse), 2 h ; joueur à 8 h, 6 h (Horloge Maîtresse), 4 h.
- Ligne de **Minuit** (horizontale, au centre) : on ne pose ses unités que dans sa moitié.
- 3 voies : arc gauche (10 h → 8 h), arc droit (2 h → 4 h), voie centrale (12 h → 6 h) traversant le Noyau.
- **Noyau temporel** (centre) : capture en y restant (barre 0–100 % par camp). Contrôle = +20 % de régénération Chronos.
- **L'Aiguille** : 1 tour/min, sens horaire. Unité touchée = ralentie de 40 % pendant 2 s. Le Paradoxe la fait reculer de 30°.
- **Énergie Chronos** : max 10, +1 toutes les 2,8 s (×2 dans la dernière minute).
- Cartes, progression, monétisation : selon le GDD.
- Repères clés du GDD : match 3 min + 1 min de prolongation ; énergie de départ 5 ; régén 2,8 s → 1,4 s (Heure de pointe) → 0,9 s (prolongation) ; deck 8 cartes, main 4 + aperçu ; 1 carte Temporelle max par deck ; Tour d'époque = 1 couronne, Horloge Maîtresse = 3 + fin du match.
- Paradoxe (6 énergie) : restaure l'état d'il y a 100 ticks pour les entités adverses + PV des tours du lanceur ; unités adverses posées entre-temps → retour en main (énergie perdue) ; Aiguille -30° ; préavis sépia 1 s ; cooldown global 20 s ; ne rembobine pas les couronnes ni un autre Rembobinage ; l'Ancre temporelle protège de l'effet.
- Simulation : viser le déterminisme (virgule fixe) — à trancher à l'étape 2.

## Direction artistique
- Style : Art déco + jouets mécaniques. Figurines low-poly stylisées, pièces d'horlogerie peintes (rouages, rivets, laiton), proportions légèrement chibi.
- Palette :
  - Fond bleu nuit `#0F1A2B`, cadran `#13223A`
  - Laiton `#D4A24C` / `#E9C77B` (cadres, aiguille, pastilles d'énergie)
  - Crème `#F2E6CC` (cartes)
  - Camp joueur turquoise `#3FB8AF`, camp adverse corail `#E86A58`
- Époques : Médiéval `#2F5FC4`, Far West `#A8662A`, Préhistoire `#3F7F2F`, Ère industrielle `#B5652B`, Futur `#2BA6C9`, Temporel `#7046D9`.
- Typo : **Bungee** (titres, chiffres), **Inter** (texte).
- UI : cartes crème à cadre laiton, pastille de coût en engrenage, liseré couleur d'époque en bas de carte, énergie en 10 pastilles dorées.
- Rembobinage : filtre sépia, Aiguille qui recule, son de mécanisme qu'on remonte.
- Maquettes de référence : `docs/ref/`.
- **Prompt de style 3D commun (Meshy)** :
  > stylized low-poly mechanical toy figurine, art deco clockwork details, brass rivets and gears, painted enamel colors, slightly chibi proportions, clean readable silhouette from top-down view, mobile game asset

## Stack
- Jeu : Unity (C#, URP), iOS + Android, portrait.
- Simulation partagée : `TimeClash.Simulation` (.NET Standard 2.1), utilisée par Unity et le serveur.
- Serveur de match : console .NET, 20 ticks/s, autoritaire, buffer circulaire de 100 états (Rembobinage).
- API : ASP.NET Core, Clean Architecture + CQRS/MediatR, PostgreSQL, Redis.
- 3D : Meshy (API) → Blender (Blender MCP) → Unity (Unity MCP).

## Architecture (cible)
```
src/      TimeClash.sln : Simulation, Contracts, MatchServer, Api, Simulation.Tests   (étape 2)
unity/    Projet Unity URP                                                          (étape 4)
art/      raw (Meshy) / blender (sources .blend) / export (FBX pour Unity)
tools/    Scripts (meshy_generate.py, ...)
docs/     GDD.md, PROGRESS.md, ref/ (captures)
```

## Conventions
- Commits en anglais, style Conventional Commits (`feat:`, `fix:`, `chore:`, `docs:`, `test:`).
- Commit + push sur `origin/main` à la fin de chaque étape validée par l'utilisateur.
- Secrets uniquement dans `.env` (ignoré par git). Jamais dans le code, ce fichier ou GitHub. Vérifier `git ls-files` avant chaque push.
- Binaires (fbx, glb, blend, png, psd, wav, ogg, mp3) via Git LFS (`.gitattributes`).
- Dossier synchronisé OneDrive : en cas de fichier verrouillé/conflit, s'arrêter et demander de mettre OneDrive en pause.
- Travail étape par étape avec rapport (✅ 🧪 📁 ⚠️ ➡️) et attente du "OK" utilisateur.
- N'installer que les outils listés ; demander avant tout autre.

## Commandes utiles
```bash
cd "C:\Users\HICHAMZYADNI\OneDrive - ALEXSYS SOLUTIONS\Documents\CODE\TimeClash"
git status ; git lfs track ; git lfs ls-files
git ls-files | grep -i -E "\.env$|secret"   # vérif secrets avant push
# (à venir) dotnet build src/TimeClash.sln ; dotnet test src/TimeClash.sln
```

## Outils connectés
| Outil | État |
|---|---|
| git 2.47.1 | ✅ installé |
| Git LFS 3.6.1 | ✅ installé et configuré |
| gh (GitHub CLI) | ❌ non installé (optionnel ; accès vérifié via `git ls-remote`) |
| Blender MCP | ⏳ étape 3 |
| Unity MCP | ⏳ étape 4 |
| Meshy API | ⏳ étape 5 |

## Décisions prises
- 2026-11-09 : dépôt GitHub vide au départ → branche `main` initialisée localement.
- 2026-11-09 : `.gitkeep` dans chaque dossier vide pour conserver l'arborescence.
- 2026-11-09 : `.gitignore` racine avec règles Unity préfixées `unity/` (projet Unity dans un sous-dossier).
- 2026-11-09 : GDD fourni déjà en V2 (arène §2 et DA §8 conformes) → copié tel quel dans `docs/GDD.md`, avec une note de priorité vers CLAUDE.md.

## État actuel
- Étape 0 terminée (commit initial poussé). Prochaine : **étape 1 — vérification de l'environnement**.
