# Projektplan-Editor

Gantt-Diagramm im Browser. Die Daten liegen in `data.yaml`, `gantt.html` zeigt und bearbeitet sie.

## Dateien

| Datei | Zweck |
|---|---|
| `gantt.html` | Viewer und Editor für die Projektplanung als Gantt-Diagramm  |
| `data.yaml` | Die Plandaten, einzige Quelle |

## Benutzung

1. `gantt.html` in **Edge oder Chrome** öffnen
2. Einmalig **„YAML-Datei verbinden"** klicken, `data.yaml` wählen und im Dialog **„Bei jedem Besuch zulassen"** anklicken.
3. Danach lädt die Seite die Datei selbst und speichert Änderungen automatisch (Schalter unter **Zahnrad-Button**). 
4. Änderungen direkt in der data.yaml oder über die Web-Oberfläche möglich.
5. Eine andere YAML-Datei lässt sich jederzeit über **„Öffnen"** laden. 


## Aufbau von `data.yaml`

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
| `nach` | ID oder Liste: Start am Tag nach dem spätesten Ende |
| `mit` | ID: gleicher Start |
| `start` | festes Datum (überschreibt `nach`/`mit`) |
| `versatz` | zusätzliche Arbeitstage auf den Start |
| `fortschritt` | 0 bis 1 |
| `typ` | `arbeit` (Standard), `doku` oder `meilenstein` |
| `farbe` | optional, bei Phase oder Aufgabe: `stahl`, `salbei`, `sand`, `flieder`, `schiefer`, `oliv`, `taupe`, `himmel` |
