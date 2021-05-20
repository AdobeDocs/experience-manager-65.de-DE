---
title: AEM Forms-App
seo-title: AEM Forms-App
description: Die AEM Forms-App ermöglicht Ihren Außendienstmitarbeitern die Verwendung adaptiver Formulare auf mobilen Endgeräten.
seo-description: Die AEM Forms-App ermöglicht Ihren Außendienstmitarbeitern die Verwendung adaptiver Formulare auf mobilen Endgeräten.
uuid: fac976c8-b713-4492-b153-f567e7a11ceb
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: e18aa345-034c-473b-b4c2-01678bb10616
exl-id: 171754a2-1ba5-42dc-b6d2-3d730807cc31
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2470'
ht-degree: 78%

---

# Einführung in die AEM Forms-App {#aem-forms-app}

## Überblick {#overview}

Die AEM Forms-App ermöglicht die Synchronisierung adaptiver Formulare sowie von Formularen auf Mobilgeräten und Formularsätzen auf Mobilgeräten basierend auf Ihrem Server. Sie können Workflows definieren, die [formularzentrierte Workflows auf OSGi ](/help/forms/using/aem-forms-workflow.md) oder  Formular-Workflows auf JEE  sind. Angenommen, Sie leiten ein Bankgeschäft und nutzen AEM Forms für die Verwaltung von Kundenanträgen und - mitteilungen. Ihre Kunden füllen ein Formular aus und übermitteln es zur Prüfung. Wenn Sie das Formular auf Mobilgeräten aktivieren, können Ihre Kunden es in der AEM Forms-App ausfüllen. Sie können darüber hinaus den Arbeitsablauf für die Prüfung verwalten, indem Sie das Überprüfungsformular auf Mobilgeräten aktivieren. Ihr Außendienstmitarbeiter kann ein Mobilgerät zum Kundenstandort mitnehmen, die Details überprüfen und das Formular senden. Die AEM Forms-App wird mit dem AEM Forms-Server synchronisiert und ruft die Formulare ab, die für Mobilgeräte aktiviert wurden. Wenn die App offline ist, speichert sie die Daten lokal.

Der Quellcode der AEM Forms-App ist für Kunden über die Software Distribution verfügbar. Das Quellcode-Paket in Softwareverteilung ist verfügbar als: `adobe-aemfd-forms-app-src-pkg-<version>.zip`.

Die AEM Forms-App wird auf iOS-, Android- und Windows-Geräten unterstützt. Sie können die AEM Forms-App für Android aus Google Play, iOS aus dem App Store und Windows aus dem Windows Store installieren.

    [ ![google_play](assets/google_play.png)](https://play.google.com/store/apps/details?id=com.adobe.aem.forms)
    
    [ ![app_store](assets/app_store.png)(https://itunes.apple.com/us/app/adobe-experience-manager-forms/id1129625976?ls=1&amp;mt=8)
    
    [ ![microsoft-badge-icon](assets/microsoft-badge-icon.png)](https://www.microsoft.com/en-us/store/p/adobe-experience-manager-forms/9nd12rlxtgtt)

Informationen zum Installieren, Anpassen und Verteilen der App auf iOS-, Android- oder Windows-Geräten erhalten Sie unter [Anpassen, Erstellen und Verteilen der AEM Forms-App](#customize-build-distribute).

## Voraussetzungen {#prerequisites}

Die AEM Forms-App erfordert einen AEM Forms-Server. Benutzer können Formulare wiedergeben, die Sie im AEM Forms-Server erstellt haben, sie ausfüllen, als Entwürfe speichern und senden. Die App stellt eine Verbindung zum Server her und ruft aktivierte Formulare ab. Die AEM Forms-App wird mit dem Server synchronisiert und sobald Formulare in der App geladen werden, können Benutzer im Offlinemodus arbeiten. Wenn die App offline ist, werden die Daten auf dem Gerät gespeichert, und die Daten werden mit dem Server synchronisiert, wenn die App wieder online ist.

### AEM Forms-App mit Servern, die den AEM Forms-Arbeitsablauf verwenden {#aem-forms-app-with-servers-using-aem-forms-workflow}

Wenn Sie einen AEM Forms Workflow-Server haben, können Sie Formulare als Aufgaben in der AEM Forms App wiedergeben. Angenommen, Sie leiten ein Bankgeschäft und ein Kunde füllt einen Antrag für die Nutzung Ihrer Dienstleistungen aus. Die Anwendung ist ein adaptives Formular, in das Ihre Kunden Daten eingeben, die dann als Antrag zur Prüfung übermittelt werden. Der Administrator prüft den Antrag und sendet eine Überprüfungsanforderung an den Außendienstmitarbeiter. Der weitergeleitete Antrag aktiviert in der App des Außendienstmitarbeiters ein Überprüfungsformular als Aufgabe. Ihr Außendienstmitarbeiter nimmt das Mobilgerät zum Kundenstandort mit und überprüft die Angaben.

### AEM Forms-App mit Servern, die formularzentrierte Workflows in OSGi verwenden {#aem-forms-app-with-servers-using-forms-centric-workflow-on-osgi}

Wenn Sie über einen AEM Forms-Server verfügen, können Sie adaptive Formulare als AEM Inbox-Anwendung und Aufgaben in der AEM Forms-App ausgeben. Angenommen, Sie leiten eine Bank und ein Kunde füllt einen Antrag, um Ihre Dienstleistungen in Anspruch zu nehmen. Die Anwendung ist mit einem adaptiven Formular verknüpft, in das Ihre Kunden Daten eingeben, die dann als Sendung für den Review gespeichert werden. Der Administrator überprüft die Aufgabe und genehmigt die Überprüfungsanfrage an den Außendienstmitarbeiter. Ihr Außendienstmitarbeiter nimmt das Mobilgerät zum Kundenstandort mit und überprüft die Angaben.

### Eigenständige Formulare oder AEM Forms-App mit Servern ohne AEM Forms-Workflow {#standalone-forms-or-aem-forms-app-with-servers-without-aem-forms-workflow}

Ein AEM Forms-Server, der keinen AEM Forms-Workflow verwendet, ist AEM Forms on OSGi oder ein eigenständiges Formulare für Mobilgeräte oder ein adaptives Formular. Die AEM Forms-App kann mit Ihrer AEM Forms-Implementierung unter [OSGi](/help/sites-deploying/configuring-osgi.md) eingesetzt werden. Formulare, die Sie für die AEM Forms-App aktivieren und veröffentlichen, stehen in der App zur Verfügung.

Die Formulare werden in Ihre App heruntergeladen und sind offline verfügbar. Beispiel: Sie führen ein Bankunternehmen aus und ein Kunde füllt einen Antrag auf Ihrer Site aus. Die Anwendung ist ein adaptives Formular, in das Ihre Kunden Daten eingeben, die dann zur Prüfung übermittelt werden. Der Administrator prüft das Formular und erstellt in einer Autoreninstanz von AEM ein Überprüfungsformular. Der Administrator aktiviert die Synchronisierung des Formulars mit der AEM Forms-App und veröffentlicht es. Wenn das Überprüfungsformular in der AEM Forms-App verfügbar ist, kann Ihr Außendienstmitarbeiter die Angaben des Kunden auf einem Mobilgerät überprüfen. Das Mobilgerät wird mit dem Server synchronisiert und das Überprüfungsformular wird in der App geladen. Ihr Außendienstmitarbeiter kann Ihren Kunden besuchen, die Angaben überprüfen und die Daten als Entwurf speichern oder das Überprüfungsformular übermitteln. Das Formular wird jedes Mal, wenn Ihre App online ist, mit dem Server synchronisiert.

Formular in der AEM Forms-App synchronisieren

1. Wählen Sie in der Autoreninstanz ein Formular aus und klicken Sie auf **** Eigenschaften anzeigen.

1. Klicken Sie auf der Eigenschaftenseite auf **[!UICONTROL Erweitert]**.
1. Aktivieren Sie unter &quot;Erweitert&quot;die Option: **[!UICONTROL Synchronisieren mit AEM Forms App]** und tippen Sie auf **[!UICONTROL Speichern]**.

Wenn das Formular veröffentlicht wird, wird die App mit dem Server synchronisiert und ruft das Formular ab. Um mehrere Formulare zu synchronisieren, wählen Sie in der Autoreninstanz mehrere Formulare in Forms Manager aus und tippen Sie auf **[!UICONTROL Mit AEM Forms-App synchronisieren]**.

## Unterstützung für Mobilgeräte  {#mobile-device-support}

Weitere Informationen finden Sie unter [AEM Forms-App (vorher bekannt als Mobile Workspace)](/help/forms/using/aem-forms-jee-supported-platforms.md#aem-forms-workspace-app)

## Hauptfunktionen der AEM Forms-App  {#key-features-of-aem-forms-app}

### AEM Forms-App mit AEM Forms-Servern {#aem-forms-app-with-aem-forms-servers}

Sie können Ihre App mit dem AEM Forms-Server synchronisieren und auf Ihrem Mobilgerät Formulare bearbeiten.

Auf einem AEM Forms-Server können Sie ein Formular einem Startpunkt in einem Workbench-Vorgang und einer AEM Inbox-Anwendung zuordnen. Einer AEM Inbox-Anwendung kann ein adaptives Formular zugeordnet werden. Einem Startpunkt kann ein adaptives Formular, ein HTML5-Formular oder ein Formularsatz zugeordnet werden. Es ist möglich, einen Startpunkt als Aufgabe zu senden oder die Aufgabe als Entwurf zu speichern. Weitere Informationen zu den Unterschieden zwischen einer AEM Inbox-Anwendung und einem Startpunkt finden Sie unter [Aktionen und Funktionen formularzentrierter AEM-Workflows auf OSGi- und AEM Forms-JEE-Workflows](capabilities-osgi-jee-workflows.md).

Bei AEM Forms-Servern ohne AEM Forms-Arbeitsablauf werden Formulare, für die die Synchronisierung in der App aktiviert ist, in der AEM Forms-App wiedergegeben. Formulare sind auf der Registerkarte „Formulare“ der App verfügbar und können gesendet oder als Entwurf gespeichert werden. Adaptive Formulare und Formulare für Mobilgeräte werden in der App unterstützt.

1. **Speichern einer Aufgabe oder eines Formulars als Entwurf**

   Mit der Option „Als Entwurf speichern“ wird ein Schnappschuss einer Aufgabe bzw. eines Formulars zusammen mit den eingegebenen Daten und den im zugehörigen Formular angehängten Dateien gespeichert. Die Entwürfe werden auf dem Mobilgerät gespeichert und für den späteren Abruf mit dem AEM Forms-Server synchronisiert.

   Weitere Informationen finden Sie unter [Speichern einer Aufgabe oder eines Formulars als Entwurf](/help/forms/using/save-as-draft.md).

1. **Speichern von Formularen als Vorlagen**

   Wenn Benutzer ein Formular ausfüllen, müssen Eingaben in manchen Felder zuweilen unverändert bleiben. In solchen Fällen können Sie die Felder, für die in allen Instanzen dieselben Werte benötigt werden, ausfüllen und das Formular bzw. den Entwurf als Vorlage speichern. Danach sind die angegebenen Felder jedes Mal, wenn Sie eine Instanz der Vorlage erstellen, bereits mit den Werten aus der Vorlage ausgefüllt. Dies spart Zeit und Mühe beim Ausfüllen des Formulars.

   Weitere Informationen finden Sie unter[ Speichern von Formularen als Vorlagen](/help/forms/using/save-forms-and-start-points-as-templates.md).

### Mit Aufgaben und Formularen arbeiten  {#working-with-tasks-and-forms}

Sie können Ihre App mit dem AEM Forms Workflow-Server synchronisieren und auf Ihrem Mobilgerät an Aufgaben und Formularen arbeiten.

Eine Aufgabe auf dem Mobilgerät enthält ein adaptives Formular, ein HTML5-Formular oder einen Formularsatz und kann auch Anhänge und die [Zusammenfassungs-URL](/help/forms/using/getting-task-variables-summary-url.md) enthalten. Standardmäßig werden die Ihnen zugewiesenen Aufgaben im Ordner **[!UICONTROL Tasks]** platziert. Bei der Bearbeitung einer Aufgabe können Sie die Aufgabe ändern und einen Aufgabenentwurf auf dem AEM Forms-Server speichern.

Ein Formular auf einem Mobilgerät kann ein adaptives Formular oder ein Formular für ein Mobilgerät sein. Die für die Synchronisierung aktivierten Formulare in der Forms-App stehen im Ordner „Formulare“ zur Verfügung. Es ist möglich, Formulare zu synchronisieren, die auf dem AEM Forms-Server ohne AEM Form-Arbeitsablauf (AEM Forms on OSGi) aktiviert sind.

Siehe:

* [Öffnen einer Aufgabe](/help/forms/using/open-task.md)
* [Arbeiten mit einem Formular](/help/forms/using/working-with-form.md)

### Offline arbeiten {#working-offline}

Sie können auf Ihrem Gerät im Offline-Modus arbeiten. Sie können sich bei der Anwendung anmelden, auch wenn keine Netzwerkverbindung besteht, und alle Formulare bearbeiten, die mit dem Gerät synchronisiert wurden, als Sie zuletzt online waren. Weitere Informationen zum Synchronisieren der Formulare erhalten Sie unter [Synchronisieren der App](/help/forms/using/sync-app.md). Wenn Sie die mit einem Formular verknüpften Anlagen synchronisieren möchten, können Sie die Anlagen auch im Offline-Modus öffnen. Sie können im Offline-Modus das Formular bearbeiten, Anmerkungen hinzufügen und ein Formular senden oder speichern. Das Formulare wird mit dem AEM Forms-Server synchronisiert, wenn Sie das nächste Mal online sind.

Weitere Informationen finden Sie unter [Arbeiten im Offlinemodus](/help/forms/using/work-offline-mode.md).

### Hinzufügen von Anmerkungen  {#adding-annotations}

Sie können Formularen auf Ihrem Gerät die folgenden Anhänge hinzufügen

* **Anmerkungen** - Sie können die Funktion &quot;Hinweise&quot;verwenden, um Ihrem Formular ein Freihand-Scribble oder eine Textanmerkung hinzuzufügen. Weitere Informationen finden Sie unter [ Notizen hinzufügen](/help/forms/using/add-attachments.md#adding-a-note).

* **Bild** - Die AEM Forms-App enthält eine Funktion, die die Kamerafunktion oder die Galerie Ihres Mobilgeräts verwendet. Mit dem Fotoanhang können Sie dem zugehörigen Formular ein Foto hinzufügen. Weitere Informationenfinden Sie unter [Hinzufügen eines Fotos](/help/forms/using/add-attachments.md#adding-a-photograph).

### Automatisch speichern {#autosave}

Wenn ein Benutzer Daten in die AEM Forms-App eingibt, speichert diese Funktion die Angaben in regelmäßigen Abständen. Die automatische Speicherung in der AEM Forms-App hilft Ihnen, Datenverlust zu vermeiden, wenn die App unbeabsichtigt geschlossen wird, etwa wegen niedrigen Batteriestands.

Weitere Informationen finden Sie unter [ Verwenden der automatischen Speicherung in der AEM Forms-App](/help/forms/using/autosave-data-app.md).

## Unterschiede zwischen den Funktionen von AEM Inbox und AEM Forms-App  {#differences-between-aem-inbox-and-aem-forms-app-features}

Zwei der wichtigsten Möglichkeiten, einen Forms-orientierten Workflow zu starten, sind die Verwendung von [AEM Posteingang](/help/forms/using/manage-applications-inbox.md) und der AEM Forms-App. Die Funktionen von AEM Inbox und AEM Forms-App sind jedoch unterschiedlich. AEM Posteingang funktioniert nur mit [Forms-orientierten Workflows](/help/forms/using/aem-forms-workflow.md), während die AEM Forms-App sowohl mit Forms-orientierten Workflows als auch mit Prozessverwaltung funktioniert. Weitere Informationen zu den Unterschieden zwischen AEM Inbox- und AEM Forms-App-Funktionen finden Sie unter [Aktionen und Funktionen formularzentrierter AEM Workflows in OSGi- und AEM Forms JEE-Workflows](capabilities-osgi-jee-workflows.md).

## Unterstützte Formulare {#supported-forms}

Unterstützte Formulartypen in der AEM Forms-App:

### Adaptives Formular  {#adaptive-form}

Ein adaptives Formular, das sich Benutzereingaben dynamisch anpasst, wird in der AEM Forms-App unterstützt. Verzögert geladene adaptive Formulare werden ebenfalls unterstützt.

### Formulare für Mobilgeräte {#mobile-form}

Sie können Formulare für Mobilgeräte in AEM Forms erstellen. Formulare für Mobilgeräte werden als HTML-Formulare auf Mobilgeräten wiedergeben und passen sich an die Anzeige auf dem jeweiligen Gerät an.

### Formularsatz {#formset}

Mit Formularsätzen können mehrere zu einem Dienst oder Prozess gehörige Formulare gruppiert werden, um einen Geschäftsprozess zu automatisieren, und anschließend für die Endbenutzer bereitgestellt werden. In einem solchen Fall können die Benutzer den gesamten Formularsatz als einzelnes Formular ausfüllen und es besteht keine Notwendigkeit, einzelne Formulare oder Prozesse zu archivieren, zu versenden oder nachzuverfolgen.

>[!NOTE]
>
>Hierfür ist AEM Forms Workflow (AEM Forms on JEE) erforderlich.

## Funktionsweise der AEM Forms-App  {#how-aem-forms-app-works}

Die AEM Forms-App bietet eine mobile Lösung für Außendienstmitarbeiter, um mit ihnen zugewiesenen Formularen zu arbeiten. Die Anwendung speichert alle Daten vom Server zwischen und bietet einen effizienten Arbeitsablauf, da die gesamte Arbeit lokal gespeichert wird. Diese Daten werden über regelmäßige Synchronisierungsupdates an den Server gesendet.

Die AEM Forms-App ist eine PhoneGap 5.0-basierte Anwendung, in der das Backbone-Modell effizient eingesetzt wird, um in den Modellen gespeicherte Daten über Ansichten darzustellen. Alle nativen Vorgänge werden durch PhoneGap-Plug-Ins ausgeführt.

## AEM Forms-App anpassen, erstellen und verteilen  {#customize-build-distribute}

>[!NOTE]
>
>Gilt nur, wenn Sie AEM Forms-App-Quellcode zum Erstellen der App verwenden.

Die AEM Forms-App lässt sich ganz einfach an organisationsspezifische Anforderungen anpassen. Der Quellcode für die Anwendung wird zusammen mit AEM Forms bereitgestellt. Sie können Änderungen am Quellcode vornehmen und Ihre eigene benutzerdefinierte Mobile Workspace-Lösung erstellen. Sie können die App auch mit Ihrem eigenen Unternehmensschlüssel signieren.

### Anpassen {#customize}

Sie können Ihre App anpassen:

**Branding**: Ändern Sie das App-Symbol, den App-Namen, Startbilder und Seiten in der AEM Forms-App. Außerdem können Sie Text ändern, um die App für eine bestimmte Region zu lokalisieren. Weitere Informationen zum Branding der AEM Forms-App finden Sie unter [Branding-Anpassung](/help/forms/using/branding-customization.md).

**Design**: Ändern Sie Stile wie Farben, Schriftarten und Abstände in der Benutzeroberfläche der AEM Forms-App. Weitere Informationen finden Sie unter [Designanpassung](/help/forms/using/theme-customization.md).

**Geste**: Ändern Sie Gesten wie das Wischen nach rechts und links in der Benutzeroberfläche der AEM Forms-App. Weitere Informationen finden Sie unter [Gestenanpassung](/help/forms/using/gesture-customization.md).

Weitere Informationen zum Einrichten eines AEM Forms-App-Projekts zur Anpassung finden Sie unter:

* [Einrichten einer Umgebung für die AEM Forms-App](/help/forms/using/setup-environment-mobile-workspace.md)
* [Einrichten des Visual Studio-Projekts und Erstellen der Windows-App](/help/forms/using/setup-visual-studio-project-build-installer.md)
* [Einrichten des Xcode-Projekts und Erstellen der iOS-App](/help/forms/using/setup-xcode-project-build-installer.md)
* [Einrichten des Eclipse-Projekts und Erstellen der Android-App](/help/forms/using/setup-eclipse-project-build-installer.md)

### Pakete erstellen und bereitstellen {#build-and-distribute}

Der Quellcode für die AEM Forms-App kann aus dem `adobe-lc-mobileworkspace-src.zip` extrahiert werden, das als Teil des AEM Forms-Quellpakets für die App auf Softwareverteilung verfügbar ist.

Um die AEM Forms App-Quelle zu erhalten, führen Sie die folgenden Schritte aus:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können auch die Option **[!UICONTROL Downloads suchen]** verwenden, um die Ergebnisse zu filtern.
1. Tippen Sie auf den Paketnamen für Ihr Betriebssystem, wählen Sie **[!UICONTROL Endbenutzer-Lizenzbedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Download]**.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

**iOS**:

Weitere Informationen zum Erstellen einer iOS-App (.ipa), finden Sie unter [Einrichten des Xcode-Projekts und Erstellen der iOS-App](/help/forms/using/setup-xcode-project-build-installer.md).

Weitere Informationen zum Signieren der AEM Forms-App mit Ihrem Bereitstellungsprofil finden Sie unter [iOS Code Signing Setup, Process, and Troubleshooting](https://developer.apple.com/support/code-signing/).

**Android**:

Weitere Informationen zum Erstellen einer Android-App (.apk) finden Sie unter [Einrichten des Eclipse-Projekts und Erstellen der Android-App](/help/forms/using/setup-eclipse-project-build-installer.md).

Weitere Informationen zum Signieren der AEM Forms-App finden Sie unter [Signing Your Applications](https://developer.android.com/tools/publishing/app-signing.html).

**Für Windows**:

Weitere Informationen zum Erstellen einer Windows-App (.appx) finden Sie unter [Einrichten des Visual Studio-Projekts und Erstellen der Windows-App](/help/forms/using/setup-visual-studio-project-build-installer.md).

Weitere Informationen zum Verteilen der App über MDM finden Sie unter [Verteilen der AEM Forms-App](/help/forms/using/distribute-mobile-workspace-app.md). App-Verteilung über MDM gilt nur für iOS und Android.

## Empfehlungen zur Aktualisierung von Mobile Workspace auf der AEM Forms-App {#recommendations-to-upgrade-mobile-workspace-to-aem-forms-app}

Wenn Sie auf die neueste Version von AEM Forms-App aktualisieren, achten Sie darauf, dass Sie folgende Punkte lesen:

* **Wenn Sie eine frühere Version der App vom Play Store auf Android installiert haben** können Sie die App direkt vom Play Store aktualisieren.

* **Wenn eine frühere Version des Programms mithilfe des Quellcodes erstellt und installiert wird (gilt für iOS und Android)**:

   Synchronisieren Sie vor der Installation der neuen App alle Ihre Daten mit dem AEM Forms-Server. Nachdem die Daten synchronisiert wurden, müssen Sie frühere Versionen der App und die neue App installieren.
