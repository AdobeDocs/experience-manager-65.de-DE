---
title: Aktualisieren abgelaufener Reader Extension-Dienstzertifikate
description: 'Reader für erweiterte Dokumente funktioniert nicht, Zertifikate aktualisieren '
source-git-commit: 5f2fc6a32f67cfed3bc4b09b63bcf9689659a99d
workflow-type: tm+mt
source-wordcount: '1572'
ht-degree: 26%

---


# Aktualisieren abgelaufener Reader Extension-Dienstzertifikate {#Updating-expired-Reader-Extension-service-certificates}

Adobe Experience Manager Forms (AEM Forms)-Kunden mit Adobe Managed Services- oder On-Premise-Enterprise-Basislizenzen sind berechtigt, den Reader Extension-Dienst zu verwenden. Der Dienst ermöglicht es einem Unternehmen, interaktive PDF-Dokumente einfach freizugeben, indem die Funktionalität von Adobe Reader um zusätzliche Verwendungsrechte erweitert wird. Der Dienst fügt einem PDF-Dokument Verwendungsrechte hinzu und aktiviert Funktionen, die normalerweise nicht verfügbar sind, wenn ein PDF-Dokument mit Adobe Acrobat Reader DC geöffnet wird, z. B. das Hinzufügen von Kommentaren zu einem Dokument, das Ausfüllen von Formularen und das Speichern des Dokuments. Externe Benutzer benötigen keine zusätzliche Software oder Plug-Ins für das Verwenden von Dokumenten mit aktivierten Benutzerrechten. PDF-Dokumente, für die Nutzungsrechte gelten, werden als Dokumente mit aktivierten Nutzungsrechten bezeichnet. Benutzer, die ein PDF-Dokument mit aktivierten Nutzungsrechten in Adobe Reader öffnen, können Vorgänge durchführen, die für dieses Dokument aktiviert sind.

Adobe nutzt eine PKI (Public-Key-Infrastruktur), um digitale Zertifikate für die Lizenzierung und Aktivierung von Funktionen auszustellen. Adobe hat Zertifikate unter der Zertifizierungsstelle &quot;Adobe Root CA&quot; ausgestellt, die am 7. Januar 2023 ablaufen soll. Dies führt zur Gültigkeit aller Zertifikate, die im Rahmen dieser Zertifizierungsstelle ausgestellt werden. Nach Ablauf des Zertifikats funktionieren alle von den Zertifikaten abhängigen Funktionen nicht mehr. Beispielsweise funktioniert ein durch Leser erweitertes PDF-Dokument, das das Hinzufügen von Kommentaren mit Adobe Acrobat Reader ermöglicht, nach dem 7. Januar 2023 nicht mehr für Kunden. Um dieses Problem zu beheben, sollte der Administrator des Reader Extension-Dienstes unter Verwendung alter Zertifikate neue Zertifikate der neuen Adobe Root CA G2 auf ihre PDF-Dokumente abrufen und erneut anwenden (Leser erweitern die PDF-Dokumente mit neuen Zertifikaten).

Der Ablauf von Zertifikaten wirkt sich sowohl auf AEM Forms on JEE als auch AEM Forms auf OSGi-Stacks aus. Beide Stapel verfügen über unterschiedliche Anweisungen. Wählen Sie je nach Stapel einen der folgenden Pfade aus:

* Aktualisieren von Zertifikaten für eine AEM Forms on JEE-Umgebung
* Aktualisieren von Zertifikaten für eine AEM Forms in einer OSGi-Umgebung

>[!NOTE]
>
>Das Dokument verwendet austauschbar Begriffe und Berechtigungen.

## Voraussetzungen {#Pre-requisites}

Die Aktualisierung der Zertifikate erfordert die Verwendung von Aktionen, die in der AEM Forms-Administrator-Konsole und in den von AEM Forms bereitgestellten Reader Extension-APIs verfügbar sind. Das Dokument richtet sich an Benutzer und Administratoren mit Kenntnissen in der Verwendung von Adobe Experience Manager Forms-APIs. Bevor Sie beginnen, stellen Sie Folgendes sicher:

* der Benutzer über Administratorrechte für die zugrunde liegende AEM Forms-Umgebung verfügt.
* der Benutzer die [Entwicklungsumgebung](https://experienceleague.adobe.com/docs/experience-manager-65/developing/devtools/howto-projects-eclipse.html) und hat Zugriff darauf.
* die Zertifikate zu erhalten.

### Zertifikate abrufen {#obtain-the-certificates}

Die Berechtigung für Rechte wird als digitales Zertifikat übermittelt, das den öffentlichen und den privaten Schlüssel sowie das Kennwort enthält, das für den Zugriff auf die Berechtigung verwendet wird.

Wenn Ihr Unternehmen eine Produktionsversion von Reader Extensions erwirbt, wird die Berechtigung für Produktionsrechte von der Adobe Licensing Website (LWS) bereitgestellt. Eine Produktionsberechtigung für Rechte ist für Ihr Unternehmen eindeutig und kann die von Ihnen benötigten spezifischen Verwendungsrechte aktivieren.

Wenn Sie Reader Extensions über einen Partner oder Softwareanbieter erhalten haben, der Reader Extensions in seine Software integriert hat, wird Ihnen die Berechtigung für Rechte von diesem Partner geliefert, der diese Berechtigungen wiederum von Adobe erhalten hat.

>[!NOTE]
>
>Die Berechtigung für Rechte kann nicht für ein typisches Signieren von Dokumenten oder die Bestätigung von Identitäten verwendet werden. Für diese Zwecke können Sie ein selbst signiertes Zertifikat verwenden oder ein Identitätszertifikat von einer Zertifizierungsstelle anfordern.

Die folgenden Arten von Berechtigungen für Rechte stehen zur Verfügung:

**Kundenauswertung**: Eine Berechtigung mit einer kurzen Gültigkeitsdauer, die Kunden zur Verfügung gestellt wird, die Reader-Erweiterungen auswerten möchten. Verwendungsrechte, die mithilfe dieser Berechtigung auf Dokumente angewendet werden, laufen mit Ablauf der Berechtigung ebenfalls ab. Dieser Berechtigungstyp ist nur zwei bis drei Monate gültig.

**Produktion**: Eine Berechtigung mit einer langen Gültigkeitsdauer, die Kunden gewährt wird, die das gesamte Produkt gekauft haben. Produktionsberechtigungen sind für jeden Kunden eindeutig, können jedoch auf mehreren Systemen installiert werden.

Wenn Sie bereits Zertifikate zum Reader Extending von PDF-Dateien verwendet haben, laden Sie ein Produktionszertifikat von herunter. [Adobe Licensing Website (LWS)](https://licensing.adobe.com/).

## Aktualisieren und Anwenden von Zertifikaten für eine AEM Forms on JEE-Umgebung {#Updating-and-Applying-certificates-for-an-AEM-Forms-on-JEE-environment}

Für die Aktualisierung und Anwendung neuer Zertifikate auf dem AEM Forms on JEE-Stapel ist der Import neuer Anmeldeinformationen, das Entfernen von Verwendungsrechten aus vorhandenen PDF-Dokumenten und das Anwenden von Verwendungsrechten erforderlich. Sie können die Admin Console verwenden, um Anmeldeinformationen zu importieren, und AEM Forms Reader Extension-APIs, um Verwendungsrechte zu entfernen und anzuwenden.

### Berechtigungen importieren und konfigurieren

Sie können die Seiten &quot;Trust Store-Verwaltung&quot;verwenden, um neue oder Ersatzberechtigungen zu importieren. Der Trust Store kann mehr als eine Berechtigung für Reader Extensions enthalten. Sie müssen eine dieser Berechtigungen als Standardberechtigung für Reader Extensions festlegen. Die Standardberechtigung wird verwendet, wenn ein Workbench-Benutzer nicht entscheiden kann, welche Berechtigung bei der Prozesserstellung verwendet werden soll. Diese Regeln gelten für Standardberechtigungen:

* Wenn Sie eine Berechtigung für Reader Extensions importieren und der Trust Store keine weiteren Berechtigungen für Reader Extensions enthält, wird er als Standard festgelegt.
* Wenn Sie eine Reader Extensions-Berechtigung importieren und die Option &quot;Standard&quot;ausgewählt ist, wird der Standardtyp aus einer vorhandenen Standardberechtigung entfernt. Die importierte Berechtigung wird die Standardberechtigung.
* Standardberechtigungen für Reader Extensions können nicht gelöscht werden. Um die Standardberechtigung zu löschen, müssen Sie zunächst eine andere Berechtigung als Standard festlegen. Dabei gilt folgende Ausnahme: Wenn es nur eine Berechtigung gibt, können Sie diese löschen, obwohl es sich dabei um die Standardberechtigung handelt.
* Die Standardberechtigung für Reader Extensions kann nicht aktualisiert werden.

Importieren der Anmeldeinformationen:

1. Klicken Sie in Administration Console auf „Einstellungen“ > „Trust Store-Verwaltung“ > „Lokale Berechtigungen“.
1. Klicken Sie auf „Importieren“ und wählen Sie unter „Trust Store-Typ“ die Option „Acrobat Reader DC Extensions-Berechtigung“.
1. (Optional) Um anzugeben, dass dies die Standardberechtigung ist, die mit Acrobat Reader DC Extensions verwendet werden soll, wählen Sie „Standard“ aus.
1. Geben Sie in das Feld „Alias“ einen Bezeichner für die Berechtigung ein. Dieser Bezeichner wird in Acrobat Reader DC Extensions als Anzeigename für die Berechtigung verwendet. Außerdem wird dieser Alias für den programmgesteuerten Zugriff auf die Berechtigung mithilfe des AEM Forms SDK verwendet.
1. Klicken Sie auf „Eine Datei auswählen“, um die Berechtigung zu suchen. Geben Sie das Kennwort der Berechtigung ein und klicken Sie auf „OK“.

Wenn die Fehlermeldung &quot;Berechtigung konnte nicht importiert werden aufgrund eines falschen Dateiformats oder eines falschen Kennworts&quot;angezeigt wird, überprüfen Sie, ob das Kennwort gültig ist.

Sie können Berechtigungen auch importieren und programmgesteuert löschen. (Weitere Informationen finden Sie unter [Programmieren mit AEM Forms](../../developing/credentials.md).)

### Entfernen von Verwendungsrechten aus vorhandenen PDF-Dokumenten mit aktivierten Berechtigungen

Entfernen Sie Verwendungsrechte aus vorhandenen PDF-Dokumenten mit aktivierten Berechtigungen, bevor Sie Verwendungsrechte mit aktuellen Berechtigungen anwenden. AEM Forms on JEE bietet APIs zum Entfernen von Nutzungsrechten. Detaillierte Anweisungen finden Sie unter [Entfernen von Verwendungsrechten aus PDF-Dokumenten](../../developing/assigning-usage-rights.md#removing-usage-rights-from-pdf-documents).

Informationen zum Entfernen von Verwendungsrechten für in Workbench entwickelte AEM Forms on JEE-Prozesse finden Sie unter [Workbench-Hilfe](https://helpx.adobe.com/content/dam/help/de/experience-manager/6-5/forms/pdf/WorkbenchHelp.pdf).

### Verwendungsrechte auf PDF-Dokumente anwenden

Wenden Sie nach dem Import neuer Anmeldeinformationen und dem Entfernen von Verwendungsrechten aus vorhandenen PDF-Dokumenten mit aktivierten Berechtigungen mithilfe der neuen Anmeldeinformationen Verwendungsrechte auf PDF-Dokumente an. Mit der Java Client-API und dem Webdienst von Acrobat Reader DC Extensions können Sie Verwendungsrechte auf PDF-Dokumente anwenden.  Weitere Informationen finden Sie unter [Anwenden von Nutzungsrechten auf PDF-Dokumente](../../developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).


## Aktualisieren und Anwenden von Zertifikaten für eine AEM Forms in einer OSGi-Umgebung {#Updating-and-applying-certificates-for-an-AEM-Forms-on-OSGi-environment}

Für das Aktualisieren und Anwenden neuer Zertifikate auf AEM Forms auf dem OSGi-Stapel ist der Import neuer Berechtigungen, das Entfernen von Verwendungsrechten aus vorhandenen PDF-Dokumenten und das Anwenden von Verwendungsrechten erforderlich. Sie können die Admin Console verwenden, um Anmeldeinformationen zu importieren, und AEM Forms Reader Extension-APIs, um Verwendungsrechte zu entfernen und anzuwenden.

### Importberechtigungen {#Import-credentials}

In einer AEM Forms on OSGi-Umgebung ist eine Berechtigung für die Reader-Erweiterung mit dem fd-service -Benutzer verknüpft. Bevor Sie Anmeldeinformationen für den Fd-User-Schlüsselspeicher hinzufügen, führen Sie die folgenden Schritte aus, um einen Schlüssel-Store zu erstellen:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz als Administrator an.
1. Navigieren Sie zu Tools > Sicherheit > Benutzer.
1. Scrollen Sie in der Liste der Benutzer nach unten, bis Sie das fd-service-Benutzerkonto finden.
1. Klicken Sie auf den Benutzer fd-service .
1. Klicken Sie auf die Registerkarte Keystore .
1. Klicken Sie auf KeyStore erstellen .
1. Legen Sie das KeyStore Access Password fest und speichern Sie Ihre Einstellungen, um das KeyStore-Kennwort zu erstellen.

Fügen Sie nach dem Erstellen des Key-Stores Anmeldeinformationen zum fd-service-Benutzer hinzu.

>[!VIDEO](https://images-tv.adobe.com/mpcv3/5577/8db8e554-f04b-4fae-8108-b9b5e0eb03ad_1627925794.854x480at800_h264.mp4)

Der folgende Befehl listet die Details der pfx-Datei auf. Bevor Sie den Befehl ausführen, navigieren Sie zum Verzeichnis, das die .pfx-Datei enthält.

`keytool -v -list -storetype pkcs12 -keystore <name of your .pfx file>`

Beispiel: keytool -v -list -storetype pkcs12 -keystore 1005566.pfx , wobei 1005566.pfx der Name meiner pfx-Datei ist

### Entfernen von Verwendungsrechten aus vorhandenen PDF-Dokumenten mit aktivierten Berechtigungen

Entfernen Sie Verwendungsrechte aus vorhandenen PDF-Dokumenten mit aktivierten Berechtigungen, bevor Sie Verwendungsrechte mit aktuellen Berechtigungen anwenden. Sie können die Verwendungsrechte für ein Dokument entfernen, indem Sie die removeUsageRights-API in der docAssuranceService-API aufrufen. Detaillierte Informationen finden Sie unter [Verwendungsrechte entfernen](/help/forms/using/aem-document-services-programmatically.md#removing-usage-rights) Dokument.

### Verwendungsrechte auf PDF-Dokumente anwenden

Um Verwendungsrechte in einer AEM Forms in einer OSGi-Umgebung anzuwenden, erstellen Sie einen benutzerdefinierten OSGi-Dienst auf die Verwendungsrechte für die Dokumente. Sie können auch ein Servlet mit einer POST-Methode erstellen, um dem Leser die erweiterte PDF zurückzugeben. Detaillierte Anweisungen finden Sie unter [Anwenden von Reader-Erweiterungen](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/document-services/apply-reader-extension-rights-to-pdf.html).

## Häufig gestellte Fragen

**An wen kann ich mich bei weiteren Fragen wenden?**

Sie können [Adobe-Support](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;lang=de#support) oder ein Support-Ticket erstellen.

**Was passiert, wenn ich mein Zertifikat nicht vor dem 7. Januar 2023 aktualisiert habe?**

Beim Versuch, einen mit alten PDF-Zertifikaten erweiterten Reader für-Dokumente zu öffnen, wird eine Fehlermeldung angezeigt, die den Benutzern keinen Zugriff mehr auf die mit dem Leser erweiterten Funktionen gewährt. Ein Beispielfehler ist.

`The document has been changed since it was created and use of extended features in no longer available. Please contact the author for the orignal version of this document.`

**Gibt es eine Änderung im Namen der neuen Beschreibung?**

In den neuen Reader Extension-Zertifikaten wird in der Beschreibung als Programmname G3-P24 angegeben. In den älteren Zertifikaten wurde in der Beschreibung der Programmname P24 angegeben.