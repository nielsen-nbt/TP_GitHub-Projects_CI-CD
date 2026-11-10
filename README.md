## Question 1

``git init`` : Crée le dépôt Git local.

``git add`` : Prépare les fichiers pour le commit (zone d'index).

``git commit`` : Sauvegarde définitivement l'état des fichiers préparés dans l'historique.

## Question 2
Local vs Distant : Le local réside sur votre machine ; le distant est hébergé en ligne (GitHub) pour partager et sauvegarder le code.

``origin`` : Alias donné par défaut à l'URL du dépôt distant.

``git push`` : Envoie vos commits locaux vers le dépôt distant.

Option -u : Lie la branche locale à la distante pour pouvoir exécuter un simple git push ou git pull plus tard.

## Question 3
Intérêt du venv : Isole les dépendances Python du projet pour éviter les conflits avec le reste du système.

Test de division par zéro : pytest.raises s'attend à ce que l'erreur se produise. L'exception étant le comportement voulu, le test valide la condition et réussit.