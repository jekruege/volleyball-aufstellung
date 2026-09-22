# Volleyball-Aufstellung

Interaktives Volleyballfeld zum Planen von Aufstellungen: beide Feldhälften, ein
gegnerischer Angreifer mit Schlagwinkeln und sechs eigene Spieler, die sich frei
verschieben lassen.

Live: https://jekruege.github.io/volleyball-aufstellung/

## Bedienung

- **Verschieben**: Spieler, Angreifer und Ball mit Maus oder Finger ziehen.
- **Klick** auf einen eigenen Spieler wechselt die Farbe: Spieler (blau) →
  Zuspieler (orange) → Libero (grün).
- **Doppelklick** ändert die Beschriftung.
- **Vereins-Vorlagen** kommen aus `vorlagen.json` und sind für alle gleich.
- **Eigene Vorlagen** speichert jeder in seinem eigenen Browser. Doppelklick auf
  den Namen überschreibt sie mit der aktuellen Aufstellung.

## Vereins-Vorlagen ändern

1. Aufstellungen in der Seite bauen und unter „Eigene Vorlagen" speichern.
2. „Als Datei sichern" klicken – es entsteht `volleyball-vorlagen.json`.
3. Die Datei hier im Repository als `vorlagen.json` hochladen (ersetzen).

Nach ein bis zwei Minuten zeigt die Seite die neuen Vorlagen. Wer sie vorher
offen hatte, muss einmal neu laden.

## Dateien

- `index.html` – die komplette Anwendung, ohne externe Abhängigkeiten
- `vorlagen.json` – die gemeinsamen Vereins-Vorlagen

Die Seite funktioniert auch offline: `index.html` herunterladen und per
Doppelklick öffnen. Die Vereins-Vorlagen fehlen dann, alles andere läuft.
