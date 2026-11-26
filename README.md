# Peilung – Was liegt vor mir?

Android-App zur Orientierung im Gelände. Sie nutzt GPS und Kompass des Handys und zeigt markante Punkte in deiner Blickrichtung an: Kirchen, Berge, Burgen und Schlösser, Leuchttürme, Funkmasten, Türme, Windparks sowie die nächsten Orte mit Entfernung und Richtung. Die Daten stammen aus OpenStreetMap (Overpass API).

## APK herunterladen

Bei jedem Push auf `main` baut GitHub Actions automatisch eine neue APK:

- **Releases** (rechte Seitenleiste im Repo) → neueste Version → `Peilung-1.0.X.apk`
- oder **Actions** → „APK bauen“ → letzter Lauf → Artefakt

Auf dem Handy die APK öffnen und „Installation aus unbekannten Quellen“ für den Browser bzw. Dateimanager erlauben. Neue Versionen lassen sich direkt über die alte installieren.

## Aufbau

| Pfad | Inhalt |
|---|---|
| `web/index.html` | Die eigentliche App (HTML/JS), läuft auch im Browser über https |
| `app/` | Android-Hülle (WebView), lädt `web/` als App-Inhalt |
| `.github/workflows/build-apk.yml` | Baut die APK und erstellt ein Release |

Änderungen an der App macht man in `web/index.html` – nach dem Push entsteht automatisch eine neue APK.

## Hinweis zur Signatur

Die APK wird mit einem festen Debug-Schlüssel (`app/debug.keystore`, Passwort `android`) signiert, damit Updates ohne Deinstallation möglich sind. Für eine Veröffentlichung im Play Store wäre ein eigener, geheimer Schlüssel nötig.

## Bedienung

- Handy aufrecht halten wie beim Fotografieren – das Panorama zeigt, was vor dir liegt.
- Ziel antippen → Details, Links zu OpenStreetMap/Wikipedia.
- „Kompass kalibrieren“: Wenn du ein Ziel sicher erkennst, darauf richten und kalibrieren – korrigiert Kompassabweichungen.
- Sichtfeld, Umkreis und Kategorien sind einstellbar; „Kamera“ legt die Beschriftungen über das Kamerabild.
