# 1.introduction :
As-tu déjà travaillé en entreprise ou sur un projet étudiant ? Si oui, tu t'es peut-être déjà retrouvé dans mon cas avec un dossier qui ressemble à ça :

     └── big_project 
      ├── big_project_01.xls
       ├── big_project_03.xls
        ├── big_project_final_féfé.xls
         ├── big_project_final.xls
          ├── big_project.xls
           └── [WIP] big_project_fin.xls

En gros, c'est souvent le bordel dans le monde des moldus du code. Ces derniers passent leur temps à créer des milliers de fichiers, juste au cas où ils auraient besoin de revenir à une version précédente.

Maintenant, imagine devoir travailler en équipe sur des dossiers de code contenant des milliers de fichiers. Créer des index_VERSIONNUMBER.html à tire-larigot n'est clairement pas la meilleure solution. L'idéal serait d'avoir un logiciel capable de faire des photographies à un instant T d'un dossier, et de préciser pour chacune de ces sauvegardes la réponse aux 4 questions suivantes :

- **Quoi** : quels fichiers ont été modifiés dans cette photographie ?
- **Qui** : qui est responsable de cette modification ?
- **Quand** : de quand cette modification date ?
- **Pourquoi** : pourquoi cette modification existe-t-elle ?

[clique ici](https://www.git-tower.com/learn/git/ebook/en/desktop-gui/basics/what-is-version-control)

Comprends-tu maintenant pourquoi le gestionnaire de version appelé [Git](https://git-scm.com) est un super logiciel, et pourquoi c'est un indispensable dans l'univers du code ? Dans cette ressource, nous verrons comment l'installer et s'en servir. Ensuite, nous verrons de quelle manière l'utiliser pour mettre ses dossiers en ligne avec GitHub (un équivalent de DropBox) pour te permettre de partager ton code et collaborer facilement avec d'autres devs.

# **2. Contexte et historique**
Tout comme il existe plusieurs explorateurs Internet (Firefox, Chrome, Safari, etc), il existe plein de logiciels de gestion de versions ([SVN](https://subversion.apache.org), [BitKeeper](https://www.bitkeeper.org), etc). Nous allons travailler avec Git pour ce cours car c'est de très très loin le plus connu et utilisé.

Git a été créé en 2005 par Linus Torvald, qui a (entre autres) créé le système d'exploitation Linux.

[GitHub](https://github.com) est un service de mise en ligne de projets "versionnés" via Git, créé en 2008. Il a été racheté par     .Microsoft en 2018 pour la modique somme de 7,5 milliards de dollars.

En gros, voici ce que font Git et GitHub :

- **Git** est un logiciel de gestion de versions. C'est à dire, un logiciel permettant de photographier à l'instant T les fichiers d'un dossier.
- **GitHub** est un service en ligne qui utilise Git, et qui permet entre autres de :
    .Mettre en ligne ses dossiers Git (dans ce qu'on appelle "un repository").
    .Collaborer à plusieurs sur un même dossier Git.
# **3. Le cours**
## **3.1. Git**
Nous allons maintenant voir :

- Comment installer Git sur ton ordinateur.
- Comment créer un dossier Git (repository).
- Comment faire une photographie (appelé "commit").
- Comment revenir à des versions précédentes.

## **3.1.1. Installation**
Pour installer Git, rien de plus simple : va sur le site du même nom dans la rubrique [téléchargements](https://git-scm.com/downloads), choisis ton OS, puis télécharge et installe le logiciel. Redémarre ton terminal, et voilà !

🚀 **ALERTE BONNE ASTUCE**

Git est un logiciel **CLI** (Command Line Interface). Avec ce type de logiciels, tout passe par le terminal. Il s'oppose à **GUI**, Graphical User Interface.

Exemple : lorsque tu utilises la GUI de ton explorateur de fichiers, tu double-cliques sur un fichier pour l'ouvrir. Avec la CLI, tu tapes la commande $ open nom_du_fichier dans ton terminal. Autre exemple : pour créer un dossier en GUI, tu cliques droit -> nouveau dossier en GUI. En CLI, tu tapes $ mkdir nom_dossier dans ton terminal.

Bref, toutes les actions de ce cours traiteront de la CLI et passeront par le terminal avec les commandes que nous allons t'enseigner. Il existe [des versions GUI](https://git-scm.com/downloads/guis) pour Git, mais elles ne seront pas enseignées dans ce cours pour plusieurs raisons :

- Un peu comme Photoshop, la version GUI peut faire très peur avec ses milliers de boutons.
- Pas besoin d'avoir moult softwares installés : il suffit d'un terminal et à toi la gloire !
- Le but de cette semaine est de te donner les bases pour comprendre l'univers du développement. La version GUI n'étant pas utilisée par les devs, l'enseigner ne répond pas à notre vision : rendre l'univers du développement plus accessible. 
- Le but de cette semaine est de te donner les bases pour comprendre l'univers du développement. La version GUI n'étant pas utilisée par les devs, l'enseigner ne répond pas à notre vision : rendre l'univers du développement plus accessible. 

Lance (ou relance) ton terminal, puis rentre la ligne suivante :

>$ git --version

Le terminal devrait te renvoyer quelque chose comme : git version X.XX.X. S'il te renvoie un truc du genre command not found: git, c'est que tu n'as pas installé Git ou relancé ton terminal !

Pour se servir de Git, c'est simple : il suffit de rentrer dans le terminal les commandes $ git truc ou git machin pour lui faire exécuter truc ou machin. Voyons maintenant la commande permettant d'initialiser un dossier git.

## **3.1.2. Mise en place de ton dossier : git init et git status**
Avant de commencer, il faut dire au logiciel Git : "ceci est un dossier de travail correspondant à un projet. Initialise Git dans ce dossier stp". En gros, tu vas initialiser un repository Git, ce qui te permettra de faire des photographies à l'instant T. Pour ceci, mets-toi dans un dossier de travail (avec la commande cd) et exécute la commande suivante :

>$ git init
>Initialized empty Git repository in /home/felix/Desktop/my_big_project/.git/

⚠️ ALERTE ERREUR COMMUNE

Quand on débute dans le code, on a tendance à faire git init à la volée un peu partout. Il ne faut pas. Voici les types de dossiers dans lesquels tu dois initialiser des repository :

- Un dossier contenant le code de ton projet Google.
- Un dossier contenant le projet d'un site internet.
- Un dossier contenant un projet clair et défini.

Voici où **tu ne dois pas** faire git init :

- Le dossier qui contient tout ton ordinateur (exemple : exécuter git init en première ligne de commande de ton terminal).
- Ton dossier Desktop ou My Documents.
Un dossier the_hacking_project contenant tous tes projets de THP.
- Un dossier qui contiendrait plusieurs dossiers de projets différents.

En général la rule of thumbs est : un git init par projet. Si jamais tu as fait git init dans un dossier qui n'est pas bon, tu peux supprimer le dossier caché contenant toutes les informations de git en faisant :

>$ rm -rf .git

Et maintenant, quelle est la commande la plus importante quand on manipule git ? Réponse : git status. Cette commande permet de te donner en un rien de temps l'état de ton projet git. Tu peux tester en entrant git status dans un repository git :

>$ git status
>On branch master

>No commits yet

>nothing to commit (create/copy files and use "git add" to track)

Le logiciel git te dit actuellement qu'il n'y a rien dans ton dossier, et donc rien à photographier ("nothing to commit"). Voyons maintenant comment faire un commit, justement.

## **3.1.3. Faire un commit**
Un commit est une photographie à un instant T d'un projet. Pour faire court, tu vas prendre certains fichiers et les ajouter à la liste de ceux que tu veux photographier (cette liste peut aussi être vide). Ensuite, tu vas faire ta photographie en faisant git commit.

3.1.3.1. Ajouter un fichier avec git add
Pour savoir quels fichiers git va prendre en photo, il faut les ajouter avec la commande git add :

$ git add nom_de_ton_fichier
Tu peux voir avec git status que ton fichier est bien ajouté.

3.1.3.2. Faire un commit avec git commit
Maintenant que tu as ajouté tes fichiers à la liste, tu as juste à les prendre en photo avec la commande git commit :

$ git commit -m "I made a change this is a comment why I did it"
[master (root-commit) cfec956] change
 n files changed, m insertions(+), x deletions(-)
 create mode 100644 blabla
Et voilà comment marche le commit !



