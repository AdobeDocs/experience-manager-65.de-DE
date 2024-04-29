---
title: Konfigurieren von Berechtigungen für Acrobat Reader DC-Erweiterungen
description: Erfahren Sie, wie Sie Berechtigungen für Acrobat Reader DC-Erweiterungen konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: e8015d59-7587-46dc-a672-e0f1108102ad
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '546'
ht-degree: 100%

---

# Konfigurieren von Berechtigungen für Acrobat Reader DC-Erweiterungen{#configuring-credentials-for-use-with-acrobat-reader-dc-extensions}

Um Verwendungsrechte in PDF-Dokumenten anzuwenden, konfigurieren Sie AEM Forms mit einer gültigen Berechtigung für Acrobat Reader DC-Erweiterungen. Bei der Installation von AEM Forms wurde eventuell eine Berechtigung konfiguriert. Wenn Sie Ihre Berechtigung für Acrobat Reader DC-Erweiterungen nicht mit dem Konfigurations-Manager konfiguriert haben oder eine neue oder eine Ersatzberechtigung importieren müssen, ist dies über die Seiten der Trust Store-Verwaltung möglich.

Wenn Sie eine Testberechtigung verwenden, müssen Sie diese nach dem Wechsel in die Produktionsumgebung durch eine Produktionsberechtigung ersetzen. Um eine abgelaufene oder zum Testen bereitgestellte Berechtigung zu aktualisieren, müssen Sie zunächst die alte Berechtigung für Acrobat Reader DC-Erweiterungen löschen.

Weitere Informationen zum Abrufen einer Berechtigung finden Sie unter [Vorbereiten der Installation von AEM Forms (Einzel-Server)](https://helpx.adobe.com/de/pdf/aem-forms/6-3/prepare-install-single-server.pdf).

Der Trust Store enthält möglicherweise mehr als eine Berechtigung für Acrobat Reader DC-Erweiterungen. Legen Sie eine dieser Berechtigungen als Standardberechtigung für Reader-Erweiterungen fest. Die Standardberechtigung wird verwendet, wenn Workbench-Benutzende nicht entscheiden können, welche Berechtigung bei der Prozesserstellung verwendet werden soll. Diese Regeln gelten für Standardberechtigungen:

* Wenn Sie eine Berechtigung für Acrobat Reader DC-Erweiterungen importieren und der Trust Store keine weiteren Berechtigungen für Acrobat Reader DC-Erweiterungen enthält, wird diese als Standard festgelegt.
* Wenn Sie eine Berechtigung für Acrobat Reader DC-Erweiterungen importieren und die Option „Standard“ ausgewählt ist, wird der Standardtyp von einer vorhandenen Standardberechtigung entfernt. Die importierte Berechtigung wird die Standardberechtigung.
* Eine Standardberechtigung für Acrobat Reader DC-Erweiterungen kann nicht gelöscht werden. Um die Standardberechtigung zu löschen, müssen Sie zunächst eine andere Berechtigung als Standard festlegen. Dabei gilt folgende Ausnahme: Wenn es nur eine Berechtigung gibt, können Sie diese löschen, obwohl es sich dabei um die Standardberechtigung handelt.
* Eine Standardberechtigung für Acrobat Reader DC-Erweiterungen kann nicht aktualisiert werden.

>[!NOTE]
>
>Sie können Berechtigungen auch programmgesteuert importieren und löschen. (Siehe [Programmieren mit AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de).)

## Importieren einer Berechtigung für Acrobat Reader DC-Erweiterungen {#import-a-acrobat-reader-dc-extensions-credential}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Klicken Sie auf „Importieren“ und wählen Sie unter „Trust Store-Typ“ die Berechtigung für Acrobat Reader DC-Erweiterungen aus.
1. (Optional) Um anzugeben, dass dies die Standardberechtigung ist, die mit Acrobat Reader-Erweiterungen verwendet werden soll, wählen Sie die Option „Standard“ aus.
1. Geben Sie in das Feld „Alias“ einen Kennung für die Berechtigung ein. Diese Kennung wird in den Acrobat Reader DC-Erweiterungen als Anzeigename für die Berechtigung verwendet. Außerdem wird dieser Alias für den programmgesteuerten Zugriff auf die Berechtigung mit dem AEM Forms SDK verwendet.

   >[!NOTE]
   >
   >Der Aliasname wird zu Anzeigezwecken automatisch in Großschreibung konvertiert. Wenn Sie auf den Aliasnamen in einem Prozess verweisen, wird nicht zwischen Groß-/Kleinschreibung unterschieden.

1. Klicken Sie auf „Eine Datei auswählen“, um die Berechtigung zu suchen. Geben Sie das Kennwort der Berechtigung ein und klicken Sie auf „OK“.

   Wenn die Fehlermeldung „Fehler beim Importieren einer Berechtigung aufgrund eines fehlerhaften Dateiformats oder eines falschen Kennworts“ angezeigt wird, müssen Sie sicherstellen, dass das Kennwort gültig ist. 

## Entfernen einer Berechtigung für Acrobat Reader DC-Erweiterungen {#remove-a-acrobat-reader-dc-extensions-credential}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Wählen Sie die Berechtigung aus und klicken Sie auf „Löschen“.

## Ersetzen einer Berechtigung für Acrobat Reader DC-Erweiterungen {#replace-a-acrobat-reader-dc-extensions-credential}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Notieren Sie sich den Alias der vorhandenen Berechtigung, wählen Sie ihn aus und klicken Sie dann auf „Löschen“.
1. Importieren Sie die neue Berechtigung unter Verwendung von exakt demselben Aliasnamen.
