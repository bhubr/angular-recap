# Récapitulatif Angular

## 1. Contexte et vocabulaire

* Angular est un **framework** : un "cadre de travail", une boîte à outils, permettant de créer des applications **front-end**, web et mobile.
* Pour rappel, la partie front-end concerne tout ce qui est visible par l'utilisateur : l'aspect de l'interface, et toutes les interactions qu'elle permet
* Angular permet de faciliter le développement d'applications complexes, dans le sens où il encourage l'adoption de principes qu'on retrouvera dans toutes les applications Angular.
* Des développeurs ayant travaillé sur d'autres projets Angular n'auront donc pas de difficulté à travailler sur un nouveau projet.
* Angular se réfère aux versions 2 et ultérieures, tandis qu'AngularJS désigne les versions antérieures (jusqu'à 1.6.x)

## 2. Principes

* Angular repose sur une "brique élémentaire" : le **composant**. Une application est formée d'une hiérarchie de composants : des "boîtes" imbriquées les unes dans les autres, et réutilisables (voir schéma ci-dessous, représentant une application de blog très simplifiée)
* Les composants peuvent transmettre des données à des composants situés "en-dessous" dans la hiérarchie
* Les données peuvent également être situées en-dehors des composants, dans des classes TypeScript prévues à cet effet : les **services**.

![Angular components](angular-components.drawio.svg)

## 3. Initialisation

### 3.1. Angular CLI

* Angular CLI est l'outil qui permet de générer une nouvelle application, de nouveaux fichiers (composants, services), de démarrer l'application, etc.
* Pré-requis : avoir installé [Node.js](https://nodejs.org), incluant l'outil de gestion de "paquets" `npm` (**Node Package Manager**), sur son poste de travail.
* Pour **installer** la "CLI" (_Command-Line Interface_) d'Angular sur un nouveau poste de travail : `npm install -g @angular/cli`
* Après cette opération, on peut lancer, de n'importe quel terminal (PowerShell, Invite de commandes, ou Git Bash) la commande : `ng`, qui fournit de nombreuses "sous-commandes"

### 3.2. Initialiser un nouveau projet

Pour initialiser un nouveau projet (nommé ici `project-name`) :

```
ng new project-name
```

La commande pose plusieurs questions :

* `? Would you like to add Angular routing? (y/N)` &rarr; répondre **Y** si vous souhaitez gérer la **navigation** (_routing_), ce qui sera souvent le cas (sauf pour des applications très simples)
* `? Which stylesheet format would you like to use?` &rarr; répondre **CSS** sauf si vous connaissez et souhaitez utiliser un "préprocesseur" CSS

Elle se termine sur l'affichage des fichiers générés (tronqué ici), et un message indiquant que les "packages" sont en cours d'installation (ce qui peut prendre du temps) :

```
CREATE angular-recap-app/README.md (1061 bytes)
CREATE angular-recap-app/.editorconfig (274 bytes)
CREATE angular-recap-app/.gitignore (620 bytes)
CREATE angular-recap-app/angular.json (3105 bytes)
CREATE angular-recap-app/package.json (1081 bytes)
...
✔ Packages installed successfully.
```

### 3.3. Démarrer l'application

Deux commandes strictement équivalentes :

```
ng serve
```

Ou :

```
npm start
```

Cette dernière est un "script" défini dans `package.json`, qui appelle `ng serve`.

**Dans tous les cas**, après un petit délai de lancement, l'application sera accessible via l'URL <http://localhost:4200>.
 
## 4. Composants

### 4.1. Création d'un nouveau composant

* Pour initialiser un nouveau composant (nommé ici `some-component`) : `ng generate component some-component --skip-tests`, qui peut être abrégé en `ng g c some-component --skip-tests`.
* `--skip-tests` évite de générer le fichier de tests (notion qui dépasse le cadre de ce cours, mais qui demeure importante dans le développement d'applications professionnelles)
* La commande précédente génère 3 fichiers :

    * un fichier `.html` : le **template**, contenant les balises HTML que le composant doit afficher
    * un fichier `.ts` : la classe TypeScript contenant la logique qui dirige le comportement du composant (parfois appelée **contrôleur**, bien que ce soit un terme un peu obsolète, issu de l'ancien AngularJS).
    * un fichier `.css` : la **feuille de style** spécifique au composant (les styles déclarés dans ce fichier n'affecteront pas d'autres composants)
* En plus de cela, elle modifie le fichier `app.module.ts` pour y référencer le composant qui vient d'être généré (indispensable pour qu'on puisse l'utiliser)

### 4.2. Anatomie d'un composant

Dans l'application `angular-recap-app`, on a lancé la commande : `ng g c blog --skip-tests`.



### 4.3. Exemple


Pour "appeler" ce composant (l'afficher) depuis le composant principal, on supprime tout le contenu de `src/app/app.component.html`, 