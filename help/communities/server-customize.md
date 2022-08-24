---
title: Serverseitige Anpassung
seo-title: Server-side Customization
description: Serverseitige Anpassung in AEM Communities
seo-description: Customizing server-side in AEM Communities
uuid: 5e9bc6bf-69dc-414c-a4bd-74a104d7bd8f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: df5416ec-5c63-481b-99ed-9e5a91df2432
exl-id: 190735bc-1909-4b92-ba4f-a221c0cd5be7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---

# Serverseitige Anpassung {#server-side-customization}

| **[⇐ Funktionsgrundlagen](essentials.md)** | **[Client-seitige Anpassung imetall](client-customize.md)** |
|---|---|
|  | **[SCF-Handlebars Helpers imetall](handlebars-helpers.md)** |

## Java-APIs {#java-apis}

>[!NOTE]
>
>Der Paketspeicherort der Communities-APIs kann sich ändern, wenn von einer Hauptversion zur nächsten aktualisiert wird.

### SocialComponent-Schnittstelle {#socialcomponent-interface}

SocialComponents sind POJOs, die eine Ressource für eine AEM Communities-Funktion darstellen. Idealerweise stellt jede SocialComponent einen bestimmten resourceType mit offen gelegten GETters dar, die dem Client Daten bereitstellen, damit die Ressource korrekt dargestellt wird. Alle Geschäftslogik und Ansichtslogik sind in der SocialComponent eingeschlossen, einschließlich der Sitzungsinformationen des Site-Besuchers, sofern erforderlich.

Die Schnittstelle definiert einen grundlegenden Satz von GETters, die zur Darstellung einer Ressource erforderlich sind. Wichtig ist, dass die Oberfläche Map festlegt&lt;string object=&quot;&quot;> getAsMap() - und String toJSONString() -Methoden, die erforderlich sind, um Handlebars-Vorlagen zu rendern und GET JSON-Endpunkte für Ressourcen verfügbar zu machen.

Alle SocialComponent-Klassen müssen die Schnittstelle implementieren `com.adobe.cq.social.scf.SocialComponent`

### SocialCollectionComponent-Schnittstelle {#socialcollectioncomponent-interface}

Die Schnittstelle SocialCollectionComponent erweitert die Schnittstelle SocialComponent , um Ressourcen besser darzustellen, die Sammlungen anderer Ressourcen sind.

Alle SocialCollectionComponent-Klassen müssen die Schnittstelle com.adobe.cq.social.scf.SocialCollectionComponent implementieren

### SocialComponentFactory-Schnittstelle {#socialcomponentfactory-interface}

Eine SocialComponentFactory (Factory) registriert eine SocialComponent mit dem Framework. Die Factory bietet eine Möglichkeit, dem Framework mitzuteilen, welche SocialComponents für einen bestimmten resourceType verfügbar sind, und seine Prioritätsstufe zu geben, wenn mehrere SocialComponents identifiziert werden.

Eine SocialComponentFactory ist für das Erstellen einer Instanz der ausgewählten SocialComponent verantwortlich, die es ermöglicht, alle Abhängigkeiten, die von der SocialComponent benötigt werden, mithilfe von DI-Verfahren aus der Factory einzufügen.

Eine SocialComponentFactory ist ein OSGi-Dienst und hat Zugriff auf andere OSGi-Dienste, die über einen Konstruktor an die SocialComponent übergeben werden können.

Alle SocialComponentFactory-Klassen müssen die Schnittstelle implementieren `com.adobe.cq.social.scf.SocialComponentFactory`

Eine Implementierung der Methode SocialComponentFactory.getPriority() sollte den höchsten Wert zurückgeben, damit die Factory für den angegebenen resourceType verwendet wird, wie von getResourceType() zurückgegeben.

### SocialComponentFactoryManager-Schnittstelle {#socialcomponentfactorymanager-interface}

Der SocialComponentFactoryManager (manager) verwaltet alle im Framework registrierten SocialComponents und ist für die Auswahl der SocialComponentFactory für eine bestimmte Ressource (resourceType) verantwortlich. Wenn für einen bestimmten resourceType keine Fabriken registriert sind, gibt der Manager eine Factory mit dem nächsten Supertyp für die jeweilige Ressource zurück.

Ein SocialComponentFactoryManager ist ein OSGi-Dienst und hat Zugriff auf andere OSGi-Dienste, die über einen Konstruktor an die SocialComponent übergeben werden können.

Ein Handle für den OSGi-Dienst wird durch Aufrufen von abgerufen `com.adobe.cq.social.scf.SocialComponentFactoryManager`

### HTTP-API - POST-Anfragen {#http-api-post-requests}

#### PostOperation-Klasse {#postoperation-class}

Die Endpunkte der HTTP-API-POST sind PostOperation-Klassen, die durch Implementierung der `SlingPostOperation` Schnittstelle (package) `org.apache.sling.servlets.post`).

Die `PostOperation` Endpunkt-Implementierungssätze `sling.post.operation` auf einen Wert, auf den der Vorgang reagieren soll. Alle POST-Anfragen mit einem:operation -Parameter, der auf diesen Wert gesetzt ist, werden dieser Implementierungsklasse zugewiesen.

Die `PostOperation` ruft die `SocialOperation` , der die für den Vorgang erforderlichen Aktionen durchführt.

Die `PostOperation` erhält das Ergebnis von `SocialOperation` und gibt die entsprechende Antwort an den Client zurück.

#### SocialOperation-Klasse {#socialoperation-class}

Jeder `SocialOperation` endpoint erweitert die Klasse AbstractSocialOperation und überschreibt die Methode `performOperation()`. Diese Methode führt alle erforderlichen Aktionen aus, um den Vorgang abzuschließen und eine `SocialOperationResult` oder andernfalls `OperationException`: In diesem Fall wird anstelle des normalen JSON-Antwort- oder Erfolgs-HTTP-Status-Codes ein HTTP-Fehlerstatus mit einer Nachricht zurückgegeben, sofern verfügbar.

Erweitern `AbstractSocialOperation` ermöglicht die Wiederverwendung von `SocialComponents` , um JSON-Antworten zu senden.

#### SocialOperationResult-Klasse {#socialoperationresult-class}

Die `SocialOperationResult` -Klasse wird als Ergebnis der `SocialOperation` und besteht aus einer `SocialComponent`, HTTP-Statuscode und HTTP-Statusmeldung.

Die `SocialComponent` stellt die Ressource dar, die vom Vorgang betroffen war.

Bei einem Erstellen -Vorgang wird die `SocialComponent` im `SocialOperationResult` die soeben erstellte Ressource darstellt und für einen Aktualisierungsvorgang die Ressource darstellt, die durch den Vorgang verändert wurde. Nein `SocialComponent` wird für einen Löschvorgang zurückgegeben.

Folgende Erfolgs-HTTP-Status-Codes werden verwendet:

* 201 für Vorgänge zum Erstellen
* 200 für Aktualisierungsvorgänge
* 204 für Löschvorgänge

#### OperationException-Klasse {#operationexception-class}

Ein `OperationExcepton` kann bei der Ausführung eines Vorgangs ausgelöst werden, wenn die Anfrage ungültig ist oder ein anderer Fehler auftritt, z. B. interne Fehler, ungültige Parameterwerte, falsche Berechtigungen usw. Ein `OperationException` besteht aus einem HTTP-Status-Code und einer Fehlermeldung, die an den Client als Antwort auf die `PostOperatoin`.

#### OperationService-Klasse {#operationservice-class}

Das Social-Komponenten-Framework empfiehlt, dass die Geschäftslogik, die für die Durchführung des Vorgangs verantwortlich ist, nicht im `SocialOperation` -Klasse, sondern stattdessen an einen OSGi-Dienst delegiert. Wenn Sie einen OSGi-Dienst für Geschäftslogik verwenden, wird eine `SocialComponent`, auf die sich ein `SocialOperation` -Endpunkt, der in anderen Code integriert werden soll und unterschiedliche Geschäftslogik angewendet wird.

Alle `OperationService` Klassen erweitern `AbstractOperationService`, wodurch zusätzliche Erweiterungen möglich sind, die mit dem ausgeführten Vorgang verbunden werden können. Jeder Vorgang im Dienst wird durch eine `SocialOperation` -Klasse. Die `OperationExtensions` -Klasse kann während der Vorgangsausführung durch Aufruf der -Methoden aufgerufen werden

* `performBeforeActions()`

   Ermöglicht Vorab-Prüfungen/Vorab-Bearbeitung und Überprüfungen
* `performAfterActions()`

   Ermöglicht die weitere Änderung von Ressourcen oder das Aufrufen benutzerdefinierter Ereignisse, Workflows usw.

#### OperationExtension-Klasse {#operationextension-class}

`OperationExtension` -Klassen sind benutzerdefinierte Code-Abschnitte, die in einen Vorgang eingefügt werden können, der eine Anpassung der Vorgänge an die Geschäftsanforderungen ermöglicht. Die Verbraucher der Komponente können der Komponente dynamisch und schrittweise Funktionen hinzufügen. Das Erweiterungs-/Erweiterungs-Muster ermöglicht es Entwicklern, sich ausschließlich auf die Erweiterungen selbst zu konzentrieren, und macht das Kopieren und Überschreiben ganzer Vorgänge und Komponenten überflüssig.

## Beispielcode {#sample-code}

Beispielcode ist im Abschnitt [Adobe Marketing Cloud GitHub](https://github.com/Adobe-Marketing-Cloud) Repository. Suchen Sie nach Projekten mit dem Präfix `aem-communities` oder `aem-scf`.

## Best Practices {#best-practices}

Anzeigen der [Kodierungsrichtlinien](code-guide.md) für verschiedene Codierungsrichtlinien und Best Practices für AEM Communities-Entwickler.

Siehe auch [Storage Resource Provider (SRP) für UGC](srp.md) , um mehr über den Zugriff auf benutzergenerierte Inhalte zu erfahren.

| **[⇐ Funktionsgrundlagen](essentials.md)** | **[Client-seitige Anpassung imetall](client-customize.md)** |
|---|---|
|  | **[SCF-Handlebars Helpers imetall](handlebars-helpers.md)** |
