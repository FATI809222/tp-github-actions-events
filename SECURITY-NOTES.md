# Notes de Sécurité - TP7

## Q3
Il faut épingler une version (@v4) plutôt que @main pour garantir la reproductibilité et la sécurité. @main est une branche mouvante : si le créateur de l'action met à jour son code (même malveillant), la prochaine exécution de ton workflow utilisera cette nouvelle version sans que tu ne changes rien. Épingler @v4 (ou mieux, un SHA de commit) fige le code.

## Q4
Non, le badge « créateur vérifié » ne garantit pas qu'une action est sûre. Il garantit seulement que l'identité de l'utilisateur ou de l'organisation derrière l'action a été vérifiée par GitHub. Le code source de l'action peut toujours contenir des vulnérabilités ou être compromis.

## Q5
Deux vérifications à faire avant d'utiliser une action inconnue :
1. Lire le code source de l'action (notamment le fichier action.yml et les scripts exécutés) pour vérifier qu'elle ne fait pas de requêtes réseau suspectes ou ne vole pas de secrets.
2. Vérifier la réputation de l'auteur, le nombre d'étoiles, la fréquence des mises à jour et les issues ouvertes sur le dépôt GitHub.