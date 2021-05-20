---
title: Einrichten eines PDFG-Netzwerkdruckers (nur Windows)
seo-title: Einrichten eines PDFG-Netzwerkdruckers (nur Windows)
description: Erfahren Sie, wie Sie einen PDFG-Netzwerkdrucker (nur Windows) einrichten
seo-description: Erfahren Sie, wie Sie einen PDFG-Netzwerkdrucker (nur Windows) einrichten
uuid: 13b8481e-5ef0-4a07-9602-7bc4d9e05dd4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 7620e5e4-022e-49b2-8cfe-d5eec8ab99d7
feature: PDF Generator
exl-id: c3fc159e-2677-4b71-b0b2-2feaf69e1a32
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 97%

---

# Einrichten eines PDFG-Netzwerkdruckers (nur Windows) {#setting-up-a-pdfg-network-printer-windows-only}

Mit dem PDFG-Netzwerkdrucker können Benutzer ein PDF-Dokument aus jeder Anwendung heraus erstellen, die Druckfunktionen unterstützt. Nachdem ein Benutzer den PDFG-Netzwerkdrucker installiert hat, wird ein neuer Drucker mit dem Namen *PDF Generator* im Bereich „Drucker“ in der Windows-Systemsteuerung angezeigt. Wenn bereits ein Drucker mit demselben Namen vorhanden ist, wird der Benutzer aufgefordert, einen anderen Namen einzugeben.

Beim Drucken mit diesem Drucker aus einer beliebigen Anwendung wird das Dokument (im PostScript-Format) an PDF Generator gesendet. PDF Generator konvertiert dann die PostScript-Datei in eine PDF-Datei. Je nach der Konfiguration von PDF Generator wird das PDF-Dokument als Anlage zu einer E-Mail an den Benutzer gesendet oder an einen angegebenen AEM Forms-Dienst oder -Vorgang weitergeleitet oder es werden beide Aktionen ausgeführt.

Zum Einrichten eines PDFG-Netzwerkdruckers sind folgende Schritte erforderlich:

1. E-Mail-Einstellungen konfigurieren. (Siehe [E-Mail-Einstellungen für den PDFG-Netzwerkdrucker konfigurieren](setting-pdfg-network-printer-windows.md#configure-email-settings-for-pdfg-network-printer).)
1. Konfigurieren Sie in Administration Console die Einstellungen des PDFG-Netzwerkdruckers. (Siehe [Einstellungen für den PDFG-Netzwerkdrucker konfigurieren](setting-pdfg-network-printer-windows.md#configure-the-pdfg-network-printer-settings).)
1. Stellen Sie sicher, dass Ihre Benutzer über eine gültige E-Mail-Adresse in der AEM Forms-Datenbank verfügen, und weisen Sie jedem Benutzer die PDFG-Benutzerberechtigung zu. <!-- Fix broken link See Setting up and organizing users -->
1. Stellen Sie sicher, dass 32-Bit-JRE6 auf den Computern der Benutzer installiert ist.
1. Installieren Sie den Drucker auf den Computern der Benutzer. (Siehe [PDFG-Netzwerkdrucker auf dem Computer des Benutzers installieren](setting-pdfg-network-printer-windows.md#install-pdfg-network-printer-on-a-user-s-computer).)

## E-Mail-Einstellungen für den PDFG-Netzwerkdrucker konfigurieren {#configure-email-settings-for-pdfg-network-printer}

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite „Dienstverwaltung“ auf „provider.email_sendmail_service“, geben Sie die SMTP-Einstellungen an und klicken Sie auf „Speichern“.

## Einstellungen für den PDFG-Netzwerkdrucker konfigurieren  {#configure-the-pdfg-network-printer-settings}

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „PDFG-Netzwerkdrucker“.
1. Wählen Sie in der Liste „Adobe PDF-Einstellungen und Sicherheitseinstellungen“ die Optionen aus, die auf die erstellte PDF-Datei angewendet werden sollen. Genauere Informationen zu diesen Einstellungen finden Sie unter [Adobe PDF-Einstellungen konfigurieren](/help/forms/using/admin-help/configuring-pdf-settings.md#configuring-adobe-pdf-settings) und [Sicherheitseinstellungen konfigurieren](/help/forms/using/admin-help/configuring-security-settings.md#configuring-security-settings).
1. Um die konvertierten PDF-Dateien wieder zu den Benutzern zurückzusenden, wählen Sie die Option „Konvertierte PDF-Datei per E-Mail zurück an Benutzer senden“ aus und geben Sie die folgenden Informationen an:

   * Die E-Mail-Adresse, die beim Versenden der PDF-Dateien an die Benutzer verwendet werden soll
   * Den Betreff der E-Mail
   * Die Kopfzeile, den Nachrichtentext und die Fußzeile der E-Mail In der E-Mail wird &lt;Empfängername> durch den vollständigen Namen des Benutzers, der das Dokument gedruckt hat, ersetzt.

1. Um die konvertierten PDF-Dateien an einen AEM Forms-Dienst oder -Prozess weiterzuleiten, wählen Sie die Option „Konvertierte PDF an den angegebenen AEM Forms-Dienst oder -Prozess weiterleiten“ und geben Sie die folgenden Informationen an:

   * Name des aufzurufenden Dienstes.
   * Name des aufzurufenden Vorgangs des Dienstes.
   * Name des Eingabeparameters wie in der Datei „component.xml“ des Dienstes oder Prozesses angegeben. Das PDF-Dokument wird als Wert für diesen Eingabeparameter verwendet.

1. Klicken Sie auf Speichern.

Wenn Sie den ursprünglichen Standardtext in der E-Mail wiederherstellen möchten, klicken Sie auf „E-Mail-Inhalt wiederherstellen“.

## PDFG-Netzwerkdrucker auf dem Computer des Benutzers installieren  {#install-pdfg-network-printer-on-a-user-s-computer}

Benutzer, die entweder über die Rolle „PDFG-Administrator“ oder über die Rolle „PDFG-Benutzer“ verfügen, können einen PDFG-Netzwerkdrucker installieren. Sie müssen ein 32-Bit JDK auf dem Computer installiert haben.

1. (PDFG-Administratoren) Klicken Sie in Administration Console auf „Dienste“ > „ PDF Generator “ > „PDFG-Netzwerkdrucker“.

   (PDFG-Benutzer) Wechseln Sie zu `http(s)://[host]:'port'/pdfgui` und klicken Sie auf den Link unter &quot;Installation des PDFG-Netzwerkdruckers&quot;.

1. Klicken Sie unter „Installation des PDFG-Netzwerkdruckers“ auf den Link. Wenn Sie zur Eingabe der Benutzerkontoinformationen aufgefordert werden, geben Sie den Benutzernamen und das Kennwort an, das Sie in Schritt 1 bei der Anmeldung verwendet haben. Es wird eine Nachricht angezeigt, dass der Drucker erfolgreich installiert wurde.

   ***Hinweis **Wenn sich das Kennwort des Benutzers ändert, muss der PDFG-Netzwerkdrucker erneut auf dessen Computer installiert werden. Es ist nicht möglich, das Kennwort mithilfe von Administration Console zu aktualisieren.*

1. Klicken Sie auf OK.
