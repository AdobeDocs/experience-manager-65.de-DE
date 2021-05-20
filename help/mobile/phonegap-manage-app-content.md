---
title: Erstellen und Verwalten von App-Inhalten
seo-title: Erstellen und Verwalten von App-Inhalten
description: Die Verwaltung von App-Inhalten erfordert kollektive Anstrengungen von Entwicklern, Inhaltsautoren und Administratoren.  Autoren bearbeiten Seiten, die wiederum auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden.
seo-description: Die Verwaltung von App-Inhalten erfordert kollektive Anstrengungen von Entwicklern, Inhaltsautoren und Administratoren.  Autoren bearbeiten Seiten, die wiederum auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden.
uuid: ca049bad-9be8-47aa-b010-298258feda26
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: 5c8971ab-b07c-4131-b4cb-f34c52425014
exl-id: 9d350935-129a-40d3-89f4-2e6f69676e5e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 7%

---

# Erstellen und Verwalten von App-Inhalten{#creating-and-managing-app-content}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Die Verwaltung von App-Inhalten erfordert einen kollektiven Aufwand von [Entwicklern](#developer), Inhalten [Autoren](#author) und [Administratoren](#administrator). Autoren bearbeiten Seiten, die wiederum auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden.

Schließlich veröffentlichen Administratoren strategisch den aktualisierten App-Inhalt.

>[!NOTE]
>
>**Voraussetzung**:
>
>In [Bereitstellen und Warten](/help/sites-deploying/deploy.md) haben sich Entwickler mit AEM System von Komponenten und Vorlagen vertraut gemacht.

## Bereich &quot;Seiteninhalt verwalten&quot;{#the-manage-page-content-tile}

>[!CAUTION]
>
>Wenn Sie keine native App-Vorlage verwenden, müssen Sie einen Content Sync-Handler konfigurieren, um die Veröffentlichung neuer App-Inhalte im OTA zu ermöglichen.
>
>Weitere Informationen finden Sie unter [Mobil mit Inhaltssynchronisierung](/help/mobile/phonegap-contentsync.md) im Abschnitt für Entwickler .

Hier können Inhalte in AEM Mobile auf die gleiche Weise erstellt, bearbeitet und gelöscht werden wie in AEM Sites.

Die Kachel **Seiteninhalt verwalten** zeigt die Anzahl der Seiten verwalteten Inhalts an und zuletzt geändert für eine bestimmte Payload. Durch Klicken auf die einzelnen Datensätze in diesem Bereich können Sie Details für den Inhalt anzeigen, um Seiten zu erstellen, zu kopieren, zu verschieben, zu löschen und zu aktualisieren.

Sobald der Inhalt aktualisiert wurde, können Administratoren eine Payload für Inhaltsaktualisierungen Over-the-Air (OTA) für Kunden über die Kachel **Inhaltspakete verwalten veröffentlichen.**

![chlimage_1-161](assets/chlimage_1-161.png)

Wählen Sie eines der aufgelisteten Inhaltspakete aus, um Inhalte zu erstellen oder zu bearbeiten, z. B. Seiten zu erstellen, zu bearbeiten oder zu entfernen, Navigation und Seitenreihenfolge zu ändern, Inhalte wie Kopieren (Text) und Medien zu erstellen oder zu aktualisieren.

Hinweis *Alles ist Inhalt*, d. h. Anwendungsstile, Kopieren (Text), Medien, Seiten, Navigation und das Targeting von Inhalten können ohne Besuch eines Appstores bearbeitet und aktualisiert werden.

Um AEM Mobile-Inhalte zu bearbeiten, benötigen AEM Autoren ein umfassendes Verständnis der AEM Inhaltsbearbeitungsoberfläche: [Authoring von Seiten in AEM.](/help/sites-authoring/qg-page-authoring.md)

## Die Kachel &quot;Inhaltspakete verwalten&quot;{#the-manage-content-packages-tile}

Hier können *AEM Administratoren* ihre Apps schnell und einfach aktualisieren, um ansprechende Erlebnisse und aktuelle Inhalte bereitzustellen, um die Markeninteraktion zu fördern und Geschäftsziele zu erreichen - alles ohne dass Entwickler oder Appstore erneut übermittelt werden müssen.

![chlimage_1-162](assets/chlimage_1-162.png)

Sobald *AEM-Autoren* Inhalte über die Kachel &quot;Inhalt verwalten&quot;hinzugefügt oder geändert haben, können *AEM Administratoren* diese Änderungen an Kunden mit einer Aktualisierung von Inhaltspaketen weiterleiten.

Mit der Aktion &quot;Inhaltspaket&quot;kann der *AEM-Autor* Seiteninhalte erstellen und bearbeiten, während das Entwicklungsteam Änderungen an einem Host-Anwendungsdesign und -Implementierung vornimmt, einschließlich Navigation, Stil, serverseitiger Logik, Vorlagen und Komponenten, und diese Änderungen dann an Kunden weiterleitet, ohne sie an die verschiedenen Stores zur Verteilung erneut senden zu müssen.

**So veröffentlichen Sie neue oder aktualisierte Inhalte**

Wählen Sie ein Inhaltspaket aus der Kachel aus, in diesem Beispiel das englische Paket. Beachten Sie, dass ein Dialogfeld für die Inhaltsaktualisierung die entsprechende *Inhaltssynchronisierung*-Konfiguration auflistet. Wenn der App-Inhalt seit einer vorherigen Aktualisierung geändert wurde, zeigt der Status *Ausstehend* an, wie unten dargestellt.

![chlimage_1-163](assets/chlimage_1-163.png)

Wählen Sie dann oben rechts die Aktion **Stage** aus, um die neue Inhaltsaktualisierung zu erstellen. Fügen Sie die entsprechenden Aktualisierungsinformationen hinzu und klicken Sie auf Fertig .

![chlimage_1-164](assets/chlimage_1-164.png)

Der Handler *Inhaltssynchronisierung* erstellt dann die erforderlichen Pakete, indem er ein Delta bildet (ein Paket von *nur* was geändert wurde). Nach Abschluss dieser Aktualisierung wurde das Inhaltspaket wie unten dargestellt gestaltet.

Durch das Staging und Aktualisieren von Inhalten können mehrere Aktualisierungen vorgenommen werden, bevor sie in OTA auf Mobilgeräten veröffentlicht werden.

>[!NOTE]
>
>Der gestaffelte Inhalt kann vor der Veröffentlichung mit der AEM Überprüfungs-App überprüft werden.
>
>Weitere Informationen zur AEM Verify-App finden Sie unter [Mobile Quickstart für AEM Verifizierung](/help/mobile/phonegap-mobile-quickstart.md) .

![chlimage_1-165](assets/chlimage_1-165.png)

Wenn Sie Ihren App-Benutzern mit Content Sync OTA neue Inhalte bereitstellen möchten, wählen Sie **Publish** aus, wie unten dargestellt.

![chlimage_1-166](assets/chlimage_1-166.png)

### Die nächsten Schritte {#the-next-steps}

Nachdem Sie im Anwendungs-Dashboard Informationen zum Erstellen und Verwalten von App-Inhalten erhalten haben, finden Sie in den folgenden Ressourcen weitere Autorenrollen:

* [Bereich „App verwalten“](/help/mobile/phonegap-app-details-tile.md)
* [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md)
* [App-Definitionen](/help/mobile/phonegap-app-definitions.md)
* [Erstellen einer neuen App mit dem Assistenten zum Erstellen einer App](/help/mobile/phonegap-create-new-app.md)
* [Vorhandene Hybrid-App importieren](/help/mobile/phonegap-adding-content-to-imported-app.md)

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Administratoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
