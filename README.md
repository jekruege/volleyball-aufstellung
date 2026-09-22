# Volleyball-Aufstellung

Interaktives Volleyballfeld zum Planen von Aufstellungen: beide Feldhälften, je
sechs Spieler, Schlagwinkel des gegnerischen Angreifers und frei verschiebbare
Figuren.

Live: https://jekruege.github.io/volleyball-aufstellung/

## Bedienung

- **Verschieben**: alle Figuren mit Maus oder Finger ziehen.
- **Klick** wechselt die Rolle und damit die Farbe. Bei eigenen Spielern:
  Spieler (blau) → Zuspieler (orange) → Libero (grün) → ausgeblendet.
  Beim Gegner: Spieler (grau) → Angreifer (rot, mit Schlagwinkeln) →
  ausgeblendet. Es kann immer nur ein Angreifer markiert sein.
- **Ausgeblendete** Figuren erscheinen oben in der Seitenleiste und kommen per
  Klick darauf zurück.
- **Doppelklick** ändert die Beschriftung. „Z" färbt orange, „L" grün.
- **Standardvorlagen**: Grundstellung, W-Annahme sowie Abwehr mit vorgezogener
  und mit zurückgezogener 6, jeweils mit Doppel- und Einerblock gegen Angriffe
  über deren 4, deren 2 und die Mitte. Sie sind fest eingebaut.
- **Weitere Vorlagen** kommen aus einer JSON-Datei, die im Link angegeben wird
  (siehe unten). Ohne Angabe bleibt es bei den Standardvorlagen.
- **Eigene Vorlagen** speichert jeder in seinem eigenen Browser. Doppelklick auf
  den Namen überschreibt sie mit der aktuellen Aufstellung.

Die zuletzt gezeigte Aufstellung merkt sich der Browser und stellt sie beim
nächsten Öffnen wieder her.

## Mehrere Vorlagensätze über den Link

Ohne Zusatz zeigt die Seite nur die eingebauten Standardvorlagen. Mit dem
Parameter `?vorlagen=` kommt ein eigener Satz dazu – praktisch, um jeder
Mannschaft ihren eigenen Link zu geben.

Die gemeinsamen Vorlagen aus diesem Repository:

```
https://jekruege.github.io/volleyball-aufstellung/?vorlagen=vorlagen.json
```

Ein anderer Satz, ebenfalls hier abgelegt:

```
https://jekruege.github.io/volleyball-aufstellung/?vorlagen=damen2.json
```

Datei irgendwo sonst auf GitHub (vollständige Roh-Adresse):

```
https://jekruege.github.io/volleyball-aufstellung/?vorlagen=https://raw.githubusercontent.com/jekruege/volleyball-aufstellung/main/damen2.json
```

Die Überschrift in der Seitenleiste zeigt dann den Dateinamen an, damit im
Training klar ist, welcher Satz geladen ist.

Aus Sicherheitsgründen werden nur Dateien neben der Seite und GitHub-Adressen
geladen (`github.com`, `raw.githubusercontent.com`, `gist.github.com`,
`gist.githubusercontent.com`, `*.github.io`). Andere Adressen lehnt die Seite
mit einem Hinweis ab, damit ein präparierter Link keine fremden Inhalte
einschleusen kann.

Die Adresse darf dabei so aussehen, wie sie im Browser steht – die Seite rechnet
sie selbst auf die Roh-Adresse um. Diese drei Formen funktionieren alle:

```
https://gist.github.com/name/abc123
https://gist.github.com/name/abc123/raw/.../vorlagen.json
https://github.com/jekruege/volleyball-aufstellung/blob/main/vorlagen.json
```

## Eigene Vorlagen ohne Zugriff aufs Repository teilen (Gist)

Wer selbst Vorlagen beisteuern will, braucht keinen Zugang zu diesem
Repository. Ein Gist genügt – eine Art Notizzettel bei GitHub:

1. In der Seite alle Aufstellungen bauen und unter „Eigene Vorlagen" speichern.
2. Auf „Als Datei sichern" klicken. Die Datei landet im Download-Ordner.
3. Die Datei in einem Texteditor öffnen und den gesamten Inhalt kopieren.
4. Auf https://gist.github.com anmelden, den Inhalt in das große Feld einfügen,
   als Dateinamen `vorlagen.json` eintragen und unten auf **Create secret gist**
   klicken. Secret heißt: nicht öffentlich auffindbar, aber für jeden mit dem
   Link lesbar. **Create public gist** geht genauso.
5. Die Adresse aus der Adresszeile kopieren und an den Link ttps://jekruege.github.io/volleyball-aufstellung/?vorlagen= anhängen. So zum Beispiel:

```
https://jekruege.github.io/volleyball-aufstellung/?vorlagen=https://gist.github.com/name/abc123
```

Diesen Link kann die Person dann an ihre Mannschaft weitergeben. Ändert sie
später etwas, bearbeitet sie den Gist über **Edit** – der Link bleibt derselbe,
und alle sehen beim nächsten Aufruf den neuen Stand.

Wer gar kein GitHub-Konto hat, schickt einfach die gesicherte Datei weiter; sie
lässt sich in jeder Seite über „Datei laden" einlesen.

## Vorlagen anlegen oder ändern

1. Aufstellungen in der Seite bauen und unter „Eigene Vorlagen" speichern.
2. „Als Datei sichern" klicken – es entsteht `volleyball-vorlagen.json`.

Über „Datei laden" lässt sich so eine Datei auch wieder in den eigenen Browser
einlesen – gleichnamige Vorlagen werden ersetzt, die übrigen bleiben erhalten.

## Format der Vorlagen-Datei

Eine JSON-Datei mit einem Eintrag je Aufstellung. Koordinaten sind Meter:
`x` läuft von 0 (links) bis 9 (rechts), `y` ist der Abstand zum Netz – positiv
auf der eigenen Seite, negativ beim Gegner.

```json
{
  "Abwehr gegen deren 4": {
    "own":  [["1", 8.1, 7.4, "spieler"], ["2", 7.9, 0.45, "zuspieler"], "… sechs Einträge"],
    "opp":  [["4", 8.0, -1.3, "angreifer"], ["3", 4.6, -1.4, "gegner"], "… sechs Einträge"],
    "ball": [7.8, -0.5]
  }
}
```

Mögliche Rollen sind `spieler`, `zuspieler`, `libero` und `versteckt` für die
eigene Mannschaft sowie `gegner`, `angreifer` und `versteckt` für die
gegnerische. Ältere Dateien, die statt `opp` nur ein einzelnes `att` enthalten,
werden weiterhin gelesen; die übrigen fünf Gegner sind dann ausgeblendet.

## Dateien

- `index.html` – die komplette Anwendung, ohne externe Abhängigkeiten
- `vorlagen.json` – die gemeinsamen Vorlagen des Vereins, per `?vorlagen=`
  aufrufbar

Die Seite funktioniert auch offline: `index.html` herunterladen und per
Doppelklick öffnen. Die Vereins-Vorlagen fehlen dann, alles andere läuft.
