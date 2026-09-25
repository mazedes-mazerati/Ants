# Refraktor

Echtzeit-Simulation von Lichtbrechung in Glas und Wasser – als Animation und als Kamera-Filter fürs iPhone.
Eine einzige Datei (`index.html`), keine Abhängigkeiten, läuft komplett auf der GPU (WebGL2).

## Modi

**Animation** – ein physikalisch basierter Raytracer:

- Objekte: Wasser (Pool), Glaskugel, Prisma, Linse, Diamant (Brillantschliff), Glasring, Würfel auf der Spitze, gedrehte Skulptur
- Wellen: glatt, Dünung, Wind, Regen, Sturm, Interferenz – Tippen aufs Wasser lässt Tropfen fallen
- Untergrund: Stein, Holz, Schach, Pool-Fliesen, Sand
- **Echte Kaustiken**: Hunderttausende Sonnenstrahlen werden pro Frame einzeln durch Glas bzw. Wasseroberfläche verfolgt und auf dem Boden gesammelt (Photon-Splatting, zeitlich akkumuliert). Dadurch entstehen Brennpunkte, Lichtnetze am Poolboden und Regenbögen hinter dem Prisma.
- **Dispersion**: bis zu 8 Wellenlängen pro Pixel mit Brechungsindex nach Cauchy (`n_F − n_C`, Abbe-Zahl wird angezeigt)
- Fresnel-Reflexion, Totalreflexion, Absorption nach Beer-Lambert (Tönungen: Klar, Aqua, Smaragd, Bernstein, Rosé, Kobalt)
- **Dunkelkammer mit Lichtstrahl**: schmaler Lichtspalt im dunklen Raum, sichtbarer Strahl – das klassische Prisma-Spektrum

**Kamera** – die Rückkamera (oder Frontkamera) wird durch eine simulierte Glasscheibe gefiltert:

Wasser, Regen am Fenster (mit beschlagener Scheibe und laufenden Tropfen), Riffelglas, Hammerschlag, Glasbausteine,
Facetten, Prisma (mit Regenbogen-Lichtstreifen), Glaskugel (umgedrehtes Bild), Kristall, Wellenglas.
Ziehen verschiebt Kugel/Prisma/Kristall. Auslöser speichert ein Foto (Teilen-Menü bzw. Download).
Ohne Kamera funktioniert der Filter auch mit einem eigenen Bild oder dem Beispielbild.

**Licht** – ein Tageszeit-Regler von 4:00 bis 22:30 steuert Sonnenstand, Himmelsfarben, Dunst und Farbstimmung:
Dämmerung, Morgen (kühler, dunstiger), Mittag, Goldene Stunde, Sonnenuntergang, Blaue Stunde, Nacht (Mondlicht, Sterne).
Dazu HDR-Rendering mit Bloom, filmischem Tonemapping, Vignette und Filmkorn.

## Aufs iPhone bringen

Die Kamera funktioniert im Browser nur über **HTTPS**. Am einfachsten mit GitHub Pages:

1. Im Repository auf GitHub: **Settings → Pages**
2. Unter „Build and deployment“: Source **Deploy from a branch**, Branch auswählen (z. B. `main` oder diesen Branch), Ordner `/ (root)`, speichern
3. Nach ein bis zwei Minuten ist die Seite unter `https://<benutzer>.github.io/<repo>/` erreichbar
4. Auf dem iPhone in Safari öffnen, auf **Kamera** tippen und den Zugriff erlauben
5. Optional: Teilen → **Zum Home-Bildschirm** – dann startet Refraktor im Vollbild wie eine App

`…/index.html#kamera` öffnet direkt im Kamera-Modus.

Lokal testen geht mit jedem statischen Server, z. B. `python3 -m http.server` und dann `http://localhost:8000`
(localhost gilt als sicher, dort funktioniert auch die Kamera).

## Bedienung

| Geste | Animation | Kamera |
| --- | --- | --- |
| Ziehen | Kamera um das Objekt drehen | Glaskugel / Prisma / Kristall verschieben |
| Pinch / Mausrad | Zoom | Größe der Struktur |
| Tippen | Tropfen ins Wasser | Welle (Struktur „Wasser“) |

Die Qualität (Schnell / Ausgewogen / Maximal) legt Auflösung, Anzahl der Wellenlängen und Photonen fest.
Wenn das Gerät nicht hinterherkommt, senkt Refraktor die Auflösung automatisch.
