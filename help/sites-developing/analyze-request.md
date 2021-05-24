---
title: Anfragenanalyse-Skript
seo-title: Anfragenanalyse-Skript
description: Das Anfragenanalyse-Skript vereinfacht die Analyse der access.log-Dateien und erzeugt einen lesbaren Bericht für die spätere Verarbeitung.
seo-description: Das Anfragenanalyse-Skript vereinfacht die Analyse der access.log-Dateien und erzeugt einen lesbaren Bericht für die spätere Verarbeitung.
uuid: 24eff3c6-5748-46f3-a30c-4a3a6427ce1d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: 1b5e0ccf-4157-45e3-8caf-1d6739d7d9d2
exl-id: e14a9cda-890f-46b7-9433-1b52eb91eae3
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 47%

---

# Anfragenanalyse-Skript{#request-analysis-script}

## Download {#download}

Dieses Skript wurde erstellt, um die Analyse der `access.log`-Dateien zu vereinfachen, die einen lesbaren Bericht für die spätere Verarbeitung erzeugen.

[Datei laden](assets/analyse-access.sh)

## Beschreibung {#description}

Dieses Skript wurde erstellt, um die Analyse der `access.log`-Dateien zu vereinfachen, die einen lesbaren Bericht für die spätere Verarbeitung erzeugen.

Es liefert die Gesamtzahl an Anfragen, einen Vergleich zwischen GET und POST, die Anfrageverteilung über einen Zeitraum hinweg usw.

Die Ausgabe erfolgt in Markdown-Syntax. Daher ist es einfacher, sie mit Tools wie Pandoc in PDF-Dateien zu konvertieren oder in einem Browser mit Plug-ins wie Markdown-Viewer anzuzeigen.

Sie kann einen benutzerdefinierten Pfad analysieren, der in der Befehlszeile angegeben ist.

Ausgehend von dem Kommentar in der Datei, der angibt, wie Sie sie ausführen:

Analysieren Sie CQ `access.log` extrapolieren Sie verschiedene Informationen und erzeugen Sie eine Markdown-Ausgabe auf `stdout`.

## Nutzung {#usage}

`./analyse-access.sh access.log.2013-&ast;`

Sie können zusätzliche benutzerdefinierte Pfade für die Analyse in der Befehlszeile angeben

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

Sie können die Ausgabe durch einfaches Piping speichern

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`
