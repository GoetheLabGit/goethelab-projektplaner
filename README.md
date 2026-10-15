# Projektplan-Editor

Gantt-Diagramm für Projekt- und Abschlussarbeiten, direkt im Browser. Der Plan steht in einer YAML-Datei, `gantt.html` zeigt und bearbeitet sie. Kein Server, keine Installation.

## Dateien

| Datei | Zweck |
|---|---|
| `gantt.html` | Viewer und Editor für den Projektplan |
| `data_example.yaml` | Beispielprojekt, Vorlage für die eigene YAML-Datei |

## Vorgehen

1. **Eigene YAML-Datei erstellen:** Notizen, Exposé, Word-Dokument o. Ä. zusammen mit `data_example.yaml` an eine KI geben, z. B. *„Erstelle aus meinen Unterlagen einen Projektplan im Format dieser YAML-Datei.“* Der Kommentarkopf der Vorlage erklärt alle Felder. Ergebnis als `.yaml` speichern.
2. **`gantt.html` in Edge oder Chrome öffnen.** Ohne verbundene Datei zeigt die Seite das Beispielprojekt.
3. **Einmalig verbinden:** **„YAML-Datei verbinden"** klicken, die eigene Datei wählen und im Dialog **„Bei jedem Besuch zulassen"** anklicken. Danach lädt die Seite die Datei bei jedem Öffnen selbst.
4. **Bearbeiten** im Browser oder direkt in der Datei. Änderungen an der Datei übernimmt die Seite nach wenigen Sekunden, Änderungen im Browser schreibt **„Automatisch speichern"** (unter ⚙) in die Datei.
5. Weitere Pläne jederzeit über **„Öffnen"** laden.

## Aufbau der YAML-Datei

```yaml
titel: Projekttitel
autor: Name
start: 2026-10-05
frei:
  - 2026-12-24..2027-01-01      # freie Tage, einzeln oder von..bis
phasen:
  - name: Phase 1
    aufgaben:
      - {id: a, name: Aufgabe A, dauer: 5, fortschritt: 0.2}
      - {id: b, name: Aufgabe B, nach: a, dauer: 3}
```

| Feld | Bedeutung |
|---|---|
| `dauer` | Arbeitstage (ohne Wochenenden und `frei`), `0` ist erlaubt. Entfällt bei Meilensteinen |
| `nach` | ID oder Liste von IDs: Start am nächsten Arbeitstag nach dem spätesten Ende |
| `mit` | ID: gleicher Start |
| `start` | festes Datum (überschreibt `nach`/`mit`) |
| `versatz` | zusätzliche Arbeitstage auf den Start |
| `fortschritt` | 0 bis 1 |
| `typ` | `arbeit` (Standard), `doku` oder `meilenstein` |
| `notiz` | optionaler Zusatz, erscheint unter dem Namen |
| `farbe` | optional, bei Phase oder Aufgabe: `stahl`, `salbei`, `sand`, `flieder`, `schiefer`, `oliv`, `taupe`, `himmel` |

Werte mit Komma oder Doppelpunkt in Anführungszeichen setzen. Ein vollständiges Beispiel mit allen Feldern ist `data_example.yaml`.
