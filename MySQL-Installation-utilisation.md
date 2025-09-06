<div align="center">

  <br></br>

  <p align="center">
    <a href="https://github.com/0xCyberLiTech">
      <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=50&duration=6000&pause=1000000000&color=FF0048&center=true&vCenter=true&width=1100&lines=%3ELAMP_" alt="Titre dynamique LAMP" />
    </a>
  </p>

  <br></br>

  <h2>Laboratoire numérique pour la cybersécurité, Linux & IT.</h2>

  <p align="center">
    <a href="https://github.com/0xCyberLiTech">
      <img src="https://img.shields.io/badge/Profil-GitHub-181717?logo=github&style=flat-square" alt="Profil GitHub" />
    </a>
    <a href="https://github.com/0xCyberLiTech/Apache2/releases/latest">
      <img src="https://img.shields.io/github/v/release/0xCyberLiTech/Apache2?label=version&style=flat-square&color=blue" alt="Dernière version" />
    </a>
    <a href="https://github.com/0xCyberLiTech/Apache2/blob/main/CHANGELOG.md">
      <img src="https://img.shields.io/badge/📄%20Changelog-Apache2-blue?style=flat-square" alt="CHANGELOG" />
    </a>
    <a href="https://github.com/0xCyberLiTech?tab=repositories">
      <img src="https://img.shields.io/badge/Dépôts-publics-blue?style=flat-square" alt="Dépôts publics" />
    </a>
    <a href="https://github.com/0xCyberLiTech/Apache2/graphs/contributors">
      <img src="https://img.shields.io/badge/👥%20Contributeurs-cliquez%20ici-007ec6?style=flat-square" alt="Contributeurs" />
    </a>
  </p>

</div>

<div align="center">
  <img src="https://img.icons8.com/fluency/96/000000/cyber-security.png" alt="CyberSec" width="80"/>
</div>

<div align="center">
  <p>
    <strong>Cybersécurité</strong> <img src="https://img.icons8.com/color/24/000000/lock--v1.png"/> • <strong>Linux Debian</strong> <img src="https://img.icons8.com/color/24/000000/linux.png"/> • <strong>Sécurité informatique</strong> <img src="https://img.icons8.com/color/24/000000/shield-security.png"/>
  </p>
</div>

---

<div align="center">
  
## À propos & Objectifs.

</div>

Ce projet propose des solutions innovantes et accessibles en cybersécurité, avec une approche centrée sur la simplicité d’utilisation et l’efficacité. Il vise à accompagner les utilisateurs dans la protection de leurs données et systèmes, tout en favorisant l’apprentissage et le partage des connaissances.

Le contenu est structuré, accessible et optimisé SEO pour répondre aux besoins de :
- 🎓 Étudiants : approfondir les connaissances
- 👨‍💻 Professionnels IT : outils et pratiques
- 🖥️ Administrateurs système : sécuriser l’infrastructure
- 🛡️ Experts cybersécurité : ressources techniques
- 🚀 Passionnés du numérique : explorer les bonnes pratiques

---

# 🐬 Installation & utilisation de MariaDB
## 🎯 Objectif du tutoriel

Installer, configurer et manipuler MariaDB sur Debian 12 ou 13 avec une approche pédagogique et des exemples concrets :
>
✔️ Installation  
✔️ Création de base de données  
✔️ Gestion des utilisateurs et privilèges  
✔️ Requêtes de base (SHOW, CREATE, INSERT…)  
✔️ Export / Import d'une base de données  
✔️ Sécurisation du serveur MariaDB

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

-- Créer une base de données si elle n'existe pas
CREATE DATABASE IF NOT EXISTS cyberlogs;

-- Supprimer une base
DROP DATABASE nom_de_la_base;

-- Créer une table si elle n'existe pas
CREATE TABLE IF NOT EXISTS logs (
    id INT AUTO_INCREMENT PRIMARY KEY,
    message TEXT
);

-- Supprimer une table
DROP TABLE nom_de_la_table;

-- Lister les utilisateurs
SELECT User, Host FROM mysql.user;

-- Afficher les privilèges d’un utilisateur
SHOW GRANTS FOR 'analyste'@'localhost';

-- Afficher la base en cours
SELECT DATABASE();
```

---

## 🧪 4. Création d’une base de données & d’un utilisateur

```sql
CREATE DATABASE cyberlogs;
CREATE USER 'analyste'@'localhost' IDENTIFIED BY 'CyberPass123!';
GRANT ALL PRIVILEGES ON cyberlogs.* TO 'analyste'@'localhost';
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

-- Modifier une table
ALTER TABLE connexions ADD navigateur VARCHAR(100);
ALTER TABLE connexions MODIFY statut VARCHAR(30);
ALTER TABLE connexions DROP navigateur;

-- Supprimer toutes les données (sans supprimer la table)
TRUNCATE TABLE connexions;

-- Mise à jour
UPDATE connexions SET statut = 'autorisé' WHERE adresse_ip = '10.0.0.5';

-- Suppression de lignes
DELETE FROM connexions WHERE adresse_ip = '10.0.0.5';
```

### 🔍 Interroger les données

```sql
SELECT * FROM connexions;
SELECT * FROM connexions WHERE statut = 'refusé';
```

---

## 🔒 6. Gestion des privilèges

```sql
-- Révoquer les privilèges
REVOKE ALL PRIVILEGES ON cyberlogs.* FROM 'analyste'@'localhost';
DROP USER 'analyste'@'localhost';

-- Donner des privilèges spécifiques
GRANT SELECT, INSERT ON cyberlogs.connexions TO 'lecteur'@'localhost';

-- Révoquer un privilège spécifique
REVOKE INSERT ON cyberlogs.connexions FROM 'lecteur'@'localhost';

-- Supprimer un utilisateur
DROP USER IF EXISTS 'lecteur'@'localhost';

-- Modifier un mot de passe
ALTER USER 'analyste'@'localhost' IDENTIFIED BY 'NouveauPass123!';

-- Voir tous les utilisateurs
SELECT User, Host FROM mysql.user;

-- Voir les privilèges d’un utilisateur
SHOW GRANTS FOR 'analyste'@'localhost';
```

---

## 📤 7. Export d'une base de données

```bash
# Export d'une base
mysqldump -u root -p cyberlogs > cyberlogs_backup.sql

# Export structure uniquement
mysqldump -u root -p --no-data cyberlogs > cyberlogs_structure.sql

# Export d'une table spécifique
mysqldump -u root -p cyberlogs connexions > connexions_backup.sql

# Export de toutes les bases
mysqldump -u root -p --all-databases > all_databases_backup.sql
```

---

## 📥 8. Import d’une base de données

```bash
# Créer la base si nécessaire
mysql -u root -p -e "CREATE DATABASE IF NOT EXISTS cyberlogs;"

# Import d'un dump
mysql -u root -p cyberlogs < cyberlogs_backup.sql

# Import global
mysql -u root -p < all_databases_backup.sql
```

---

## 🧼 9. Supprimer une base ou une table

```sql
DROP DATABASE cyberlogs;
DROP DATABASE IF EXISTS cyberlogs;

DROP TABLE connexions;
DROP TABLE IF EXISTS connexions;
```

---

## 🛡️ 10. Sécurisation avancée de MariaDB

```sql
-- Supprimer les utilisateurs anonymes
DELETE FROM mysql.user WHERE User='';
FLUSH PRIVILEGES;

-- Restreindre root à localhost
UPDATE mysql.user SET Host='localhost' WHERE User='root';
FLUSH PRIVILEGES;

-- Créer un utilisateur dédié
CREATE USER 'webapp'@'localhost' IDENTIFIED BY 'PasswordSecur3!';
GRANT SELECT, INSERT, UPDATE, DELETE ON cyberlogs.* TO 'webapp'@'localhost';
FLUSH PRIVILEGES;
```

### 🔧 Fichier de configuration

Dans `/etc/mysql/mariadb.conf.d/50-server.cnf` :

```ini
bind-address = 127.0.0.1

[mysqld]
general_log = 1
general_log_file = /var/log/mysql/general.log
```

```bash
# Fichiers et permissions
sudo chown -R mysql:mysql /var/lib/mysql
sudo chmod -R 750 /var/lib/mysql

# Journalisation
sudo touch /var/log/mysql/general.log
sudo chown mysql:mysql /var/log/mysql/general.log
sudo systemctl restart mariadb
```

### 🔥 Pare-feu

```bash
sudo ufw allow OpenSSH
sudo ufw enable
sudo ufw deny 3306
```

---

## 🧠 À retenir

- MariaDB est une solution robuste, libre, bien adaptée à LAMP.
- Toujours sécuriser les accès, limiter les privilèges, et surveiller l’activité.
- Ne jamais exposer MariaDB sur Internet sans tunnel sécurisé (VPN, SSH).

---

📚 **Ressources utiles** :
- [Documentation MariaDB](https://mariadb.com/kb/en/)
- [Commandes SQL](https://mariadb.com/kb/en/sql-statements/)

---

<div align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="440">
  </a>
</div>

<div align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</div>

