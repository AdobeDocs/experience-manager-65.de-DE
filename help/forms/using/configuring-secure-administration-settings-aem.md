---
title: Konfigurieren sicherer Verwaltungseinstellungen für AEM Forms on JEE
seo-title: Konfigurieren sicherer Verwaltungseinstellungen für AEM Forms on JEE
description: Erfahren Sie, wie Sie Benutzerkonten und -dienste verwalten, die zwar in einer privaten Entwicklungs-Umgebung erforderlich sind, in einer Umgebung von AEM Forms on JEE jedoch nicht erforderlich sind.
seo-description: Erfahren Sie, wie Sie Benutzerkonten und -dienste verwalten, die zwar in einer privaten Entwicklungs-Umgebung erforderlich sind, in einer Umgebung von AEM Forms on JEE jedoch nicht erforderlich sind.
uuid: 04e45d06-f57d-406c-8228-15f483199430
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: d211d8b0-e75f-49c3-808d-5d0e26ad3a6b
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 80%

---


# Konfigurieren sicherer Verwaltungseinstellungen für AEM Forms on JEE {#configuring-secure-administration-settings-for-aem-forms-on-jee}

Erfahren Sie, wie Sie Benutzerkonten und -dienste verwalten, die zwar in einer privaten Entwicklungs-Umgebung erforderlich sind, in einer Umgebung von AEM Forms on JEE jedoch nicht erforderlich sind.

Im Allgemeinen verwenden Entwickler nicht die -Produktionsumgebung zum Erstellen und Testen ihrer Anwendungen. Sie müssen daher Benutzerkonten und -dienste verwalten, die, obwohl sie in einer privaten Entwicklungsumgebung benötigt werden, in einer Produktionsumgebung nicht erforderlich sind.

In diesem Abschnitt werden Methoden beschrieben, mit denen Sie durch Verwaltungsoptionen in AEM Forms on JEE die Angriffsmöglichkeiten verringern.

## Nicht erforderlichen Remote-Zugriff auf Dienste deaktivieren {#disabling-non-essential-remote-access-to-services}

Wenn AEM Forms on JEE installiert und konfiguriert ist, kann mithilfe von SOAP oder Enterprise JavaBeans™ (EJB) per Remote-Zugriff auf viele Dienste zugegriffen werden. Der Begriff Remote bezeichnet in diesem Fall alle Aufrufer mit Netzwerkzugriff auf die SOAP-, EJB- oder AMF-Anschlüsse (Action Message Format) für den Anwendungsserver.

AEM Forms on JEE-Dienste erfordern zwar, dass gültige Berechtigungen für einen autorisierten Aufrufer übergeben werden, dennoch sollten Sie den Remote-Zugriff nur für Dienste zulassen, für die der Remote-Zugriff erforderlich ist. Um die Verfügbarkeit einzuschränken, sollten Sie die Gruppe remote verfügbarer Dienste auf das Minimum für ein funktionierendes System begrenzen und dann den Remote-Aufruf für zusätzlich erforderliche Dienste aktivieren.

AEM Forms on JEE-Dienste benötigen zumindest SOAP-Zugriff. Diese Dienste sind meist für die Verwendung durch Workbench erforderlich; es sind jedoch auch Dienste darunter, die von der Workspace-Webanwendung aufgerufen werden.

Führen Sie dieses Verfahren mithilfe der Webseite &quot;Anwendungen und Dienste&quot;in Administration Console aus:

1. Melden Sie sich bei Administration Console an, indem Sie die folgende URL in einen Webbrowser eingeben:

   ```java
            https://[host name]:'port'/adminui
   ```

1. Klicken Sie auf **Dienste > Anwendungen und Dienste > Voreinstellungen**.
1. Legen Sie unter „Voreinstellungen“ fest, dass bis zu 200 Dienste und Endpunkte auf einer Seite angezeigt werden sollen.
1. Klicken Sie auf **Dienste** > **Anwendungen und Dienste** > **Endpunktverwaltung**.
1. Wählen Sie in der Liste **Anbieter** den Eintrag **EJB** aus und klicken Sie auf **Filter**.
1. Aktivieren Sie zum Deaktivieren aller EJB-Endpunkte das Kontrollkästchen neben allen Endpunkten in der Liste und klicken Sie auf **Deaktivieren**.
1. Klicken Sie auf **Weiter** und wiederholen Sie den vorhergehenden Schritt für alle EJB-Endpunkte. Stellen Sie vor dem Deaktivieren von Endpunkten sicher, dass EJB in der Spalte „Anbieter“ aufgeführt wird.
1. Wählen Sie in der Liste **Anbieter** den Eintrag **SOAP** aus und klicken Sie auf **Filter**.
1. Aktivieren Sie zum Entfernen von SOAP-Endpunkten das Kontrollkästchen neben allen Endpunkten in der Liste und klicken Sie auf **Entfernen**. Entfernen Sie folgende Endpunkte nicht:

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

1. Klicken Sie auf **Weiter** und wiederholen Sie den vorhergehenden Schritt für SOAP-Endpunkte, die nicht in der obigen Liste aufgeführt sind. Stellen Sie vor dem Entfernen von Endpunkten sicher, dass SOAP in der Spalte „Anbieter“ aufgeführt wird.

## Nicht erforderlichen anonymem Zugriff auf Dienste deaktivieren   {#disabling-non-essential-anonymous-access-to-services}

Einige Formularserverdienste lassen den nicht authentifizierten (anonymen) Aufruf bestimmter Vorgänge zu. Das heißt, ein oder mehrere vom Dienst offengelegte Vorgänge können von beliebigen authentifizierten Benutzern oder anonymen Benutzern aufgerufen werden.

1. Melden Sie sich bei Administration Console an, indem Sie die folgende URL in einen Webbrowser eingeben:

   ```java
            https://[host name]:'port'/adminui
   ```

1. Klicken Sie auf **Dienste > Anwendungen und Dienste > Dienstverwaltung**.
1. Klicken Sie auf den Namen des zu deaktivierenden Dienstes (z. B. AuthenticationManagerService).
1. Klicken Sie auf die Registerkarte **Sicherheit**, deaktivieren Sie **Anonymer Zugriff zulässig** und klicken Sie auf **Speichern**.
1. Wiederholen Sie die Schritte 3 und 4 für die folgenden Dienste:

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

   Wenn Sie vorhaben, alle oder einiger dieser Dienste für den Remote-Aufruf verfügbar zu machen, sollten Sie auch überlegen, ob Sie nicht den anonymen Zugriff für diese Dienste deaktivieren. Ansonsten kann jeder Aufrufer mit Netzwerkzugriff auf diesen Dienst den Dienst ohne Übergabe gültiger Berechtigungen aufrufen.

   Der anonyme Zugriff sollte für alle nicht erforderlichen Dienste deaktiviert werden. Für viele interne Dienste muss die anonyme Authentifizierung aktiviert sein, da sie möglicherweise von jedem beliebigen Benutzer im System ohne vorherige Authentifizierung aufgerufen werden müssen.

## Standardmäßiges globales Zeitlimit ändern {#changing-the-default-global-time-out}

Endbenutzer können sich über Workbench, AEM Forms-Webanwendungen oder benutzerdefinierte Anwendungen, die AEM Forms-Serverdienste aufrufen, bei AEM Forms authentifizieren. Mithilfe einer globalen Zeitlimiteinstellung wird festgelegt, wie lange solche Benutzer AEM Forms nutzen können (mittels einer auf SAML basierenden Bestätigung), bevor sie sich erneut authentifizieren müssen. Der Standardwert ist zwei Stunden. In einer Produktionsumgebung muss die Zeitdauer auf den zulässigen Mindestwert in Minuten verringert werden.

### Zeitlimit für die erneute Authentifizierung auf das Minimum einstellen  {#minimize-reauthentication-time-limit}

1. Melden Sie sich bei Administration Console an, indem Sie die folgende URL in einen Webbrowser eingeben:

   ```java
            https://[host name]:'port'/adminui
   ```

1. Klicken Sie auf **Einstellungen > User Management > Konfiguration > Konfigurationsdateien importieren und exportieren**.
1. Klicken Sie auf **Exportieren**, um eine „config.xml“-Datei mit den vorhandenen AEM Forms-Einstellungen zu erstellen.
1. Öffnen Sie die XML-Datei in einem Editor und suchen Sie folgenden Eintrag:

   `<entry key=”assertionValidityInMinutes” value=”120”/>`

1. Ändern Sie den Wert in eine Zahl größer gleich 5 (Minuten) und speichern Sie die Datei.
1. Wechseln Sie in Administration Console zur Seite „Konfigurationsdateien importieren und exportieren“.
1. Geben Sie den Pfad der geänderten „config.xml“-Datei ein oder klicken Sie auf „Durchsuchen“, um zu dieser Datei zu wechseln.
1. Klicken Sie auf **Importieren**, um die geänderte „config.xml“-Datei hochzuladen und klicken Sie dann auf **OK**.

