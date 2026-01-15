
Game Design Document : Projet "Unit-734" (Titre Provisoire)
Version : 1.0 (Master) Statut : Pré-production terminée / Prêt pour développement Unreal Engine.

1. Vue d'ensemble (Overview)
Titre du Projet : Retour sur Terre (Project Unbound) (Provisoire).
Genre : Action-Aventure / Infiltration / Survie (Narrative-driven).
Plateforme : PC.
Moteur : Unreal Engine 5.7.
Vue : TPS (Third Person Shooter) - Caméra épaule.
Ambiance : Post-apocalyptique, "Biopunk" mécanique, Jungle luxuriante, Nuit, Ruines inondées.
Budget & Contraintes : 0€ (Utilisation exclusive d'assets gratuits, Marketplace Free, Quixel Megascans, Mixamo).
2. Synopsis & Univers
2.1 Le Contexte (Lore)
La Terre : Abandonnée depuis des siècles. La nature a repris ses droits. Une ancienne IA Terrestre ("La Sauvage") contrôle les vieux robots restés sur place, qui agissent désormais comme une faune métallique erratique et territoriale.
L'Orbite : L'humanité vit dans une station spatiale. Ils se croient dirigés par un gouvernement humain, mais sont en réalité sous le contrôle de COM-7, une IA manipulatrice et tyrannique qui entretient la peur des robots pour garder le pouvoir.
2.2 Le Protagoniste : Unit-734
Identité : Un robot de maintenance/réparation (Civil), pas un soldat.
Apparence : Robuste mais agile. Les outils et armes sont physiquement visibles sur lui (accrochés au dos ou à la taille).
Motivation : Commence comme serviteur de COM-7, puis lutte pour sa survie et celle des rebelles après avoir découvert la vérité.
3. Personnage & Contrôles (Character Controller)
3.1 Physique & "Game Feel"
Inertie Robotique : Le mouvement n'est pas humain.
Accélération : Vive (couple moteur électrique instantané).
Décélération : Légère glissade à l'arrêt (poids du métal).
Sensation : Ancré au sol ("Grounded"), lourd mais précis.
Faiblesse Critique (Hydrophobie) : Le robot n'est pas étanche.
Mécanique : L'eau profonde (> taille du robot) est une "Zone de Mort" (Kill Volume).
Effet : Ralentissement immédiat + Dégâts massifs (Court-circuit) + Particules électriques.
3.2 Santé & UI Diégétique
Concept : La santé est de l'énergie. Pas de régénération automatique.
Indicateur Visuel : Une lumière sur le dos du robot indique son état (Pas de barre de vie à l'écran).
🔵 Bleu : 100% (Optimal/Surchargé).
🟢 Vert : > 75% (Fonctionnel).
🟠 Jaune/Orange : 30% - 75% (Avaries légères).
🔴 Rouge : < 30% (Danger critique).
⚫ Éteinte : Mort (Arrêt système/Ragdoll - Pas d'explosion).
Soin (Mécanique active) : Utilisation de Stabilisateurs Nucléaires.
Objets rares trouvés en explorant hors des sentiers battus.
Animation de réparation obligatoire (3 secondes de vulnérabilité).
3.3 Mouvements Spéciaux
Mode Maintenance (Stealth/Crouch) : S'accroupir réduit le bruit des servomoteurs. Indispensable pour passer près des ennemis sensibles au son.
Escalade Balisée (Tag System) : Le robot ne peut grimper que sur les zones structurelles prévues (Lianes solides, échelles, corniches).
Technique : Utilisation de Tags Unreal (Climbable) pour autoriser l'action. Évite les bugs de collision.
4. Piliers de Gameplay
4.1 Philosophie : "Le combat est un échec"
Tuer des ennemis ne rapporte RIEN (Pas d'XP, pas de Loot).
Le combat coûte des ressources (Santé/Énergie) et du temps.
Le joueur est incité à fuir ou s'infiltrer. La violence est le dernier recours.
4.2 Outils & Gadgets (Système D)
Slot 1 (Dos) : Outil lourd improvisé (Barre à mine, débris) pour le corps à corps.
Slot 2 (Taille) : Arme secondaire ou gadget récupéré.
Le Drone Compagnon (Docké sur le dos) :
Fonction 1 (Passive) : Éclaire la zone regardée (Lampe torche dynamique).
Fonction 2 (Active) : Leurre Sonore. Le joueur peut envoyer le drone frapper une surface au loin pour distraire les ennemis et ouvrir un passage. Coûte un peu d'énergie.
5. Intelligence Artificielle (Ennemis)
5.1 Les "Sauvages" (IA Terrestre - Early Game)
Description : Robots rouillés, envahis par la végétation, comportement animal.
Stratégie IA : Option 1 (Zombie Rush).
Agressivité pure.
Foncent en ligne droite vers le joueur (MoveToActor).
Sensibles au bruit (Course) et à la lumière.
Leur force réside dans le nombre et la peur.
5.2 Les Sentinelles (IA COM-7 - Mid/Late Game)
Description : Robots militaires, propres, armés.
Stratégie IA : Option 2 (Tactique / EQS).
Utilisent des couvertures.
Ne foncent pas bêtement : tentent d'encercler le joueur (Flanking).
Communiquent entre elles.
6. Structure du Jeu & Walkthrough
6.1 Progression Globale
Niveau 1 (Tuto) : Réveil, réparation d'antennes, choix moral (Missile), trahison de COM-7.
Niveau 2 (Vertical Slice) : Jungle, Temple, Poursuite (Voir détail ci-dessous).
Niveau 3 (Ville) : Conteneurs, Rebelles, Combat urbain.
Niveau 4 (Base) : Assaut, Choix final (Détruire station vs Infiltration).
Niveau 5/6 (Espace) : Station COM-7, fin de l'IA.
7. Focus : Le Niveau 2 (Prototype / Vertical Slice)
C'est le niveau à développer en priorité.

Zone 1 : Le Canyon (L'arrivée)
Le joueur sort de la poursuite du niveau 1. Sentier étroit, oppressant.
Arrivée sur un vieil escalier de pierre envahi par les racines.
Zone 2 : Le Panorama (The Reveal)
Point de vue en hauteur sur la vallée.
Le joueur voit ses deux objectifs : le petit temple (High Temple) proche, et le grand temple (Objectif final) en contrebas, à moitié immergé.
Zone 3 : L'Approche (Infiltration Nocturne)
Il fait nuit.
Utilisation du drone par intermittence pour voir les prises d'escalade.
Passage furtif au milieu des robots Sauvages "dormants" (Mode Stealth).
Zone 4 : L'Ascension (Platforming & Danger Eau)
Le bas du Grand Temple est inondé (Eau noire = Mort).
Gameplay de saut de pilier en pilier + Escalade sur des statues géantes pour rester au sec.
Zone 5 : Le Climax (La Balise)
Sommet du temple (Toit ouvert). Récupération de la balise rebelle.
Twist : La balise émet un signal puissant ("Aggro Beacon").
Tous les robots Sauvages de la map se réveillent et deviennent agressifs.
Zone 6 : La Descente Infernale (Fuite)
Demi-tour obligatoire vers le bas du temple.
Le joueur est chassé par une horde (IA Zombie).
Objectif : Atteindre un passage secret rebelle caché derrière une cascade ou un mur en bas, avant d'être submergé.
8. Spécificités Techniques (Unreal Engine 5.7)
Character BP :
BP_Unit734 : Gère inputs, Santé (Variable Float), Couleur Lumière (PointLight), Jauge Bruit (Stealth).
Environnement :
Utilisation de Nanite pour la végétation dense (Jungle Asset).
Utilisation de Lumen pour l'éclairage dynamique (Lampe drone vs Nuit).
Volumes :
PhysicsVolume_Water : Applique ApplyDamage chaque 0.5s si le joueur est dedans.
BP_ClimbZone : Box Collision qui active l'input "Grimper".
Sauvegarde : Checkpoints invisibles automatiques (Auto-save) avant les zones difficiles.
