##WEBGL - BABYLON

* Simon Ziza et Guillaume Emery

**Introduction :**

A l'aide de la bibliothèque *Babylonjs*, nous avons réalisé un mini jeu. Le but est de faire passer la balle dans l'anneau.


**Comment jouer :**

→ Il faut commencer par choisir la direction de la balle, ainsi que la force :
	- flèche gauche et flèche droite pour orienter la balle horizontalement
	- flèche haut bas pour orienter la balle verticalement
	- a pour augmenter la puissance et z pour la diminuer

Ces trois caractéristiques sont affichées dans l'espace 3D par un repère orthogonal : 
Ainsi, quand le joueur change une direction, la flèche correspondante va augmenter ou diminuer en temps réel.
→ Quand la balle est prête à être tirée, il ne reste plus qu'à appuyer sur la barre espace.
→ Pour replacer la balle à la position initiale, appuyer sur la touche retour/effacer/backspace.
→ Jouez sur 6 niveaux différents ! ( clavier, numéro 0;1;2;3;4;5).


**Choix techniques adoptés :**

→ physique du tore
	Pour le tore, il n'existe pas de type de *PhysicsImpostor* particulier comme pour la sphère (*SphereImpostor*). On utilise le type le plus générique, *MeshImpostor*. 
Les autres types ne fonctionnant pas correctement dans notre cas. En effet nous les avons essayé, notamment *SphereImpostor* et *CylinderImpostor*, mais la balle ne pouvait plus passer au milieu du tore.
Le type *MeshImpostor* fonctionne plutôt bien ; nous avons cependant observé quelques fois un bug, ou la balle traversait le tore ( la partie pleine), ce bug arrive le plus souvent quand la balle est rapide.

→ impulsion donné à la balle
	Pour lancer la balle, nous avons décidé d'utiliser la fonction *applyImpulse*, qui applique un vecteur vitesse à l'objet sélectionné.

→ annuler la vitesse :
	Lorsque l'on replace la balle à la position initiale, il ne faut pas oublier de remettre à zéro et le vecteur vitesse et le vecteur rotation (-setLinearVelocity* et *setAngularVelocity*), sinon la balle conserve sa vitesse d'avant repositionnement.

→ Lumière et ombre :
	On utilise des *spotlights* pour imiter des lampadaires. Cependant nous avons d nous limiter à 2 au lieu de 4 (un dans chaque angle) à cause de la latence qui apparaissait et qui empêchait de profiter pleinement du jeu. Nous avons toutefois laissé dans le code les deux *spotlights* supplémentaire, commenté, qui une fois décommenté donne un effet stade de foot à la scène.

