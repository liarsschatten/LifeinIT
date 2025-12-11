# Allgemeine Erklärung zu Containern
Ein Container ist ein vom Hauptsystem getrenntes Programm welches einen bestimmten Dienst bereitstellt. Container sind leicht aufzusetzen und daher für Mikro Services und Applikationstests sehr gut geeignet. Es erlaubt das schnelle austauschen von Services ohne die Daten zu verändern.
Ein Programm welches auf Container spezialisiert ist ist Docker.
# Docker Befehle
Alle Docker Befehle müssen mit Root Rechten ausgeführt werden
## Docker Run
Erstellt und startet einen neuen Container
```sh
docker run --name Name-der-Instanz -d -p Port-des-Hosts:Port-des-Container name-des-images
```

- -d startet den Docker im HIntergrund
- -p gibt an welcher Port vom Host zum Hauptport des Containers geht
Man kann beliebig viele Instanzen des selben Docker erstellen
## Docker Start
Startet einen bereits existierenden Docker
```sh
docker start Container-Name
```
## Docker Volume
```sh 
docker volume create Volume-Name
```