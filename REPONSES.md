# Réponses TP7

## Q1
actions/checkout n'a pas besoin de with car il a des paramètres par défaut qui fonctionnent pour la majorité des cas (il checkout la branche courante). setup-node a besoin de with car il faut lui préciser obligatoirement la version de Node.js à installer, sinon il ne saurait pas quoi faire.

## Q2
Le job verify ne retrouve pas report.txt sans l'artefact car chaque job s'exécute sur un runner (une machine virtuelle) différent et éphémère. Le runner du job verify est vierge et ne partage pas le disque dur de celui du job build. L'artefact sert justement à transférer des fichiers d'un runner à un autre.

## Q6
actions/checkout doit s'exécuter avant l'appel d'une action locale car l'action locale est un fichier stocké dans le dépôt. Si le dépôt n'est pas cloné sur le runner, le runner n'a pas accès au fichier action.yml et ne peut donc pas exécuter l'action.

## Q7
shell: bash est obligatoire sur les steps run d'une action composite car le runner ne sait pas quel interpréteur de commandes utiliser par défaut. Contrairement aux workflows classiques qui utilisent bash par défaut sous Linux, les actions composites exigent que l'on précise explicitement le shell.