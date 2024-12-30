---
title: Erstellen und Verwalten von App-Inhalten
description: Die Verwaltung von App-Inhalten erfordert eine gemeinsame Anstrengung von Entwicklern, Inhaltsautoren und Administratoren. Autoren bearbeiten Seiten, die auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
exl-id: 9d350935-129a-40d3-89f4-2e6f69676e5e
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 5%

---

# Erstellen und Verwalten von App-Inhalten{#creating-and-managing-app-content}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Die Verwaltung von App-Inhalten erfordert eine gemeinsame Anstrengung [Entwickler](#developer), [Autoren](#author) und [Administratoren](#administrator). Autoren bearbeiten Seiten, die auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden.

Schließlich veröffentlichen Admins den aktualisierten App-Inhalt strategisch.

>[!NOTE]
>
>**Voraussetzung**:
>
>In [Bereitstellung und Wartung](/help/sites-deploying/deploy.md) haben sich Entwicklerinnen und Entwickler mit Systemkomponenten und Vorlagen in Adobe Experience Manager (AEM) vertraut gemacht.

## Die Kachel „Seiteninhalt verwalten“ {#the-manage-page-content-tile}

>[!CAUTION]
>
>Wenn Sie keine vordefinierte App-Vorlage verwenden, müssen Sie einen Inhaltssynchronisierungs-Handler konfigurieren, um die Veröffentlichung neuer App-Inhalte in OTA zu ermöglichen.
>
>Weitere [ finden Sie ](/help/mobile/phonegap-contentsync.md) Abschnitt „Mobile mit Inhaltssynchronisierung“ im Entwicklerbereich.

Hier können Inhalte in AEM Mobile auf die gleiche Weise wie in AEM Sites erstellt, bearbeitet und gelöscht werden.

Die **Kachel Seiteninhalt verwalten** zeigt die Anzahl der Seiten mit verwaltetem Inhalt und der letzten Änderung für eine bestimmte Payload an. Sie können Inhalte aufschlüsseln, um Seiten zu erstellen, zu kopieren, zu verschieben, zu löschen und zu aktualisieren, indem Sie auf jeden Datensatz in der Kachel klicken.

Nachdem der Inhalt aktualisiert wurde, können Admins über die Kachel Inhaltspakete verwalten eine Inhaltsaktualisierungs-Payload (OTA) **Kunden veröffentlichen**

![chlimage_1-161](assets/chlimage_1-161.png)

Wählen Sie eines der aufgelisteten Inhaltspakete aus, um Inhalte zu erstellen oder zu bearbeiten, z. B. Seiten zu erstellen, zu bearbeiten oder zu entfernen, die Navigation und Seitenreihenfolge zu ändern, Inhalte wie z. B. zu kopieren (Text) und Medien zu erstellen oder zu aktualisieren.

Hinweis *Alles ist Inhalt*, d. h. Anwendungsstile, Kopien (Text), Medien, Seiten, Navigation und Targeting von Inhalten können alle ohne einen Besuch eines App-Stores bearbeitet und aktualisiert werden.

Um AEM Mobile-Inhalte bearbeiten zu können, benötigen AEM-Autorinnen und -Autoren ein fundiertes Verständnis der Inhaltsbearbeitungsoberfläche von AEM: [Authoring von Seiten in AEM.](/help/sites-authoring/qg-page-authoring.md)

## Die Kachel Inhaltspakete verwalten {#the-manage-content-packages-tile}

Hier können *AEM-Administratoren* ihre Apps schnell und einfach aktualisieren, um ansprechende Erlebnisse und aktuelle Inhalte bereitzustellen, um die Markeninteraktion zu fördern und Geschäftsziele zu erreichen, ohne dass ein Entwickler oder ein App Store erneut übermittelt werden muss.

![chlimage_1-162](assets/chlimage_1-162.png)

Sobald *AEM-* Inhalte über die Kachel „Inhalt verwalten“ hinzugefügt oder geändert haben, können *AEM-* diese Änderungen mit einer Aktualisierung der Inhaltspakete an Kunden senden.

Mit der Inhaltspaketaktion kann die *AEM-Autoreninstanz* Seiteninhalte erstellen und bearbeiten, während das Entwicklungs-Team Änderungen am Design und an der Implementierung einer Hostanwendung vornimmt, einschließlich Navigation, Stil, Server-seitiger Logik, Vorlagen und Komponenten, und diese Änderungen dann an Kundinnen und Kunden von OTA überträgt, ohne erneut an die verschiedenen Stores zur Verteilung übermitteln zu müssen.

**So veröffentlichen Sie neue oder aktualisierte Inhalte**

Wählen Sie ein Inhaltspaket aus der Kachel aus, in diesem Beispiel das englische Paket. Beachten Sie, dass im Dialogfeld Inhaltsaktualisierung die entsprechende Konfiguration *Inhaltssynchronisierung* aufgeführt wird. Wenn der App-Inhalt seit einer vorherigen Aktualisierung geändert wurde, wird der Status *Ausstehend* angezeigt, wie unten dargestellt.

![chlimage_1-163](assets/chlimage_1-163.png)

Wählen Sie als Nächstes oben rechts die **Staging**-Aktion aus, um die Inhaltsaktualisierung zu erstellen. Fügen Sie die entsprechenden Aktualisierungsinformationen hinzu und klicken Sie auf Fertig.

![chlimage_1-164](assets/chlimage_1-164.png)

Der *Content Sync*-Handler erstellt dann die erforderlichen Pakete, indem er ein Delta-Paket (ein Paket aus *nur* Änderungen) bildet. Nach Abschluss des Updates wurde dieses Inhaltspaket bereitgestellt, wie unten dargestellt.

Beim Staging einer Inhaltsaktualisierung können mehrere Aktualisierungen vorgenommen werden, bevor sie auf OTA-Geräten veröffentlicht werden.

>[!NOTE]
>
>Der bereitgestellte Inhalt kann vor der Veröffentlichung mit der AEM-Überprüfungs-App überprüft werden.
>
>Siehe [Mobile Schnellstart für AEM-Überprüfung](/help/mobile/phonegap-mobile-quickstart.md) für weitere Informationen zur AEM-Verifizierungs-App.

![chlimage_1-165](assets/chlimage_1-165.png)

Wenn Sie bereit sind, Ihren App-Benutzern mit Content Sync OTA neue Inhalte bereitzustellen, wählen Sie **Publish** aus, wie unten dargestellt.

![chlimage_1-166](assets/chlimage_1-166.png)

### Die nächsten Schritte {#the-next-steps}

Nachdem Sie sich mit dem Erstellen und Verwalten von App-Inhalten im Anwendungs-Dashboard vertraut gemacht haben, finden Sie weitere Informationen in den folgenden Ressourcen für andere Authoring-Rollen:

* [Verwalten der App-Kachel](/help/mobile/phonegap-app-details-tile.md)
* [Bearbeiten von App-Metadaten](/help/mobile/phonegap-editmetadata.md)
* [App-Definitionen](/help/mobile/phonegap-app-definitions.md)
* [Erstellen einer neuen App mit dem Assistenten „App erstellen“](/help/mobile/phonegap-create-new-app.md)
* [Importieren einer vorhandenen Hybrid-App](/help/mobile/phonegap-adding-content-to-imported-app.md)

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten eines Administrators bzw. einer Administratorin und eines Entwicklers finden Sie in den folgenden Ressourcen:

* [Entwickeln für Adobe PhoneGap Enterprise mit AEM](/help/mobile/developing-in-phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
