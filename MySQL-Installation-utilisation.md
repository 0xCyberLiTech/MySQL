<!-- MASTER-HEADER-START -->
<div align="center">

<a href="https://0xcyberlitech.com/">
  <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/headers/header-mysql.svg" alt="ATELIER MYSQL & MARIADB // BASES SQL" width="100%" />
</a>

<p align="center">
  <a href="https://0xcyberlitech.com/"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-portal.svg" alt="Portail 0xCyberLiTech.com" width="24%" /></a>
  <a href="https://0xcyberlitech.com/soc-rd.html"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-soc-rd.svg" alt="Livre Blanc SOC Cockpit" width="24%" /></a>
  <a href="https://0xcyberlitech.com/jarvis-rd.html"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-jarvis-rd.svg" alt="Livre Blanc JARVIS IA" width="24%" /></a>
  <a href="https://github.com/0xCyberLiTech?tab=repositories"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-github.svg" alt="Catalogue des 23 Dépôts" width="24%" /></a>
</p>
<p align="center">
  <a href="README.md"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-back-readme.svg" alt="Retour au sommaire du dépôt" width="340" /></a>
</p>

<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/divider-hud.svg" alt="" width="100%" />
</div>
<!-- MASTER-HEADER-END -->

<!-- DEBIAN-TRUTH-START -->
> [!IMPORTANT]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-shield.svg" width="18" height="18" align="absmiddle" alt="" /> ** Matrice Officielle Debian — `Debian 12 (Bookworm)` · `Debian 13 (Trixie)` · `Debian 14 (Forky)`**
> - **Sources Officielles Debian.org (`mariadb`) :** `Bookworm (12)` : **`1:10.11.18-0+deb12u1`** &nbsp;·&nbsp; `Trixie (13 — Stable)` : **`1:11.8.6-0+deb13u1`** &nbsp;·&nbsp; `Forky (14 — Next-Gen)` : **`1:11.8.9+ds-2`**
> - **Références Officielles :** [Paquet Debian Trixie (`mariadb-server`)](https://packages.debian.org/trixie/mariadb-server) &nbsp;·&nbsp; [Paquet Debian Forky (`mariadb-server`)](https://packages.debian.org/forky/mariadb-server) &nbsp;·&nbsp; [Documentation Officielle Debian](https://wiki.debian.org/MySql)
> - **Note d'Ingénierie (Divergence 13 vs 14) :** Sous Debian 13 (Trixie) et Debian 14 (Forky), MariaDB est le moteur par défaut et les binaires `mysql`, `mysqldump`, `mysql_secure_installation` sont remplacés par **`mariadb`**, **`mariadb-dump`** et **`mariadb-secure-installation`**.

<details>
<summary><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> <b>Afficher les Encarts Ligne de Commande : Debian 13 (Trixie — Stable) vs Debian 14 (Forky — Next-Gen)</b></summary>

#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Profil Production Stable — Commandes pour `Debian 13 (Trixie)`
```bash
# Debian 13 (Trixie — MariaDB 11.4+ LTS natif) : Authentification unix_socket sans mot de passe root reseau
sudo apt update && sudo apt install -y mariadb-server
sudo mariadb -e 'SELECT VERSION();' && sudo systemctl status mariadb
```

#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-rd.svg" width="46" height="16" align="absmiddle" alt="[R&D]" /> Profil Anticipation Next-Gen — Commandes pour `Debian 14 (Forky)`
```bash
# Debian 14 (Forky) — Utilitaires natifs mariadb-* (les alias mysql* historiques sont deprecies) :
sudo mariadb-secure-installation
sudo mariadb-dump --all-databases > backup.sql
```

</details>
<!-- DEBIAN-TRUTH-END -->

<!-- CIEL-PEDAGOGY-START -->
<details>
<summary><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> <b>Synthèse d'Architecture, Standards Officiels &amp; Diagnostic (Niveau 1 : Fondamentaux · Niveau 2 : Repères · Niveau 3 : Diagnostic)</b></summary>

- **Niveau 1 — Fondamentaux &amp; Principe d'Architecture :** **MariaDB / MySQL** est un Système de Gestion de Base de Données Relationnelle (**SGBDR**) transactionnel reposant sur le moteur de stockage **InnoDB**, garantissant l'intégrité des données critiques pour les applications Web et les plateformes de supervision.
- **Niveau 2 — Repères Officiels (Ports IANA, Fichiers Debian &amp; Commandes de Validation) :** **Port IANA :** `TCP 3306` (écoutant par défaut sur `127.0.0.1`) &nbsp;|&nbsp; **Fichiers Debian :** `/etc/mysql/mariadb.conf.d/50-server.cnf`, `/var/log/mysql/error.log` &nbsp;|&nbsp; **Validation officielle :** `sudo mariadb-admin ping`.
- **Niveau 3 — Diagnostic d'Incidents &amp; Ingénierie Avancée :** **Diagnostic & Architecture :** Sous Debian 12, 13 et 14, l'accès d'administration local `root` utilise l'authentification noyau sans mot de passe réseau **`unix_socket`**. Appliquez le principe du moindre privilège en créant un utilisateur SQL dédié par application (`GRANT ALL PRIVILEGES ON db.* TO 'app'@'localhost'`) et conservez le moteur **InnoDB** (support ACID, verrouillage par ligne et récupération sur crash).
- **Sources de Vérité Officielles Éditeurs &amp; Standards :** [Documentation Officielle MariaDB Server](https://mariadb.com/kb/en/documentation/) &nbsp;·&nbsp; [Paquet Officiel Debian MariaDB](https://packages.debian.org/trixie/mariadb-server)
- **Livres Blancs &amp; 67 Podcasts Audio R&amp;D :** [Portail 0xCyberLiTech](https://0xcyberlitech.com/) &nbsp;·&nbsp; [Livre Blanc SOC Cockpit v5.5](https://0xcyberlitech.com/soc-rd.html) &nbsp;·&nbsp; [Livre Blanc JARVIS Mark-VII](https://0xcyberlitech.com/jarvis-rd.html) &nbsp;·&nbsp; [Blueprint Logiciel &amp; Matériel RTX 5080](https://0xcyberlitech.com/blueprint-jarvis.html)

</details>
<!-- CIEL-PEDAGOGY-END -->


# <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Installation & utilisation de MariaDB
## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> Objectif du tutoriel
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

Installer, configurer et manipuler MariaDB sur Debian 12 (Bookworm), Debian 13 (Trixie) & Debian 14 (Forky) ou 13 avec une approche pédagogique et des exemples concrets :
>
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Installation 
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Création de base de données 
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Gestion des utilisateurs et privilèges 
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Requêtes de base (SHOW, CREATE, INSERT…) 
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Export / Import d'une base de données 
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Sécurisation du serveur MariaDB

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> 1. Installation de MariaDB
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Mise à jour du système

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> sudo apt update && sudo apt upgrade -y
> ```
<!-- CODE-WINDOW-END -->

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Installation du serveur MariaDB

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> sudo apt install mariadb-server -y
> ```
<!-- CODE-WINDOW-END -->

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Lancement et activation du service MariaDB

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> sudo systemctl start mariadb
> sudo systemctl enable mariadb
> ```
<!-- CODE-WINDOW-END -->

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Sécurisation du serveur

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> sudo mysql_secure_installation
> ```
<!-- CODE-WINDOW-END -->

<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-crypto.svg" width="18" height="18" align="absmiddle" alt="" /> **Questions typiques** :
- Définir un mot de passe root : **Oui**
- Supprimer les utilisateurs anonymes : **Oui**
- Interdire l’accès root depuis l’extérieur : **Oui**
- Supprimer la base test : **Oui**
- Recharger les tables de privilèges : **Oui**

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-crypto.svg" width="18" height="18" align="absmiddle" alt="" /> 2. Connexion à MariaDB
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> sudo mariadb -u root -p
> ```
<!-- CODE-WINDOW-END -->

> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> Si aucun mot de passe n’a été défini, omettez `-p`.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 3. Commandes de base
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```sql
> -- Afficher les bases de données existantes
> SHOW DATABASES;
>
> -- Sélectionner une base de données
> USE nom_de_la_base;
>
> -- Afficher les tables de la base
> SHOW TABLES;
>
> -- Voir la structure d'une table
> DESCRIBE nom_de_la_table;
>
> -- Créer une base de données si elle n'existe pas
> CREATE DATABASE IF NOT EXISTS cyberlogs;
>
> -- Supprimer une base
> DROP DATABASE nom_de_la_base;
>
> -- Créer une table si elle n'existe pas
> CREATE TABLE IF NOT EXISTS logs (
>     id INT AUTO_INCREMENT PRIMARY KEY,
>     message TEXT
> );
>
> -- Supprimer une table
> DROP TABLE nom_de_la_table;
>
> -- Lister les utilisateurs
> SELECT User, Host FROM mysql.user;
>
> -- Afficher les privilèges d’un utilisateur
> SHOW GRANTS FOR 'analyste'@'localhost';
>
> -- Afficher la base en cours
> SELECT DATABASE();
> ```
<!-- CODE-WINDOW-END -->

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 4. Création d’une base de données & d’un utilisateur
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```sql
> CREATE DATABASE cyberlogs;
> CREATE USER 'analyste'@'localhost' IDENTIFIED BY 'CyberPass123!';
> GRANT ALL PRIVILEGES ON cyberlogs.* TO 'analyste'@'localhost';
> FLUSH PRIVILEGES;
> ```
<!-- CODE-WINDOW-END -->

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 5. Création d’une table & insertion de données
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```sql
> USE cyberlogs;
>
> CREATE TABLE connexions (
>     id INT AUTO_INCREMENT PRIMARY KEY,
>     adresse_ip VARCHAR(45),
>     timestamp DATETIME,
>     statut VARCHAR(20)
> );
>
> INSERT INTO connexions (adresse_ip, timestamp, statut)
> VALUES 
> ('192.168.1.10', NOW(), 'autorisé'),
> ('10.0.0.5', NOW(), 'refusé');
>
> -- Modifier une table
> ALTER TABLE connexions ADD navigateur VARCHAR(100);
> ALTER TABLE connexions MODIFY statut VARCHAR(30);
> ALTER TABLE connexions DROP navigateur;
>
> -- Supprimer toutes les données (sans supprimer la table)
> TRUNCATE TABLE connexions;
>
> -- Mise à jour
> UPDATE connexions SET statut = 'autorisé' WHERE adresse_ip = '10.0.0.5';
>
> -- Suppression de lignes
> DELETE FROM connexions WHERE adresse_ip = '10.0.0.5';
> ```
<!-- CODE-WINDOW-END -->

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Interroger les données

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> SELECT * FROM connexions;
> SELECT * FROM connexions WHERE statut = 'refusé';
> ```
<!-- CODE-WINDOW-END -->

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-crypto.svg" width="18" height="18" align="absmiddle" alt="" /> 6. Gestion des privilèges
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```sql
> -- Révoquer les privilèges
> REVOKE ALL PRIVILEGES ON cyberlogs.* FROM 'analyste'@'localhost';
> DROP USER 'analyste'@'localhost';
>
> -- Donner des privilèges spécifiques
> GRANT SELECT, INSERT ON cyberlogs.connexions TO 'lecteur'@'localhost';
>
> -- Révoquer un privilège spécifique
> REVOKE INSERT ON cyberlogs.connexions FROM 'lecteur'@'localhost';
>
> -- Supprimer un utilisateur
> DROP USER IF EXISTS 'lecteur'@'localhost';
>
> -- Modifier un mot de passe
> ALTER USER 'analyste'@'localhost' IDENTIFIED BY 'NouveauPass123!';
>
> -- Voir tous les utilisateurs
> SELECT User, Host FROM mysql.user;
>
> -- Voir les privilèges d’un utilisateur
> SHOW GRANTS FOR 'analyste'@'localhost';
> ```
<!-- CODE-WINDOW-END -->

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 7. Export d'une base de données
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> # Export d'une base
> mysqldump -u root -p cyberlogs > cyberlogs_backup.sql
>
> # Export structure uniquement
> mysqldump -u root -p --no-data cyberlogs > cyberlogs_structure.sql
>
> # Export d'une table spécifique
> mysqldump -u root -p cyberlogs connexions > connexions_backup.sql
>
> # Export de toutes les bases
> mysqldump -u root -p --all-databases > all_databases_backup.sql
> ```
<!-- CODE-WINDOW-END -->

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 8. Import d’une base de données
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```sql
> # Créer la base si nécessaire
> mysql -u root -p -e "CREATE DATABASE IF NOT EXISTS cyberlogs;"
>
> # Import d'un dump
> mysql -u root -p cyberlogs < cyberlogs_backup.sql
>
> # Import global
> mysql -u root -p < all_databases_backup.sql
> ```
<!-- CODE-WINDOW-END -->

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 9. Supprimer une base ou une table
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```sql
> DROP DATABASE cyberlogs;
> DROP DATABASE IF EXISTS cyberlogs;
>
> DROP TABLE connexions;
> DROP TABLE IF EXISTS connexions;
> ```
<!-- CODE-WINDOW-END -->

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-shield.svg" width="18" height="18" align="absmiddle" alt="" /> 10. Sécurisation avancée de MariaDB
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```sql
> -- Supprimer les utilisateurs anonymes
> DELETE FROM mysql.user WHERE User='';
> FLUSH PRIVILEGES;
>
> -- Restreindre root à localhost
> UPDATE mysql.user SET Host='localhost' WHERE User='root';
> FLUSH PRIVILEGES;
>
> -- Créer un utilisateur dédié
> CREATE USER 'webapp'@'localhost' IDENTIFIED BY 'PasswordSecur3!';
> GRANT SELECT, INSERT, UPDATE, DELETE ON cyberlogs.* TO 'webapp'@'localhost';
> FLUSH PRIVILEGES;
> ```
<!-- CODE-WINDOW-END -->

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> Fichier de configuration

Dans `/etc/mysql/mariadb.conf.d/50-server.cnf` :

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```ini
> bind-address = 127.0.0.1
>
> [mysqld]
> general_log = 1
> general_log_file = /var/log/mysql/general.log
> ```
<!-- CODE-WINDOW-END -->

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> # Fichiers et permissions
> sudo chown -R mysql:mysql /var/lib/mysql
> sudo chmod -R 750 /var/lib/mysql
>
> # Journalisation
> sudo touch /var/log/mysql/general.log
> sudo chown mysql:mysql /var/log/mysql/general.log
> sudo systemctl restart mariadb
> ```
<!-- CODE-WINDOW-END -->

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-threat.svg" width="18" height="18" align="absmiddle" alt="" /> Pare-feu

<!-- CODE-WINDOW-START -->
> [!CAUTION]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-code-red.svg" width="100%" alt="TERMINAL // BLOC DE CODE" />
>
> ```bash
> sudo ufw allow OpenSSH
> sudo ufw enable
> sudo ufw deny 3306
> ```
<!-- CODE-WINDOW-END -->

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-brain.svg" width="18" height="18" align="absmiddle" alt="" /> À retenir
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- MariaDB est une solution robuste, libre, bien adaptée à LAMP.
- Toujours sécuriser les accès, limiter les privilèges, et surveiller l’activité.
- Ne jamais exposer MariaDB sur Internet sans tunnel sécurisé (VPN, SSH).

---

<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> **Ressources utiles** :
- [Documentation MariaDB](https://mariadb.com/kb/en/)
- [Commandes SQL](https://mariadb.com/kb/en/sql-statements/)

<!-- MASTER-FOOTER-START -->
<div align="center">
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/divider-hud.svg" alt="" width="100%" />

<a href="https://0xcyberlitech.com/">
  <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/footer-master.svg" alt="0xCyberLiTech — Architecture Cyberdéfense, Ingénierie Déterministe & IA Souveraine" width="100%" />
</a>

<p align="center"><a href="https://0xcyberlitech.com/"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/badge-antigravity.svg" alt="Architecturé par Marc & Antigravity (Google DeepMind)" width="520" /></a></p>

<sub><b>Architecturé &amp; Forgé par Marc &amp; Antigravity (Google DeepMind)</b> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/"><b>0xcyberlitech.com</b></a> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/soc-rd.html">Architecture SOC Cockpit v5.5</a> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/jarvis-rd.html">Architecture JARVIS Mark-VII</a> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/blueprint-jarvis.html">Blueprint Matériel RTX 5080</a></sub>

</div>
<!-- MASTER-FOOTER-END -->
