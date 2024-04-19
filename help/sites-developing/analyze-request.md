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
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 93%

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

Analysieren von CQ `access.log` Hochladen verschiedener Informationen und Generieren einer Markdown-Ausgabe auf `stdout`.

## Nutzung {#usage}

`./analyse-access.sh access.log.2013-&ast;`

Sie können zusätzliche benutzerdefinierte Pfade für die Analyse in der Befehlszeile angeben

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

Sie können die Ausgabe durch einfaches Piping speichern

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`
