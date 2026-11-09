# Journal de progression — Time Clash

## 2026-11-09 — Étape 0 : dépôt, mémoire et structure ✅
**Fait**
- git 2.47.1 et Git LFS 3.6.1 présents ; gh absent (optionnel). Accès au dépôt vérifié par `git ls-remote` (exit 0, dépôt vide).
- Clone dans `...\Documents\CODE\TimeClash`, branche `main` initialisée localement.
- `git lfs install` + suivi de *.fbx, *.glb, *.blend, *.png, *.psd, *.wav, *.ogg, *.mp3.
- `.gitignore` (Unity, .NET, .env, temporaires Blender), README.md, CLAUDE.md, ce journal.
- Arborescence : src/, unity/, art/{raw,blender,export}/, tools/, docs/ref/.
- docs/GDD.md ajouté (V2 déjà conforme à la Direction du jeu et à la DA ; note de priorité ajoutée).

**Testé**
- `git remote -v`, `git status`, `git log -1`, `git lfs track`, arborescence → OK (voir rapport d'étape).
- Vérification des secrets : aucun fichier `.env`/secret suivi.

**Reste à faire**
- Étape 1 : vérification de l'environnement (.NET SDK, Python, uv, Blender, Unity).
