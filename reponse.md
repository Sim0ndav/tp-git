B1-Git - Partie 1 : Création du dépôt et commits
Ouvrir un terminal (terminal Git Bash à privilégier)

Créer, en ligne de commande, un répertoire tp-git
- mkdir tp-git

Se déplacer dans le répertoire
- cd tp-git

Vérifier qu’on est dans le bon répertoire en affichant le chemin du répertoire courant
- pwd

Initialiser un dépôt Git
- git init

Lister tous les fichiers du répertoire (y compris les fichiers cachés) pour s’assurer que le répertoire .git à été créé
- ls -a

Ouvrir ce répertoire sous VS Code


Exécuter git status et copier/coller la sortie
-$ git status
-On branch master
-
-No commits yet
-
-Untracked files:
-  (use "git add <file>..." to include in what will be committed)
-        tp-git/

-nothing added to commit but untracked files present (use "git add" to track)



Créer le fichier fichier1.md avec un contenu quelconque et l’enregistrer (vous pouvez utiliser VS Code pour créer et éditer des fichiers)
-touch fichier1.md
-echo "toto" > fichier1.md
-cat fichier1.md 

Attention, il s’agit bien de créer un nouveau fichier, et non un répertoire. Il en sera de même tout au long de ce TP.
Créer le fichier fichier2.md avec un contenu quelconque et l’enregistrer
-touch fichier2.md
-echo "Bonjour tout le monde" > fichier2.md
-cat fichier2.md 

Exécuter git status et copier/coller la sortie
-$ git status
-On branch master
-
-No commits yet
-
-Untracked files:
-  (use "git add <file>..." to include in what will be committed)
-        fichier1.md
-        fichier2.md
-        
-
-nothing added to commit but untracked files present (use "git add" to track)



Ajouter fichier1.md à l’index de Git (zone de Staging)
-git add fichier1.md

Exécuter git status et copier/coller la sortie
-$ git status
-On branch master

-No commits yet

-Changes to be committed:
-  (use "git rm --cached <file>..." to unstage)
-        new file:   fichier1.md
-
-Untracked files:
-  (use "git add <file>..." to include in what will be committed)
-        fichier2.md


Créer un commit avec pour message: “Ajout de fichier1.md”
- git commit -m "Ajout de fichier1.md"

VALIDATION PROF01

Exécuter git status et copier/coller la sortie
-$ git status
-On branch master
-Untracked files:
-  (use "git add <file>..." to include in what will be committed)
-        fichier2.md
-
-nothing added to commit but untracked files present (use "git add" to track)

Modifier fichier1.md et enregistrer
-nano fichier1.md

Exécuter git status et copier/coller la sortie
-$ git status
-On branch master
-Changes not staged for commit:
-  (use "git add <file>..." to update what will be committed)
-  (use "git restore <file>..." to discard changes in working directory)
-        modified:   fichier1.md
-
-Untracked files:
-  (use "git add <file>..." to include in what will be committed)
-        fichier2.md
-
-no changes added to commit (use "git add" and/or "git commit -a")


Ajouter fichier1.md et fichier2.md à la zone de Staging
-$ git add fichier1.md fichier2.md

Créer un commit “Ajout de fichier2.md et modification de fichier1.md”
-$ git commit -m "Ajout de fichier1.md et modification de fichier1.md"

Exécuter git status et copier/coller la sortie
-On branch master
-nothing to commit, working tree clean

Copier/coller l’ID des deux premiers commits (utiliser log) :

ID commit 1: commit d2a8c787b1ba2badd84a7cf7cdb8cd31732f0d31
ID commit 2: commit 9641a22cb8f28a8be065ea79b44c8bee470f110f

Que signifie qu’un fichier est “tracked” ou “untracked“ ?
- tracked signifie que git garde un oeil sur le fichier et qu'il est suivie
- et inversement untracked signifie que le ficher n'est pas encore suivie car il n'est pas dans la zone - de Staging

Pourquoi doit-on passer les fichiers par la zone de Staging (l’index) avant de les committer ?
- car sans le passage en zone Staging, git n'aura rien a committer ( Staging est comme la salle d'attente avant le commit)

VALIDATION PROF02


B1-Git - Partie 2 : Gestion de branches
Cette partie est à faire sur le même dépôt que la partie précédente. C’est la suite.

Créer une branche fonctionnalite1
- git branch fonctionnalite1

Lister les branches
- git branch

Se déplacer sur la branche fonctionnalite1
- git switch fonctionnalite1

Lister les branches
- git branch

Que représente l’étoile à côté des noms des branches ?
- l'etoile représente la branche sur la quelle on se trouve. 

Créer un nouveau fichier fichier3.md
- touch fichier3.md

Modifier le fichier fichier2.md
- nano fichier2.md

Comment utiliser VS Code pour qu’il nous montre les différences entre l’ancienne version de fichier2.md et la version courante que l’on vient d’éditer ?
- en ouvrant le fichier et ensuite dans le terminal de VS ecrire " git diff "

Committer ces deux modifications : “Fonctionnalité 1 - première phase”
- git add fichier2.md fichier3.md
- git commit -m "Fonctionnalité 1 - première phase"

Créer un nouveau fichier fichier4.md
- touch fichier4.md

Modifier de nouveau le fichier fichier2.md
- nano fichier2.md

Committer ces deux modifications : “Fonctionnalité 1 - terminée”
- git commit -m "Fonctionnalité 1 - terminée"

VALIDATION PROF03

Afficher la liste des fichiers du répertoire
- ls
- fichier1.md  fichier2.md  fichier3.md  fichier4.md

Se déplacer sur la branche master
- git switch master

Afficher la liste des fichiers du répertoire
- ls 
- fichier1.md  fichier2.md

Pourquoi les deux sorties sont-elles différentes ? Les fichiers ont-ils disparus ?
- car les fichiers créer dans fonctionnalité ne sont pas afficher dans master 

Créer une nouvelle branche fonctionnalite2
- git branch fonctionnalite2

Cette branche ne va pas avoir toutes les données incluses dans fonctionnalite1. Pourquoi ?
- car les données incluses dans une branche sont exclusives a celle-ci.

Qu’aurait-il fallu faire si on avait souhaité démarrer la branche fonctionnalite2 en intégrant les modifications récentes de fonctionnalite1 ?
- il aurait fallu créer la fonctionnalité2 sur la fct1

Se déplacer sur la nouvelle branche fonctionnalite2
- git switch fonctionnalite2

Créer un nouveau fichier fichier5.md
- git touch fichier5.md

Faire un commit intégrant cette ajout : “Ajout fichier5.md”
- git add fichier5.md
- git commit "Ajout fichier5.md"

Entrer la commande git log --oneline --decorate --graph --all pour visualiser, sur le terminal, le graphe des commits sur toutes les branches

-$ git log --oneline --decorate --graph --all
-* ce41521 (HEAD -> fonctionnalite2) Ajout fichier5.md
-| * 3787bb2 (fonctionnalite1) Fonctionnalité 1 - terminée
-| * 838b6b9 Fonctionnalité 1 - première phase
-|/
-* 9641a22 (master) Ajout de fichier1.md et modification de fichier1.md
-* d2a8c78 Ajout de fichier1.md


Noter la « déviation » entre les deux branches, à partir de la branche master (schématisée sous forme de traits)
l’option --all permet de visualiser toutes les branches, pas seulement celle sur laquelle on est
l’option --oneline affiche les commits sur une seule ligne
l’option --graph affiche le log sous forme de graphe
(utilisez si besoin les touches haut/bas pour naviguer dans la sortie de cette commande et Q pour quitter)
Installer l’extension VS Code Git Graph et visualiser le graphe actuel des commits à l’aide de cette extension

Sur cette représentation, que représente les points ? 
- Les points représente les commits réaliser sur chaque branch

Comment voit-on sur quelle branche on est actuellement ?
grace a cette ligne : "-* ce41521 (HEAD -> fonctionnalite2) Ajout fichier5.md" c'est la branche HEAD

VALIDATION PROF04


PARTIE 3


On considère que la branche originale (master ou main) est la branche d’intégration, c’est-à-dire celle qui va contenir l’historique de toutes les modifications développées au fur et à mesure dans les branches annexes

Se déplacer sur la branche master
- git switch master

Noter le changement dans l’onglet Git Graph
On va maintenant intégrer la branche fonctionnalite1, qui est terminée, dans la branche d’intégration (ça s’appelle une fusion, ou un merge) : fusionner avec la branche fonctionnalite1
- git merge fonctionnalité1

Noter le changement dans l’onglet Git Graph. Que signifie la mention Fast-forward indiquée par la sortie de la commande ?
- la branche de fct1 rejoint la branche master lord du merge

On veut maintenant fusionner fonctionnalite2 dans la branche d’intégration (master). Effectuer cette fusion.
- git merge fonctionnalité2

Noter le changement dans l’onglet Git Graph. Que signifie la mention Merge made by the … strategy indiquée par la sortie de la commande ?
- cela veut dire que le merging a était effectué entre fct2 et master

Quelle est la différence fondamentale avec la fusion précédente ?

Créer une nouvelle branche fonctionnalite3, se déplacer dessus, et modifier le fichier fichier1.md en y ajoutant une ligne de texte. Committer : “Modification fichier1 pour fonctionnalité 3”

Comment utiliser Git Graph pour qu’il nous montre les différences entre l’ancienne version de fichier1.md et la version courante que l’on vient de committer ?
- il faut aller chercher les anciens commit plus bas dans la branch master

Repartir sur master, et modifier fichier1.md en y ajoutant aussi une ligne (différente de celle qu’on a ajoutée sur l’autre branche) ; ajouter à l’index et commit

Tenter de fusionner la branche fonctionnalite3 avec master
- $ git merge fonctionnalite3
- Auto-merging fichier1.md
- CONFLICT (content): Merge conflict in fichier1.md
- Automatic merge failed; fix conflicts and then commit the result.


Que se passe-t-il et pourquoi ?
- la fusion ne s'effcetue pas a cause des modification de fichier1.md
Lancer un git status

Que doit-on faire si on veut annuler la fusion en cours ? (ne pas lancer la commande)
On veut résoudre le conflit. Plusieurs possibilités :
- git merge --abort

Conserver uniquement les modifications faites dans fonctionnalite3
Conserver uniquement les modifications faites dans master
Conserver les deux modifications
Supprimer les deux modifications ou remanier sensiblement le fichier pour les intégrer correctement
Git nous laisse totalement la main et ne va pas essayer d’imposer l’un de ces choix pour nous, ni nous assister dans l’application automatique de l’un d’entre eux : il faut examiner le(s) fichier(s) en conflit et éditer nous-mêmes

Ouvrir le fichier en question sous VS Code

La chaîne <<<<<<<<<< marque le début du conflit
La chaîne >>>>>>>>>> marque la fin du conflit
La chaîne ========== sépare les deux versions
Éditer le fichier pour faire en sorte d’intégrer les deux modifications ; à la fin de l’édition :

Il ne doit plus y avoir de marques quelconques en dehors des ajouts fonctionnels originaux, c’est-à-dire pas de <<<<<<<<<<, ni de mentions de nom de branche, etc. : vous rendez le fichier tel qu’il doit apparaître dans le commit de fusion, avec les conflits résolus manuellement
Sauvegarder
Ajouter les modification à l’index et committer

NB : parfois, plusieurs fichiers sont en conflit ; le processus est identique, il faut juste résoudre les conflits sur tous les fichiers

NB : les conflits de fusion sont fréquents lorsqu’on travaille en collaboration (plusieurs personnes vont travailler sur le même fichier pour remplir deux fonctionnalités différentes)

Les branches créées n’ont plus de raison d’exister

Elles avaient pour but de créer une déviation afin de travailler sur des fonctionnalités individuelles, sans interférer avec le travail des autres, avant de les fusionner dans la branche d’intégration
On va vouloir nettoyer le dépôt en les supprimant
Cela ne va bien sûr pas supprimer tous les commits qui y sont associés
Attention cependant d’éviter en général de supprimer une branche qui n’a pas encore été intégrée à la branche d’intégration, sauf on souhaite vraiment abandonner le développement de cette branche
Ne pas réutiliser une branche qui a déjà été intégrée pour démarrer une nouvelle piste : toujours utiliser une nouvelle branche
Nouvelle tâche ? => nouvelle branche à partir d’un commit de la branche d’intégration (en général le plus récent)
Tâche terminée ? => fusion dans la branche d’intégration et suppression de la branche
Supprimer les trois branches fonctionnalitex (attention : on ne peut pas supprimer une branche sur laquelle on est)

VALIDATION PROF05

Partie 4 - Travailler avec un dépôt distant (remote)
Faire un fork du dépôt https://github.com/rose-line/sio1-2024-java-grpb (pas par commande Git, c’est sur l’interface GitHub)

Cloner localement votre fork (ne pas cloner le dépôt original)

Quelle est la différence entre un fork et un clonage ? 
- un fork ce n'est pas local par rapport a un clone.

Indiquer dans quelles circonstances on voudrait forker et/ou cloner un dépôt
Modifier le fichier README.md à la racine du dépôt en ajoutant une ligne quelconque

On veut maintenant envoyer cette modification vers le dépôt distant

Il faut d’abord faire un add/commit local
Puis utiliser la commande qui « pousse » les modifs sur le dépôt GitHub (push)
Vérifier directement sur GitHub que le push a bien fonctionné
Trouver la commande qui affiche le nom du ou des dépôt(s) distant(s) relié(s) avec le dépôt local : cela permet de savoir si le dépôt courant est synchronisé avec un dépôt en ligne ou non
- git remote -v


On va faire un merge en local puis push :

Créer une branche locale bugfix1, se déplacer dessus, créer un nouveau fichier ok.java à la racine du dépôt
Ajouter ok.java à l’index et faire un commit
Retourner sur master, créer le fichier ajout.java, ajouter à l’index et committer
Fusionner la branche bugfix1 dans la branche master
Afficher le log des commits ; noter les emplacements des trois branches différentes, en local et en remote
Faire un push
Refaire un affichage du log ; origin/master a bougé : que représente cette branche ?
Étudier le résultat sur GitHub, en examinant commits et branches (bouton drop-down sur la page du dépôt pour voir les branches) : qu’est-ce qui est différent de la version locale ?

Le bug est corrigé et intégré ; que doit-on faire de la branche bugfix1 maintenant ?

VALIDATION PROF06

Supposons que l’on veuille effectivement publier sur le remote une branche sur laquelle on travaille (pour sauvegarde ou pour que d’autres puissent l’utiliser)

Créer une nouvelle branche partage
Aller sur la branche
Ajouter un fichier partage.md
L’inclure dans l’index
Faire un commit
Push
Que se passe-t-il ?
Exécuter la bonne commande pour sauvegarder la branche sur le remote
Vérifier sur GitHub que la branche apparaît bien
La branche partage n’a pas été fusionnée avant le push ; on va utiliser un autre moyen offert par GitHub pour fusionner une branche en remote : la Pull Request

La Pull Request est très utilisée en collaboration : elle permet à l’intégrateur du projet d’examiner les demandes de merge au niveau du remote avant de les accepter (ou non)
Sur GitHub, cliquer sur le bouton Compare & pull request, qui apparaît directement sur la page du dépôt depuis le dernier push qui a ajouté la branche (voir ci-dessus).

À gauche, la branche d’intégration (« base », qui reçoit le merge) ; à droite, la branche à fusionner (« compare »)

On doit fusionner partage dans master
Attention, il faut bien choisir le repo de base qui est sur votre propre compte (pas le compte du dépôt d’origine que vous avez forké)
On peut ajouter d’autres informations : titre et commentaire de la pull request, et même upload de fichiers annexes, liens éventuels… Également, on peut ajouter des labels pour étiquetter la pull request et lui affecter un reviewer, qui va officiellement être en charge
Valider en cliquant sur le bouton Create pull request
La page résultante informe sur les branches source et cible, sur les commits concernés, les fichiers qui ont été modifiés…

On peut aussi y démarrer une conversation notamment entre l’émetteur de la pull request et l’intégrateur

On voit que l’intégrateur (possesseur du compte cible) peut accepter la pull request en cliquant sur le bouton Merge pull request (ou refuser en cliquant sur Close pull request).

En discutant de la pull request, on se rend compte que certaines choses devraient être modifiées

Repartir en local pour effectuer une modification sur partage.md et ajouter precision.md
Commit des deux modifs
Push
Observer la pull request : que s’est-il passé ?
Finalement, faire le merge sur la page de la pull request
Noter que l’interface nous propose alors de supprimer la branche devenue inutile ; supprimer la branche
Dans un contexte de travail en collaboration sur un même dépôt, donner un workflow (façon de travailler) possible qui va permettre à tous les intervenants de viser des ajouts à la branche d’intégration, d’en discuter, et ceci sans danger pour la branche d’intégration, avant que finalement l’intégrateur (probablement propriétaire du dépot) accepte les changements.

VALIDATION PROF07





