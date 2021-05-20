---
title: Installieren und Konfigurieren des Document Security-Servers
seo-title: Installieren und Konfigurieren des Document Security-Servers
description: 'Verwenden Sie Document Security, um alle Informationen, die Sie in einem unterstützten Format gespeichert haben, sicher zu verteilen. Nur autorisierte Benutzer können auf geschützte Dokumente zugreifen. '
seo-description: 'Verwenden Sie Document Security, um alle Informationen, die Sie in einem unterstützten Format gespeichert haben, sicher zu verteilen. Nur autorisierte Benutzer können auf geschützte Dokumente zugreifen. '
uuid: 04c67a84-01ad-45b7-a590-822b1c067d52
contentOwner: khsingh
discoiquuid: 600d13e7-6655-41c5-aab4-c8e9e2a8d14f
role: Administrator
exl-id: 4a4bad4a-3e68-43cb-b55c-03b509a5d304
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 42%

---

# Installieren und Konfigurieren des Document Security-Servers {#installing-and-configuring-the-document-security-server}

Verwenden Sie Document Security, um alle Informationen, die Sie in einem unterstützten Format gespeichert haben, sicher zu verteilen. Nur autorisierte Benutzer können auf geschützte Dokumente zugreifen.

Document Security stellt sicher, dass Ihre Dokumente nur von autorisierten Benutzern genutzt werden können. Mithilfe von Document Security können Sie Informationen sicher verteilen, die Sie in einem unterstützten Format gespeichert haben. Unterstützte Dateiformate beinhalten Adobe Portable Document Format (PDF) sowie Microsoft Word-, Excel- und PowerPoint-Dateien.

Sie können Dokumente durch Richtlinien schützen. Die Vertraulichkeitseinstellungen, die Sie in einer Richtlinie angeben, bestimmen, wie ein Empfänger ein Dokument nutzen darf, auf das Sie die Richtlinie anwenden. Sie können beispielsweise angeben, ob Empfänger Folgendes dürfen: Text drucken, kopieren oder bearbeiten, geschützten Dokumenten Signaturen und Kommentare hinzufügen.

Die Richtlinien werden zwar auf dem Document Security-Server gespeichert, Sie wenden sie jedoch über Ihre Client-Anwendung auf Dokumente an. Wenn Sie eine Richtlinie auf ein Dokument anwenden, werden die in der Datei enthaltenen Informationen durch die in der Richtlinie angegebenen Vertraulichkeitseinstellungen geschützt. Sie können das richtliniengeschützte Dokument an Empfänger verteilen, die durch die Richtlinie autorisiert sind.

Document Security bietet außerdem Clients, Viewer und Indexer zum Schützen von Dokumenten, zum Anzeigen geschützter Dokumente und zum Indexieren geschützter Dokumente. Ausführliche Informationen zu Document Security finden Sie unter [Informationen zu Document Security](/help/forms/using/admin-help/document-security.md).

## Bereitstellungstopologie  {#deployment-topology}

Die Document Security-Funktion ist nur in AEM Forms on JEE verfügbar. Sie benötigen nur eine Instanz von AEM Forms on JEE. Sie können bei Bedarf auch einen Cluster oder eine Farm von AEM Forms-Servern erstellen. Die folgende Topologie ist eine indikative Topologie zum Ausführen der Document Security-Funktion. Detaillierte Informationen zu Topologien finden Sie unter [Architektur und Bereitstellungstopologien für AEM Forms](aem-forms-architecture-deployment.md).

<!--fix above link-->

![](do-not-localize/document-security-server_topology.png)

Die folgende Abbildung zeigt die typische Architektur für AEM Forms Document Security:

![](do-not-localize/document-security-typical-environment.png)

## Installieren von AEM Forms on JEE {#installing-aem-forms-on-jee}

Führen Sie die folgenden Schritte aus, um AEM Forms on JEE zu installieren und zu konfigurieren:

1. Laden Sie das Installationsprogramm für AEM 6.5 Forms on JEE von der [Adobe Licensing-Website (LWS)](https://licensing.adobe.com/) herunter. Sie benötigen einen gültigen Vertrag für Wartung und Support, um das Installationsprogramm herunterzuladen.
1. Lesen Sie das Dokument [Unterstützte Plattformen für AEM Forms on JEE](/help/forms/using/aem-forms-jee-supported-platforms.md) und stellen Sie sicher, dass die Software, Hardware, Betriebssysteme, Anwendungsserver, Datenbanken, JDKs und andere Infrastruktur für die Installation von AEM Forms on JEE bereit sind.
1. (Nur Nicht-Turnkey-Installationen) Lesen Sie den Abschnitt [Vorbereiten der Installation von AEM Forms-Einzelserver](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_64) oder [Vorbereiten der Installation des AEM Forms-Serverclusters](https://www.adobe.com/go/learn_aemforms_prepareInstallcluster_64) und bereiten Sie Ihre Umgebung für die Installation und Konfiguration von AEM Forms on JEE vor.
1. Wählen Sie je nach Umgebung und Anwendungsserver eines der folgenden Dokumente aus und befolgen Sie die Anweisungen, um die Installation abzuschließen.

   * [Installieren und Bereitstellen von AEM Forms on JEE mithilfe von JBoss Turnkey](https://www.adobe.com/go/learn_aemforms_installTurnkey_64)
   * [Installieren und Bereitstellen von AEM Forms on JEE für JBoss](https://www.adobe.com/go/learn_aemforms_installJBoss_64)
   * [Installieren und Bereitstellen von AEM Forms on JEE für WebLogic](https://www.adobe.com/go/learn_aemforms_installWebLogic_64)
   * [Installieren und Bereitstellen von AEM Forms on JEE für WebSphere](https://www.adobe.com/go/learn_aemforms_installWebSphere_64)
   * [Konfigurieren von AEM Forms on JEE auf einem JBoss-Cluster](https://www.adobe.com/go/learn_aemforms_clusterJBoss_64)
   * [Das Konfigurieren von AEM Forms on JEE auf einem WebLogic-Cluster](https://www.adobe.com/go/learn_aemforms_clusterWebLogic_64)
   * [Konfigurieren von AEM Forms unter JEE auf einem WebSphere-Cluster](https://www.adobe.com/go/learn_aemforms_clusterWebSphere_64)

   >[!NOTE]
   >
   >Wählen Sie im Bildschirm &quot;Modulauswahl&quot;des AEM Forms on JEE Configuration Manager die Option Document Security aus. Für die Option Document Security müssen keine anderen Module ausgewählt werden.

## Nächste Schritte {#next-steps}

* [Client- und Server-Optionen konfigurieren](/help/forms/using/admin-help/configuring-client-server-options.md)
* [Richtlinien erstellen und verwalten](/help/forms/using/admin-help/creating-policies.md)
* [Richtliniensätze erstellen und verwalten](/help/forms/using/admin-help/creating-policy-sets.md)
