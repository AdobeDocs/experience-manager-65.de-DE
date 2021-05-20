---
title: AEM aktivieren, um durch Document Security geschützte PDF-Dokumente zu durchsuchen
seo-title: AEM aktivieren, um durch Document Security geschützte PDF-Dokumente zu durchsuchen
description: Erfahren Sie, wie Sie die native AEM-Suche aktivieren, um eine Volltextsuche in DRM-geschützten PDF-Dokumenten durchzuführen.
seo-description: Erfahren Sie, wie Sie die native AEM-Suche aktivieren, um eine Volltextsuche in DRM-geschützten PDF-Dokumenten durchzuführen.
uuid: dba882f8-bad4-4122-a0df-03cf087afb23
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 7eebef08-83b9-4b56-90ec-35ab3b0c27e8
noindex: true
feature: Dokumentensicherheit
exl-id: 91cbd1f1-d53d-455b-8d2c-6918b521db81
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 80%

---

# AEM aktivieren, um durch Document Security geschützte PDF-Dokumente zu durchsuchen{#enable-aem-to-search-document-security-protected-pdf-and-microsoft-office-documents}

Adobe Experience Manager bietet eine Benutzeroberfläche zum Suchen und Auffinden verschiedener Assets, die in AEM gespeichert werden. Die programmeigene Suchfunktion kann AEM-Assets durchsuchen und nach  Textsuche in verschiedenen häufig verwendeten Dokumentformaten wie Textdateien, Microsoft Office-Dokumenten und PDF-Dokumenten. Sie können die native Suche auch erweitern und aktivieren, um eine Volltextsuche in DRM-geschützten PDF- und Microsoft Office-Dokumenten durchzuführen.

Führen Sie die folgenden Schritte aus, um AEM die Suche in sicherheitsgeschützten PDF- und Microsoft Office Dokumenten zu ermöglichen:

## Bevor Sie beginnen {#before-you-start}

* Installieren und konfigurieren Sie AEM Forms Document Security.
* Fügen Sie das Paket sun.util.calendar zur Zulassungsliste der **Deserialisierungs-Firewall-Konfiguration hinzu.** Die Konfiguration wird unter  `https://'[server]:[port]'/system/console/configMgr`aufgeführt.
* Stellen Sie sicher, dass alle AEM-Pakete aktiv sind. Die Bundles sind unter `https://'[server]:[port]'/system/console/bundles` aufgeführt. Wenn alle Bundles nicht aktiv, warten Sie einige Minuten und überprüfen Sie den Status der Bundles.

## Erstellen Sie eine sichere Verbindung AEM Forms Workflow (AEM Forms on JEE) {#establish-a-secure-connection-within-aem-forms-workflow-aem-forms-on-jee}

Eine sichere Verbindung ermöglicht den Informationsfluss zwischen AEM Forms on JEE und den OSGi-Diensten, die auf demselben Server ausgeführt werden. Verwenden Sie eine der folgenden Methoden, um eine sichere Verbindung herzustellen:

* Konfigurieren des AEM Forms Client SDK Bundle mit AEM Forms on JEE-Administratorberechtigungen
* Konfigurieren von AEM Forms Client SDK Bundle mit gegenseitiger Authentifizierung  

### Konfigurieren des AEM Forms Client SDK Bundle mit AEM Forms on JEE-Administratorberechtigungen {#configure-aem-forms-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Öffnen Sie AEM Configuration Manager und melden Sie sich als Administrator an. Die Standard-URL lautet https://&lt;ServerName>:&lt;Port>/lc/system/console/configMgr.
1. Öffnen Sie das AEM Forms Client SDK Bundle. Geben Sie Werte für die folgenden Eigenschaften an:

   * **Server-URL:** Geben Sie die HTTP-URL des AEM Forms on JEE-Servers an. Um die Kommunikation über HTTPS zu aktivieren, starten Sie den AEM Forms on JEE-Server mit dem Parameter -Djavax.net.ssl.trustStore=&lt;Pfad der AEM Forms on JEE-Keystore-Datei> neu.
   * **Dienstname**: Fügen Sie den RightsManagementService zur Liste der angegebenen Dienste hinzu.
   * **Benutzername:** Geben Sie den Benutzernamen des AEM Forms on JEE-Kontos an, um Aufrufe vom AEM Forms on JEE-Server zu initiieren. Das angegebene Konto benötigt Berechtigungen zum Aufrufen der Document Services auf dem AEM Forms on JEE-Server.
   * **Kennwort:** Geben Sie das Kennwort für das AEM Forms on JEE-Konto an, das im Feld „Benutzername“ erwähnt ist.

   Klicken Sie auf **Speichern**. AEM ist aktiviert, um PDF- und Microsoft Office-Dokumente, die durch Document Security geschützt sind zu durchsuchen.

### Konfigurieren von AEM Forms Client SDK Bundle mit gegenseitiger Authentifizierung   {#configure-aem-forms-client-sdk-bundle-using-mutual-authentication}

1. Aktivieren Sie die gegenseitige Authentifizierung für AEM Forms on JEE. Weitere Informationen finden Sie unter [CAC und gegenseitige Authentifizierung](https://helpx.adobe.com/de/livecycle/kb/cac-mutual-authentication.html).
1. Öffnen Sie AEM Configuration Manager und melden Sie sich als Administrator an. Die Standard-URL lautet https://&lt;ServerName>:&lt;Port>/lc/system/console/configMgr.
1. Öffnen Sie das AEM Forms Client SDK Bundle. Geben Sie Werte für die folgenden Eigenschaften an:

   * **Server-URL:** Geben Sie die HTTPS-URL des AEM Forms on JEE-Servers an. Um die Kommunikation über HTTPS zu aktivieren, starten Sie den AEM Forms on JEE-Server mit dem Parameter -Djavax.net.ssl.trustStore=&lt;Pfad der AEM Forms on JEE-Keystore-Datei> neu.
   * **2-Weg-SSL aktivieren**: Aktivieren Sie die Option für 2-Weg-SSL.
   * **KeyStore-Datei-URL**: Geben Sie die URL der KeyStore-Datei an.
   * **TrustStore-Datei-URL**: Geben Sie die URL für die TrustStore-Datei an.
   * **KeyStore-Kennwort**: Geben Sie das Kennwort für die KeyStore-Datei an.
   * **TrustStorePassword**: Geben Sie das Kennwort für die TrustStore-Datei an.
   * **Dienstname**: Fügen Sie den RightsManagementService zur Liste der angegebenen Dienste hinzu.

   Klicken Sie auf **Speichern**. AEM ist aktiviert, um PDF- und Microsoft Office-Dokumente, die durch Document Security geschützt sind zu durchsuchen.

## Indexieren Sie ein Beispiel für ein richtliniengeschütztes PDF- oder Microsoft Office-Dokument.  {#index-a-sample-policy-protected-pdf-or-microsoft-office-document}

1. Melden Sie sich bei AEM Assets als Administrator an.
1. Erstellen Sie einen Ordner in AEM Digital Asset Manager und laden Sie die durch Richtlinien geschützten PDF oder Microsoft Office-Dokumente in den neu erstellten Ordner hoch. Durchsuchen Sie nun die Inhalte der richtliniengeschützten Dokumente mit der AEM-Suche. Das Dokument muss zurückzugeben werden, das den gesuchten Text enthält, das Text enthält.
