# Urlaubsplan

Urlaubsplanung für eine Arztpraxis: Abwesenheiten im Kalender, Urlaubskonten, Mindestbesetzung pro Team,
Schließzeiten, Schulferien und Feiertage NRW, Notizen und Excel-Export.

Läuft im Browser auf iPhone, iPad und Mac. Anmeldung mit Google. Jede Person hat ihre eigene Planung:
Wer sich anmeldet, sieht nur die eigenen Daten.

## Aufbau

| Datei | Inhalt |
| --- | --- |
| `index.html` | Die ganze App (Oberfläche und Logik) |
| `firebase-config.js` | Verbindung zum Firebase-Projekt |
| `firestore.rules` | Zugriffsregeln: jede Person nur auf ihre eigenen Daten |
| `manifest.webmanifest`, `icons/` | Damit sich die App wie eine echte App auf den Home-Bildschirm legen lässt |

Die Daten liegen in Firestore unter `urlaubsplan/{Benutzer-ID}/…`. Beim ersten Anmelden werden die Standard-Teams
und die Schulferien NRW automatisch angelegt.

## Einrichtung in Firebase (einmalig)

1. **Google-Anmeldung einschalten:** Firebase Console → *Authentication* → *Sign-in method* → *Google* aktivieren.
2. **Adresse freigeben:** *Authentication* → *Settings* → *Authorized domains* → `xplewy.github.io` hinzufügen.
3. **Datenbank anlegen:** *Firestore Database* → *Datenbank erstellen* (Standort z. B. `europe-west3`, Frankfurt).
4. **Regeln eintragen:** *Firestore Database* → *Regeln*. Den Inhalt von
   [`firestore.rules`](firestore.rules) einfügen und *Veröffentlichen*.
   Am einfachsten den ganzen Inhalt von `firestore.rules` hineinkopieren (das Projekt gehört nur dieser App).

## Veröffentlichen mit GitHub Pages

GitHub → Repository → *Settings* → *Pages* → *Source: Deploy from a branch* → Branch `main`, Ordner `/ (root)`.
Die App ist dann unter `https://xplewy.github.io/Urlaubsplanung/` erreichbar.

## Auf dem iPhone installieren

Adresse in Safari öffnen → Teilen → *Zum Home-Bildschirm*.
