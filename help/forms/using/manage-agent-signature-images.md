---
title: Verwalten von Agentsignaturbildern
description: Nachdem Sie eine Briefvorlage erstellt haben, können Sie sie dafür verwenden, in AEM Forms Korrespondenzen zu erstellen, indem Sie Daten, Inhalte und Anhänge verwalten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
exl-id: f044ed75-bb72-4be1-aef6-2fb3b2a2697b
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
source-wordcount: '689'
ht-degree: 92%
---
# Verwalten von Agentsignaturbildern{#manage-agent-signature-images}

## Überblick {#overview}

In Correspondence Management können Sie ein Bild verwenden, um Agentsignaturen in Briefen zu rendern. Nachdem Sie das Bild für die Agentsignatur festgelegt haben, können Sie es in Briefen, die Sie erstellen, als Signatur des Absenderagenten ausgeben.

Das agentSignatureImage-DDE ist ein berechnetes DDE zur Darstellung des Signaturbilds des Agenten. Der Ausdruck für dieses berechnete DDE verwendet eine neue benutzerdefinierte Funktion, die vom Baustein „Expression Manager“ bereitgestellt wird. Diese benutzerdefinierte Funktion akzeptiert „agentID“ und „agentFolder“ als Eingabeparameter und ruft den Bildinhalt auf Basis dieser Parameter ab. Über das Systemdatenwörterbuch SystemContext erhalten Briefe in Correspondence Management Zugriff auf Informationen im aktuellen Systemkontext. Der Systemkontext umfasst Informationen zum derzeit angemeldeten Benutzer und zu aktiven Konfigurationsparametern.

Sie können Bilder im cmuserroot-Ordner hinzufügen. In den [Eigenschaften der Correspondence Management-Konfiguration](/help/forms/using/cm-configuration-properties.md) können Sie mithilfe der Eigenschaft „URL für CM-Benutzerelemente“ den Ordner wechseln, aus dem das Agentsignaturbild abgerufen wird.

Der Wert des agentFolder-DDE wird aus dem CMUserRoot-Konfigurationsparameter für die Correspondence Management-Konfigurationseigenschaften abgerufen. Standardmäßig verweist dieser Konfigurationsparameter auf /content/cmUserRoot im CRX-Repository. Sie können den Wert der CMUserRoot-Konfiguration in den Konfigurationseigenschaften ändern.
Sie können die Standardfunktion auch überschreiben, um eine eigene Logik zum Abrufen des Bilds der Benutzerunterschrift zu definieren.

## Agentsignaturbild hinzufügen {#adding-agent-signature-image}

1. Stellen Sie sicher, dass das Agentsignaturbild denselben Namen wie der AEM-Benutzername des Benutzers hat. (Eine Erweiterung wird den Namen der Bilddateien nicht benötigt.)
1. Erstellen Sie in CRX einen Ordner mit dem Namen `cmUserRoot` im aktuellen Ordner.

   1. Rufen Sie `https://'[server]:[port]'/crx/de` auf. Falls erforderlich, melden Sie sich als Administrator an.

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **content** und wählen Sie **Erstellen** > **Ordner erstellen**.

      ![Ordner erstellen](assets/1_createnode_cmuserroot.png)

   1. Geben Sie im Dialogfeld „Ordner erstellen“ den Namen des Ordners als `cmUserRoot` an. Klicken Sie auf **Alle speichern**.

      >[!NOTE]
      >
      >„cmUserRoot“ ist der Standardspeicherort, unter dem AEM nach dem Agentsignaturbild sucht. Sie können dies jedoch ändern, indem Sie die Eigenschaft „URL für CM-Benutzerelemente“ in den [Eigenschaften der Correspondence Management-Konfiguration](/help/forms/using/cm-configuration-properties.md) bearbeiten.

1. Navigieren Sie in Content Explorer zum cmUserRoot-Ordner und fügen Sie das Agentsignaturbild hinzu.

   1. Rufen Sie `https://'[server]:[port]'/crx/explorer/index.jsp` auf. Melden Sie sich ggf. als Admin an.
   1. Klicken Sie auf **Content Explorer**. Content Explorer wird in einem neuen Fenster geöffnet.
   1. Navigieren Sie in Content Explorer zum cmUserRoot-Ordner und wählen Sie ihn aus. Klicken Sie mit der rechten Maustaste auf den Ordner **cmUserRoot** und wählen Sie **Neuer Knoten** aus.

      ![Neuer Knoten in cmUserRoot](assets/2_cmuserroot_newnode.png)

      Nehmen Sie die folgenden Einträge in der Zeile für neue Knoten vor und klicken Sie dann auf das grüne Häkchen.

      **Name:** Max Mustermann (oder der Name Ihrer Agentsignaturdatei)

      **Typ:** nt:file

      Im `cmUserRoot`-Ordner wird ein neuer Ordner mit dem Namen `JohnDoe` (bzw. dem Namen, den Sie im vorigen Schritt angegeben haben) erstellt.

   1. Klicken Sie auf den von Ihnen erstellten neuen Ordner (hier: `JohnDoe`). In Content Explorer wird der Inhalt des Ordners abgeblendet angezeigt.

   1. Doppelklicken Sie auf die **jcr:content**-Eigenschaft, legen Sie als Typ **nt:resource** fest und klicken Sie dann auf das grüne Häkchen, um den Eintrag zu speichern.

      Wenn die Eigenschaft nicht vorhanden ist, erstellen Sie zunächst eine Eigenschaft mit dem Namen jcr:content.

      ![jcr:content-Eigenschaft](assets/3_jcrcontentntresource.png)

      Zu den Untereigenschaften von jcr:content gehört jcr:data, das abgeblendet ist. Doppelklicken Sie auf jcr:data. Die Eigenschaft wird bearbeitbar und die Schaltfläche „Datei wählen“ wird im entsprechenden Eintrag angezeigt. Klicken Sie auf **Datei wählen** und wählen Sie die Bilddatei aus, die Sie als Logo benutzen möchten. Für die Bilddatei wird keine Erweiterung benötigt.

      ![JCR-Daten](assets/5_jcrdata.png)

   Klicken Sie auf **Alle speichern**.

1. Stellen Sie sicher, dass das XDP\Layout, das Sie im Brief verwenden, unten links (oder an einer anderen geeigneten Stelle im Layout, an der Sie die Signatur rendern möchten) über ein Bildfeld zum Rendern des Signaturbilds verfügt.
1. Wählen Sie beim Erstellen von Korrespondenz wie folgt auf der Registerkarte „Daten“ ein Bildfeld für das Signaturbild:

   1. Wählen Sie aus dem Popupmenü „Verbindungstyp“ im rechten Bereich die Option „System“.

   1. Wählen Sie das agentSignatureImage-DDE aus der Liste im Datenelementbereich für das SystemContext-DD.

   1. Speichern Sie den Brief.

1. Wenn der Brief gerendert wird, wird die Signatur ind er Briefvorschau im Bildfeld angezeigt, wie durch das Layout bestimmt.

   ![Agentsignaturbild im Brief](assets/letterwithsignature.png)
