PROJET DE COMPILATION
Du texte d'une expression régulière à l'automate

1. Présentation
Transformation d'une expression régulière en AFN avec ε-transitions par analyse prédictive LL(1) et construction de Thompson. Simulation des mots et export Graphviz.

2. Prérequis
Python 3 ; Graphviz pour produire les images PNG.
Aucune bibliothèque Python externe nécessaire.

3. Organisation
src/
    lexer.py : analyse lexicale
    analyseur_syntaxique.py : analyse prédictive et construction
    automate.py : constructions de Thompson
    simulation.py : reconnaissance des mots
    export_graphviz.py : export DOT
    main.py : interface en ligne de commande
tests/
    tests.txt : expressions valides
    erreurs.txt : expressions invalides
    lancer_tests.py : tests automatiques
automates/
    Fichiers DOT et images PNG générés par Graphviz.

4. Exécution depuis la racine du projet
python src/main.py "a|b" a b ab
Résultat attendu :
a : OUI
b : OUI
ab : NON

Opérateurs : | (union), * (étoile), + (répétition positive), ? (optionnel).
La concaténation est implicite. Les parenthèses permettent le regroupement.
@ représente le mot vide dans les expressions et tests.txt.
En ligne de commande, passer un argument vide ("") pour tester le mot vide.

5. Export et visualisation
Créer le dossier automates/ s’il n’existe pas déjà.
Depuis la racine du projet :
python src/main.py "a|bc*" --dot automates/automate.dot
dot -Tpng automates/automate.dot -o automates/automate.png

6. Tests automatiques Jeu de tests complet (partie 6)
python tests/lancer_tests.py
