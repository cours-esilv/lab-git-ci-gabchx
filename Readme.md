[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/fqgCysTO)

# TP 1 : CI/CD

## Instructions

Les réponses aux questions posées dans cet énoncé doivent être soumises sous forme de fichiers nommé en fonction du numéro de la question au sein de votre repository, dans le dossier `answers`.
Chaque réponse fera l'objet d'une nouveau fichier dans votre repo.

> Les questions requérant une réponse sous forme de fichier seront taggées par l'icone suivante: ⚠️ Ces fichiers sont corrigés automatiquement par Github Autograde

> Les commits ne sont pas facultatifs. **Commitez au minimum dès que l'énoncé vous le demande**.

Le TP doit être rendu individuellement et se basera sur les réponses présentes dans les fichiers du dossier `answers`, ainsi que sur le code présent dans vos repositories personnels.

## Rappels

### Git

[Git Documentation Officielle](https://git-scm.com/docs)
Commande | Description
-- | --
`git clone` | Clone a repository on your computer
`git add` | Add files to the staging area (which will be taken into account in the next commit)
`git commit` | Create a new commit locally
`git push` | Push your local commit tree to the server (Local --> GitHub)
`git pull` | Synchronise your local tree with the remote tree (Local <-- GitHub)
`git branch` | Create a new local branch
`git merge` | Apply changes from one branch to another locally

### GitHub flow

[GitHub flow](https://docs.github.com/en/get-started/quickstart/github-flow)
![GitHub flow diagram](https://i0.wp.com/blogs.embarcadero.com/wp-content/uploads/2021/12/Github-flow-with-GitHub-actions-7803961-8145433.jpg?ssl=1)

### Pull request

![Pull request diagram](https://miro.medium.com/max/600/1*ubVyD2GaOAlSfqRNbL0Bjg.png)

### Github

- Classroom
- Issue

### Github actions

- Service SaaS - [github.com/features/actions](https://github.com/features/actions)
- Pipeline: CI vs CD
- Pipeline: Configuration as code

---

## 1 : Git

### 1.0 : Création de compte Github

Allez sur [Github](https://github.com/) et se créer un compte si ce n'est pas déjà la cas.

### 1.1 : Accepter l'assignment

Suivez le lien présent au tableau ou dans le channel de votre groupe Discord pour récupérer une copie personnelle de ce repository dans l'organisation GitHub Classroom `devops-cloud-courses`.

### 1.2 : Cloner le repository

Clonez le repo nouvellement copié sur votre ordinateur

### 1.3 : Faire un commit

Dans votre repo, éditez le fichier identity.md et remplissez le avec vos données personnelles (nom, prénom)

Committez et pushez les changements apportés au fichier

> Les commits ne sont pas facultatifs. **Commitez au minimum dès que l'énoncé vous le demande**.

> ⚠️ **ANSWER**: Create a file called `1.3` containing the commands you used to commit and push your changes.

### 1.4 : Naviguer dans les logs

Affichez les logs des commits précédents.

Bear in mind that everything has been logged since the start of the project. You can find messages, dates and also the authors of past commits.

> ⚠️ **ANSWER**: Create a file called `1.4` containing the command you used to view the logs.

### 1.5 : Ginny a disparu, j'ai peur qu'on ne la retrouve jamais !

A l'aide de la commande utilisée dans la question précédente, retrouvez la trace de **Ginny** avant qu'il ne soit trop tard !

> **Indice**: Cherchez dans la documentation de la commande précédente pour trouver des idées de commandes.

> ⚠️ **ANSWER**: Create a file called `1.5` containing **only** the command you used to track down Ginny.

### 1.6 : Listez les branches

Listez **toutes** les branches présentes dans le repository.

Est-ce que toutes les branches vous paraissents normales ? Y a t-il une branche qui retient votre attention ?
Si oui, déplacez vous dessus (checkout).

> ⚠️ **ANSWER**: Create a file called `1.6` containing the command you used to display the branches in your repo.

### 1.7 : Mergez la branche

Maintenant que vous avez fait un tour sur la branche qui a retenue votre attention, rappatriez les changements présents sur cette dernière sur votre branche principale (snape -> main). Puis, supprimez la branch `snape` localement.

> ⚠️ **ANSWER**: Create a file called `1.7.1` containing the command you used to merge the `snape` branch into the `main` branch.

> ⚠️ **ANSWER**: Create a file called `1.7.2` containing the command you used to delete the `snape` branch (after merging the changes to `main`).

### 1.8 : Créez une branche

Maintenant que vous n'avez plus qu'une branche `main` dans votre repo, créez une branche à partir de `main`. La branche à créer doit s'appeler `feature/` suivi de la première lettre de votre prénom puis du nom de famille en minuscule (pas d'espace ni d'accent dans le nom).

> Ex Albus Dumbledore --> feature/adumbledore

Then go to your newly created `feature/{name}` branch.

> ⚠️ **ANSWER**: Create a file called `1.8` containing the commands you used to create it, and move to the new branch.

### 1.9 : Ah, c'est la que tu aurais aimé suivre le dernier cours :trollface:

Répondez aux questions contenues dans le fichier `questions.md`, puis committez les changements sur la branche `feature/{nom}`.
Enfin, pushez tous vos changements présents réalisés sur toutes les branches sur votre repository GitHub.

> ⚠️ **ANSWER**: Create a file called `1.9` containing the commands you used to push all the branches to your GitHub repo.

### 1.10 : Pull request time !!

Dans l'interface web GitHub, ouvrez une pull request partant de votre branche `feature/{nom}` pointant sur la branche develop de votre repository.

> **Warning**: Pensez bien à m'ajouter (arthur) en tant que reviewer de votre pull request afin que je puisse vous corriger.

For more help on pull requests see the [official documentation](https://help.github.com/articles/about-pull-requests/)

---

#2: CI/CD with GitHub Actions
In this second part, you must use the same repo as that obtained at the end of part 1, by placing yourself on the `main` branch of your repo.

> ⚠️ **WARNING**: Each question requiring a code modification requires at least one commit and one push in your repository. The breakdown of commits is taken into account in the scoring.

> Pour réaliser l'ensemble des étapes demandées dans cette partie, vous vous placerez sur la branche `main`

Le but de cette seconde partie de TP est d'implémenter un pipeline CI (intégration continue) permettant d'automatiser:

- le téléchargement des dépendances utiles au build applicatif
- le build de l'application
- les tests de l'application et leur mise à disposition dans une UI utilisable par n'importe qui
- le package de l'application à l'aide de Docker - sans pression, je vous donne tout pour la partie Docker pour l'instant :ok_hand:

Pour cela, nous allons utiliser une solution SaaS intégrée à GitHub appelée **GitHub Actions**.

Cette solution permet notamment grâce à son système de pipeline d'implémenter les automatisations que nous voulons réaliser dans ce TP.

Les pipelines sont décrits à travers des fichiers de code YAML (pipeline as code).

For an overview of GitHub Actions features, [see the official page](https://docs.github.com/en/actions)
For more documentation on the syntax of YAML files, [see the official documentation](https://docs.github.com/en/actions/learn-github-actions/workflow-syntax-for-github-actions)

**Important**: The above documentation will be essential for the successful completion of this and subsequent tasks.

### 2.1 : Création de votre premier Pipeline - Build & Test

Dans la page d'accueil de votre repository (sur GitHub), allez dans le menu `Actions` et cliquez sur `set up a workflow yourself`.
Cela va vous afficher le fichier YAML correspondant à la Continuous Integration (CI) que vous êtes en train de créer.

Ce fichier décrit plusieurs étapes essentielles à la mise en place d'un pipeline:

- **triggers** (`on` keyword): Définit à quelles conditions seront réalisées les actions décrites dans ce pipeline
- **steps**: La description des étapes à automatiser

Vous pouvez maintenant cliquer sur le bouton `Start commit`.

> ⚠️ **WARNING**: Don't forget to add a meaningful commit message to each commit. This will help you when you come back to the project in the future.

Observe the execution of the pipeline in the GitHub Actions UI.

### 2.2 : Buildons notre application

Pour l'instant, le build ne fait pas grand chose mis à part nous afficher deux messages.
Nous allons donc modifier le pipeline pour faire en sorte de builder notre application java.

To do this, modify the `.github/workflows/main.yml` file to add the following build steps:

```yaml
# Installe java 8 sur l'agent
- name: Set up JDK 8
  uses: actions/setup-java@v2
  with:
    java-version: '8'
    distribution: 'adopt'

# Compile notre application
- name: Build with Maven
  run: mvn --batch-mode --update-snapshots package
```

Commitez vos changements et observez le build de votre application.

### 2.3 : Intégrer les résultats de tests

Si vous observez bien les logs de build, vous verrez que des tests unitaires sont exécutés.
Nous allons récupérer le rapport de test pour l'afficher dans le résultat du pipeline.

Pour cela, modifiez le fichier `.github/workflows/main.yml` pour y ajouter les étapes de build suivantes:

```yaml
# Publie les résultats de test
- name: Publish Unit Test Results
  uses: EnricoMi/publish-unit-test-result-action@v1
  if: always()
  with:
    files: target/**/*.xml
```

Start your changes and observe the build and the results of your application's unit tests.

### 2.4 : Publier l'artifact buildé

Vous allez maintenant publier l'artifact que vous avez buildé dans les étapes précédentes.
Cela vous permet de télécharger l'artifact en question mais aussi de le déployer dans des étapes ultérieures sur différents environnements.

Pour cela, modifiez le fichier `.github/workflows/main.yml` pour y ajouter les étapes de build suivantes:

```yaml
# Publie les fichiers présents dans le dossier target dans un build artifact
- name: Upload a Build Artifact
  uses: actions/upload-artifact@v2.2.4
  with:
    name: my-app-1.0
    path: target/*
```

Commit your changes and observe the build and the artifact published on the build page.

### 2.5 : Ajout du packaging

Jusqu'ici le pipeline build et test l'applicatif mais aucun package déployable n'est réalisé ou persisté.
Vous allez créer une image Docker afin de rendre notre applicatif prêt à l'emploi.

To do this, create a Dockerfile at the root of your project containing the following code:

```dockerfile
FROM maven:3.3.9-jdk-8-alpine

COPY target/my-app-1.0-SNAPSHOT.jar /root/my-app-1.0-SNAPSHOT.jar

CMD ["java", "-jar", "/root/my-app-1.0-SNAPSHOT.jar"]
```

Then modify the `.github/workflows/main.yml` file to add the following build steps:

```yaml
# Installe la commande docker sur l'agent
- name: Install Docker
  uses: docker/setup-buildx-action@v1
  id: buildx
  with:
    install: true

# Build l'image Docker
- name: Docker build
  run: |
    docker build .
```

Commit your changes one last time and observe the build of the Docker image via the logs.

### 2.6 : Mise en place de la gestion multi-branche

Pour l'instant votre pipeline ne se déclanche que sur la branche `main` (cf. trigger).

Modifiez la valeur du trigger afin de lancer le pipeline sur toutes les branches de type:

- main
- feature (commençant par le mot feature/...)

### 2.6 : Création d'une nouvelle branche

Votre pipeline est maintenant prêt à exécuter les étapes définies en son sein quelles que soient les branches qui soient créées.

Créez une branche `feature/test-build` à partir de la branch develop et constatez que le build est automatiquement appliqué sur cette branche.

### 2.6 : Conclusion

Vous pouvez maintenant créer plusieurs branches features et vous apercevoir que ces branches se verront appliquée les étapes de build, test et package.

All this configuration means that you can have a validation system that is as close as possible without wasting time on the rapid feedback you need to improve product quality.
