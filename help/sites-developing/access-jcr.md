---
title: Anleitung für den programmgesteuerten Zugriff auf das AEM-JCR
seo-title: Anleitung für den programmgesteuerten Zugriff auf das AEM-JCR
description: Sie können programmgesteuert Knoten und Eigenschaften ändern, die sich innerhalb des AEM-Repositorys befinden, das Teil von Adobe Marketing Cloud ist.
seo-description: Sie können programmgesteuert Knoten und Eigenschaften ändern, die sich innerhalb des AEM-Repositorys befinden, das Teil von Adobe Marketing Cloud ist.
uuid: 2051d03f-430a-4cae-8f6d-e5bc727d733f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 69f62a38-7991-4009-8db7-ee8fd35dc535
translation-type: tm+mt
source-git-commit: 6d216e7521432468a01a29ad2879f8708110d970

---


# Anleitung für den programmgesteuerten Zugriff auf das AEM-JCR{#how-to-programmatically-access-the-aem-jcr}

Sie können programmgesteuert Knoten und Eigenschaften ändern, die sich innerhalb des Adobe CQ-Repositorys befinden, das Teil von Adobe Marketing Cloud ist. Für den Zugriff auf das CQ-Repository verwenden Sie die Java Content Repository (JCR)-API. Mit der JCR-API können Sie Erstellungs-, Ersetzungs-, Aktualisierungs- und Lösch- (CRUD)-Vorgänge für Inhalte im Adobe CQ-Repository durchführen. For more information about the Java JCR API, see [https://jackrabbit.apache.org/jcr/jcr-api.html](https://jackrabbit.apache.org/jcr/jcr-api.html).

>[!NOTE]
>
>Dieser Entwicklungsartikel modifiziert das Adobe CQ-JCR aus einer externen Java-Anwendung. Es besteht auch die Möglichkeit, das JCR aus einem OSGi-Bundle mithilfe der JCR-API zu modifizieren. For details, see [Persisting CQ data in the Java Content Repository](https://helpx.adobe.com/experience-manager/using/persisting-cq-data-java-content1.html).

>[!NOTE]
>
>To use the JCR API, add the `jackrabbit-standalone-2.4.0.jar` file to your Java application’s class path. You can obtain this JAR file from the Java JCR API web page at [https://jackrabbit.apache.org/jcr/jcr-api.html](https://jackrabbit.apache.org/jcr/jcr-api.html).

>[!NOTE]
>
>Eine Anleitung zur Abfrage des Adobe CQ-JCR mithilfe der JCR-Abfrage-API finden Sie in [Abfragen von Adobe Experience Manager-Daten mit der JCR-API](https://helpx.adobe.com/experience-manager/using/querying-experience-manager-data-using1.html).

## Repository-Instanz erstellen {#create-a-repository-instance}

Es gibt unterschiedliche Verfahren zur Herstellung einer Verbindung mit einem Repository. In diesem Entwicklungsartikel wird eine statische Methode verwendet, die der Klasse `org.apache.jackrabbit.commons.JcrUtils` zuzuordnen ist. Der Name der Methode lautet `getRepository`. Diese Methode verwendet einen Zeichenfolgenparameter, der die URL des Adobe CQ-Servers darstellt. Beispiel `http://localhost:4503/crx/server`.

Die Methode `getRepository` gibt eine `Repository`-Instanz zurück, was im folgenden Codebeispiel veranschaulicht wird.

```java
//Create a connection to the AEM JCR repository running on local host
Repository repository = JcrUtils.getRepository("http://localhost:4503/crx/server");
```

## Sitzungsinstanz erstellen {#create-a-session-instance}

The `Repository`instance represents the CRX repository. You use the `Repository`instance to establish a session with the repository. To create a session, invoke the `Repository`instance’s `login`method and pass a `javax.jcr.SimpleCredentials` object. The `login`method returns a `javax.jcr.Session` instance.

You create a `SimpleCredentials`object by using its constructor and passing the following string values:

* den Benutzernamen und
* das zugehörige Kennwort

When passing the second parameter, call the String object’s `toCharArray`method. The following code shows how to call the `login`method that returns a `javax.jcr.Sessioninstance`.

```java
//Create a Session instance
javax.jcr.Session session = repository.login( new SimpleCredentials("admin", "admin".toCharArray()));
```

## Knoteninstanz erstellen {#create-a-node-instance}

Use a `Session`instance to create a `javax.jcr.Node` instance. A `Node`instance lets you perform node operations. Beispielsweise können Sie einen neuen Knoten erstellen. To create a node that represents the root node, invoke the `Session`instance&#39;s `getRootNode` method, as shown in the following line of code.

```java
//Create a Node
Node root = session.getRootNode();
```

Once you create a `Node`instance, you can perform tasks such as creating another node and adding a value to it. Mit dem folgenden Code werden beispielsweise zwei Knoten erstellt und dem zweiten Knoten ein Wert hinzugefügt.

```java
// Store content
Node day = adobe.addNode("day");
day.setProperty("message", "Adobe CQ is part of the Adobe Digital Marketing Suite!");
```

## Knotenwerte abrufen {#retrieve-node-values}

To retrieve a node and its value, invoke the `Node`instance’s `getNode`method and pass a string value that represents the fully-qualified path to the node. Betrachten Sie die Knotenstruktur, die im vorherigen Codebeispiel erstellt wurde. Zum Abrufen des Tagesknotens geben Sie „adobe/day“ an, wie das folgende Codebeispiel zeigt:

```java
// Retrieve content
Node node = root.getNode("adobe/day");
System.out.println(node.getPath());
System.out.println(node.getProperty("message").getString());
```

## Knoten im Adobe CQ-Repository erstellen {#create-nodes-in-the-adobe-cq-repository}

The following Java code example represents a Java class that connects to Adobe CQ, creates a `Session`instance, and adds new nodes. Einem Knoten wird ein Datenwert zugewiesen, woraufhin der Wert des Knotens und seines Pfades aus der Konsole geschrieben wird. Wenn Sie die Sitzung abgeschlossen haben, melden Sie sich unbedingt ab.

```java
/*
 * This Java Quick Start uses the jackrabbit-standalone-2.4.0.jar
 * file. See the previous section for the location of this JAR file
 */

import javax.jcr.Repository;
import javax.jcr.Session;
import javax.jcr.SimpleCredentials;
import javax.jcr.Node;

import org.apache.jackrabbit.commons.JcrUtils;
import org.apache.jackrabbit.core.TransientRepository;

public class GetRepository {

public static void main(String[] args) throws Exception {

try {

    //Create a connection to the CQ repository running on local host
    Repository repository = JcrUtils.getRepository("http://localhost:4503/crx/server");

   //Create a Session
   javax.jcr.Session session = repository.login( new SimpleCredentials("admin", "admin".toCharArray()));

  //Create a node that represents the root node
  Node root = session.getRootNode();

  // Store content
  Node adobe = root.addNode("adobe");
  Node day = adobe.addNode("day");
  day.setProperty("message", "Adobe CQ is part of the Adobe Digital Marketing Suite!");

  // Retrieve content
  Node node = root.getNode("adobe/day");
  System.out.println(node.getPath());
  System.out.println(node.getProperty("message").getString());

  // Save the session changes and log out
  session.save();
  session.logout();
  }
 catch(Exception e){
  e.printStackTrace();
  }
 }
}
```

After you run the full code example and create the nodes, you can view the new nodes in the **[!UICONTROL CRXDE Lite]**, as shown in the following illustration.

![chlimage_1-68](assets/chlimage_1-68a.png)

