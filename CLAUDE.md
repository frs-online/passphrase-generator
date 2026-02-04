# CLAUDE.md

## Projektübersicht

Dies ist ein Passphrasen-Generator für einen kleinen Handelsbetrieb (15 MA) zur Absicherung ihrer JTL-Wawi.

## Wichtiger Kontext

- **Kein Passwort-Manager verfügbar** – daher muss das Tool standalone funktionieren
- **JTL-Wawi hat keine 2FA** – Passwörter müssen stark sein
- **Teams-Integration gewünscht** – aber JS läuft dort nicht, daher lokale Nutzung
- **Zielgruppe: Nicht-technische Mitarbeiter** – muss einfach sein

## Design-Entscheidungen

1. **2048 Wörter** statt 1024 → 11 Bit/Wort → 4 Wörter + Zahl > 50 Bit
2. **Trennzeichen nur DE/US-tippbare** → kein @, ~, |, \
3. **00-99 statt 10-99** → führende Null für mehr Entropie
4. **Clipboard-Fallback** → für restriktive Browser (Teams)

## Bei Änderungen beachten

- Wortliste muss exakt 2048 Einträge haben (für 11 Bit)
- Entropie-Berechnung in `calculateEntropy()` anpassen wenn Optionen ändern
- Keine externen JS-Dependencies (muss offline funktionieren)
- Google Fonts sind optional, nicht kritisch

## Bekannte Limitierungen

- Funktioniert nicht im Teams-Datei-Viewer (kein JS)
- Clipboard API braucht HTTPS oder localhost in manchen Browsern

## Offene Tasks

Siehe DECISIONS.md → "Offene Punkte"
