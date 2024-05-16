---
title: Übernehmen von XDP- und PDF-Dokumenten in AEM Forms
description: Mit AEM Forms können Sie Formulare und unterstützte Assets hochladen, um sie mit adaptiven Formularen zu verwenden. Sie können Formulare und zugehörige Ressourcen im Stapel als ZIP-Datei hochladen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
docset: aem65
role: Admin,User
exl-id: 9ecdc50a-31e3-46ae-948a-d1f6e6085734
solution: Experience Manager, Experience Manager Forms
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '671'
ht-degree: 100%

---

# Übernehmen von XDP- und PDF-Dokumenten in AEM Forms{#getting-xdp-and-pdf-documents-in-aem-forms}

## Übersicht {#overview}

Sie können Formulare aus Ihrem lokalen Dateisystem in das CRX-Repository importieren, indem Sie sie in AEM Forms hochladen. Der Hochladevorgang wird für die folgenden Asset-Typen unterstützt:

* Formularvorlagen (XFA-Formulare)
* PDF-Formulare
* Dokumente (reduzierte PDF-Dokumente)

Sie können die unterstützten Assettypen einzeln oder als ZIP-Archiv hochladen. Sie können ein Asset des Typs `Resource` nur zusammen mit einem XFA-Formular in einem ZIP-Archiv hochladen.

>[!NOTE]
>
>Vergewissern Sie sich, dass Sie Mitglied der Gruppe `form-power-users` sind, um XDP-Dateien hochladen zu können. Wenden Sie sich an Ihre Admins, um Mitglied der Gruppe zu werden.

## Hochladen von Formularen {#uploading-forms}

1. Melden Sie sich bei der Benutzeroberfläche von AEM Forms an, indem Sie auf `https://'[server]:[port]'/aem/forms.html` zugreifen.
1. Navigieren Sie zu dem Ordner, in den Sie das Formular oder die Ordner mit Formularen hochladen möchten.
1. Wählen Sie in der Aktionssymbolleiste **Erstellen > Datei hochladen** aus.

   ![Dateien von der Option „Lokaler Speicher“ unter „Erstellen“](assets/step.png)

1. Mit dem Uploadformular- oder Paketdialogfeld können Sie die Datei suchen und auswählen, die Sie hochladen möchten. Im Datei-Browser werden nur die unterstützten Dateiformate angezeigt (ZIP, XDP und PDF).

   >[!NOTE]
   >
   >Ein Dateiname darf nur alphanumerische Zeichen, Bindestriche oder Unterstriche enthalten.

1. Klicken Sie nach der Dateiauswahl auf „Hochladen“, um die Dateien hochzuladen, oder auf „Abbrechen“, um den Upload abzubrechen. In einem Popup-Fenster werden die Assets aufgelistet, die hinzugefügt werden und die, die im aktuellen Speicherort aktualisiert werden.

   >[!NOTE]
   >
   >Bei einer ZIP-Datei werden die relativen Pfade aller unterstützten Assets angezeigt. Nicht unterstützte Assets in der ZIP-Datei werden ignoriert und nicht aufgelistet. Wenn das ZIP-Archiv jedoch nur die nicht unterstützten Assets enthält, wird anstelle des Popup-Dialogfensters eine Fehlermeldung angezeigt.

   ![Upload-Dialogfenster beim Hochladen eines XFA-Formulars](assets/upload-scr.png)

1. Wenn der Dateiname von einem oder mehreren Assets ungültig ist, wird ein Fehler angezeigt. Korrigieren Sie die rot markierten Dateinamen und laden Sie die Dateien erneut hoch.

   ![Fehlermeldung beim Hochladen eines XFA-Formulars](assets/upload-scr-err.png)

Wenn das Hochladen abgeschlossen ist, wird basierend auf der Asset-Vorschau über einen Workflow im Hintergrund für jedes Asset eine Miniatur generiert. Wenn neuere Versionen von Assets hochgeladen werden, werden die vorhandenen Assets überschrieben.

### Abgesicherter Modus {#protected-mode}

AEM Forms-Server ermöglicht es Ihnen, JavaScript-Code auszuführen. Ein bösartiger JavaScript-Code kann eine AEM Forms-Umgebung schädigen. Der abgesicherte Modus beschränkt AEM Forms darauf, XDP-Dateien nur von vertrauenswürdigen Assets und Speicherorten auszuführen. Alle in der AEM Forms-Benutzeroberfläche verfügbaren XDP-Dateien gelten als vertrauenswürdige Assets.

Der abgesicherte Modus ist standardmäßig aktiviert. Bei Bedarf können Sie den abgesicherten Modus deaktivieren:

1. Melden Sie sich bei der AEM Web-Konsole als Administrator an. Die URL lautet https://&#39;[server]:[port]&#39;/system/console/configMgr
1. Öffnen Sie Mobile Forms-Konfigurationen für die Bearbeitung.
1. Wählen Sie die Option „Abgesicherter Modus“ und klicken Sie auf **Speichern**. Der abgesicherte Modus ist deaktiviert.

## Aktualisieren von referenzierten XFA-Formularen {#updating-referenced-xfa-forms}

In AEM Forms kann eine XFA-Formularvorlage durch ein adaptives Formular oder eine andere XFA-Formularvorlage referenziert werden. Des Weiteren kann eine Vorlage auf eine Ressource oder eine andere XFA-Vorlage verweisen.

Die Felder eines adaptiven Formulars, das auf eine XFA verweist, sind mit den Feldern verbunden, die in der XFA verfügbar sind. Nach dem Aktualisieren einer Formularvorlage versucht das zugehörige adaptive Formular, sich mit der XFA zu synchronisieren. Weitere Informationen finden Sie unter[ Synchronisieren von adaptiven Formularen mit der zugehörigen XFA](../../forms/using/synchronizing-adaptive-forms-xfa.md).

Durch das Entfernen einer Formularvorlage wird das abhängige adaptive Formular bzw. die Formularvorlage beschädigt.  Ein solches adaptives Formular wird manchmal auch als schmutziges Formular bezeichnet.  In der AEM Forms-Benutzeroberfläche stehen Ihnen zwei Möglichkeiten zur Verfügung, die nachfolgend beschrieben werden, um die schmutzigen Formulare zu finden.

* In der Asset-Auflistung wird ein Warnsymbol auf der Miniaturansicht des adaptiven Formulars angezeigt. Außerdem wird die folgende Nachricht angezeigt, wenn Sie den Mauszeiger über das Warnsymbol bewegen.\
  `Schema/Form Template for this adaptive form has been updated so go to Authoring mode and rebase it with new version.`

![Warnung für ein unsynchronisiertes adaptives Formular nach dem Aktualisieren der zugehörigen XFA](assets/dirtyaf.png)

Die Kennzeichnung bleibt bestehen, damit schmutzige adaptive Formulare erkannt werden.  Diese Informationen befinden sich auf der Seite mit den Formulareigenschaften neben den Metadaten.  Lediglich für unsaubere adaptive Formulare zeigt eine Metadateneigenschaft `Model Refresh` den Wert `Recommended` an.

![Kennzeichnung eines adaptiven Formular, das mit dem XFA-Modell nicht synchronisiert ist](assets/model-refresh.png)
