---
title: Fehlerbehebung der AEM Forms-App
description: Erfahren Sie mehr über häufige Probleme mit der AEM Forms-App und wie Sie diese beheben können.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: caec5fc3-db52-4bf5-8eb2-17e5189ab819
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 100%

---

# Fehlerbehebung der AEM Forms-App {#troubleshoot-aem-forms-app}

In diesem Artikel werden die Fehlermeldungen beschrieben, die beim Erstellen der AEM Forms-App möglicherweise angezeigt werden, sowie die Schritte zu ihrer Behebung.

Die Abschnitte in diesem Artikel beinhalten:

* [Verlust von Anhängen für iOS-Benutzer](/help/forms/using/issues-aem-forms-app.md#attachment-loss-for-ios-users)
* [Entwürfe von HTML5 -Formularen, die von Workspace-Benutzern eingesendet wurden, werden nicht auf dem Portal angezeigt](/help/forms/using/issues-aem-forms-app.md#html-form-drafts-submitted-by-workspace-users-are-not-visible-on-the-portal)
* [HTML5-Formulare (nicht zwischengespeichert) werden in AEM Forms App nicht geladen](/help/forms/using/issues-aem-forms-app.md#html-forms-not-cached-fail-to-load-in-aem-forms-app)
* [AEM Forms werden unter Windows nicht synchronisiert](/help/forms/using/issues-aem-forms-app.md#aem-forms-do-not-sync-on-windows)
* [Nicht unterstützte Version von Gradle](/help/forms/using/issues-aem-forms-app.md#unsupported-version-of-gradle)
* [Kompatibilitätsprobleme mit Gradle und Android Gradle Plug-In](/help/forms/using/issues-aem-forms-app.md#gradle-and-android-gradle-plug-in-compatibility-issues)

## Verlust von Anhängen für iOS-Benutzer {#attachment-loss-for-ios-users}

Die AEM Forms-App für iOS, die für die Synchronisierung mit AEM Forms unter OSGi konfiguriert ist, unterstützt nur Anlagen auf Feldebene. Alle Anlagen müssen eindeutige Namen haben. Wenn mehrere Anlagen denselben Namen haben, wird nur eine Anlage beibehalten und alle anderen mit identischem Namen gehen verloren. Führen Sie die folgenden Schritte aus, um Benutzer auf iOS-Geräten vor Datenverlust zu bewahren:

1. Auf dem verbundenen Server navigieren Sie zu: **Adobe Experience Manager > Werkzeuge > Vorgänge > Webkonsole**.
1. Suchen Sie nach **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** und klicken Sie darauf.
1. Aktivieren Sie im Dialog [!UICONTROL Adaptives Formular und interaktive Kommunikation Webkanal-Konfiguration] die Option **Dateinamen individualisieren**.

   Wenn die Einstellung **Dateinamen individualisieren** deaktiviert ist, können die Benutzer Daten verlieren, wenn sie versuchen, adaptive Formulare mit mehreren Anlagen zu versenden.

1. Klicken Sie auf **Speichern**.

## Entwürfe von HTML5 -Formularen, die von Workspace-Benutzern eingesendet wurden, werden nicht auf dem Portal angezeigt {#html-form-drafts-submitted-by-workspace-users-are-not-visible-on-the-portal}

Bei HTML5-Formularen, die in der AEM Forms-Anwendung mit dem HTML-Renderprofil **Als Entwurf speichern** aktiviert sind, sind die gespeicherten Entwürfe für Arbeitsbereichsbenutzer nicht sichtbar. Führen Sie die folgenden Schritte aus, um gespeicherte Entwürfe von HTML5-Formularen anzuzeigen, die von Arbeitsbereichsbenutzern im Portal übermittelt wurden:

1. Öffnen Sie CRXDE und melden Sie sich als Administrator an.

   URL: `https://<server>:<port>/lc/crx/de/index.jsp`

1. Im Stammpfad von CRXDE, in der Zugriffssteuerungsliste unter Zugriffssteuerung klicken Sie auf **+**.
1. Klicken Sie im Dialogfeld **Neuen Eintrag hinzufügen** auf die Schaltfläche für die Gruppensuche im Feld „Prinzipal“.
1. Geben Sie im Feld „Name“ des Dialogfelds „Prinzipal auswählen“ `PERM_WORKSPACE_USER` ein und klicken Sie auf **„Suchen“**. 
1. Wählen Sie `PERM_WORKSPACE_USER`-Gruppe im Dialogfeld „Prinzipal wählen“ und klicken Sie auf **OK**.
1. Im Dialogfeld „Neuen Eintrag hinzufügen“ wird `PERM_WORKSPACE_USER`-Gruppe im Feld „Prinzipal“ ausgewählt.

    Aktivieren Sie `jcr:read`-Berechtigungen für die Benutzergruppe.

1. Klicken Sie auf **OK**.

## HTML5-Formulare (nicht zwischengespeichert) werden in der AEM Forms-App nicht geladen {#html-forms-not-cached-fail-to-load-in-aem-forms-app}

Wenn die AEM Forms-App mit einer älteren Version des AEM-Formular-Servers verbunden ist, können nicht zwischengespeicherte HTML5-Formulare nicht in der AEM Forms-App geladen werden.

Führen Sie zur Behebung dieses Problems folgende Schritte durch:

1. Navigieren Sie in der Autoreninstanz zu **Adobe Experience Manager > Tools > Workspace-App-Offline-Dienst konfigurieren > Jetzt konfigurieren**.
1. Auf der Seite **Workspace-App Offline-Service** klicken Sie auf **Manueller Ressourcen-Cache**.

   URL: https://&lt;server>:&lt;port>/libs/fd/workspace-offline/content/config.html

1. Im **manuellen Ressourcen-Cache** klicken Sie auf die Schaltfläche **+**, um einen CRX-Pfad hinzuzufügen.
1. Geben Sie in das Feld **Neue Ressourcen hinzufügen** ein: /etc.clientlibs/fd/xfaforms/I18N/en_US.js und klicken Sie auf **Hinzufügen**.
1. Klicken Sie auf **Speichern**.

## AEM Forms werden unter Windows nicht synchronisiert {#aem-forms-do-not-sync-on-windows}

In der AEM Forms-App unter Windows wird ein Formular nicht mit dem verbundenen Server synchronisiert, wenn der Pfad des Formulars oder seiner Ressourcen 256 Zeichen oder mehr enthält.

Ändern Sie den Pfad des Formulars und seiner Ressourcen, um die Anzahl der Zeichen auf weniger als 256 zu reduzieren.

## Nicht unterstützte Version von Gradle {#unsupported-version-of-gradle}

**Fehlermeldung:** Das Projekt verwendet eine nicht unterstützte Version von Gradle.

Die Fehlermeldung wird angezeigt, wenn Sie die AEM Forms-App in Android Studio erstellen. Das Problem tritt aufgrund einer nicht unterstützten Version von Gradle auf, die vom System unterstützt wird.

**Lösung:** Klicken Sie auf **Gradle-Wrapper reparieren und Projekt erneut importieren**, um das Problem zu lösen.

![gradle_unsupported_version](assets/gradle_unsupported_version.png)

## Kompatibilitätsprobleme mit Gradle und Android Gradle Plug-In {#gradle-and-android-gradle-plug-in-compatibility-issues}

**Fehlermeldung:** Die Versionen des Android Gradle Plug-Ins und Gradle sind nicht kompatibel.

Die Fehlermeldung wird angezeigt, wenn Sie die Option **APK erstellen** aus dem Menü **Erstellen** auf der Android Studio-Benutzeroberfläche wählen.

![gradle_plugin_compatibility](assets/gradle_plugin_compatibility.png)

**Lösung:** Öffnen Sie die Datei **Gradle Scripts** > **gradle-wrapper.properties** und bearbeiten Sie die Eigenschaft **distributionUrl**.

Beispielsweise empfiehlt die Android Studio-Konsole ein Downgrade der Gradle-Version auf 3.5. Bearbeiten Sie die Version in **distributionUrl** der **gradle-wrapper.properties**-Datei.

Wählen Sie erneut **Erstellen** > **APK erstellen**, um den Fehler zu beheben und die .apk-Datei zu generieren.

![gradle_wrapper_properties](assets/gradle_wrapper_properties.png)
