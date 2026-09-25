# Formica: Ameisenalgorithmus-Simulator

Ein interaktiver Simulator für Ameisenalgorithmen im Browser. Eine einzelne Datei, keine Abhängigkeiten, kein Build. `index.html` im Browser öffnen, fertig.

## Modi

**Kolonie:** Futtersuche mit Stigmergie. Jede Ameise tastet mit drei Fühlern zwei Pheromonfelder ab:
Heimweg-Pheromon (auf der Suche abgelegt) und Futter-Pheromon (auf dem Rückweg mit Futter abgelegt).
Die Felder verdunsten und diffundieren, sodass nur häufig genutzte Wege bestehen bleiben.

- Szenarien: *Offenes Feld*, *Doppelbrücke* (nach Deneubourg et al., 1990) und ein zufälliges *Labyrinth*
- Werkzeuge: Futter malen, Wände ziehen, radieren, Nest versetzen
- Einstellbar: Anzahl Ameisen (bis 4000), Tempo, Fühlerwinkel und -reichweite, Zufallsanteil, Verdunstung, Diffusion

**Rundreise (TSP):** Ant Colony Optimization für das Problem des Handlungsreisenden.

- Varianten: Ant System, Elitäres Ant System, MAX-MIN Ant System
- Parameter α, β, ρ, Ameisen pro Iteration, Iterationen pro Sekunde
- Karten: zufällig, Cluster oder Kreis (beim Kreis ist das Optimum bekannt und wird zum Vergleich angezeigt)
- Städte per Klick setzen, per Shift-Klick oder Rechtsklick entfernen
- Konvergenzdiagramm mit bester und mittlerer Tourlänge sowie der Nächster-Nachbar-Tour als Referenz

## Tastatur

- `Leertaste`: Pause / Weiter
- `R`: Neustart
