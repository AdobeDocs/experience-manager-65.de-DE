---
title: Wie kann der execute-Skriptdienst in AEM Forms on JEE Workbench zum Erstellen von XML-Daten verwendet werden?
description: Verwenden des Execute-Script-Dienstes in AEM Forms on JEE Workbench zum Erstellen von XML-Daten
source-git-commit: 730ae7cd6cd04eb6377b37eafe29db597e93cce3
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 0%

---

# Verwenden des Execute-Script-Dienstes in AEM Forms on JEE Workbench zum Erstellen von XML-Daten {#using-execute-script-service-forms-jee-workbench}

Es gibt viele XML-Vorgänge, die mit AEM Forms on JEE-Prozess-Management-Workflows verbunden sind, z. B.: XML-Informationen können in einem Prozess erstellt und an eine Flex-Anwendung in AEM Forms on JEE Workspace gesendet werden, für Systemeinstellungen verwendet werden oder Informationen an und von Formularen übergeben werden. Es gibt viele Instanzen, in denen ein AEM Forms on JEE-Entwickler XML verwalten muss. Dies erfordert oft, dass die XML über einen AEM Forms on JEE-Prozess verwaltet wird.

Bei der Arbeit mit einfachen XML-Einstellungen kann der Dienst `Set Value` verwendet werden, der ein standardmäßiger AEM Forms on JEE-Dienst ist. Dieser Dienst legt den Wert eines oder mehrerer Datenelemente im Prozessdatenmodell fest. Bei sehr einfachen bedingten Logikszenarios mit dem Namen &quot;if this, then that&quot; kann dieser Dienst dem Zweck entsprechen.

In komplexeren Situationen ist der Set Value-Dienst jedoch nicht so effektiv. In diesen Situationen muss man sich auf einen robusteren Satz von Programmierbefehlen verlassen, wie z. B. die, die von einer Programmiersprache wie Java bereitgestellt werden. Die Verwendung von Java zum Erstellen komplexer XML-Dateien kann viel einfacher und klarer sein als das Erstellen eines XML-Dokuments aus einfachem Text innerhalb des Set Value-Dienstes. Darüber hinaus ist es einfacher, bedingte Programmierung in Java als in einen Set Value-Dienst einzubinden.

## Verwenden des Execute Script-Dienstes in einem Prozess {#using-execute-script-service-in-process}

Im Satz der standardmäßigen AEM Forms on JEE-Dienste, die in AEM Forms on JEE Workbench verfügbar sind, befindet sich der Dienst `Execute Script`. Mit diesem Dienst können Sie Skripte in Prozessen ausführen und den `executeScript`-Vorgang bereitstellen.

### Erstellen einer Anwendung und eines Prozesses mit dem Dienst &quot;Execute Script&quot;, der als Aktivität definiert ist {#create-an-application}

Die allgemeine Anwendungs- und Prozesserstellung ist für dieses Tutorial nicht relevant, aber um dieser Anleitung willen haben wir eine Anwendung namens &quot;DemoApplication02&quot;erstellt. Wenn eine Anwendung bereits erstellt wurde, müssen wir in dieser Anwendung einen Prozess erstellen, um den executeScript-Dienst aufzurufen. So fügen Sie einen Prozess zur Anwendung hinzu, der den Dienst `Execute Script` enthält:

1. Klicken Sie mit der rechten Maustaste auf Ihre Anwendung und wählen Sie [!UICONTROL Neu] aus. Wählen Sie im Menü [!UICONTROL Neu] die Option [!UICONTROL Prozess]. Benennen Sie den Prozess entsprechend, fügen Sie bei Bedarf eine Beschreibung hinzu und wählen Sie das Symbol aus, das diesen Prozess darstellen soll. Für die Zwecke dieses Tutorials haben wir einen Prozess erstellt und diesen mit `executeScriptDemoProcess` bezeichnet.
1. Definieren Sie Ihre Startpunkte oder einfach entscheiden Sie sich, Ihre Startpunkte später hinzuzufügen.
1. Der Prozess wird jetzt erstellt und sollte automatisch im Fenster [!UICONTROL Process Design] geöffnet werden. Klicken Sie in diesem Fenster auf das Symbol für den Aktivitätswähler oben im Fenster &quot;Process Design&quot;und ziehen Sie die neue Aktivität auf die Swim-Spur. An dieser Stelle sollte das Fenster [!UICONTROL Aktivität definieren] angezeigt werden (siehe Abbildung unten).
   ![Aktivität definieren](assets/define-activity.jpg)
1. Der executeScript-Dienst befindet sich unter dem Satz von `Foundation` -Diensten. Im Namen Dienste wird das Objekt als `Execute Script – 1.0` mit dem Vorgangsnamen `executeScript` aufgeführt. Klicken Sie auf dieses Element.
1. Dieser Prozess sollte jetzt erstellt werden. Standardmäßig sollte das Fenster [!UICONTROL Process Properties] im Bereich auf der linken Seite angezeigt werden.

#### Hinzufügen eines Skripts zum Prozess mit dem Dienst &quot;Execute Script&quot; {#add-script-to-process-with-execute-script}

Nachdem der Prozess mit der definierten Aktivität &quot;Script ausführen&quot;erstellt wurde, kann diesem Prozess ein Skript hinzugefügt werden. So fügen Sie diesem Prozess ein Skript hinzu:

1. Navigieren Sie zur Palette [!UICONTROL Prozesseigenschaften] . Erweitern Sie in dieser Palette den Bereich [!UICONTROL Input] und klicken Sie auf das Symbol &quot;...&quot;.

1. Schreiben Sie Ihr Skript in das angezeigte Textfeld. Wenn das Skript geschrieben wurde, drücken Sie OK (siehe Abbildung unten).
   ![Execute Script](assets/execute-script.jpg)

## Erstellen von XML mit dem Execute Script-Dienst {#create-xml-execute-script-service}

Nachdem ein Prozess mit dem hinzugefügten Execute Script-Dienst erstellt wurde, kann dieses Skript zur Erstellung von XML verwendet werden. Man schreibt die unten beschriebenen Skripte in das Textfeld, das im Abschnitt Skript zum Prozess mit dem Dienst hinzufügen oben beschrieben ist.`Execute Script`

**Über die Technologie des Execute Script-Dienstes**

Um zu wissen, welche Fähigkeiten und Einschränkungen der Execute Script-Dienst-Funktion aufweisen, muss man die technologischen Grundlagen des Dienstes kennen. AEM Forms on JEE verwendet den Apache Xerces Document Object Model (DOM)-Parser, um XML-Variablen in Prozessen zu erstellen und zu speichern. Xerces ist eine Java-Implementierung der Document Object Model-Spezifikation des W3C-Consortiums. definiert [hier](https://dom.spec.whatwg.org/). Die DOM-Spezifikation ist eine Standardmethode zur Bearbeitung von XML, die seit 1998 existiert. Die Java-Implementierung von Xerces, Xerces-J, unterstützt DOM Level 2 Version 1.0.

Die Java-Klassen, die zum Speichern von XML-Variablen verwendet werden, sind:

* org.apache.xerces.dom.NodeImpl und

* org.apache.xerces.dom.DocumentImpl

DocumentImpl ist eine Unterklasse von NodeImpl. Daher kann angenommen werden, dass jede XML-Prozessvariable eine NodeImpl-Ableitung ist. Die Dokumentation für NodeImpl [finden Sie hier](http://xerces.apache.org/xerces-j/apiDocs/org/apache/xerces/dom/NodeImpl.html).

**Beispiel für die XML-Erstellung mit dem Execute Script-Dienst**

Im Folgenden finden Sie ein Beispiel für das Erstellen von XML in einem Execute Script-Dienst. Der Prozess verfügt über eine Variable, einen Knoten, der vom Typ XML ist. Das Endergebnis dieser Aktivität ist ein XML-Dokument. Was dieses Dokument tut oder wie es auf den gesamten Prozess angewendet wird, ist für dieses Tutorial nicht relevant. Letztlich geht es darum, was XML in der übergeordneten Anwendung tun muss. Wie in der Einführung erwähnt, kann XML in AEM Forms on JEE-Formularen und -Prozessen für viele Zwecke verwendet werden. Dies ist lediglich eine Erklärung dafür, wie die Aktivität &quot;Skript ausführen&quot;codiert wird, um ein einfaches XML-Dokument auszugeben.

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

**Verwenden einer Iterativen Schleife zum Hinzufügen von Knoten zur XML-Datei**

Knoten können auch innerhalb des Prozesses zu einer vorhandenen XML-Variablen hinzugefügt werden. Die Variable node enthält das soeben erstellte XML-Objekt.

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



