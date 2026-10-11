---
title: Aktivieren von AEM, um durch Document Security geschützte PDF-Dokumente zu durchsuchen
description: Erfahren Sie, wie Sie die native AEM-Suche aktivieren, um eine Volltextsuche in DRM-geschützten PDF-Dokumenten durchzuführen.
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
noindex: true
feature: Document Security
exl-id: 91cbd1f1-d53d-455b-8d2c-6918b521db81
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 50158d81-1c06-57f7-8bd7-e8ff76a93f85
    internal-label: Document Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 97%
---
# AEM aktivieren, um durch Document Security geschützte PDF-Dokumente zu durchsuchen{#enable-aem-to-search-document-security-protected-pdf-and-microsoft-office-documents}

Adobe Experience Manager bietet eine Benutzeroberfläche zum Suchen und Auffinden verschiedener Assets, die in AEM gespeichert werden. Mithilfe der nativen Suche kann nach AEM-Assets gesucht und eine Textsuche für verschiedene häufig verwendete Dokumentformate wie Textdateien, Microsoft Office-Dokumente und PDF-Dokumente durchgeführt werden. Sie können dies auch erweitern und die native Suche aktivieren, um eine Volltextsuche in DRM-geschützten PDF- und Microsoft-Office-Dokumenten durchzuführen.

Führen Sie die folgenden Schritte aus, um AEM die Suche in durch die Dokumentensicherheit geschützten PDF- und Microsoft Office-Dokumenten zu ermöglichen:

## Bevor Sie beginnen {#before-you-start}

* Installieren und konfigurieren Sie die AEM Forms-Dokumentensicherheit.
* Fügen Sie das Paket „sun.util.calendar“ zur Zulassungsliste „Deserialisierungs **Firewallkonfiguration“ hinzu** Die Konfiguration ist unter `https://'[server]:[port]'/system/console/configMgr` aufgeführt.
* Stellen Sie sicher, dass alle AEM-Pakete aktiv sind. Die Pakete sind unter `https://'[server]:[port]'/system/console/bundles` aufgeführt. Wenn alle Pakete nicht aktiv, warten Sie einige Minuten und überprüfen Sie den Status der Pakete.

## Erstellen einer sicheren Verbindung in AEM Forms Workflow (AEM Forms auf JEE) {#establish-a-secure-connection-within-aem-forms-workflow-aem-forms-on-jee}

Eine sichere Verbindung ermöglicht den nahtlosen Informationsfluss zwischen AEM Forms auf JEE und den OSGi-Diensten, die auf demselben Server ausgeführt werden. Verwenden Sie eine der folgenden Methoden, um eine sichere Verbindung herzustellen:

* Konfigurieren des AEM Forms Client SDK-Pakets mit AEM Forms on JEE-Administratorberechtigungen
* Konfigurieren von AEM Forms Client SDK-Pakets mit gegenseitiger Authentifizierung

### Konfigurieren des AEM Forms Client SDK-Pakets mit AEM Forms on JEE-Administratorberechtigungen {#configure-aem-forms-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Öffnen Sie AEM Configuration Manager und melden Sie sich als Admin an. Die Standard-URL lautet https://&lt;serverName>:&lt;port>/lc/system/console/configMgr.
1. Öffnen Sie das AEM Forms Client SDK-Pakets. Geben Sie Werte für die folgenden Eigenschaften an:

   * **Server-URL:** Geben Sie die HTTP-URL des AEM Forms on JEE-Servers an. Um die Kommunikation über HTTPS zu aktivieren, starten Sie AEM Forms auf JEE-Server mit dem Parameter -Djavax.net.ssl.trustStore=&lt;Pfad der Keystore-Datei von AEM Forms auf JEE> neu.
   * **Dienstname**: Fügen Sie den RightsManagementService zur Liste der angegebenen Dienste hinzu.
   * **Benutzername:** Geben Sie den Benutzernamen des AEM Forms on JEE-Kontos an, um Aufrufe vom AEM Forms on JEE-Server zu initiieren. Das angegebene Konto benötigt Berechtigungen zum Aufrufen der Dokumentendienste auf dem AEM Forms auf JEE-Server.
   * **Kennwort**: Geben Sie das Kennwort für das AEM Forms auf JEE-Konto an, das im Feld „Benutzername“ erwähnt wird.

   Klicken Sie auf **Speichern**. AEM ist jetzt aktiviert, um PDF- und Microsoft Office-Dokumente durchsuchen zu können, die durch die Dokumentensicherheit geschützt sind.

### Konfigurieren von AEM Forms Client SDK-Pakets mit gegenseitiger Authentifizierung {#configure-aem-forms-client-sdk-bundle-using-mutual-authentication}

1. Aktivieren Sie die gegenseitige Authentifizierung für AEM Forms auf JEE. Weitere Informationen finden Sie unter [CAC und gegenseitige Authentifizierung](https://helpx.adobe.com/de/livecycle/kb/cac-mutual-authentication.html).
1. Öffnen Sie AEM Configuration Manager und melden Sie sich als Admin an. Die Standard-URL lautet https://&lt;serverName>:&lt;port>/lc/system/console/configMgr.
1. Öffnen Sie das AEM Forms Client SDK-Pakets. Geben Sie Werte für die folgenden Eigenschaften an:

   * **Server-URL:** Geben Sie die HTTPS-URL des AEM Forms on JEE-Servers an. Um die Kommunikation über HTTPS zu aktivieren, starten Sie AEM Forms auf JEE-Server mit dem Parameter -Djavax.net.ssl.trustStore=&lt;Pfad der Keystore-Datei von AEM Forms auf JEE> neu.
   * **2-Weg-SSL aktivieren**: Aktivieren Sie die Option für 2-Weg-SSL.
   * **KeyStore-Datei-URL**: Geben Sie die URL der KeyStore-Datei an.
   * **TrustStore-Datei-URL**: Geben Sie die URL für die TrustStore-Datei an.
   * **KeyStore-Kennwort**: Geben Sie das Kennwort für die KeyStore-Datei an.
   * **TrustStorePassword**: Geben Sie das Kennwort für die TrustStore-Datei an.
   * **Service-Name**: Fügen Sie den RightsManagementService zur Liste der angegebenen Services hinzu.

   Klicken Sie auf **Speichern**. AEM ist jetzt aktiviert, um PDF- und Microsoft Office-Dokumente durchsuchen zu können, die durch die Dokumentensichereit geschützt sind.

   >[!NOTE]
   >
   > Es wird empfohlen, den Befehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

## Indexieren eines richtliniengeschützten PDF- oder Microsoft Office-Beispieldokuments {#index-a-sample-policy-protected-pdf-or-microsoft-office-document}

1. Melden Sie sich bei AEM Assets als Administrator an.
1. Erstellen Sie einen Ordner in AEM Digital Asset Manager und laden Sie die durch Richtlinien geschützten PDF oder Microsoft Office-Dokumente in den neu erstellten Ordner hoch. Durchsuchen Sie nun die Inhalte der richtliniengeschützten Dokumente mit der AEM-Suche. Das Dokument muss zurückzugeben werden, das den gesuchten Text enthält, das Text enthält.
