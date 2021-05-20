---
title: Fehlerbehebung der AEM Forms-App
seo-title: Fehlerbehebung der AEM Forms-App
description: Erfahren Sie mehr über die häufigsten Probleme mit AEM Forms-App und wie die Fehlerbehebung für diese Probleme durchgeführt wird.
seo-description: Erfahren Sie mehr über die häufigsten Probleme mit AEM Forms-App und wie die Fehlerbehebung für diese Probleme durchgeführt wird.
uuid: a5cc3065-0ebf-48c0-a8fe-f1061632ca90
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 2f45a965-590b-43b1-95c6-df4b74ad15b9
exl-id: caec5fc3-db52-4bf5-8eb2-17e5189ab819
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 62%

---

# Fehlerbehebung der AEM Forms-App {#troubleshoot-aem-forms-app}

In diesem Artikel werden die Fehlermeldungen, die beim Erstellen von AEM Forms App möglicherweise angezeigt werden und die Schritte zur Problembehebung.

Die Abschnitte in diesem Artikel behandeln Folgendes:

* [Verlust von Anhängen für iOS-Benutzer](/help/forms/using/issues-aem-forms-app.md#attachment-loss-for-ios-users)
* [Entwürfe von HTML5 -Formularen, die von Workspace-Benutzern eingesendet wurden, werden nicht auf dem Portal angezeigt](/help/forms/using/issues-aem-forms-app.md#html-form-drafts-submitted-by-workspace-users-are-not-visible-on-the-portal)
* [HTML5-Formulare (nicht zwischengespeichert) werden in AEM Forms App nicht geladen](/help/forms/using/issues-aem-forms-app.md#html-forms-not-cached-fail-to-load-in-aem-forms-app)
* [AEM Forms werden unter Windows nicht synchronisiert](/help/forms/using/issues-aem-forms-app.md#aem-forms-do-not-sync-on-windows)
* [Nicht unterstützte Version von Gradle](/help/forms/using/issues-aem-forms-app.md#unsupported-version-of-gradle)
* [Kompatibilitätsprobleme mit Gradle und Android Gradle Plug-In](/help/forms/using/issues-aem-forms-app.md#gradle-and-android-gradle-plug-in-compatibility-issues)

## Verlust von Anhängen für iOS-Benutzer {#attachment-loss-for-ios-users}

AEM Forms-App für iOS, die zur Synchronisierung mit AEM Forms unter OSGi konfiguriert ist, unterstützt nur Anlagen auf Feldebene. Alle Anlagen müssen eindeutige Namen haben. Wenn mehrere Anlagen denselben Namen haben, wird nur eine Anlage beibehalten und alle anderen mit identischem Namen gehen verloren. Führen Sie die folgenden Schritte aus, um Benutzer auf iOS-Geräten vor Datenverlust zu bewahren:

1. Navigieren Sie auf dem verbundenen Server zu **Adobe Experience Manager > Tools > Vorgänge > Web Console**.
1. Klicken Sie auf **[!UICONTROL Webkanalkonfiguration für adaptive Formulare und interaktive Kommunikation]**.
1. Aktivieren Sie im Dialogfeld [!UICONTROL Webkanalkonfiguration für adaptive Formulare und interaktive Kommunikation] die Option **Dateinamen individualisieren**.

   Wenn die Einstellung **Dateinamen individualisieren** deaktiviert ist, gehen die Daten der Benutzer verloren, wenn sie versuchen, adaptive Formulare mit mehreren Anhängen zu senden.

1. Klicken Sie auf **Speichern**.

## Entwürfe von HTML5 -Formularen, die von Workspace-Benutzern eingesendet wurden, werden nicht auf dem Portal angezeigt {#html-form-drafts-submitted-by-workspace-users-are-not-visible-on-the-portal}

Bei HTML5-Formularen, die in der AEM Forms-App mit **Als Entwurf speichern** HTML-Renderprofil aktiviert sind, sind die gespeicherten Entwürfe für Workspace-Benutzer nicht sichtbar. Um gespeicherte Entwürfe von HTML5-Formularen anzuzeigen, die von Workspace-Benutzern im Portal gesendet wurden, führen Sie die folgenden Schritte aus:

1. Öffnen Sie CRXDE und melden Sie sich als Administrator an.

   URL: `https://<server>:<port>/lc/crx/de/index.jsp`

1. Im Stammpfad von CRXDE, in der Zugriffssteuerungsliste unter Zugriffssteuerung klicken Sie auf **+**.
1. Klicken Sie im Dialogfeld **Neuen Eintrag hinzufügen** auf die Gruppensuche-Schaltfläche im Feld „Prinzipal“.
1. Geben Sie im Feld &quot;Name&quot;des Dialogfelds &quot;Prinzipal auswählen&quot;`PERM_WORKSPACE_USER` ein und klicken Sie auf **Suche**.
1. Wählen Sie die Gruppe `PERM_WORKSPACE_USER` im Dialogfeld &quot;Prinzipal auswählen&quot;und klicken Sie auf **OK**.
1. Im Dialogfeld „Neuen Eintrag hinzufügen“ wird `PERM_WORKSPACE_USER`-Gruppe im Feld „Prinzipal“ ausgewählt.

   Aktivieren Sie die `jcr:read`-Berechtigungen für die Benutzergruppe.

1. Klicken Sie auf **OK**.

## HTML5-Formulare (nicht zwischengespeichert) werden in AEM Forms App nicht geladen {#html-forms-not-cached-fail-to-load-in-aem-forms-app}

Wenn AEM Forms App mit einer älteren Version von AEM Forms-Server verbunden ist, können nicht zwischengespeicherte HTML5-Formulare nicht in AEM Forms App hochgeladen werden.

Führen Sie zur Behebung dieses Problems folgende Schritte durch:

1. Navigieren Sie in der Autoreninstanz zu **Adobe Experience Manager > Tools > Workspace-App-Offline-Dienst konfigurieren > Jetzt konfigurieren**.
1. Auf der Seite **Workspace-App Offline-Service** klicken Sie auf **Manueller Ressourcen-Cache**.

   URL: https://&lt;server>:&lt;port>/libs/fd/workspace-offline/content/config.html

1. Im **manuellen Ressourcen-Cache** klicken Sie auf die Schaltfläche **+**, um einen CRX-Pfad hinzuzufügen.
1. Geben Sie im Feld **Neue Ressource** Folgendes ein: /etc.clientlibs/fd/xfaforms/I18N/en_US.js und klicken Sie auf **Hinzufügen**.
1. Klicken Sie auf **Speichern**.

## AEM Forms werden unter Windows nicht synchronisiert  {#aem-forms-do-not-sync-on-windows}

Ein Formular wird unter Windows nicht in der AEM Forms-App mit dem verbundenen Server synchronisiert, wenn der Pfad des Formulars oder seine Ressourcen länger als 256 Zeichen lang sind.

Modifizieren Sie den Pfad des Formulars und seine Ressourcen, um die Anzahl der Zeichen im Pfad auf 256 zu reduzieren.

## Nicht unterstützte Version von Gradle  {#unsupported-version-of-gradle}

**Fehlermeldung:** Das Projekt verwendet eine nicht unterstützte Version von Gradle.

Die Fehlermeldung wird angezeigt, wenn Sie die AEM Forms-App in Android Studio erstellen. Das Problem tritt aufgrund einer nicht unterstützten Version von Gradle auf, die vom System unterstützt wird.

**Lösung:** Klicken Sie auf Gradle Wrapper  **reparieren und** importieren Sie das Projekt erneut, um das Problem zu beheben.

![gradle_unsupported_version](assets/gradle_unsupported_version.png)

## Kompatibilitätsprobleme mit Gradle und Android Gradle Plug-In {#gradle-and-android-gradle-plug-in-compatibility-issues}

**Fehlermeldung:** Die Versionen des Android Gradle-Plug-ins und Gradle sind nicht kompatibel.

Die Fehlermeldung wird angezeigt, wenn Sie die Option **Build APK** aus dem Menü **Build** auf der Benutzeroberfläche von Android Studio auswählen.

![gradle_plugin_compatibility](assets/gradle_plugin_compatibility.png)

**Lösung:** Öffnen Sie die Datei  **Gradle Scripts**  >  **gradle-wrapper.** properties und bearbeiten Sie die Eigenschaft  **** distributionUrlproperty.

Beispielsweise empfiehlt die Android Studio-Konsole, die Gradle-Version auf 3.5 herabzustufen. Bearbeiten Sie die Version in der Datei **distributionUrl** von **gradle-wrapper.properties** .

Wählen Sie erneut **Build** > **Build APK** aus, um den Fehler zu beheben und die .apk-Datei zu generieren.

![gradle_wrapper_properties](assets/gradle_wrapper_properties.png)
