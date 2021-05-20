---
title: Kachel „App verwalten“
seo-title: Kachel „App verwalten“
description: Auf dieser Seite erfahren Sie mehr über die Kachel App verwalten im App-Dashboard, in der Details zur Anwendung geändert werden können.
seo-description: Auf dieser Seite erfahren Sie mehr über die Kachel App verwalten im App-Dashboard, in der Details zur Anwendung geändert werden können.
uuid: bde75ecd-8694-427c-9b16-2c4ab2fd4d8b
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: a87834c9-247c-49fa-9978-a969230db91c
exl-id: 8bcf70ef-94d2-4958-90b5-bc375b360916
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 44%

---

# Kachel „App verwalten“{#manage-app-tile}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

In der Kachel **App verwalten** im App-Dashboard können Sie die Details der Anwendung ändern. Um die Seite „Details“ zu öffnen, klicken Sie in der Kachel „App verwalten“ auf den Link „Details“. Auf der Seite &quot;App verwalten&quot;können Sie die Einstellungen der PhoneGap-Anwendungskonfiguration (config.xml) bearbeiten und Ihre Anwendung für die Übermittlung an die verschiedenen Anwendungsspeicher vorbereiten.

![chlimage_1-116](assets/chlimage_1-116.png)

## Grundlegendes zum Bereich App verwalten {#understanding-the-manage-app-tile}

Sie können einen Drilldown für jede Kachel im Bereich **App verwalten** durchführen, um Details anzuzeigen oder zu bearbeiten, indem Sie auf &quot;..&quot;klicken. in der unteren rechten Ecke.

### Die Registerkarte Allgemein {#the-basic-tab}

Sie können die **Name**, **Autor**, **Kurzbeschreibung** und die **Beschreibung** für Ihre App von dieser Registerkarte aus bearbeiten.

![chlimage_1-117](assets/chlimage_1-117.png)

### Die Registerkarte Erweitert {#the-advanced-tab}

Jede Mobile App-Plattform beschreibt, welche Daten erfasst werden, wobei jeder App Store speziell ausgewählt wird.

Die Plattformanzeige wird durch den Inhalt der config.xml von PhoneGap gesteuert:

```xml
<widget>
<gap:platform name="ios"/>
<gap:platform name="android"/>
</widget>
```

Jeder Appstore von Anbietern, z. B. Apple App Store oder Google Play Store, benötigt mindestens einen Screenshot Ihrer Mobile App, um Ihre Anwendungsdetails für Kunden anzuzeigen. Diese Screenshots können strenge Anforderungen an Dimensionen und Inhalte haben (sie müssen im Grunde die Anwendung wirklich repräsentieren). AEM Apps bietet Unterstützung für die Auswahl und Verwaltung dieser Screenshots für die unterstützten Plattformen und das Anzeigen von Port-Dimensionen, wie es für den Anwendungsspeicher jedes Anbieters erforderlich ist.

>[!NOTE]
>
>Die AEM Verify-App bietet die Möglichkeit, Screenshots in AEM direkt an Ihre App-Details zu senden.
>
>Weitere Informationen finden Sie unter [Mobile Quickstart für AEM Verifizierung](/help/mobile/phonegap-mobile-quickstart.md).

![chlimage_1-118](assets/chlimage_1-118.png)

### Metadaten   {#metadata}

>[!NOTE]
>
>Sobald Sie mit der Kachel **App verwalten** vertraut sind, finden Sie unter [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md) Informationen zum Anzeigen und Bearbeiten der Metadaten.

#### Allgemeine Metadaten {#common-metadata}

Jede Anwendung sollte zugeordnete Metadaten haben, die beim Konfigurieren der verschiedenen Aspekte der Anwendung helfen. Die Seite &quot;App verwalten&quot;ist in zwei verschiedene Bereiche unterteilt, die mit der Metadatenerfassung zusammenhängen. Plattformspezifische Metadaten und allgemeine Metadaten.

Es gibt allgemeine Konfigurationen und Metadaten für alle Plattformen.

In diesem Abschnitt definieren Sie die Server-URL für Inhaltsaktualisierungen, die Einstiegsseite für Ihre mobile Anwendung, die PhoneGap-Version für die Kompilierung, die Version, den Namen und die Beschreibung Ihrer Anwendung und mehr.

**App-** Version ist die funktionierende Version Ihrer Anwendung. Eine bewährte Vorgehensweise ist die aus 3 Stellen bestehende Nummerierung, wobei vor dem ersten Release unter 1.0.0 begonnen werden sollte.

**PhoneGap-** Version ist die Version, in der Sie Ihre Anwendung mit PhoneGap kompilieren möchten. Es ist eine bewährte Vorgehensweise, die jeweils aktuelle Version zu verwenden, damit alle neuen und vorteilhaften Funktionen und Fehlerbehebungen genutzt werden können.

**Die** URL des Inhaltsaktualisierungs-Servers ist die URL, die Ihre Anwendung zum Aufrufen von ContentSync-Aktualisierungen verwendet. Sie muss auf die URL des Dispatchers festgelegt werden oder, wenn Sie keinen Dispatcher verwenden, auf eine der Veröffentlichungsinstanzen, die zum Einbinden von Aktualisierungen über die Inhaltssynchronisierung in Ihre Anwendung verwendet wird.

![chlimage_1-119](assets/chlimage_1-119.png)

>[!NOTE]
>
>Dieser Abschnitt kann leer erscheinen, es sei denn, es liegen Daten zum Ausfüllen der Felder vor.
>
>Im oberen Bereich der Detailansicht finden Sie die Anwendungsversion, PhoneGap-Version und Aktualisierungs-URL. Jeder dieser Werte kann innerhalb der allgemeinen Metadaten festgelegt werden. Die Anwendungs-ID kann jedoch nicht bearbeitet werden.

#### Plattformmetadaten {#platform-metadata}

Alle Plattformen, die in der config.xml von PhoneGap definiert sind, können benutzerdefinierte Plattformeigenschaften enthalten. Ein AEM-Entwickler muss die Inhaltsstruktur kennen, damit diese Eigenschaften erfasst werden können. Ein Beispiel für plattformspezifische Eigenschaften finden Sie für iOS.

Metadaten für alle konfigurierten Plattformen werden jetzt auf der Registerkarte Erweitert der Kachel App verwalten gleichzeitig angezeigt.

>[!NOTE]
>
>Die Abschnitte mit den Plattformmetadaten werden nicht von PhoneGap für eine CLI oder einen PhoneGap-Remote-Build verwendet, sondern die Plattformmetadaten werden von AEM für die Veröffentlichung der App im jeweiligen App-Store erfasst.

Bei Plattformen, die nicht von AEM interpretiert werden können, können die AEM-Entwickler die Benutzeroberfläche so erweitern, dass diese Metadaten erfasst werden und sie später exportiert und bei der Anwendungsveröffentlichung verwendet werden können.

#### iOS-Metadaten {#ios-metadata}

Der Apple App Store erfordert zusätzliche Metadaten für die Veröffentlichung Ihrer App. Im Abschnitt „iOS-Metadaten“ werden die erforderlichen Informationen gesammelt, die dann vom iTMSTransporter-Tool von Apple für die Veröffentlichung von Metadaten im verknüpften Konto des Apple-Entwicklers verwendet werden können.

Um die Apple-spezifischen Metadaten zu erhalten, müssen Sie zunächst Ihre Anwendung auf [https://itunesconnect.apple.com](https://itunesconnect.apple.com/) erstellen. Nach dem Erstellen Ihrer Anwendung generiert Apple Metadaten, die im Abschnitt „iOS-Metadaten“ erforderlich sind, wenn Sie das Apple-Tool iTMSTransporter zum Validieren und Hochladen der Metadaten in itunesconnect.apple.com verwenden möchten. Wenn Sie nur die zu erfassenden Metadaten abrufen möchten, müssen Sie nicht unbedingt die iOS-spezifischen Metadaten ausfüllen. Sie können weiterhin die Metadaten exportieren, die die iOS- und allgemeinen Metadaten zusammenführen, und alle Screenshots in eine ZIP-Datei erfassen, die jederzeit heruntergeladen werden kann.

Die heruntergeladene Zip-Datei enthält eine itmsp-Datei, in der die metadata.xml zu finden ist. Die itmsp-Datei enthält die exportierten Metadaten (innerhalb der Datei &quot;metadata.xml&quot;) sowie alle zugehörigen Screenshots.

Die Exportfunktion ist eine praktische Möglichkeit, Screenshots und Metadaten zu erfassen, um sie dem anbieterspezifischen App Store zur Verfügung zu stellen.

![chlimage_1-120](assets/chlimage_1-120.png)

#### Android-Metadaten {#android-metadata}

Wenn Sie die Android-Plattform auswählen, gibt es zu diesem Zeitpunkt keine benutzerdefinierten Metadaten, die festgelegt werden können. Wenn Sie auf die Download-Schaltfläche klicken, wird eine ZIP-Datei mit einer Eigenschaftendatei generiert, die alle Metadaten und zugehörigen Screenshots enthält.

Die Exportfunktion ist eine praktische Möglichkeit, Screenshots und Metadaten zu erfassen, um sie dem anbieterspezifischen App Store zur Verfügung zu stellen.

![chlimage_1-121](assets/chlimage_1-121.png)

### Server-URL für Inhaltsaktualisierung {#content-update-server-url}

Eine der wichtigsten Funktionen von AEM Apps ist die Möglichkeit, mit ContentSync neue Inhalte von einer Mobile App anzufordern, bei denen es sich bei Inhalten um HTML-Ressourcen, Seiten, Video, Bilder, Text usw. handeln kann. Sobald ein Inhaltsautor Inhalte aktualisiert und dann veröffentlicht hat, stellt der Server die Inhaltsaktualisierung für die Mobile App zum Herunterladen bereit.

Die Eigenschaft &quot;Content Update Server URL&quot;ist die URL, die auf eine Veröffentlichungsinstanz verweisen muss. entweder direkt oder über den Dispatcher oder CDN. Das Format der URL ist ganz einfach:

`https://[hostname]:[port]`

>[!NOTE]
>
>Wenn von Ihrer Autorserverinstanz auf mehrere Veröffentlichungsserverinstanzen repliziert wird (gängige Architektur bei AEM), verfügt jeder Veröffentlichungsserver über denselben Aktualisierungsinhalt, da die Aktualisierung auf der Autorinstanz erstellt wird und von da aus auf alle Veröffentlichungsinstanzen repliziert wird. Grundsätzlich werden Lastenausgleich und Failover vollständig unterstützt.

### Registerkarte &quot;Plug-ins&quot;{#the-plugins-tab}

Auf der Registerkarte **Plugins** werden die Plug-ins beschrieben, die mit Ihrer App verknüpft sind. Diese Informationen werden verwendet, um das entsprechende Plug-in während eines Builds abzurufen.

![chlimage_1-122](assets/chlimage_1-122.png)

### Registerkarte &quot;Screenshots&quot;{#the-screenshots-tab}

Auf der Registerkarte **Screenshots** werden die unterstützten Screenshot-Auflösungen für verschiedene Plattformen angezeigt.

![chlimage_1-123](assets/chlimage_1-123.png)

>[!NOTE]
>
>Informationen zum Hinzufügen und Entfernen von Screenshots finden Sie unter [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md).

### Registerkarte &quot;Authentifizierung&quot;{#the-authentication-tab}

Auf der Registerkarte **Authentifizierung** können Sie einen OAuth-Client auswählen, der mit Ihrer Anwendung verknüpft werden soll, und einem Entwickler die Verwendung der OAuth-Authentifizierung von Adobe Experience Manager ermöglichen.

![chlimage_1-124](assets/chlimage_1-124.png)

### Die nächsten Schritte {#the-next-steps}

Nachdem Sie im Anwendungs-Dashboard Informationen zum Verwalten der App-Kachel erhalten haben, finden Sie in den folgenden Ressourcen weitere Autorenrollen:

* [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md)
* [App-Definitionen](/help/mobile/phonegap-app-definitions.md)
* [Erstellen einer neuen App mit dem Assistenten zum Erstellen einer App](/help/mobile/phonegap-create-new-app.md)
* [Vorhandene Hybrid-App importieren](/help/mobile/phonegap-adding-content-to-imported-app.md)
* [Content Services](/help/mobile/develop-content-as-a-service.md)

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Administratoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
