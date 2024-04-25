---
title: Erstellen von mobilen Anwendungen
description: Mit dem AEM Mobile Dashboard können Sie Ihre Mobile App erstellen, erstellen und bereitstellen sowie Metadaten für Anwendungen erstellen, löschen und bearbeiten. Auf dieser Seite erfahren Sie mehr.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
exl-id: 073daff7-0c1d-4715-bfd4-3e2336e4cb88
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 3%

---

# Erstellen von mobilen Anwendungen{#authoring-mobile-applications}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Mit dem AEM Mobile-Dashboard können Sie Ihre Mobile App erstellen, erstellen und bereitstellen sowie Metadaten für Anwendungen erstellen, löschen und bearbeiten. Sobald Ihre Anwendung live ist, können Sie Anwendungsanalysen einschließlich Lebenszyklus- und Nutzungsmetriken analysieren, um die Kundenkonvertierung und Markenloyalität zu verbessern.

Informationen zum Erstellen Ihrer AEM Mobile-Anwendung finden Sie unter [Erstellen von Mobile Apps](/help/mobile/building-app-mobile-phonegap.md) Seite.

Informationen zum Einrichten der Umgebung und zum Einstieg finden Sie unter [Verwalten von AEM zur Verwendung AEM PhoneGap Enterprise](/help/mobile/administer-phonegap.md).

## Der AEM Mobile Apps-Katalog {#the-aem-mobile-apps-catalog}

Die [AEM Mobile Apps-Katalog](http://localhost:4502/aem/apps.html/content/phonegap) zeigt alle Ihre Mobile App an, die in AEM verwaltet wird.

Stellen Sie sich diesen Katalog als &quot;Landingpage&quot;für AEM Mobile vor, auf der Administratoren eine neue AEM Mobile-Anwendung starten können, indem sie entweder auf der Grundlage einer Vorlage erstellen oder eine vorhandene App hochladen, die bereits von einem Mobile-Entwickler gestartet wurde.

Gehen Sie wie folgt vor, um zur Landingpage des Apps-Katalogs zu gelangen:

1. Navigieren Sie zu **Navigation** und wählen Sie dann **Mobilnummer**.

1. Auswählen **Apps** , um den Apps-Katalog zu öffnen.

![AEM Mobile Apps-Katalog](assets/chlimage_1-135.png)

## Das Dashboard der AEM Mobile-App {#the-aem-mobile-app-dashboard}

Wenn Sie eine AEM Mobile-App aus dem Katalog auswählen, wird ihr Dashboard angezeigt. Hier können Sie Ihre App verwalten, Statistiken anzeigen, Inhalte für Ihre Mobile App erstellen, bereitstellen und verwalten.

Sie können in jede Kachel im AEM Mobile-Dashboard einblenden, um Details anzuzeigen oder zu bearbeiten, indem Sie rechts unten auf &quot;..&quot;klicken.

![AEM Mobile Applications Command Center](assets/chlimage_1-136.png)

### Die Kachel App verwalten {#the-manage-app-tile}

Im Bereich App verwalten werden Ihr Anwendungssymbol, Ihr Name, Ihre Beschreibung, die unterstützten Plattformen sowie der Aufruf der Startseite mit Informationen zu Updates-URL und Version angezeigt. Sie können diese Kachel näher untersuchen, um die PhoneGap-Anwendungskonfiguration (config.xml) zu bearbeiten und zu verwalten und Ihre Anwendung für die Übermittlung an die verschiedenen Anwendungsspeicher zur Verteilung vorzubereiten.

Klicks [here](/help/mobile/phonegap-app-details-tile.md) für Details.

![chlimage_1-137](assets/chlimage_1-137.png)

### Kachel &quot;Seiteninhalt verwalten&quot; {#the-manage-page-content-tile}

Inhalte können in AEM Mobile auf die gleiche Weise erstellt, aktualisiert und gelöscht werden wie in AEM Sites. Die **Kachel &quot;Seiteninhalt verwalten&quot;** zeigt die Anzahl der Seiten verwalteten Inhalts und der zuletzt geänderten Inhalte an. Sie können einen Drilldown in den Inhalt durchführen, um Seiten zu erstellen, zu kopieren, zu verschieben, zu löschen und zu aktualisieren, indem Sie auf jeden Datensatz in der Kachel klicken. Sobald der Inhalt aktualisiert wurde, können Sie Ihren Kunden eine Inhaltsaktualisierung über die **Kachel Inhaltspakete verwalten**

![Inhaltsbereich](assets/chlimage_1-138.png)

### Die Kachel Inhaltspakete verwalten {#the-manage-content-packages-tile}

Nachdem Sie Ihren Inhalt über die Kachel Seiteninhalt verwalten hinzugefügt oder geändert haben, können Sie diese Änderungen mit einem Update der Inhaltsfreigabe an Ihre Kunden senden.

Das Inhaltspaket ermöglicht es dem AEM App-Autor, Seiteninhalte in AEM zu verwalten und Ihr Entwicklerteam zu veranlassen, Ihre PhoneGap Shell-Anwendung zu ändern (d. h. das App-Framework oder die Infrastruktur) und diese Änderungen dann schnell an Ihre Kunden zu senden, ohne dass ein Entwickler dazu aufgefordert werden muss, sich erneut an die verschiedenen Stores zur Verteilung anzumelden.

Das Inhaltspaket erstellt für jedes Update eine ZIP-Datei, die als Inhaltsfreigabepaket gilt. Diese Pakete enthalten HTML-Ressourcen und HTML-Seiten, die beim Rendern der App generiert werden und intelligent genug sind, nur die Dateien zu verpacken, die seit der letzten Aktualisierung geändert wurden.

Die Kachel &quot;Inhaltspaket verwalten&quot; **Typ** -Spalte zeigt entweder &quot;App&quot;an, um Application Shell-Inhalt anzugeben, z. B. das Framework oder die Infrastruktur der App, die von einem Entwickler verwaltet wird, oder &quot;Inhalt&quot;, die den vom Inhaltsautor verwalteten Seiteninhalt darstellt.

Inhalte können als Sprache oder als bestimmter Teil der App dargestellt werden, in dem die App mehrere Inhaltsfreigabe-Pakete nutzt. Die Art und Weise, wie Sie Inhalte bündeln, ist flexibel und hängt vollständig davon ab, wie Sie Inhalte für Ihre Anwendung verwalten möchten.

Die **Geändert** gibt an, wann die Seiten zuletzt geändert wurden.

Die **Staging** gibt an, wann die letzte Inhaltsaktualisierung erstellt wurde. Um eine Inhaltsaktualisierung zu erstellen und Ihre Änderungen zu testen, öffnen Sie einen beliebigen Datensatz in der Kachel und erstellen Sie eine Aktualisierung.

Die **Veröffentlicht** gibt an, wann die letzte Inhaltsaktualisierung veröffentlicht und für Ihre Kunden zur Verfügung gestellt wurde. Um Inhalte zu veröffentlichen, müssen Sie zunächst diesen Inhalt bereitstellen und dann die Aktualisierung veröffentlichen, indem Sie in diese Kachel navigieren und über die Konsole Inhaltsfreigabe-Details veröffentlichen.

![Bereich &quot;Inhaltsfreigabe&quot;](assets/chlimage_1-139.png) ![ContentSync-Paket für die App-Shell](do-not-localize/chlimage_1-5.png)

Dieses Symbol stellt ein Inhaltsfreigabepaket für die App-Shell dar

![Symbol für Inhaltsfreigabe-Paket , das durch zwei quadratische, überlappende Paketsymbole angezeigt wird.](do-not-localize/chlimage_1-6.png)

Diese Symbole stellen ein Inhaltsfreigabepaket für App-Inhalte dar.

### Der PhoneGap Build {#the-phonegap-build-tile}

Die **PhoneGap Build-Kachel** stellt `https://build.phonegap.com` um Remote-Builds zu erstellen und zu hosten. Nach der Erstellung wird der Build entweder als Download oder direkt auf Ihrem Gerät über einen QR-Code bereitgestellt.

Alternativ können Sie die Gerätequelle herunterladen, um sie über die PhoneGap-CLI (`https://docs.phonegap.com/en/3.5.0/guide_cli_index.md.html`).

![PhoneGap Build-Kachel](assets/chlimage_1-140.png)

### Bereich &quot;Metriken&quot; {#the-metrics-tile}

>[!CAUTION]
>
>Die Kachel Metriken wird erst nach der Konfiguration des Cloud-Service angezeigt.
>
>Siehe [Adobe Mobile Services Cloud Service konfigurieren](/help/mobile/configure-adobe-mobile-cloud-service.md) für Details.

AEM Mobile kann über [Adobe Mobile Services SDK](https://experienceleague.adobe.com/docs/mobile.html) (AMS).

Das Kontrollzentrum **Metrikbereich** zeigt zusammenfassende Analysen an, die von AMS für Ihre Anwendung abgerufen wurden. Sie können einen Drilldown im Analyse-Dashboard durchführen, indem Sie rechts unten auf &quot;...&quot;klicken.

![Metrikbereich](assets/chlimage_1-141.png)

### Kachel &quot;Entitätsinhalt verwalten&quot; {#the-manage-entity-content-tile}

Über die Kachel &quot;Entitätsinhalt verwalten&quot;können Sie App-Definitionen hinzufügen und verwalten. Mit App-Definitionen können Sie ermitteln, welche Leerzeichen (und andere Konfigurationen) für die App geeignet sind. Auf diese Weise kann ein neues Leerzeichen hinzugefügt werden, ohne dass die App neu kompiliert werden muss. Die App-Definition wird aktualisiert und enthält die Informationen zu neuen Platzierungen.

Klicks [here](/help/mobile/phonegap-app-definitions.md) , um Ihre App-Definitionen zu erstellen und zu verwalten.

Sie können einen Drilldown im Dashboard zum Verwalten von Entitätsinhalten durchführen, indem Sie rechts unten auf &quot;...&quot;klicken.

![chlimage_1-142](assets/chlimage_1-142.png)

#### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Administratoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
