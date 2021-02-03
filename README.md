2. Le projet
<hr>
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
