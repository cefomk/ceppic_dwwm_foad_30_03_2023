# FOAD jeudi 30/03/2023

## Instructions

### Git

- Créer un **dépôt** sur **Github**, ou autres service : [Gitlab](https://gitlab.com),[Bitbucket](https://bitbucket.org/) (car il n'y pas que Github dans la vie !) avec cette intitulé : `FOAD_DWWM_2202023_pseudo_compte_github`
- **Versionner** votre code **php** ci-dessous avec **git** sur votre ordinateur
- Entraîner vous à faire des **commits atomiques**
- Envoyer (**push**) votre travail sur votre **dépôt github** crée précédemment
- Cette etape est pas nécéssaire pour ceux qui m'ont déjà envoyé leur compte github : Envoyer moi par **email** votre **compte github** pour que je puisse voir votre travail

### Symfony

Tout ce qui suit sera basé sur la documentation de **Symfony** : [https://symfony.com/doc/current/index.html](https://symfony.com/doc/current/index.html).



#### Installation

Pour pouvoir travailler avec **Symfony** il faut installer **php** et **composer**.

**php** est déjà installé car on utilise [**xampp**](https://www.apachefriends.org/fr/index.html).

**composer** s'installe en suivant les instructions [https://getcomposer.org/download/](https://getcomposer.org/download/).

Installer l'utilitaire en ligne de commande CLI `symfony` en suivant les instructions : [https://symfony.com/download](https://symfony.com/download).

Vérifier que l'installation c'est bien passé en ouvrant un **terminal**(git bash,powershell,...) , la commande suivante doit vous la version de Symfony CLI : 5.5.2 au :

`symfony -V`

`Symfony CLI version 5.5.2 (c) 2021-2023 Fabien Potencier #StandWithUkraine Support Ukraine (2023-03-22T19:49:09Z - stable)`


#### Créaton d'un nouveau projet

On va utiliser la ligne de commande (**CLI**) pour installer un nouveau projet , ce n'est pas une obligation d'etre dans `htdocs` de **xammp** pour utliser **Symfony**.

Afin de voir toutes les possibilitées qu'offre la **CLI** de **Symfony** , on tapant : `symfony list`

Creation d'un nouveau projet , dans un **terminal** :

`symfony new --webapp notre_projet`

Renter dans le projet : `cd notre_projet`

Lancer le serveur interne de **Symfony** : `symfony server:start -d` ou `symfony serve -d`

Pour arreter le serveur interne de **Symfony** : `symfony server:stop`

Pour voir les logs du serveur interne de **Symfony** : `symfony server:log`

Pour sortir d'un commande qui est en cours comme les logs il faut faire la combinaison de touche `control c`

Pour connaitre l'etat du server interne à **Symfony** : ``symfony server:status`

Afin de visualiser notre projet ouvir un navigateur à l'adreese `http://localhost:8000/`

On peut aussi demander à **Symfony** de lancer notre projet dans un navigateur (definit par par défault sur votre ordinateur) pour nous : `symfony open:local`

La majeur partie du temps on va travailler dans 4 dossiers dans **Symfony** :

- `config`
- `public`
- `src`
- `templates`

#### Controller

[Docs Controller](https://symfony.com/doc/current/controller.html)

Dans un **Symfony** créer une page consiste à créer :

- une **route** (un chemein dans l'url) 
- créer un **controller** , les controllers sont implémenté sous forme de classes

On peut créer des **controller** donc des classes dans des fichiers directement dans le dossier `src/Controller/` 

**Symfony** nous facilite la vie car on peut créer des **controllers** via la **CLI** et le bundle (plugin,extensions dans le monde **Symfony**) `symfony/maker-bundle` , qui est déjà installé en effet nous avons fait une installation complete via avec le parametre lors de la création du projet `--webapp` :

`symfony console make:controller` 

Renseigner le nom de votre **controlleur** : `TestController`

**Symfony** vient de vous créer :
- `src/Controller/TestController.php` 
- `templates/test/index.html.twig`

Dans la classe **TestController** se trouve :

- un **attribut** `#[Route('/test', name: 'app_test')]` pour définir la route pour accéder à ce **controler**
- une **methode** `index()` qui renvoie une **Response** ici on renvoit vers le **template** qui se strouve `templates/test/index.html.twig` 

A l'url : `https://127.0.0.1:8000/test` nous avons bien un affichage qui correspond au **template**.

La **methode** `index()` envoie un tableau avec une variable `controller_name` qu'on recupere dans le **template** `index.html.twig``
