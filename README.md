# Passphrasen-Generator

Offline-Tool zur Generierung sicherer, merkbarer Passwörter nach XKCD-Prinzip.

## Nutzung

1. `passphrase-generator.html` im Browser öffnen
2. Einstellungen wählen (4+ Wörter empfohlen)
3. "Generieren" klicken
4. Passphrase kopieren

## Für Mitarbeiter

```
Bitte nutzt ein Passwort, das ihr NUR für die Wawi verwendet.
Mindestens 4 Wörter + Zahl aktiviert lassen.
```

## Dateien

- `passphrase-generator.html` – Der Generator (self-contained)
- `DECISIONS.md` – Entwicklungsentscheidungen und Kontext
- `README.md` – Diese Datei

## Sicherheit

- Läuft komplett offline im Browser
- Nutzt `crypto.getRandomValues()` für echten Zufall
- 2048 deutsche Wörter = 11 Bit Entropie pro Wort
- Keine Datenübertragung, keine Cookies
