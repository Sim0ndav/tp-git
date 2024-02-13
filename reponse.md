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

Noter le changement dans l’onglet Git Graph. Que signifie la mention Merge made by the … strategy indiquée par la sortie de la commande ?

Quelle est la différence fondamentale avec la fusion précédente ?

Créer une nouvelle branche fonctionnalite3, se déplacer dessus, et modifier le fichier fichier1.md en y ajoutant une ligne de texte. Committer : “Modification fichier1 pour fonctionnalité 3”

Comment utiliser Git Graph pour qu’il nous montre les différences entre l’ancienne version de fichier1.md et la version courante que l’on vient de committer ?
Repartir sur master, et modifier fichier1.md en y ajoutant aussi une ligne (différente de celle qu’on a ajoutée sur l’autre branche) ; ajouter à l’index et commit

Tenter de fusionner la branche fonctionnalite3 avec master

Que se passe-t-il et pourquoi ?
Lancer un git status

Que doit-on faire si on veut annuler la fusion en cours ? (ne pas lancer la commande)
On veut résoudre le conflit. Plusieurs possibilités :

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
