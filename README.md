# ALWA – Karriereseite

Recruiting-Landingpage für die ALWA GmbH & Co. KG (Deißlingen).
Stellen: Werkzeugbauer, Lagerist und Mitarbeiter Qualitätssicherung (m/w/d).

## Inhalt

- `index.html` – die komplette Seite (self-contained, keine Build-Schritte nötig)
- `supabase-bewerbungen.sql` – legt den Storage-Bucket für den optionalen Lebenslauf-Upload an
- `.nojekyll` – sorgt dafür, dass GitHub Pages die Dateien 1:1 ausliefert

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
