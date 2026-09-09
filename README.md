# Förderverein TUMO Köln – Website

Neue Website für tumo.koeln, umgesetzt als reines HTML/CSS/JS-Projekt (kein Build-Schritt nötig)
für GitHub Pages, als Ersatz für die bisherige Elementor/STRATO-Seite.

## Struktur

```
index.html         Startseite
ueber-uns.html      Über den Förderverein
angebot.html        Das TUMO-Konzept (Lernformat, 10 Lernfelder, Zielgruppen)
mitmachen.html       Spenden / Mitglied werden / Unternehmenspartner / Ehrenamt
kontakt.html         Kontakt & Standort
impressum.html       Impressum (Platzhalter – vor Go-Live ausfüllen!)
datenschutz.html     Datenschutzerklärung (Platzhalter – vor Go-Live prüfen lassen!)
css/style.css        Gesamtes Design-System
js/main.js           Mobile-Navigation, kleine Interaktionen
```

Inhalte sind zusammengefasst aus tumo.de, techandteach.de/tumo und techandteach.de/tumo-koeln.

## Vor dem Go-Live: TODOs erledigen

Im Quellcode sind mit `TODO`-Badges markierte Platzhalter enthalten – bitte vor Veröffentlichung ausfüllen:

- **impressum.html** – Vereinsname/Rechtsform, Anschrift, Vorstand, ggf. Registernummer, Kontakt
- **datenschutz.html** – an tatsächlich genutzte Tools (Formular, Zahlungsdienstleister, Analytics) anpassen
- **mitmachen.html** – Bankverbindung (IBAN/BIC), Mitgliedsbeitrag & Anmeldeweg
- **ueber-uns.html** – Namen des Vorstands, Gründungsdatum
- **kontakt.html** – Postanschrift, E-Mail, Telefon des Vereins

Am schnellsten findest du alle offenen Stellen mit:

```bash
grep -rn "TODO\|\[.*ergänzen\|\[.*Platzhalter\|\[Straße\|\[Name" --include="*.html" .
```

## Lokal ansehen

Kein Build nötig – einfach `index.html` im Browser öffnen, oder für sauberes Routing:

```bash
python3 -m http.server 8080
```

und dann `http://localhost:8080` öffnen.

## GitHub-Repository anlegen & pushen

Dieses Verzeichnis ist bereits ein lokales Git-Repository (`git init` + erster Commit).
So bringst du es auf GitHub (Account: `dattallah`, Vorschlag Repo-Name: `tumo-koeln`):

```bash
# Auf github.com: New repository → Name z. B. "tumo-koeln" → OHNE README/gitignore anlegen
git remote add origin https://github.com/dattallah/tumo-koeln.git
git branch -M main
git push -u origin main
```

## GitHub Pages aktivieren

1. Im Repo auf GitHub: **Settings → Pages**
2. Unter „Build and deployment“ → Source: **Deploy from a branch**
3. Branch: `main`, Ordner: `/ (root)` → Speichern
4. Die Seite ist danach unter `https://dattallah.github.io/tumo-koeln/` erreichbar

## Eigene Domain tumo.koeln anbinden (Umzug von STRATO)

1. In GitHub unter **Settings → Pages → Custom domain** `tumo.koeln` eintragen und speichern
   → GitHub legt automatisch die Datei `CNAME` im Repo an/aktualisiert sie (liegt hier schon vor)
2. Bei STRATO im DNS-Bereich der Domain `tumo.koeln`:
   - **A-Records** für `@` (die nackte Domain) auf die vier GitHub-Pages-IPs setzen:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - Optional **CNAME-Record** für `www` auf `dattallah.github.io.` setzen
3. Bisherige Elementor-Verweise/A-Records bei STRATO auf das alte Hosting entfernen
4. In GitHub Pages **„Enforce HTTPS“** aktivieren, sobald das Zertifikat ausgestellt wurde (kann
   nach DNS-Umstellung bis zu 24 Std. dauern)
5. Das alte STRATO-Hosting-Paket erst kündigen, wenn tumo.koeln zuverlässig über GitHub Pages läuft

## Lizenz / Rechtliches

Inhalte fassen öffentlich zugängliche Informationen von TUMO Deutschland und Tech and Teach gGmbH
zusammen. Der Förderverein TUMO Köln ist organisatorisch eigenständig; Markenzeichen Dritter
verbleiben bei den jeweiligen Inhabern.
