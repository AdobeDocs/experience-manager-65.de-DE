---
title: Konfigurieren der erweiterten Authentifizierung über den externen Browser für Document Security
description: Erfahren Sie, wie Sie die externe Browser-Authentifizierung konfigurieren, damit sich Benutzende für richtliniengeschützte PDF-Dokumente in Acrobat oder Reader mit dem standardmäßigen Webbrowser des Systems authentifizieren können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: a452674c-aea0-45d6-88cd-438af539d355
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: 89a07256cd5bb850aac19565ad86273322fa1f31
workflow-type: tm+mt
source-wordcount: '1029'
ht-degree: 4%

---

# Konfigurieren der erweiterten Authentifizierung über den externen Browser für Document Security {#configure-external-browser-authentication-document-security}

>[!NOTE]
>
> Stellen Sie sicher, dass Sie über Administratorrechte für den Zugriff auf die AEM Forms Administration Console verfügen.

Die erweiterte Authentifizierung über einen externen Browser ermöglicht es Benutzenden, sich für richtliniengeschützte PDF-Dokumente mit dem standardmäßigen Webbrowser des Systems (z. B. Microsoft Edge oder Google Chrome) anstatt mit dem eingebetteten Browsersteuerelement in Acrobat oder Reader zu authentifizieren. Dies ermöglicht moderne Authentifizierungsmethoden wie PassKey, biometrische Authentifizierung und andere Identitätsanbieter-Funktionen (IDP), für die ein moderner Browser erforderlich ist.

Wenn diese Option aktiviert ist, wird beim Öffnen eines richtliniengeschützten Dokuments in Acrobat oder Reader die IDP-Anmeldeseite im Standardbrowser des Benutzers gestartet. Nach der Authentifizierung wird der Benutzer automatisch zurück zu Acrobat oder Reader weitergeleitet und das Dokument entsperrt.

## Voraussetzungen {#prerequisites}

Stellen Sie vor der Konfiguration der externen Browser-Authentifizierung sicher, dass die folgenden Anforderungen erfüllt sind:

* AEM Forms 6.5 on JEE mit Service Pack 6.5.25.0 bereitgestellt oder Service Pack 6.5.24.0 mit dem entsprechenden JEE-Hotfix-Patch, der auf einem unterstützten Anwendungsserver (JBoss, WebLogic oder WebSphere) installiert ist. Siehe [Software-Verteilungslinks für AEM Forms JEE Hotfix2 6.5.24.0](#software-distribution-links).
* Die erweiterte Authentifizierung (Authentifizierung von Drittanbietern) ist bereits aktiviert und funktioniert mit einem IDP. Siehe [Serverkonfigurationseinstellungen](/help/forms/using/admin-help/configuring-client-server-options.md#server-configuration-settings) und [Erweiterten Authentifizierungsanbieter hinzufügen](/help/forms/using/admin-help/configuring-client-server-options.md#add-the-extended-authentication-provider).
* Adobe Acrobat Pro oder Adobe Acrobat Reader (64-Bit) mit dem neuesten Update auf dem Windows-Client installiert.

>[!NOTE]
>
> Für die externe Browser-Authentifizierung ist eine unterstützte Version von Adobe Acrobat oder Adobe Acrobat Reader auf dem Client erforderlich. Versionsdetails und -aktualisierungen finden Sie unter [Acrobat-Versionshinweise (Continuous Track vom März ](https://www.adobe.com/devnet-docs/acrobatetk/tools/ReleaseNotesDC/continuous/dccontinuousmarch2026.html#dccontinuousmarchtwentytwentysix)).

### Software-Verteilungslinks für AEM Forms JEE Hotfix2 6.5.24.0 {#software-distribution-links}

Die externe Browser-Authentifizierung ist in AEM Forms on JEE Service Pack 6.5.25.0 und höher verfügbar.

Wenn Sie AEM Forms on JEE Service Pack 6.5.24.0 oder früher verwenden, führen Sie einen der folgenden Schritte aus:

* Aktualisieren Sie auf [AEM Forms on JEE Service Pack 6.5.25.0](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.25.0.zip).
* Installieren Sie den AEM Forms JEE Hotfix 6.5.24.0 Patch für Ihren Anwendungsserver und Ihre Plattform mithilfe der unten stehenden Links.

Laden Sie den AEM Forms JEE Hotfix 6.5.24.0 Patch für Ihre Plattform von [Adobe Software Distribution herunter und installieren Sie ihn](https://experience.adobe.com/#/downloads/content/software-distribution/de/aem.html):

**JBoss**

* Windows: [Hotfix für AEM Service Pack 6.5.24.0 unter Windows für JBoss JEE-Server](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-24-0-hotfix-02/jboss/adobe-aem-forms-jee-hotfix2-6.5.24.0-win-jboss.zip)
* Linux: [Hotfix für AEM Service Pack 6.5.24.0 unter Linux für JBoss JEE-Server](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-24-0-hotfix-02/jboss/adobe-aem-forms-jee-hotfix2-6.5.24.0-linux-jboss.tar.gz)

**WebSphere**

* Windows: [Hotfix für AEM Service Pack 6.5.24.0 unter Windows für WebSphere JEE-Server](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-24-0-hotfix-02/websphere/adobe-aem-forms-jee-hotfix2-6.5.24.0-win-websphere.zip)
* Linux: [Hotfix für AEM Service Pack 6.5.24.0 unter Linux für WebSphere JEE-Server](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-24-0-hotfix-02/websphere/adobe-aem-forms-jee-hotfix2-6.5.24.0-linux-websphere.tar.gz)

**WebLogic**

* Windows: [Hotfix für AEM Service Pack 6.5.24.0 unter Windows für WebLogic JEE-Server](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-24-0-hotfix-02/weblogic/adobe-aem-forms-jee-hotfix2-6.5.24.0-win-weblogic.zip)
* Linux: [Hotfix für AEM Service Pack 6.5.24.0 unter Linux für WebLogic JEE-Server](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-24-0-hotfix-02/weblogic/adobe-aem-forms-jee-hotfix2-6.5.24.0-linux-weblogic.tar.gz)

Installationsanweisungen finden Sie unter [JEE-Patch installieren](/help/release-notes/jee-patch-installer-65.md).

## Externe Browser-Authentifizierung aktivieren {#enable-external-browser-authentication}

In diesem Video wird gezeigt, wie die externe Browser-Authentifizierung auf dem AEM Forms Document Security-Server aktiviert wird.

>[!VIDEO](https://video.tv.adobe.com/v/3492357/)

1. Klicken Sie in der Administration-Console auf **Services** > **Document Security** > **Configuration** > **Server Configuration**.
1. Suchen Sie den Abschnitt **Erweiterte Authentifizierung von einem externen Browser für Adobe-Client-Anwendungen zulassen**.
1. Aktivieren Sie das Kontrollkästchen für jede Adobe-Client-Plattform, die Sie aktivieren möchten:
   * **Adobe Acrobat und Reader (64 Bit) - Desktop**
   * **Adobe Acrobat Reader (32-Bit) - Desktop**
1. Klicken Sie auf **OK**.

Eine Beschreibung der Server-Einstellungen finden Sie unter [Server-Konfigurationseinstellungen](/help/forms/using/admin-help/configuring-client-server-options.md#server-configuration-settings).

<!--
## Client configuration (Acrobat / Reader) {#client-configuration}

External browser authentication is enabled by default in Acrobat and Reader. No client-side configuration is needed for most deployments. When the server is configured to allow external browser authentication, the client uses it automatically.

To disable external browser authentication on specific client machines (forcing the embedded browser fallback), set the following registry value:

`HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Adobe\Adobe Acrobat\<product_branch>\FeatureLockDown\EDC`

| Setting | Value |
| ------- | ----- |
| Value name | `TPExternalBrowserAuthAdmin` |
| Value type | `REG_DWORD` |
| Value data | `0` (to disable) |

>[!NOTE]
>
> Both the server-side setting and the client-side preference must be enabled for external browser authentication to work. If either is disabled, the client falls back to the embedded browser.
-->

## Überprüfung {#verification}

In diesem Video erfahren Sie, wie Sie die Authentifizierung eines externen Browsers überprüfen: Öffnen Sie eine richtliniengeschützte PDF in Acrobat, melden Sie sich über Ihren Standardbrowser an und bestätigen Sie, dass das Dokument nach der Authentifizierung entsperrt wird.

>[!VIDEO](https://video.tv.adobe.com/v/3492356/)

1. Erstellen Sie ein richtliniengeschütztes PDF-Dokument mithilfe des Document Security-Servers.
1. Öffnen Sie auf einem Windows-Client-Computer die geschützte PDF in Acrobat Pro oder Acrobat Reader.
1. In Acrobat wird ein Einverständnisdialogfeld angezeigt. Klicken Sie **Anmelden**.
1. Stellen Sie sicher, dass der Standard-Browser des Systems mit der IDP-Anmeldeseite geöffnet wird.
1. Vollständige Authentifizierung.
1. Stellen Sie sicher, dass das geschützte Dokument erfolgreich geöffnet wurde.

## Fehlerbehebung {#troubleshooting}

### Der eingebettete Browser wird anstelle des System-Browsers geöffnet {#embedded-browser-opens-instead-of-system-browser}

* Stellen Sie sicher, dass die Authentifizierung für den externen Browser auf dem Server aktiviert ist. Siehe [Aktivieren der externen Browser-Authentifizierung](#enable-external-browser-authentication).
* Vergewissern Sie sich, dass die Acrobat- oder Reader-Version diese Funktion unterstützt. Siehe [Acrobat](#acrobat).

### Die Authentifizierung im Browser ist erfolgreich, aber das Dokument wird nicht entsperrt {#authentication-succeeds-but-document-does-not-unlock}

* Stellen Sie sicher, dass Acrobat oder Reader ausgeführt wird und nicht durch eine Firewall oder Sicherheitssoftware blockiert wird.
* Wenn das Problem weiterhin besteht, installieren oder reparieren Sie die Acrobat- oder Reader-Installation neu, um die Registrierung des Protokoll-Handlers wiederherzustellen.

### Die Nachricht „Wir konnten Sie nicht anmelden“ wird in Acrobat angezeigt {#we-couldnt-sign-you-in-message}

* Möglicherweise hat der Benutzer zu lange gebraucht, um die Authentifizierung abzuschließen. Erneut versuchen.
* Überprüfen Sie die Netzwerkverbindung zwischen dem Browser und dem AEM Forms-Server.

### Die Authentifizierungsoption wird nicht auf der Anmeldeseite angezeigt {#authentication-option-does-not-appear}

* Authentifizierungsmethoden und -optionen werden vom IDP und nicht von AEM Forms oder Acrobat konfiguriert. Stellen Sie sicher, dass der IDP die Authentifizierungsmethode unterstützt, die Sie verwenden möchten.
* Überprüfen Sie, ob die Anmeldeseite im System-Browser (nicht im eingebetteten Browser) geladen wird.
