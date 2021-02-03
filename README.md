# bdd_models_exo
2. Le projet
2.1. Exo 1 : Allociné

Dans cet exercice, on va te faire créer une app Rails dont la BDD contiendra des films. Dans un premier temps, tu vas créer le model et la BDD. Ensuite on va te faire manipuler tout ça avec la console. Pour finir, tu vas seeder ta BDD.

Ici on ne fait que de la manipulation pour t'habituer à jouer avec les models. Tu n'as aucun travail de conception de ta BDD car on va te donner des instructions précises.

Let's go ! 🎬
2.1.1. Mise en place du model et de la BDD

Commence par créer une application Rails. Ensuite, tu vas générer un model Movie (rappelle-toi, les noms des models sont forcément au singulier !) dont les attributs seront les suivants :

    name qui porte le nom du film et est de type string.
    year qui porte l'année de sortie et est de type integer.
    genre qui porte le type de film (horreur, action, etc.) et est de type string.
    synopsis qui porte le résumé du film et est de type text.
    director qui porte le nom du réalisateur et est de type string.
    allocine_rating qui porte le score "spectateur" visible sur allocine.fr et est de type float.
    my_rating qui porte ton score personnel sur le film et est de type integer.
    already_seen qui indique si tu as déjà vu le film et est de type boolean.

2.1.2. Jouons en console

Ok, si tu arrives ici, c'est que tu as créé le model, préparé la migration pour générer la table movies et que tu as passé la migration. C'est bien ça ?

Commence, par pure conscience professionnelle, par vérifier si la migration est bien passée avec un petit rails db:migrate:status. C'est bon, elle est bien en up ? Parfait, passons aux exercices.
a) Un premier film à la mano

On va commencer par saisir un chef d’œuvre du cinéma franco-américain : Beowulf.

Va dans la console de rails et initialise un film avec un petit film1 = Movie.new.

Maintenant tu vas saisir en console la valeur de chaque attribut de Beowulf en te référant à la page Allociné du film. Je veux que tu fasses une ligne par attribut. Par exemple pour le nom tu vas faire tout simplement :

2.5.1 :001 > film1.name = "Beowulf"

Répète l'opération pour chaque attribut. Tu peux laisser my_rating à nil si tu n'as pas vu le film.

N'oublie pas de finir l'opération par un petit film1.save pour inscrire tout ça en BDD. Voilà un premier film de saisi ! Tu peux vérifier qu'il a bien été enregistré en faisant des petits Movie.last ou Movie.all. Profites-en pour vérifier qu'aucun attribut n'a été oublié.
b) Deux films à la mano mais efficace

Bon, c'était sympa ce petit échauffement mais maintenant on va rentrer 2 films en une seule ligne de console. Je te donne les liens Allociné pour le premier et pour le second.

Tu vas les insérer chacun en BDD en écrivant une seule ligne dans ta console (via un create donc). Inspire-toi de l'exemple ci-dessous en le complétant avec tous attributs existants :

2.5.1 :00 > Movie.create(name: "xxxx", year: 1999, already_seen: false)

Vérifie à chaque fois que tu as bien réussi en faisant des Movie.last ou Movie.all.
c) Un peu de freestyle

Ta BDD est fonctionnelle, tu as déjà créé trois entrées… il est temps de lâcher les chevaux 🐎 ! Voici ce que je veux que tu fasses :

    Crée une entrée avec un film de ton choix (un film que tu as déjà vu). Je veux juste que l'ensemble des attributs soient renseignés.
    Modifie la note Allociné de Beowulf pour qu'elle soit à 4,7. Ce chef-d’œuvre mérite d'être reconnu comme tel.
    Modifie le genre de l'Exorciste pour que ça soit une comédie. Avec un peu de chance ta petite soeur va tomber dessus.
    Affiche, avec une commande en Movie.where, l'ensemble des films que tu as déjà vus.
    À partir de cet array de films que tu as déjà vus, supprime le premier de ta BDD.

Maintenant que tu as effectué toutes ces modifications en console, je veux que tu affiches le contenu de ta BDD grâce à la gem table print. Pour que ça soit moins moche, n'hésite pas à limiter le nombre de colonne affichées.
d) Le seed : aux BDD bien créées, la valeur n'attend point le nombre des années

On ne va pas se contenter de quelques films : il est temps de voir comment notre application réagirait avec une BDD bien remplie. Je vais te demander de préparer un seed de plein de Movie en respectant ces contraintes :

    Tu vas créer 100 films avec du contenu venant de Faker.
    Le nom de chaque film doit être plausible.
    L'année doit être comprise entre 1900 et 2020.
    Le genre doit être l'une des valeurs suivantes : ["action", "horreur", "comédie", "drame"]
    Chaque synopsis doit être composé d'au moins 10 mots
    Le réalisateur doit être un nom plausible.
    La note Allociné doit être aléatoire et comprise entre 0 et 5. Il ne faut pas que ça soit uniquement des entiers : on veut 1 chiffre après la virgule.
    Le already_seen doit être à false et my_rating à nil.

Tu peux supprimer, si nécessaire, les 3-4 films que tu as créés dans les questions précédentes.

Maintenant que les 100 entrées sont créées, affiche le tout en console avec table_print (ne mets pas toutes les colonnes). Balade-toi, en scrollant, dans la liste et repère 10 films que tu trouves bien funs (noms improbables, etc.). Pour chacun de ces films tu vas faire comme si tu venais de les visionner :

    Retrouve-les soit via leur id avec Movie.find ou via leur nom avec Movie.find_by(name: "xxx") puis affecte-les à une variable du genre mon_film.
    Passe alors leur already_seen en true.
    Donne leur une note dans my_rating.

Bien joué ! Tu as là une base de données qui est 1) fonctionnelle et 2) assez plausible pour servir à tester (par exemple) un allociné-like.
2.2. Exo 2 : Chinook Music

Pour cet exercice, je vais te refiler une BDD sur laquelle tu vas bosser… ce qui devrait te rappeler un exercice d'hier ! Mais plutôt que de se passer des fichiers de BDD, je vais te faire re-créer cette BDD via un seed.
2.2.1. Création des models

Crée une nouvelle application Rails. Tu vas maintenant générer un nouveau model Album dont les attributs seront les suivants :

    title qui porte le titre de l'album et est de type string.
    artist qui porte nom de l'artiste et est de type string.

Ensuite tu vas faire un second model Track avec les attributs :

    title qui porte le titre de la chanson et est de type string.
    album qui porte le titre de l'album et est de type string.
    artist qui porte le nom de l'artiste et est de type string.
    duration qui porte la durée de la chanson (en millisecondes) et est de type integer.
    size qui porte la taille (en octets) de la chanson et est de type integer.
    price qui porte le prix de la chanson et est de type float.

Pense bien à passer les migrations et n'hésite pas à tester le bon fonctionnement des 2 models en console.
2.2.2. Seed de la BDD de travail

Maintenant, tu vas coller le code suivant dans ton seeds.rb puis lancer un $ rails db:seed. Attention, je te préviens, les arrays sont très longs 😇

  album_array.each_with_index do |album, index|
    Album.create(album)
    puts "#{index} albums créés"
  end

  tracks_array.each_with_index do |track,index|
    Track.create(track)
    puts "#{index} pistes créés"
  end

2.2.3. Questions

Maintenant que ta BDD est prête, tu vas répondre aux questions ci-dessous :
a) Niveau facile

    Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?
    Qui est l'auteur de la chanson "White Room" ?
    Quelle chanson dure exactement 188133 milliseconds ?
    Quel groupe a sorti l'album "Use Your Illusion II" ?

b) Niveau Moyen

    Combien y a t'il d'albums dont le titre contient "Great" ? (indice)
    Supprime tous les albums dont le nom contient "music".
    Combien y a t'il d'albums écrits par AC/DC ?
    Combien de chanson durent exactement 158589 millisecondes ?

c) Niveau Difficile

Pour ces questions, tu vas devoir effectuer des boucles dans la console Rails. C'est peu commun mais c'est faisable, tout comme dans IRB.

    puts en console tous les titres de AC/DC.
    puts en console tous les titres de l'album "Let There Be Rock".
    Calcule le prix total de cet album ainsi que sa durée totale.
    Calcule le coût de l'intégralité de la discographie de "Deep Purple".
    Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.
=========================================================================================================
3. Rendu attendu

Deux repo Github chacun contenant une application Rails (une par exercice). Le Readme doit afficher les réponses en texte aux différentes questions qui n'impliquent pas de modifier l'app Rails (combien de... Calcule ... etc.)
=========================================================================================================

a)

1 - Il ya  347 Album dans la BDD
2 - Eric Clapton
3 - id: 40, title: "Perfect", album: "Jagged Little Pill", artist: "Alanis 				Morissette", duration: 188133, size: 6145404, price: 0.99
4 - id: 92, title: "Use Your Illusion II", artist: "Guns N Roses", created_at: "2021-02-03 				17:42:41", updated_at: "2021-02-03 17:42:41"> 

b)

1 - Album.find_by("title like ?", "%Great%")
2 - music_selected = Album.find_by("title like ?", "%music%") 
    music_selected.delete
3 - arcdc = Album.where(artist: "AC/DC")
	2.7.1 :067 > arcdc.count
	   (0.3ms)  SELECT COUNT(*) FROM "albums" WHERE "albums"."artist" = ?  [["artist", "AC/DC"]]
	 => 2
4 - search_by_duration = Track.where(duration: 158589)
	search_by_duration.count
  	 (0.3ms)  SELECT COUNT(*) FROM "tracks" WHERE "tracks"."duration" = ?  [["duration", 158589]]
 	=> 0 

c) 

1 - 
	
Track.where(artist: "AC/DC").each do |track|
puts track.title
end

2 - 

Track.where(title: "Let There Be Rock").each do |track|
puts track.title
end

  Track Load (0.3ms)  SELECT "tracks".* FROM "tracks" WHERE "tracks"."title" = ?  [["title", "Let There Be Rock"]]
Let There Be Rock
 => [#<Track id: 17, title: "Let There Be Rock", album: "Let There Be Rock", artist: "AC/DC", duration: 366654, size: 12021261, price: 0.99, created_at: "2021-02-03 17:42:43", updated_at: "2021-02-03 17:42:43">]
 
3 - 
