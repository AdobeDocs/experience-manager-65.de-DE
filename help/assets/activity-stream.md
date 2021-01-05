---
title: Aktivität des Streams digitaler Assets in der Ansicht der Zeitschiene
description: Dieser Artikel beschreibt, wie Sie Aktivitätsprotokolle für Assets in der Timeline anzeigen können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 12c56c27c7f97f1029c757ec6d28f482516149d0
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 69%

---


# Aktivitäts-Stream in der Timeline {#activity-stream-in-timeline}

Diese Funktion zeigt Aktivitätsprotokolle für Assets in der Timeline an. Wenn Sie einen der folgenden Asset-bezogenen Vorgänge in [!DNL Adobe Experience Manager Assets] ausführen, wird die Zeitschiene durch die Stream-Funktion der Aktivität aktualisiert, um die Aktivität widerzuspiegeln.

Folgende Vorgänge werden im Aktivitäts-Stream protokolliert:

* Erstellen
* Löschen
* Download (einschließlich Wiedergaben)
* Veröffentlichung
* Veröffentlichung rückgängig machen
* Genehmigen
* Ablehnen
* Verschieben

Die in der Timeline angezeigten Aktivitätsprotokolle werden aus dem Ordner `/var/audit/com.day.cq.dam/content/dam` in CRX abgerufen, in dem Protokolldateien gespeichert werden. Darüber hinaus wird die Aktivität der Zeitschiene protokolliert, wenn neue Assets hochgeladen oder vorhandene Assets geändert und über [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) oder [Experience Manager Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html) in [!DNL Experience Manager] eingecheckt werden.

>[!NOTE]
>
>Übergangsarbeitsabläufe werden nicht in der Timeline angezeigt, da keine Verlaufsinformationen für diese Arbeitsabläufe gespeichert werden.

Um den Aktivitätsstream anzuzeigen, führen Sie einen oder mehrere Vorgänge für die Assets aus, wählen Sie das Asset aus und wählen Sie dann **[!UICONTROL Timeline]** aus der GlobalNav-Liste aus.

![timeline-2](assets/timeline-2.png)

In der Timeline wird der Aktivitäts-Stream für die mit den Assets ausgeführten Vorgänge angezeigt.

![aktivität_stream](assets/activity_stream.png)

>[!NOTE]
>
>Der standardmäßige Speicherort für Aufgaben des Typs **[!UICONTROL Veröffentlichen]** und **[!UICONTROL Veröffentlichung rückgängig machen]** befindet sich in `/var/audit/com.day.cq.replication/content`. Für Aufgaben des Typs **[!UICONTROL Verschieben]** ist der standardmäßige Speicherort `/var/audit/com.day.cq.wcm.core.page`.
