---
title: Erstellen von Mobile Apps
description: Mit dem AEM Mobile-Dashboard können Sie Ihre Mobile App erstellen, erstellen und bereitstellen sowie Anwendungsmetadaten erstellen, löschen und bearbeiten. Auf dieser Seite erfahren Sie mehr.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
exl-id: 073daff7-0c1d-4715-bfd4-3e2336e4cb88
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 1%

---

# Erstellen von Mobile Apps{#authoring-mobile-applications}

{{ue-over-mobile}}

Mit dem AEM Mobile-Dashboard können Sie Ihre Mobile App erstellen, erstellen und bereitstellen sowie Anwendungsmetadaten erstellen, löschen und bearbeiten. Sobald Ihre Anwendung live ist, können Sie die Anwendungsanalyse einschließlich Lebenszyklus- und Nutzungsmetriken analysieren, um die Kundenkonversion und die Markentreue zu verbessern.

Informationen zum Erstellen Ihrer AEM Mobile-Anwendung finden Sie auf [ Seite zum Erstellen ](/help/mobile/building-app-mobile-phonegap.md) Mobile Apps .

Informationen zum Einrichten Ihrer Umgebung und zu den ersten Schritten finden Sie unter [Verwalten von AEM zur Verwendung von AEM PhoneGap Enterprise](/help/mobile/administer-phonegap.md).

## Der AEM Mobile Apps-Katalog {#the-aem-mobile-apps-catalog}

Im [AEM Mobile Apps Catalog](http://localhost:4502/aem/apps.html/content/phonegap) werden alle in AEM verwalteten Mobile Apps angezeigt.

Stellen Sie sich diesen Katalog als „Landingpage“ für AEM Mobile vor, auf der Admins eine neue AEM Mobile-Anwendung starten können, indem sie entweder eine auf einer Vorlage basierende Anwendung erstellen oder eine bereits von einem Mobilentwickler gestartete App hochladen.

Führen Sie die folgenden Schritte aus, um zur Landingpage für den App-Katalog zu gelangen:

1. Navigieren Sie zu **Navigation** und wählen Sie dann **Mobil** aus.

1. Wählen Sie **Apps** aus, um den App-Katalog zu öffnen.

![AEM Mobile Apps-Katalog](assets/chlimage_1-135.png)

## Das Dashboard der AEM Mobile-App {#the-aem-mobile-app-dashboard}

Wenn Sie eine AEM Mobile-App im Katalog auswählen, wird ihr Dashboard angezeigt. Hier können Sie Ihre Mobile App verwalten, Statistiken anzeigen, Inhalte erstellen, bereitstellen und verwalten.

Sie können jede Kachel im AEM Mobile-Dashboard erweitern, um Details anzuzeigen oder zu bearbeiten, indem Sie unten rechts auf &quot;…“ klicken.

![AEM Mobile Applications Command Center](assets/chlimage_1-136.png)

### Verwalten der App-Kachel {#the-manage-app-tile}

Die Kachel „Programm verwalten“ zeigt Ihr Anwendungssymbol, Ihren Namen, Ihre Beschreibung, die unterstützten Plattformen und die Startseite für URL-Updates und Versionsinformationen an. Sie können einen Drilldown in diese Kachel durchführen, um die PhoneGap-Anwendungskonfiguration (config.xml) zu bearbeiten und zu verwalten und Ihre Anwendung für die Übermittlung an die verschiedenen Anwendungsspeicher zur Verteilung vorzubereiten.

Klicken Sie [hier](/help/mobile/phonegap-app-details-tile.md), um weitere Informationen zu erhalten.

![chlimage_1-137](assets/chlimage_1-137.png)

### Die Kachel „Seiteninhalt verwalten“ {#the-manage-page-content-tile}

Inhalte können in AEM Mobile auf die gleiche Weise erstellt, aktualisiert und gelöscht werden wie in AEM Sites. Die **Kachel „Seiteninhalt verwalten** zeigt die Anzahl der Seiten mit verwaltetem Inhalt und der letzten Änderung an. Sie können Inhalte aufschlüsseln, um Seiten zu erstellen, zu kopieren, zu verschieben, zu löschen und zu aktualisieren, indem Sie auf jeden Datensatz in der Kachel klicken. Nachdem der Inhalt aktualisiert wurde, können Sie eine Inhaltsaktualisierung über die Kachel „Inhaltspakete verwalten **an Ihre Kunden pushen**

![Inhaltskachel](assets/chlimage_1-138.png)

### Die Kachel Inhaltspakete verwalten {#the-manage-content-packages-tile}

Nachdem Sie Ihren Inhalt über die Kachel Seiteninhalt verwalten hinzugefügt oder geändert haben, können Sie diese Änderungen mit einer Aktualisierung der Inhaltsversion an Ihre Kunden übertragen.

Mit dem Inhaltspaket kann der AEM-App-Autor Seiteninhalte in AEM verwalten und Ihr Entwicklungs-Team Ihre PhoneGap Shell-Anwendung (d. h. das App-Framework oder die Infrastruktur) ändern und diese Änderungen dann schnell an Ihre Kunden senden, ohne einen Entwickler für die erneute Übermittlung an die verschiedenen Stores zur Verteilung verpflichten zu müssen.

Content Package erstellt für jede Aktualisierung eine ZIP-Datei, die als Content Release Package betrachtet wird. Diese Pakete enthalten HTML-Ressourcen und HTML-Seiten, die beim Rendern der App generiert werden, und sind intelligent genug, um nur die Dateien zu verpacken, die seit der letzten Aktualisierung geändert wurden.

Die Spalte **Typ** der Kachel „Inhaltspaket verwalten“ zeigt entweder „App“ an, um den Inhalt der Anwendungs-Shell anzugeben, z. B. Framework oder Infrastruktur der von einem Entwickler verwalteten App oder „Inhalt“, der den vom Inhaltsautor verwalteten Seiteninhalt darstellt.

Inhalte können als Sprache oder als bestimmter Teil der App dargestellt werden, in dem mehrere Content-Release-Pakete von der App genutzt werden. Die Auswahl der Art und Weise, wie Sie Ihre Inhalte bündeln, ist flexibel und hängt vollständig davon ab, wie Sie die Inhalte für Ihr Programm verwalten möchten.

Die Spalte **Geändert** gibt an, wann Seiten zuletzt geändert wurden.

Die Spalte **Gestaffelt** zeigt an, wann die letzte Inhaltsaktualisierung erstellt wurde. Um eine Inhaltsaktualisierung zu erstellen und Ihre Änderungen einzustufen, öffnen Sie einen beliebigen Datensatz in der Kachel und erstellen Sie eine Aktualisierung.

Die Spalte **Veröffentlicht** zeigt an, wann die letzte Inhaltsaktualisierung veröffentlicht und für Ihre Kunden verfügbar gemacht wurde. Um Inhalte zu veröffentlichen, müssen Sie zunächst diesen Inhalt bereitstellen und dann die Aktualisierung veröffentlichen, indem Sie einen Drilldown in diese Kachel durchführen und die Veröffentlichung über die Konsole „Details zur Inhaltsveröffentlichung“ durchführen.

![Content-Release-Kachel](assets/chlimage_1-139.png) ![ContentSync-Paket für die App-Shell](do-not-localize/chlimage_1-5.png)

Dieses Symbol stellt ein Content-Release-Paket für die Shell des Programms dar

![Das Symbol für das Inhaltspaket wird durch zwei quadratische, sich überlappende Paketsymbole angezeigt.](do-not-localize/chlimage_1-6.png)

Diese Symbole stellen ein Inhaltspaket für App-Inhalte dar

### Die Kachel PhoneGap Build {#the-phonegap-build-tile}

Die **PhoneGap Build-Kachel** stellt eine Verbindung mit `https://build.phonegap.com` her, um Remote-Builds zu erstellen und zu hosten. Nach der Erstellung wird der Build entweder als Download oder direkt über einen QR-Code auf Ihrem Gerät zur Verfügung gestellt.

Alternativ können Sie die Gerätequelle herunterladen, um lokal über die PhoneGap-CLI (`https://docs.phonegap.com/en/3.5.0/guide_cli_index.md.html`) zu erstellen.

![PhoneGap Build-Kachel](assets/chlimage_1-140.png)

### Die Kachel Metriken . {#the-metrics-tile}

>[!CAUTION]
>
>Die Kachel Metriken wird erst angezeigt, nachdem Sie den Cloud-Service konfiguriert haben.
>
>Weitere [ finden Sie unter „Konfigurieren des Adobe Mobile Services](/help/mobile/configure-adobe-mobile-cloud-service.md)Cloud Service&quot;.

AEM Mobile lässt sich über [Adobe Mobile Services SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=de) (AMS) mit Adobe Analytics integrieren.

Die Kachel Control Center **Metriken** zeigt Zusammenfassungsanalysen an, die von AMS für Ihre Anwendung abgerufen wurden. Sie können einen Drilldown im Analytics-Dashboard durchführen, indem Sie unten rechts auf &quot;…“ klicken.

![Metriken-Kachel](assets/chlimage_1-141.png)

### Die Kachel Entitätsinhalt verwalten {#the-manage-entity-content-tile}

Über die Kachel Entitätsinhalt verwalten können Sie App-Definitionen hinzufügen und verwalten. App-Definitionen sind eine Möglichkeit, herauszufinden, welche Platzierungen (und andere Konfigurationen) für die App geeignet sind. Auf diese Weise kann ein neuer Bereich hinzugefügt werden, ohne dass die App neu kompiliert werden muss. Die App-Definition wird aktualisiert und enthält die Informationen für alle neuen Platzierungen.

Klicken Sie [hier](/help/mobile/phonegap-app-definitions.md), um Ihre App-Definitionen zu erstellen und zu verwalten.

Sie können einen Drilldown im Dashboard für die Verwaltung von Entitätsinhalten durchführen, indem Sie unten rechts auf &quot;…“ klicken.

![chlimage_1-142](assets/chlimage_1-142.png)

#### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten eines Administrators bzw. einer Administratorin und eines Entwicklers finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
