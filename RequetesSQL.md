# Requêtes SQL sur la base de données Chinook

[image](assets/chinook.jpg)

> **Consignes importantes** : Chaque requête doit être autonome et ne doit pas s'appuyer sur les résultats d'une requête précédente.

---

### 1. Récupérer tous les albums

```sql
SELECT * FROM albums;
```

### 2. Récupérer tous les albums dont le titre contient "Great"

```sql
SELECT *
FROM albums
WHERE Title LIKE "%Great%";
```

### 3. Donner le nombre total d'albums

```sql
SELECT COUNT(*)
FROM albums;
```

### 4. Supprimer tous les albums dont le nom contient "music"

```sql
DELETE FROM albums
WHERE Title LIKE "%music%";
```

### 5. Récupérer tous les albums écrits par AC/DC

```sql
SELECT albums.*
FROM albums
JOIN artists ON albums.ArtistId = artists.ArtistId
WHERE artists.Name = "AC/DC";
```

### 6. Récupérer tous les titres des albums de AC/DC

```sql
SELECT albums.Title
FROM albums
JOIN artists ON albums.ArtistId = artists.ArtistId
WHERE artists.Name = "AC/DC";
```

### 7. Récupérer la liste des titres de l'album "Let There Be Rock"

```sql
SELECT tracks.Name
FROM tracks
JOIN albums ON tracks.AlbumId = albums.AlbumId
WHERE albums.Title = "Let There Be Rock";
```

### 8. Afficher le prix et la durée totale de l'album "Let There Be Rock"

```sql
SELECT
  SUM(tracks.UnitPrice) AS "Prix Total",
  SUM(tracks.Milliseconds) / 60000 AS "Durée (minutes)"
FROM tracks
JOIN albums ON tracks.AlbumId = albums.AlbumId
WHERE albums.Title = "Let There Be Rock";
```

### 9. Afficher le coût de l'intégralité de la discographie de "Deep Purple"

```sql
SELECT SUM(tracks.UnitPrice) AS "Coût Total Discographie"
FROM artists
JOIN albums ON artists.ArtistId = albums.ArtistId
JOIN tracks ON albums.AlbumId = tracks.AlbumId
WHERE artists.Name = "Deep Purple";
```

### 10. Créer un nouvel album

L'ajout d'un album complet nécessite plusieurs étapes pour renseigner correctement les différentes tables (`artists`, `albums`, `tracks`). La fonction `LAST_INSERT_ROWID()` est utilisée pour récupérer l'ID de la dernière ligne insérée et le réutiliser comme clé étrangère.

```sql
INSERT INTO artists (Name)
VALUES ('Pink Floyd');

-- LAST_INSERT_ROWID() renvoie l'ID du dernier artiste créé
INSERT INTO albums (Title, ArtistId)
VALUES ('The Dark Side Of The Moon', LAST_INSERT_ROWID());

-- Je ne rentre que la première chanson de l'album
INSERT INTO tracks (Name, AlbumId, MediaTypeId, GenreId, Composer, Milliseconds, Bytes, UnitPrice)
VALUES ('Speak to Me', LAST_INSERT_ROWID(), 1, 1, 'Roger Waters', 67000, 2200000, 0.99);
```
