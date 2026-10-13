---
title: Benutzerdefiniertes Wasserzeichen in der PDF-Briefvorschau
description: Erfahren Sie, wie Sie benutzerdefinierte Wasserzeichen in der PDF-Briefvorschau erstellen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
exl-id: 7d90fade-1ca4-41d8-bbf9-45490465784a
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 3f00fc92-85ee-583e-abd1-3bc3d96de3a0
    internal-label: Correspondence Management
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 100%
---
# Benutzerdefiniertes Wasserzeichen in der PDF-Briefvorschau{#custom-watermark-in-letter-pdf-preview}

## Übersicht {#overview}

Agenten-Benutzende zeigen in der Benutzeroberfläche „Korrespondenz erstellen“ eine Vorschau der Korrespondenz in ihrer endgültigen Form an, in der sie zur Nachbearbeitung gesendet wird, z. B. für E-Mails oder zum Drucken.

Um eine nicht autorisierte Nutzung dieser Daten zu verhindern, können Unternehmen der PDF-Vorschau ein Wasserzeichen hinzufügen. Das standardmäßige Wasserzeichen ist „VORSCHAU“ und wird über die gesamte PDF hinweg angezeigt.

Um das Wasserzeichen in der PDF-Vorschau zu aktivieren, wählen Sie die Option **[!UICONTROL Wasserzeichen während der Vorschau anwenden]** in **[!UICONTROL Korrespondenzverwaltungskonfigurationen]** unter https://[server]:[port]/system/console/configMgr.

![default-watermark](assets/default-watermark.png)

Sie können folgende Schritte verwenden, um den Text und das Erscheinungsbild des Wasserzeichens anzupassen.

## Anpassen des Wasserzeichens in der PDF-Vorschau in der Benutzeroberfläche „Korrespondenz erstellen“ {#customizewatermark-}

1. Wechseln Sie zu `https://'[server]:[port]'/[ContextPath]/crx/de` und melden Sie sich als „Administrator“ an.
1. Erstellen Sie im Anwendungsordner einen Ordner mit dem Namen **[!UICONTROL previewwatermark]**, dessen Pfad/Struktur der des Ordners „previewwatermark“ im Ordner „libs“ entspricht:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **previewwatermark** unter dem folgenden Pfad und wählen Sie **Overlay Node**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **Pfad:** /libs/fd/cm/configFiles/previewwatermark

      **Überlagerungsspeicherort:** /apps/

      **Knotentypen abgleichen:** Überprüft

      >[!NOTE]
      >
      >Ändern Sie die /libs-Verzweigung nicht. Alle Änderungen, die Sie vornehmen, gehen möglicherweise verloren, da diese Verzweigung sich ändern kann, wenn Sie:
      >
      >    
      >    
      >    * Ihre Instanz aktualisieren
      >    * einen Hotfix anwenden
      >    * ein Feature Pack installieren
      >    
      >

   1. Klicken Sie auf **OK** und dann auf **Alle speichern**. Der Ordner **[!UICONTROL previewwatermark]** wird unter dem angegebenen Pfad erstellt.

1. Kopieren Sie die ddx-Datei aus dem Ordner „/libs/fd/cm/configFiles/previewwatermark“ in den Ordner „/apps/fd/cm/configFiles/previewwatermark“ und klicken Sie auf **[!UICONTROL Alle speichern]**.
1. Nehmen Sie in der ddx-Datei unter „/apps/fd/cm/configFiles/previewwatermark/“ die gewünschten Änderungen vor.

   ```xml
   <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
    <PDF result="output.pdf">
     <PDF source="input.pdf"/>
           <Watermark opacity="15%" rotation="45">
            <StyledText>
                     <p font-family="Georgia" font-size="70pt" color="black" font-weight="bold">
                         PREVIEW
                    </p>
            </StyledText>
           </Watermark>
    </PDF>
   </DDX>
   ```

   Informationen zum Anpassen des Erscheinungsbildes, des Textes und der Ausrichtung des Wasserzeichens finden Sie unter Hinzufügen und Entfernen von Wasserzeichen und Hintergründen im Dokument [Assembler-Dienst und DDX-Referenz](https://help.adobe.com/de_DE/livecycle/11.0/ddxRef.pdf).

   >[!NOTE]
   >
   >In der DDX-Datei sollten die Verweise auf das Ergebnis und die Quelle für „output.pdf“ und „input.pdf“ unverändert bleiben. Der Name der DDX-Datei sollte ebenfalls nicht geändert werden.

1. Klicken Sie auf **Alle speichern**.
