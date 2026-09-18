# Abschlussarbeit

## Projektbeschreibung

Dieses Projekt enthält eine bestehende ToDo-Applikation mit Node.js.

Für die Abschlussaufgabe wird die Anwendung zuerst lokal eingerichtet und getestet. Anschließend wird die Anwendung mit Docker containerisiert und mit Docker Compose verwaltet.

Zusätzlich werden Git und GitHub für die Versionierung und Veröffentlichung des Projekts verwendet.

---

## Voraussetzungen

Für die Verwendung des Projekts werden folgende Programme benötigt:

-   Node.js
-   Git
-   Docker
-   GitHub
-   Visual Studio Code

---

## Repository klonen

Zuerst wird das Repository von GitHub geklont.

git clone https://github.com/RayanBlanco/docker-nodejs-sample.git

## Pakete installieren

Damit die Anwendung funktioniert, müssen zuerst die benötigten Node.js-Abhängigkeiten installiert werden.

Dazu wird folgender Befehl ausgeführt:

npm install

Die benötigten Pakete werden anhand der Datei package.json installiert.

Die Datei package-lock.json sorgt dafür, dass die verwendeten Paketversionen nachvollziehbar und reproduzierbar sind.

## Anwendung lokal starten

Nach der Installation der Abhängigkeiten kann die Anwendung gestartet werden.

npm start

Der Startbefehl ist in der package.json im Bereich scripts definiert.

Beispielsweise:

"scripts": {
"start": "node src/index.js"
}

Nach dem Start kann die Anwendung im Browser geöffnet werden.

Beispiel:

http://localhost:3000

## Docker-Image erstellen

Bevor die Anwendung in einem Container gestartet werden kann, muss zuerst ein Docker-Image erstellt werden.

Das Image wird mit folgendem Befehl erstellt:

docker build -t todo-app .

Dabei bedeutet:

docker build erstellt ein neues Docker-Image.
-t todo-app gibt dem Image den Namen todo-app.
. verwendet das aktuelle Verzeichnis als Build-Kontext.

Das Dockerfile enthält die Anweisungen, die Docker für den Aufbau des Images benötigt.

Das erstellte Image kann anschliessend überprüft werden:

docker image ls

## Anwendung mit Docker starten

Anwendung mit Docker Compose starten

Docker Compose ermöglicht es, die Konfiguration der Anwendung in einer compose.yaml-Datei festzulegen.

Beispiel für die Konfiguration:

services:
todo:
build:
context: .
ports: - "3000:3000"

Die Anwendung kann anschliessend mit folgendem Befehl gestartet werden:

docker compose up --build

Docker Compose erstellt dabei das Image und startet anschliessend den Container.

Die Anwendung kann danach wieder unter

http://localhost:3000

aufgerufen werden.

Um die Anwendung im Hintergrund zu starten, kann -d verwendet werden:

docker compose up -d

Der Status kann mit folgendem Befehl überprüft werden:

docker compose ps

## Anwendung stoppen

Wenn die Anwendung mit Docker Compose gestartet wurde, kann sie mit folgendem Befehl gestoppt werden:

docker compose down

Dadurch werden die von Docker Compose erstellten Container beendet und entfernt.

Wenn ein Container mit docker run gestartet wurde, kann dieser beispielsweise mit folgendem Befehl gestoppt werden:

docker stop todo-container

Anschliessend kann der Container entfernt werden:

docker rm todo-container

Das Docker-Image bleibt dabei weiterhin vorhanden.
