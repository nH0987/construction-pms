# Construction Project Management System

PHP/MySQL sistem za upravljanje građevinskim projektima - prati zaposlene, timove, projekte i napredak izgradnje po fazama.

##  Karakteristike

- **Upravljanje zaposlenima** - Dodavanje i praćenje radnika sa pozicijama
- **Pozicije i plate** - Definisanje uloga i dnevnih naknada
- **Projekti** - Kreiranje projekata sa budžetom, lokacijom i rokovima
- **Faze projekta** - Podjela na Layout, Floor, Roof, Windows itd.
- **Timovi** - Organizacija radnih timova za projekte
- **Praćenje napretka** - Vizuelizacija napretka po fazama sa graficima
- **Dashboard** - Pregled svih projekata, deadlines i notifikacije

## Preduslovi

- PHP 7.4 ili noviji
- MySQL 5.7+ ili MariaDB
- Web server (Apache/Nginx) ili PHP built-in server

## Brza instalacija

### Linux/Ubuntu:
```bash
# 1. Kloniraj projekat
git clone https://github.com/nH0987/construction-pms.git
cd construction-pms

# 2. Instaliraj zavisnosti
sudo apt update
sudo apt install mysql-server php php-mysql -y

# 3. Import baze (automatski kreira korisnika)
sudo mysql -u root < database/cons_db.sql

# 4. Kopiraj konfiguraciju
cp includes/db.example.php includes/db.php

# 5. Pokreni server
php -S localhost:8000
```

**Otvori browser:** `http://localhost:8000`

**Login:** `admin` / `admin`

### Windows (XAMPP):

1. Instaliraj [XAMPP](https://www.apachefriends.org/)
2. Kloniraj projekat u `C:/xampp/htdocs/`
3. Pokreni XAMPP - uključi Apache i MySQL
4. Otvori phpMyAdmin → Import `database/cons_db.sql`
5. Kopiraj `includes/db.example.php` → `includes/db.php`
6. Otvori: `http://localhost/construction-pms/`

## Default kredencijali

- **Username:** admin
- **Password:** admin

**Promijeni lozinku odmah nakon prvog logovanja!**

## Struktura projekta
```
construction-pms/
├── database/           # SQL baza
├── includes/           # Backend logika
├── pages/             # Aplikacione stranice
├── css/               # Stilovi
├── js/                # JavaScript
├── images/            # Slike
└── index.php          # Login stranica
```

## VAŽNO UPOZORENJE

**OVAJ PROJEKAT NIJE SIGURAN ZA PRODUKCIJU!**

Ovo je edukativni/demo projekat sa poznatim sigurnosnim problemima:

-  SQL Injection ranjivosti
-  Lozinke u plain textu (nisu hash-ovane)
-  Nedostaje CSRF zaštita
-  Nedovoljna validacija inputa

### Odličan za:
-  Učenje PHP i MySQL
-  Demonstraciju funkcionalnosti

### NE koristi za:
-  Produkcijske aplikacije
-  Aplikacije sa pravim korisnicima
-  Aplikacije koje čuvaju osetljive podatke

##  Troubleshooting

### "Connection failed"
Provjeri da li je MySQL pokrenut:
```bash
sudo systemctl status mysql
```

### "Table doesn't exist"
Re-import baze:
```bash
sudo mysql -u root < database/cons_db.sql
```

### "Access denied for user"
Kreiraj korisnika ponovo:
```bash
sudo mysql -u root
DROP USER IF EXISTS 'pms_user'@'localhost';
CREATE USER 'pms_user'@'localhost' IDENTIFIED BY 'PMS_2024!';
GRANT ALL PRIVILEGES ON construction_pms_db.* TO 'pms_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

##  Doprinos

Pull requests su dobrodošli! Za veće izmjene, molim otvori issue prvo.

