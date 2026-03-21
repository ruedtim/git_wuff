# Git-Workshop für die NE

> **Dauer:** 2.5 Stunden | **Teilnehmende:** 8 | **Vorkenntnisse:** keine IT-Kenntnisse nötig

## Voraussetzungen (vor dem Workshop erledigen)

- [ ] Visual Studio Code installiert
- [ ] Git installiert
- [ ] GitHub-Account erstellt unter [github.com](https://github.com)

## Zeitplan
### Dieser Untertitel hat noch gefehlt

| Block | Dauer | Inhalt |
|-------|-------|--------|
| Theorie | ~20 min | Motivation, Git-Konzepte, GitHub |
| Setup | ~15 min | VS Code, git config, Repo klonen |
| Teil 1: Hunde-Repo | ~45 min | Commit, Push, Konflikt, Branch, Pull Request |
| *Pause* | ~10 min | |
| Teil 2: XML-Editionsdaten | ~50 min | Issues, Branches, echte Editionsarbeit |
| Abschluss | ~10 min | Fragen, Zusammenfassung, Glossar |

---

# Praxisteil 1: Hunde-Repo 🐕

Nach jedem Commit auf `main` werden die aktuellen Hunde automatisch auf GitHub Pages deployed. Nach einer kurzen Deploy‑Zeit (meist Sekunden bis wenige Minuten) sind sie unter https://ruedtim.github.io/git_wuff/hunde.html sichtbar.

## 1. Setup

- "Repositories"-Ordner erstellen auf "C:\Temp\Repositories"
- Visual Studio Code öffnen
- Unten links klicken und mit Github-Konto verknüpfen

### Git config

> ⚠️ Die Proxy-Zeile ist nur im Kantonsnetzwerk nötig.
> ⚠️ Ersetze Tim Rüdiger mit Deinem Namen

```bash
git config --global http.proxy http://127.0.0.1:9000
git config --global user.name "Tim Rüdiger"
git config --global user.email "tim.ruediger@ji.zh.ch"
```

## 2. Repository klonen

- Repo klonen in den "Repositories"-Ordner

Beispiel (in PowerShell oder Terminal):

```bash
git clone https://github.com/ruedtim/git_wuff "C:\Temp\Repositories\git_wuff"
```

## 3. Der erste Commit: Hund benennen

- `hunde.html` öffnen
- Eigenen Hundenamen vergeben
- Speichern (Ctrl+s)
- In VS Code: Änderung vormerken (stagen)
- Commit-Message schreiben, z.B. "Wolfi erblickt die Welt"
- Push
- restliche Konfigurationen durchführen, aber nach jeder Einzelkonfiguration committen (z.B. "Wolfi erhält Sonnenbrille", "Wolfi spricht") und pushen

## 4. Merge-Konflikt: Was passiert, wenn alle gleichzeitig pushen?

- Mehrere Personen ändern die gleiche Datei und pushen
- → Git meldet einen **Konflikt**: "Jemand anderes hat in der Zwischenzeit auch etwas geändert"
- Gemeinsam anschauen: Wie sieht ein Konflikt aus? Wie löst man ihn auf?
- **Erkenntnis:** Deshalb brauchen wir Branches!

- hier können wir zu demonstrationszwecken einen Commit, der schon eine Zeit zurück liegt, rückgängig machen

## 4.1. Was passiert, wenn jemand den Code kapputtmacht?

## 5. Branches: Sicher arbeiten ohne den Hauptstrang zu gefährden

- Jede/r erstellt einen eigenen Branch, z.B. `Wolfi`
- Auf dem Branch eine Änderung machen und committen
- **Pull Request** auf GitHub erstellen und gemeinsam anschauen: Wie wird er gemergt?

## 6. Einen Commit rückgängig machen

- Git erstellt einen neuen Commit, der die Änderung rückgängig macht — die Geschichte bleibt erhalten


# Praxisteil 2: XML-Editionsdaten

> Dieser Teil arbeitet mit einem anderen Repository (XML-Editionsdaten). Die Teilnehmenden klonen also ein zweites Repo — in diesem Workshop verwenden wir das Repo `qzh_vibe`.

Beispiel zum Klonen des XML-Repos:

```bash
git clone https://github.com/ruedtim/qzh_vibe "C:\Temp\Repositories\qzh_vibe"
```

### Hinweis: Deployment & Branch‑Schutz im XML‑Repo

- Der Branch "live" wird automatisch nach jedem Merge deployed und ist unter https://ruedtim.github.io/qzh_vibe erreichbar.
- Im Unterschied zum Hunde‑Repo ist "live" geschützt:
    - Direktes Pushen auf "live" ist nicht möglich.
    - Änderungen kommen nur via Pull Request (PR) in "live".
    - Mindestens 1 Review (Approval) ist erforderlich, bevor gemerged werden darf.

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