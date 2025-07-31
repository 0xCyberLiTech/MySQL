<p align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="./images/mysql_logo.png" alt="Logo MySQL" width="250">
  </a>
</p>

<div align="center">

  <a href="https://github.com/0xCyberLiTech">
    <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=D14A4A&center=true&vCenter=true&width=700&lines=SERVEUR+WEB+APACHE2;VirtualHosts+•+.htaccess+•+Sécurité;Guides+et+Bonnes+Pratiques" alt="Typing SVG" />
  </a>

  <p align="center">
    <em>Installation & utilisation de MariaDB sur Debian 12 & 13.</em><br>
    <b>🌐 Web – 🔐 Sécurité – 🚀 Performance</b>
  </p>

  [![🔗 Profil GitHub](https://img.shields.io/badge/Profil-GitHub-181717?logo=github&style=flat-square)](https://github.com/0xCyberLiTech)
  [![📦 Dernière version](https://img.shields.io/github/v/release/0xCyberLiTech/Apache2?label=version&style=flat-square&color=blue)](https://github.com/0xCyberLiTech/Apache2/releases/latest)
  [![📄 CHANGELOG](https://img.shields.io/badge/📄%20Changelog-Apache2-blue?style=flat-square)](https://github.com/0xCyberLiTech/Apache2/blob/main/CHANGELOG.md)
  [![📂 Dépôts publics](https://img.shields.io/badge/Dépôts-publics-blue?style=flat-square)](https://github.com/0xCyberLiTech?tab=repositories)
  [![👥 Contributeurs](https://img.shields.io/badge/👥%20Contributeurs-cliquez%20ici-007ec6?style=flat-square)](https://github.com/0xCyberLiTech/Apache2/graphs/contributors)

</div>

---

### 👨‍💻 **À propos de moi.**

> Bienvenue dans mon **laboratoire numérique personnel** dédié à l’apprentissage et à la vulgarisation de la cybersécurité.  
> Passionné par **Linux**, la **cryptographie** et les **systèmes sécurisés**, je partage ici mes notes, expérimentations et fiches pratiques.  
>  
> Pproposer un contenu clair, structuré et accessible pour étudiants, curieux et professionnels de l’IT.  
> 🔗 [Mon GitHub principal](https://github.com/0xCyberLiTech)

<p align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim" alt="Skills" alt="Logo techno" width="300">
  </a>
</p>

---

### 🎯 **Objectif de ce dépôt.**

> Ce dépôt a pour vocation de centraliser un ensemble de notions clés concernant la pile LAMP (Linux, Apache, MySQL/MariaDB, PHP/Perl/Python). Il s’adresse aux passionnés, étudiants et professionnels souhaitant
> mieux comprendre cette architecture web open-source, apprendre à déployer et gérer des applications basées sur LAMP, et se familiariser avec les concepts et outils essentiels à son bon fonctionnement et à son
> optimisation.

---

# 🐬 Installation & utilisation de MariaDB sur Debian 12 & 13.

## 🎯 Objectif de ce dépôt

> Ce dépôt a pour vocation de centraliser un ensemble de notions clés concernant la pile **LAMP** (Linux, Apache, MySQL/MariaDB, PHP/Perl/Python).  
> Il s’adresse aux passionnés, étudiants et professionnels souhaitant mieux comprendre cette architecture web open-source, apprendre à déployer et gérer des applications basées sur LAMP, et se familiariser avec les concepts et outils essentiels à son bon fonctionnement et à son optimisation.

---

## 🎯 Objectif du tutoriel

Installer, configurer et manipuler MariaDB sur Debian 12 ou 13 avec une approche pédagogique et des exemples concrets :  
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
```

---

## 🧪 4. Création d’une base de données & d’un utilisateur

### ✅ Exemple concret : une base nommée `cyberlogs`

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
```

### 🔍 Interroger les données

```sql
SELECT * FROM connexions;
SELECT * FROM connexions WHERE statut = 'refusé';
```

---

## 🔒 6. Gestion des privilèges

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

```bash
mysqldump -u root -p cyberlogs > cyberlogs_backup.sql
```

---

## 📥 8. Import d’une base de données

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

## 🛡️ 10. Sécurisation avancée de MariaDB

### ✅ Supprimer les utilisateurs anonymes

```sql
DELETE FROM mysql.user WHERE User='';
FLUSH PRIVILEGES;
```

### ✅ Restreindre l'accès root au localhost

```sql
UPDATE mysql.user SET Host='localhost' WHERE User='root';
FLUSH PRIVILEGES;
```

### ✅ Créer des utilisateurs dédiés

```sql
CREATE USER 'webapp'@'localhost' IDENTIFIED BY 'PasswordSecur3!';
GRANT SELECT, INSERT, UPDATE, DELETE ON cyberlogs.* TO 'webapp'@'localhost';
FLUSH PRIVILEGES;
```

### ✅ Désactiver l’accès distant

Dans `/etc/mysql/mariadb.conf.d/50-server.cnf` :

```ini
bind-address = 127.0.0.1
```

```bash
sudo systemctl restart mariadb
```

### ✅ Sécuriser les fichiers système

```bash
sudo chown -R mysql:mysql /var/lib/mysql
sudo chmod -R 750 /var/lib/mysql
```

### ✅ Activer le journal général des requêtes

Dans `/etc/mysql/mariadb.conf.d/50-server.cnf` :

```ini
[mysqld]
general_log = 1
general_log_file = /var/log/mysql/general.log
```

```bash
sudo touch /var/log/mysql/general.log
sudo chown mysql:mysql /var/log/mysql/general.log
sudo systemctl restart mariadb
```

### ✅ Bloquer les connexions réseau au port 3306

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

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>
