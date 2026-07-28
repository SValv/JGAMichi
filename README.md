# Weinwochenende – Bullshit-Bingo mit Supabase

## Dateien

- `index.html` – Spielseite
- `auswertung.html` – globale Auswertung mit Admin-Passwort
- `config.js` – Supabase-Projekt-URL und öffentlicher Key
- `supabase-setup.sql` – Datenbank, Sicherheitsregeln und Auswertungsfunktion

## 1. Supabase einrichten

1. Kostenloses Supabase-Konto und neues Projekt anlegen.
2. Im Projekt den **SQL Editor** öffnen.
3. `supabase-setup.sql` öffnen.
4. `MEIN-SICHERES-ADMIN-PASSWORT` durch ein eigenes Passwort ersetzen.
5. Das gesamte SQL ausführen.

Das Admin-Passwort steht danach nur als sicherer Hash in der Datenbank.

## 2. Website konfigurieren

In `config.js` eintragen:

- `SUPABASE_URL`: Project URL
- `SUPABASE_KEY`: Publishable Key oder älterer `anon` Key

Diese Werte findest du in Supabase unter **Project Settings → API**.

Der Publishable-/anon-Key darf in einer Browser-App stehen. Niemals einen `service_role`- oder Secret-Key dort eintragen.

## 3. Auf GitHub Pages veröffentlichen

1. Alle vier Dateien ins Root-Verzeichnis deines GitHub-Repositories laden.
2. **Settings → Pages**
3. **Deploy from a branch**
4. Branch `main`, Ordner `/ (root)`
5. Speichern

Spielseite:
`https://DEIN-NAME.github.io/DEIN-REPO/`

Auswertung:
`https://DEIN-NAME.github.io/DEIN-REPO/auswertung.html`

## Verhalten bei schlechtem Empfang

Jede Änderung wird zuerst in `localStorage` auf dem Handy gesichert. Bei Internetzugang wird sie zusätzlich an Supabase übertragen. Beim erneuten Onlinegehen versucht die Seite, alle 30 Slots erneut zu synchronisieren.

## Sicherheitshinweis

Die Teilnehmer können Daten schreiben, aber die Tabelle nicht direkt auslesen. Die globale Auswertung ist nur über die Passwortprüfung in der Datenbankfunktion zugänglich. Für ein privates JGA-Spiel ist das ein sinnvoller, einfacher Schutz; es ersetzt jedoch kein vollständiges Benutzer- und Rechtesystem.
