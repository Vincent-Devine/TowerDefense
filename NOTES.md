DEVINE
MAZURIE
ZALLIO

# Commentaire général
Très bon rendu, vous avez fait fort ! Vous êtes allé bien au-delà des attentes. (Voir les détails dans NOTES.md)

## Programmation orientée objet
### Héritage $$5
Bonne utilisation de l'héritage
### Encapsulation $$3.5
Partielle. Beaucoup de membres `public` (variables et fonctions) auraient mérités être en `private`.
Comme par exemple `Game::InitButton()` ou `InitText()`
### Fonctions virtuelles $$4.5
Bonne utilisation des fonctions virtuelles, aussi bien pour les éléments de gameplay que pour les systèmes (scene, ui)
### Utilisation de références et pas de copies inutiles $$5
Pas de problèmes constatés.

## Clarté du code
### Niveau d'abstraction cohérent (updates en cascade) $$4
Main -> Scene -> Update. Ce découpage fonctionne bien !
Attention à ce que la granularité de vos fonctions (niveau de détail), soit cohérent.
### Clarté des nommages (fonctions/variables) $$4.5
Plutôt soigné
### Découpage des fichiers cohérent $$4.5
Bon découpage, le code est plutôt bien réparti

Par contre, le `Game::Update()` aurait pu être plus clair. Par exemple, `sWave->Update(sTimeScale);` et `CheckForWin();` sont parlant. Il aurait fallu faire de mêmes avec la gestion des enemies morts et la supression des tours vendues.

## Fonctionnalités
### Qualité du rendu $$4.5
Très bon polish. Vous avez eu le soucis du détail. L'ensemble est cohérent et vraiment agréable à parcourir.

### Absence de warning à la compilation $$5
OK

### Memory leaks $$4
Problème de flow de destruction : Gros memory leak (~Game n'est pas appelé) lorsqu'on quitte une partie en passant par le menu pause. Le problème ne survient pas lorsqu'on fait échap en jeu.

Pas de leak critiques (récurrents)

Pas de leaks de resources.

### Crash $$4
Pas de crash mais un dépassement de limite rencontré lors d'une partie (voir buffer_overflow.txt)

## Présentation
### Commentaires $$2
Quasi absence de commentaire !
### Readme $$3.5
Readme correct, mais aurait mérité un peu plus de travail pour rendre hommage à la qualité du jeu (screenshots).
### Norme de code $$3.25
Norme pas toujours consistante (underscore pour les paramètres de fonction, préfixe m pour les membres).

## Bonus $$5
### Sons $$5
Très bonne intégration sonore
### Format de donnée (niveau, score) $$5
Niveau
### Editeur de niveau $$5
Editeur de map/waves/chemin
Vous avez fait fort !!

## Git
### Qualité des messages $$3.25
Plutôt bons dans l'ensemble mais éviter les messages de style :
- liujhnbf vcxdfxgchm,.
- t4un ca marche
- JE VE CASSE MASTER MDR,
- Update à 23h :=)

### Régularité des commits $$4
Commits réguliers


## Gestion de projet
### Utilisation des tâches GitLab $$4.5
Très bonne utilisation
### Bonne répartition des tâches $$4.5
Semble assez bien réparties

## Code review (divers)
Attention à votre gestion "risquée" des UIelements.

```c++
// Ca ->
UIelements[mItStatTower[i]]->isActive = !UIelements[mItStatTower[i]]->isActive;
// Ou ça ->
((Button*)UIelements[1])->mSprite.SetTexture(SpeedTextureX2);

// Aurait été plus clair avec :
mStatTowerButtons[i]->isActive = !mStatTowerButtons[i]->isActive;
// Et 
mSpeedButton->mSprite.SetTexture(SpeedTextureX2);
```

C'est dès de la construction de ces objets qu'il faut garder ces références. Conserver un pointeur vers la classe concrête est beaucoup plus pratique de que de stocker un index vers un tableau de classe abstraite.

Concrêtement :
```c++
// Dans le constructeur, au lieu de :
UIelements.push_back(new Button(collision::Box(1550, 30, 125, 80), ...

// On aurait eu :
mSpeedButton = addUIElement<Button>(new Button(collision::Box(...)));

// Avec l'ajout de la fonction addUIElement() dans la classe de base
// ainsi que potentiellement un removeUIElement(UIElement*) qui aurait été utile au lieu de faire un .erase manuellement sur la liste UIElements

// Evidemment, pour les objets qui ne nécessitent pas d'intéraction, pas la peine de stocker le pointeur
addUIElement(new UIText(...); // Suffit
```

Une fonction protected virtuelle DoUpdate() dans la classe scène aurait éviter l'appel de :
```c++
void GameOver::Update() 
{
    Scene::Update(); // Appelée dans chaque scene
}

// La modif ->
void Scene::Update()
{
    DoUpdate(); // <- Fonction à override dans les classes enfants
    // Render UIElements, etc...
}
void GameOver::DoUpdate() 
{
    // Spécificité du game over screen 
}
```
La musique devrait être en format compressé et jouée via `PlayAudioStream()` plutôt que `PlaySound()`.

