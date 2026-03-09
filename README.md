# Git-Workshop für die NE

> **Dauer:** 2.5 Stunden | **Teilnehmende:** 8 | **Vorkenntnisse:** keine IT-Kenntnisse nötig

## Voraussetzungen (vor dem Workshop erledigen)

- [ ] Visual Studio Code installiert
- [ ] Git installiert
- [ ] GitHub-Account erstellt unter [github.com](https://github.com)

## Zeitplan

| Block | Dauer | Inhalt |
|-------|-------|--------|
| Theorie | ~20 min | Motivation, Git-Konzepte, GitHub |
| Setup | ~15 min | VS Code, git config, Repo klonen |
| Teil 1: Hunde-Repo | ~45 min | Commit, Push, Konflikt, Branch, Pull Request |
| *Pause* | ~10 min | |
| Teil 2: XML-Editionsdaten | ~50 min | Issues, Branches, echte Editionsarbeit |
| Abschluss | ~10 min | Fragen, Zusammenfassung, Glossar |

---

# Theorieteil

## 1. Status Quo: Unsere Editionsdaten liegen auf Netzlaufwerk

- **Gemeinsam Bearbeiten**, aber nur nacheinander
- **Wenn eine Datei bearbeitet wird**, wird die alte Version quasi gelöscht

### Probleme:

- Keine Nachvollziehbarkeit, wer wann was geändert hat
- Keine Möglichkeit, parallel zu arbeiten
- Keine Möglichkeit, Schritte rückgängig zu machen
- Keine Möglichkeit, Änderungen zu testen, ohne Schattenablagen zu machen
- Versionenchaos

## 2. Warum git?

Git löst konkret die Probleme von oben:

- **Jede Änderung wird festgehalten** — wer hat wann was geändert (wie "Track Changes" in Word, aber für alle Dateien)
- **Nichts geht verloren** — jeder frühere Zustand ist wiederherstellbar; einzelne Commits können gezielt rückgängig gemacht werden, ohne die Geschichte zu löschen
- **Parallel arbeiten** — mehrere Personen können gleichzeitig an verschiedenen Stellen arbeiten
- **Testen ohne Risiko** — Änderungen in einem geschützten Bereich ausprobieren, bevor sie "live" gehen

## 3. Wie funktioniert das Arbeiten mit Git?

Vier Begriffe reichen für den Anfang:

- **Repository (Repo)**: Ein Projektordner, der von Git überwacht wird — inklusive der gesamten Änderungshistorie
- **Commit**: Ein Snapshot — ein gespeicherter Zustand der Dateien mit einer kurzen Beschreibung ("Hundenamen ergänzt")
- **Branch**: Ein Parallelstrang — man arbeitet auf einer Kopie, ohne den Hauptstrang zu verändern
- **Push / Pull**: Änderungen hochladen (push) oder herunterladen (pull) — zwischen dem eigenen Computer und GitHub
- **Klonen**: Einmaliges Herunterladen eines Repos von GitHub auf den eigenen Computer — inklusive der gesamten Git-History und der Verknüpfung zu GitHub
- **Pull Request (PR)**: Eine Anfrage, Änderungen aus einem Branch in den Hauptstrang (`main`) zu übernehmen — eine andere Person prüft die Änderungen, bevor sie "live" gehen

### Der typische Ablauf:

```
Datei ändern → Änderung vormerken (stagen) → Commit → Push zu GitHub
```

## 4. Und was ist Github?

- GitHub ist der **gemeinsame Ort im Internet**, wo unser Repository liegt
- Wie ein Netzlaufwerk, aber mit Versionshistorie und Kommentarfunktion
- Dort kann man:
  - Die Änderungshistorie ansehen
  - Dateien im Browser anschauen
  - **Pull Requests** stellen und prüfen (→ Theorie: Pull Request)
  - **Issues** erstellen: Aufgaben und Fehler erfassen

---

# Praxisteil 1: Hunde-Repo 🐕

## 1. Setup

- Visual Studio Code öffnen
- Unten links klicken und mit Github-Konto verknüpfen

### Git config

> ⚠️ Die Proxy-Zeile ist nur im Kantonsnetzwerk nötig.

```bash
git config --global http.proxy http://127.0.0.1:9000
git config --global user.name "Tim Rüdiger"
git config --global user.email "tim.ruediger@ji.zh.ch"
```

- "Repositories"-Ordner erstellen auf C:-Laufwerk

## 2. Repository klonen

- Repo klonen in den "Repositories"-Ordner

## 3. Der erste Commit: Hund benennen

- `hunde.html` öffnen
- Eigenen Hundenamen vergeben
- Speichern
- In VS Code: Änderung vormerken (stagen)
- Commit-Message schreiben, z.B. "Wolfi erblickt die Welt"
- Push

## 4. Merge-Konflikt: Was passiert, wenn alle gleichzeitig pushen?

- Mehrere Personen ändern die gleiche Datei und pushen
- → Git meldet einen **Konflikt**: "Jemand anderes hat in der Zwischenzeit auch etwas geändert"
- Gemeinsam anschauen: Wie sieht ein Konflikt aus? Wie löst man ihn auf?
- **Erkenntnis:** Deshalb brauchen wir Branches!

## 5. Branches: Sicher arbeiten ohne den Hauptstrang zu gefährden

- Jede/r erstellt einen eigenen Branch, z.B. `feature/mein-hund`
- Auf dem Branch eine Änderung machen und committen
- **Pull Request** auf GitHub erstellen und gemeinsam anschauen: Wie wird er gemergt?

## 6. Einen Commit rückgängig machen

- In VS Code: Rechtsklick auf einen Commit → "Revert Commit"
- Git erstellt einen neuen Commit, der die Änderung rückgängig macht — die Geschichte bleibt erhalten


# Praxisteil 2: XML-Editionsdaten

> Dieser Teil arbeitet mit einem anderen Repository (XML-Editionsdaten). Die Teilnehmenden klonen also ein zweites Repo — der Ablauf ist identisch wie in Schritt 2.

## 7. Issues: Aufgaben erfassen und zuweisen

- Was sind Issues? → Aufgabenliste direkt im Repository
- Auf GitHub gemeinsam Issues erstellen, z.B.:
  - "ß zu ss ändern in QZH_109"
  - "Fehlende Keywords ergänzen in QZH_110"
  - "Datum im `<publicationStmt>` prüfen"
- Issue sich selbst zuweisen

## 8. Übung: Editionsaufgabe mit Branch und Pull Request

Jede/r nimmt sich ein Issue vor und arbeitet den vollen Workflow durch:

1. Issue auf GitHub auswählen und sich zuweisen
2. Einen Branch für das Issue erstellen (z.B. `fix/ss-in-qzh109`)
3. Die XML-Datei in VS Code bearbeiten
4. Commit mit Issue-Referenz, z.B. `"ß zu ss geändert, fixes #3"`
5. Push und Pull Request erstellen
6. Eine andere Person prüft den Pull Request und mergt

### Mögliche Aufgaben:

- ß zu ss ändern
- Keywords (`<term>`) ergänzen oder korrigieren
- Kommentare (`<!-- -->`) in den XML-Dateien prüfen und bereinigen
- Metadaten prüfen (Datumsangaben, Personen)

## 9. Demo: Grössere Änderungen

- Kurze Demo (kein Hands-on): Wie man mit "Suchen und Ersetzen" über mehrere Dateien hinweg arbeitet
- Z.B. Links zum Query massenhaft anpassen

---

# Abschluss

## Zusammenfassung

Der typische Workflow für unsere Editionsarbeit:

1. `pull` — neusten Stand holen
2. Branch erstellen für die Aufgabe
3. Dateien bearbeiten, stagen, committen
4. Push und Pull Request erstellen
5. Jemand prüft → Merge

## Glossar (Spickzettel)

| Begriff | Erklärung |
|---------|-----------|
| **Repository (Repo)** | Ein Projektordner mit Git-Überwachung und kompletter Änderungshistorie |
| **Commit** | Ein gespeicherter Snapshot mit Beschreibung — wie "Speichern unter" mit Kommentar |
| **Branch** | Ein Parallelstrang zum Ausprobieren, ohne den Hauptstrang zu verändern |
| **Push / Pull** | Änderungen zu GitHub hochladen (push) bzw. herunterladen (pull) |
| **Merge** | Zwei Branches zusammenführen |
| **Pull Request (PR)** | Eine Anfrage, Änderungen aus einem Branch in den Hauptstrang zu übernehmen — mit Review |
| **Issue** | Eine Aufgabe oder ein Fehler, der im Repository erfasst und zugewiesen wird |
| **Merge-Konflikt** | Entsteht, wenn zwei Personen die gleiche Stelle geändert haben — muss manuell gelöst werden |
    
    
