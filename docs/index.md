# rnek0's notes

Voici des notes dans mon parcours d'apprentissage, ceci est purement perso mais il est possible que cela se retrouve sur le net (de nos jours cela serait non pas une sextape mais des notetape :D) elles ne seront pas traduites donc parfois en français ou espagnol ou en anglais. Celui qui a un doute il a qu'à aller sur :

* [translate google](https://translate.google.fr)
* [translate deepl](https://www.deepl.com/translator)
* [Bing Microsoft Translator](https://www.bing.com/translator/)

ou d'autres outils, au choix...

Ces notes se trouvent ici : 

* [rnek0's notes - local](http://127.0.0.1:8000/) lorsque je travaille dessus.
* [rnek0's notes - online](https://rnek0.github.io/lunarDocs/) sur le web.

Les endroits ou j'apprends des choses peuvent être divers et variés.  
Cela peut être un point de depart sur ma [page de liens](https://web.lunarviews.net/enlaces/)

## Pourquoi ?

Parce que je n'ai pas un cerveau musclé comme Schwarzenegger à l'époque de Conan le Barbare...

Et bien, le sujet est toujours le même, il y en a qui préfèrent [Cherrytree](https://framalibre.org/content/cherrytree) ou bien [Obsidian](https://obsidian.md/) ou que sais je, le block notes avec l'explorateur et de la patience; oui il y a un petit dernier à tester qui est [Logsec](https://github.com/logseq/logseq), voici la [doc](https://docs.logseq.com/#/page/start%20here).  

Bref, il me faut un bon système de prise de notes et je suis en phase de test; puis pour ne rien vous cacher mes prérequis sont :

* il faut que le machin puisse générer des sites, voir des books 
* que la lecture soit disponible de partout 
* que la mise à jour se fasse facilement, donc le workflow soit simple.
* qu'on puisse customiser la chose tant qu'a faire et qu'on puisse fasse perso.
* i18n serait un plus.
* Pourquoi pas générer des pdf.

En complement peut être rechercher a faire des mindmaps, mais je verrais plus tard.

## Les tests

Voici mes choix du moment, toujours en [Markdown](https://daringfireball.net/projects/markdown/) puis génération avec [pandoc](https://pandoc.org/) ou autres apps vers quelque chose de plus structuré.

Pour les blogs ou docs en ligne :

* **Jekyll** (*Python*) avec md pour un blog simple <https://web.lunarviews.net>
* **Hugo** (*Go*) avec md pour un blog simple 
    * Mon theme (en travaux) <https://blog.lunarviews.net>
    * Avec [hugo-ficurinia](https://gitlab.com/gabmus/hugo-ficurinia) <https://rnek0.srht.site/>
* **Material for MkDocs** (*Python*) <https://rnek0.github.io/lunarDocs/>

* **Jupyter notebooks** (*Python*) (intéressant car je peux générer des pdf à la volée)
    * Tests en lisant des tutos <https://github.com/rnek0/TSbook>  

Il y a ceux-ci également, mais ce ne sont pas forcement mes choix pour une utilisation en ligne :

* [Logsec](https://framalibre.org/content/logseq) que j'ai pas encore testé.
* [Cherrytree](https://framalibre.org/content/cherrytree)
* [Obsidian](https://obsidian.md/)

Et aussi [mdBook](https://rust-lang.github.io/mdBook/) (*Rust*) que j'aimerais avoir le temps de tester car Rust est la grande mode, récemment introduite dans le kernel Linux si j'en crois mes oreilles.

## Mkdocs

C'est le générateur de documentation que vous voyez en ce moment. Si vous êtes intéressé voici une video de [James Willett](https://yewtu.be/watch?v=Q-YA_dA8C20) à ne pas manquer.  

Quelques commandes très utiles de [MkDocs](https://www.mkdocs.org/)

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

### Strucure du projet

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.

### Choisir le thème

<https://www.mkdocs.org/user-guide/choosing-your-theme/>

### Keycodes pour les shortcuts

<https://www.toptal.com/developers/keycode>