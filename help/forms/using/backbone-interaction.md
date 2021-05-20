---
title: Interaktion mit Backbone
seo-title: Interaktion mit Backbone
description: Grundlegende Informationen zur Verwendung von Backbone JavaScript-Modellen in AEM Forms Workspace.
seo-description: Grundlegende Informationen zur Verwendung von Backbone JavaScript-Modellen in AEM Forms Workspace.
uuid: 040f42cb-3b76-4657-ba05-9e52647efb12
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 538591fe-29e4-40c4-a045-06095cc0c6b8
docset: aem65
exl-id: 8fd9770b-6ec4-4b09-b6b2-47a5e5d40f79
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 81%

---

# Interaktion mit Backbone{#backbone-interaction}

Backbone ist eine Bibliothek, die das Erstellen und Verfolgen von MVC-Architektur in Webanwendungen unterstützt. Die Grundidee von Backbone ist, Ihre Benutzeroberfläche in logischen Ansichten zu organisieren, unterstützt von Modellen, die bei Modelländerungen jeweils einzeln aktualisiert werden können, ohne dass die Seite neu gezeichnet werden muss. Weitere Informationen zu Backbone finden Sie unter [https://backbonejs.org](https://backbonejs.org/).

Einige Hauptkonzepte sind die folgenden:

**Backbone** modelEnthält Daten und den Großteil der Logik, die sich auf diese Daten bezieht.

**Backbone** viewWird verwendet, um den Status des entsprechenden Modells darzustellen. Eine Backbone-Ansicht verhält sich im Prinzip wie ein Controller, der Benutzeroberflächenereignisse wie Benutzerklicks oder Modellereignisse (wie Datenänderungen) erfasst und die Benutzeroberfläche entsprechend ändert.

**HTML** templateEine Wrapper-Vorlage mit Platzhaltern, die vom Modell aufgefüllt werden.

**AEM Forms** WorkspaceEnthält mehrere einzelne Komponenten. Jede Komponente:

* Stellt ein einzelnes logischen Element der Benutzeroberfläche dar.
* Kann eine Sammlung ähnlicher Komponenten sein.
* Erstellt aus Backbone-Modell, Backbone-Ansicht und HTML-Vorlage.
* Enthält Verweis zu einem Dienst.
* Enthält Verweis zu erforderlichen Dienstprogrammen.

Wenn eine Komponente initialisiert wurde, werden folgende Objekte erstellt:

* Eine neue Instanz des Backbone-Modells für die Komponente wird erstellt. Dienst wird ins Modell injiziert.
* Eine neue Instanz der Backbone-Ansicht wird erstellt.
* Instanz des entsprechenden Modells, HTML-Vorlage und Dienstprogramme werden in die Ansicht injiziert.

In der Backbone-Ansicht gibt es eine Ereigniszuordnung für die verschiedenen Ereignisse, die durch Benutzeroberflächeninteraktionen mit einem entsprechenden Handler auftreten können. Diese Zuordnung wird ausgelöst, wenn eine Komponente initialisiert wird.

Wenn eine Ansicht initialisiert wird, ruft die Ansicht das entsprechende Modell zum Datenabruf vom Server auf. Nachdem alle für eine Ansicht erforderlich Daten verfügbar sind, gibt die Ansicht die Daten in dem Format wieder, das in der HTML-Vorlage angegeben ist. Mehrere Ansichten können dasselbe Modell für die Kommunikation nutzen.

![](do-not-localize/aem_forms_workflow.png)

Ein Beispiel:

1. Benutzer klickt in der Aufgabenliste auf eine Aufgabenvorlage.
1. Aufgabenansicht erfasst den Klick und ruft Renderfunktion im Aufgabenmodell auf.
1. Das Aufgabenmodell ruft anschließend den Dienst auf, der ein gemeinsamer Punkt für die gesamte Kommunikation mit dem AEM Forms-Server ist.
1. Die Dienstklasse ruft den AEM Forms REST-Endpunkt für die Rendermethode über Ajax auf.
1. Der Erfolgsrückruf für diesen Ajax-Aufruf wird im Aufgabenmodell definiert.
1. Aufgabenmodell erstellt ein Backbone-Ereignis als Benachrichtigung, dass der Renderaufruf abgeschlossen ist.
1. Eine andere Ansicht, die Aufgabendetailansicht, überwacht dieses Ereignis des Aufgabenmodells.
1. Aufgabendetailansicht ändert dann die Aufgabendetailvorlage, um die gerenderte Aufgabe (Formular, Details, Anlagen, Hinweise usw.) für den Benutzer anzuzeigen.
