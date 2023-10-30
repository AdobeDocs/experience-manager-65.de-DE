---
title: Verwalten lokaler Anmeldeinformationen
description: Erfahren Sie, wie Sie lokale Berechtigungen mithilfe der Trust Store-Verwaltung verwalten. AEM Formulare unterstützen RSA- und DSA-Anmeldeinformationen im PKCS12-Standardformular.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: c5905272-7d09-47e4-8b35-4cc25a148477
source-git-commit: 6caf3ef4a00275f0f73be52b6a9ccba77d277f1a
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 3%

---

# Verwalten lokaler Anmeldeinformationen {#managing-local-credentials}

Lokale Anmeldeinformationen sind Anmeldedaten für private Schlüssel, die in der Trust Store-Verwaltung gehostet werden. A *lokale Berechtigungen* gibt an, wo die DES-Berechtigung eines Benutzers gespeichert ist. Mithilfe der Trust Store-Verwaltung können Sie Ihre lokalen Berechtigungen importieren und verwalten, indem Sie beispielsweise vorhandene PFX-Dateien verwenden, damit Sie lokale Berechtigungen importieren, bearbeiten und löschen können.

AEM Formulare unterstützen RSA- und DSA-Anmeldeinformationen mit bis zu 4096 Bit im PKCS12-Standardformat (.pfx- und .p12-Dateien).

Sie können beliebig viele Anmeldeinformationen importieren und exportieren. Wenn Sie eine abgelaufene Berechtigung mit demselben Alias ersetzen möchten, löschen Sie die Berechtigung und importieren Sie dann die neue Berechtigung mit demselben Alias.

Informationen und Anweisungen zu Acrobat Reader DC-Erweiterungen finden Sie unter [Konfigurieren von Berechtigungen für die Verwendung mit Acrobat Reader DC Extensions](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions).

## Berechtigung importieren {#import-a-credential}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;Lokale Berechtigungen&quot;.
1. Klicken Sie auf Importieren. Wählen Sie unter Trust Store Type eine der folgenden Optionen aus:

   * **Berechtigung für die Dokumentsignierung:** Eine Berechtigung, die zum Hinzufügen einer digitalen Signatur zu einem Dokument dient.
   * **Acrobat Reader DC Extensions-Berechtigungen:** Ein digitales Zertifikat speziell für Acrobat Reader DC-Erweiterungen, das die Aktivierung von Adobe Reader-Verwendungsrechten in den erstellten PDF-Dokumenten ermöglicht.
   * **Standard:** Gibt an, dass dies die Standardberechtigung ist, die mit Acrobat Reader DC Extensions verwendet werden soll.

   Informationen zum Abrufen einer Berechtigung finden Sie unter [Vorbereiten der Installation AEM Formulare](https://helpx.adobe.com/pdf/aem-forms/6-3/prepare-install-single-server.pdf).

1. Geben Sie in das Feld &quot;Alias&quot;eine Kennung für die Berechtigung ein. Diese Kennung wird als Anzeigename für die Berechtigung in Acrobat Reader DC Extensions und im Signature-Dienst verwendet. Dieser Alias wird auch verwendet, um mithilfe des AEM Forms SDK programmgesteuert auf die Berechtigung zuzugreifen.

   >[!NOTE]
   >
   >Der Aliasname wird zu Anzeigezwecken automatisch in Großbuchstaben umgewandelt. Beim Aliasnamen wird nicht zwischen Groß- und Kleinschreibung unterschieden, wenn Sie in einem Prozess darauf verweisen.

1. Klicken Sie auf Durchsuchen , um die Berechtigung zu suchen, geben Sie das Kennwort der Berechtigung ein und klicken Sie auf OK.

   Wenn die Fehlermeldung &quot;Berechtigung konnte nicht importiert werden aufgrund eines falschen Dateiformats oder eines falschen Kennworts&quot;angezeigt wird, überprüfen Sie, ob das Kennwort gültig ist.

## Berechtigung exportieren {#export-a-credential}

Anmeldeinformationen werden als P12-Dateien im PKCS#12-Format exportiert.

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;Lokale Berechtigungen&quot;.
1. Klicken Sie auf den Aliasnamen der Berechtigung, die Sie exportieren möchten, und klicken Sie dann auf &quot;Exportieren&quot;.
1. Geben Sie in das Feld &quot;Kennwort&quot;das Kennwort ein. Dieses Kennwort ist neu und wird zum Verschlüsseln der exportierten Berechtigung verwendet.
1. Klicken Sie auf &quot;Exportieren&quot;, befolgen Sie die Anweisungen, damit Sie die Berechtigung exportieren können, und klicken Sie auf &quot;OK&quot;.

## Alias- oder Trust Store-Typ einer Berechtigung bearbeiten {#edit-a-credential-s-alias-or-trust-store-type}

Nachdem eine Berechtigung importiert wurde, können Sie den Aliasnamen und den Trust Store-Typ bearbeiten.

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;Lokale Berechtigungen&quot;.
1. Klicken Sie auf den Aliasnamen der Berechtigung, die Sie bearbeiten möchten.
1. Klicken Sie auf Berechtigung aktualisieren.
1. Bearbeiten Sie den Aliasnamen und den Trust Store-Typ nach Bedarf und klicken Sie auf OK.

## Berechtigung löschen {#delete-a-credential}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;Trust Store-Verwaltung&quot;> &quot;Lokale Berechtigungen&quot;.
1. Aktivieren Sie die Kontrollkästchen der zu löschenden Anmeldeinformationen.
1. Klicken Sie auf Löschen und dann auf OK.
