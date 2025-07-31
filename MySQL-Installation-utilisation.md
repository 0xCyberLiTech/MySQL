



# 🐬 Tutoriel complet – MariaDB sur Debian 12 & 13

## 🎯 Objectif

Installer, configurer et manipuler MariaDB sur Debian 12 ou 13 avec une approche pédagogique et des exemples concrets :  
✔️ Installation  
✔️ Création de base de données  
✔️ Gestion des utilisateurs et privilèges  
✔️ Requêtes de base (SHOW, CREATE, INSERT…)  
✔️ Export / Import d'une base de données

---

## 🔧 1. Installation de MariaDB

### ✅ Mise à jour du système

```bash
sudo apt update && sudo apt upgrade -y
```

### ✅ Installation du serveur MariaDB

```bash
sudo apt install mariadb-server -y
```

### ✅ Lancement et activation du service MariaDB

```bash
sudo systemctl start mariadb
sudo systemctl enable mariadb
```

### ✅ Sécurisation du serveur

```bash
sudo mysql_secure_installation
```

🔐 **Questions typiques** :
- Définir un mot de passe root : **Oui**
- Supprimer les utilisateurs anonymes : **Oui**
- Interdire l’accès root depuis l’extérieur : **Oui**
- Supprimer la base test : **Oui**
- Recharger les tables de privilèges : **Oui**

---

## 🔑 2. Connexion à MariaDB

```bash
sudo mariadb -u root -p
```

> 💡 Si aucun mot de passe n’a été défini, omettez `-p`.

---

## 🗃️ 3. Commandes de base

```sql
-- Afficher les bases de données existantes
SHOW DATABASES;

-- Sélectionner une base de données
USE nom_de_la_base;

-- Afficher les tables de la base
SHOW TABLES;

-- Voir la structure d'une table
DESCRIBE nom_de_la_table;
```

---

## 🧪 4. Création d’une base de données & d’un utilisateur

### ✅ Exemple concret : une base nommée `cyberlogs`

```sql
-- Créer une base
CREATE DATABASE cyberlogs;

-- Créer un utilisateur avec mot de passe
CREATE USER 'analyste'@'localhost' IDENTIFIED BY 'CyberPass123!';

-- Donner les droits à cet utilisateur
GRANT ALL PRIVILEGES ON cyberlogs.* TO 'analyste'@'localhost';

-- Appliquer les changements
FLUSH PRIVILEGES;
```

---

## ✏️ 5. Création d’une table & insertion de données

```sql
USE cyberlogs;

CREATE TABLE connexions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    adresse_ip VARCHAR(45),
    timestamp DATETIME,
    statut VARCHAR(20)
);

INSERT INTO connexions (adresse_ip, timestamp, statut)
VALUES 
('192.168.1.10', NOW(), 'autorisé'),
('10.0.0.5', NOW(), 'refusé');
```

### 🔍 Interroger les données

```sql
SELECT * FROM connexions;

SELECT * FROM connexions WHERE statut = 'refusé';
```

---

## 🔒 6. Gestion des privilèges (bons réflexes sécurité)

### 🔐 Révocation d'accès

```sql
REVOKE ALL PRIVILEGES ON cyberlogs.* FROM 'analyste'@'localhost';
DROP USER 'analyste'@'localhost';
```

### 👀 Voir les utilisateurs

```sql
SELECT User, Host FROM mysql.user;
```

---

## 📤 7. Export d'une base de données

Sauvegarder la base `cyberlogs` dans un fichier `.sql` :

```bash
mysqldump -u root -p cyberlogs > cyberlogs_backup.sql
```

---

## 📥 8. Import d’une base de données

Importer une base à partir d’un fichier `.sql` :

```bash
mysql -u root -p cyberlogs < cyberlogs_backup.sql
```

---

## 🧼 9. Supprimer une base ou une table

```sql
DROP DATABASE cyberlogs;
DROP TABLE connexions;
```

---

## 🧠 À retenir

- ✅ MariaDB est une solution robuste, libre, et bien intégrée dans les systèmes Linux.
- ✅ La gestion des privilèges est essentielle pour la sécurité.
- ✅ Utiliser des exports réguliers (`mysqldump`) est une bonne pratique de sauvegarde.
- ✅ Mieux vaut créer un utilisateur spécifique à chaque application ou service.

---

📚 **Ressources utiles** :
- Documentation officielle : [https://mariadb.com/kb/en/](https://mariadb.com/kb/en/)
- Commandes SQL : [https://mariadb.com/kb/en/sql-statements/](https://mariadb.com/kb/en/sql-statements/)

---

✍️ Auteur : [0xCyberLiTech](https://github.com/0xCyberLiTech)  
📅 Version : Debian 12 & 13 — MariaDB dernière version stable














