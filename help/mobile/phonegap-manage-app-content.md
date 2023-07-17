---
title: Erstellen und Verwalten von App-Inhalten
description: Die Verwaltung von App-Inhalten erfordert kollektive Anstrengungen von Entwicklern, Inhaltsautoren und Administratoren. Autoren bearbeiten Seiten, die auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
exl-id: 9d350935-129a-40d3-89f4-2e6f69676e5e
source-git-commit: 96e2e945012046e6eac878389b7332985221204e
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 2%

---

# Erstellen und Verwalten von App-Inhalten{#creating-and-managing-app-content}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, die ein Framework-basiertes clientseitiges Rendering von Einzelseiten-Apps erfordern (z. B. React). [Weitere Informationen](/help/sites-developing/spa-overview.md)

Die Verwaltung von App-Inhalten erfordert eine kollektive Anstrengung von [Entwickler](#developer), Inhalt [Autoren](#author)und [Administratoren](#administrator). Autoren bearbeiten Seiten, die auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden.

Schließlich veröffentlichen Administratoren strategisch den aktualisierten App-Inhalt.

>[!NOTE]
>
>**Voraussetzung**:
>
>In [Bereitstellung und Wartung](/help/sites-deploying/deploy.md)-Entwickler wurden mit Systemkomponenten und Vorlagen in Adobe Experience Manager (AEM) vertraut.

## Kachel &quot;Seiteninhalt verwalten&quot; {#the-manage-page-content-tile}

>[!CAUTION]
>
>Wenn Sie keine vordefinierte App-Vorlage verwenden, müssen Sie einen Content Sync-Handler konfigurieren, um die Veröffentlichung neuer App-Inhalte im OTA zu ermöglichen.
>
>Siehe [Mobil mit Inhaltssynchronisierung](/help/mobile/phonegap-contentsync.md) Weitere Informationen finden Sie im Abschnitt für Entwickler .

Hier können Inhalte in AEM Mobile ähnlich wie in AEM Sites erstellt, bearbeitet und gelöscht werden.

Die **Kachel &quot;Seiteninhalt verwalten&quot;** zeigt die Anzahl der Seiten verwalteten Inhalts an und zuletzt geändert für eine bestimmte Payload. Sie können einen Drilldown in den Inhalt durchführen, um Seiten zu erstellen, zu kopieren, zu verschieben, zu löschen und zu aktualisieren, indem Sie auf jeden Datensatz in der Kachel klicken.

Sobald der Inhalt aktualisiert wurde, können Administratoren eine Payload für Inhaltsaktualisierungen Over-the-Air (OTA) für Kunden über die **Kachel &quot;Inhaltspakete verwalten&quot;.**

![chlimage_1-161](assets/chlimage_1-161.png)

Wählen Sie eines der aufgelisteten Inhaltspakete aus, um Inhalte wie das Erstellen, Bearbeiten oder Entfernen von Seiten, das Ändern der Navigation und Seitenreihenfolge, das Erstellen oder Aktualisieren von Inhalten wie Kopieren (Text) und Medien zu erstellen oder zu bearbeiten.

Hinweis *Alles ist Inhalt* bedeutet, dass Anwendungsstile, Kopieren (Text), Medien, Seiten, Navigation und Targeting von Inhalten ohne Besuch eines Appstores alle bearbeitet und aktualisiert werden können.

Zum Bearbeiten von AEM Mobile-Inhalten benötigen AEM Autoren ein fundiertes Verständnis AEM Inhaltsbearbeitungsoberfläche: [Erstellen von Seiten in AEM.](/help/sites-authoring/qg-page-authoring.md)

## Die Kachel Inhaltspakete verwalten {#the-manage-content-packages-tile}

Hier, *AEM Administratoren* Sie können Ihre Apps schnell und einfach aktualisieren, um ansprechende Erlebnisse und aktuelle Inhalte bereitzustellen, um die Markeninteraktion zu fördern und Geschäftsziele zu erreichen, ohne dass Entwickler oder Appstore erneut übermittelt werden müssen.

![chlimage_1-162](assets/chlimage_1-162.png)

Einmal *AEM-Autoren* über die Kachel Inhalt verwalten Inhalt hinzugefügt oder geändert haben, *AEM Administratoren* können diese Änderungen mit einer Aktualisierung von Inhaltspaketen an Kunden weiterleiten.

Die Aktion &quot;Inhaltspaket&quot;ermöglicht die *AEM-Autor* , um Seiteninhalte zu erstellen und zu bearbeiten, während das Entwicklungsteam Änderungen am Design und an der Implementierung einer Host-Anwendung vornimmt, einschließlich Navigation, Stil, serverseitiger Logik, Vorlagen und Komponenten, und diese Änderungen dann an Kunden weiterleitet, ohne dass sie erneut an die verschiedenen Stores zur Verteilung gesendet werden müssen.

**So veröffentlichen Sie neue oder aktualisierte Inhalte**

Wählen Sie ein Inhaltspaket aus der Kachel aus, in diesem Beispiel das englische Paket. Beachten Sie, dass ein Dialogfeld zur Inhaltsaktualisierung die relevanten *Inhaltssynchronisierung* Konfiguration. Wenn der App-Inhalt seit einer vorherigen Aktualisierung geändert wurde, wird der Status angezeigt *Ausstehend*, wie unten dargestellt.

![chlimage_1-163](assets/chlimage_1-163.png)

Wählen Sie als Nächstes die **Staging** -Aktion oben rechts, um die Inhaltsaktualisierung zu erstellen. Fügen Sie die entsprechenden Aktualisierungsinformationen hinzu und klicken Sie auf Fertig .

![chlimage_1-164](assets/chlimage_1-164.png)

Die *Inhaltssynchronisierung* -Handler erstellt dann die erforderlichen Pakete, indem er ein Delta (ein Paket von *only* was sich geändert hat). Nach Abschluss dieser Aktualisierung wurde das Inhaltspaket wie unten dargestellt gestaltet.

Durch das Staging und Aktualisieren von Inhalten können mehrere Aktualisierungen vorgenommen werden, bevor sie in OTA auf Mobilgeräten veröffentlicht werden.

>[!NOTE]
>
>Der gestaffelte Inhalt kann vor der Veröffentlichung mit der AEM Überprüfungs-App überprüft werden.
>
>Siehe [Mobil-Schnellstart für AEM Verifizierung](/help/mobile/phonegap-mobile-quickstart.md) Weitere Informationen zur AEM Verify-App.

![chlimage_1-165](assets/chlimage_1-165.png)

Wenn Sie Ihren App-Benutzern mit Content Sync OTA neue Inhalte bereitstellen möchten, wählen Sie **Veröffentlichen** wie unten dargestellt.

![chlimage_1-166](assets/chlimage_1-166.png)

### Die nächsten Schritte {#the-next-steps}

Nachdem Sie sich mit dem Erstellen und Verwalten von App-Inhalten im Anwendungs-Dashboard vertraut gemacht haben, lesen Sie die folgenden Ressourcen für andere Authoring-Rollen:

* [Die Kachel App verwalten](/help/mobile/phonegap-app-details-tile.md)
* [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md)
* [App-Definitionen](/help/mobile/phonegap-app-definitions.md)
* [Erstellen einer neuen App mit dem Assistenten zum Erstellen einer App](/help/mobile/phonegap-create-new-app.md)
* [Vorhandene Hybrid-App importieren](/help/mobile/phonegap-adding-content-to-imported-app.md)

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Administratoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
