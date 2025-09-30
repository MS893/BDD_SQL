# BDD_SQL

# MOOCademy

plateforme d'apprentissage en ligne. Il y a plein de cours. Chaque cours a un titre et une description. Enfin, chaque cours a plusieurs leçons, qui ont un titre et un body.

CREATE TABLE `cours` (
`id` INTEGER PRIMARY KEY AUTOINCREMENT, 
`titre` TEXT,
`description` TEXT
);

CREATE TABLE `leçon` (
`id` INTEGER PRIMARY KEY AUTOINCREMENT, 
`id_cours` INTEGER,
`titre` TEXT,
`body` TEXT
);

SELECT * FROM leçon
JOIN cours ON leçon.id_cours = cours.id


# The Hacking Pinterest

Pinterest, tu voudrais créer un site où les utilisateurs peuvent créer des "pins". Chaque pin contient l'URL d'une image sur le net. Les utilisateurs peuvent commenter les pins, mais ne peuvent pas commenter les commentaires.

CREATE TABLE `Pinterest` (
`id` INTEGER PRIMARY KEY AUTOINCREMENT, 
`name` TEXT,
`age` INTEGER,
`specialty` TEXT
);

# The Hacking News

Message board à la Hacker News. Les utilisateurs peuvent poster des liens. Les autres utilisateurs peuvent commenter les liens soumis, ou commenter les commentaires (mais on ne peut pas aller plus loin qu'un commentaire de commentaire). Comment faire en sorte qu'un commentaire sache où dans la hiérarchie il se trouve ?

CREATE TABLE `TheHackingNews' (
  `id` INTEGER PRIMARY KEY AUTOINCREMENT, 
  `name` TEXT,
  `age` INTEGER,
  `specialty` TEXT
);

# The Hacking Class

Site d'éducation en ligne. Dans ce site il y aura des élèves qui peuvent s'inscrire à un seul cours. Un cours pourra avoir plusieurs élèves.

CREATE TABLE `TheHackingClass` (
  `id` INTEGER PRIMARY KEY AUTOINCREMENT, 
  `name` TEXT,
  `age` INTEGER,
  `specialty` TEXT
);
