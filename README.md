# Kicad_Method
How to use kicad to realize modules

PROCESS KICAD

1 - Donner un nom de projet sans espaces ni accents

2 - Remplir le cartouche (Fichier ; Ajustage page)

	2.1 - Anticiper les zones à dupliquer
	2.2 - Poser les composants et les test points sur eeschema
	2.3 - Donner les valeurs aux composants 
	2.4 - Ne pas numéroter les composants (Cela se fait à la fin en annotation automatique)
	2.5 - Toujours prolonger les pattes des composants par un fil
	2.6 - Je jamais hésiter à mettre des commentaires si besoin
/!\ une * avant le commentaire permet la simulation SPICE (Simulation Program with Integrated Circuit Emphasis : https://fr.wikipedia.org/wiki/SPICE_(logiciel) )
	2.7 - Placer les équipotentiels : GND, VCC, label local, label global
	2.8 - Créer composants si besoin
	2.9 - Annotation automatique

3 - ERC

Exécution du contrôle des règles électriques ERC (Electrical Rules Check)
Vérification automatiquement votre schéma. Il détecte les erreurs dans la feuille, comme les pins ou les symboles hiérarchiques non connectés, les sorties en court-circuit, etc. . .

4 - Assigner les empreintes

	4.1 - Mettre la grille à 0,635 mm est un bon compromis pour commencer
	4.2 - Ouvrir l’éditeur d’empreintes 
	4.3 - Chercher les empreintes manquantes, ne pas hésiter à s’aider des datasheets
	4.4 - Pour faire des recherches sur le net : par ex NE555 type:pdf (privilégiez les documents fourni pas le constructeur par ex : Texas Instrument au lieu de prendre chez AllDatasheet. 
		Les documents sont plus sûrs…
	4.5 - Anticiper les diamètres des pattes de composants pour les perçages.
	4.6 - Mettre les 3 couches :
		→ F.Silks
		→ F.Cryd
		→ F.Fab

5 - Générer la NetList

	5.1 - Choisir sa destination

6 - Ouvrir PCBnew

	6.1 - Régler la grille en pouce ou prendre une valeur en mm qui correspond à des pouces comme par exemple 0,635mm (Les composants sont très souvent exprimés en pouces)
	6.2 - Remplir le cartouche une nouvelle fois
	6.3 - Tracer les contour de la carte (couche edge cut) mettre les cotes sur la couche User.Drawings
	6.4 -Mettre les coordonnées du pcb à zéro 
	6.5 - Importer la NetList
	6.6 - Placer les trous de perçage (NPTH - Non Plated Through Hole - Pads à Trous Non-Métallisés)
	6.7 - Décocher F.Fab permet d’éclaircir le schéma
	6.8 - Bien positionner les empreintes /!\ au croisement des pistes
	6.9 - Positionner les éléments avec la contrainte de la face avant ou du Cahier Des Charges
	6.10 - Gestion des couches
	6.11 - Configurer le routeur interactif
	6.11.1 - Option du CI
	6.11.2 - Choisir 2 couches et les composants dessus et dessous car cela permet d’alléger le nombre de couches apparentes.
	6.11.3 - Règles de conception
		Ce sont les classes de routage (Par exemple Eurocircuit pcb Calculator)
		C’est la technologie utilisée avec sa classification : de 3 à 9
		La classe 6 est utilisée par défaut.
	6.12Les classes d’équipotentiels
	6.12.1Classe dédiée aux signaux, classe dédiée aux alimentations, etc.

7 - Tracer les pistes

	7.1 - Préférences/Préférences/Accrochage aux pads : toujours
	Préférences/Préférences/Accrochage aux pistes : toujours
	7.2 - Tracer les pistes /!\ elles ne suivent pas un déplacement de composants
	7.3 - Tracer le plan de masse (Lorsque vous bougez des pistes ou des composants il est nécessaire d’actualiser le plan de masse, un appui sur la touche B met à jour.
	7.4 - Routeur interactif
	7.4.1 - Choisir drag interactif (Les pistes suivent les vias)
	7.4.2Choisir pousser ou contourner

8 - La sérigraphie

	8.1 - Déplacer les références pour accroître la visibilité
	8.2 - Ajouter des textes en plus : Nom du PCB, Version, Déco…
	8.3 - Double clic sur le texte afin de le mettre en invisible s’il n’est pas important de le laisser apparaître en sérigraphie.

9 - La couche de fabrication (Facultative)

	9.1 - Elle ne sert que si le fournisseur place les composants
	9.2 - Vous pouvez décocher les couches non utiles B.Cu, F.Cu etc
	9.3 - Pour faire disparaître les pads, allez dans l’onglet Couches/Éléments

10 - Faire le rendu 3D du PCB

11 - Générer les fichiers GERBER

	11.1 - Créer un dossier dédié GERBER et mettre tous les fichiers générés dedans.
	11.2 - Il faudra Zipper le dossier pour l’envoyer au fabricant
	11.3 - Fichier/Fichiers de fabrication/Gerber .gbr
	11.4 - Options Gerber : Choisir Gerber Protel
	11.5 - Sélectionner les pistes incluses nécessaires au fabricant du PCB
		Couche cuivre : F.Cu et B.Cu
		Couche adhésive : F.Adhesive et B.Adhesive
		Couche pochoir ou stencil : F.Paste et B Paste
		Couche de sérigraphie : F.Silkscreen et  B.Silkscreen
		Couche du vernis épargne : F.Mask et B.Mask
		Couche des dessins explicatifs : User.Drawings
		Couche des commentaires utilisateurs : User.Comments
		Couche avec un usage défini par l’utilisateur : User.Eco1 et User.Eco2
		Couche de définition des coutours du PCB : Edge.Cuts
		Couche de fabrication : F.Fab et B.Fab
	11.6 - Tracer et créer fichier de perçage au format excellon
	11.7 - Possibilité de visualiser les gerbers avec l’outils visionneuse de fichiers Gerber dans la fenêtre projet.

12 - BOM Bill of materials (en français, nomenclature ou liste de pièces)

	12.1 - Installer : Interactive BOM sur Github : https://github.com/openscopeproject/InteractiveHtmlBom/wiki
	12.2 - Parametrage : Il faut créer un dossier pour stocker les résultats (Dossier BOM)





A poursuivre :

Règle pour définir la largeur des pistes
Rainurage pour JlcPCB (Renommer le .Gml en .GKO)
Rainurage pour eurocircuit. Rien à faire
Rechercher une empreinte ou un symbole
Faire la simulation
