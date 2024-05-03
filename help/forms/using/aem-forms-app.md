---
title: AEM Forms-App
description: Die AEM Forms-App ermöglicht es Ihren Außendienstmitarbeitenden, adaptive Formulare auf Mobilgeräten zu verwenden.
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 171754a2-1ba5-42dc-b6d2-3d730807cc31
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '2410'
ht-degree: 100%

---

# Einführung in die AEM Forms Workspace-App {#aem-forms-app}

## Übersicht {#overview}

Die AEM Forms-App ermöglicht die Synchronisierung adaptiver Formulare, mobiler Formulare sowie von Formularsätzen auf Mobilgeräten je nach Ihrem Server. Sie können Workflows definieren, die [formularzentrierte Workflows auf OSGi](/help/forms/using/aem-forms-workflow.md) oder Formular-Workflows auf JEE sind. Angenommen, Sie führen eine Bank und nutzen AEM Forms für die Verwaltung von Kundschafts-Anträgen und der Kommunikation mit der Kundschaft. Ihre Kundinnen und Kunden füllen ein Formular aus und übermitteln es zur Prüfung. Wenn Sie das Formular für Mobilgeräte aktivieren, können es Ihre Kundinnen und Kunden in der AEM Forms-App ausfüllen. Sie können darüber hinaus den Überprüfungs-Workflow verwalten, indem Sie das Überprüfungsformular für Mobilgeräte aktivieren. Ihre Außendienstmitarbeitenden können ein Mobilgerät zum Kundenstandort mitnehmen, die Details überprüfen und das Formular übermitteln. Die AEM Forms-App wird mit dem AEM Forms-Server synchronisiert und ruft die Formulare ab, die für Mobilgeräte aktiviert wurden. Wenn die App offline ist, speichert sie die Daten lokal.

Der Quellcode der AEM Forms-App ist für Kunden über die Software Distribution verfügbar. Das Paket mit dem Quell-Code steht in Software Distribution zur Verfügung als `adobe-aemfd-forms-app-src-pkg-<version>.zip`.

Die AEM Forms-App wird auf iOS-, Android- und Windows-Geräten unterstützt. Sie können die Mobile App von AEM Forms für Android über Google Play, für iOS über den App Store und für Windows über den Windows Store installieren.

    [ ![google_play](assets/google_play.png)](https://play.google.com/store/apps/details?id=com.adobe.aem.forms)
    
    [ ![app_store](assets/app_store.png)](https://itunes.apple.com/us/app/adobe-experience-manager-forms/id1129625976?ls=1&amp;mt=8)
    
    [ ![microsoft-badge-icon](assets/microsoft-badge-icon.png)](https://www.microsoft.com/en-us/store/p/adobe-experience-manager-forms/9nd12rlxtgtt)

Informationen zum Installieren, Anpassen und Verteilen der App auf iOS-, Android- oder Windows-Geräten finden Sie unter [Anpassen, Erstellen und Verteilen der AEM Forms-App](#customize-build-distribute).

## Voraussetzungen {#prerequisites}

Die AEM Forms-App erfordert einen AEM Forms-Server. Benutzer können Formulare wiedergeben, die Sie im AEM Forms-Server erstellt haben, sie ausfüllen, als Entwürfe speichern und senden. Die App stellt eine Verbindung zum Server her und ruft aktivierte Formulare ab. Die AEM Forms-App wird mit dem Server synchronisiert, und sobald Formulare in der App geladen werden, können Benutzende im Offline-Modus arbeiten. Wenn die App offline ist, werden die Daten auf dem Gerät gespeichert. Die Daten werden mit dem Server synchronisiert, wenn die App wieder online ist.

### AEM Forms-App bei Servern mit AEM Forms Workflow {#aem-forms-app-with-servers-using-aem-forms-workflow}

Wenn Sie über einen AEM Forms Workflow-Server verfügen, können Sie Formulare als Aufgaben in der AEM Forms-App rendern. Angenommen, Sie führen eine Bank und eine Kundin oder ein Kunde füllt einen Antrag aus, weil sie oder er Ihre Dienstleistungen in Anspruch nehmen möchte. Der Antrag ist ein adaptives Formular, in das Ihre Kundinnen und Kunden Daten eingeben, die gespeichert und dann zur Prüfung übermittelt werden. Die oder der Admin prüft den Antrag und sendet eine Überprüfungsanfrage an die Außendienstmitarbeitende oder den Außendienstmitarbeitenden. Der weitergeleitete Antrag aktiviert in der App der oder des Außendienstmitarbeitenden ein Überprüfungsformular als Aufgabe. Ihr Außendienstmitarbeiter nimmt das Mobilgerät zum Kundenstandort mit und überprüft die Angaben.

### AEM Forms-App bei Servern mit formularzentrierten Workflows in OSGi {#aem-forms-app-with-servers-using-forms-centric-workflow-on-osgi}

Wenn Sie über einen AEM Forms-Server verfügen, können Sie adaptive Formulare als AEM-Posteingangs-Anwendung und Aufgaben in der AEM Forms-App rendern. Angenommen, Sie führen eine Bank und eine Kundin oder ein Kunde füllt einen Antrag aus, weil sie oder er Ihre Dienstleistungen in Anspruch nehmen möchte. Der Antrag ist mit einem adaptiven Formular verknüpft, in das Ihre Kundschaft Daten eingibt, die gespeichert und dann zur Prüfung übermittelt werden. Die oder der Admin überprüft die Aufgabe und sendet die genehmigte Überprüfungsanfrage an die Außendienstmitarbeitende bzw. den Außendienstmitarbeitenden. Ihr Außendienstmitarbeiter nimmt das Mobilgerät zum Kundenstandort mit und überprüft die Angaben.

### Eigenständige Formulare oder AEM Forms-App mit Servern ohne AEM Forms Workflow {#standalone-forms-or-aem-forms-app-with-servers-without-aem-forms-workflow}

Ein AEM Forms-Server ohne AEM Forms Workflow entspricht AEM Forms on OSGi oder einem eigenständigen mobilen oder adaptiven Formular. Die AEM Forms-App kann mit Ihrer AEM Forms-Implementierung unter [OSGi](/help/sites-deploying/configuring-osgi.md) eingesetzt werden. Formulare, die Sie für die AEM Forms-App aktivieren und veröffentlichen, stehen in der App zur Verfügung.

Die Formulare werden in Ihre App heruntergeladen und sind offline verfügbar. Angenommen, Sie haben ein Bankgeschäft und ein Kunde füllt auf Ihrer Website einen Antrag aus. Der Antrag ist ein adaptives Formular, in das Ihre Kundschaft Daten einträgt, die dann zur Prüfung gespeichert werden. Die Administratorin oder der Administrator überprüft das Formular und erstellt ein Überprüfungsformular in der AEM-Autoreninstanz. Die oder der Admin aktiviert die Synchronisierung des Formulars mit der AEM Forms-App und veröffentlicht es. Wenn das Überprüfungsformular in der AEM Forms-App verfügbar ist, kann jemand in Ihrem Außendienst die Angaben der Kundin oder des Kunden auf einem Mobilgerät überprüfen. Das Mobilgerät wird mit dem Server synchronisiert und das Überprüfungsformular in der App geladen. Ihre Außendienstmitarbeiterin bzw. Ihr Außendienstmitarbeiter kann die Kundschaft besuchen, die Angaben überprüfen und die Daten als Entwurf speichern oder das Überprüfungsformular übermitteln. Das Formular wird jedes Mal, wenn Ihre App online ist, mit dem Server synchronisiert.

Formular in der AEM Forms-App synchronisieren

1. Wählen Sie in der Autoreninstanz ein Formular aus und klicken Sie auf **[!UICONTROL Eigenschaften anzeigen]**.

1. Klicken Sie auf der Eigenschaftenseite auf **[!UICONTROL Erweitert]**.
1. Aktivieren Sie unter „Erweitert“ die Option **[!UICONTROL Mit AEM Forms-App synchronisieren]** und wählen Sie **[!UICONTROL Speichern]** aus.

Wenn das Formular veröffentlicht ist, synchronisiert sich die App mit dem Server und ruft das Formular ab. Um mehrere Formulare zu synchronisieren, wählen Sie in der Authoring-Instanz mehrere Formulare in Forms Manager und dann **[!UICONTROL Mit AEM Forms-App synchronisieren]** aus.

## Unterstützung für Mobilgeräte {#mobile-device-support}

Siehe [AEM Forms-App (vorher bekannt als Mobile Workspace)](/help/forms/using/aem-forms-jee-supported-platforms.md#aem-forms-workspace-app)

## Hauptfunktionen der AEM Forms-App {#key-features-of-aem-forms-app}

### AEM Forms-App bei AEM Forms-Servern {#aem-forms-app-with-aem-forms-servers}

Sie können Ihre App mit dem AEM Forms-Server synchronisieren und auf Ihrem Mobilgerät Formulare bearbeiten.

Auf einem AEM Forms-Server können Sie ein Formular einem Startpunkt in einem Workbench-Vorgang und einer AEM Inbox-Anwendung zuordnen. Einer AEM-Posteingangs-Anwendung kann ein adaptives Formular zugeordnet werden. Einem Startpunkt kann ein adaptives Formular, ein HTML5-Formular oder ein Formularsatz zugeordnet werden. Es ist möglich, einen Startpunkt als Aufgabe zu senden oder die Aufgabe als Entwurf zu speichern. Weitere Informationen zu den Unterschieden zwischen einer AEM Inbox-Anwendung und einem Startpunkt finden Sie unter [Aktionen und Funktionen formularzentrierter AEM-Workflows auf OSGi- und AEM Forms-JEE-Workflows](capabilities-osgi-jee-workflows.md).

Bei AEM Forms-Servern ohne AEM Forms Workflow werden Formulare, für die die Synchronisierung in der App aktiviert ist, in der AEM Forms-App gerendert. Formulare sind auf der Registerkarte „Formulare“ der App verfügbar und können gesendet oder als Entwurf gespeichert werden. In der App werden adaptive und mobile Formulare unterstützt.

1. **Speichern einer Aufgabe oder eines Formulars als Entwurf**

   Mit der Option „Als Entwurf speichern“ wird ein Schnappschuss einer Aufgabe bzw. eines Formulars zusammen mit den eingegebenen Daten und den im zugehörigen Formular angehängten Dateien gespeichert. Die Entwürfe werden auf dem Mobilgerät gespeichert und mit dem AEM Forms-Server für den späteren Abruf synchronisiert.

   Siehe [Speichern einer Aufgabe oder eines Formulars als Entwurf](/help/forms/using/save-as-draft.md).

1. **Speichern eines Formulars als Vorlage**

   Wenn Benutzende ein Formular ausfüllen, müssen Eingaben in bestimmten Feldern manchmal unbedingt übereinstimmen. In solchen Fällen können Sie die Felder ausfüllen, für die in allen Instanzen dieselben Werte benötigt werden, und das Formular bzw. den Entwurf als Vorlage speichern. Danach sind die angegebenen Felder jedes Mal, wenn Sie eine Instanz der Vorlage erstellen, bereits mit den Werten aus der Vorlage ausgefüllt. Dies spart Zeit und Mühe beim Ausfüllen des Formulars.

   Siehe [Speichern von Formularen als Vorlagen](/help/forms/using/save-forms-and-start-points-as-templates.md).

### Arbeiten mit Aufgaben und Formularen {#working-with-tasks-and-forms}

Sie können Ihre App mit dem AEM Forms Workflow-Server synchronisieren und auf Ihrem Mobilgerät Aufgaben und Formulare bearbeiten.

Eine Aufgabe auf dem Mobilgerät enthält ein adaptives Formular, ein HTML5-Formular oder einen Formularsatz und kann auch Anhänge und eine [Zusammenfassungs-URL](/help/forms/using/getting-task-variables-summary-url.md) enthalten. Standardmäßig werden die Ihnen zugewiesenen Aufgaben im Ordner **[!UICONTROL Tasks]** platziert. Bei der Bearbeitung einer Aufgabe können Sie diese ändern und als Entwurf auf dem AEM Forms-Server speichern.

Ein Formular auf einem Mobilgerät kann ein adaptives oder ein mobiles Formular sein. Die für die Synchronisierung aktivierten Formulare in der Forms-App stehen im Formularordner zur Verfügung. Es ist möglich, Formulare zu synchronisieren, die auf einem AEM Forms-Server ohne AEM Forms Workflow (AEM Forms on OSGi) aktiviert sind.

Siehe:

* [Öffnen einer Aufgabe](/help/forms/using/open-task.md)
* [Arbeiten mit einem Formular](/help/forms/using/working-with-form.md)

### Offline arbeiten {#working-offline}

Sie können auf Ihrem Mobilgerät im Offline-Modus arbeiten. Sie können sich bei der Anwendung anmelden, auch wenn keine Netzwerkverbindung besteht, und alle Formulare bearbeiten, die mit dem Gerät synchronisiert wurden, als Sie zuletzt online waren. Weitere Informationen zum Synchronisieren der Formulare erhalten Sie unter [Synchronisieren der App](/help/forms/using/sync-app.md). Wenn Sie die Anlagen, die mit einem Formular verbunden sind, synchronisieren, können Sie die Anlagen ebenfalls im Offline-Modus öffnen. Sie können im Offline-Modus das Formular bearbeiten, Anmerkungen hinzufügen und ein Formular senden oder speichern. Das Formular wird mit dem AEM Forms-Server synchronisiert, wenn Sie das nächste Mal online sind.

Weitere Informationen finden Sie unter [Arbeiten im Offline-Modus](/help/forms/using/work-offline-mode.md).

### Hinzufügen von Anmerkungen {#adding-annotations}

Sie können Formularen auf Ihrem Mobilgerät Folgendes hinzufügen:

* **Anmerkungen**: Mithilfe der Funktion „Anmerkungen“ können Sie Freihand-Scribbles oder Textanmerkungen zum Formular hinzufügen. Weitere Informationen finden Sie unter [Notizen hinzufügen](/help/forms/using/add-attachments.md#adding-a-note).

* **Bild**: In der Mobile App von AEM Forms steht eine Funktion zur Verfügung, über die Sie die Kamerafunktion oder die Galerie Ihres Mobilgeräts nutzen können. Mit dem Fotoanhang können Sie dem zugehörigen Formular ein Foto hinzufügen. Weitere Informationenfinden Sie unter [Hinzufügen eines Fotos](/help/forms/using/add-attachments.md#adding-a-photograph).

### Automatische Speicherung {#autosave}

Wenn Benutzende Daten in die AEM Forms-App eingeben, speichert diese Funktion Änderungen in regelmäßigen Abständen automatisch. Die automatische Speicherung in der AEM Forms-App hilft Ihnen, Datenverluste zu vermeiden, wenn die App unbeabsichtigt geschlossen wird, etwa wegen eines niedrigen Akkustands.

Weitere Informationen finden Sie unter [Verwenden der automatischen Speicherung in der AEM Forms-App](/help/forms/using/autosave-data-app.md).

## Unterschiede zwischen den Funktionen von AEM Inbox und AEM Forms-App {#differences-between-aem-inbox-and-aem-forms-app-features}

Zwei der bekanntesten Möglichkeiten zum Starten eines formularbasierten Workflows sind der [AEM-Posteingang](/help/forms/using/manage-applications-inbox.md) und die Mobile App von AEM Forms. Die Funktionen von AEM Inbox und AEM Forms-App sind jedoch unterschiedlich. Der AEM-Posteingang funktioniert nur mit [formularzentrierten Workflows](/help/forms/using/aem-forms-workflow.md), während die AEM Forms-App sowohl mit formularzentrierten Workflows als auch mit der Prozessverwaltung verwendet werden kann. Weitere Informationen zu den Unterschieden zwischen den Funktionen des AEM-Posteingangs und der Mobile App von AEM Forms finden Sie unter [Aktionen und Funktionen von formularbasierten AEM-Workflows auf OSGi und AEM Forms-JEE-Workflows](capabilities-osgi-jee-workflows.md).

## Unterstützte Formulare {#supported-forms}

Unterstützte Formulartypen in der AEM Forms-App:

### Adaptives Formular {#adaptive-form}

In der AEM Forms-App wird ein adaptives Formular unterstützt, das sich Benutzereingaben dynamisch anpasst. Verzögert geladene adaptive Formulare werden ebenfalls unterstützt.

### Mobiles Formular {#mobile-form}

Sie können in AEM Forms Formulare für Mobilgeräte erstellen. Mobile Formulare werden als HTML-Formulare auf Mobilgeräten gerendert und passen sich an die Anzeige auf dem jeweiligen Gerät an.

### Formularsatz {#formset}

Mit Formularsätzen können mehrere zu einem Dienst oder Prozess gehörige Formulare gruppiert werden, um einen Geschäftsprozess zu automatisieren, und anschließend für die Endbenutzenden bereitgestellt werden. In einem solchen Fall können die Benutzenden den gesamten Formularsatz als einzelnes Formular ausfüllen. Es besteht zudem keine Notwendigkeit, einzelne Formulare oder Prozesse zu archivieren, zu übermitteln oder nachzuverfolgen.

>[!NOTE]
>
>Hierfür ist AEM Forms Workflow (AEM Forms on JEE) erforderlich.

## Funktionsweise der AEM Forms-App {#how-aem-forms-app-works}

Die Mobile App von AEM Forms ist eine mobile Lösung für Außendienstmitarbeiter zur Arbeit mit Formularen, die ihnen zugewiesen wurden. Die Anwendung speichert alle Daten vom Server zwischen und bietet ein effizientes Anwendererlebnis, da die gesamte Arbeit lokal gespeichert wird. Diese Daten auf der Festplatte werden über regelmäßige Synchronisierungs-Updates an den Server gesendet.

Die Mobile App von AEM Forms ist ein PhoneGap 5.0-basiertes Programm, in dem das Backbone-Modell effizient eingesetzt wird, um in den Modellen gespeicherte Daten durch Ansichten darzustellen. Alle nativen Vorgänge werden durch PhoneGap-Plug-ins ausgeführt.

## Anpassen, Erstellen und Verteilen der AEM Forms-App {#customize-build-distribute}

>[!NOTE]
>
>Dies gilt nur, wenn Sie AEM Forms-App-Quell-Code zum Erstellen der App verwenden.

Die Mobile App von AEM Forms lässt sich ganz einfach an die Anforderungen Ihres Unternehmens anpassen. Der Quellcode für die Anwendung wird zusammen mit AEM Forms bereitgestellt. Sie können Änderungen am Quellcode vornehmen und Ihre eigene benutzerdefinierte Mobile Workspace-Lösung erstellen. Sie können die App auch mit Ihrem eigenen Unternehmensschlüssel signieren.

### Anpassen {#customize}

Sie können Ihre App wie folgt anpassen:

**Branding**: Ändern Sie das App-Symbol, den App-Namen, Startbilder und Seiten in der AEM Forms-App. Außerdem können Sie Text ändern, um die App für eine bestimmte Region zu lokalisieren. Weitere Informationen zum Branding der AEM Forms-App finden Sie unter [Branding-Anpassung](/help/forms/using/branding-customization.md).

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
1. Wählen Sie im Kopfzeilenmenü **[!UICONTROL Adobe Experience Manager]** aus.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]** aus.
   2. Wählen Sie die Version aus und geben Sie sie für das Paket ein. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Wählen Sie den für Ihr Betriebssystem zutreffenden Paketnamen, dann **[!UICONTROL EULA-Bedingungen akzeptieren]** und dann **[!UICONTROL Herunterladen]** aus.
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

## Empfehlungen zur Aktualisierung von Mobile Workspace in der AEM Forms-App {#recommendations-to-upgrade-mobile-workspace-to-aem-forms-app}

Wenn Sie auf die neueste Version der AEM Forms-App aktualisieren, achten Sie darauf, dass Sie folgende Punkte lesen:

* **Wenn Sie eine frühere Version der App vom Play Store auf Android installiert haben** können Sie die App direkt vom Play Store aktualisieren.

* **Wenn eine frühere Version der Mobile App mithilfe des Quell-Codes erstellt und installiert wird (gilt für iOS und Android)**:

  Synchronisieren Sie vor der Installation der neuen Mobile App alle Ihre Daten mit dem AEM Forms-Server. Nachdem die Daten synchronisiert wurden, müssen Sie frühere Versionen der App und die neue App installieren.
