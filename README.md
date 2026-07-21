# ALWA – Karriereseite

Recruiting-Landingpage für die ALWA GmbH & Co. KG (Deißlingen).
Stellen: Werkzeugbauer, Lagerist und Mitarbeiter Qualitätssicherung (m/w/d).

## Inhalt

- `index.html` – die komplette Seite (self-contained, keine Build-Schritte nötig)
- `supabase-bewerbungen.sql` – legt den Storage-Bucket für den optionalen Lebenslauf-Upload an
- `.nojekyll` – sorgt dafür, dass GitHub Pages die Dateien 1:1 ausliefert

## Bilder (Hero-Fotos)

Die Fotos gehören in einen Ordner **`bilder/`** im Repo-Root. Der Hero lädt
automatisch das passende Bild – fehlt es, bleibt ein Farbverlauf stehen (kein
kaputtes Bild). Erwartete Dateinamen:

- `bilder/hero.jpg` – allgemeines Hero-Bild (Startseite ohne Stellen-Parameter)
- `bilder/werkzeugmechaniker.jpg` – bei `?stelle=werkzeugmechaniker`
- `bilder/lagerlogistik.jpg` – bei `?stelle=lagerlogistik`
- `bilder/qualitaetssicherung.jpg` – bei `?stelle=qualitaetssicherung`

Querformat, mind. ~1600 px breit. Motiv rechts platzieren – links liegt die
Textfläche.

## Stellen-Deeplinks für die Ad

Die Anzeige kann direkt auf eine Stelle verlinken; die Seite wählt sie vor und
startet beim Erfahrungs-Schritt:

- `…/?stelle=werkzeugmechaniker`
- `…/?stelle=lagerlogistik`
- `…/?stelle=qualitaetssicherung`

## Screening & Reload-Sperre

Wer bei der Erfahrungsfrage „weder Ausbildung noch Erfahrung“ wählt, fliegt aus
dem Prozess (kein Lead an Leadtable) und kann sich – auch nach Neuladen der
Seite – nicht erneut bewerben (per `localStorage`). Nach erfolgreicher
Bewerbung erscheint bei erneutem Aufruf ein „bereits beworben“-Hinweis.

## Live schalten (GitHub Pages)

1. Repo-Settings → **Pages** → Source: **Deploy from a branch**, Branch: `main` / `/root`.
2. Nach ein paar Minuten ist die Seite unter `https://<user>.github.io/alwa-gmbh/` erreichbar
   (bzw. unter der hinterlegten Custom-Domain).

## Bewerbungen (Leadtable)

Jede abgeschlossene Bewerbung wird per Webhook an Leadtable gesendet
(Felder u. a. `stelle`, `branche`, `erfahrung`, `starttermin`, `lebenslauf`).
Der Webhook ist in `index.html` in der Variable `WEBHOOK_URL` hinterlegt.

## Lebenslauf-Upload

Der optionale Datei-Upload nutzt Supabase Storage (Bucket `bewerbungen`).
**Einmalig** `supabase-bewerbungen.sql` im Supabase-SQL-Editor ausführen –
danach landet im Leadtable-Feld `lebenslauf` ein direkt öffenbarer Link.
