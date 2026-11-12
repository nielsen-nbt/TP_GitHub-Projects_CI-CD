# TP GitHub Actions - CI/CD
![CI](https://github.com/nielsen-nbt/TP_GitHub-Projects_CI-CD/actions/workflows/ci-cd.yml/badge.svg)


## RÃ©ponses au questionnaire

### 1. Quelle est la diffÃ©rence entre `git init`, `git add` et `git commit` ?

`git init` permet de crÃ©er un dÃ©pÃ´t Git local dans le dossier du projet. `git add` prÃ©pare les fichiers Ã  enregistrer dans le prochain commit. `git commit` enregistre dÃ©finitivement ces modifications dans lâ€™historique Git.

### 2. Quelle est la diffÃ©rence entre un dÃ©pÃ´t local et un dÃ©pÃ´t distant ?

Le dÃ©pÃ´t local est sur notre ordinateur, tandis que le dÃ©pÃ´t distant est hÃ©bergÃ© en ligne, par exemple sur GitHub. Le dÃ©pÃ´t distant permet de sauvegarder le projet et de le partager facilement.

`origin` est le nom par dÃ©faut du dÃ©pÃ´t distant que lâ€™on ajoute avec `git remote add origin ...`.

`git push` sert Ã  envoyer les commits du dÃ©pÃ´t local vers le dÃ©pÃ´t distant.

Lâ€™option `-u` dans `git push -u origin main` permet de relier la branche locale Ã  la branche distante, ce qui simplifie ensuite les prochains `git push` et `git pull`.

### 3. Quel est lâ€™intÃ©rÃªt dâ€™un environnement virtuel ?

Un environnement virtuel isole les dÃ©pendances Python du projet. Cela Ã©vite les conflits entre les bibliothÃ¨ques du projet et celles dÃ©jÃ  installÃ©es sur lâ€™ordinateur.

Le test de division par zÃ©ro passe parce que lâ€™on vÃ©rifie bien quâ€™une exception est levÃ©e. La fonction `divide(10, 0)` doit provoquer une erreur `ZeroDivisionError`, et `pytest.raises` confirme exactement cela.

### 4. Pourquoi le premier push sur `main` dÃ©clenche-t-il automatiquement la CI ?

Parce que le workflow est configurÃ© pour Ã©couter les Ã©vÃ©nements de type `push` sur la branche `main`.

Le fichier GitHub Actions contient ceci :

```yaml
on:
  push:
    branches:
      - main
```

Donc, dÃ¨s quâ€™un push est effectuÃ© sur `main`, la CI se lance automatiquement.

### 5. Pourquoi le test dÃ©tecte-t-il la rÃ©gression ?

Le test `test_add` vÃ©rifie que `add(2, 3)` donne bien `5`.

Si on remplace temporairement lâ€™addition par une soustraction, le programme retourne `-1` au lieu de `5`. Le test Ã©choue donc immÃ©diatement, ce qui montre bien la rÃ©gression.

Le journal de CI donne aussi les dÃ©tails complets : la valeur attendue, la valeur obtenue, et le point prÃ©cis oÃ¹ lâ€™erreur sâ€™est produite. Lâ€™icÃ´ne rouge donne juste un signal visuel, mais le journal explique la cause du problÃ¨me.

## Diagnostic et correction

Pendant le TP, une erreur a Ã©tÃ© introduite volontairement pour observer le comportement de la CI. La fonction `add` a Ã©tÃ© remplacÃ©e par une soustraction, puis le test a Ã©chouÃ©. Jâ€™ai ensuite remis la bonne version :

```python
def add(a, b):
    return a + b
```

AprÃ¨s correction, les tests sont revenus au vert.

## Validation

Commande exÃ©cutÃ©e :

```bash
python -m pytest -v
```

RÃ©sultat obtenu :

```text
6 passed in 0.34s
```

Le projet est donc fonctionnel et la CI est validÃ©e.
## 8. Bilan et compte rendu

- Nom du dÃ©pÃ´t GitHub : `TP_GitHub-Projects_CI-CD`
- URL du dÃ©pÃ´t : `https://github.com/nielsen-nbt/TP_GitHub-Projects_CI-CD`
- Branche principale utilisÃ©e : `main`
- Le workflow GitHub Actions est dÃ©clenchÃ© automatiquement aprÃ¨s un `push` sur `main` ou une `pull request` vers `main`.
- Le test en Ã©chec a Ã©tÃ© `test_add`, car la fonction `add` a Ã©tÃ© remplacÃ©e temporairement par une soustraction.
- La correction a consistÃ© Ã  remettre `return a + b` dans la fonction `add`.
- Une validation locale (`python -m pytest -v`) et une CI GitHub Actions exÃ©cutent les mÃªmes tests, mais la CI sâ€™exÃ©cute dans un environnement propre et reproductible fourni par GitHub.

### Ce quâ€™il faut prendre en capture pour le rendu

- Une capture de lâ€™arborescence du dÃ©pÃ´t GitHub.
- Une capture du workflow GitHub Actions avec le contrÃ´le rouge puis le contrÃ´le vert.
- Une capture de la pull request ou du commit de correction montrant le correctif appliquÃ©.
- Une capture du rÃ©sultat des tests (`6 passed`) pour prouver la validation finale.

Lâ€™ensemble de ces Ã©lÃ©ments permet de dÃ©montrer la correction de la rÃ©gression, la validation automatique par la CI, et la mise en ligne du projet GitHub.

