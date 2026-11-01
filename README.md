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
> [!TIP]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> **Guide de Lecture &amp; Progression par Niveau (MySQL)**
> - **Rôle de la brique :** **MariaDB / MySQL** est un Système de Gestion de Base de Données Relationnelle (**SGBDR**) transactionnel reposant sur le moteur de stockage **InnoDB**, garantissant l'intégrité des données critiques pour les applications Web et les plateformes de supervision.
> - **Parcours recommandé :** **Niveau 1 (Fondamentaux &amp; Installation initiale)** pour déployer une base saine &rarr; **Niveau 2 (Configuration &amp; Intégration)** &rarr; **Niveau 3 (Haute Disponibilité, Durcissement &amp; Exploitation)**.

<details>
<summary><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> <b>Synthèse d'Architecture, Standards Officiels &amp; Diagnostic (Niveau 1 : Fondamentaux · Niveau 2 : Repères · Niveau 3 : Diagnostic)</b></summary>

- **Niveau 1 — Fondamentaux &amp; Principe d'Architecture :** **MariaDB / MySQL** est un Système de Gestion de Base de Données Relationnelle (**SGBDR**) transactionnel reposant sur le moteur de stockage **InnoDB**, garantissant l'intégrité des données critiques pour les applications Web et les plateformes de supervision.
- **Niveau 2 — Repères Officiels (Ports IANA, Fichiers Debian &amp; Commandes de Validation) :** **Port IANA :** `TCP 3306` (écoutant par défaut sur `127.0.0.1`) &nbsp;|&nbsp; **Fichiers Debian :** `/etc/mysql/mariadb.conf.d/50-server.cnf`, `/var/log/mysql/error.log` &nbsp;|&nbsp; **Validation officielle :** `sudo mariadb-admin ping`.
- **Niveau 3 — Diagnostic d'Incidents &amp; Ingénierie Avancée :** **Diagnostic & Architecture :** Sous Debian 12, 13 et 14, l'accès d'administration local `root` utilise l'authentification noyau sans mot de passe réseau **`unix_socket`**. Appliquez le principe du moindre privilège en créant un utilisateur SQL dédié par application (`GRANT ALL PRIVILEGES ON db.* TO 'app'@'localhost'`) et conservez le moteur **InnoDB** (support ACID, verrouillage par ligne et récupération sur crash).
- **Sources de Vérité Officielles Éditeurs &amp; Standards :** [Documentation Officielle MariaDB Server](https://mariadb.com/kb/en/documentation/) &nbsp;·&nbsp; [Paquet Officiel Debian MariaDB](https://packages.debian.org/trixie/mariadb-server)
- **Livres Blancs &amp; 67 Podcasts Audio R&amp;D :** [Portail 0xCyberLiTech](https://0xcyberlitech.com/) &nbsp;·&nbsp; [Livre Blanc SOC Cockpit v5.5](https://0xcyberlitech.com/soc-rd.html) &nbsp;·&nbsp; [Livre Blanc JARVIS Mark-VII](https://0xcyberlitech.com/jarvis-rd.html) &nbsp;·&nbsp; [Blueprint Logiciel &amp; Matériel RTX 5080](https://0xcyberlitech.com/blueprint-jarvis.html)

</details>
<!-- CIEL-PEDAGOGY-END -->


# <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-shield.svg" width="20" height="20" align="absmiddle" alt="" /> Sommaire :

| Nº  | Astuce                              | Lien vers la section                                                  |
|-----|-------------------------------------|-----------------------------------------------------------------------|
| 01  |  Installation & utilisation de MariaDB.             | [<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-explore.svg" alt="Accéder" />](https://github.com/0xCyberLiTech/MySQL/blob/main/MySQL-Installation-utilisation.md) |

# <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Qu'est-ce que MySQL / MariaDB ?

**MySQL** et **MariaDB** sont des **Systèmes de Gestion de Bases de Données Relationnelles (SGBDR)**. Ils permettent de créer, gérer, interroger et sécuriser des bases de données structurées. Très utilisés dans le développement web et les applications métier, ils reposent sur le langage **SQL (Structured Query Language)**.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Différences entre MySQL et MariaDB
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

| Caractéristique       | MySQL                           | MariaDB                          |
|-----------------------|----------------------------------|----------------------------------|
| Origine               | Oracle Corporation              | Créée par les fondateurs de MySQL |
| Licence               | Open-source + licence Oracle    | 100% open-source (GPL)           |
| Compatibilité         | Très proche                     | Compatible avec MySQL            |
| Performances          | Bonnes                          | Optimisée dans certaines requêtes|
| Mises à jour          | Oracle décide                   | Communauté ouverte               |

> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> **MariaDB est un "fork" de MySQL**, développé pour garantir la liberté, la performance et la transparence du code.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> Fonctionnalités clés
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Stockage de données relationnelles (tables, colonnes, index…)
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Support du langage SQL
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Transactions ACID
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Réplication (master/slave, Galera cluster pour MariaDB)
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Sécurité renforcée (utilisateurs, rôles, droits)
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Intégration avec les langages : PHP, Python, Java, Node.js…

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> Utilisations typiques
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- CMS (WordPress, Joomla, Drupal)
- Sites e-commerce (PrestaShop, Magento…)
- Applications web et ERP (Dolibarr, Odoo…)
- Plateformes cloud (Nextcloud, GitLab…)
- Outils de monitoring (Zabbix, GLPI…)

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> MySQL ou MariaDB : Que choisir ?
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-crypto.svg" width="18" height="18" align="absmiddle" alt="" /> **MySQL** : Choix pertinent si vous travaillez déjà dans un écosystème Oracle ou sur des solutions commerciales intégrées.
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> **MariaDB** : Recommandé pour les projets **open-source**, communautaires, souverains ou personnels, avec des performances améliorées dans certains cas.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> Téléchargement
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-network.svg" width="18" height="18" align="absmiddle" alt="" /> [Télécharger MySQL](https://dev.mysql.com/downloads/)
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-network.svg" width="18" height="18" align="absmiddle" alt="" /> [Télécharger MariaDB](https://mariadb.org/download/)

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-brain.svg" width="18" height="18" align="absmiddle" alt="" /> À retenir
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- **MySQL** et **MariaDB** sont des piliers du monde des bases de données.
- **MariaDB** est 100 % libre, performant, soutenu par la communauté.
- Ils sont compatibles et peuvent être substitués selon vos besoins techniques et éthiques.
- L'apprentissage du **SQL** avec ces outils est une base incontournable dans les métiers IT.

---

<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Pour aller plus loin :
- [Documentation MariaDB](https://mariadb.com/kb/en/documentation/)
- [Documentation MySQL](https://dev.mysql.com/doc/)

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
