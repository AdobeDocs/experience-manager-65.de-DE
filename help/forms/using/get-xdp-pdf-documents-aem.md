---
title: Übernehmen von XDP- und PDF-Dokumenten in AEM Forms
description: Mit AEM Forms können Sie Formulare und unterstützte Assets zur Verwendung mit adaptiven Formularen hochladen. Sie können Formulare und zugehörige Ressourcen auch per Massen-Upload als ZIP-Datei hochladen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
docset: aem65
role: Admin
exl-id: 9ecdc50a-31e3-46ae-948a-d1f6e6085734
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 35%

---

# Übernehmen von XDP- und PDF-Dokumenten in AEM Forms{#getting-xdp-and-pdf-documents-in-aem-forms}

## Übersicht {#overview}

Sie können Ihre Formulare aus Ihrem lokalen Dateisystem in das CRX-Repository importieren, indem Sie sie in AEM Forms hochladen. Der Upload-Vorgang wird für die folgenden Asset-Typen unterstützt:

* Formularvorlagen (XFA-Formulare)
* PDF-Formulare
* Dokument (einfache PDF-Dokumente)

Sie können die unterstützten Assettypen einzeln oder als ZIP-Archiv hochladen. Sie können ein Asset des Typs `Resource` nur zusammen mit einem XFA-Formular in einem ZIP-Archiv hochladen.

>[!NOTE]
>
>Vergewissern Sie sich, dass Sie Mitglied der Gruppe `form-power-users` sind, um XDP-Dateien hochladen zu können. Wenden Sie sich an Ihren Administrator, um Mitglied der Gruppe zu werden.

## Hochladen von Formularen {#uploading-forms}

1. Melden Sie sich bei der Benutzeroberfläche von AEM Forms an, indem Sie auf `https://'[server]:[port]'/aem/forms.html` zugreifen.
1. Navigieren Sie zu dem Ordner, in den Sie das Formular oder den Ordner mit Formularen hochladen möchten.
1. Wählen Sie in der Symbolleiste &quot;Aktionen&quot;die Option **Erstellen > Datei-Upload**.

   ![Dateien von der Option „Lokaler Speicher“ unter „Erstellen“](assets/step.png)

1. Mit dem Uploadformular- oder Paketdialogfeld können Sie die Datei suchen und auswählen, die Sie hochladen möchten. Im Dateibrowser werden nur die unterstützten Dateiformate (ZIP, XDP und PDF) angezeigt.

   >[!NOTE]
   >
   >Dateinamen dürfen nur alphanumerische Zeichen, Bindestriche oder Unterstriche enthalten.

1. Klicken Sie nach der Dateiauswahl auf Hochladen , um die Dateien hochzuladen, oder klicken Sie auf Abbrechen , um den Upload abzubrechen. In einem Popup-Fenster werden die hinzugefügten Assets und die Assets aufgelistet, die am aktuellen Speicherort aktualisiert werden.

   >[!NOTE]
   >
   >Bei einer ZIP-Datei werden die relativen Pfade aller unterstützten Assets angezeigt. Nicht unterstützte Assets innerhalb der ZIP werden ignoriert und nicht aufgelistet. Wenn das ZIP-Archiv jedoch nur die nicht unterstützten Assets enthält, wird anstelle des Popup-Dialogfensters eine Fehlermeldung angezeigt.

   ![Upload-Dialogfenster beim Hochladen eines XFA-Formulars](assets/upload-scr.png)

1. Wenn der Dateiname von einem oder mehreren Assets ungültig ist, wird ein Fehler angezeigt. Korrigieren Sie die rot markierten Dateinamen und laden Sie die Dateien erneut hoch.

   ![Fehlermeldung beim Hochladen eines XFA-Formulars](assets/upload-scr-err.png)

Nach Abschluss des Uploads generiert ein Hintergrundworkflow Miniaturansichten für jedes Asset, basierend auf der Asset-Vorschau. Neuere Versionen von Assets überschreiben beim Hochladen vorhandene Assets.

### Geschützter Modus {#protected-mode}

Mit dem AEM Forms-Server können Sie JavaScript-Code ausführen. Ein bösartiger JavaScript-Code kann eine AEM Forms-Umgebung schädigen. Der geschützte Modus beschränkt AEM Forms darauf, XDP-Dateien nur aus vertrauenswürdigen Assets und Speicherorten auszuführen. Alle in der AEM Forms-Benutzeroberfläche verfügbaren XDP-Dateien gelten als vertrauenswürdige Assets.

Der geschützte Modus ist standardmäßig aktiviert. Bei Bedarf können Sie den geschützten Modus deaktivieren:

1. Melden Sie sich bei der AEM Web-Konsole als Administrator an. Die URL lautet https://&#39;[server]:[port]&#39;/system/console/configMgr
1. Öffnen Sie Mobile Forms-Konfigurationen zur Bearbeitung.
1. Deaktivieren Sie die Option Geschützter Modus und klicken Sie auf **Speichern**. Der abgesicherte Modus ist deaktiviert.

## Aktualisieren referenzierter XFA-Formulare {#updating-referenced-xfa-forms}

In AEM Forms kann eine XFA-Formularvorlage durch ein adaptives Formular oder eine andere XFA-Formularvorlage referenziert werden. Eine Vorlage kann auch auf eine Ressource oder eine andere XFA-Vorlage verweisen.

Die Felder eines adaptiven Formulars, das auf eine XFA verweist, sind an die in der XFA verfügbaren Felder gebunden. Beim Aktualisieren einer Formularvorlage versucht das zugehörige adaptive Formular, mit der XFA zu synchronisieren. Weitere Informationen finden Sie unter [Synchronisieren von adaptiven Formularen mit der zugehörigen XFA](../../forms/using/synchronizing-adaptive-forms-xfa.md).

Das Entfernen einer Formularvorlage beschädigt das abhängige adaptive Formular oder die Formularvorlage. Ein solches adaptives Formular wird manchmal informell als schmutziges Formular bezeichnet. In der Benutzeroberfläche von AEM Forms finden Sie die schmutzigen Formulare auf zwei Arten:

* Auf der Miniaturansicht des adaptiven Formulars in der Asset-Liste wird ein Warnsymbol angezeigt. Die folgende Meldung wird angezeigt, wenn Sie den Mauszeiger über das Warnsymbol bewegen.\
  `Schema/Form Template for this adaptive form has been updated so go to Authoring mode and rebase it with new version.`

![Warnung für ein unsynchronisiertes adaptives Formular nach dem Aktualisieren der zugehörigen XFA](assets/dirtyaf.png)

Ein Flag wird beibehalten, um anzugeben, ob ein adaptives Formular schmutzig ist. Diese Informationen sind auf der Seite mit den Formulareigenschaften neben den Formularmetadaten verfügbar. Lediglich für unsaubere adaptive Formulare zeigt eine Metadateneigenschaft `Model Refresh` den Wert `Recommended` an.

![Kennzeichnung eines adaptiven Formular, das mit dem XFA-Modell nicht synchronisiert ist](assets/model-refresh.png)
