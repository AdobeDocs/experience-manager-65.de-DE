---
title: App-Kachel verwalten
description: Erfahren Sie mehr über die Kachel "App verwalten"im App-Dashboard, über die Sie Details zur Anwendung bearbeiten können.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
exl-id: 8bcf70ef-94d2-4958-90b5-bc375b360916
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 4%

---

# App-Kachel verwalten{#manage-app-tile}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Über die Kachel &quot;**`Manage App`**&quot;im App-Dashboard können Sie Details zur Anwendung bearbeiten. Um die Detailseite zu öffnen, klicken Sie auf den Detaillink der Kachel **`Manage App`** . Auf der Seite &quot;**`Manage App`**&quot;können Sie die Einstellungen der PhoneGap-Anwendungskonfiguration (config.xml) bearbeiten und Ihre Anwendung für die Übermittlung an die verschiedenen Anwendungsspeicher vorbereiten.

![chlimage_1-116](assets/chlimage_1-116.png)

## Grundlegendes zur Kachel `Manage App` {#understanding-the-manage-app-tile}

Sie können einen Drilldown für jede Kachel in der Kachel **`Manage App`** durchführen, um Details anzuzeigen oder zu bearbeiten, indem Sie auf &quot;..&quot;in der unteren rechten Ecke klicken.

### Registerkarte &quot;Standard&quot; {#the-basic-tab}

Sie können den **Namen**, den **Autor**, die **Kurzbeschreibung** und die **Beschreibung** für Ihre App von dieser Registerkarte aus bearbeiten.

![chlimage_1-117](assets/chlimage_1-117.png)

### Der Tab Erweitert {#the-advanced-tab}

Jede Mobile App-Plattform beschreibt, welche Daten erfasst werden, wobei jeder App Store speziell ausgewählt wird.

Die angezeigten Plattformen werden durch den Inhalt der Datei &quot;PhoneGap config.xml&quot;gesteuert:

```xml
<widget>
<gap:platform name="ios"/>
<gap:platform name="android"/>
</widget>
```

Jeder Appstore von Anbietern - z. B. Apple App Store oder Google Play Store - benötigt mindestens einen Screenshot Ihrer Mobile App, um Ihre Anwendungsdetails für Kunden anzuzeigen. Diese Screenshots können strenge Anforderungen an Dimensionen und Inhalte haben (sie müssen im Grunde die Anwendung wirklich repräsentieren). AEM Apps unterstützt das Auswählen und Verwalten dieser Screenshots für die unterstützten Plattformen und das Anzeigen von Port-Dimensionen, wie es für den Anwendungsspeicher jedes Anbieters erforderlich ist.

>[!NOTE]
>
>Mit der AEM Verify-App können Sie Screenshots direkt an Ihre App-Details in AEM senden.
>
>Weitere Informationen finden Sie unter [Mobile Quickstart für AEM Verifizierung](/help/mobile/phonegap-mobile-quickstart.md) .

![chlimage_1-118](assets/chlimage_1-118.png)

### Metadaten {#metadata}

>[!NOTE]
>
>Sobald Sie mit der Kachel &quot;**`Manage App`**&quot;vertraut sind, finden Sie Informationen zum Anzeigen und Bearbeiten der Metadaten unter [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md) .

#### Allgemeine Metadaten {#common-metadata}

Jede Anwendung sollte über zugeordnete Metadaten verfügen, die bei der Konfiguration verschiedener Aspekte der Anwendung helfen. Die Seite &quot;App verwalten&quot;ist in zwei verschiedene Bereiche unterteilt, die mit der Metadatenerfassung zusammenhängen. Plattformspezifische Metadaten und allgemeine Metadaten.

Es gibt eine allgemeine Konfiguration und Metadaten für alle Plattformen.

In diesem Abschnitt definieren Sie die URL des Inhaltsaktualisierungs-Servers, die Landingpage für Ihre Mobile App, die PhoneGap-Version für die Kompilierung, Ihre Anwendungsversion, Ihren Namen, Ihre Beschreibung und mehr.

**App-Version** ist die funktionierende Version Ihrer Anwendung. Übliche Best Practice ist, eine 3-Dezimalnotation-Notation zu verwenden und vor der ersten Version unter 1.0.0 zu beginnen.

**PhoneGap Version** ist die Version, in der Sie Ihre Anwendung mit PhoneGap kompilieren möchten. Es empfiehlt sich, mit der aktuellen Version Schritt zu halten, um sicherzustellen, dass Sie die neuesten und besten Funktionen und Fehlerbehebungen erhalten.

**Content Update Server URL** ist die URL, die Ihre Anwendung zum Aufrufen von ContentSync-Updates verwendet. Sie muss auf Ihre Dispatcher-URL oder, falls Sie kein Dispatcher verwenden, auf eine Ihrer Veröffentlichungsinstanzen festgelegt sein, die zum Bereitstellen von ContentSync-Aktualisierungen für Ihre Anwendung verwendet wird.

![chlimage_1-119](assets/chlimage_1-119.png)

>[!NOTE]
>
>Dieser Abschnitt kann leer erscheinen, es sei denn, es liegen Daten zum Ausfüllen der Felder vor.
>
>Oben in der Detailansicht werden die Anwendungsversion, die PhoneGap-Version und die Aktualisierungs-URL angezeigt. Jeder dieser Werte kann im Abschnitt &quot;Allgemeine Metadaten&quot;festgelegt werden. Die Anwendungs-ID kann jedoch nicht bearbeitet werden.

#### Plattformmetadaten {#platform-metadata}

Jede Plattform, die in der Datei &quot;PhoneGap config.xml&quot;definiert ist, kann benutzerdefinierte Plattformeigenschaften enthalten. Ein AEM Entwickler muss die Inhaltsstruktur zur Erfassung dieser Eigenschaften beitragen. Ein Beispiel für plattformspezifische Eigenschaften finden Sie für iOS.

Metadaten für alle konfigurierten Plattformen werden jetzt auf der Registerkarte Erweitert der Kachel `Manage App` gleichzeitig angezeigt.

>[!NOTE]
>
>Die Abschnitte für Plattformmetadaten werden von PhoneGap während einer CLI oder beim Erstellen von Remote PhoneGap nicht verwendet. Stattdessen versucht AEM, Metadaten für Plattformen zu erfassen, die später beim Senden an den App Store des jeweiligen Anbieters verwendet werden können.

Bei Plattformen, die von AEM nicht verstanden werden, ist es für AEM Entwickler weiterhin möglich, die Benutzeroberfläche zu erweitern, um diese Metadaten zu erfassen, die später exportiert und während des Antragsübermittlungsprozesses verwendet werden können.

#### iOS-Metadaten {#ios-metadata}

Für den Apple AppStore sind zusätzliche Metadaten erforderlich, um Ihre Anwendung zur Verteilung zu übermitteln. Der Abschnitt &quot;iOS-Metadaten&quot;versucht, die erforderlichen Informationen zu erfassen, die vom iTMSTransporter-Tool von Apple zum Veröffentlichen der Metadaten in dem zugehörigen Apple-Entwicklerkonto verwendet werden können.

Um die Apple-spezifischen Metadaten abzurufen, erstellen Sie Ihre Anwendung auf [https://itunesconnect.apple.com](https://itunesconnect.apple.com/). Beim Erstellen Ihrer Anwendung generiert Apple Metadaten, die für den iOS-Metadatenabschnitt erforderlich sind, wenn Sie das Apple iTMSTransporter-Tool zum Überprüfen und Hochladen der Metadaten auf itunesconnect.apple.com verwenden möchten. Wenn Sie die zu erfassenden Metadaten abrufen möchten, müssen Sie die iOS-spezifischen Metadaten nicht ausfüllen. Sie können weiterhin die Metadaten exportieren, die die iOS und die gängigen Metadaten zusammenführen, und alle Screenshots in eine ZIP-Datei erfassen, die jederzeit heruntergeladen werden kann.

Die heruntergeladene ZIP-Datei enthält eine itmsp-Datei, die auf die Datei &quot;metadata.xml&quot;überprüft werden kann. Die itmsp-Datei enthält die exportierten Metadaten (innerhalb der Datei &quot;metadata.xml&quot;) sowie alle zugehörigen Screenshots.

Die Exportfunktion bietet eine praktische Möglichkeit, die Screenshots und Metadaten zu erfassen, die zur Eingabe in den herstellerspezifischen App Store an den Anwendungs-Publisher übergeben werden können.

![chlimage_1-120](assets/chlimage_1-120.png)

#### Android™-Metadaten {#android-metadata}

Bei der Auswahl der Android™-Plattform können derzeit keine benutzerdefinierten Metadaten festgelegt werden. Beim Klicken auf die Download-Schaltfläche wird eine ZIP-Datei mit einer Eigenschaftendatei generiert, die alle Metadaten und zugehörigen Screenshots enthält.

Die Exportfunktion bietet eine praktische Möglichkeit, die Screenshots und Metadaten zu erfassen, die zur Eingabe in den herstellerspezifischen App Store an den Anwendungs-Publisher übergeben werden können.

![chlimage_1-121](assets/chlimage_1-121.png)

### Server-URL für Inhaltsaktualisierung {#content-update-server-url}

Eine der wichtigsten Funktionen von AEM Apps ist die Möglichkeit, mit ContentSync neue Inhalte von einer Mobile App anzufordern, bei denen es sich bei Inhalten um HTML-Ressourcen, Seiten, Video, Bilder, Text usw. handeln kann. Nachdem ein Inhaltsautor Inhalte aktualisiert und dann veröffentlicht hat, stellt der Server die Inhaltsaktualisierung für die Mobile App zum Herunterladen bereit.

Die Eigenschaft &quot;Content Update Server URL&quot;ist die URL, die auf eine Veröffentlichungsinstanz verweisen muss, entweder direkt oder über Dispatcher oder CDN. Das Format der URL lautet einfach:

`https://[hostname]:[port]`

>[!NOTE]
>
>Wenn Ihre Autorenserverinstanz auf viele Veröffentlichungs-Server-Instanzen repliziert (gängige Architektur für AEM), hat jeder Veröffentlichungsserver denselben Aktualisierungsinhalt. Der Grund dafür ist, dass die Aktualisierung auf dem Autor aufbaut und auf allen Veröffentlichungsinstanzen repliziert wird. Grundsätzlich werden Lastenausgleich und Failover vollständig unterstützt.

### Registerkarte &quot;Plug-ins&quot; {#the-plugins-tab}

Auf der Registerkarte **Plug-ins** werden die Plug-ins beschrieben, die mit Ihrer App verknüpft sind. Diese Informationen werden verwendet, um das entsprechende Plug-in während eines Builds abzurufen.

![chlimage_1-122](assets/chlimage_1-122.png)

### Registerkarte &quot;Screenshots&quot; {#the-screenshots-tab}

Auf der Registerkarte **Screenshots** werden die unterstützten Screenshot-Auflösungen auf verschiedenen Plattformen angezeigt.

![chlimage_1-123](assets/chlimage_1-123.png)

>[!NOTE]
>
>Informationen zum Hinzufügen und Entfernen von Screenshots finden Sie unter [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md).

### Registerkarte &quot;Authentifizierung&quot; {#the-authentication-tab}

Auf der Registerkarte **Authentifizierung** können Sie einen OAuth-Client auswählen, der mit Ihrer Anwendung verknüpft werden soll, und Entwicklern die Verwendung der OAuth-Authentifizierung von Adobe Experience Manager ermöglichen.

![chlimage_1-124](assets/chlimage_1-124.png)

### Die nächsten Schritte {#the-next-steps}

Nachdem Sie sich mit der Verwaltung der App-Kachel im Anwendungs-Dashboard vertraut gemacht haben, lesen Sie die folgenden Ressourcen für andere Authoring-Rollen:

* [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md)
* [App-Definitionen](/help/mobile/phonegap-app-definitions.md)
* [Erstellen einer neuen App mit dem Assistenten zum Erstellen einer App](/help/mobile/phonegap-create-new-app.md)
* [Vorhandene Hybrid-App importieren](/help/mobile/phonegap-adding-content-to-imported-app.md)
* [Content Services](/help/mobile/develop-content-as-a-service.md)

### Sonstige Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Administratoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
