# Entwicklungsentscheidungen: Passphrasen-Generator

## Kontext & Ziel

**Auftraggeber:** Kleiner Handelsbetrieb für Sicherheitstechnik (15 Mitarbeiter)
**Anwendungsfall:** Sichere Passwörter für JTL-Wawi (ERP-System, Client-Server, kein Browser)
**Problem:** JTL hat keine 2FA/Passkeys, daher müssen Passwörter stark sein

## Warum XKCD-Style Passphrasen?

### Vorteile
- Merkbar ohne Passwort-Manager (Manager kann aktuell nicht eingesetzt werden)
- Länge schlägt Komplexität bei Brute-Force
- Einfach zu tippen, weniger Tippfehler

### Bekannte Kritik an XKCD-Passphrasen
1. **Dictionary Attacks** – Angreifer wissen, dass Passphrasen aus Wortlisten kommen
2. **Merkbarkeit überschätzt** – 5 zufällige Wörter sind schwerer zu merken als gedacht
3. **Länge ≠ Stärke** – Entropie hängt von Wortlistengröße ab, nicht Zeichenanzahl

**Fazit:** Trotzdem solide für den Anwendungsfall, wenn echte Zufälligkeit verwendet wird.

## Technische Entscheidungen

### Wortliste: 2048 Wörter (11 Bit/Wort)

| Listengröße | Bit/Wort | 4 Wörter + Zahl |
|-------------|----------|-----------------|
| 1024        | 10       | ~47 Bit         |
| **2048**    | **11**   | **~51 Bit** ✓   |

**Entscheidung:** 2048 Wörter, um mit 4 Wörtern + Zahl über 50 Bit zu kommen.

### Zahlenbereich: 00-99 (nicht 10-99)

- 00-99 = 100 Möglichkeiten = 6.6 Bit
- 10-99 = 90 Möglichkeiten = 6.5 Bit
- Führende Null erhöht Entropie minimal, sieht aber "zufälliger" aus

### Trennzeichen: 13 Optionen (3.7 Bit)

Ausgewählt nach Tippbarkeit auf DE/US-Tastaturen:
```
- . _ , / + * # ! = : ; [Leerzeichen]
```

**Bewusst weggelassen:** `@ ~ | \ [ ] { }` (brauchen AltGr auf deutschen Tastaturen)

### Entropie-Berechnung

| Komponente           | Bit   |
|----------------------|-------|
| 4 Wörter (2048)      | 44    |
| Zahl (00-99)         | 6.6   |
| Trennzeichen (13)    | 3.7   |
| **Gesamt**           | **~55** |

**Ziel erreicht:** >50 Bit mit Default-Einstellungen

## Warum kein externer Dienst (useapassphrase.com etc.)?

- Trust in fremden Code unnötig
- Kompromittierung der Seite = alle generierten Passwörter betroffen
- Für Firmenkontext: Lieber lokal/offline

## Clipboard-Problem in Teams

**Problem:** Teams-Datei-Viewer führt kein JavaScript aus.

**Implementierte Fallbacks:**
1. Moderne Clipboard API
2. execCommand (legacy)
3. Prompt-Dialog zum manuellen Kopieren

**Lösung für Teams:** Datei herunterladen und lokal im Browser öffnen.

## Sicherheitshinweise für Mitarbeiter

Empfohlene Kommunikation:
> "Die Wawi hat keine 2FA. Deshalb: Passphrase mit Generator erstellen, 
> mindestens 4 Wörter + Zahl. Nirgendwo sonst verwenden."

## Offene Punkte / Verbesserungen

- [ ] Hosting auf internem Server oder GitHub Pages für einfacheres Teilen
- [ ] VPN-Pflicht für Wawi-Zugang prüfen (wichtiger als Passwort-Policy)
- [ ] SQL-Server Login-Auditing aktivieren
- [ ] Brute-Force-Sperre am SQL-Server prüfen

## Technische Details

- **Zufallsgenerator:** `crypto.getRandomValues()` (kryptografisch sicher)
- **Keine externen Abhängigkeiten:** Komplett self-contained HTML
- **Fonts:** Google Fonts (JetBrains Mono, Space Grotesk) – optional, funktioniert auch offline
