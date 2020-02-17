---
title: Bearbeiten von Anwendungen
seo-title: Bearbeiten von Anwendungen
description: Mit dem AEM Mobile Dashboard können Sie Ihre mobile Anwendung erstellen, erstellen und bereitstellen, Anwendungsmetadaten erstellen, löschen und bearbeiten. Auf dieser Seite erfahren Sie mehr.
seo-description: Mit dem AEM Mobile Dashboard können Sie Ihre mobile Anwendung erstellen, erstellen und bereitstellen, Anwendungsmetadaten erstellen, löschen und bearbeiten. Auf dieser Seite erfahren Sie mehr.
uuid: 293b5d29-df7e-42dd-ae64-8c677317e7a5
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: abfeea65-102d-4800-abeb-304d61afcc13
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Bearbeiten von Anwendungen{#authoring-mobile-applications}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Mit dem AEM Mobile Dashboard können Sie Ihre mobile Anwendung erstellen, erstellen und bereitstellen, Anwendungsmetadaten erstellen, löschen und bearbeiten. Sobald Ihre Anwendung live ist, können Sie Anwendungsanalysen einschließlich Lebenszyklusmetriken und Nutzungsmetriken analysieren, um die Kundenkonversion und die Markentreue zu verbessern.

To build your AEM Mobile Application, see the [Building Mobile Applications](/help/mobile/building-app-mobile-phonegap.md) page.

Informationen zum Einrichten Ihrer Umgebung und zum Einstieg finden Sie unter [Verwalten von AEM zur Verwendung von AEM PhoneGap Enterprise](/help/mobile/administer-phonegap.md).

## Der AEM Mobile-App-Katalog {#the-aem-mobile-apps-catalog}

The [AEM Mobile Apps Catalog](http://localhost:4502/aem/apps.html/content/phonegap) displays all of your mobile app managed in AEM.

Stellen Sie sich diesen Katalog als &quot;Einstiegsseite&quot;für AEM Mobile vor, auf der Administratoren eine neue AEM Mobile-Anwendung starten können, indem sie entweder eine Vorlage erstellen oder eine App hochladen, die bereits von einem Mobilentwickler gestartet wurde.

Führen Sie die folgenden Schritte aus, um zur Einstiegsseite des Apps-Katalogs zu gelangen:

1. Navigieren Sie zur **Navigation** und wählen Sie dann &quot; **Mobil**&quot;.

1. Wählen Sie &quot; **Apps** &quot;, um den App-Katalog zu öffnen.

![AEM Mobile-App-Katalog](assets/chlimage_1-135.png)

## Das AEM Mobile-App-Dashboard {#the-aem-mobile-app-dashboard}

Wenn Sie eine AEM Mobile-App aus dem Katalog auswählen, wird das entsprechende Dashboard angezeigt. Hier können Sie Ihre Anwendung verwalten, Statistiken anzeigen, Inhalte für Ihre mobile App erstellen, bereitstellen und verwalten.

Sie können jede Kachel im AEM Mobile Dashboard erweitern, um Details anzuzeigen oder zu bearbeiten, indem Sie auf &quot;...&quot;klicken. in der unteren rechten Ecke.

![AEM Mobile-Apps-Befehlszentrale](assets/chlimage_1-136.png)

### Bereich „App verwalten“{#the-manage-app-tile}

Der Bereich „App verwalten“ zeigt Symbol, Name, Beschreibung, unterstützte Plattformen, Quell-URL für Updates sowie Versionsinformationen an. Sie können einen Drilldown in diese Kachel durchführen, um die PhoneGap-Anwendungskonfiguration (config.xml) zu bearbeiten und zu verwalten und Ihre Anwendung für die Übermittlung an die verschiedenen Anwendungsspeicher zur Verteilung vorzubereiten.

Click [here](/help/mobile/phonegap-app-details-tile.md) for details.

![chlimage_1-137](assets/chlimage_1-137.png)

### The Manage Page Content Tile {#the-manage-page-content-tile}

Inhalt kann in AEM Mobile im Prinzip auf dieselbe Weise wie in AEM Sites erstellt, aktualisiert und gelöscht werden. The **Manage Page Content Tile** displays the number of pages of managed content and last modified. Durch Klicken auf die einzelnen Datensätze in diesem Bereich können Sie Details für den Inhalt anzeigen, um Seiten zu erstellen, zu kopieren, zu verschieben, zu löschen und zu aktualisieren. Once content has been updated, you can push a content update to your customers through the **Manage Content Packages Tile.**

![Bereich „Inhalt“](assets/chlimage_1-138.png)

### The Manage Content Packages Tile {#the-manage-content-packages-tile}

Nachdem Sie Ihre Inhalte über die Kachel &quot;Seiteninhalt verwalten&quot;hinzugefügt oder geändert haben, können Sie diese Änderungen mit einem Content Release-Update an Ihre Kunden senden.

Mit dem Content Package kann der AEM App Author Seiteninhalte in AEM verwalten und Ihr Entwicklungsteam Änderungen an Ihrer PhoneGap Shell-Anwendung (d. h. App-Framework oder -Infrastruktur) vornehmen und diese dann schnell an Ihre Kunden weiterleiten, ohne dass ein Entwickler aufgefordert werden muss, sich erneut zur Distribution an die Varios Stores zu wenden.

Content Package erstellt für jedes Update eine ZIP-Datei, die als Inhaltsveröffentlichungspaket bezeichnet wird. Diese Pakete enthalten HTML-Ressourcen und HTML-Seiten, die beim Rendern der App generiert werden und intelligent genug sind, nur die Dateien zu verpacken, die seit der letzten Aktualisierung geändert wurden.

The Manage Content Package Tile&#39;s **Type** column will display either &#39;App&#39; to signify Application Shell content, for example framework or infrastructure of the app managed by a developer or, &#39;Content&#39; which represents page content managed by the content author.

Inhalt kann als Sprache dargestellt werden oder als ein bestimmter Teil der App, in dem mehrere Inhaltsfreigabe-Pakete von der App genutzt werden. Die Art und Weise der Inhaltsbündelung ist flexibel und hängt komplett davon ab, wie Sie den Inhalt Ihrer App verwalten möchten.

Die Spalte **Geändert** gibt an, wann Seiten zuletzt geändert wurden.

Die Spalte **Gestaffelt** zeigt an, wann die letzte Inhaltsaktualisierung erstellt wurde. Um eine neue Inhaltsaktualisierung zu erstellen und die Änderungen gestaffelt bereitzustellen, öffnen Sie einen beliebigen Datensatz in diesem Bereich und erstellen Sie eine neue Aktualisierung.

Die Spalte **Veröffentlicht** zeigt an, wann die letzte Inhaltsaktualisierung veröffentlicht und für die Nutzung durch Ihre Kunden zur Verfügung gestellt wurde. Um Inhalte zu veröffentlichen, müssen Sie zunächst den Inhalt bereitstellen und dann das Update veröffentlichen, indem Sie in diese Kachel blättern und in der Konsole mit den Inhaltsveröffentlichungsdetails veröffentlichen.

![Content Release Tile](assets/chlimage_1-139.png) ![ContentSync-Paket für die App-Shell](do-not-localize/chlimage_1-5.png)

Dieses Symbol stellt ein Inhaltsaktualisierungs-Paket für die App-Shell dar

![](do-not-localize/chlimage_1-6.png)

Dieses Symbol stellt ein Inhaltsaktualisierungs-Paket für den App-Inhalt dar

### Bereich „PhoneGap-Build“ {#the-phonegap-build-tile}

The **PhoneGap Build Tile** connects with [https://build.phonegap.com](https://build.phonegap.com) to build and host remote buids. Nach der Erstellung wird der Build entweder als Download oder direkt über einen QR-Code für Ihr Gerät zur Verfügung gestellt.

Sie können auch die Gerätequelle herunterladen, um die Erstellung lokal über die [PhoneGap-CLI](https://docs.phonegap.com/en/3.5.0/guide_cli_index.md.html) abzuwickeln.

![Bereich „PhoneGap-Build“](assets/chlimage_1-140.png)

### Bereich „Metrik“{#the-metrics-tile}

>[!CAUTION]
>
>Die Kachel &quot;Metriken&quot;wird erst nach der Konfiguration des Cloud-Dienstes angezeigt.
>
>Weitere Informationen finden Sie unter Adobe Mobile Services Cloud-Dienst [konfigurieren](/help/mobile/configure-adobe-mobile-cloud-service.md) .

AEM Mobile integerates with Adobe Analytics through [Adobe Mobile Services SDK](https://www.adobe.com/ca/solutions/digital-marketing/mobile-services/app-sdk.html) (AMS).

Im **Bereich „Metrik“** des Kontrollzentrums wird für Ihre App eine zusammenfassende Analyse mit Daten aus AMS angezeigt. Sie können Details im Analyse-Dashboard anzeigen, indem Sie rechts unten auf „...“ klicken.

![Bereich „Metrik“](assets/chlimage_1-141.png)

### The Manage Entity Content Tile {#the-manage-entity-content-tile}

Mit der Kachel &quot;Entitätsinhalt verwalten&quot;können Sie App-Definitionen hinzufügen und verwalten. Mit App-Definitionen können Sie identifizieren, welche Bereiche (und andere Konfigurationen) für die App geeignet sind. Auf diese Weise kann ein neuer Bereich hinzugefügt werden, ohne dass die App neu kompiliert werden muss. Die App-Definition wird aktualisiert und enthält die Informationen zu allen neuen Bereichen.

Klicken Sie [hier](/help/mobile/phonegap-app-definitions.md) , um Ihre App-Definitionen zu erstellen und zu verwalten.

Sie können einen Drilldown zum Dashboard zum Verwalten von Entitätsinhalten durchführen, indem Sie auf &quot;...&quot;klicken. unten rechts.

![chlimage_1-142](assets/chlimage_1-142.png)

#### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Verantwortlichkeiten von Administratoren und Entwicklern finden Sie in den nachfolgend aufgeführten Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)

