---
title: Wie kann der Service „execute script“ aus der Workbench von AEM Forms on JEE zum Erstellen von XML-Daten verwendet werden?
description: Verwenden des Service „execute script“ aus der Workbench von AEM Forms on JEE zum Erstellen von XML-Daten
exl-id: 2ec57cd4-f41b-4e5c-849d-88ca3d2cfe19
source-git-commit: de38dbb9d0ce523543c11e665c02034f4b38f1e6
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 100%

---

# Verwenden des Service „execute script“ in AEM Forms on JEE Workbench zum Erstellen von XML-Daten {#using-execute-script-service-forms-jee-workbench}

Viele Prozess-Management-Workflows für AEM Forms on JEE beinhalten XML. XML-Informationen können zum Beispiel in einem Prozess erstellt und an ein Flex-Programm im Arbeitsbereich von AEM Forms on JEE gesendet oder für Systemeinstellungen verwendet werden oder mittels XML können Informationen an und von Formularen übergeben werden. Es gibt viele Fälle, in denen ein Entwickler für AEM Forms on JEE XML verwalten muss. Häufig muss dazu die XML über einen AEM Forms on JEE-Prozess verwaltet werden.

Bei einfachen XML-Einstellungen kann der Service `Set Value` verwendet werden. Es handelt sich dabei um einen Standard-Service von AEM Forms on JEE. Dieser Service legt den Wert eines oder mehrerer Datenelemente im Prozessdatenmodell fest. Für Szenarien mit einer sehr einfachen bedingten „if this, then that“-Logik kann dieser Service den Zweck erfüllen.

In komplexeren Situationen ist der Service „Set Value“ jedoch nicht so effektiv. In diesen Situationen muss man sich auf einen robusteren Satz von Programmierbefehlen verlassen, wie sie beispielsweise eine Programmiersprache wie Java bietet. Die Verwendung von Java zum Erstellen komplexer XML-Dateien kann viel einfacher und klarer sein als das Erstellen eines XML-Dokuments aus einfachem Text im Service „Set Value“. Darüber hinaus ist es einfacher, bedingte Programmierung in Java als in den Service „Set Value“ einzubinden.

## Verwenden des Service „Execute Script“ in einem Prozess {#using-execute-script-service-in-process}

Zum Satz der Standard-Services von AEM Forms on JEE, die in der Workbench von AEM Forms on JEE verfügbar sind, gehört der Service `Execute Script`. Dieser Service ermöglicht die Ausführung von Skripten in Prozessen und stellt hierzu den Vorgang `executeScript` bereit.

### Erstellen eines Programms und eines Prozesses mit dem als Aktivität definierten Service „Execute Script“ {#create-an-application}

Die allgemeine Erstellung von Programmen und Prozessen ist nicht Gegenstand dieses Tutorials, aber für diese Anleitung haben wir ein Programm namens „DemoApplication02“ erstellt. Wenn ein Programm bereits erstellt wurde, müssen wir in diesem Programm einen Prozess erstellen, um den executeScript-Service aufzurufen. So fügen Sie dem Programm einen Prozess hinzu, der den Service `Execute Script` beinhaltet:

1. Klicken Sie mit der rechten Maustaste auf das Programm und wählen Sie [!UICONTROL Neu]. Wählen Sie im ausklappbaren Menü [!UICONTROL Neu] die Option [!UICONTROL Prozess]. Benennen Sie den Prozess entsprechend, fügen Sie bei Bedarf eine Beschreibung hinzu und wählen Sie das Symbol aus, das diesen Prozess darstellen soll. Für dieses Tutorial haben wir einen Prozess erstellt und ihn `executeScriptDemoProcess` genannt.
1. Definieren Sie die Startpunkte oder entscheiden Sie sich einfach, die Startpunkte später hinzuzufügen.
1. Der Prozess wird jetzt erstellt und sollte automatisch im Fenster [!UICONTROL Prozess-Design] geöffnet werden. Klicken Sie hier oben im Fenster „Prozess-Design“ auf das Symbol für die Aktivitätsauswahl und ziehen Sie die neue Aktivität auf die Bahn. Zu diesem Zeitpunkt sollte das Fenster [!UICONTROL Aktivität definieren] angezeigt werden (siehe Abbildung unten).
   ![Aktivität definieren](assets/define-activity.jpg)
1. Der executeScript-Service befindet sich unter der Gruppe `Foundation` der Services. Unter „Services“ wird das Objekt als `Execute Script – 1.0` mit dem Vorgangsnamen `executeScript` aufgeführt. Wählen Sie dieses Element aus, indem Sie darauf klicken.
1. Dieser Prozess sollte jetzt erstellt werden. Standardmäßig sollte das Fenster [!UICONTROL Prozesseigenschaften] im linken Bereich angezeigt werden.

#### Hinzufügen eines Skripts zum Prozess mit dem Service „Execute Script“ {#add-script-to-process-with-execute-script}

Nachdem der Prozess mit der definierten Aktivität „Execute Script“ erstellt wurde, kann diesem Prozess ein Skript hinzugefügt werden. So fügen Sie diesem Prozess ein Skript hinzu:

1. Navigieren Sie zur Palette [!UICONTROL Prozesseigenschaften]. Erweitern Sie in dieser Palette den Abschnitt [!UICONTROL Eingabe] und klicken Sie auf das Symbol „...“.

1. Schreiben Sie Ihr Skript in das angezeigte Textfeld. Wenn das Skript vollständig eingegeben wurde, wählen Sie „OK“ (siehe Abbildung unten).
   ![Execute Script](assets/execute-script.jpg)

## Erstellen von XML mit dem Service „Execute Script“ {#create-xml-execute-script-service}

Nachdem ein Prozess, der den Service „Execute Script“ enthält, erstellt wurde, kann dieses Skript zur Erstellung von XML verwendet werden. Sie würden die unten beschriebenen Skripte in das Textfeld eingeben, das im Abschnitt „Hinzufügen eines Skripts zum Prozess mit dem Service `Execute Script`“ weiter oben beschrieben wurde.

**Über die Technologie des Service „Execute Script“**

Um zu wissen, welche Funktionen und Einschränkungen der Service „Execute Script“ hat, müssen Sie die technologischen Grundlagen des Service kennen. AEM Forms on JEE verwendet den Parser Apache Xerces Document Object Model (DOM), um XML-Variablen in Prozessen zu erstellen und zu speichern. Xerces ist eine Java-Implementierung der W3C-Spezifikation von Document Object Model, deren Definition [hier](https://dom.spec.whatwg.org/) zu finden ist. Die DOM-Spezifikation ist ein Standardverfahren zur Bearbeitung von XML, das seit 1998 existiert. Die Java-Implementierung von Xerces, Xerces-J, unterstützt DOM Level 2 Version 1.0.

Die Java-Klassen, die zum Speichern von XML-Variablen verwendet werden, sind:

* org.apache.xerces.dom.NodeImpl und

* org.apache.xerces.dom.DocumentImpl

DocumentImpl ist eine Unterklasse von NodeImpl. Daher kann angenommen werden, dass jede XML-Prozessvariable eine NodeImpl-Ableitung ist. Die Dokumentation für NodeImpl finden Sie [hier](http://xerces.apache.org/xerces-j/apiDocs/org/apache/xerces/dom/NodeImpl.html).

**Beispiel für die XML-Erstellung mit dem Service „Execute Script“**

Im Folgenden finden Sie ein Beispiel für das Erstellen von XML in einem Service „Execute Script“. Der Prozess verfügt über eine Variable, einen Knoten, der vom Typ XML ist. Das Endergebnis dieser Aktivität ist ein XML-Dokument. Was dieses Dokument tut oder wie es auf den gesamten Prozess angewendet wird, ist für dieses Tutorial nicht relevant. Letztlich geht es darum, was XML im übergeordneten Programm tun muss. Wie in der Einführung erwähnt, kann XML in AEM Forms on JEE-Formularen und -Prozessen für viele Zwecke verwendet werden. Dies ist lediglich eine Erklärung dafür, wie die Aktivität „Execute Script“ kodiert wird, um ein einfaches XML-Dokument auszugeben.

Ein einfaches Java-Skript zur Ausgabe von XML würde in etwa wie folgt aussehen:

```xml
import org.apache.xerces.dom.DocumentImpl;

import org.w3c.dom.Document;

import org.w3c.dom.Element;



Document document = new DocumentImpl();

Element topLevelResources = document.createElement("resources");

Element resource = document.createElement("resource");

resource.setAttribute("id", "first item id");

resource.setAttribute("value", "first item value");

topLevelResources.appendChild(resource);

document.appendChild(topLevelResources);

patExecContext.setProcessDataValue("/process_data/node", document);
```

>[!NOTE]
>
>dass die oben genannten DOM-Objekte in das Skript importiert werden müssen.

Das Ergebnis dieses einfachen Skripts ist ein neues XML-Dokument mit einem Variablenknoten, der auf Folgendes festgelegt ist:

```xml
<resources>

<resource id="first item id" value="first item value"/>

</resources>
```

**Verwenden einer iterativen Schleife zum Hinzufügen von Knoten zur XML-Datei**

Knoten können auch innerhalb des Prozesses zu einer vorhandenen XML-Variablen hinzugefügt werden. Die Variable, der Knoten, enthält das soeben erstellte XML-Objekt.

```xml
Document document = patExecContext.getProcessDataValue("/process_data/node");

NodeList childNodes = document.getChildNodes();

int numChildren = childNodes.getLength();

for (int i = 0; i < numChildren; i++)

{

Node currentChild = childNodes.item(i);

if (currentChild.getNodeType() == Node.ELEMENT_NODE)

{

// found the top level node

Element newResource = document.createElement("resource");

newResource.setAttribute("id", "second item id");

newResource.setAttribute("value", "second item value");

currentChild.appendChild(newResource);

break;

}

}

patExecContext.setProcessDataValue("/process_data/node", document);
The variable node in the XML is now set to:

<resources> 

<resource id="first item id" value="first item value"/> 

<resource id="second item id" value="second item value"/> 

</resources>
```
