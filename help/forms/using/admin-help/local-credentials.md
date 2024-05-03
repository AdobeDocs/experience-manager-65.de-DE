---
title: Verwalten lokaler Anmeldeinformationen
description: Erfahren Sie, wie Sie lokale Berechtigungen mithilfe der Trust Store-Verwaltung verwalten. AEM Formulare unterstützen RSA- und DSA-Anmeldeinformationen im PKCS12-Standardformular.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: c5905272-7d09-47e4-8b35-4cc25a148477
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 100%

---

# Verwalten lokaler Anmeldeinformationen {#managing-local-credentials}

Lokale Berechtigungen sind auf privaten Schlüsseln basierende Berechtigungen, für welche die Trust Store-Verwaltung als Host dient. Eine *lokale Berechtigung* gibt an, wo die DES-Berechtigung einer Benutzerin oder eines Benutzers gespeichert wird. Über die Trust Store-Verwaltung können Sie Ihre lokalen Berechtigungen importieren und verwalten, indem Sie beispielsweise vorhandene PFX-Dateien verwenden, sodass Sie lokale Berechtigungen importieren, bearbeiten und löschen können.

AEM Forms unterstützt RSA- und DSA-Berechtigungen bis zu 4096 Bit im PKCS12-Standardformat (PFX- und P12-Dateien).

Sie können eine beliebige Anzahl von Berechtigungen im- und exportieren. Wenn Sie eine abgelaufene Berechtigung mit demselben Alias ersetzen möchten, löschen Sie die Berechtigung und importieren Sie anschließend die neue Berechtigung mit demselben Alias.

Weitere Informationen und Anweisungen zu Acrobat Reader DC Extensions finden Sie unter [Konfigurieren von Berechtigungen für die Verwendung mit Acrobat Reader DC Extensions](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions).

## Importieren von Berechtigungen {#import-a-credential}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Klicken Sie auf „Importieren“. Wählen Sie unter „Trust Store-Typ“ eine der folgenden Optionen aus:

   * **Berechtigung für die Dokumentsignierung:** Eine Berechtigung, die zum Hinzufügen einer digitalen Signatur zu einem Dokument dient.
   * **Berechtigung für Acrobat Reader DC-Erweiterungen:** Ein digitales Zertifikat, das speziell für Acrobat Reader DC-Erweiterungen gilt und die Aktivierung von Adobe Reader-Benutzerrechten in den erstellten PDF-Dokumenten ermöglicht.
   * **Standard:** Zeigt an, dass dies die Standardberechtigung ist, die mit Acrobat Reader DC-Erweiterungen verwendet werden soll.

   Weitere Informationen zum Abrufen einer Berechtigung finden Sie unter [Vorbereiten der Installation von AEM Forms](https://helpx.adobe.com/de/pdf/aem-forms/6-3/prepare-install-single-server.pdf).

1. Geben Sie in das Feld „Alias“ einen Kennung für die Berechtigung ein. Diese Kennung wird als Anzeigename für die Berechtigung in Acrobat Reader DC-Erweiterungen und im Signature-Dienst verwendet. Außerdem wird dieser Alias für den programmgesteuerten Zugriff auf die Berechtigung mit dem AEM Forms SDK verwendet.

   >[!NOTE]
   >
   >Der Aliasname wird zu Anzeigezwecken automatisch in Großschreibung konvertiert. Wenn Sie auf den Aliasnamen in einem Prozess verweisen, wird nicht zwischen Groß-/Kleinschreibung unterschieden.

1. Klicken Sie auf „Durchsuchen“, um die Berechtigung zu suchen. Geben Sie das Kennwort der Berechtigung ein und klicken Sie auf „OK“.

   Wenn die Fehlermeldung „Fehler beim Importieren einer Berechtigung aufgrund eines fehlerhaften Dateiformats oder eines falschen Kennworts“ angezeigt wird, müssen Sie sicherstellen, dass das Kennwort gültig ist. 

## Exportieren einer Berechtigung {#export-a-credential}

Berechtigungen werden als P12-Dateien im PKCS#12-Format exportiert.

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Klicken Sie auf den Aliasnamen der Berechtigung, die exportiert werden soll, und anschließend auf „Exportieren“.
1. Geben Sie in das Feld „Kennwort“ das Kennwort ein. Dieses Kennwort ist neu und dient zum Verschlüsseln der exportierten Berechtigung.
1. Klicken Sie auf „Exportieren“, befolgen Sie die Anweisungen zum Exportieren der Berechtigung und klicken Sie anschließend auf „OK“.

## Bearbeiten des Alias oder Trust Store-Typ einer Berechtigung {#edit-a-credential-s-alias-or-trust-store-type}

Nachdem eine Berechtigung importiert wurde, können Sie den Aliasnamen und den Trust Store-Typ bearbeiten.

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Klicken Sie auf den Aliasnamen der Berechtigung, die bearbeitet werden soll.
1. Klicken Sie auf „Berechtigung aktualisieren“.
1. Bearbeiten Sie den Aliasnamen und den Trust Store-Typ nach Bedarf und klicken Sie auf „OK“.

## Löschen einer Berechtigung {#delete-a-credential}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Aktivieren Sie die Kontrollkästchen der Berechtigungen, die gelöscht werden sollen.
1. Klicken Sie auf „Löschen“ und dann auf „OK“.
