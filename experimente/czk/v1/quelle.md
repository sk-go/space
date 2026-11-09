## Frage

Viele Gedanken entstehen inzwischen im Gespräch mit Sprachmodellen: in Claude, ChatGPT und Gemini, beim Programmieren in Claude Code. Dort bleiben sie liegen, verteilt über Hunderte von Chats, und mit der Zeit verschwimmt, wer was gesagt hat. Der Chattelkasten macht aus diesen Gesprächen einen Zettelkasten in Obsidian. Er beantwortet zu jeder Idee zwei Fragen: Woran schließt sie an, und von wem stammt sie?

Die zweite Frage ist die strengere. Für Hausarbeiten gelten Regeln für KI-Hilfe. Eine Idee des Modells, die als eigene markiert ist, ist der schlimmste Fehler, den das System machen kann. Die Herkunft ist deshalb kein Schmuck, sondern das Feld, an dem alles andere hängt.

## Aufbau

Der Kasten arbeitet in sechs Schritten. Jeder Schritt merkt sich, was er schon erledigt hat; ein Abbruch ist harmlos.

| Schritt | Was geschieht | Womit |
|---|---|---|
| Import | Exporte von Claude, ChatGPT und Gemini, Claude-Code-Sitzungen, Web-Clippings | eigene Parser |
| Extraktion | Die gehaltvollen Gedanken werden als atomare Zettel herausgeschrieben: eine Idee pro Notiz, ohne den Chat verständlich | Claude-API |
| Einbettung | Jeder Zettel wird ein Punkt in einem Vektorraum | Qwen3-Embedding, lokal über Ollama |
| Clustering | Themen-Cluster mit typischen Begriffen und Titel; Cluster werden zu Bereichen gruppiert | UMAP, HDBSCAN, c-TF-IDF |
| Verknüpfung | Für ähnliche Zettel aus verschiedenen Clustern wird geprüft, ob eine argumentative Beziehung besteht | Claude-API |
| Vault | Ideen-, Cluster- und Chat-Notizen in Obsidian | Markdown |

Verknüpfungen bleiben Vorschläge: *stützt*, *widerspricht*, *setzt voraus*, *ist Beispiel für*, *beantwortet*, *erweitert*, *analog*. Übernommen wird nur, was im Zettel angehakt ist, und Verworfenes kommt nicht wieder. Was unterhalb der Markierung `czk:auto:end` steht, gehört dem Schreibenden und wird nie überschrieben.

## Herkunft

Jeder Zettel trägt eine von fünf Herkünften:

| Herkunft | Bedeutung |
|---|---|
| ich | eigener Gedanke |
| gemeinsam | im Gespräch entstanden |
| modell | vom Modell |
| quelle | aus einem eingefügten fremden Text, auch wenn das Modell ihn übersetzt oder umformt |
| unklar | der Sprecher des Beitrags lässt sich nicht sicher bestimmen |

Die Regel lautet: im Zweifel *unklar*, nie *ich*. Das ist schwieriger, als es klingt. Exporte nennen den Sprecher ausdrücklich, Web-Clippings nicht; dort wird die Rolle für jeden Beitrag einzeln aus der Form erschlossen, weil Antworten eines Modells formatiert sind und diktierte Beiträge nicht. In Claude-Code-Sitzungen erscheinen Zusammenfassungen nach einer Kompaktierung, Meldungen von Hintergrundaufgaben und Shell-Zeilen formal als Beiträge des Nutzers; sie werden herausgefiltert. Jede dieser Regeln ist durch Tests abgesichert.

## Polyphonie

Qwen3-Embedding bettet nach einer Anweisung ein. Dieselben Zettel ergeben unter verschiedenen Anweisungen verschiedene Räume. Jede Anweisung ist eine *Stimme*, eine {{Warte}}: *Begriff* hört auf das Thema, *Struktur* auf die Form des Arguments, dazu kommen *Motiv* und *Bild*. Aufschlussreich sind die Paare, die nur eine Stimme hört. Dort stehen Analogien über Themen hinweg, etwa zwei Argumente gleicher Form aus verschiedenen Gebieten.

Ob die Polyphonie trägt, wird gemessen. Für je zwei Stimmen zählt der Kasten die gemeinsamen Nachbarn und prüft, wie weit ihre Geometrien übereinstimmen. Liegen beide Werte nahe 1, ist eine Stimme keine eigene Warte und kann wegfallen. Jeder Zettel trägt außerdem eine *Mehrstimmigkeit* zwischen 0 (alle Stimmen hören dieselben Nachbarn) und 1 (jede Stimme hört andere).

## Nachbarn beim Schreiben

Das Obsidian-Plugin zeigt beim Schreiben in der Seitenleiste die nächsten Zettel und eigenen Permanenzen zum Absatz unter dem Cursor, mit dem Kapitel darüber als Kontext. Oben wird die Stimme gewählt. Jede Zeile zeigt Ähnlichkeit und Herkunft: Eigenes ist frei nutzbar, Gemeinsames und Fremdes wird zitiert oder in eigene Worte gebracht. Ein Klick öffnet die Notiz neben dem Text.

Das Plugin spricht mit einem lokalen Dienst (`czk serve`), der nur auf dem eigenen Rechner läuft und Ollama braucht, aber keinen API-Schlüssel. Es steht nicht im Verzeichnis der Community-Plugins, sondern liegt im Ordner `obsidian/` des Repos und wird von Hand eingebunden.

## Anbindung an Sprachmodelle

Mit `czk mcp` wird der Kasten zu einem MCP-Server. Ein Sprachmodell, etwa in Claude Code, kann darin suchen, Zettel lesen, die Cluster überblicken und eine neue These gegen frühere Entscheidungen und verworfene Spuren prüfen. Auch hier trägt jeder Zettel seine Herkunft, und der Server weist das Modell an, Ideen, die nicht von *ich* stammen, nie ungekennzeichnet als eigene auszugeben.

Hypothesen-Entwürfe nimmt der Server nur an, wenn jedes Zeichen der Formel in einer Legende einen Begriff erhält, eine präzise Bedingung angegeben ist, unter der die Hypothese widerlegt wäre, und die Herkunft nicht *ich* lautet. Was ein Modell vorschlägt, kann so nicht als eigener Gedanke in den Kasten gelangen.

## Stand

Gebaut sind Import, Extraktion, Clustering, Bereiche, Verknüpfung, Polyphonie, ein erster Schnitt des Plugins und der MCP-Server. Geplant sind der Abgleich mit der Gliederung einer Hausarbeit, ein automatischer Import über Hooks und die Übernahme eines Zettels als eigene Permanenz direkt aus dem Plugin.
