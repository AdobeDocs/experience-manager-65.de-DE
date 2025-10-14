---
title: Server-seitige Anpassung
description: Erfahren Sie, wie Sie in Adobe Experience Manager Communities Server-seitig anpassen können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 190735bc-1909-4b92-ba4f-a221c0cd5be7
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---

# Server-seitige Anpassung {#server-side-customization}

| **[⇐ Feature Essentials](essentials.md)** | **[Client-seitige ⇒](client-customize.md)** |
|---|---|
|   | **[SCF Handlebars Helpers ⇒](handlebars-helpers.md)** |

## Java™-APIs {#java-apis}

>[!NOTE]
>
>Der Paketspeicherort von Communities-APIs kann sich beim Upgrade von einer Hauptversion zur nächsten ändern.

### SocialComponent-Benutzeroberfläche {#socialcomponent-interface}

Social-Komponenten sind POJOs, die eine Ressource für eine AEM Communities-Funktion darstellen. Idealerweise stellt jede SocialComponent einen bestimmten resourceType mit bereitgestellten GETters dar, die dem Client Daten bereitstellen, damit die Ressource korrekt dargestellt wird. Die gesamte Geschäfts- und Ansichtslogik ist in der SocialComponent gekapselt, einschließlich der Sitzungsinformationen der Site-Besuchenden, falls erforderlich.

Die -Schnittstelle definiert einen grundlegenden Satz von GETters, die zur Darstellung einer Ressource erforderlich sind. Wichtig ist, dass die Schnittstelle die Map&lt;String, Object> getAsMap()- und String toJSONString()-Methoden festlegt, die zum Rendern von Handlebars-Vorlagen und zum Offenlegen von GET-JSON-Endpunkten für Ressourcen erforderlich sind.

Alle SocialComponent-Klassen müssen die `com.adobe.cq.social.scf.SocialComponent` implementieren

### SocialCollectionComponent-Schnittstelle {#socialcollectioncomponent-interface}

Die SocialCollectionComponent-Schnittstelle erweitert die SocialComponent-Schnittstelle, um Ressourcen besser darzustellen, die Auflistungen anderer Ressourcen sind.

Alle SocialCollectionComponent-Klassen müssen die Schnittstelle com.adobe.cq.social.scf.SocialCollectionComponent implementieren

### SocialComponentFactory-Schnittstelle {#socialcomponentfactory-interface}

Eine SocialComponentFactory (Factory) registriert eine SocialComponent im Framework. Die Factory bietet eine Möglichkeit, dem Framework mitzuteilen, welche Social-Komponenten für einen bestimmten resourceType verfügbar sind, und deren Prioritätsreihenfolge, wenn mehrere Social-Komponenten identifiziert werden.

Eine SocialComponentFactory ist für die Erstellung einer Instanz der ausgewählten SocialComponent verantwortlich, sodass alle von der SocialComponent benötigten Abhängigkeiten von der Factory mithilfe von ID-Praktiken eingefügt werden können.

Eine SocialComponentFactory ist ein OSGi-Dienst und hat Zugriff auf andere OSGi-Dienste, die über einen Konstruktor an die SocialComponent übergeben werden können.

Alle SocialComponentFactory-Klassen müssen die Schnittstelle `com.adobe.cq.social.scf.SocialComponentFactory` implementieren

Eine Implementierung der Methode SocialComponentFactory.getPriority() sollte den höchsten Wert für die Factory zurückgeben, die für den angegebenen resourceType verwendet werden soll, wie er von getResourceType() zurückgegeben wird.

### SocialComponentFactoryManager-Schnittstelle {#socialcomponentfactorymanager-interface}

Der SocialComponentFactoryManager (Manager) verwaltet alle beim Framework registrierten SocialComponents und ist für die Auswahl der für eine bestimmte Ressource (resourceType) zu verwendenden SocialComponentFactory verantwortlich. Wenn für einen bestimmten resourceType keine Factories registriert sind, gibt der Manager eine Factory mit dem nächsten Supertyp für die angegebene Ressource zurück.

Ein SocialComponentFactoryManager ist ein OSGi-Dienst und hat Zugriff auf andere OSGi-Dienste, die über einen Konstruktor an die SocialComponent übergeben werden können.

Ein Handle für den OSGi-Dienst wird durch Aufrufen von `com.adobe.cq.social.scf.SocialComponentFactoryManager` abgerufen

### HTTP-API - POST-Anfragen {#http-api-post-requests}

#### PostOperation-Klasse {#postoperation-class}

Die Endpunkte der HTTP-API-POST sind PostOperation-Klassen, die durch die Implementierung der `SlingPostOperation`-Schnittstelle (Package `org.apache.sling.servlets.post`) definiert werden.

Die `PostOperation`-Endpunktimplementierung setzt `sling.post.operation` auf einen Wert, auf den der Vorgang antwortet. Alle POST-Anforderungen, für die ein:operation-Parameter auf diesen Wert festgelegt ist, werden an diese Implementierungsklasse delegiert.

Die `PostOperation` ruft die `SocialOperation` auf, die die für den Vorgang erforderlichen Aktionen ausführt.

Der `PostOperation` empfängt das Ergebnis vom `SocialOperation` und gibt die entsprechende Antwort an den Client zurück.

#### SocialOperation-Klasse {#socialoperation-class}

Jeder `SocialOperation` Endpunkt erweitert die AbstractSocialOperation-Klasse und überschreibt die `performOperation()`. Diese Methode führt alle Aktionen aus, die zum Abschließen des Vorgangs und Zurückgeben eines `SocialOperationResult` erforderlich sind. Andernfalls wird ein `OperationException` ausgelöst. In diesem Fall wird anstelle der normalen JSON-Antwort oder des Erfolgs-HTTP-Status-Codes ein HTTP-Fehlerstatus mit einer Meldung zurückgegeben, sofern verfügbar.

Die Erweiterung von `AbstractSocialOperation` ermöglicht die Wiederverwendung von `SocialComponents` zum Senden von JSON-Antworten.

#### SocialOperationResult-Klasse {#socialoperationresult-class}

Die `SocialOperationResult`-Klasse wird als Ergebnis der `SocialOperation` zurückgegeben und besteht aus einer `SocialComponent`, einem HTTP-Status-Code und einer HTTP-Statusmeldung.

Die `SocialComponent` stellt die Ressource dar, die von dem Vorgang betroffen war.

Bei einem Erstellungsvorgang stellt der im `SocialOperationResult` enthaltene `SocialComponent` die erstellte Ressource dar und bei einem Aktualisierungsvorgang die Ressource, die durch den Vorgang geändert wurde. Für einen Löschvorgang wird kein `SocialComponent` zurückgegeben.

Die verwendeten HTTP-Erfolgs-Status-Codes sind:

* 201 für Vorgänge vom Typ Erstellen
* 200 für Aktualisierungsvorgänge
* 204 für Löschvorgänge

#### OperationException-Klasse {#operationexception-class}

Beim Ausführen eines Vorgangs wird ein `OperationExcepton` ausgelöst, wenn die Anfrage ungültig ist oder ein anderer Fehler auftritt. Beispielsweise interne Fehler, ungültige Parameterwerte oder falsche Berechtigungen. Ein `OperationException` besteht aus einem HTTP-Status-Code und einer Fehlermeldung, die als Antwort auf die `PostOperatoin` an den Client zurückgegeben werden.

#### OperationService-Klasse {#operationservice-class}

Im Social Component Framework wird empfohlen, die für die Durchführung des Vorgangs verantwortliche Geschäftslogik nicht innerhalb der `SocialOperation`-Klasse zu implementieren, sondern stattdessen an einen OSGi-Dienst zu delegieren. Durch die Verwendung eines OSGi-Dienstes für die Geschäftslogik kann ein `SocialComponent`, auf den ein `SocialOperation`-Endpunkt einwirkt, in anderen Code integriert werden und eine andere Geschäftslogik angewendet werden.

Alle `OperationService` Klassen erweitern `AbstractOperationService` und ermöglichen so zusätzliche Erweiterungen, die in den ausgeführten Vorgang eingebunden werden können. Jeder Vorgang im Dienst wird durch eine `SocialOperation`-Klasse dargestellt. Die `OperationExtensions`-Klasse kann während der Ausführung des Vorgangs durch Aufruf der Methoden aufgerufen werden

* `performBeforeActions()`

  Ermöglicht Vorabprüfungen/Vorab-Bearbeitung und Validierungen
* `performAfterActions()`

  Ermöglicht die weitere Bearbeitung von Ressourcen oder das Aufrufen benutzerdefinierter Ereignisse, Workflows usw.

#### OperationExtension-Klasse {#operationextension-class}

Die `OperationExtension` Klassen sind benutzerdefinierte Code-Abschnitte, die in einen Vorgang eingefügt werden können, um die Anpassung von Vorgängen an Geschäftsanforderungen zu ermöglichen. Die Benutzer der Komponente können der Komponente dynamisch und inkrementell Funktionen hinzufügen. Das Erweiterungs-/Hook-Muster ermöglicht es Entwicklerinnen und Entwicklern, sich ausschließlich auf die Erweiterungen selbst zu konzentrieren, und macht das Kopieren und Überschreiben ganzer Vorgänge und Komponenten überflüssig.

## Beispielcode {#sample-code}

Beispielcode ist im Repository [Adobe Experience Cloud GitHub](https://github.com/Adobe-Marketing-Cloud) verfügbar. Nach Projekten mit dem Präfix `aem-communities` oder `aem-scf` suchen.

## Best Practices {#best-practices}

Im Abschnitt [Kodierungsrichtlinien](code-guide.md) finden Sie verschiedene Kodierungsrichtlinien und Best Practices für AEM Communities-Entwickler.

Informationen [&#x200B; Zugriff auf benutzergenerierte Inhalte finden Sie unter &#x200B;](srp.md)Speicherressourcenanbieter (SRP) für benutzergenerierte Inhalte).

| **[⇐ Feature Essentials](essentials.md)** | **[Client-seitige ⇒](client-customize.md)** |
|---|---|
|   | **[SCF Handlebars Helpers ⇒](handlebars-helpers.md)** |
