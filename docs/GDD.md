# Time Clash — Game Design Document

Version V2 « Arène Horloge » · 9 novembre 2026 · Hicham

> En cas de conflit, la section « Direction du jeu (V2 — Arène Horloge) » de [CLAUDE.md](../CLAUDE.md) est prioritaire sur ce document.

## 1. Vision et pitch

Time Clash est un jeu de stratégie PvP en temps réel de 3 minutes, où des unités de cinq époques s'affrontent sur une arène en forme de cadran d'horloge, et où le joueur peut manipuler le temps lui-même.

**Pitch en une phrase :** « Un chevalier, un cowboy et un T-Rex entrent dans une horloge géante — et ton adversaire vient de rembobiner tes 5 dernières secondes. »

**Ce qui le différencie (USP) :**

- **Le temps est une ressource tactique** : rembobiner, accélérer ou geler une zone. Aucun jeu du genre ne joue sur cet axe.
- **Une arène unique en cadran d'horloge** : une Aiguille géante qui balaie le terrain et un Noyau temporel à capturer au centre.
- **Synergies entre époques** : mélanger les époques dans un deck crée des combos (« Paradoxes ») inédits.
- **Lisibilité immédiate** : tout le monde comprend un chevalier contre un robot, sans tutoriel long.

**Public cible :** joueurs mid-core de 14 à 35 ans, sur mobile, qui aiment les sessions courtes et compétitives.

**Plateformes :** iOS (App Store) et Android (Play Store), portrait, une main.

**Références de genre :** jeux de cartes/stratégie en temps réel en arène. Time Clash garde ce format connu, mais remplace l'arène classique à deux voies par un cadran d'horloge à trois voies, et ajoute la couche « temps » comme signature.

## 2. Core gameplay

Un match dure 3 minutes, plus 1 minute de prolongation : chaque joueur détruit les tours adverses en posant des cartes qui coûtent de l'énergie Chronos.

**L'arène : le cadran d'horloge**

- Une arène circulaire, vue de dessus, en mode portrait.
- La ligne de **Minuit** (horizontale, au centre) sépare les deux camps : chaque joueur ne pose ses unités que dans sa moitié.
- **Tours adverses** : 10 h et 2 h (Tours d'époque), 12 h (Horloge Maîtresse).
- **Tours du joueur** : 8 h et 4 h (Tours d'époque), 6 h (Horloge Maîtresse).
- **3 voies** : un arc à gauche (de 10 h à 8 h), un arc à droite (de 2 h à 4 h), et une voie centrale (de 12 h à 6 h) qui traverse le Noyau.
- Une Tour d'époque détruite donne 1 couronne, l'Horloge Maîtresse en donne 3 et termine le match.

**Le Noyau temporel**

- Il se trouve au centre du cadran, sur la voie centrale.
- Il se capture en y gardant des unités : une barre de contrôle va de 0 à 100 % pour chaque camp.
- Le camp qui le contrôle gagne **+20 % de régénération d'énergie Chronos**.

**L'Aiguille**

- Une aiguille géante qui fait **1 tour par minute** dans le sens horaire.
- Toute unité touchée est **ralentie de 40 % pendant 2 s**.
- Le chrono en haut de l'écran annonce son prochain passage : poser ses cartes au bon moment fait partie de la stratégie.

**L'énergie Chronos**

| Paramètre | Valeur |
| --- | --- |
| Énergie max | 10 |
| Énergie de départ | 5 |
| Régénération normale | 1 point / 2,8 s |
| Dernière minute (« Heure de pointe ») | 1 point / 1,4 s |
| Prolongation | 1 point / 0,9 s |
| Bonus du Noyau temporel | +20 % sur la régénération |

**Le deck et la main**

- Un deck de **8 cartes**, une main visible de **4 cartes**, plus l'aperçu de la suivante.
- Une carte jouée repart à la fin du cycle : le joueur peut prévoir ses combos.
- Règle spéciale : **1 seule carte Temporelle** (rare) autorisée par deck, pour garder le Rembobinage exceptionnel.

**Conditions de victoire**

1. Destruction de l'Horloge Maîtresse : victoire immédiate.
2. Fin du temps : le joueur avec le plus de couronnes gagne.
3. Égalité après 1 minute de prolongation : la tour la plus abîmée perd (« Mort subite par l'horloge »).

**Les rôles d'unités**

- **Tank** : beaucoup de PV, lent, attire les tirs.
- **DPS mêlée** et **DPS distance** : les dégâts.
- **Essaim** : plusieurs petites unités pas chères.
- **Bâtiment** : défense fixe ou générateur.
- **Sort** : effet instantané sur une zone.
- **Temporel** : manipule le temps (section 3).

## 3. Mécanique signature : le Rembobinage

La carte **Paradoxe** (6 énergie) annule les 5 dernières secondes de l'adversaire : c'est le moment « wow » qui fera parler du jeu.

**Ce que le Rembobinage annule chez l'adversaire**

- Les unités posées dans les 5 dernières secondes disparaissent et retournent dans sa main. L'énergie dépensée est **perdue**.
- Les unités ennemies déjà en jeu reculent à leur position d'il y a 5 secondes, avec leurs PV de l'époque.
- Les dégâts faits à **tes** tours pendant ces 5 secondes sont restaurés.
- **L'Aiguille recule de 30°**.

**Ce qu'il n'annule pas**

- Tes propres actions : seul l'adversaire est rembobiné.
- Les couronnes déjà gagnées (une tour détruite reste détruite).
- Un autre Rembobinage : pas de boucle infinie.

**Contre-jeu et équilibrage**

- **Effet visuel d'1 seconde avant l'effet** (l'arène se teinte en sépia) : l'adversaire peut réagir en posant une carte, qui ne sera pas rembobinée.
- **Cooldown global de 20 secondes** après usage, même si la carte revient en main.
- **L'Ancre temporelle** (bâtiment, 3 énergie) protège les unités dans sa zone contre le Rembobinage.

**Les autres cartes Temporelles (1 par deck)**

| Carte | Coût | Effet |
| --- | --- | --- |
| Paradoxe | 6 | Rembobine les 5 dernières secondes de l'adversaire |
| Sablier figé | 4 | Gèle le temps dans une zone pendant 3 s (unités et tirs) |
| Accélération | 3 | Tes unités dans la zone vont 2× plus vite pendant 4 s |
| Écho | 5 | Rejoue gratuitement ta dernière carte, en version fantôme (50 % PV) |
| Saut quantique | 2 | Téléporte une de tes unités à sa position d'il y a 5 s |

**Pourquoi c'est techniquement faisable :** le serveur garde un historique de l'état du match, une « photo » par tick (20 ticks par seconde, donc 100 photos pour 5 s). Rembobiner, c'est recharger la photo d'il y a 100 ticks pour les entités de l'adversaire (détails en section 7).

## 4. Époques et cartes

Le jeu sort avec 5 époques et 25 cartes. Chaque époque a une identité de jeu claire, et le mélange d'époques débloque des bonus.

**Les 5 époques**

| Époque | Identité de jeu | Bonus d'époque (3 cartes ou plus dans le deck) |
| --- | --- | --- |
| Préhistoire | Force brute, gros PV, lent | +10 % PV pour les unités préhistoriques |
| Médiéval | Formations, défense, boucliers | Tours d'époque +8 % PV |
| Far West | Distance, rapidité, critiques | 15 % de chance de tir critique (×2) |
| Ère industrielle | Machines, bâtiments, zone | Bâtiments construits 30 % plus vite |
| Futur | Technologie, boucliers d'énergie, téléportation | -1 énergie sur la première carte Futur de chaque cycle |

**Les cartes de lancement (valeurs de départ, à équilibrer en test)**

| Carte | Époque | Coût | Rôle | PV | Dégâts | Rareté |
| --- | --- | --- | --- | --- | --- | --- |
| T-Rex | Préhistoire | 7 | Tank | 4 200 | 320 | Épique |
| Chasseurs de mammouth (×3) | Préhistoire | 3 | Essaim | 300 | 90 | Commune |
| Ptérodactyle | Préhistoire | 4 | DPS aérien | 800 | 140 | Rare |
| Pluie de météores | Préhistoire | 5 | Sort | — | 600 | Épique |
| Chevalier | Médiéval | 3 | Tank léger | 1 500 | 170 | Commune |
| Archers (×2) | Médiéval | 3 | DPS distance | 280 | 100 | Commune |
| Catapulte | Médiéval | 5 | Bâtiment / siège | 1 100 | 380 | Rare |
| Dragon de légende | Médiéval | 6 | DPS aérien zone | 1 600 | 220 | Légendaire |
| Cowboy | Far West | 3 | DPS distance | 650 | 160 | Commune |
| Bandits (×4) | Far West | 4 | Essaim rapide | 250 | 70 | Commune |
| Shérif | Far West | 5 | DPS ciblé (vise le plus fort) | 1 200 | 280 | Rare |
| Train fou | Far West | 6 | Charge en ligne droite | — | 800 | Épique |
| Ouvrier à vapeur | Ère industrielle | 2 | Réparateur de bâtiments | 400 | 40 | Commune |
| Canon Gatling | Ère industrielle | 4 | Bâtiment défensif | 1 300 | 60 / 0,2 s | Rare |
| Zeppelin | Ère industrielle | 6 | Tank aérien, bombes | 2 500 | 250 | Épique |
| Usine d'automates | Ère industrielle | 5 | Générateur d'unités | 900 | — | Rare |
| Robot sentinelle | Futur | 4 | Tank à bouclier | 1 800 | 150 | Commune |
| Drones (×3) | Futur | 3 | Essaim aérien | 200 | 60 | Commune |
| Laser orbital | Futur | 4 | Sort ligne | — | 450 | Rare |
| Mecha Titan | Futur | 8 | Méga-tank | 5 500 | 400 | Légendaire |
| Ancre temporelle | Neutre | 3 | Anti-Rembobinage | 800 | — | Rare |
| Paradoxe | Temporel | 6 | Rembobinage | — | — | Légendaire |
| Sablier figé | Temporel | 4 | Gel de zone | — | — | Épique |
| Accélération | Temporel | 3 | Boost de zone | — | — | Rare |
| Écho | Temporel | 5 | Copie fantôme | — | — | Épique |

**Les « Paradoxes » : synergies entre époques**

Quand deux unités précises se touchent, elles déclenchent un effet bonus. C'est ce qui donne envie d'expérimenter avec ses decks.

- **Cowboy + T-Rex** → « Rodéo » : le cowboy monte sur le T-Rex, qui gagne une attaque à distance.
- **Chevalier + Robot sentinelle** → « Armure du futur » : le chevalier gagne un bouclier de 400 PV.
- **Dragon + Zeppelin** → « Ciel en feu » : les bombes du zeppelin enflamment le sol 3 s.
- **Archers + Drones** → « Flèches guidées » : les flèches ne ratent plus leur cible.

Les Paradoxes sont découverts en jouant (pas listés au départ) et ajoutés à un « Codex du temps » : c'est une collection à compléter qui pousse à rejouer.

## 5. Progression

Le joueur progresse sur trois axes en parallèle (trophées, niveau de cartes, Pass saisonnier) pour toujours avoir un objectif proche.

**Les trophées et les arènes**

- Une victoire rapporte environ +30 trophées, une défaite en retire environ -28 (ajusté selon l'écart avec l'adversaire).
- Chaque palier débloque une nouvelle arène (un nouveau décor de cadran), avec ses propres cartes à gagner.

| Arène | Trophées | Débloque |
| --- | --- | --- |
| 1. Vallée des Dinosaures | 0 | Cartes Préhistoire |
| 2. Château de Camelot | 400 | Cartes Médiéval |
| 3. Ville fantôme | 1 000 | Cartes Far West |
| 4. Usine à vapeur | 1 800 | Cartes Ère industrielle |
| 5. Métropole 3000 | 2 800 | Cartes Futur |
| 6. Faille du Temps | 4 000 | Cartes Temporelles + classement mondial |

**Le niveau des cartes**

- 11 niveaux par carte, améliorés avec des copies de la carte et de l'or.
- En match classé, le niveau est **plafonné selon l'arène** : un joueur qui paie ne peut pas écraser les autres. Ce choix limite le « pay-to-win ».

**Les récompenses de match**

- Chaque victoire remplit une **Capsule temporelle**, avec un contenu **affiché avant l'ouverture** (pas de loot box aléatoire, voir section 6).
- **Quêtes quotidiennes** (3 par jour) et **hebdomadaires**, qui s'accumulent jusqu'à 3 jours si le joueur ne se connecte pas.

**Les saisons (4 semaines)**

- Un **Pass saisonnier** avec une voie gratuite et une voie premium.
- Une époque « à l'honneur » chaque saison (exemple : saison de l'Égypte antique), avec 2 nouvelles cartes.
- Un reset partiel des trophées au-dessus de 4 000.

**Les modes de jeu**

- **Classé** : le mode principal, 1 contre 1.
- **Entraînement contre l'IA** : sans perte de trophées, aussi utile tant qu'il y a peu de joueurs.
- **Défis du week-end** : règles spéciales (exemple : tout le monde a le Paradoxe, ou énergie ×2).
- **Plus tard** : 2 contre 2 et un mode clan (« Guildes du temps »).

## 6. Monétisation éthique et règles des stores

Le jeu est gratuit (free-to-play) et gagne de l'argent surtout avec le cosmétique et le Pass, jamais avec de la puissance pure.

**Les sources de revenus**

| Source | Prix indicatif | Ce que le joueur obtient |
| --- | --- | --- |
| Pass saisonnier premium | 4,99 $ / saison | Récompenses supplémentaires, skin exclusif, emote |
| Skins d'unités | 1,99 – 9,99 $ | Apparence uniquement (exemple : T-Rex robotique) |
| Skins de tours et de cadran | 2,99 – 6,99 $ | Apparence uniquement |
| Gemmes (monnaie premium) | 0,99 – 49,99 $ | Accélère la progression, achat de skins |
| Pubs récompensées | Gratuit pour le joueur | Doubler une récompense, 1 fois par capsule |
| Offre de démarrage | 1,99 $ (une seule fois) | Gemmes + or + 1 skin, très rentable pour la conversion |

**Ce qu'on s'interdit**

- **Aucune loot box payante à contenu aléatoire** : le contenu de chaque capsule est affiché avant achat ou ouverture. Les loot boxes sont interdites ou encadrées dans plusieurs pays (Belgique, Pays-Bas en partie), et elles nuisent à l'image du jeu.
- **Pas de pubs forcées** pendant ou entre les matchs, seulement des pubs que le joueur choisit de regarder.
- **Pas de punition** si le joueur ne se connecte pas un jour (pas de série perdue).
- **Des limites de dépenses** proposées aux comptes mineurs.

**Les règles des stores à respecter**

- **Les achats de contenu numérique passent obligatoirement par le système de paiement d'Apple et de Google** (pas de paiement externe dans l'app, sauf cas prévus par les règles locales).
- **Les probabilités doivent être affichées** pour toute récompense aléatoire, même gratuite.
- **La classification d'âge** (PEGI, ESRB via IARC) est à remplir honnêtement : le jeu vise PEGI 7.
- **Une politique de confidentialité** publique, la fiche « Data safety » sur Google Play et l'étiquette de confidentialité sur l'App Store.
- **La suppression de compte** doit être possible depuis l'app (exigée par Apple et Google).
- **La conformité RGPD** pour les joueurs européens, et un consentement pour les pubs personnalisées.
- **Le nom et les visuels** doivent être 100 % originaux : aucune ressemblance avec un jeu existant.

## 7. Architecture technique

Tout est en C# : Unity pour le jeu, .NET pour le serveur de match et l'API. La même bibliothèque de simulation tourne sur le client et sur le serveur.

**Les composants**

- **Client Unity (iOS et Android)** : affichage, entrées, juice, pubs récompensées. Il prédit le match avec la simulation partagée, et parle au serveur de match en temps réel (UDP) et à l'API (HTTPS).
- **Serveur de match (.NET)** : la seule source de vérité. Simulation autoritaire à 20 ticks/s, 100 photos d'état gardées (5 s de Rembobinage), anti-triche : le client n'envoie que les cartes jouées. Il envoie le résultat du match à l'API (trophées, capsule).
- **API services (ASP.NET Core)** : comptes, decks, trophées, quêtes, boutique, Pass, capsules, et lancement des matchs (matchmaking).
- **PostgreSQL** : comptes, decks, trophées, achats.
- **Redis** : file de matchmaking, sessions, classement.
- **Apple et Google** : paiements in-app obligatoires, reçus vérifiés côté serveur par l'API.

**La structure de la solution .NET**

| Projet | Type | Rôle |
| --- | --- | --- |
| TimeClash.Simulation | Bibliothèque .NET Standard 2.1 | Règles du combat, cadran, Aiguille, Noyau, cartes, Rembobinage. Partagée avec Unity |
| TimeClash.Contracts | Bibliothèque | Messages réseau et DTO communs |
| TimeClash.MatchServer | Console .NET | Boucle de jeu 20 ticks/s, réseau UDP |
| TimeClash.Api | ASP.NET Core | Clean Architecture + CQRS/MediatR : comptes, decks, boutique |
| TimeClash.Client | Projet Unity | Rendu, UI, sons, SDK pubs et achats |

**Comment fonctionne le Rembobinage côté serveur**

1. À chaque tick, le serveur copie l'état des unités, des tours et de l'Aiguille dans un **buffer circulaire** de 100 cases (5 s à 20 ticks/s).
2. Quand un joueur joue Paradoxe, le serveur relit la case d'il y a 100 ticks.
3. Il restaure uniquement les entités de l'adversaire et les PV des tours du lanceur, renvoie les unités posées entre-temps dans la main adverse, et fait reculer l'Aiguille de 30°.
4. Il envoie l'état corrigé aux deux clients, qui jouent l'animation de rembobinage.

**Les choix techniques importants**

- **Le réseau** : UDP avec une bibliothèque C# comme LiteNetLib, ou une solution intégrée (Unity Netcode, Photon Fusion) pour aller plus vite.
- **Le déterminisme** : utiliser des calculs en virgule fixe dans la simulation, pour que client et serveur obtiennent exactement le même résultat.
- **La validation des achats** : chaque reçu Apple ou Google est vérifié par l'API avant de créditer des gemmes.
- **L'hébergement** : serveurs de match sur des VPS proches des joueurs (Europe d'abord), API et bases de données sur un cloud managé, le tout en conteneurs Docker.
- **Le suivi** : analytics de jeu (rétention, équilibrage des cartes) et rapports de crash dès le prototype.

## 8. Direction artistique, UI et « juice »

Un style Art déco et jouets mécaniques, en laiton et bleu nuit : chaque unité ressemble à une figurine d'horlogerie peinte.

**Le style visuel**

- **Vue de dessus** sur le cadran, légèrement inclinée pour donner du relief aux figurines.
- **Les unités** sont des figurines low-poly stylisées, comme des pièces d'horlogerie peintes : rouages, rivets, laiton, clé de remontoir, avec des proportions légèrement chibi et une silhouette lisible de loin.
- **La palette** : bleu nuit #0F1A2B (fond), #13223A (cadran), laiton #D4A24C / #E9C77B (cadres, Aiguille, pastilles d'énergie), crème #F2E6CC (cartes), camp joueur turquoise #3FB8AF, camp adverse corail #E86A58.
- **Les couleurs d'époque** : Médiéval #2F5FC4, Far West #A8662A, Préhistoire #3F7F2F, Ère industrielle #B5652B, Futur #2BA6C9, Temporel #7046D9.
- **La typographie** : Bungee pour les titres et les chiffres, Inter pour le texte.
- **Les effets temporels** ont leur propre code visuel : sépia pour le Rembobinage, bleu glacé pour le gel, traînées lumineuses pour l'accélération.

**L'interface**

- Jeu à une main en mode portrait, avec les 4 cartes en bas de l'écran, à portée du pouce.
- **Les cartes** sont crème, avec un cadre laiton, une pastille de coût en forme d'engrenage et un liseré de couleur d'époque en bas.
- **La jauge Chronos** est faite de 10 pastilles dorées.
- **La barre du haut** affiche l'adversaire, le chrono, le prochain passage de l'Aiguille et les couronnes.
- Un écran d'accueil avec 5 onglets maximum : Boutique, Cartes, Combat, Guilde, Événements.
- Des emotes rapides pendant le match (sans chat libre, pour éviter la toxicité).

**Le « juice » (les retours de satisfaction)**

- **Un léger tremblement d'écran et une vibration** quand une grosse unité est posée ou qu'une tour tombe.
- **Des nombres de dégâts qui « sautent »**, plus gros et dorés pour les critiques.
- **Le passage de l'Aiguille** : un « tic » sonore et une onde dorée sur les unités ralenties.
- **Un ralenti d'une demi-seconde** quand l'Horloge Maîtresse est détruite.
- **Le Rembobinage** : un filtre sépia, l'Aiguille qui recule, les unités qui reculent à l'envers, et le son d'un mécanisme qu'on remonte. C'est le moment à rendre le plus spectaculaire.
- **L'ouverture de capsule** en 3 temps : tremblement, lumière, révélation des cartes une par une.

**Le son**

- Une musique qui change selon l'arène et qui accélère pendant l'Heure de pointe, avec un tic-tac de fond.
- Une « voix » sonore distincte par époque : rugissements, cliquetis d'armure, coups de revolver, vapeur, sons électroniques.

**La production des assets**

Les modèles sont générés avec Meshy (texte vers 3D, auto-rig, animations), retouchés et animés dans Blender via Blender MCP, puis intégrés dans Unity via Unity MCP. Prompt de style commun pour toutes les unités : « stylized low-poly mechanical toy figurine, art deco clockwork details, brass rivets and gears, painted enamel colors, slightly chibi proportions, clean readable silhouette from top-down view, mobile game asset ».

## 9. Roadmap, budget et KPIs

Le plan vise un lancement mondial environ 12 mois après le début, en validant que le jeu est fun **avant** de construire le multijoueur.

**Les phases**

1. **Prototype (mois 1–2)** : 8 cartes, l'arène Horloge, combat contre l'IA, Paradoxe, Aiguille et Noyau jouables. Critère pour continuer : 10 testeurs rejouent sans qu'on leur demande.
2. **Vertical slice (mois 3–4)** : 3 époques, 15 cartes, graphismes finaux sur une arène, juice complet.
3. **Multijoueur (mois 5–7)** : serveur de match, matchmaking, comptes, decks, trophées.
4. **Contenu et méta (mois 8–9)** : 25 cartes, 6 arènes, capsules, quêtes, Pass, boutique, pubs récompensées.
5. **Soft launch (mois 10–11)** : sortie dans 2 ou 3 petits pays (exemple : Philippines, Canada) pour mesurer la rétention et équilibrer les cartes.
6. **Lancement mondial (mois 12)** : App Store et Play Store, puis une saison toutes les 4 semaines.

**Le budget de départ (estimation)**

| Poste | Coût |
| --- | --- |
| Compte Apple Developer | ~99 $ / an |
| Compte Google Play | ~25 $ (une fois) |
| Unity Personal | Gratuit sous 200 000 $ de revenus et fonds sur 12 mois |
| Meshy (génération 3D) | Gratuit ou ~20 $ / mois |
| Packs d'assets et sons | 200 – 600 $ (une fois) |
| Artiste freelance (icône, retouches) | 300 – 1 500 $ |
| Serveurs de match + API + base de données | 20 – 80 € / mois au lancement |
| Commission des stores | 15 % sur le premier million de dollars de revenus par an |

Les prix des serveurs, des outils et des freelances sont des estimations, à vérifier auprès des fournisseurs.

**Les KPIs à suivre pendant le soft launch**

| Indicateur | Objectif minimum | Bon résultat |
| --- | --- | --- |
| Rétention J1 (joueurs revenus le lendemain) | 35 % | 45 % et plus |
| Rétention J7 | 12 % | 20 % et plus |
| Rétention J30 | 4 % | 8 % et plus |
| Durée de session moyenne | 8 min | 15 min et plus |
| Matchs par jour et par joueur actif | 4 | 7 et plus |
| Joueurs payants | 2 % | 4 % et plus |

Ces objectifs sont des repères courants pour les jeux mid-core, pas des garanties. Si la rétention J1 reste sous 30 %, on améliore le gameplay avant de dépenser en publicité pour attirer des joueurs.

**Sources**

- [Unity — offres et seuils de revenus 2026](https://unity.com/runtime-fee)
