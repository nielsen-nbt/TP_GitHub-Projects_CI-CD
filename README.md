# TP GitHub Actions - CI/CD
![CI](https://github.com/nielsen-nbt/TP_GitHub-Projects_CI-CD/actions/workflows/ci-cd.yml/badge.svg)


## Réponses au questionnaire

### 1. Quelle est la différence entre `git init`, `git add` et `git commit` ?

`git init` permet de créer un dépôt Git local dans le dossier du projet. `git add` prépare les fichiers à enregistrer dans le prochain commit. `git commit` enregistre définitivement ces modifications dans l’historique Git.

### 2. Quelle est la différence entre un dépôt local et un dépôt distant ?

Le dépôt local est sur notre ordinateur, tandis que le dépôt distant est hébergé en ligne, par exemple sur GitHub. Le dépôt distant permet de sauvegarder le projet et de le partager facilement.

`origin` est le nom par défaut du dépôt distant que l’on ajoute avec `git remote add origin ...`.

`git push` sert à envoyer les commits du dépôt local vers le dépôt distant.

L’option `-u` dans `git push -u origin main` permet de relier la branche locale à la branche distante, ce qui simplifie ensuite les prochains `git push` et `git pull`.

### 3. Quel est l’intérêt d’un environnement virtuel ?

Un environnement virtuel isole les dépendances Python du projet. Cela évite les conflits entre les bibliothèques du projet et celles déjà installées sur l’ordinateur.

Le test de division par zéro passe parce que l’on vérifie bien qu’une exception est levée. La fonction `divide(10, 0)` doit provoquer une erreur `ZeroDivisionError`, et `pytest.raises` confirme exactement cela.

### 4. Pourquoi le premier push sur `main` déclenche-t-il automatiquement la CI ?

Parce que le workflow est configuré pour écouter les événements de type `push` sur la branche `main`.

Le fichier GitHub Actions contient ceci :

```yaml
on:
  push:
    branches:
      - main
```

Donc, dès qu’un push est effectué sur `main`, la CI se lance automatiquement.

### 5. Pourquoi le test détecte-t-il la régression ?

Le test `test_add` vérifie que `add(2, 3)` donne bien `5`.

Si on remplace temporairement l’addition par une soustraction, le programme retourne `-1` au lieu de `5`. Le test échoue donc immédiatement, ce qui montre bien la régression.

Le journal de CI donne aussi les détails complets : la valeur attendue, la valeur obtenue, et le point précis où l’erreur s’est produite. L’icône rouge donne juste un signal visuel, mais le journal explique la cause du problème.

## Diagnostic et correction

Pendant le TP, une erreur a été introduite volontairement pour observer le comportement de la CI. La fonction `add` a été remplacée par une soustraction, puis le test a échoué. J’ai ensuite remis la bonne version :

```python
def add(a, b):
    return a + b
```

Après correction, les tests sont revenus au vert.

## Validation

Commande exécutée :

```bash
python -m pytest -v
```

Résultat obtenu :

```text
6 passed in 0.34s
```

Le projet est donc fonctionnel et la CI est validée.
