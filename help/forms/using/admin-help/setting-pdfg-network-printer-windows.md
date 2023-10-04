---
title: Einrichten eines PDFG-Netzwerkdruckers (nur Windows)
description: Erfahren Sie, wie Sie einen PDFG-Netzwerkdrucker einrichten ( nur Windows ).
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
exl-id: c3fc159e-2677-4b71-b0b2-2feaf69e1a32
source-git-commit: 5bdf42d1ce7b2126bfb2670049deec4b6eaedba2
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 11%

---

# Einrichten eines PDFG-Netzwerkdruckers (nur Windows) {#setting-up-a-pdfg-network-printer-windows-only}

Mit dem PDFG-Netzwerkdrucker können Benutzer ein PDF-Dokument aus jeder Anwendung erstellen, die Druckfunktionen unterstützt. Nachdem ein Benutzer den PDFG-Netzwerkdrucker installiert hat, wird ein neuer Drucker mit dem Namen *PDF Generator* im Bereich „Drucker“ in der Windows-Systemsteuerung angezeigt. Wenn bereits ein Drucker mit demselben Namen vorhanden ist, wird der Benutzer aufgefordert, einen anderen Namen anzugeben.

Beim Drucken auf diesem Drucker aus einer beliebigen Anwendung wird das Dokument (im PostScript-Format) an PDF Generator gesendet, der die PostScript-Datei in PDF konvertiert. Je nachdem, wie Sie den PDF Generator konfiguriert haben, wird das PDF-Dokument als Anlage zu einer E-Mail-Nachricht an den Benutzer gesendet, das PDF-Dokument an einen angegebenen AEM Forms-Dienst oder -Prozess weitergeleitet oder es werden beide Aktionen ausgeführt.

Die folgenden Schritte sind erforderlich, um einen PDFG-Netzwerkdrucker einzurichten:

1. E-Mail-Einstellungen konfigurieren. (Siehe [E-Mail-Einstellungen für den PDFG-Netzwerkdrucker konfigurieren](setting-pdfg-network-printer-windows.md#configure-email-settings-for-pdfg-network-printer).
1. Konfigurieren Sie in Administration Console die Einstellungen des PDFG-Netzwerkdruckers. (Siehe [PDFG-Netzwerkdruckereinstellungen konfigurieren](setting-pdfg-network-printer-windows.md#configure-the-pdfg-network-printer-settings).
1. Stellen Sie sicher, dass Ihre Benutzer mit einer gültigen E-Mail-Adresse in der AEM Forms-Datenbank konfiguriert sind, und weisen Sie jedem Benutzer die PDFGUserPermission zu. <!-- Fix broken link See Setting up and organizing users -->
1. Stellen Sie sicher, dass 32-Bit JRE6 auf den Computern Ihrer Benutzer installiert ist.
1. Installieren Sie den Drucker auf den Computern Ihrer Benutzer. (Siehe [Installieren Sie den PDFG-Netzwerkdrucker auf dem Computer eines Benutzers](setting-pdfg-network-printer-windows.md#install-pdfg-network-printer-on-a-user-s-computer).

## E-Mail-Einstellungen für den PDFG-Netzwerkdrucker konfigurieren {#configure-email-settings-for-pdfg-network-printer}

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite Dienstverwaltung auf provider.email_sendmail_service , geben Sie die SMTP-Einstellungen an und klicken Sie auf Speichern.

## PDFG-Netzwerkdruckereinstellungen konfigurieren {#configure-the-pdfg-network-printer-settings}

1. Klicken Sie in Administration Console auf Dienste > PDF Generator > PDFG-Netzwerkdrucker.
1. Wählen Sie in den Adobe PDF-Einstellungen und in den Sicherheitseinstellungen die Optionen aus, die auf die generierte PDF angewendet werden sollen. Weitere Informationen zu diesen Einstellungen finden Sie unter [Konfigurieren von Adobe PDF-Einstellungen](/help/forms/using/admin-help/configuring-pdf-settings.md#configuring-adobe-pdf-settings) und [Sicherheitseinstellungen konfigurieren](/help/forms/using/admin-help/configuring-security-settings.md#configuring-security-settings).
1. Um die konvertierten PDF wieder an Benutzer zu senden, wählen Sie die Option Konvertierte PDF-Datei per E-Mail an den Benutzer zurücksenden aus und geben Sie die folgenden Informationen an:

   * Die E-Mail-Adresse, die zum Senden von PDF an die Benutzer verwendet werden soll
   * Betreff der E-Mail
   * Die Kopf-, Fuß- und Textkopfzeile der E-Mail-Nachricht. In der E-Mail-Nachricht &lt;receivername> durch den vollständigen Namen des Benutzers ersetzt, der das Dokument gedruckt hat.

1. Um die konvertierten PDF an einen AEM Forms-Dienst oder -Prozess zu senden, wählen Sie die Option &quot;Weiterleiten der konvertierten PDF an den angegebenen AEM Forms-Dienst oder -Prozess&quot;und geben Sie die folgenden Informationen an:

   * Der Name des aufzurufenden Dienstes
   * Der Name des Vorgangs des aufzurufenden Dienstes
   * Der Name des Eingabeparameters, wie in der Datei &quot;component.xml&quot;des Dienstes oder Prozesses angegeben. Das PDF-Dokument wird als Wert für diesen Eingabeparameter verwendet.

1. Klicken Sie auf Speichern.

Wenn Sie zum ursprünglichen Standard-E-Mail-Text zurückkehren möchten, klicken Sie auf E-Mail-Inhalt wiederherstellen .

## Installieren Sie den PDFG-Netzwerkdrucker auf dem Computer eines Benutzers {#install-pdfg-network-printer-on-a-user-s-computer}

Benutzer mit der Rolle &quot;PDFG-Administrator&quot;oder &quot;PDFG-Benutzer&quot;können einen PDFG-Netzwerkdrucker installieren. Auf dem Computer muss ein 32-Bit-JDK installiert sein.

1. (PDFG-Administratoren) Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;PDFG-Netzwerkdrucker&quot;.

   (PDFG-Benutzer) Gehen Sie zu `http(s)://[host]:'port'/pdfgui` und klicken Sie auf den Link unter PDFG Netzwerkdrucker-Installation.

1. Klicken Sie unter &quot;Installation des PDFG-Netzwerkdruckers&quot;auf den Link. Wenn Sie zur Eingabe von Benutzerkontoinformationen aufgefordert werden, geben Sie den Benutzernamen und das Kennwort an, mit denen Sie sich in Schritt 1 angemeldet haben. Es wird eine Meldung angezeigt, die besagt, dass der Drucker erfolgreich installiert wurde.

   ***Hinweis **: Wenn sich das Kennwort des Benutzers ändert, müssen die Benutzer den PDFG-Netzwerkdrucker erneut auf ihren Computern installieren. Sie können das Kennwort nicht über Administration Console aktualisieren.*

1. Klicken Sie auf OK.
