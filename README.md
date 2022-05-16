# Heizgradtage pro Schweizer Gemeinde

## Kurzbeschrieb
Die drei nachfolgenden Jupyter-Notebooks berechnen pro Gemeinde die Heizgradzahl. Die Berechnungen werden auf Basis von den 2km-Raster Temperaturdaten pro Monat (gemittelt von den Jahren 1991-2020) berechnet.<br>

[1 Daten Laden](/1_DatenLaden.ipynb)<br>
[2 Daten Aufbereiten](2_DatenAufbereiten.ipynb)<br>
[3 Resultate Ploten](4_Resultate_Ploten.ipynb)

## Motivation
In der Schweiz fallen rund 23.9 % (Jahr 2020) der Treibhausgase im Bereich Gebäude an. Quelle: https://www.bafu.admin.ch/bafu/de/home/themen/klima/zustand/daten/treibhausgasinventar/gebaeude.html
Dadurch steigt das Bedürfnis, die Heizanlage zu optimieren und bei Neuanschaffung einen möglichst effizienten Betrieb zu garantieren. Bei Neu- oder Umbau der Heizanlage werden Informationen zum potenziellen Heizbedarf benötigt.
Für die Nebenkostenabrechnung wird die Heizgradzahl gebraucht, um den Mietern eine möglichst genaue Nebenkostenabrechnung ohne übertriebenen Aufwand ausstellen. Damit man dies auch bei Mieterwechsel möglichst genau berechnen kann, ist die Information zum Bedarf von Heizenergie pro Monat wichtig. 
In der Schweiz wird die Kennzahl „Heizgradtage“ für diese Problemstellungen verwendet. Diese Kennzahl ist öffentlich nur für wenige Orte verfügbar. In dieser Arbeit werden diese Heizgradtage pro Gemeinde berechnet. 

![Heizgradtage pro Gemeinde](/data/plot.png?raw=true "Heizgradtage pro Gemeinde")

## Methode
1.	Die Gemeindedaten sind im LV95 Format. Sie werden ins WGSS84 Format umgewandelt.
2.	Die Raster-Temperatur-Daten werden in ein verarbeitbares Format konvertiert.
3.	Es werden pro Gemeinde vier Koordinaten (Länge- und Breitegrad) im WGS84 Format berechnet, welche die Eckpunkte eines Fenster repräsentieren. 
4.	Jeder Gemeinde werden alle in diesem Fenster vorhanden Raster-Temperatur-Daten zugewiesen.
5.	Diese Temperatur-Raster-Daten werden so aggregiert (Mittelwert), dass man pro Gemeinde und Monat ein Temperatur-Mittelwert erhält
6.	Berechnung der Heizgradtage pro Gemeinde und Monat berechnet. Weil es sich um Monatsnormtemperaturen handelt, wird die Temperaturdifferenz mit 30 (vereinfachte Berechnung für einen Monat) multipliziert.
7.	Aggregation der Daten pro Gemeinde und Jahr
8.	Die Namen der Messstationen werden angepasst, damit sie in einem nächsten Schritt mit den entsprechenden Gemeinde verglichen werden können.
9.	Es wird eine absolute und relative Differenz zwischen den berechneten Heizgradtage vom Schritt 1 und dem vom Hauseigentümerverband publizierten Heizgradtage berechnet.


## Daten
1. Metadaten zu den Gemeinden (Position, Höhenlage etc.)
Quelle: Bundesamt für Statistik
URL: https://www.bfs.admin.ch/bfs/de/home/dienstleistungen/geostat/geodaten-bundesstatistik/administrative-grenzen/generalisierte-gemeindegrenzen.assetdetail.21224783.html

2. Gemittelte Temperatur-Rasterdaten (2km) pro Monat für die Jahre 1991-2020
Quelle: Meteo Schweiz
URL: https://www.meteoschweiz.admin.ch/content/dam/meteoswiss/de/Ungebundene-Seiten/Produkte/doc/tnorm9120.zip​

3. Metadaten zu den Messstationen von Meteo Schweiz (z.B geografische Position, Höhenlage)​
Quelle: Geoportal des Bundes
URL: https://data.geo.admin.ch/ch.meteoschweiz.messnetz-automatisch/ch.meteoschweiz.messnetz-automatisch_de.csv​

4. Heizgradtage für einzelne Ortschaften, die mit den Messstationen aus dem dritten Datensatz übereinstimmen. Die Heizgradtage werden benötigt, um die im Projekt erarbeiteten Resultate zu verifizieren.
Quelle: HEV Schweiz
URL: https://www.hev-schweiz.ch/vermieten/nebenkostenabrechnungen/heizgradtage-hgt/

Autoren:
Adrian Rupp, 
