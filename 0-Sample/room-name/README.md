# 🔐 [Nom de la Room]

> **Plateforme** : [TryHackMe](https://tryhackme.com/room/SLUG)

> **Difficulté** : `Easy` / `Medium` / `Hard`

> **Catégories** : `recon` `web` `privesc`

> **Date** : JJ/MM/AAAA

> **Auteur** : [MrYXeL](https://github.com/MrYXeL)

---

## TL;DR

> Court résumé de la room en 3–4 lignes.
> Quelles vulnérabilités ont été exploitées ? Quel était le chemin vers root ?
> Exemple : *Enumération web → LFI → reverse shell → sudo misconfiguration → root.*

---

## Sommaire

- [Reconnaissance](#reconnaissance)
- [Enumération](#enumération)
- [Exploitation](#exploitation)
- [Escalade de privilèges](#escalade-de-privilèges)
- [Flags](#flags)
- [Leçons apprises](#leçons-apprises)

---

## Environnement

| Paramètre   | Valeur          |
|-------------|-----------------|
| IP cible    | `10.10.X.X`     |
| OS cible    | Linux / Windows |
| Outils      | nmap, gobuster, … |

---

## Reconnaissance

### Scan Nmap

```bash
nmap -sC -sV -oN nmap/initial.txt 10.10.X.X
```

<details>
<summary>Output Nmap</summary>

```
Colle ici l'output nmap
```

</details>

**Ports ouverts :**

| Port | Service | Version |
|------|---------|---------|
| 22   | SSH     | OpenSSH 7.6 |
| 80   | HTTP    | Apache 2.4.29 |

---

## Enumération

### Web

```bash
gobuster dir -u http://10.10.X.X -w /usr/share/wordlists/dirb/common.txt -o gobuster.txt
```

<details>
<summary>Output Gobuster</summary>

```
Colle ici l'output gobuster
```

</details>

> **Observation :** note ici ce qui a attiré ton attention (page de login, upload, commentaire HTML…)

### Autre service (ex: SMB, FTP…)

```bash
# commande utilisée
```

---

## Exploitation

### Vulnérabilité identifiée

> Décris la vulnérabilité : CVE, type (SQLi, RCE, LFI, XXE…), pourquoi elle est exploitable ici.

### Méthode

```bash
# Commandes utilisées pour l'exploitation
```

![Screenshot exploitation](screenshots/exploit.png)

> **Pourquoi ça marche :** brève explication du mécanisme pour consolider ta compréhension.

### Accès initial

```bash
# Reverse shell / accès obtenu
```

**Shell obtenu en tant que :** `www-data` / `user`

---

## Escalade de privilèges

### Enumération locale

```bash
# LinPEAS, sudo -l, find / -perm -4000, etc.
sudo -l
find / -perm -4000 2>/dev/null
```

<details>
<summary>Output LinPEAS (extrait)</summary>

```
Colle les parties pertinentes seulement
```

</details>

### Vecteur identifié

> Décris ce que tu as trouvé : binary SUID, cron job, sudo sans mot de passe, kernel exploit, mauvaise permission…

```bash
# Commandes pour exploiter le vecteur
```

![Screenshot privesc](screenshots/privesc.png)

**Shell obtenu en tant que :** `root`

---

## Flags

<details>
<summary>User flag</summary>

```
THM{xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx}
```

</details>

<details>
<summary>Root flag</summary>

```
THM{xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx}
```

</details>

---

## Leçons apprises

### Ce que j'ai appris

- Point clé 1
- Point clé 2
- Point clé 3

### Ce qui m'a bloqué

> Honnêteté sur les points de friction — très utile pour la relecture future.

### Ressources consultées

- [Titre ressource](https://lien.com)
- [HackTricks - Topic](https://book.hacktricks.xyz)

### Ce que je ferais différemment

> Optimisations ou raccourcis que tu ferais en recommençant.

---

*Write-up rédigé par [MrYXeL](https://github.com/MrYXeL)*
