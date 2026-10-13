---
title: Anfragenanalyse-Skript
description: Das Anfragenanalyse-Skript vereinfacht die Analyse der access.log-Dateien und erzeugt einen lesbaren Bericht für die spätere Verarbeitung.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
exl-id: e14a9cda-890f-46b7-9433-1b52eb91eae3
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 100%
---
# Anfragenanalyse-Skript{#request-analysis-script}

## Download {#download}

Dieses Skript vereinfacht die Analyse der `access.log`-Dateien und erzeugt einen lesbaren Bericht für die spätere Verarbeitung.

[Datei laden](assets/analyse-access.sh)

## Beschreibung {#description}

Dieses Skript vereinfacht die Analyse der `access.log`-Dateien und erzeugt einen lesbaren Bericht für die spätere Verarbeitung.

Es liefert die Gesamtzahl der Anfragen, einen Vergleich zwischen GET und POST, die Anfrageverteilung über einen Zeitraum hinweg usw.

Die Ausgabe erfolgt in Markdown-Syntax. Somit lässt sie sich einfacher mit Tools wie Pandoc in PDF-Dateien umwandeln oder mit einem Plug-in wie Markdown Viewer in einem Browser anzeigen.

Das Skript kann auch einen benutzerdefinierten Pfad analysieren, der in der Befehlszeile angegeben wird.

Im Kommentar in der Datei finden Sie Angaben zur Ausführung:

Analysieren Sie die Datei `access.log` von CQ. Dabei werden verschiedene Daten extrapoliert und eine Markdown-Ausgabe wird auf `stdout` erstellt.

## Nutzung {#usage}

`./analyse-access.sh access.log.2013-&ast;`

Sie können zusätzliche benutzerdefinierte Pfade für die Analyse in der Befehlszeile angeben

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

Sie können die Ausgabe durch einfaches Piping speichern

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`
