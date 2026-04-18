# Mara Steinbach – Website verwalten

Anleitung zum Pflegen der Website-Inhalte. Alles funktioniert ohne technische Vorkenntnisse – du brauchst nur einen Webbrowser.

**Live-Adresse:** https://ti-wa.github.io/miniature-adventure/

---

## Schnellübersicht: Was kann ich wo ändern?

| Ich möchte... | Datei |
|---|---|
| Texte auf der Startseite ändern | [`index.md`](index.md) |
| Gemälde in der Galerie verwalten | [`_data/paintings.yml`](_data/paintings.yml) |
| Ein Gemälde als verkauft markieren | [`_data/paintings.yml`](_data/paintings.yml) |
| Preis eines Gemäldes ändern | [`_data/paintings.yml`](_data/paintings.yml) |
| Bio und Ausstellungsliste ändern | [`ueber-mich.md`](ueber-mich.md) |
| Einen neuen Blog-Beitrag schreiben | Neue Datei in [`_posts/`](_posts/) anlegen |
| Blog-Einleitung ändern | [`blog.md`](blog.md) |
| Galerie-Untertitel ändern | [`galerie.md`](galerie.md) |
| Menü oben anpassen | [`_data/navigation.yml`](_data/navigation.yml) |
| Name, E-Mail, Standort ändern | [`_config.yml`](_config.yml) |

---

## Grundprinzip

Alle editierbaren Texte stehen entweder:

1. **Im oberen Block** einer Markdown-Datei – zwischen zwei `---` Linien
2. **Im Text-Körper** einer Markdown-Datei – alles nach dem zweiten `---` (z.B. Bio, Blog-Beiträge)
3. **In einer `.yml`-Datei** im Ordner `_data/` – für Strukturdaten wie Gemälde oder das Menü

Du musst **nie HTML-Code anfassen**.

---

## Wie speichere und veröffentliche ich Änderungen?

Der einfachste Weg: direkt im Browser auf GitHub.

1. Öffne https://github.com/ti-wa/miniature-adventure
2. Klicke die Datei an, die du ändern möchtest
3. Klicke das **Bleistift-Symbol** oben rechts
4. Mach deine Änderungen
5. Scrolle ganz nach unten und klicke **"Commit changes..."**
6. Schreibe eine kurze Beschreibung (z.B. *"Preis für Morgengrauen geändert"*)
7. Klicke **"Commit changes"**

Nach ca. **1 Minute** ist die Änderung online.
Status prüfen: https://github.com/ti-wa/miniature-adventure/actions (grüner Haken = fertig).

---

## Anleitungen für typische Aufgaben

### Neues Gemälde hinzufügen

**Schritt 1 – Bild hochladen:**

- Auf GitHub in den Ordner `assets/images/` navigieren
- "Add file" → "Upload files" → Bild hineinziehen → "Commit changes"
- Dateiname-Tipp: Kleinbuchstaben, Bindestriche statt Leerzeichen, keine Umlaute
  - Gut: `bluehende-wiese.jpg`
  - Schlecht: `Blühende Wiese.JPG`

**Schritt 2 – In die Galerie eintragen:**

Öffne [`_data/paintings.yml`](_data/paintings.yml) und füge **am Anfang** der Liste einen neuen Block ein:

```yaml
- title: Blühende Wiese
  year: 2026
  medium: Öl auf Leinwand
  size: 100 × 80 cm
  image: /assets/images/bluehende-wiese.jpg
  price: "2.500 €"
  sold: false
```

**Wichtig:**
- Einrückung mit **2 Leerzeichen** (keine Tabs!)
- Zwischen Einträgen eine **Leerzeile**
- Der Preis **in Anführungszeichen**: `"2.500 €"`
- Die Reihenfolge hier = die Reihenfolge in der Galerie (neueste zuoberst)

---

### Ein Gemälde als verkauft markieren

In [`_data/paintings.yml`](_data/paintings.yml) beim gewünschten Bild die `sold:`-Zeile anpassen:

```yaml
sold: true
```

Das Verkauft-Badge erscheint automatisch, der Preis wird ausgeblendet.

Rückgängig: `sold: false` → Preis wird wieder angezeigt.

---

### Preis ändern

In [`_data/paintings.yml`](_data/paintings.yml) beim Bild:

```yaml
price: "3.500 €"
```

---

### Blog-Beitrag schreiben

**Schritt 1 – Neue Datei anlegen** in [`_posts/`](_posts/). Der Dateiname muss genau diesem Muster folgen:

```
JAHR-MONAT-TAG-titel-mit-bindestrichen.md
```

Beispiel: `2026-05-12-neue-serie-beginnt.md`

**Schritt 2 – Inhalt:**

```markdown
---
layout: post
title: "Der Titel deines Beitrags"
date: 2026-05-12 10:00:00 +0200
---

Hier beginnt dein Text. Du kannst ganz normal schreiben.

Absätze werden durch Leerzeilen getrennt.

## Eine Zwischenüberschrift

Weiterer Text. Ein *kursiv* geschriebenes Wort. Ein **fettes** Wort.
```

Der Beitrag erscheint automatisch im Blog und auf der Startseite (sortiert nach Datum).

---

### Texte auf der Startseite ändern

Öffne [`index.md`](index.md). Alle Texte stehen zwischen den zwei `---` Linien.

Beispiel – Hauptüberschrift ändern:

```yaml
intro_headline: "Deine neue Überschrift"
```

Nur den Text in Anführungszeichen ändern – Feldnamen (`intro_headline:`) bleiben wie sie sind.

---

### Bio und Ausstellungen ändern

Öffne [`ueber-mich.md`](ueber-mich.md).

- **Bio-Text** steht **unterhalb** des zweiten `---` – dort einfach normalen Fließtext schreiben
- **Ausstellungen** und **Ausbildung** stehen **oberhalb** im YAML-Block

Neue Ausstellung hinzufügen (zuoberst in der Liste):

```yaml
- year: 2027
  title: '„Titel der Ausstellung"'
  venue: "Galerie, Stadt"
  note: "Einzelausstellung"
```

Achtung: Wegen der deutschen Anführungszeichen `„...”` steht der Titel in **einfachen** Anführungszeichen (`'...'`).

---

### Menü anpassen

Öffne [`_data/navigation.yml`](_data/navigation.yml).
Reihenfolge der Einträge = Reihenfolge im Menü.

---

## Bilder hochladen

Alle Bilder liegen in `assets/images/`. Upload über GitHub:

1. Ordner `assets/images/` öffnen
2. "Add file" → "Upload files"
3. Bild auswählen oder hineinziehen
4. "Commit changes"

Dann in `_data/paintings.yml` den Pfad eintragen:
```yaml
image: /assets/images/dein-bild.jpg
```

---

## Hilfe, etwas ist kaputt!

Nach dem Speichern sieht die Website falsch aus oder wird nicht aktualisiert?

1. Öffne https://github.com/ti-wa/miniature-adventure/actions
2. Wenn der letzte Eintrag ein **rotes X** hat, gab es einen Fehler beim Bauen der Seite
3. Häufigste Ursachen:
   - Einrückung mit Tabs statt Leerzeichen
   - Vergessene Anführungszeichen bei Preisen oder Titeln
   - Fehlender `-` (Bindestrich) am Anfang eines neuen Listen-Eintrags
   - Sonderzeichen aus Word/anderen Programmen (führt oft zu Fehlern – besser direkt auf GitHub tippen)

**Lösung:** Zurück in die Datei, auf "History" klicken, die vorletzte funktionierende Version auswählen, "..." → "Revert".

Oder den Entwickler fragen.

---

## Ordner-Überblick

```
├── README.md               ← Diese Anleitung
├── _config.yml             ← Site-Einstellungen (Name, E-Mail, URL)
├── index.md                ← Startseite (Texte)
├── galerie.md              ← Galerie-Seite (Überschrift)
├── blog.md                 ← Blog-Übersicht (Einleitung)
├── ueber-mich.md           ← Über-mich (Bio, CV)
├── 404.html                ← Fehlerseite
├── _data/
│   ├── paintings.yml       ← Alle Gemälde (Titel, Preis, verkauft...)
│   └── navigation.yml      ← Menü oben auf der Seite
├── _posts/                 ← Blog-Beiträge (eine Datei pro Beitrag)
├── assets/
│   ├── images/             ← Bilder hochladen
│   └── css/main.scss       ← Design (nur für Entwickler)
├── _layouts/               ← Seitengerüste (nur für Entwickler)
└── .github/workflows/      ← Auto-Deployment (nur für Entwickler)
```

---

## Für Entwickler

- **Technologie:** Jekyll 4, GitHub Pages, GitHub Actions Deployment
- **Lokales Testen:** `bundle install && bundle exec jekyll serve`
- **Layouts:** `_layouts/default.html`, `home.html`, `gallery.html`, `blog.html`, `about.html`, `post.html`, `page.html`
- **Styling:** `assets/css/main.scss` (Custom Design, CSS Variables, kein Framework)
- **Build:** `.github/workflows/jekyll.yml` baut mit `bundle exec jekyll build` auf Push zu `main`
