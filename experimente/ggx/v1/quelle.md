## These

In *Gewohnte Gleichzeitigkeiten* wird {{Sinn}} als Kraft bestimmt, die wir vermuten, wenn Gleichzeitigkeiten gleichartiger Ereignisse wiederholt aufeinander folgen [[gg/v1#r27]]. Daraus ergibt sich eine Tripelstruktur aus Art, Folge und Zugleichsein [[gg/v1#r29]]. Dieses Experiment fragt, ob sich diese Struktur in einem Sprachmodell wiederfinden lässt.

Die These lautet: Der *Attention Sink* eines Transformers – der Ort, an dem ein Attention-Kopf seine Aufmerksamkeit ablädt, wenn im Kontext nichts resoniert – ist eine verdrängte Asynchronizität. Er wäre damit das technische Gegenstück zu jener Sinnvergessenheit, die nach einem Sinn sucht [[gg/v1#r35]], und zur Asynchronizität als Koinzidenz verschiedenartiger Momente [[gg/v1#r44]].

## Aufbau

Um die Dimensionen des Sinns einzeln zu prüfen, werden sie in fünf Bedingungen gezielt zerstört:

| Bedingung | Art | Folge | Konstruktion |
|---|---|---|---|
| A kohärent | ✓ | ✓ | zusammenhängender Text |
| B wortgewürfelt | ✓ | ✗ | Wörter von A permutiert |
| B2 satzgewürfelt | ✓ | teilweise | Sätze von A permutiert, Grammatik bleibt |
| C disparat | ✗ | ✓ | Einzelsätze aus fremden Dokumenten |
| D Rauschen | ✗ | ✗ | Zufallstokens nach Häufigkeit |

Gemessen werden die Sink-Masse (der Anteil der Aufmerksamkeit eines Kopfes, der auf das Start-Token fällt), die Entropie der Ausgabeverteilung als Asynchronizität auf der Ausgabeseite und der Loss als Kontrolle, ob die Bedingungen wirken.

## Methode

Jede Untersuchung beginnt mit einem Pilotlauf auf eigenem Korpus und eigenem Seed, der nicht in die Hypothesentests einfließt. Danach werden Hypothesen, Entscheidungsregeln und Parameter präregistriert und committet, *bevor* der Hauptlauf startet. Die Hauptläufe verwenden GPT-2 und Pythia-160M; über die Trainings-Checkpoints von Pythia lässt sich verfolgen, wie sich der Sink im Lauf des Trainings herausbildet – die Frage nach der {{Gewohnheit}}, die eine {{Warte}} erst aufbaut [[gg/v1#r8]].

Weil beide Modelle Wikipedia und viele Webtexte im Training gesehen haben, stammen die kohärenten Texte für Replikationen aus Wikipedia-Artikeln, die erst nach Ende 2023 angelegt wurden. Statistisch werden einseitige Permutationstests, Bootstrap-Konfidenzintervalle und eine Korrektur für multiples Testen verwendet.

## Stand

Das Projekt läuft. Bisher sind sieben Präregistrierungen festgehalten:

- Hauptlauf mit den Hypothesen H1 (Asynchronizität), H2 (Dissoziation von Art und Folge) und H3 (Genese im Training)
- Präregistrierung 2: Abweichung von H3
- Präregistrierung 3: Replikation des Hauptlaufs mit Wikipedia-Korpus
- Präregistrierung 4: Kontrollbedingung C0
- Präregistrierung 5: Valenz-Inkongruenz und Rekognition im Begriff
- Präregistrierung 6: Die faktorielle Ablations-Triade
- Präregistrierung 7: Ontogenese des Sinns durch Gewohnheit (Training)

Ergebnisse werden hier erst veröffentlicht, wenn die jeweiligen Läufe abgeschlossen und geprüft sind. Bis dahin liegen Code, Präregistrierungen und Rohdaten im Repository.

## Bezug zu *Gewohnte Gleichzeitigkeiten*

Die Hausarbeit führt die {{Warte}} als zeitliche Invarianz ein, an der ein Phänomen nicht mechanisch registriert, sondern erblickt wird: Es erhält eine Wertung, einen unterstellten Urheber und eine Schätzung seiner Dauer [[gg/v1#r31]] [[gg/v1#r32]]. Ein Attention-Kopf lässt sich als eine solche Warte lesen: Er bestimmt, welche Positionen zueinander passen (Art), in welcher Ordnung sie stehen (Folge) und was zu einer gemeinsamen Repräsentation zusammengefasst wird (Zugleichsein).

Das Experiment übersetzt damit die begriffliche Zusammenführung aus Kapitel 4 [[gg/v1#k4]] und die Überlegungen zur Asynchronizität aus Kapitel 5.4 [[gg/v1#k5.4]] in überprüfbare Vorhersagen. Bestätigt sich die These nicht, ist der Sink eine inhaltsunabhängige Gewohnheit des Modells – auch das wäre ein Befund über die Grenzen der Übertragung von {{Synchronizität}} und {{Gleichzeitigkeit}} auf Maschinen.
