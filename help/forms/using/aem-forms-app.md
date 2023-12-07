---
title: AEM Forms-App
description: Die AEM Forms-App ermöglicht es Außendienstmitarbeitern, adaptive Formulare auf ihren Mobilgeräten zu verwenden.
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 171754a2-1ba5-42dc-b6d2-3d730807cc31
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '2410'
ht-degree: 42%

---

# Einführung in die AEM Forms Workspace-App {#aem-forms-app}

## Übersicht {#overview}

Das AEM Forms-Programm ermöglicht die Synchronisierung adaptiver Formulare, mobiler Formulare und Formularsätze auf Mobilgeräten basierend auf Ihrem Server. Sie können Workflows definieren, die [formularzentrierte Workflows auf OSGi](/help/forms/using/aem-forms-workflow.md) oder Formular-Workflows auf JEE sind. Beispiel: Sie führen ein Bankunternehmen und verwenden AEM Forms, um Kundenanwendungen und -kommunikation zu verwalten. Ihre Kunden füllen ein Formular aus und senden es zur Überprüfung. Wenn Sie das Formular auf Mobilgeräten aktivieren, können Ihre Kunden das Formular in der AEM Forms-App ausfüllen. Sie können den Überprüfungs-Workflow auch verwalten, indem Sie das Überprüfungsformular auf Mobilgeräten aktivieren. Ihr Außendienstmitarbeiter kann ein Mobilgerät zum Kunden mitnehmen, die Details überprüfen und das Formular senden. Das AEM Forms-Programm synchronisiert mit dem AEM Forms-Server und ruft die für Mobilgeräte aktivierten Formulare ab. Wenn die App offline ist, speichert sie die Daten lokal.

Der Quellcode der AEM Forms-App ist für Kunden über die Software Distribution verfügbar. Das Paket mit dem Quell-Code steht in Software Distribution zur Verfügung als `adobe-aemfd-forms-app-src-pkg-<version>.zip`.

Die AEM Forms-App wird auf iOS-, Android- und Windows-Geräten unterstützt. Sie können die Mobile App von AEM Forms für Android über Google Play, für iOS über den App Store und für Windows über den Windows Store installieren.

    [ ![google_play](assets/google_play.png)](https://play.google.com/store/apps/details?id=com.adobe.aem.forms)
    
    [ ![app_store](assets/app_store.png)](https://itunes.apple.com/us/app/adobe-experience-manager-forms/id1129625976?ls=1&amp;mt=8)
    
    [ ![microsoft-badge-icon](assets/microsoft-badge-icon.png)](https://www.microsoft.com/en-us/store/p/adobe-experience-manager-forms/9nd12rlxtgtt)

Informationen zum Installieren, Anpassen und Verteilen der App auf iOS-, Android- oder Windows-Geräten finden Sie unter [Anpassen, Erstellen und Verteilen der AEM Forms-App](#customize-build-distribute).

## Voraussetzungen {#prerequisites}

Für das AEM Forms-Programm ist ein AEM Forms-Server erforderlich. Benutzer können Formulare wiedergeben, die Sie im AEM Forms-Server erstellt haben, sie ausfüllen, als Entwürfe speichern und senden. Das Programm stellt eine Verbindung zum Server her und ruft aktivierte Formulare ab. Das AEM Forms-Programm wird mit dem Server synchronisiert und sobald Formulare in der App geladen werden, können Benutzer offline arbeiten. Wenn die App offline ist, werden die Daten auf dem Gerät gespeichert und die Daten mit dem Server synchronisiert, wenn die App online ist.

### AEM Forms-App mit Servern, die den AEM Forms-Workflow verwenden {#aem-forms-app-with-servers-using-aem-forms-workflow}

Wenn Sie über einen AEM Forms Workflow-Server verfügen, können Sie Formulare in der AEM Forms-App als Aufgaben rendern. Beispiel: Sie führen ein Bankunternehmen und der Kunde füllt eine Anwendung aus, um Ihre Dienste zu nutzen. Der Antrag ist ein adaptives Formular, das Informationen von Ihren Kunden akzeptiert und als Übermittlung zur Überprüfung speichert. Der Administrator prüft einen Antrag und leitet einen Überprüfungsantrag an den Außendienstmitarbeiter weiter. Der weitergeleitete Antrag aktiviert ein Überprüfungsformular in der App Ihres Außendienstmitarbeiters als Aufgabe. Ihr Außendienstmitarbeiter nimmt das Mobilgerät zum Kundenstandort mit und überprüft die Angaben.

### AEM Forms-App mit Servern, die einen Forms-orientierten Workflow auf OSGi verwenden {#aem-forms-app-with-servers-using-forms-centric-workflow-on-osgi}

Wenn Sie über einen AEM Forms-Server verfügen, können Sie adaptive Formulare als AEM Posteingangsanwendung und Aufgaben in der AEM Forms-App rendern. Beispiel: Sie führen ein Bankunternehmen und der Kunde füllt eine Anwendung aus, um Ihre Dienste zu nutzen. Der Antrag ist mit einem adaptiven Formular verknüpft, das Informationen von Ihren Kunden akzeptiert und als Übermittlung zur Überprüfung speichert. Der Administrator überprüft die Aufgabe und genehmigt die Überprüfungsanforderung an den Außendienstmitarbeiter. Ihr Außendienstmitarbeiter nimmt das Mobilgerät zum Kundenstandort mit und überprüft die Angaben.

### Eigenständige Formulare oder AEM Forms-App mit Servern ohne AEM Forms Workflow {#standalone-forms-or-aem-forms-app-with-servers-without-aem-forms-workflow}

Ein AEM Forms-Server, der keinen AEM Forms-Workflow verwendet, ist AEM Forms on OSGi oder ein eigenständiges mobiles Formular oder adaptives Formular. Die AEM Forms-App kann mit Ihrer AEM Forms-Implementierung unter [OSGi](/help/sites-deploying/configuring-osgi.md) eingesetzt werden. Formulare, die Sie für die AEM Forms-App aktivieren und veröffentlichen, stehen in der App zur Verfügung.

Die Formulare werden in Ihre App heruntergeladen und sind offline verfügbar. Angenommen, Sie haben ein Bankgeschäft und ein Kunde füllt auf Ihrer Website einen Antrag aus. Der Antrag ist ein adaptives Formular, das Informationen von Ihren Kunden akzeptiert und zur Überprüfung speichert. Der Administrator überprüft das Formular und erstellt ein Überprüfungsformular in AEM Autoreninstanz. Der Administrator aktiviert die Synchronisierung des Formulars mit der AEM Forms-App und veröffentlicht es. Wenn das Überprüfungsformular in der AEM Forms-App verfügbar ist, kann Ihr Außendienstmitarbeiter die Kundendetails mithilfe eines Mobilgeräts überprüfen. Das Mobilgerät wird mit dem Server synchronisiert und das Überprüfungsformular wird in die App geladen. Ihr Außendienstmitarbeiter kann Ihren Kunden besuchen, die Details überprüfen, Daten als Entwurf speichern oder das Überprüfungsformular übermitteln. Das Formular wird mit dem Server synchronisiert, sobald die App online ist.

Formular in der AEM Forms-App synchronisieren

1. Wählen Sie in der Autoreninstanz ein Formular aus und klicken Sie auf **[!UICONTROL Eigenschaften anzeigen]**.

1. Klicken Sie auf der Eigenschaftenseite auf **[!UICONTROL Erweitert]**.
1. Aktivieren Sie unter &quot;Erweitert&quot;die Option: **[!UICONTROL Mit AEM Forms App synchronisieren]** und wählen **[!UICONTROL Speichern]**.

Wenn das Formular veröffentlicht wird, synchronisiert die App mit dem Server und ruft das Formular ab. Um mehrere Formulare zu synchronisieren, wählen Sie in der Autoreninstanz mehrere Formulare im Forms Manager aus und wählen Sie **[!UICONTROL Mit AEM Forms App synchronisieren]**.

## Mobilgeräteunterstützung {#mobile-device-support}

Siehe [AEM Forms-App (früher bekannt als Mobile Workspace)](/help/forms/using/aem-forms-jee-supported-platforms.md#aem-forms-workspace-app)

## Hauptfunktionen der AEM Forms-App {#key-features-of-aem-forms-app}

### AEM Forms-App mit AEM Forms-Servern {#aem-forms-app-with-aem-forms-servers}

Sie können Ihre App mit dem AEM Forms-Server synchronisieren und Formulare auf Ihrem Mobilgerät verwenden.

Auf einem AEM Forms-Server können Sie ein Formular einem Startpunkt in einem Workbench-Vorgang und einer AEM Inbox-Anwendung zuordnen. AEM Posteingangsanwendung kann ein adaptives Formular zugeordnet sein. Einem Startpunkt kann ein adaptives Formular, ein HTML5-Formular oder ein Formularsatz zugeordnet sein. Ein Startpunkt kann als Aufgabe gesendet oder die Aufgabe als Entwurf gespeichert werden. Weitere Informationen zu den Unterschieden zwischen einer AEM Inbox-Anwendung und einem Startpunkt finden Sie unter [Aktionen und Funktionen formularzentrierter AEM-Workflows auf OSGi- und AEM Forms-JEE-Workflows](capabilities-osgi-jee-workflows.md).

Bei AEM Forms-Server ohne AEM Forms-Workflow wird ein Formular, das für die Synchronisierung in der App aktiviert ist, in der AEM Forms-App wiedergegeben. Forms sind auf der Registerkarte Forms des Programms verfügbar und können als Entwurf übermittelt oder gespeichert werden. Adaptive Formulare und mobile Formulare werden in der App unterstützt.

1. **Speichern einer Aufgabe oder eines Formulars als Entwurf**

   Mit der Option &quot;Als Entwurf speichern&quot;wird ein Schnappschuss einer Aufgabe oder eines Formulars zusammen mit den ausgefüllten Daten und den im zugehörigen Formular angehängten Dateien gespeichert. Die Entwürfe werden auf dem Mobilgerät gespeichert und für einen späteren Abruf mit dem AEM Forms-Server synchronisiert.

   Siehe [Speichern einer Aufgabe oder eines Formulars als Entwurf](/help/forms/using/save-as-draft.md).

1. **Formular als Vorlage speichern**

   Wenn Benutzer ein Formular ausfüllen, bleiben die Eingaben in einige Felder manchmal gleich. In solchen Fällen können Sie die Felder ausfüllen, für die in jeder Instanz identische Werte erforderlich sind, und das Formular oder den Entwurf als Vorlage speichern. Jedes Mal, wenn Sie eine Instanz der Vorlage erstellen, werden die angegebenen Felder bereits mit den in der Vorlage angegebenen Werten ausgefüllt. Auf diese Weise sparen Sie Zeit und Mühe beim Ausfüllen des Formulars.

   Siehe [Speichern von Formularen als Vorlagen](/help/forms/using/save-forms-and-start-points-as-templates.md).

### Arbeiten mit Aufgaben und Formularen {#working-with-tasks-and-forms}

Sie können Ihre App mit dem AEM Forms Workflow-Server synchronisieren und auf Ihrem Mobilgerät an Aufgaben und Formularen arbeiten.

Eine Aufgabe auf dem Mobilgerät enthält ein adaptives Formular, ein HTML5-Formular oder einen Formularsatz und kann auch Anhänge und eine [Zusammenfassungs-URL](/help/forms/using/getting-task-variables-summary-url.md) enthalten. Standardmäßig werden die Ihnen zugewiesenen Aufgaben im Ordner **[!UICONTROL Tasks]** platziert. Bei der Bearbeitung einer Aufgabe können Sie diese ändern und als Entwurf auf dem AEM Forms-Server speichern.

Ein Formular auf dem Mobilgerät kann ein adaptives Formular oder ein mobiles Formular sein. Forms, das für die Synchronisierung in der Forms-App aktiviert ist, ist im Ordner &quot;Forms&quot;verfügbar. Sie können Formulare synchronisieren, die auf dem AEM Forms-Server ohne AEM Forms-Workflow (AEM Forms unter OSGi) aktiviert sind.

Siehe:

* [Öffnen einer Aufgabe](/help/forms/using/open-task.md)
* [Arbeiten mit einem Formular](/help/forms/using/working-with-form.md)

### Offline arbeiten {#working-offline}

Sie können auf Ihrem Mobilgerät im Offline-Modus arbeiten. Sie können sich bei der Anwendung anmelden, auch wenn keine Netzwerkverbindung besteht, und alle Formulare bearbeiten, die mit dem Gerät synchronisiert wurden, als Sie zuletzt online waren. Weitere Informationen zum Synchronisieren der Formulare erhalten Sie unter [Synchronisieren der App](/help/forms/using/sync-app.md). Wenn Sie die Anlagen, die mit einem Formular verbunden sind, synchronisieren, können Sie die Anlagen ebenfalls im Offline-Modus öffnen. Sie können im Offline-Modus das Formular bearbeiten, Anmerkungen hinzufügen und ein Formular senden oder speichern. Das Formular wird mit dem AEM Forms-Server synchronisiert, wenn Sie das nächste Mal online sind.

Weitere Informationen finden Sie unter [Arbeiten im Offline-Modus](/help/forms/using/work-offline-mode.md).

### Hinzufügen von Anmerkungen {#adding-annotations}

Sie können die folgenden Anhänge zu einem Formular auf Ihrem Mobilgerät hinzufügen

* **Anmerkungen**: Mithilfe der Funktion „Anmerkungen“ können Sie Freihand-Scribbles oder Textanmerkungen zum Formular hinzufügen. Weitere Informationen finden Sie unter [Notizen hinzufügen](/help/forms/using/add-attachments.md#adding-a-note).

* **Bild**: In der Mobile App von AEM Forms steht eine Funktion zur Verfügung, über die Sie die Kamerafunktion oder die Galerie Ihres Mobilgeräts nutzen können. Mit dem Fotoanhang können Sie dem zugehörigen Formular ein Foto hinzufügen. Weitere Informationenfinden Sie unter [Hinzufügen eines Fotos](/help/forms/using/add-attachments.md#adding-a-photograph).

### Automatische Speicherung {#autosave}

Wenn ein Benutzer Daten in die AEM Forms-App eingibt, speichert die Funktion sie in regelmäßigen Abständen. Die Funktion zum automatischen Speichern in der AEM Forms-App hilft Ihnen, Datenverlust zu vermeiden, wenn die App aufgrund von Bedingungen wie niedrigem Akku geschlossen wird.

Weitere Informationen finden Sie unter [Verwenden der automatischen Speicherung in der AEM Forms-App](/help/forms/using/autosave-data-app.md).

## Unterschiede zwischen den Funktionen von AEM Inbox und AEM Forms-App {#differences-between-aem-inbox-and-aem-forms-app-features}

Zwei der bekanntesten Möglichkeiten zum Starten eines formularbasierten Workflows sind der [AEM-Posteingang](/help/forms/using/manage-applications-inbox.md) und die Mobile App von AEM Forms. Die Funktionen von AEM Inbox und AEM Forms-App sind jedoch unterschiedlich. AEM Posteingang funktioniert nur mit [Forms-orientierte Workflows](/help/forms/using/aem-forms-workflow.md) während die AEM Forms-App sowohl mit Forms-orientierten Workflows als auch mit Prozessverwaltung funktioniert. Weitere Informationen zu den Unterschieden zwischen den Funktionen des AEM-Posteingangs und der Mobile App von AEM Forms finden Sie unter [Aktionen und Funktionen von formularbasierten AEM-Workflows auf OSGi und AEM Forms-JEE-Workflows](capabilities-osgi-jee-workflows.md).

## Unterstützte Formulare {#supported-forms}

Unterstützte Formulartypen in der AEM Forms-App:

### Adaptives Formular {#adaptive-form}

Ein adaptives Formular, das sich dynamisch an Benutzereingaben anpasst, wird in der AEM Forms-App unterstützt. Verzögert geladene adaptive Formulare werden ebenfalls unterstützt.

### Mobile Formular {#mobile-form}

Sie können Formulare für Mobilgeräte in AEM Forms erstellen. Mobile Formulare werden als HTML-Formulare auf Mobilgeräten wiedergegeben, die sich je nach Anzeigegerät anpassen.

### Formularsatz {#formset}

Mit Formularsätzen können mehrere mit einem Dienst oder Prozess verknüpfte Formulare gruppiert werden, um einen Geschäftsprozess zu automatisieren und den Endbenutzern vorzustellen. In einem solchen Szenario können die Benutzer den gesamten Satz als einen Satz ausfüllen und es ist nicht erforderlich, einzelne Formulare oder Prozesse zu archivieren, zu senden und zu verfolgen.

>[!NOTE]
>
>Erfordert AEM Forms Workflow (AEM Forms on JEE).

## Funktionsweise der AEM Forms-App {#how-aem-forms-app-works}

Die Mobile App von AEM Forms ist eine mobile Lösung für Außendienstmitarbeiter zur Arbeit mit Formularen, die ihnen zugewiesen wurden. Das Programm speichert die vollständigen Daten vom Server zwischen und bietet ein effizientes Benutzererlebnis, indem es alle Arbeiten lokal speichert. Die Daten von der Festplatte werden über zeitnahe Synchronisierungsaktualisierungen an den Server gesendet.

Die Mobile App von AEM Forms ist ein PhoneGap 5.0-basiertes Programm, in dem das Backbone-Modell effizient eingesetzt wird, um in den Modellen gespeicherte Daten durch Ansichten darzustellen. Alle nativen Vorgänge werden über PhoneGap-Plug-ins ausgeführt.

## Anpassen, Erstellen und Verteilen der AEM Forms-App {#customize-build-distribute}

>[!NOTE]
>
>Gilt nur, wenn Sie den Quellcode der AEM Forms-App zum Erstellen der App verwenden.

Die Mobile App von AEM Forms lässt sich ganz einfach an die Anforderungen Ihres Unternehmens anpassen. Der Quellcode für die Anwendung wird zusammen mit AEM Forms bereitgestellt. Sie können Änderungen am Quellcode vornehmen und Ihre eigene benutzerdefinierte Mobile Workspace-Lösung erstellen. Sie können die App auch mit Ihrem eigenen Unternehmensschlüssel signieren.

### Anpassen {#customize}

Sie können Ihre App anpassen für:

**Branding**: Ändern Sie das App-Symbol, den App-Namen, Startbilder und Seiten in der AEM Forms-App. Sie können auch den Text ändern, um die App für eine bestimmte Region zu lokalisieren. Weitere Informationen zum Branding der AEM Forms-App finden Sie unter [Branding-Anpassung](/help/forms/using/branding-customization.md).

**Design**: Ändern Sie Stile wie Farben, Schriftarten und Abstände in der Benutzeroberfläche der Mobile App von AEM Forms. Weitere Informationen finden Sie unter [Designanpassung](/help/forms/using/theme-customization.md).

**Geste**: Ändern Sie Gesten wie das Streichen nach rechts und links in der Benutzeroberfläche der Mobile App von AEM Forms. Weitere Informationen finden Sie unter [Gestenanpassung](/help/forms/using/gesture-customization.md).

Weitere Informationen zum Einrichten eines AEM Forms-App-Projekts zur Anpassung finden Sie unter:

* [Einrichten einer Umgebung für die AEM Forms-App](/help/forms/using/setup-environment-mobile-workspace.md)
* [Einrichten des Visual Studio-Projekts und Erstellen der Windows-App](/help/forms/using/setup-visual-studio-project-build-installer.md)
* [Einrichten des Xcode-Projekts und Erstellen der iOS-App](/help/forms/using/setup-xcode-project-build-installer.md)
* [Einrichten des Eclipse-Projekts und Erstellen der Android-App](/help/forms/using/setup-eclipse-project-build-installer.md)

### Pakete erstellen und bereitstellen {#build-and-distribute}

Der Quell-Code für die Mobile App von AEM Forms kann aus der Datei `adobe-lc-mobileworkspace-src.zip` extrahiert werden, die als Teil des Quellpakets der Mobile App von AEM Forms auf Software Distribution verfügbar ist.

Um die AEM Forms App-Quelle zu erhalten, führen Sie die folgenden Schritte aus:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Auswählen **[!UICONTROL Adobe Experience Manager]** im Kopfzeilenmenü verfügbar.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]** aus.
   2. Wählen Sie die Version aus und geben Sie sie für das Paket ein. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Wählen Sie den für Ihr Betriebssystem zutreffenden Paketnamen aus und wählen Sie **[!UICONTROL EULA-Bedingungen akzeptieren]** und wählen Sie **[!UICONTROL Herunterladen]**.
1. Öffnen Sie [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

**Für iOS**:

Weitere Informationen zum Erstellen einer iOS-App (.ipa) finden Sie unter [Einrichten des Xcode-Projekts und Erstellen der iOS-App](/help/forms/using/setup-xcode-project-build-installer.md).

Einzelheiten zum Signieren der Mobile App von AEM Forms mit Ihrem Bereitstellungsprofil finden Sie unter [Einrichtung, Prozess und Fehlerbehebung für iOS Code Signing](https://developer.apple.com/support/code-signing/).

**Android**:

Weitere Informationen zum Erstellen einer Android-App (.apk), finden Sie unter [Einrichten des Eclipse-Projekts und Erstellen der Android-App](/help/forms/using/setup-eclipse-project-build-installer.md).

Weitere Informationen zum Signieren der Mobile App von AEM Forms finden Sie unter [Signieren Ihrer Programme](https://developer.android.com/tools/publishing/app-signing.html).

**Für Windows**:

Weitere Informationen zum Erstellen einer Windows-App (.appx) finden Sie unter [Einrichten des Visual Studio-Projekts und Erstellen der Windows-App](/help/forms/using/setup-visual-studio-project-build-installer.md).

Weitere Informationen zum Verteilen der App über MDM finden Sie unter [Verteilen der AEM Forms-App](/help/forms/using/distribute-mobile-workspace-app.md). App-Verteilung über MDM gilt nur für iOS und Android.

## Recommendations aktualisiert Mobile Workspace auf AEM Forms-App {#recommendations-to-upgrade-mobile-workspace-to-aem-forms-app}

Wenn Sie auf die neueste Version des AEM Forms-Programms aktualisieren, sollten Sie die folgenden Punkte lesen:

* **Wenn Sie eine frühere Version der App vom Play Store auf Android installiert haben** können Sie die App direkt vom Play Store aktualisieren.

* **Wenn eine frühere Version der Mobile App mithilfe des Quell-Codes erstellt und installiert wird (gilt für iOS und Android)**:

  Synchronisieren Sie vor der Installation der neuen Mobile App alle Ihre Daten mit dem AEM Forms-Server. Nachdem die Daten synchronisiert wurden, müssen Sie frühere Versionen der App und die neue App installieren.
