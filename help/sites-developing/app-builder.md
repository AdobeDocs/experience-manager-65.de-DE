---
title: Erweitern von [!DNL Adobe Experience Manager] 6.5 mithilfe von Adobe Developer App Builder.
description: Erweitern von [!DNL Adobe Experience Manager] 6.5 mithilfe von Adobe Developer App Builder.
source-git-commit: aab7d4aaf11b6aef3b729f906259a76c152fd6f0
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 1%

---


# Erweitern von [!DNL Adobe Experience Manager] mithilfe von Adobe Developer App Builder {#extend-using-app-builder}

## Was ist App Builder für AEM {#project-firefly}

Der neue Adobe Developer App Builder bietet ein Erweiterbarkeits-Framework, mit dem Entwickler AEM Funktionen einfach erweitern können.

App Builder bietet ein einheitliches Drittanbieter-Erweiterbarkeits-Framework für die Integration und Erstellung benutzerdefinierter Erlebnisse, die Adobe Experience Manager erweitern. Mit diesem vollständigen Erweiterbarkeits-Framework, das auf der Infrastruktur der Adobe basiert, können Entwickler benutzerdefinierte Microservices erstellen, Adobe Experience Manager über Adobe-Lösungen und den Rest des IT-Stapels erweitern und integrieren.

App Builder bietet Kunden eine Möglichkeit, Adobe Experience Manager in verschiedenen Anwendungsfällen einfach zu erweitern:

* Middleware-Erweiterbarkeit: Verbinden Sie externe Systeme mit Adobe Apps, indem Sie benutzerdefinierte Connectoren erstellen oder eine Suite vordefinierter Integrationen nutzen.
* Erweiterbarkeit der Hauptdienste - Erweiterung der Kernanwendungsfunktionen durch Erweiterung des Standardverhaltens mit benutzerdefinierten Funktionen und Geschäftslogik.
* Benutzererlebnis-Erweiterbarkeit - Erweitern Sie das Kernerlebnis, um Geschäftsanforderungen zu unterstützen oder kundenspezifische digitale Eigenschaften, Storefronts- und Back-Office-Apps zu erstellen.

App Builder (ehemals Project Firefly) steht seit Sommer 2020 für Unternehmenskunden und -partner über unsere Entwicklervorschau zur Verfügung. Die allgemeine Verfügbarkeit (GA) von App Builder ist für Dezember 2021 geplant. Wir freuen uns über Entwickler, den App Builder über unser [Testprogramm](http://adobe.ly/appbuilder-trial) auszuprobieren.

>[!NOTE]
>
> Kunden, die den App Builder nutzen möchten, AEM als Cloud Service nutzen möchten, finden unter [Erweitern von Adobe Experience Manager as a Cloud Service mit dem Adobe Developer App Builder](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/configuring-and-extending/app-builder.html) weitere Informationen.

## Architektur {#architecture}

Anstelle einer vordefinierten Lösung bietet Adobe Developer App Builder eine gemeinsame, konsistente und standardisierte Entwicklungsplattform für die Erweiterung von Adobe Cloud-Lösungen wie AEM:

* Adobe Developer Console - Für die Entwicklung benutzerdefinierter Microservices und Erweiterungen können Entwickler Projekte erstellen und verwalten, während sie auf alle Tools und APIs zugreifen, die sie zum Erstellen von Plug-ins und Integrationen benötigen.
* Entwicklertools - Open-Source-Tools, SDKs und Bibliotheken, mit denen Entwickler einfach benutzerdefinierte Erweiterungen und Integrationen erstellen können. Verwenden Sie React Spectrum (UI-Toolkit der Adobe), um eine gemeinsame Benutzeroberfläche für alle Adobe Apps zu haben.
* Dienste - I/O Runtime für das Hosting der Infrastruktur auf unserer Server-losen Plattform und I/O-Ereignisse für ereignisbasierte Integrationen. Wir bieten auch native Unterstützung für das Speichern von Daten und Dateien.
* Adobe Experience Cloud - Entwickler können Erweiterungen und Integrationen senden, die in ihrer Experience Cloud-Organisation veröffentlicht werden sollen. Systemadministratoren können diese Erweiterungen dann überprüfen, verwalten und genehmigen. Nach der Veröffentlichung finden Sie Ihre benutzerdefinierten App Builder-Erweiterungen und -Tools zusammen mit anderen Adobe Experience Cloud-Apps.

Die folgende Abbildung zeigt, wie eine auf App Builder aufbauende Standardanwendung diese Funktionen nutzt:

![Architektur](assets/firefly-architecture.jpg)

Weitere Informationen zur App Builder-Architektur finden Sie unter [Architekturübersicht](https://www.adobe.io/project-firefly/docs/guides/).

## Erste Schritte mit App Builder {#additional-resources}

Um Ihnen die ersten Schritte mit App Builder zu erleichtern, haben wir eine Reihe von Dokumentationen erstellt, die Sie bei den ersten Schritten unterstützen:

* [App Builder - Erste Schritte](https://www.adobe.io/project-firefly/docs/getting_started/)

## Weiteres Lernen mit Dokumentation {#appbuilder-documentation}

App Builder bietet Videos und Dokumentation für Entwickler, einschließlich Handbüchern, und Referenzdokumentation, die Sie bei der Entwicklung Ihrer eigenen benutzerdefinierten Anwendungen unterstützen:

* [App Builder-Dokumentation](https://www.adobe.io/project-firefly/docs/overview/)
* [App Builder-Videos](https://www.youtube.com/playlist?list=PLcVEYUqU7VRfDij-Jbjyw8S8EzW073F_o)

## Testen einer der Beispielanwendungen {#appbuilder-codesamples}

Bereit zur Entwicklung? Wir haben viele Beispielanwendungen, mit denen Sie schnell loslegen können:

* [App Builder-Code-Labs auf der Adobe Developer-Website](https://www.adobe.io/project-firefly/docs/resources/)

## Support {#support}

Für Entwickler-Supportanfragen empfehlen wir Entwicklern, unser [Experience League-Forum](https://experienceleaguecommunities.adobe.com/t5/project-firefly/ct-p/project-firefly) zu verwenden.
