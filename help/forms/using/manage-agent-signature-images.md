---
title: Verwalten von Agentsignaturbildern
seo-title: Manage agent signature images
description: Nachdem Sie eine Briefvorlage erstellt haben, können Sie diese verwenden, um Korrespondenz in AEM Forms zu erstellen, indem Sie Daten, Inhalte und Anhänge verwalten.
seo-description: After you have created a letter template, you can use it to create correspondence in AEM Forms by managing data, content, and attachments.
uuid: 48b2697e-6065-4e23-9aa8-333e7b11ede1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: a81cdd53-f0fb-4ac5-b2ec-c19aeee7186e
docset: aem65
feature: Correspondence Management
exl-id: f044ed75-bb72-4be1-aef6-2fb3b2a2697b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '690'
ht-degree: 100%

---

# Verwalten von Agentsignaturbildern{#manage-agent-signature-images}

## Übersicht {#overview}

In der Correspondence Management können Sie ein Bild für die Agentunterzeichnung in Briefen verwenden. Nachdem Sie das Bild für die Agentsignatur festgelegt haben, können Sie es in Briefen, die Sie erstellen, als Signatur des Absenderagenten ausgeben.

Das agentSignatureImage-DDE ist ein berechnetes DDE zur Darstellung des Signaturbilds des Agenten. Der Ausdruck für dieses berechnete DDE verwendet eine neue benutzerdefinierte Funktion, die vom Baustein „Expression Manager“ bereitgestellt wird. Diese benutzerdefinierte Funktion akzeptiert agentID und agentFolder als Eingabeparameter und ruft den Bildinhalt auf Basis dieser Parameter ab. Über das Systemdatenwörterbuch SystemContext erhalten Briefe in Correspondence Management Zugriff auf Informationen im aktuellen Systemkontext. Der Systemkontext umfasst Informationen zum derzeit angemeldeten Benutzer und zu aktiven Konfigurationsparametern.

Sie können Bilder im cmuserroot-Ordner hinzufügen. In den [Eigenschaften der Correspondence Management-Konfiguration](/help/forms/using/cm-configuration-properties.md) können Sie mithilfe der Eigenschaft „URL für CM-Benutzerelemente“ den Ordner wechseln, aus dem das Agentsignaturbild abgerufen wird.

Der Wert des agentFolder-DDE wird aus dem CMUserRoot-Konfigurationsparameter für die Correspondence Management-Konfigurationseigenschaften abgerufen. Standardmäßig verweist dieser Konfigurationsparameter auf /content/cmUserRoot im CRX-Repository. Sie können den Wert der CMUserRoot-Konfiguration in den Konfigurationseigenschaften ändern. Sie können die Standardfunktion auch überschreiben, um eine eigene Logik zum Abrufen des Bilds der Benutzerunterschrift zu definieren.

## Agentsignaturbild hinzufügen {#adding-agent-signature-image}

1. Stellen Sie sicher, dass das Agentsignaturbild denselben Namen wie der AEM-Benutzername des Benutzers hat. (Eine Erweiterung wird den Namen der Bilddateien nicht benötigt.)
1. Erstellen Sie in CRX einen Ordner mit dem Namen `cmUserRoot` im aktuellen Ordner.

   1. Rufen Sie `https://'[server]:[port]'/crx/de` auf. Falls erforderlich, melden Sie sich als Administrator an.

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **content** und wählen Sie **Erstellen** > **Ordner erstellen**.

      ![Ordner erstellen](assets/1_createnode_cmuserroot.png)

   1. Geben Sie im Dialogfeld „Ordner erstellen“ den Namen des Ordners als `cmUserRoot` an. Klicken Sie auf **Alle speichern**.

      >[!NOTE]
      >
      >cmUserRoot ist der Standardspeicherort, unter dem AEM nach dem Agentsignaturbild sucht. Sie können dies jedoch ändern, indem Sie die Eigenschaft „URL für CM-Benutzerelemente“ in den [Eigenschaften der Correspondence Management-Konfiguration](/help/forms/using/cm-configuration-properties.md) bearbeiten.

1. Navigieren Sie in Content Explorer zum cmUserRoot-Ordner und fügen Sie das Agentsignaturbild hinzu.

   1. Rufen Sie `https://'[server]:[port]'/crx/explorer/index.jsp` auf. Melden Sie sich nötigenfalls als Administrator an.
   1. Klicken Sie auf **Content Explorer**. Content Explorer wird in einem neuen Fenster geöffnet.
   1. Navigieren Sie in Content Explorer zum cmUserRoot-Ordner und wählen Sie ihn aus. Klicken Sie mit der rechten Maustaste auf den **cmUserRoot**-Ordner und wählen Sie **Neuer Knoten**.

      ![Neuer Knoten in cmUserRoot](assets/2_cmuserroot_newnode.png)

      Nehmen Sie die folgenden Einträge in der Zeile für neue Knoten vor und klicken Sie dann auf das grüne Häkchen.

      **Name:** Max Mustermann (oder der Name Ihrer Agentsignaturdatei)

      **Typ:** nt:file

      Im `cmUserRoot`-Ordner wird ein neuer Ordner mit dem Namen `JohnDoe` (bzw. dem Namen, den Sie im vorigen Schritt angegeben haben) erstellt.

   1. Klicken Sie auf den von Ihnen erstellten neuen Ordner (hier: `JohnDoe`). In Content Explorer wird der Inhalt des Ordners abgeblendet angezeigt.

   1. Doppelklicken Sie auf die Eigenschaften **jcr:content**, legen Sie als Typ **nt:resource** fest und klicken Sie dann auf das grüne Häkchen, um den Eintrag zu speichern.

      Wenn die Eigenschaft nicht vorhanden ist, erstellen Sie zuerst eine Eigenschaft mit dem Namen „jcr:content“. 

      ![Eigenschaft „jcr:content“](assets/3_jcrcontentntresource.png)

      Zu den Untereigenschaften von „jcr:content“ gehört die abgeblendet dargestellte Eigenschaft „jcr:data“. Doppelklicken Sie auf „jcr:data“. Die Eigenschaft wird bearbeitbar und die Schaltfläche „Datei wählen“ wird im entsprechenden Eintrag angezeigt. Klicken Sie auf **Datei wählen** und wählen Sie die Bilddatei aus, die Sie als Logo benutzen möchten. Für die Bilddatei wird keine Erweiterung benötigt.

      ![JCR-Daten](assets/5_jcrdata.png)
   Klicken Sie auf **Alle speichern**.

1. Stellen Sie sicher, dass im für den Brief verwendeten XDP\Layout in der linken unteren Ecke (oder einer anderen geeigneten Stelle im Layout, an der die Signatur ausgegeben werden soll) ein Bildfeld für die Ausgabe des Signaturbilds zur Verfügung steht.
1. Wählen Sie beim Erstellen von Korrespondenz wie folgt auf der Registerkarte „Daten“ ein Bildfeld für das Signaturbild:

   1. Wählen Sie aus dem Popupmenü „Verbindungstyp“ im rechten Bereich die Option „System“.

   1. Wählen Sie das agentSignatureImage-DDE aus der Liste im Datenelementbereich für das SystemContext-DD.

   1. Speichern Sie den Brief.

1. Wenn der Brief gerendert wird, wird die Signatur ind er Briefvorschau im Bildfeld angezeigt, wie durch das Layout bestimmt.

   ![Agentsignaturbild im Brief](assets/letterwithsignature.png)
