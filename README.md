# GrafanaExample
Beispiel für InfluxDB + Grafana mit Feed von Homematic / RedNode

# Anleitung 

## Docker

### docker-compose-Datei anpassen:

* Jeweils in den Volumes-Abschnitten den Teil VOR dem Doppelpunkt **anpassen** und das **Verzeichnis anlegen** (hier werden die Daten gespeichert). Der Teil nach dem Doppelpunkt ist das entsprechende Verzeichnis innerhalb des Containers (nicht ändern).

* Für InfluxDB die Initialen Logindaten ändern

        - DOCKER_INFLUXDB_INIT_USERNAME=USER    
        - DOCKER_INFLUXDB_INIT_PASSWORD=PASSWORD

### Container starten:

Via Web-Interface falls in der Diskstation möglich oder per Befehl in der Kommandozeile:

    docker-compose up -d

## Einrichten von InfluxDB und Grafana

(Aus dem Kopf versucht zu reproduzieren)

Influxdb ist unter http://SERVERIP:8086 erreichbar und wird beim ersten Aufruf eingerichtet. 

Grafana ist unter http://SERVERIP:3000 erreichbar und wird beim ersten Aufruf eingerichtet inkl. Vergabe des Kennwort.

In InfluxDB muss ein API-Key eingerichtet werden, mit dem Grafana auf InfluxDB zugreift.

Die Container haben ein gemeinsames virtuelles Netzwerk. Grafana findet InfluxDB unter http://influxdb:8086

## NodeRed

Der Flow findet sich unter NodeJS-Flow.json und kann im Menüpunkt "Importieren" importiert werden. Die IP des Servers und der API-Key müssen angepasst werden.

## Next Steps

Bei Bedarf noch automatische Updates für die Container konfigurieren, indem zusätzlich der Watchtower-Container gestartet wird. Dieser Prüft alle 24h, ob Updates für die Container bereitstehen und aktualisiert bei Bedarf. Das Vorgehen ist analog zu den Grafana- und InfluxDB-Containern.
