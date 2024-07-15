---
title: Konfigurieren sicherer Verwaltungseinstellungen für AEM Forms on JEE
description: Erfahren Sie, wie Sie Benutzerkonten und Services verwalten, die zwar in einer privaten Entwicklungsumgebung erforderlich sind, aber in einer Produktionsumgebung von AEM Forms on JEE nicht benötigt werden.
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
role: Admin,User
exl-id: 40bc01b4-a59e-4420-81d6-2887857bddce
solution: Experience Manager, Experience Manager Forms
feature: Document Security,Adaptive Forms
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 100%

---

# Konfigurieren sicherer Verwaltungseinstellungen für AEM Forms on JEE {#configuring-secure-administration-settings-for-aem-forms-on-jee}

Erfahren Sie, wie Sie Benutzerkonten und Services verwalten, die zwar in einer privaten Entwicklungsumgebung erforderlich sind, aber in einer Produktionsumgebung von AEM Forms on JEE nicht benötigt werden.

Im Allgemeinen verwenden Entwickelnde die Produktionsumgebung nicht zum Erstellen und Testen ihrer Anwendungen. Daher müssen Sie Benutzerkonten und Dienste verwalten, die, obwohl sie in einer privaten Entwicklungsumgebung erforderlich sind, in einer Produktionsumgebung nicht nötig sind.

In diesem Artikel werden Methoden beschrieben, mit denen Sie die Gesamtangriffsfläche durch Verwaltungsoptionen reduzieren können, die AEM Forms auf JEE bereitstellt.

## Deaktivieren eines nicht erforderlichen Remote-Zugriffs auf Dienste {#disabling-non-essential-remote-access-to-services}

Nachdem AEM Forms auf JEE installiert und konfiguriert wurde, stehen viele Dienste für den Remote-Aufruf über SOAP und Enterprise JavaBeans™ (EJB) zur Verfügung. Der Begriff „Remote“ bezieht sich in diesem Fall auf alle Aufrufenden mit Netzwerkzugriff auf die SOAP-, EJB- oder Action Message Format(AMF)-Anschlüsse für den Anwendungs-Server.

AEM Forms on JEE-Dienste erfordern zwar, dass gültige Berechtigungen für einen autorisierten Aufrufer übergeben werden, dennoch sollten Sie den Remote-Zugriff nur für Dienste zulassen, für die der Remote-Zugriff erforderlich ist. Um eingeschränkte Barrierefreiheit zu erreichen, sollten Sie den Satz von Diensten mit Remote-Zugriff auf das für ein funktionierendes System mögliche Minimum reduzieren und dann den Remote-Aufruf für die zusätzlichen Dienste aktivieren, die Sie benötigen.

AEM Forms auf JEE-Dienste benötigen immer mindestens SOAP-Zugriff. Diese Dienste sind normalerweise für die Verwendung durch Workbench erforderlich, umfassen aber auch Dienste, die von der Workspace-Web-Anwendung aufgerufen werden.

Führen Sie dieses Verfahren mithilfe der Web-Seite „Programme und Services“ in Administration-Console durch:

1. Melden Sie sich bei Administration-Console an, indem Sie die folgende URL in einen Webbrowser eingeben:

   ```java
            https://[host name]:'port'/adminui
   ```

1. Klicken Sie auf **Dienste > Anwendungen und Dienste > Voreinstellungen**.
1. Legen Sie die Voreinstellungen fest, um bis zu 200 Dienste und Endpunkte auf derselben Seite anzuzeigen.
1. Klicken Sie auf **Dienste** > **Anwendungen und Dienste** > **Endpunktverwaltung**.
1. Wählen Sie **EJB** aus der Liste der **Anbieter** aus und klicken Sie auf **Filtern**.
1. Um alle EJB-Endpunkte zu deaktivieren, wählen Sie das Kontrollkästchen neben jedem Endpunkt in der Liste aus und klicken Sie auf **Deaktivieren**.
1. Klicken Sie auf **Weiter** und wiederholen Sie den vorherigen Schritt für alle EJB-Endpunkte. Stellen Sie sicher, dass EJB in der Anbieterspalte aufgeführt ist, bevor Sie Endpunkte deaktivieren.
1. Wählen Sie **SOAP** aus der Liste der **Anbieter** aus und klicken Sie auf **Filtern**.
1. Um SOAP-Endpunkte zu entfernen, wählen Sie das Kontrollkästchen neben jedem Endpunkt in der Liste aus und klicken Sie auf **Entfernen**. Entfernen Sie nicht die folgenden Endpunkte:

   * AuthenticationManagerService
   * DirectoryManagerService
   * JobManager
   * event_management_service
   * event_configuration_service
   * ProcessManager
   * TemplateManager
   * RepositoryService
   * TaskManagerService
   * TaskQueueManager
   * TaskManagerQueryService
   * WorkspaceSingleSignOn
   * ApplicationManager

1. Klicken Sie auf **Weiter** und wiederholen Sie den vorherigen Schritt für SOAP-Endpunkte, die nicht in der obigen Liste enthalten sind. Stellen Sie sicher, dass SOAP in der Anbieterspalte aufgeführt ist, bevor Sie Endpunkte entfernen.

## Deaktivieren eines nicht erforderlichen anonymen Zugriffs auf Dienste {#disabling-non-essential-anonymous-access-to-services}

Einige Formular-Server-Dienste lassen einen nicht authentifizierten (anonymen) Aufruf für einige Vorgänge zu. Dies bedeutet, dass ein oder mehrere vom Dienst offengelegte Vorgänge als beliebige authentifizierte Benutzende oder als überhaupt keine authentifizierten Benutzenden aufgerufen werden können.

1. Melden Sie sich bei der Administrationskonsole an, indem Sie die folgende URL in einen Webbrowser eingeben:

   ```java
            https://[host name]:'port'/adminui
   ```

1. Klicken Sie auf **Dienste > Anwendungen und Dienste > Dienstverwaltung**.
1. Klicken Sie auf den Namen des Dienstes, den Sie deaktivieren möchten (zum Beispiel AuthenticationManagerService).
1. Klicken Sie auf die **Registerkarte Sicherheit**, deaktivieren Sie **Anonymen Zugriff zulassen**, und klicken Sie dann auf **Speichern**.
1. Erledigen Sie die Schritte 3 und 4 für die folgenden Dienste:

   * AuthenticationManagerService
   * EJB
   * E-Mail
   * JobManager
   * WatchedFolder
   * UsermanagerUtilService
   * Remoting
   * RepositoryProviderService
   * EMCDocumentumRepositoryProvider
   * IBMFilenetRepositoryProvider
   * FormAugmenter
   * TaskManagerService
   * TaskManagerConnector
   * TaskManagerQueryService
   * TaskQueueManager
   * TaskEndpointManager
   * UserService
   * WorkspaceSearchTemplateService
   * WorkspacePropertyService
   * OutputService
   * FormsService

   Wenn Sie vorhaben, alle oder einiger dieser Dienste für den Remote-Aufruf verfügbar zu machen, sollten Sie auch überlegen, ob Sie nicht den anonymen Zugriff für diese Dienste deaktivieren. Anderenfalls können alle Aufrufenden mit Netzwerkzugriff auf diesen Dienst den Dienst aufrufen, ohne gültige Anmeldeinformationen einzugeben.

   Der anonyme Zugriff sollte für alle nicht erforderlichen Dienste deaktiviert werden. Für viele interne Dienste muss die anonyme Authentifizierung aktiviert sein, da sie von potenziell allen Benutzenden ohne eine Vorautorisierung im System aufgerufen werden müssen.

## Standardmäßiges globales Zeitlimit ändern  {#changing-the-default-global-time-out}

Endbenutzer von AEM Forms können sich über Workbench, Web-Anwendungen für AEM Forms oder über benutzerdefinierte Anwendungen, die Server-Services für AEM Forms aufrufen, authentifizieren. Mithilfe einer globalen Zeitlimiteinstellung wird festgelegt, wie lange solche Benutzer AEM Forms nutzen können (mittels einer auf SAML basierenden Bestätigung), bevor sie sich erneut authentifizieren müssen. Der Standardwert ist zwei Stunden. In einer Produktionsumgebung muss die Zeitdauer auf die akzeptable Mindestanzahl von Minuten reduziert werden.

### Minimieren des Zeitlimits für die erneute Authentifizierung {#minimize-reauthentication-time-limit}

1. Melden Sie sich bei der Administrationskonsole an, indem Sie die folgende URL in einen Webbrowser eingeben:

   ```java
            https://[host name]:'port'/adminui
   ```

1. Klicken Sie auf **Einstellungen > Benutzerverwaltung > Konfiguration > Konfigurationsdateien importieren und exportieren**.
1. Klicken Sie auf **Exportieren**, um eine Datei config.xml mit den vorhandenen AEM Forms-Einstellungen zu erstellen.
1. Öffnen Sie die XML-Datei in einem Editor und suchen Sie den folgenden Eintrag: 

   `<entry key="assertionValidityInMinutes" value="120"/>`

1. Ändern Sie den Wert in eine Zahl größer als 5 (in Minuten) und speichern Sie die Datei.
1. Navigieren Sie in der Administrationskonsole zur Seite „Konfigurationsdateien importieren und exportieren“.
1. Geben Sie den Pfad zur geänderten config.xml-Datei ein oder klicken Sie auf „Durchsuchen“, um zu dieser Datei zu navigieren.
1. Klicken Sie auf **Importieren**, um die geänderte config.xml-Datei hochzuladen, und klicken Sie dann auf **OK**.
