# Why ?

> *The age of features is over, we are living in the age of experiences.*  
> Aral Balkan, [during a UX conference titled "Superheroes & Villains in Design"](https://small-tech.org/videos/ux-talk/).

Ce n'est pas juste un projet stylé parce que le Rust c'est hype, qu'il y a un mode watch super réactif, un feedback riche... **on développe une nouvelle expérience d'apprentissage pour s'approcher de la pratique délibérée en informatique !!**

## Pourquoi
Les exercices de code sont au coeur de l'apprentissage d'un language de programmation, cependant avoir des exercices avec des petits programmes ou fonctions à implémenter ne garantit pas que l'expérience de pratique sera efficiente. Selon la pratique délibérée, l'apprentissage profond passe par une boucle de feedback la plus courte possible, or l'expérience actuelle est loin d'être fluide et efficace.

Prenons l'exemple d'un exercice un *petit programme en C qui demande le prénom, nom et l'âge* et affiche une phrase incluant ces 2 valeurs. L'exo fourni dans un PDF, inclut une consigne, un bout de code de départ et un exemple d'exécution, ainsi qu'un code de solution sur la page suivante.  
Pour résoudre l'exercice, une fois la consigne lue, nous allons ouvrir un IDE, créer un fichier `main.c` manuellement, copier-coller le code de départ, lire le code existant et compléter les parties à développer.  
Une fois terminé, passons à la compilation en ouvrant un terminal dans l'IDE en tapant `gcc main main.c & main`, euh zut c'était `gcc -o main main.c && ./main`, on rentre prénom, nom et age, puis comparons l'output manuellement pour voir si c'est bien le résultat attendu, réouvrons la consigne et non il manque l'affichage de l'âge! Revenons au code, on ajoute l'âge et on relance le build et l'exécution, on rentre prénom, nom et âge à nouveau. Est-ce que l'output est bon cette fois ? Vérifions maintenant notre code avec la solution. Okay, on aurait pu utiliser `printf` au lieu de 2 fois `puts()` pour afficher le nom complet. Passons à l'exo suivant, cherchons sa consigne, la voilà, on recommence le cycle,...

Tous ces petites étapes supplémentaires autour de la rédaction du code semblent insignifiantes à première vue mais leur cumul résulte en une friction générale importante. En plus, il n'y aura que peu d'exécutions manuels c'est-à-dire très peu d'occasions de connaître la progression et d'ajuster son code au fur et à mesure, en plus d'une petite charge mentale pour compiler et lancer à la main.

Imaginons que dans un laboratoire de C *nous développions maintenant une bataille navale dans le terminal*. Tester de bout en bout de manière automatique un programme en C n'est pas une tâche évidente, en partie par manque d'outil adapté. Pour tester le fonctionnement global, il faut manuellement lancer une partie et jouer plusieurs coups pour vérifier le fonctionnement et vérifier à chaque étape si le jeu est cohérent dans son état et affichage. Une fois qu'une partie du jeu fonctionne, en développant le reste on risque de casser d'autres parties sans s'en rendre compte.

Un dernier cas concret, en *développant un petit shell en C++*, pour tester l'implémentation des pipes, il faudra compiler le shell ainsi que les CLIs accessibles, lancer le shell, puis taper quelques commandes du type `echo hey there | toupper` voir si l'output est bien `HEY THERE`, ce qui est très lent! Tester plein de plein de cas limites (plusieurs pipes, symbole de pipe collé, redirection stdout et non stderr, exit du CLI à droite du pipe, ...)

En résumé, le manque de validation automatisée ralentit le développement et l'apprentissage. Simplement ajouter des tests automatisés ne résoud pas tous les problèmes, car les tests runner ne sont pas adaptés à des tests sur des exos (pas de consigne, pas d'indices, affichage pas adapté, pas de mode watch, ...), il manque une partie d'automatisation autour. De plus, le travail d'écriture de tests pour des tous petits exos serait beaucoup trop conséquent, dans plein de cas comparer l'output avec une solution suffit à estimer si le programme est fonctionnel.

## Expérience PLX
**Le défi est d'arriver à réduire la friction au strict minimum, d'automatiser toutes les étapes administratives et de fournir un feedback riche, automatique et rapide durant l'entrainement.**

Cette expérience sera atteinte via
1. **La suppression des étapes de compilation et d'exécution manuelles**  
Aucune connaissance du système de compilation ou de ses commandes n'est nécessaire, tout se fait automatiquement dès qu'un des fichiers est sauvé (il suffit donc de taper Ctrl+S ou d'attendre que l'IDE sauve automatiquement)
1. **La suppression de toutes les rédactions manuelles de valeurs dans le terminal**  
Permettre de définir des arguments du programme et un contenu à injecter en `stdin`, avec des variantes pour tester différents cas.
1. **La suppression des étapes de comparaison d'output**  
L'output sera automatiquement comparé et une diff précise (avec surlignage des différences sur chaque ligne) sera affichée pour voir immédiatemment les différences. La diff pourrait supporter du trimming de l'output ou des lignes afin d'ignorer certains espaces blancs insignifiants. Les retours à la ligne et tabulations seront affichées avec un symbole visible.
1. **Une affichage et comparaison avec solution**  
Une fois l'exo résolu, pouvoir auto évaluer sa réponse avec la solution d'un prof est déjà d'une grande aide. Il sera possible de voir une diff de sa réponse avec la solution directement dans PLX.
1. **Une transition fluide entre exos**  
Passer à l'exo suivant devrait prendre moins de 4 secondes, le temps de passer de l'IDE à PLX (Alt+Tab), d'un raccourci (n) dans PLX pour afficher l'exo suivant et le temps que l'IDE réagisse à la demande d'ouverture du fichier.
1. **Aucun changement de fenêtre durant l'exo**  
PLX à gauche avec toute la consigne, l'IDE à droite dans un seul fichier utile, une fois les 2 fenêtres ouvertes, il n'y a plus de changement à faire comme tout est déjà disponible. La consigne s'affiche dans PLX, dès que le fichier ouvert est sauvé, le build et l'exécution se relance. Les erreurs de build sont visibles ainsi que les résultats des tests.

## Contexte
Ce projet tire inspiration de [Rustlings](https://rustlings.cool/) qui permet de s'habituer aux erreurs du compilateur Rust en corrigeant des problèmes de compilation ou en complétant une centaine de petits exercices. Dans la même idée, d'autres languages ont suivis avec golings, cplings, ziglings, ... Ce même projet a inspirée [PRJS](https://github.com/samuelroland/prjs) (Practice Runner for JavaScript), développée à l'occasion du dernier labo libre de WEB et qui permet de s'entrainer sur des fonctions vérifiées via des tests unitaires écrits et lancés avec Vitest en arrière plan.

PLX pousse encore plus loin l'expérience en supportant plusieurs languages, en y incluant la compilation automatique ainsi que le support de types de tests plus primitifs et plus simple à mettre en place qu'avec un framework de test.

Note: contrairement à Rustlings, ce repository ne contient pas d'exercices réels, seulement le code de la TUI PLX. Des exercices de démonstration seront écrits dans différents languages dans un sous dossier `examples`.


