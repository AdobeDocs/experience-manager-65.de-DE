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
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 0%

---


# Serverseitige Anpassung {#server-side-customization}

| **[⇐ Essentials](essentials.md)** | **[Clientseitige Anpassung ⇒](client-customize.md)** |
|---|---|
|  | **[SCF-Handlebars Helpers ⇒](handlebars-helpers.md)** |

## Java-APIs {#java-apis}

>[!NOTE]
>
>Der Speicherort des Pakets von Communities-APIs kann sich ändern, wenn von einer Hauptversion zur nächsten aktualisiert wird.

### SocialComponent-Schnittstelle {#socialcomponent-interface}

SocialComponents sind POJOs, die eine Ressource für eine AEM Communities-Funktion darstellen. Idealerweise stellt jede SocialComponent einen bestimmten resourceType mit offen gelegten GETters dar, die dem Client Daten bereitstellen, damit die Ressource korrekt dargestellt wird. Die gesamte Geschäftslogik und die Logik der Ansicht sind in der SocialComponent eingeschlossen, einschließlich der Sitzungsinformationen des Site-Besuchers, sofern erforderlich.

Die Schnittstelle definiert einen grundlegenden Satz von GETters, die zur Darstellung einer Ressource erforderlich sind. Wichtig ist, dass in der Schnittstelle die Methoden Map&lt;String, Object> getAsMap() und String toJSONString() festgelegt sind, die zum Rendern von Handlebars-Vorlagen und zum Bereitstellen von GET JSON-Endpunkten für Ressourcen erforderlich sind.

Alle SocialComponent-Klassen müssen die Schnittstelle implementieren `com.adobe.cq.social.scf.SocialComponent`

### SocialCollectionComponent-Schnittstelle {#socialcollectioncomponent-interface}

Die SocialCollectionComponent-Schnittstelle erweitert die SocialComponent-Schnittstelle, um Ressourcen besser darzustellen, die Sammlungen anderer Ressourcen sind.

Alle SocialCollectionComponent-Klassen müssen die Schnittstelle com.adobe.cq.social.scf.SocialCollectionComponent implementieren

### SocialComponentFactory-Schnittstelle {#socialcomponentfactory-interface}

Eine SocialComponentFactory (Factory) registriert eine SocialComponent mit dem Framework. Die Factory bietet eine Möglichkeit, dem Framework mitzuteilen, welche SocialComponents für einen bestimmten resourceType verfügbar sind und welche Priorität sie haben, wenn mehrere SocialComponents identifiziert werden.

Eine SocialComponentFactory ist für das Erstellen einer Instanz der ausgewählten SocialComponent zuständig, sodass alle Abhängigkeiten, die von der SocialComponent benötigt werden, mithilfe von DI-Verfahren aus der Factory eingefügt werden können.

Eine SocialComponentFactory ist ein OSGi-Dienst und hat Zugriff auf andere OSGi-Dienste, die über einen Konstruktor an die SocialComponent übergeben werden können.

Alle SocialComponentFactory-Klassen müssen die Schnittstelle implementieren `com.adobe.cq.social.scf.SocialComponentFactory`

Eine Implementierung der Methode SocialComponentFactory.getPriority() sollte den höchsten Wert zurückgeben, damit die Factory für den angegebenen resourceType verwendet wird, wie von getResourceType() zurückgegeben.

### SocialComponentFactoryManager-Schnittstelle {#socialcomponentfactorymanager-interface}

Der SocialComponentFactoryManager (Manager) verwaltet alle im Framework registrierten SocialComponents und ist für die Auswahl der SocialComponentFactory für eine bestimmte Ressource (resourceType) zuständig. Wenn keine Fabriken für einen bestimmten resourceType registriert sind, gibt der Manager eine Factory mit dem nächsten Supertyp für die jeweilige Ressource zurück.

Ein SocialComponentFactoryManager ist ein OSGi-Dienst und hat Zugriff auf andere OSGi-Dienste, die über einen Konstruktor an die SocialComponent übergeben werden können.

Ein Handle für den OSGi-Dienst wird durch Aufrufen von `com.adobe.cq.social.scf.SocialComponentFactoryManager`

### HTTP-API - POST-Anfragen {#http-api-post-requests}

#### PostOperation-Klasse {#postoperation-class}

Die HTTP-API-POST-Endpunkte sind PostOperation-Klassen, die durch Implementierung der `SlingPostOperation` Schnittstelle (package `org.apache.sling.servlets.post`) definiert werden.

Die Implementierung des `PostOperation` Endpunkts legt `sling.post.operation` einen Wert fest, auf den der Vorgang reagieren soll. Alle POST-Anfragen mit einem:operation-Parameter, der auf diesen Wert gesetzt ist, werden dieser Implementierungsklasse übertragen.

Die `PostOperation` ruft die `SocialOperation` auf, die die für den Vorgang erforderlichen Aktionen ausführt.

Der `PostOperation` erhält das Ergebnis von der `SocialOperation` und gibt die entsprechende Antwort an den Client zurück.

#### SocialOperation-Klasse {#socialoperation-class}

Jeder `SocialOperation` Endpunkt erweitert die Klasse AbstractSocialOperation und überschreibt die Methode `performOperation()`. Diese Methode führt alle erforderlichen Aktionen aus, um den Vorgang abzuschließen und eine `SocialOperationResult` oder andere Ausgabe eines Fehlers zurückzugeben. `OperationException`In diesem Fall wird anstelle des normalen JSON-Antwort- oder Erfolgs-HTTP-Statuscodes ein HTTP-Fehlerstatus mit einer Meldung zurückgegeben, sofern verfügbar.

Die Erweiterung `AbstractSocialOperation` ermöglicht die Wiederverwendung von `SocialComponents` zum Senden von JSON-Antworten.

#### SocialOperationResult-Klasse {#socialoperationresult-class}

Die `SocialOperationResult` Klasse wird als Ergebnis der zurückgegeben `SocialOperation` und setzt sich aus einem `SocialComponent`HTTP-Statuscode und einer HTTP-Statusmeldung zusammen.

Die `SocialComponent` Ressource, die von dem Vorgang betroffen war.

Bei einem Create-Vorgang stellt die `SocialComponent` im `SocialOperationResult` Abschnitt enthaltene Ressource die soeben erstellte Ressource und bei einem Update-Vorgang die Ressource dar, die durch den Vorgang geändert wurde. Für einen Löschvorgang `SocialComponent` wird kein Fehler zurückgegeben.

Folgende HTTP-Statuscodes werden verwendet:

* 201 für Create-Vorgänge
* 200 für Aktualisierungsvorgänge
* 204 für Löschvorgänge

#### OperationException-Klasse {#operationexception-class}

Bei Ausführung eines Vorgangs `OperationExcepton` kann eine Fehlermeldung ausgegeben werden, wenn die Anforderung ungültig ist oder ein anderer Fehler auftritt, z. B. interne Fehler, ungültige Parameterwerte, falsche Berechtigungen usw. Eine `OperationException` besteht aus einem HTTP-Statuscode und einer Fehlermeldung, die an den Client als Antwort auf die `PostOperatoin`.

#### OperationService-Klasse {#operationservice-class}

Das Framework für soziale Komponenten empfiehlt, dass die Geschäftslogik, die für die Ausführung des Vorgangs verantwortlich ist, nicht innerhalb der `SocialOperation` Klasse implementiert, sondern stattdessen an einen OSGi-Dienst delegiert wird. Durch die Verwendung eines OSGi-Dienstes für Geschäftslogik kann ein `SocialComponent`von einem `SocialOperation` Endpunkt verwendeter Endpunkt in anderen Code integriert werden und eine andere Geschäftslogik angewendet werden.

Alle `OperationService` Klassen erweitern `AbstractOperationService`und ermöglichen zusätzliche Erweiterungen, die an die auszuführende Operation angeschlossen werden können. Jeder Vorgang im Dienst wird durch eine `SocialOperation` Klasse dargestellt. Die `OperationExtensions` Klasse kann während der Ausführung des Vorgangs aufgerufen werden, indem die Methoden aufgerufen werden

* `performBeforeActions()`

   Ermöglicht die Vorab-/Vorverarbeitung und Überprüfung
* `performAfterActions()`

   Ermöglicht eine weitere Änderung der Ressourcen oder das Aufrufen benutzerdefinierter Ereignis, Workflows usw.

#### OperationExtension-Klasse {#operationextension-class}

`OperationExtension` Klassen sind benutzerdefinierte Codeabschnitte, die in einen Vorgang eingefügt werden können, der eine Anpassung der Vorgänge an die geschäftlichen Anforderungen ermöglicht. Die Benutzer der Komponente können der Komponente dynamisch und inkrementell Funktionen hinzufügen. Das Erweiterungs-/Hakenmuster ermöglicht es Entwicklern, sich ausschließlich auf die Erweiterungen selbst zu konzentrieren und entfernt die Notwendigkeit, ganze Vorgänge und Komponenten zu kopieren und zu überschreiben.

## Beispielcode {#sample-code}

Beispielcode ist im [Adobe Marketing Cloud GitHub](https://github.com/Adobe-Marketing-Cloud) Repository verfügbar. Suchen Sie nach Projekten mit dem Präfix `aem-communities` oder `aem-scf`.

## Best Practices {#best-practices}

Ansicht der [Coding-Richtlinien](code-guide.md) für verschiedene Codierungsrichtlinien und Best Practices für AEM Communities-Entwickler.

Informationen zum Zugriff auf benutzergenerierte Inhalte finden Sie unter auch [Datenspeicherung Resource Provider (SRP) für UGC](srp.md) .

| **[⇐ Essentials](essentials.md)** | **[Clientseitige Anpassung ⇒](client-customize.md)** |
|---|---|
|  | **[SCF-Handlebars Helpers ⇒](handlebars-helpers.md)** |

