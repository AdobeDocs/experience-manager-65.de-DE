---
title: Einrichten von AEM Mobile
seo-title: Einrichten von AEM Mobile
description: Folgen Sie dieser Seite, um AEM Mobile einzurichten und dem Benutzer so zu ermöglichen, den Inhalt in AEM zu erstellen und zu verwalten. Auf dieser Seite finden Sie Informationen zur Integration der AEM-Instanz mit dem Cloud-basierten AEM Mobile-On-Demand-Dienste-Konto und -Projekt/en.
seo-description: Folgen Sie dieser Seite, um AEM Mobile einzurichten und dem Benutzer so zu ermöglichen, den Inhalt in AEM zu erstellen und zu verwalten. Auf dieser Seite finden Sie Informationen zur Integration der AEM-Instanz mit dem Cloud-basierten AEM Mobile-On-Demand-Dienste-Konto und -Projekt/en.
uuid: 03bf5b56-7750-4f76-b079-43761367655a
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-on-demand-services-app
discoiquuid: 393cf504-917e-4bf6-9a8b-b7a5bd862c65
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Einrichten von AEM Mobile{#aem-mobile-setup}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!CAUTION]
>
>Bestehende AEM Mobile-Apps-Kunden, die von AEM 6.2 oder 6.3 auf AEM 6.5 migrieren, können weiterhin AEM Mobile-Apps verwenden, indem sie ein [Paket von PackageShare](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/compatpack/aem-mobile-package)herunterladen. Neue Installationen von AEM 6.5 unterstützen jedoch keine AEM Mobile-Apps-Funktionen.

Damit Sie mit AEM Inhalte für AEM Mobile-Apps erstellen können, müssen Sie die AEM-Instanz in das Cloud-basierte AEM Mobile On-Demand Services-Konto und -Projekt/e integrieren.

Führen Sie die folgenden Schritte aus, um AEM Mobile einzurichten und dem Benutzer so das Erstellen und Verwalten der Inhalte in AEM zu ermöglichen.

## AEM Mobile-Bereitstellung {#aem-mobile-provisioning}

Für die ersten Schritte mit der AEM Mobile-Einrichtung müssen Sie:

* **API-Schlüssel** anfordern: Für den Zugriff auf die On-Demand Services API müssen Sie einen API-Schlüssel anfordern. Um den API-Schlüssel anzufordern, füllen Sie das [PDF-Formular](https://helpx.adobe.com/digital-publishing-solution/help/integrating-dps.html)aus. Senden Sie das ausgefüllte Formular an den Adobe Developer Support: [wwds@adobe.com](mailto:wwds@adobe.com)

* **Generieren Sie die Geräte-ID und das Gerätetoken**: Nachdem Sie Ihren API-Schlüssel erhalten haben, können Sie die Geräte-ID und das Gerätetoken generieren. Gehen Sie zu [https://aex.aemmobile.adobe.com](https://aex.aemmobile.adobe.com/) und führen Sie folgende Schritte aus:

   * API-Schlüssel bereitstellen
   * Melden Sie sich mit einer Adobe-ID an, die Sie einem AEM Mobile-Projekt hinzugefügt haben, mit folgenden Berechtigungen (siehe die folgenden Schritte zum Erstellen des Projekts)

      * Administration > Projekte und Benutzer verwalten
      * Inhalt > Inhalt hinzufügen und bearbeiten, Inhalt löschen, Inhalt anzeigen, Inhalt veröffentlichen

Wenn alle Bedingungen erfüllt sind, werden eine Geräte-ID und ein Gerätetoken generiert.

>[!NOTE]
>
>Die erforderliche Adobe-ID sollte auf ein AEM Mobile-Projekt zugreifen können. Siehe [Kontoverwaltung für AEM Mobile](https://helpx.adobe.com/digital-publishing-solution/help/account-admin-dps.html) in der Onlinehilfe.

## Erstellen von Projekten für AEM Mobile {#creating-projects-for-aem-mobile}

Beim Erstellen eines Projekts geben Sie Einstellungen für jede Plattform an, die Sie als Ziel auswählen: iOS, Android, Windows und Web Viewer für den Desktop. Viele der angegebenen Projekteinstellungen wirken sich auf das Verhalten der App aus.

Zum Erstellen eines Projekts müssen Sie sich beim On-Demand-Dienste-Portal mit einer Adobe ID anmelden, die über eine Hauptadministrator-Rolle verfügt. Zum Bearbeiten eines Projekts ist entweder eine Hauptadministratorrolle oder eine Benutzerrolle mit der Berechtigung &quot;Projekte und Benutzer **verwalten&quot;** erforderlich.

>[!NOTE]
>
>Weitere Informationen zum Erstellen von Projekten in AEM Mobile erhalten Sie [hier](https://helpx.adobe.com/digital-publishing-solution/help/creating-projects.html).

## AEM Mobile Connector konfigurieren {#configuring-an-aem-mobile-connector}

Die Einrichtung von AEM umfasst die folgenden Schritte für die Connector-Konfiguration. Sobald die AEM Mobile Connector-Konfiguration abgeschlossen ist, kann der Benutzer Benutzergruppen und Berechtigungen einrichten.

Der AEM Mobile On-Demand-Connector wird verwendet, um verwaltete AEM Mobile-Inhalte mit den On-Demand-Diensten von Adobe Experience Manager Mobile zu verbinden. Auf diese Weise können Autoren von Inhalten mit den Werkzeugen von AEM Mobile Material für mobile Anwendungen erstellen und verwalten und gleichzeitig die On-Demand-Dienste von AEM Mobile für die einfache Verteilung von mobilen Inhalten verwenden.

>[!NOTE]
>
>Dies ist ein einmaliger Schritt zum Einrichten der AEM-Instanz.

### AEM Mobile On-Demand Services Client konfigurieren {#configuring-aem-mobile-on-demand-services-client}

Sie müssen die Konfigurationsschritte ausführen, damit die AEM Mobile-Integrationen korrekt funktionieren.

1. Zu OSGI-Dienstkonfiguration wechseln

   1. AEM > Tools > Vorgänge > Web-Konsole
   1. Blättern Sie durch oder suchen Sie nach ***Experience Manager Mobile On-Demand Services Client (Adobe Digital Publishing Solution Client)***

1. Bearbeiten des On-Demand-Dienste-Clients für ***Experience Manager Mobile***

   1. **(Obligatorisch)** Geben Sie die erforderlichen Felder ein:

      1. Client-ID.
      1. Client-Geheimnis.
   1. **(Optional)** Bearbeiten Sie vorhandene Werte.


1. Speichern Sie die Änderungen.
1. Im Folgenden finden Sie eine Beispielkonfiguration:

![chlimage_1-53](assets/chlimage_1-53.png)

### Konfigurieren von AEM Mobile On-Demand Services CloudService {#configuring-aem-mobile-on-demand-services-cloudservice}

1. Zu Cloud-Diensten wechseln

   1. AEM > Tools > Bereitstellung > [CloudServices](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html). Blättern oder Suchen nach ***Adobe Experience Manager Mobile On-Demand-Diensten***

1. Wählen Sie &quot;Jetzt ***konfigurieren*** &quot;oder &quot;Konfigurationen ***anzeigen*** &quot;und klicken Sie auf das Symbol &quot;Neue Konfiguration hinzufügen&quot;

1. Neue Konfiguration erstellen

   1. Titel und Namen eingeben
   1. Geräte-ID eingeben
   1. Gerätetoken eingeben
   1. Wählen Sie ***Gerätekonfiguration*** testen, um die eingegebenen Werte zu überprüfen
   1. Ok auswählen

## Hinzufügen von AEM Mobile-Benutzerrollen und Zuweisen von Berechtigungen {#adding-aem-mobile-user-roles-and-assigning-permissions}

Nach dem Erstellen eines Projekts sollten Sie Rollen erstellen und Benutzern Zugriff gewähren. Nur Hauptadministratoren können Rollen erstellen und bearbeiten. Wenn Sie eine Rolle erstellen, aktivieren Sie die Funktionen (oder Berechtigungen) für die Benutzer, denen diese Berechtigungen zugewiesen wurden. Sie können beispielsweise eine Rolle mit Berechtigungen zum Erstellen von Apps und eine andere Rolle mit Berechtigungen zum Erstellen und Veröffentlichen von Inhalten erstellen.

Bei der Entwicklung von AEM Mobile-Apps gibt es drei verschiedene Rollen:

* Administrator


* Entwickler
* Autor

Weitere Informationen zum Erstellen von Rollen mit unterschiedlichen Berechtigungen, z. B. zum Erstellen von Apps oder zum Erstellen und Veröffentlichen von Inhalten, erhalten Sie, wenn Sie in der AEM Mobile-Hilfe auf &quot;Benutzerrollen [erstellen und Zugriff](https://helpx.adobe.com/digital-publishing-solution/help/account-admin-dps.html) gewähren&quot;klicken.

>[!NOTE]
>
>Die Verwaltung von App-Inhalten erfordert gemeinsame Anstrengungen von Entwicklern, Inhaltserstellern und Administratoren. Autoren bearbeiten Seiten, die wiederum auf Vorlagen und Komponenten basieren, die von App-Entwicklern generiert wurden. Schließlich veröffentlichen Administratoren den aktualisierten App-Inhalt strategisch. Durch das Einrichten von AEM-Gruppen und -Berechtigungen werden ihre Rollen im App-Dashboard oder im Control Center definiert.
>
>Weitere Informationen zum AEM Mobile Dashboard erhalten Sie [hier](/help/mobile/mobile-apps-ondemand-application-dashboard.md).

Sobald Sie mit der Erstellung von Rollen mit unterschiedlichen Berechtigungen wie zum Erstellen von Apps oder zum Erstellen und Veröffentlichen von Inhalten fertig sind, lesen Sie [**Konfigurieren Sie Ihre Benutzer- und Benutzergruppen **](/help/mobile/aem-mobile-configure-users.md), um Ihre Benutzer und Gruppen zur Unterstützung des Authoring und der Verwaltung Ihrer mobilen Apps zu konfigurieren.

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu den beiden anderen Rollen und Verantwortlichkeiten beim Erstellen einer AEM Mobile-On-Demand-Dienste-App finden Sie in den folgenden Ressourcen:

* [Entwickeln von AEM Content für AEM Mobile-On-Demand-Dienste](/help/mobile/aem-mobile-on-demand.md)
* [Authoring von AEM Content für AEM Mobile On-Demand Services-App](/help/mobile/mobile-apps-ondemand.md)

>[!NOTE]
>
>Informationen zum Anzeigen einer Vorschau der App-Inhalte, einschließlich Durchsuchen-Seiten und Artikel, finden Sie unter [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md).
