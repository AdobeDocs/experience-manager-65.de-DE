---
title: Installieren und Konfigurieren des Servers für Dokumentensicherheit
seo-title: Installing and configuring the document security server
description: Mithilfe von Dokumentensicherheit können Sie Informationen sicher verteilen, die Sie in einem unterstützten Format gespeichert haben. Nur autorisierte Benutzer können auf geschützte Dokumente zugreifen.
seo-description: Use document security to safely distribute any information that you have saved in a supported format. Only authorized users can access protected documents.
uuid: 04c67a84-01ad-45b7-a590-822b1c067d52
contentOwner: khsingh
discoiquuid: 600d13e7-6655-41c5-aab4-c8e9e2a8d14f
role: Admin
exl-id: 4a4bad4a-3e68-43cb-b55c-03b509a5d304
source-git-commit: e9f64722ba7df0a7f43aaf1005161483e04142f5
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 87%

---

# Installieren und Konfigurieren des Servers für Dokumentensicherheit {#installing-and-configuring-the-document-security-server}

Mithilfe von Dokumentensicherheit können Sie Informationen sicher verteilen, die Sie in einem unterstützten Format gespeichert haben. Nur autorisierte Benutzer können auf geschützte Dokumente zugreifen.

Adobe Experience Manager Forms Document Security stellt sicher, dass nur autorisierte Benutzer Ihre Dokumente verwenden können. Mithilfe von Document Security können Sie Informationen, die Sie in einem unterstützten Format gespeichert haben, sicher verteilen. Zu den unterstützten Dateiformaten gehören Adobe Portable Document Format (PDF) sowie Microsoft Word-, Excel- und PowerPoint-Dateien.

Sie können Dokumente mithilfe von Richtlinien schützen. Die Vertraulichkeitseinstellungen, die Sie in einer Richtlinie angeben, bestimmen, wie ein Empfänger ein Dokument verwenden kann, auf das Sie die Richtlinie anwenden. Sie können beispielsweise angeben, ob Empfängerinnen und Empfänger Text drucken oder kopieren, Text bearbeiten oder geschützten Dokumenten Signaturen und Kommentare hinzufügen können.

Die Richtlinien werden auf dem Document Security-Server gespeichert. Sie wenden die Richtlinien über Ihre Clientanwendung auf Dokumente an. Wenn Sie eine Richtlinie auf ein Dokument anwenden, schützen die in der Richtlinie angegebenen Vertraulichkeitseinstellungen die Informationen, die das Dokument enthält. Sie können das richtliniengeschützte Dokument an Empfängerinnen und Empfänger verteilen, die durch die Richtlinie autorisiert sind.

Dokumentensicherheit bietet außerdem Clients, Viewer und Indexer zum Schützen von Dokumenten, zum Anzeigen geschützter Dokumente und zum Indizieren geschützter Dokumente. Ausführliche Informationen zu Dokumentensicherheit finden Sie unter [Über Dokumentensicherheit](/help/forms/using/admin-help/document-security.md).

## Bereitstellungstopologie  {#deployment-topology}

Die Funktion Dokumentensicherheit ist nur in AEM Forms auf JEE verfügbar. Sie benötigen auf JEE nur eine Instanz von AEM Forms. Sie können bei Bedarf auch einen Cluster oder eine Farm von AEM Forms-Servern erstellen. Die folgende Topologie ist eine indikative Topologie zum Ausführen der Dokumentensicherheit. Detaillierte Informationen zu Topologien finden Sie unter [Architektur und Bereitstellungstopologien für AEM Forms](aem-forms-architecture-deployment.md).

<!--fix above link-->

![Document Security-Servertopologie](do-not-localize/document-security-server_topology.png)

Die folgende Abbildung zeigt die typische Architektur für AEM Forms Document Security:

![](do-not-localize/document-security-typical-environment.png)

## Installieren von AEM Forms auf JEE {#installing-aem-forms-on-jee}

Führen Sie die folgenden Schritte aus, um AEM Forms auf JEE zu installieren und zu konfigurieren:

1. Laden Sie das Installationsprogramm für AEM 6.5 Forms on JEE von der [Adobe Licensing-Website (LWS)](https://licensing.adobe.com/) herunter. Sie benötigen einen gültigen Vertrag für Wartung und Support, um das Installationsprogramm herunterzuladen.
1. Lesen Sie das Dokument [Von AEM Forms auf JEE unterstützte Plattformen](/help/forms/using/aem-forms-jee-supported-platforms.md) und stellen Sie sicher, dass die Software, Hardware, Betriebssysteme, Programm-Server, Datenbanken, JDKs und andere Infrastrukturelemente für die Installation von AEM Forms auf JEE bereit sind.
1. (Nur Nicht-Turnkey-Installationen) Lesen Sie [Vorbereiten der Einzel-Server-Installation von AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_64_de) oder [Vorbereiten der Installation des Server-Clusters für AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareInstallcluster_64_de) und richten Sie Ihre Umgebung für die Installation und Konfiguration von AEM Forms auf JEE ein.
1. Wählen Sie je nach vorhandener Umgebung und Programm-Server eines der folgenden Dokumente und befolgen Sie die Anweisungen, um die Installation abzuschließen

   * [Installieren und Bereitstellen von AEM Forms on JEE mithilfe von JBoss Turnkey](https://www.adobe.com/go/learn_aemforms_installTurnkey_64_de)
   * [Installieren und Bereitstellen von AEM Forms on JEE für JBoss](https://www.adobe.com/go/learn_aemforms_installJBoss_64_de)
   * [Installieren und Bereitstellen von AEM Forms on JEE für WebLogic](https://www.adobe.com/go/learn_aemforms_installWebLogic_64_de)
   * [Installieren und Bereitstellen von AEM Forms on JEE für WebSphere](https://www.adobe.com/go/learn_aemforms_installWebSphere_64_de)
   * [Konfigurieren von AEM Forms on JEE auf einem JBoss-Cluster](https://www.adobe.com/go/learn_aemforms_clusterJBoss_64_de)
   * [Das Konfigurieren von AEM Forms on JEE auf einem WebLogic-Cluster](https://www.adobe.com/go/learn_aemforms_clusterWebLogic_64_de)
   * [Konfigurieren von AEM Forms unter JEE auf einem WebSphere-Cluster](https://www.adobe.com/go/learn_aemforms_clusterWebSphere_64_de)

   >[!NOTE]
   >
   >Wählen Sie im Bildschirm „Modulauswahl“ des Konfigurations-Managers für AEM Forms auf JEE die Option „Dokumentensicherheit“ aus. Für die Option „Dokumentensicherheit“ müssen keine anderen Module ausgewählt werden.

## Nächste Schritte {#next-steps}

* [Client- und Server-Optionen konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md)
* [Richtlinien erstellen und verwalten](/help/forms/using/admin-help/creating-policies.md)
* [Richtliniensätze erstellen und verwalten](/help/forms/using/admin-help/creating-policy-sets.md)
