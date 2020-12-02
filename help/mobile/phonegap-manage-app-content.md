---
title: Erstellen und Verwalten von App-Inhalten
seo-title: Erstellen und Verwalten von App-Inhalten
description: Die Verwaltung von App-Inhalten erfordert gemeinsame Anstrengungen von Entwicklern, Inhaltserstellern und Administratoren.  Autoren bearbeiten Seiten, die wiederum auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden.
seo-description: Die Verwaltung von App-Inhalten erfordert gemeinsame Anstrengungen von Entwicklern, Inhaltserstellern und Administratoren.  Autoren bearbeiten Seiten, die wiederum auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden.
uuid: ca049bad-9be8-47aa-b010-298258feda26
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: 5c8971ab-b07c-4131-b4cb-f34c52425014
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 7%

---


# Erstellen und Verwalten von App-Inhalten{#creating-and-managing-app-content}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Für die Verwaltung von App-Inhalten sind gemeinsame Anstrengungen von [Entwicklern](#developer), Inhaltsinhalten [Autoren](#author) und [Administratoren](#administrator) erforderlich. Autoren bearbeiten Seiten, die wiederum auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden.

Schließlich veröffentlichen Administratoren den aktualisierten App-Inhalt strategisch.

>[!NOTE]
>
>**Voraussetzung**:
>
>In [Bereitstellen und Warten](/help/sites-deploying/deploy.md) wurden Entwickler mit AEM System von Komponenten und Vorlagen vertraut.

## Die Kachel &quot;Seiteninhalt verwalten&quot;{#the-manage-page-content-tile}

>[!CAUTION]
>
>Wenn Sie keine vordefinierte App-Vorlage verwenden, müssen Sie einen Content Sync-Handler konfigurieren, um die Veröffentlichung neuer App-Inhalte für OTA zu aktivieren.
>
>Weitere Informationen finden Sie unter [Mobil mit Inhaltssynchronisierung](/help/mobile/phonegap-contentsync.md) im Abschnitt &quot;Entwickler&quot;.

Hier können Inhalte in AEM Mobile ähnlich wie in AEM Sites erstellt, bearbeitet und gelöscht werden.

Die Kachel **Seiteninhalt verwalten** zeigt die Anzahl der Seiten verwalteten Inhalts an und die letzte Änderung für eine bestimmte Nutzlast. Durch Klicken auf die einzelnen Datensätze in diesem Bereich können Sie Details für den Inhalt anzeigen, um Seiten zu erstellen, zu kopieren, zu verschieben, zu löschen und zu aktualisieren.

Sobald der Inhalt aktualisiert wurde, können Administratoren eine Content Update Payload Over-the-Air (OTA) für Kunden über die Kachel **Content Packages verwalten veröffentlichen.**

![chlimage_1-161](assets/chlimage_1-161.png)

Wählen Sie eines der aufgelisteten Inhaltspakete aus, um Inhalte wie das Erstellen, Bearbeiten oder Entfernen von Seiten, das Ändern der Navigation und Seitenreihenfolge, das Erstellen oder Aktualisieren von Inhalten wie Kopieren (Text) und Medien zu erstellen oder zu bearbeiten.

Hinweis *Alles ist Inhalt*, d. h. Anwendungsstile, Kopie (Text), Medien, Seiten, Navigation und Targeting von Inhalten können alle bearbeitet und aktualisiert werden, ohne dass ein Besuch in einem App Store stattfindet.

Um AEM Mobile-Inhalte bearbeiten zu können, *AEM Autoren *benötigen ein fundiertes Verständnis der Benutzeroberfläche zur Bearbeitung AEM Inhalte: [Authoring-Seiten in AEM.](/help/sites-authoring/qg-page-authoring.md)

## Die Kachel &quot;Inhaltspakete verwalten&quot;{#the-manage-content-packages-tile}

Hier können *AEM Administratoren* ihre Apps schnell und einfach aktualisieren, um ansprechende Erlebnisse und aktuelle Inhalte bereitzustellen, um die Markeninteraktion zu fördern und Geschäftsziele zu erreichen, ohne dass ein erneutes Einreichen von Entwicklern oder App Stores erforderlich ist.

![chlimage_1-162](assets/chlimage_1-162.png)

Sobald *AEM-Autoren* Inhalte über die Kachel &quot;Inhalt verwalten&quot;hinzugefügt oder geändert haben, können *AEM Administratoren* diese Änderungen an Kunden mit einem Content Packages-Update senden.

Die Aktion &quot;Inhaltspaket&quot;ermöglicht es dem AEM-Autor, Seiteninhalte zu erstellen und zu bearbeiten, während das Entwicklungsteam Änderungen am Design und der Implementierung einer Host-Anwendung vornimmt, einschließlich Navigation, Stil, serverseitige Logik, Vorlagen und Komponenten, und diese Änderungen dann an Kunden weiterzuleiten, ohne dass sie erneut an die verschiedenen Stores zur Verteilung gesendet werden müssen.**

**So veröffentlichen Sie neue oder aktualisierte Inhalte**

Wählen Sie ein Inhaltspaket aus der Kachel, in diesem Beispiel das englische Paket. Beachten Sie, dass ein Dialogfeld zur Inhaltsaktualisierung die entsprechende *Inhaltssynchronisierung*-Liste enthält. Wenn der App-Inhalt seit einer vorherigen Aktualisierung geändert wurde, zeigt der Status *Ausstehend* an, wie unten dargestellt.

![chlimage_1-163](assets/chlimage_1-163.png)

Wählen Sie dann oben rechts die Aktion **Stage** aus, um das neue Inhaltsupdate zu erstellen. hinzufügen Sie die entsprechenden Aktualisierungsinformationen und klicken Sie auf Fertig.

![chlimage_1-164](assets/chlimage_1-164.png)

Der *Content Sync*-Handler erstellt dann die erforderlichen Pakete, indem er ein Delta bildet (ein Paket von *nur* was sich geändert hat). Nach Abschluss des Vorgangs wurde dieses Updateinhaltspaket wie unten dargestellt gestaffelt.

Durch die Staging einer Aktualisierung von Inhalten können mehrere Aktualisierungen vorgenommen werden, bevor sie auf OTA für Mobilgeräte veröffentlicht werden.

>[!NOTE]
>
>Der gestaffelte Inhalt kann vor der Veröffentlichung mit der AEM Überprüfungs-App überprüft werden.
>
>Weitere Informationen zur AEM Überprüfungs-App finden Sie unter [Mobile QuickStart für AEM Verifizierung](/help/mobile/phonegap-mobile-quickstart.md).

![chlimage_1-165](assets/chlimage_1-165.png)

Wenn Sie bereit sind, Ihren App-Benutzern mit Content Sync OTA neue Inhalte bereitzustellen, wählen Sie **Publish** wie unten dargestellt.

![chlimage_1-166](assets/chlimage_1-166.png)

### Die nächsten Schritte {#the-next-steps}

Nachdem Sie Informationen zum Erstellen und Verwalten von App-Inhalten im Application Dashboard erhalten haben, finden Sie weitere Informationen zu Authoring-Rollen in den folgenden Ressourcen:

* [Bereich „App verwalten“](/help/mobile/phonegap-app-details-tile.md)
* [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md)
* [App-Definitionen](/help/mobile/phonegap-app-definitions.md)
* [Erstellen einer neuen App mit dem Assistenten zum Erstellen einer App](/help/mobile/phonegap-create-new-app.md)
* [Vorhandene Hybrid-App importieren](/help/mobile/phonegap-adding-content-to-imported-app.md)

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Verantwortlichkeiten von Administratoren und Entwicklern finden Sie in den nachfolgend aufgeführten Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
