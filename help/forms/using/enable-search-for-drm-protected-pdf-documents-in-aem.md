---
title: Aktivieren von AEM zum Durchsuchen von durch Dokumentensicherheit geschützten PDF-Dokumenten
description: Erfahren Sie, wie Sie die native AEM-Suche aktivieren, um eine Volltextsuche in DRM-geschützten PDF-Dokumenten durchzuführen.
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
geptopics: SG_AEMFORMS/categories/working_with_document_security
docset: aem65
feature: Document Security
exl-id: 7cf17fb6-021a-473e-bc3b-27c317953002
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 100%

---

# AEM zum Durchsuchen von durch Document Security geschützten PDF-Dokumenten aktivieren{#enable-aem-to-search-document-security-protected-pdf-documents}

Mithilfe der AEM-Suche kann nach AEM-Assets gesucht werden. Zudem kann eine Textsuche für verschiedene häufig verwendete Dokumentformate wie einfache Textdateien, Microsoft Office-Dokumente und PDF-Dokumente durchgeführt werden. Sie können die native Suche erweitern, um eine Volltextsuche in [mit der AEM-Dokumentensicherheit geschützten PDF-Dokumenten](../../forms/using/admin-help/document-security.md) durchzuführen. Damit AEM die Volltextsuche in solchen Dokumenten durchführen kann, führen Sie die folgenden Schritte aus:

1. Stellen Sie eine sichere Verbindung her.
1. Indizieren Sie ein richtliniengeschütztes PDF-Beispieldokument.

## Voraussetzungen {#prerequisites}

* Wenn Sie AEM Forms on OSGi verwenden: 

   * Installieren Sie[ AEM Forms-Dokumentensicherheit ](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html)auf dem AEM Forms-Server.

   * Stellen Sie sicher, dass ein AEM Forms auf dem JEE-Server läuft und die Dokumentensicherheit auf den entsprechenden AEM Forms auf dem JEE-Server installiert ist. Der AEM Forms on JEE-Server ist erforderlich, um das geschützte Dokument mit einem Index zu versehen. 

* Wenn Sie nur den AEM Forms on JEE-Server verwenden, ist das Indexpaket bereits installiert. 
* Stellen Sie sicher, dass alle Pakete aktiv sind. Wenn nicht alle Pakete aktiv sind, warten Sie, bis alle Pakete aktiv sind. 

   * Für AEM Forms unter OSGi werden die Bundles unter https://&#39;[server]:[port]&#39;/system/console/bundles aufgelistet.
   * Für AEM Forms auf JEE werden die Bundles unter https://&#39;[server]:[port]&#39;/[context-path]/system/console/bundles aufgelistet. Zum Beispiel „https://localhost:8080/lc/system/console/bundles“.

* Fügen Sie das Paket *sun.util.calendar* zur Zulassungsliste hinzu. Um das Paket zur Zulassungsliste hinzuzufügen, führen Sie die folgenden Schritte aus:

   1. Öffnen Sie die AEM Web-Konsole. Die URL lautet https://&#39;[server]:[port]&#39;/system/console/configMgr.
   1. Suchen und öffnen Sie **Deserialisierungs-Firewallkonfiguration**. 

   1. Fügen Sie das Paket sun.util.calendar zum Feld der auf die Zulassungsliste gesetzten Klassen oder Paketpräfixe hinzu und klicken Sie auf **Speichern**.

### Herstellen einer sicheren Verbindung zwischen AEM Forms JEE- und OSGi-Stapeln {#establish-a-secure-connection-between-aem-forms-jee-and-osgi-stacks}

Sie können eine der folgenden Methoden verwenden, um die sichere Verbindung herzustellen:

* Konfigurieren des Adobe LiveCycle Client SDK-Bundles mit AEM Forms auf JEE-Administratorberechtigungen
* Konfigurieren von Adobe LiveCycle Client SDK Bundle mit gegenseitiger Authentifizierung

#### Konfigurieren des Adobe LiveCycle Client SDK-Bundles mit AEM Forms auf JEE-Administratorberechtigungen {#configure-adobe-livecycle-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Öffnen Sie die AEM Web-Konsole. Die URL lautet https://&#39;[server]:[port]&#39;/system/console/configMgr.
1. Suchen Sie das **Adobe LiveCycle Client SDK-Bundle** und öffnen Sie es. Geben Sie Werte für die folgenden Felder an:

   * **Server-URL:** Geben Sie die HTTPS-URL des AEM Forms on JEE-Servers an. Um die Kommunikation über HTTPS zu aktivieren, starten Sie den AEM-Server mit dem Parameter -Djavax.net.ssl.trustStore=&lt;Pfad der AEM Forms on JEE-Keystore-Datei> neu.
   * **Dienstname**: Fügen Sie den RightsManagementService zur Liste der angegebenen Dienste hinzu.
   * **Benutzername:** Geben Sie den Benutzernamen des AEM Forms on JEE-Konto an, der verwendet werden soll, um Aufrufe von AEM-Server zu initiieren. Das angegebene Konto benötigt Berechtigungen zum Starten der Dokumentendienste auf dem AEM Forms auf JEE-Server.
   * **Kennwort**: Geben Sie das Kennwort für das AEM Forms on JEE-Konto an, das im Feld für den Benutzernamen angegeben ist.

   Klicken Sie auf **Speichern**. AEM ist jetzt aktiviert, um PDF-Dokumente durchsuchen zu können, die durch die Dokumentensichereit geschützt sind.

#### Konfigurieren von Adobe LiveCycle Client SDK Bundle mit gegenseitiger Authentifizierung {#configure-adobe-livecycle-client-sdk-bundle-using-mutual-authentication}

1. Aktivieren Sie die gegenseitige Authentifizierung für AEM Forms auf JEE.  Weitere Informationen finden Sie unter [CAC und gegenseitige Authentifizierung](https://helpx.adobe.com/de/livecycle/kb/cac-mutual-authentication.html).
1. Öffnen Sie die AEM Web-Konsole. Die URL lautet https://&#39;[server]:[port]&#39;/system/console/configMgr.
1. Suchen Sie das **Adobe LiveCycle Client SDK**-Bundle und öffnen Sie es. Geben Sie Werte für die folgenden Eigenschaften an:

   * **Server-URL:** Geben Sie die HTTPS-URL des AEM Forms on JEE-Servers an. Um die Kommunikation über HTTPS zu aktivieren, starten Sie den AEM-Server mit dem Parameter „-Djavax.net.ssl.trustStore=&lt;Pfad der AEM Forms auf JEE-Keystore-Datei>“ neu.
   * **2-Weg-SSL aktivieren**: Aktiviert die Option für 2-Weg-SSL.
   * **KeyStore-Datei-URL**: Geben Sie die URL der KeyStore-Datei an.
   * **TrustStore-Datei-URL**: Geben Sie die URL für die TrustStore-Datei an.
   * **KeyStore-Kennwort**: Geben Sie das Kennwort für die KeyStore-Datei an.
   * **TrustStorePassword**: Geben Sie das Kennwort für die TrustStore-Datei an.
   * **Dienstname**: Fügt den RightsManagementService zur Liste der angegebenen Dienste hinzu.

   Klicken Sie auf **Speichern**. AEM ist jetzt aktiviert, um PDF-Dokumente durchsuchen zu können, die durch die Dokumentensichereit geschützt sind.

### Indizieren Sie ein richtliniengeschütztes PDF-Beispieldokument. {#index-a-sample-policy-protected-pdf-document}

1. Melden Sie sich bei AEM Assets als Administrator an.
1. Erstellen Sie einen Ordner in AEM Digital Asset Manager und laden Sie die durch Richtlinien geschützten PDF-Dokumente in den neu erstellten Ordner hoch.

   Jetzt können Sie durch Richtlinien geschützte Dokumente mit der AEM-Suche durchsuchen.

   >[!NOTE]
   >
   > Es wird empfohlen, den Tastaturbefehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.
