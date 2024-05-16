---
title: Einrichten eines PDFG-Netzwerkdruckers (nur Windows)
description: Erfahren Sie, wie Sie einen PDFG-Netzwerkdrucker einrichten (nur Windows).
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
exl-id: c3fc159e-2677-4b71-b0b2-2feaf69e1a32
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '604'
ht-degree: 100%

---

# Einrichten eines PDFG-Netzwerkdruckers (nur Windows) {#setting-up-a-pdfg-network-printer-windows-only}

Mit dem PDFG-Netzwerkdrucker können Benutzende ein PDF-Dokument aus jeder Anwendung heraus erstellen, die Druckfunktionen unterstützt. Nachdem ein Benutzer den PDFG-Netzwerkdrucker installiert hat, wird ein neuer Drucker mit dem Namen *PDF Generator* im Bereich „Drucker“ in der Windows-Systemsteuerung angezeigt. Wenn bereits ein Drucker mit demselben Namen vorhanden ist, wird die Person aufgefordert, einen anderen Namen einzugeben.

Beim Drucken mit diesem Drucker aus einer beliebigen Anwendung wird das Dokument (im PostScript-Format) an PDF Generator gesendet. PDF Generator konvertiert dann die PostScript-Datei in eine PDF-Datei. Je nach PDF Generator-Konfiguration wird das PDF-Dokument als E-Mail-Anhang an die Person gesendet und/oder an einen angegebenen AEM Forms-Dienst bzw. -Vorgang weitergeleitet.

Zum Einrichten eines PDFG-Netzwerkdruckers sind folgende Schritte erforderlich:

1. Konfigurieren Sie die E-Mail-Einstellungen. (Siehe [Konfigurieren der E-Mail-Einstellungen für den PDFG-Netzwerkdrucker](setting-pdfg-network-printer-windows.md#configure-email-settings-for-pdfg-network-printer).)
1. Konfigurieren Sie in der Administrationskonsole die Einstellungen des PDFG-Netzwerkdruckers. (Siehe [Konfigurieren der Einstellungen für den PDFG-Netzwerkdrucker](setting-pdfg-network-printer-windows.md#configure-the-pdfg-network-printer-settings).)
1. Stellen Sie sicher, dass Ihre Benutzenden über eine gültige E-Mail-Adresse in der AEM Forms-Datenbank verfügen, und weisen Sie jeder Person die PDFG-Benutzerberechtigung zu. <!-- Fix broken link See Setting up and organizing users -->
1. Stellen Sie sicher, dass 32-Bit-JRE6 auf den Computern der Benutzenden installiert ist.
1. Installieren Sie den Drucker auf den Computern der Benutzenden. (Siehe [Installieren des PDFG-Netzwerkdruckers auf Benutzer-Computern](setting-pdfg-network-printer-windows.md#install-pdfg-network-printer-on-a-user-s-computer).)

## Konfigurieren der E-Mail-Einstellungen für den PDFG-Netzwerkdrucker {#configure-email-settings-for-pdfg-network-printer}

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite „Dienstverwaltung“ auf „provider.email_sendmail_service“, geben Sie die SMTP-Einstellungen an und klicken Sie auf „Speichern“.

## Konfigurieren der Einstellungen für den PDFG-Netzwerkdrucker {#configure-the-pdfg-network-printer-settings}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „PDF Generator“ > „PDFG-Netzwerkdrucker“.
1. Wählen Sie in der Liste mit den Adobe PDF-Einstellungen und Sicherheitseinstellungen die Optionen aus, die auf die erstellte PDF-Datei angewendet werden sollen. Weitere Informationen zu diesen Einstellungen finden Sie unter [Konfigurieren von Adobe PDF-Einstellungen](/help/forms/using/admin-help/configuring-pdf-settings.md#configuring-adobe-pdf-settings) und [Konfigurieren von Sicherheitseinstellungen](/help/forms/using/admin-help/configuring-security-settings.md#configuring-security-settings).
1. Um die konvertierten PDF-Dateien wieder an die Benutzenden zurückzusenden, wählen Sie die Option „Konvertierte PDF-Datei per E-Mail zurück an Benutzer senden“ aus und geben Sie die folgenden Informationen an:

   * E-Mail-Adresse, die beim Versenden der PDF-Dateien an die Benutzenden verwendet werden soll.
   * Betreff der E-Mail-Nachricht.
   * Kopfzeile, Nachrichtentext und Fußzeile der E-Mail-Nachricht. In der E-Mail-Nachricht wird &lt;Empfängername> durch den vollständigen Namen der Person ersetzt, die das Dokument gedruckt hat.

1. Um die konvertierten PDF-Dateien an einen AEM Forms-Dienst oder -Prozess zu senden, wählen Sie die Option „Konvertierte PDF an den angegebenen AEM Forms-Dienst oder -Prozess weiterleiten“ aus und geben Sie die folgenden Informationen an:

   * Namen des aufzurufenden Dienstes.
   * Namen des aufzurufenden Dienstvorgangs.
   * Namen des Eingabeparameters, wie in der Datei „component.xml“ des Dienstes oder Prozesses angegeben. Das PDF-Dokument wird als Wert für diesen Eingabeparameter verwendet.

1. Klicken Sie auf Speichern.

Wenn Sie den ursprünglichen Standardtext der E-Mail wiederherstellen möchten, klicken Sie auf „E-Mail-Inhalt wiederherstellen“.

## Installieren des PDFG-Netzwerkdruckers auf Benutzer-Computern {#install-pdfg-network-printer-on-a-user-s-computer}

Benutzende, die entweder über die PDFG-Administrator- oder PDFG-Benutzer-Rolle verfügen, können einen PDFG-Netzwerkdrucker installieren. Sie müssen ein 32-Bit-JDK auf dem Computer installiert haben.

1. (PDFG-Admins) Klicken Sie in der Administrationskonsole auf „Dienste“ > „PDF Generator“ > „PDFG-Netzwerkdrucker“.

   (PDFG-Benutzer) Gehen Sie zu `http(s)://[host]:'port'/pdfgui` und klicken Sie auf den Link unter PDFG Netzwerkdrucker-Installation.

1. Klicken Sie unter „Installation des PDFG-Netzwerkdruckers“ auf den Link. Wenn Sie zur Eingabe der Benutzerkontoinformationen aufgefordert werden, geben Sie den Benutzernamen und das Kennwort an, den bzw. das Sie in Schritt 1 zur Anmeldung verwendet haben. Es wird eine Meldung angezeigt, dass der Drucker erfolgreich installiert wurde.

   ***Hinweis **Wenn sich das Kennwort der Person ändert, muss die betroffene Person den PDFG-Netzwerkdrucker erneut auf ihrem Computer installieren. Es ist nicht möglich, das Kennwort mithilfe der Administrationskonsole zu aktualisieren.*

1. Klicken Sie auf OK.
