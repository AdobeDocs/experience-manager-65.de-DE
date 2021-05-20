---
title: Konfigurieren von Berechtigungen für die Verwendung mit Acrobat Reader DC Extensions
seo-title: Konfigurieren von Berechtigungen für die Verwendung mit Acrobat Reader DC Extensions
description: Erfahren Sie, wie Sie Berechtigungen für die Verwendung mit Acrobat Reader DC-Erweiterungen konfigurieren.
seo-description: Erfahren Sie, wie Sie Berechtigungen für die Verwendung mit Acrobat Reader DC-Erweiterungen konfigurieren.
uuid: 9210e6c9-6f5c-402d-b355-b104cdffd5eb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 5bb32fb1-4b6e-412f-aa16-f60db9dcaba1
exl-id: e8015d59-7587-46dc-a672-e0f1108102ad
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 97%

---

# Konfigurieren von Berechtigungen für die Verwendung mit Acrobat Reader DC Extensions{#configuring-credentials-for-use-with-acrobat-reader-dc-extensions}

Um Verwendungsrechte in PDF-Dokumenten anzuwenden, konfigurieren Sie AEM Forms mit einer gültigen Berechtigung für Acrobat Reader DC Extensions. Bei der Installation von AEM Forms wurde eventuell eine Berechtigung konfiguriert. Wenn Sie Ihre Acrobat Reader DC Extensions-Berechtigung nicht mithilfe von Configuration Manager konfiguriert haben oder eine neue oder Ersatzberechtigung importieren müssen, können Sie dies mithilfe der Seiten der Trust Store-Verwaltung tun.

Wenn Sie eine Testberechtigung verwenden, müssen Sie diese nach dem Wechsel in die Produktionsumgebung durch eine Produktionsberechtigung ersetzen. Um eine abgelaufene oder Testberechtigung zu aktualisieren, müssen Sie zunächst die alte Acrobat Reader DC Extensions-Berechtigung löschen.

Weitere Informationen zum Abrufen einer Berechtigung finden Sie unter [Vorbereiten der Installation von AEM Forms (Einzelserver)](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63).

Der Trust Store enthält möglicherweise mehr als eine Acrobat Reader DCExtensions-Berechtigung. Sie müssen eine dieser Berechtigungen als Standardberechtigung für Reader Extensions festlegen. Die Standardberechtigung wird verwendet, wenn ein Workbench-Benutzer nicht entscheiden kann, welche Berechtigung bei der Prozesserstellung verwendet werden soll. Diese Regeln gelten für Standardberechtigungen:

* Wenn Sie eine Acrobat Reader DC Extensions-Berechtigung importieren und der Trust Store keine weiteren Acrobat Reader DC Extensions-Berechtigungen enthält, wird diese als Standard festgelegt.
* Wenn Sie eine Acrobat Reader DC Extensions-Berechtigung importieren und die Option „Standard“ ausgewählt ist, wird der Standardtyp von einer vorhandenen Standardberechtigung entfernt. Die importierte Berechtigung wird die Standardberechtigung.
* Die Standardberechtigung für Acrobat Reader DC Extensions kann nicht gelöscht werden. Um die Standardberechtigung zu löschen, müssen Sie zunächst eine andere Berechtigung als Standard festlegen. Dabei gilt folgende Ausnahme: Wenn es nur eine Berechtigung gibt, können Sie diese löschen, obwohl es sich dabei um die Standardberechtigung handelt.
* Die Standardberechtigung für Acrobat Reader DC Extensions kann nicht aktualisiert werden.

>[!NOTE]
>
>Sie können Berechtigungen auch importieren und programmgesteuert löschen. (Weitere Informationen finden Sie unter [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63).)

## Acrobat Reader DC Extensions-Berechtigungen importieren {#import-a-acrobat-reader-dc-extensions-credential}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Klicken Sie auf „Importieren“ und wählen Sie unter „Trust Store-Typ“ die Option „Acrobat Reader DC Extensions-Berechtigung“.
1. (Optional) Um anzugeben, dass dies die Standardberechtigung ist, die mit Acrobat Reader DC Extensions verwendet werden soll, wählen Sie „Standard“ aus.
1. Geben Sie in das Feld „Alias“ einen Bezeichner für die Berechtigung ein. Dieser Bezeichner wird in Acrobat Reader DC Extensions als Anzeigename für die Berechtigung verwendet. Außerdem wird dieser Alias für den programmgesteuerten Zugriff auf die Berechtigung mithilfe des AEM Forms SDK verwendet.

   >[!NOTE]
   >
   >Der Aliasname wird zu Anzeigezwecken automatisch in Großschreibung konvertiert. Wenn Sie auf den Aliasnamen in einem Prozess verweisen, wird Groß-/Kleinschreibung nicht unterschieden.

1. Klicken Sie auf „Eine Datei auswählen“, um die Berechtigung zu suchen. Geben Sie das Kennwort der Berechtigung ein und klicken Sie auf „OK“.

   Wenn die Fehlermeldung „Fehler beim Importieren einer Berechtigung aufgrund eines fehlerhaften Dateiformats oder eines falschen Kennworts“ angezeigt wird, müssen Sie sicherstellen, dass das Kennwort gültig ist.

## Acrobat Reader DC Extensions-Berechtigungen entfernen  {#remove-a-acrobat-reader-dc-extensions-credential}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Wählen Sie die Berechtigung und klicken Sie auf „Löschen“.

## Acrobat Reader DC Extensions-Berechtigungen ersetzen  {#replace-a-acrobat-reader-dc-extensions-credential}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Notieren Sie sich den Alias der vorhandenen Berechtigung, wählen Sie ihn aus und klicken Sie auf „Löschen“.
1. Importieren Sie die neue Berechtigung unter Verwendung von exakt demselben Aliasnamen.
