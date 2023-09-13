---
title: Konfigurieren von Berechtigungen für die Verwendung mit Acrobat Reader DC Extensions
description: Erfahren Sie, wie Sie Anmeldeinformationen für die Verwendung mit Acrobat Reader DC Extensions konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: e8015d59-7587-46dc-a672-e0f1108102ad
source-git-commit: 5af420c8e95fed88a8516cce27b8bbc7d3974e75
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 5%

---

# Konfigurieren von Berechtigungen für die Verwendung mit Acrobat Reader DC Extensions{#configuring-credentials-for-use-with-acrobat-reader-dc-extensions}

Um Verwendungsrechte auf PDF-Dokumente anzuwenden, konfigurieren Sie AEM Formulare mit einer gültigen Berechtigung für Acrobat Reader DC-Erweiterungen. Während der Installation von AEM Formularen wurden möglicherweise Anmeldedaten konfiguriert. Wenn Sie Ihre Acrobat Reader DC Extensions-Berechtigung beim Ausführen von Configuration Manager nicht konfiguriert haben oder wenn Sie eine neue oder Ersatzberechtigung importieren müssen, können Sie dies über die Seiten &quot;Trust Store-Verwaltung&quot;tun.

Wenn Sie eine Testberechtigung verwenden, ersetzen Sie sie beim Wechsel in Ihre Produktionsumgebung durch eine Produktionsberechtigung. Um eine abgelaufene oder Testberechtigung zu aktualisieren, löschen Sie zunächst die alte Acrobat Reader DC Extensions-Berechtigung.

Informationen zum Abrufen einer Berechtigung finden Sie unter [Vorbereiten der Installation von AEM Forms (Einzelserver)](https://helpx.adobe.com/pdf/aem-forms/6-3/prepare-install-single-server.pdf).

Der Trust Store kann mehr als eine Acrobat Reader DC Extensions-Berechtigung enthalten. Legen Sie eine dieser Anmeldedaten als Standardberechtigung für Reader Extensions fest. Die Standardberechtigung wird verwendet, wenn ein Workbench-Benutzer nicht ermitteln kann, welche Berechtigung bei der Prozesserstellung verwendet werden soll. Diese Regeln gelten für Standardanmeldedaten:

* Wenn Sie eine Acrobat Reader DC Extensions-Berechtigung importieren und der Trust Store keine anderen Acrobat Reader DC Extensions-Anmeldeinformationen enthält, wird diese als Standard festgelegt.
* Wenn Sie eine Acrobat Reader DC Extensions-Berechtigung importieren und die Option Standard ausgewählt ist, wird der Standardtyp aus einer vorhandenen Standardberechtigung entfernt. Die importierte Berechtigung wird die Standardberechtigung.
* Sie können keine standardmäßigen Acrobat Reader DC Extensions-Berechtigungen löschen. Um die Standardberechtigung zu löschen, legen Sie zunächst eine andere Berechtigung als Standard fest. Eine Ausnahme von dieser Regel besteht darin, dass Sie, wenn nur eine Berechtigung vorhanden ist, diese löschen können, auch wenn es sich um die Standardberechtigung handelt.
* Sie können keine standardmäßigen Acrobat Reader DC Extensions-Anmeldedaten aktualisieren.

>[!NOTE]
>
>Sie können Berechtigungen auch programmgesteuert importieren und löschen. (Siehe [Programmieren mit AEM](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de).

## Acrobat Reader DC Extensions-Berechtigung importieren {#import-a-acrobat-reader-dc-extensions-credential}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;Lokale Berechtigungen&quot;.
1. Klicken Sie auf &quot;Importieren&quot;und wählen Sie unter &quot;Trust Store-Typ&quot;die Option &quot;Acrobat Reader DC Extensions-Berechtigung&quot;aus.
1. (Optional) Um anzugeben, dass diese Berechtigung die Standardberechtigung für die Verwendung mit Acrobat Reader DC Extensions ist, wählen Sie &quot;Standard&quot;aus.
1. Geben Sie in das Feld &quot;Alias&quot;eine Kennung für die Berechtigung ein. Diese Kennung wird als Anzeigename für die Berechtigung in Acrobat Reader DC Extensions verwendet. Dieser Alias wird auch verwendet, um mithilfe des AEM Forms SDK programmgesteuert auf die Berechtigung zuzugreifen.

   >[!NOTE]
   >
   >Der Aliasname wird zu Anzeigezwecken automatisch in Großbuchstaben umgewandelt. Beim Aliasnamen wird nicht zwischen Groß- und Kleinschreibung unterschieden, wenn Sie in einem Prozess darauf verweisen.

1. Klicken Sie auf „Eine Datei auswählen“, um die Berechtigung zu suchen. Geben Sie das Kennwort der Berechtigung ein und klicken Sie auf „OK“.

   Wenn die Fehlermeldung &quot;Berechtigung konnte nicht importiert werden aufgrund eines falschen Dateiformats oder eines falschen Kennworts&quot;angezeigt wird, überprüfen Sie, ob das Kennwort gültig ist.

## Berechtigung für Acrobat Reader DC Extensions entfernen {#remove-a-acrobat-reader-dc-extensions-credential}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;Lokale Berechtigungen&quot;.
1. Wählen Sie die Berechtigung aus und klicken Sie auf Löschen.

## Acrobat Reader DC Extensions-Berechtigung ersetzen {#replace-a-acrobat-reader-dc-extensions-credential}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;Lokale Berechtigungen&quot;.
1. Notieren Sie sich den Alias der vorhandenen Berechtigung, wählen Sie ihn aus und klicken Sie auf &quot;Löschen&quot;.
1. Importieren Sie die neue Berechtigung mit exakt demselben Aliasnamen.
