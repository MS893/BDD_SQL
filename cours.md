# Introduction à SQLite

Pour lancer une base de données SQLite depuis votre terminal, utilisez la commande suivante :

```bash
sqlite3 <nom_de_la_base>.sqlite
```

## Création de Table

Voici un exemple de création de table :

```sql
CREATE TABLE `doctors` (
  `id` INTEGER PRIMARY KEY AUTOINCREMENT, 
  `name` TEXT,
  `age` INTEGER,
  `specialty` TEXT
);
```

Cette commande va créer une table `doctors`, avec :
*   un `id` qui s'incrémentera automatiquement (`AUTOINCREMENT`).
*   un `name` (texte).
*   un `age` (entier).
*   une `specialty` (texte).

La **clé étrangère** (non présente dans cet exemple) est un concept qui permet de lier des tables entre elles.

## 🚀 Astuces pour l'interface SQLite

Pour améliorer l'affichage dans l'interface `sqlite3` :

*   **Améliorer la lisibilité des résultats** :
    ```sqlite
    .mode column
    .headers on
    ```
*   **Lister toutes les tables** :
    ```sqlite
    .tables
    ```
*   **Afficher les colonnes d'une table** (en affichant la première ligne) :
    ```sql
    SELECT * FROM TableName LIMIT 1;
    ```

## Opérations de base : CRUD

CRUD signifie **C**reate, **R**ead, **U**pdate, **D**elete. Ce sont les quatre opérations fondamentales pour la gestion de données.

*   **Create** : Créer une nouvelle entrée avec `INSERT`.
*   **Read** : Lire des entrées avec `SELECT`.
*   **Update** : Mettre à jour une entrée avec `UPDATE`.
*   **Delete** : Supprimer une entrée avec `DELETE`.

### Exemples

1.  **Create** (Créer) un docteur :
    ```sql
    INSERT INTO doctors (name, age, specialty) VALUES ('Dr. Dolladille', 45, 'Dentist');
    ```

2.  **Read** (Lire)
    *   Lire toutes les entrées :
        ```sql
        SELECT * FROM doctors;
        ```
    *   Lire une entrée spécifique :
        ```sql
        SELECT * FROM doctors WHERE age = 45;
        ```

3.  **Update** (Mettre à jour) un docteur :
    ```sql
    UPDATE doctors SET age = 40, name = 'John Smith' WHERE id = 3;
    ```

4.  **Delete** (Supprimer) un docteur :
    ```sql
    DELETE FROM doctors WHERE id = 3;
    ```
