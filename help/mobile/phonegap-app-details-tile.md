---
title: Programmkachel verwalten
description: Erfahren Sie mehr über die Kachel „Mobile App verwalten“ im Mobile-App-Dashboard, über die Sie Details zur Mobile App bearbeiten können.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
exl-id: 8bcf70ef-94d2-4958-90b5-bc375b360916
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '1197'
ht-degree: 2%

---

# Programmkachel verwalten{#manage-app-tile}

{{ue-over-mobile}}

Über die Kachel **`Manage App`** im App-Dashboard können Sie Details zur Anwendung bearbeiten. Um die Detailseite zu öffnen, klicken Sie auf den Link Details der **`Manage App`**. Von der Seite **`Manage App`** aus können Sie die Einstellungen für die PhoneGap-Anwendungskonfiguration (config.xml) bearbeiten und Ihren Antrag für die Übermittlung an die verschiedenen Anwendungsspeicher vorbereiten.

![chlimage_1-116](assets/chlimage_1-116.png)

## Grundlegendes zur `Manage App` Kachel {#understanding-the-manage-app-tile}

Sie können jede Kachel in der **`Manage App`** Kachel einzeln betrachten, um Details anzuzeigen oder zu bearbeiten, indem Sie unten rechts auf &quot;…“ klicken.

### Die Registerkarte Allgemein {#the-basic-tab}

Sie können die **Name**, **Autor**, **Kurzbeschreibung** und **Beschreibung** für Ihre App auf dieser Registerkarte bearbeiten.

![chlimage_1-117](assets/chlimage_1-117.png)

### Die Registerkarte Erweitert {#the-advanced-tab}

Jede Mobile-App-Plattform beschreibt, welche Daten erfasst werden und zielt speziell auf jeden Mobile-App-Store ab.

Die angezeigten Plattformen werden durch den Inhalt „PhoneGap.xml“ gesteuert:

```xml
<widget>
<gap:platform name="ios"/>
<gap:platform name="android"/>
</widget>
```

Jeder Anwendungs-Store eines Anbieters - z. B. Apple App Store oder Google Play Store - benötigt einen oder mehrere Screenshots Ihrer Mobile App, um Ihre Anwendungsdetails für Kunden anzuzeigen. Diese Screenshots können strenge Anforderungen an Dimensionen und Inhalte haben (im Grunde müssen sie wirklich die Anwendung darstellen). AEM Apps unterstützt die Auswahl und Verwaltung dieser Screenshots für die unterstützten Plattformen und die Anzeige der Portdimensionen, wie sie vom Anwendungsspeicher jedes Anbieters benötigt werden.

>[!NOTE]
>
>Mit der AEM Verify-App können Sie Screenshots direkt an Ihre App-Details in AEM senden.
>
>Siehe [Mobile-Schnellstart für AEM-Überprüfung](/help/mobile/phonegap-mobile-quickstart.md) für weitere Details.

![chlimage_1-118](assets/chlimage_1-118.png)

### Metadaten {#metadata}

>[!NOTE]
>
>Wenn Sie mit der **`Manage App`** Kachel vertraut sind, finden Sie weitere Informationen unter [Bearbeiten von App](/help/mobile/phonegap-editmetadata.md), um die Metadaten anzuzeigen und zu bearbeiten.

#### Allgemeine Metadaten {#common-metadata}

Jedes Programm sollte über zugehörige Metadaten verfügen, die bei der Konfiguration verschiedener Aspekte des Programms helfen. Die Seite „Programm verwalten“ ist in zwei verschiedene Bereiche für die Metadatenerfassung unterteilt. Plattformspezifische Metadaten und allgemeine Metadaten.

Konfiguration und Metadaten sind für alle Plattformen gleich.

In diesem Abschnitt definieren Sie die URL des Content Update Server, die Landingpage für Ihre Mobile App, die PhoneGap-Version für die Kompilierung, Ihre Anwendungsversion, den Namen, die Beschreibung und mehr.

**App-Version** ist die funktionierende Version Ihres Programms. Als Best Practice wird allgemein eine 3-Dezimalnotation verwendet, die vor der ersten Veröffentlichung unter 1.0.0 beginnen sollte.

**PhoneGap Version** ist die Version, in der Sie Ihr Programm mit PhoneGap kompilieren möchten. Es empfiehlt sich, stets die aktuelle Version zu verwenden, um sicherzustellen, dass Sie über die neuesten und besten Funktionen und Fehlerbehebungen verfügen.

**Content Update Server URL** ist die URL, mit der Ihre Anwendung ContentSync-Updates abruft. Sie muss auf Ihre Dispatcher-URL festgelegt sein oder, falls keine Dispatcher verwendet wird, auf eine Ihrer Veröffentlichungsinstanzen, die zum Bereitstellen von ContentSync-Aktualisierungen für Ihre Anwendung verwendet wird.

![chlimage_1-119](assets/chlimage_1-119.png)

>[!NOTE]
>
>Dieser Abschnitt kann leer erscheinen, es sei denn, die Felder werden mit Daten ausgefüllt.
>
>Oben in der Detailansicht sehen Sie Anwendungsversion, PhoneGap-Version und Update-URL. Jeder dieser Werte kann im Abschnitt „Allgemeine Metadaten“ festgelegt werden. Die Anwendungs-ID kann jedoch nicht bearbeitet werden.

#### Platform-Metadaten {#platform-metadata}

Jede Plattform, die in der Datei PhoneGap.xml definiert ist, kann benutzerdefinierte Plattformeigenschaften enthalten. Ein AEM-Entwickler muss die Inhaltsstruktur bereitstellen, um diese Eigenschaften zu erfassen. Ein bereitgestelltes Beispiel für plattformspezifische Eigenschaften finden Sie für iOS.

Die Metadaten für alle konfigurierten Plattformen werden jetzt gleichzeitig auf der Registerkarte Erweitert der Kachel `Manage App` angezeigt.

>[!NOTE]
>
>Die Platform-Metadatenabschnitte werden von PhoneGap während einer CLI oder eines Builds von Remote PhoneGap nicht verwendet. Stattdessen versucht AEM, Metadaten für Plattformen zu erfassen, damit sie später beim Senden an den Anwendungsspeicher des Zielanbieters verwendet werden können.

Für Plattformen, die von AEM nicht verstanden werden, ist es dennoch möglich, dass ein AEM-Entwickler die Benutzeroberfläche erweitert, um diese Metadaten zu erfassen, die später exportiert und während des Antragsübermittlungsprozesses verwendet werden können.

#### iOS-Metadaten {#ios-metadata}

Der Apple AppStore benötigt zusätzliche Metadaten, um Ihr Programm zur Verteilung zu übermitteln. Im Abschnitt mit den iOS-Metadaten wird versucht, die erforderlichen Informationen zu erfassen, die vom iTMSTransporter-Tool von Apple verwendet werden können, um die Metadaten im zugehörigen Apple-Entwicklerkonto zu veröffentlichen.

Um die Apple-spezifischen Metadaten abzurufen, erstellen Sie Ihre Anwendung auf [https://itunesconnect.apple.com](https://itunesconnect.apple.com/). Nach der Erstellung Ihres Programms generiert Apple Metadaten, die für den Abschnitt &quot;iOS-Metadaten“ erforderlich sind, wenn Sie die Metadaten mit dem Apple iTMSTransporter-Tool validieren und auf itunesconnect.apple.com hochladen möchten. Wenn Sie die zu erfassenden Metadaten abrufen möchten, müssen Sie die iOS-spezifischen Metadaten nicht ausfüllen. Sie können weiterhin die Metadaten exportieren, in denen die iOS und die allgemeinen Metadaten zusammengeführt werden, und alle Screenshots in einer ZIP-Datei erfassen, die jederzeit heruntergeladen werden kann.

Die heruntergeladene ZIP-Datei enthält eine itmsp-Datei, die auf die Datei metadata.xml überprüft werden kann. Die itmsp-Datei enthält die exportierten Metadaten (innerhalb der Datei „metadata.xml„) sowie alle damit verbundenen Screenshots.

Die Exportfunktion bietet eine praktische Möglichkeit, Screenshots und Metadaten zu erfassen, die zur Eingabe in den anbieterspezifischen Anwendungsspeicher an den Anwendungsherausgeber weitergeleitet werden können.

![chlimage_1-120](assets/chlimage_1-120.png)

#### Android™-Metadaten {#android-metadata}

Bei der Auswahl der Android™-Plattform gibt es derzeit keine benutzerdefinierten Metadaten, die festgelegt werden können. Beim Klicken auf die Schaltfläche Herunterladen wird eine ZIP-Datei mit einer Eigenschaftendatei generiert, die alle Metadaten und zugehörigen Screenshots enthält.

Die Exportfunktion bietet eine praktische Möglichkeit, Screenshots und Metadaten zu erfassen, die zur Eingabe in den anbieterspezifischen Anwendungsspeicher an den Anwendungsherausgeber weitergeleitet werden können.

![chlimage_1-121](assets/chlimage_1-121.png)

### Server-URL für Inhaltsaktualisierung {#content-update-server-url}

Eine der wichtigsten Funktionen von AEM-Apps ist die Möglichkeit, über ContentSync über eine Mobile App neue Inhalte anzufordern, wobei Inhalte HTML-Ressourcen, Seiten, Videos, Bilder, Text und mehr sein können. Nachdem ein Inhaltsautor Inhalte aktualisiert und dann veröffentlicht hat, stellt der Server die Inhaltsaktualisierung für die Mobile App zum Download bereit.

Die URL-Eigenschaft des Inhaltsaktualisierungsservers ist die URL, die auf eine Veröffentlichungsinstanz verweisen muss, entweder direkt oder über Dispatcher oder CDN. Das Format der URL ist einfach:

`https://[hostname]:[port]`

>[!NOTE]
>
>Wenn Ihre Autorenserverinstanz auf viele Veröffentlichungsserverinstanzen repliziert wird (allgemeine AEM-Architektur), hat jeder Veröffentlichungsserver dieselben Aktualisierungsinhalte. Der Grund dafür ist, dass die Aktualisierung auf der Autoreninstanz basiert und auf allen Veröffentlichungsinstanzen repliziert wird. Grundsätzlich werden Lastenausgleich und Failover vollständig unterstützt.

### Registerkarte „Plug-ins“ {#the-plugins-tab}

Die **Plug-ins** beschreibt die Plug-ins, die mit Ihrer App verbunden sind. Diese Informationen werden verwendet, um das entsprechende Plug-in während eines Builds abzurufen.

![chlimage_1-122](assets/chlimage_1-122.png)

### Die Registerkarte Screenshots {#the-screenshots-tab}

Die **Screenshots** zeigt die unterstützten Screenshot-Auflösungen auf verschiedenen Plattformen an.

![chlimage_1-123](assets/chlimage_1-123.png)

>[!NOTE]
>
>Informationen zum Hinzufügen und Entfernen von Screenshots finden Sie unter [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md).

### Die Registerkarte Authentifizierung {#the-authentication-tab}

Auf **Registerkarte** Authentifizierung“ können Sie einen OAuth-Client auswählen, der mit Ihrer Anwendung verknüpft werden soll, und es Entwickelnden ermöglichen, die OAuth-Authentifizierung von Adobe Experience Manager zu verwenden.

![chlimage_1-124](assets/chlimage_1-124.png)

### Die nächsten Schritte {#the-next-steps}

Nachdem Sie sich mit der Verwaltung der App-Kachel im Anwendungs-Dashboard vertraut gemacht haben, finden Sie die folgenden Ressourcen für andere Authoring-Rollen:

* [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md)
* [App-Definitionen](/help/mobile/phonegap-app-definitions.md)
* [Erstellen einer neuen App mit dem Assistenten „App erstellen“](/help/mobile/phonegap-create-new-app.md)
* [Importieren einer vorhandenen Hybrid-App](/help/mobile/phonegap-adding-content-to-imported-app.md)
* [Content Services](/help/mobile/develop-content-as-a-service.md)

### Sonstige Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten eines Administrators bzw. einer Administratorin und eines Entwicklers finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
