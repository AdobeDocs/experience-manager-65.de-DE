---
title: Serverseitige Anpassung
seo-title: Serverseitige Anpassung
description: Serverseitige Anpassung in AEM Communities
seo-description: Serverseitige Anpassung in AEM Communities
uuid: 5e9bc6bf-69dc-414c-a4bd-74a104d7bd8f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: df5416ec-5c63-481b-99ed-9e5a91df2432
exl-id: 190735bc-1909-4b92-ba4f-a221c0cd5be7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '896'
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

Die Schnittstelle definiert einen grundlegenden Satz von GETters, die zur Darstellung einer Ressource erforderlich sind. Wichtig ist, dass die Schnittstelle die Methoden Map&lt;String, Object> getAsMap() und String toJSONString() vorschreibt, die zum Rendern von Handlebars-Vorlagen und zum Bereitstellen von GET JSON-Endpunkten für Ressourcen erforderlich sind.

Alle SocialComponent-Klassen müssen die Schnittstelle `com.adobe.cq.social.scf.SocialComponent` implementieren

### SocialCollectionComponent-Schnittstelle {#socialcollectioncomponent-interface}

Die Schnittstelle SocialCollectionComponent erweitert die Schnittstelle SocialComponent , um Ressourcen besser darzustellen, die Sammlungen anderer Ressourcen sind.

Alle SocialCollectionComponent-Klassen müssen die Schnittstelle com.adobe.cq.social.scf.SocialCollectionComponent implementieren

### SocialComponentFactory-Schnittstelle {#socialcomponentfactory-interface}

Eine SocialComponentFactory (Factory) registriert eine SocialComponent mit dem Framework. Die Factory bietet eine Möglichkeit, dem Framework mitzuteilen, welche SocialComponents für einen bestimmten resourceType verfügbar sind, und seine Prioritätsstufe zu geben, wenn mehrere SocialComponents identifiziert werden.

Eine SocialComponentFactory ist für das Erstellen einer Instanz der ausgewählten SocialComponent verantwortlich, die es ermöglicht, alle Abhängigkeiten, die von der SocialComponent benötigt werden, mithilfe von DI-Verfahren aus der Factory einzufügen.

Eine SocialComponentFactory ist ein OSGi-Dienst und hat Zugriff auf andere OSGi-Dienste, die über einen Konstruktor an die SocialComponent übergeben werden können.

Alle SocialComponentFactory-Klassen müssen die Schnittstelle `com.adobe.cq.social.scf.SocialComponentFactory` implementieren

Eine Implementierung der Methode SocialComponentFactory.getPriority() sollte den höchsten Wert zurückgeben, damit die Factory für den angegebenen resourceType verwendet wird, wie von getResourceType() zurückgegeben.

### SocialComponentFactoryManager-Schnittstelle {#socialcomponentfactorymanager-interface}

Der SocialComponentFactoryManager (manager) verwaltet alle im Framework registrierten SocialComponents und ist für die Auswahl der SocialComponentFactory für eine bestimmte Ressource (resourceType) verantwortlich. Wenn für einen bestimmten resourceType keine Fabriken registriert sind, gibt der Manager eine Factory mit dem nächsten Supertyp für die jeweilige Ressource zurück.

Ein SocialComponentFactoryManager ist ein OSGi-Dienst und hat Zugriff auf andere OSGi-Dienste, die über einen Konstruktor an die SocialComponent übergeben werden können.

Ein Handle für den OSGi-Dienst wird durch Aufrufen von `com.adobe.cq.social.scf.SocialComponentFactoryManager` abgerufen

### HTTP-API - POST Requests {#http-api-post-requests}

#### PostOperation-Klasse {#postoperation-class}

Die HTTP-API-POST-Endpunkte sind PostOperation-Klassen, die durch Implementierung der `SlingPostOperation`-Schnittstelle (package `org.apache.sling.servlets.post`) definiert werden.

Die `PostOperation` -Endpunkt-Implementierung setzt `sling.post.operation` auf einen Wert, auf den der Vorgang reagieren soll. Alle POST-Anfragen mit einem:operation -Parameter, der auf diesen Wert gesetzt ist, werden dieser Implementierungsklasse zugewiesen.

`PostOperation` ruft die `SocialOperation` auf, die die für den Vorgang erforderlichen Aktionen ausführt.

`PostOperation` empfängt das Ergebnis von `SocialOperation` und gibt die entsprechende Antwort an den Client zurück.

#### SocialOperation-Klasse {#socialoperation-class}

Jeder `SocialOperation`-Endpunkt erweitert die Klasse AbstractSocialOperation und überschreibt die Methode `performOperation()`. Diese Methode führt alle Aktionen aus, die zum Abschließen des Vorgangs und zum Zurückgeben eines `SocialOperationResult` oder zum Ausgeben eines `OperationException`-Werts erforderlich sind. In diesem Fall wird anstelle des normalen JSON-Antwort- oder Erfolgs-HTTP-Status-Codes ein HTTP-Fehlerstatus mit einer Meldung zurückgegeben, sofern verfügbar.

Die Erweiterung `AbstractSocialOperation` ermöglicht die Wiederverwendung von `SocialComponents` zum Senden von JSON-Antworten.

#### SocialOperationResult Class {#socialoperationresult-class}

Die `SocialOperationResult`-Klasse wird als Ergebnis von `SocialOperation` zurückgegeben und besteht aus einer `SocialComponent`-, HTTP-Status-Code- und HTTP-Statusmeldung.

`SocialComponent` stellt die Ressource dar, die vom Vorgang betroffen war.

Bei einem Vorgang vom Typ Erstellen steht das im `SocialOperationResult` enthaltene `SocialComponent` für die soeben erstellte Ressource und bei einem Vorgang vom Typ Aktualisieren für die Ressource, die durch den Vorgang verändert wurde. Für einen Löschvorgang wird kein `SocialComponent` zurückgegeben.

Folgende Erfolgs-HTTP-Status-Codes werden verwendet:

* 201 für Vorgänge zum Erstellen
* 200 für Aktualisierungsvorgänge
* 204 für Löschvorgänge

#### OperationException-Klasse {#operationexception-class}

Bei Ausführung eines Vorgangs kann ein `OperationExcepton` -Wert ausgegeben werden, wenn die Anfrage ungültig ist oder ein anderer Fehler auftritt, z. B. interne Fehler, ungültige Parameterwerte, falsche Berechtigungen usw. Ein `OperationException` besteht aus einem HTTP-Statuscode und einer Fehlermeldung, die als Antwort auf `PostOperatoin` an den Client zurückgegeben werden.

#### OperationService-Klasse {#operationservice-class}

Das Social-Komponenten-Framework empfiehlt, dass die für die Ausführung des Vorgangs verantwortliche Geschäftslogik nicht innerhalb der `SocialOperation`-Klasse implementiert, sondern stattdessen an einen OSGi-Dienst delegiert wird. Durch die Verwendung eines OSGi-Diensts für Geschäftslogik kann ein `SocialComponent` -Endpunkt, auf den von einem `SocialOperation` -Endpunkt reagiert wird, in anderen Code integriert werden und unterschiedliche Geschäftslogik angewendet werden.

Alle `OperationService`-Klassen erweitern `AbstractOperationService`, wodurch zusätzliche Erweiterungen möglich sind, die in den ausgeführten Vorgang eingebunden werden können. Jeder Vorgang im Dienst wird durch eine `SocialOperation`-Klasse dargestellt. Die Klasse `OperationExtensions` kann während der Ausführung des Vorgangs durch Aufruf der Methoden aufgerufen werden

* `performBeforeActions()`

   Ermöglicht Vorab-Prüfungen/Vorab-Bearbeitung und Überprüfungen
* `performAfterActions()`

   Ermöglicht die weitere Änderung von Ressourcen oder das Aufrufen benutzerdefinierter Ereignisse, Workflows usw.

#### OperationExtension-Klasse {#operationextension-class}

`OperationExtension` -Klassen sind benutzerdefinierte Code-Abschnitte, die in einen Vorgang eingefügt werden können, der eine Anpassung der Vorgänge an die Geschäftsanforderungen ermöglicht. Die Verbraucher der Komponente können der Komponente dynamisch und schrittweise Funktionen hinzufügen. Das Erweiterungs-/Erweiterungs-Muster ermöglicht es Entwicklern, sich ausschließlich auf die Erweiterungen selbst zu konzentrieren, und macht das Kopieren und Überschreiben ganzer Vorgänge und Komponenten überflüssig.

## Beispielcode {#sample-code}

Beispielcode ist im Repository [Adobe Marketing Cloud GitHub](https://github.com/Adobe-Marketing-Cloud) verfügbar. Suchen Sie nach Projekten mit dem Präfix `aem-communities` oder `aem-scf`.

## Best Practices {#best-practices}

Im Abschnitt [Coding Guidelines](code-guide.md) finden Sie verschiedene Codierungsrichtlinien und Best Practices für AEM Communities-Entwickler.

Weitere Informationen zum Zugriff auf benutzergenerierte Inhalte finden Sie unter [Storage Resource Provider (SRP) for UGC](srp.md) .

| **[⇐ Funktionsgrundlagen](essentials.md)** | **[Client-seitige Anpassung imetall](client-customize.md)** |
|---|---|
|  | **[SCF-Handlebars Helpers imetall](handlebars-helpers.md)** |
