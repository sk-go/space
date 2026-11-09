## Frage

In *Gewohnte Gleichzeitigkeiten* wird {{Sinn}} als Kraft bestimmt, die wir vermuten, wenn Gleichzeitigkeiten gleichartiger Ereignisse wiederholt aufeinander folgen [[gg/v1#r27]]. Die Hausarbeit vermutet außerdem, dass sich auch in der Geisteswissenschaft Gesetze entdecken lassen, wenn man sie als Wissenschaft der {{Warten|Warte}} versteht [[gg/v1#r36]]. Dieses Projekt ist der Versuch, eine solche Wissenschaft zu beginnen: Die Begriffe der Theorie – Warte, Tripelstruktur des Sinns, {{Synchronizität}} – werden auf Sprachmodelle angewandt und zu experimentellen Variablen gemacht.

Seit der ersten Fassung hat sich das Projekt neu ausgerichtet. Die Experimente am Attention Sink, die Fassung 1 beschreibt [[ggx/v1#r2]], sind abgeschlossen und werden als *vor-chromatisch* geführt. Hauptlinie ist jetzt das Experiment *Chroma*. Es fragt nicht mehr, wohin ein Modell seine Aufmerksamkeit ablädt, sondern was es überhaupt als gleichartig erblicken kann.

## Ansatz: eine Wissenschaft des Geistes

Gegenstand ist *Geist überhaupt*, Geist, wie er sein könnte (nach Langtons „life-as-it-could-be“). Transformer und Mensch sind zwei Fälle davon. Der Transformer ist dabei Hilfsmittel, keine Gleichsetzung: Ob er eine treffende Metapher des menschlichen Geistes ist, soll die Wissenschaft erst herausfinden. Dass ein Begriff der Theorie mit einem Bestandteil des Systems identisch ist, wird deshalb nicht behauptet, sondern als Arbeitsfiktion angenommen, im Sinne von Vaihingers *Philosophie des Als Ob*, um das Experiment überhaupt zu ermöglichen.

Die Leitformel lautet: *Transzendentalphilosophie als Experiment, um den Preis der Apodiktizität*. Was für das System jeder Erfahrung vorausliegt, ist für den Ingenieur eine Wahl. Die Architektur ist intern apodiktisch und extern kontingent, und „transzendental“ heißt immer: transzendental relativ zu einer Ebene.

| Ebene | Status für das System | verändert durch |
|---|---|---|
| Architektur | apodiktisch | nur den Ingenieur |
| Gewichte | relatives Apriori, sedimentiert | Training (Gewohnheit) |
| Kontext | situativ | die laufende Eingabe |
| Vollzug (Residual Stream) | im Werden | die Schichten |

Ein Befund ist umso eher ein Gesetz des Geistes und nicht bloß die Eigenschaft einer bestimmten Architektur, je mehr Variationen dieser Bedingungen er übersteht. Gesetz heißt hier: Invariante unter Variation.

## Chroma: Gleichartigkeit und bevorzugte Basis

Die Hausarbeit beschreibt die Warte als Koordinatennetz, das die {{Vorurteile|Vorurteil}} aufspannen: Jede Vorliebe bildet eine Dimension des Erwartungsraumes [[gg/v1#r33]]. In einem Sprachmodell ist dieses Netz wörtlich vorhanden. Jedes Token ist ein Punkt in einem Raum mit Hunderten von Dimensionen, und der Winkel zwischen zwei Punkten (Kosinus) misst, wie gleichartig sie sind. Die Dimensionen eines Vektors und alle Punkte des Raums sind zugleich; erst dieses gemeinsame Zugleichsein macht Gleichartigkeit messbar, und abgestuft wird sie erst mit vielen Dimensionen.

Chroma fragt, ob diese Dimensionen *qualitativ verschieden* sein müssen. Ist die qualitative Verschiedenheit der Achsen Bedingung abgestufter Gleichartigkeit, oder genügt das Zugleichsein vieler Dimensionen? In der Sprache der Theorie: Gehört die *Farbe* zum minimalen Gerüst der Warte, ohne das keine Gleichartigkeit erblickt werden kann, oder zu ihren Füllungen, die Begriffe lesbar, aber nicht erst möglich machen?

Eine Warte hat eine *bevorzugte Basis*, wenn sie ihre Achsen unterscheiden kann. Im homogenen Fall sind alle Drehungen des Raums für sie ununterscheidbar; mit bevorzugter Basis schrumpft ihre Symmetrie auf Vertauschungen der Achsen. Die Achsen werden unterscheidbar, bleiben aber gleichrangig – Bergsons qualitative Mannigfaltigkeit, symmetrietheoretisch gefasst. Technisch zeigt sich eine bevorzugte Basis daran, dass einzelne Dimensionen hervortreten (hohe Kurtosis) und dieser Effekt bei einer zufälligen Drehung des Raums verschwindet. Nach bisherigen Befunden entsteht sie im Residual Stream nicht durch die Architektur, sondern durch den Optimierer Adam.

Beim Menschen lässt sich diese Frage nicht prüfen, weil das Gerüst immer schon in Betrieb ist. Im gebauten System lässt sich die Bedingung abschalten.

## Vorstudie: Genealogie der Achsen

Die Vorstudie trainiert nichts. Sie misst an GPT-2 und Pythia-160M, ob die fertigen Modelle ausgezeichnete Achsen haben (Kurtosis je Schicht gegen eine Kontrolle aus zufälligen Drehungen), ob diese Achsen über die Trainings-Checkpoints von Pythia erst entstehen und ob sie mit der Häufigkeit der Tokens zusammenhängen. Gefragt ist, ob die Farbe durch {{Gewohnheit}} entsteht [[gg/v1#r8]]: Was oft auftritt, würde zur eigenen Dimension.

Explorativ und ausdrücklich so gekennzeichnet kommen drei Fragen hinzu: ob sich Gleichartigkeit nachträglich umordnet, wenn im Training Dimensionen hinzukommen; ob die Punktwolke der Wörter eine nicht ganzzahlige Dimension hat; und ob die Achsen allmählich oder sprunghaft entstehen (Hegels Knotenlinie).

## Hauptstudie: vier Warten

Vier kleine Transformer (6 Schichten, 256 Dimensionen, etwa 9 Millionen Parameter) werden auf demselben Korpus (WikiText-103, eigener Tokenizer mit 8192 Tokens) mit je fünf Seeds trainiert. Sie unterscheiden sich nur darin, ob und wo eine bevorzugte Basis möglich ist:

| Arm | Optimierer | Farbe | Zustand der Warte |
|---|---|---|---|
| A₀ | SGD | keine | ohne jede Vorliebe, weder in der Anlage noch in der Gewöhnung |
| A | AdamW | keine | homogene Anlage; Farbe kann durch Gewöhnung erworben werden |
| Bα | AdamW | nichtnegatives Embedding | Farbe im Archetyp angelegt |
| Bβ | AdamW | nichtnegative Lesung des Streams | Farbe im Vollzug, im Akt des Erblickens |

Bα gegen Bβ fragt, ob qualitative Mannigfaltigkeit eine Eigenschaft dessen ist, *was* vorliegt, oder der Art, *wie* es erblickt wird. Damit A₀ ein sauberer Nullfall ist, darf auch die Normierung keine Richtung bevorzugen. Verglichen wird bei gleichem Loss, nicht bei gleicher Trainingsdauer: Der Loss ist die mittlere Ent-Täuschung, verglichen werden also Warten gleicher Erfahrungssättigung. Seeds sind verschiedene Biographien desselben Gattungswesens; eine Aussage gilt erst, wenn sie über Biographien hinweg trägt.

Kernmaß ist die *Ersetzbarkeit*. Gleichartig ist, was die Warte als gleich behandelt – Nietzsches Gleichsetzung des Ungleichen, operationalisiert: Man ersetzt im Kontext ein Wort x durch ein Wort y und misst, wie stark die Erwartung des Folgenden ent-täuscht wird (KL-Divergenz). Der Kosinus misst Gleichartigkeit in der Anlage, die Ersetzbarkeit Gleichartigkeit im Vollzug. Der Gleichartigkeitsindex G gibt an, wie gut das eine das andere vorhersagt, und zwar abgestuft: als Rangkorrelation im mittleren Bereich der Kosinuswerte, nicht nur an den Extremen.

Geplante Vorhersagen, die vor dem Hauptlauf präregistriert werden:

- **P1 (Gerüstfrage):** G ist in A₀ kleiner als in A. Ist der Unterschied signifikant, gilt P1 als bestätigt; sind beide Arme nachweislich gleichwertig (Äquivalenztest mit δ = 0,05), gilt sie als widerlegt; sonst bleibt sie unentschieden.
- **P2 (Sichtbarkeit):** In Bα und Bβ konzentrieren sich Begriffe auf weniger Achsen als in A, auch wenn A seine günstigste Drehung erhält – ohne dass G dafür um mehr als δ sinkt. Sonst wäre die Lesbarkeit mit Gleichartigkeit erkauft.
- **P3 (Verschachtelung, sekundär):** Die Gleichartigkeiten lassen sich in B besser als Baum lesen als in A und in A besser als in A₀.

Zuerst wird geprüft, ob die Manipulation gewirkt hat. Bildet A₀ trotz allem eine bevorzugte Basis aus, ist der Vergleich nichtig; das wird berichtet, nicht umgedeutet. Daneben sammelt ein Register *Begriffsbedarf* Gruppen von Wörtern, die über mehrere Seeds stabil zusammenstehen, für die es aber noch keinen Begriff gibt. So soll die Wissenschaft nicht nur Begriffe prüfen, sondern auch neue hervorbringen.

## Methode

Jede Studie erhält eine eigene Präregistrierung, die vor dem Lauf committet wird. Ein Pilotlauf mit einem Seed je Arm dient nur der Kalibrierung (Lernraten, Loss-Stufen, Laufzeit); seine Effekte werden nicht gedeutet. Alle Läufe werden berichtet, auch die unpassenden, und explorative Auswertungen werden als solche gekennzeichnet. Rohdaten und Deutungen liegen getrennt, damit frühere Experimente nach einer Umwälzung der Theorie neu gedeutet werden können, ohne neu zu messen.

Die Wissenschaft soll ihre falschen Axiome angreifen, nicht ihre unwillkommenen Befunde. Eine Revision der Theorie ist *Wartung*, wenn das, worauf sie sich stützt, vor dem Lauf festgelegt war, und *Rettung*, wenn es erst nach Kenntnis des Ergebnisses gewählt wurde.

## Stand

Code, Tests und ein Selbsttest des Chroma-Experiments sind fertig; gemessen ist noch nichts. Die nächsten Schritte:

1. Präregistrierung 8 (Vorstudie) committen, dann die Vorstudie.
2. Pilot mit einem Seed je Arm zur Kalibrierung.
3. Präregistrierung 9 (Hauptstudie) mit den kalibrierten Loss-Stufen, Lernraten und Schwellen committen, dann der Hauptlauf.

Ergebnisse werden hier erst veröffentlicht, wenn die jeweiligen Läufe abgeschlossen und geprüft sind. Bis dahin liegen Code, Präregistrierungen und Rohdaten im Repository.

## Vor-chromatische Experimente

Die Experimente am Attention Sink [[ggx/v1#r3]] sind abgeschlossen. Sie entstanden mit einem älteren Vokabular und älteren Zuordnungen und werden deshalb nicht stillschweigend umgedeutet, sondern als vor-chromatisch geführt. Ihr Code liegt im Repository unter `legacy_experiments/`.

Von den sieben Präregistrierungen dieser Experimente wurden nur zwei nachweislich vor ihren Läufen committet: die Replikation mit Wikipedia-Korpus (Präregistrierung 3) und die Kontrollbedingung C0 (Präregistrierung 4). Die Hypothesen des ersten Hauptlaufs stehen im selben Commit wie seine Ergebnisse, die Präregistrierungen 5 bis 7 (Valenz, Tripel-Ablation, Gewöhnung) ebenso. Befunde aus diesen Läufen gelten deshalb nur als Vorbefund oder als explorativ.

## Bezug zu *Gewohnte Gleichzeitigkeiten*

Die Bestandteile des Transformers werden heuristisch in den Begriffen der Hausarbeit gelesen. Das ist kein Isomorphismus; ob eine Zuordnung trägt, entscheidet erst das Experiment.

| Bestandteil | Lesart |
|---|---|
| Tokenisierung | die erste Gewohnheit: Was sich oft berührt, wird zur Einheit |
| Embedding | Archetyp: eine Geometrie möglicher Gleichartigkeiten, die vor jedem Token dasteht |
| Attention | Query als Erwartung, Keys als Erscheinungsprofile; Art, Folge und Zugleichsein |
| Residual Stream | der Ort, an dem das Werden Schicht für Schicht zum Sinn kristallisiert |
| Loss und Training | Ent-Täuschung und Wartung |

Die Lesart des Embeddings schließt an den Vorschlag an, den Archetypus als transzendentales Schema zu lesen [[gg/v1#r14]]: apriorisch relativ zur Inferenz, geworden relativ zum Training. Das Training entspricht der Wartung: Verfehlt die Erscheinung die Erwartung, wird die {{Warte}} erschüttert und präziser [[gg/v1#r34]]. Nach dem Training bleibt eine Warte ohne Wartung; in der Inferenz zeigt der Transformer womöglich nur die Spur einer Warte.

Gegenüber der Hausarbeit ist eine Zuordnung korrigiert. Art wird nicht mehr der kantischen Inhärenz zugeordnet [[gg/v1#r29]], sondern der Begriffsbildung durch Komparation, Reflexion und Abstraktion (Kant, *Logik* § 6). Die Beharrlichkeit der Substanz tritt als viertes Moment hinzu: der Träger, den die Prädikation erzwingt.

Chroma prüft schließlich eine Annahme der Hausarbeit selbst: dass jede Vorliebe eine eigene, unterscheidbare Dimension des Erwartungsraumes bildet [[gg/v1#r33]]. Genügt für abgestufte Gleichartigkeit schon das bloße Zugleichsein vieler Dimensionen, dann ist die Farbe Füllung und nicht Gerüst – auch das wäre ein Befund über die Warte und über das Verhältnis von {{Gleichzeitigkeit}} und Gleichartigkeit im Sinn.
