# TD-1: Installation de PostGIS et création d’une base de données spatiale

## 1. Téléchargement et installation de PostgreSQL

1. Je me suis rendu sur la [page de téléchargement de PostgreSQL](https://www.postgresql.org/download/) pour télécharger la dernière version compatible avec mon système d'exploitation (Linux, MacOS, Windows, BSD, Solaris).
2. J’ai suivi les instructions d'installation pour mon système d'exploitation.
3. Pendant l'installation, j’ai défini un mot de passe pour l'utilisateur **postgres** que j'ai noté pour une utilisation ultérieure.

---

## 2. Téléchargement et installation de PostGIS

1. Lors de l'installation de PostgreSQL, j’ai coché tous les composants (y compris **Stack Builder**).
2. Une fois l'installation terminée, Stack Builder s’est lancé automatiquement.
   - J’ai sélectionné la version de PostgreSQL que j’avais installée sur ma machine.
   - Je me suis assuré d’être connecté à Internet pour télécharger les outils nécessaires.
3. Dans Stack Builder, j’ai choisi PostGIS et suivi les instructions pour installer cette extension spatiale.

### Remarque :
- Le composant **PostGIS** était automatiquement sélectionné. J’ai noté qu’il était possible de cocher « Créer une base de données spatiale », mais j’ai préféré suivre les étapes avec **pgAdmin 4** comme mentionné dans ce tutoriel.

---

## 3. Création d'une base de données avec pgAdmin 4

1. J’ai lancé **pgAdmin 4**.
2. Je me suis connecté en entrant le mot de passe défini lors de l'installation de PostgreSQL.
3. Dans le menu de navigation, j’ai fait un clic droit sur **PostgreSQL > Create > Database**.
4. J’ai donné un nom à ma base de données (ex. : `spatial-db-1`) et cliqué sur **Save**.

---

## 4. Ajout de l'extension PostGIS à la base de données

1. Dans pgAdmin, j’ai accédé à ma nouvelle base de données (ex. : `spatial-db-1`).
2. J’ai fait un clic droit sur la base, puis choisi **Query Tool**.
3. Dans l'éditeur de requêtes, j’ai entré la commande suivante :

```sql
CREATE EXTENSION postgis;
