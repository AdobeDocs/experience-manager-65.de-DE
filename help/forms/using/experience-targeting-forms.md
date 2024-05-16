---
title: Erstellen zielgerichteter Erlebnisse in AEM Forms
description: Mithilfe von Target können Sie in AEM Forms personalisierte Erlebnisse für bestimmte Zielgruppen erstellen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
exl-id: fdc91054-3f7e-4cbf-bdfa-7d7a621747f1
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '840'
ht-degree: 100%

---

# Erstellen zielgerichteter Erlebnisse in AEM Forms {#create-targeted-experiences-in-aem-forms}

## Integrieren von Adobe Target in AEM Forms {#integrate-adobe-target-with-aem-forms}

Durch die Integration von Adobe Target mit AEM können Sie die personalisierte Erlebnisse für bestimmte Zielgruppen erstellen. Mit Adobe Target können Sie A/B-Tests erstellen, Benutzerreaktionen messen und personalisierte Web-Inhalte für die anzusprechenden Benutzer generieren. Sie können Adobe Target in AEM Forms integrieren, um Bildkomponenten adaptiver Formulare und interaktiver Kommunikation auszuwählen.

Informationen zum Konfigurieren von Adobe Target in AEM für die Verwendung mit adaptiven Formularen und interaktiver Kommunikation finden Sie unter [Erstellen einer Target-Konfiguration in AEM](/help/sites-administering/target.md) und [Framework hinzufügen](/help/sites-administering/target.md).

>[!NOTE]
>
>Targeting ist möglich, wenn das adaptive Formular oder die interaktive Kommunikation über einen Hostnamen oder eine IP-Adresse wiedergegeben wird. Es schlägt fehl, wenn das adaptive Formular über localhost wiedergegeben wird.

## Erstellen einer Target- Aktivität {#creating-a-target-activity}

1. Wählen Sie **Adobe Experience Manager > Personalisierung > Aktivitäten** aus.

   `https://<hostname>:<port>/libs/cq/personalization/touch-ui/content/v2/activities.html`

1. Wählen Sie auf der Seite „Aktivitäten“ die Optionen **Erstellen > Marke erstellen** aus.
1. Sie werden aufgefordert, eine Vorlage auswählen und Eigenschaften einzugeben.

   Wählen Sie eine Vorlage aus und dann **Weiter.** Geben Sie den Titel Ihrer Marke im Abschnitt „Eigenschaften“ ein und wählen Sie **Erstellen.**
Ihre Marke wird jetzt auf der Seite „Aktivitäten“ aufgeführt. 

1. Wählen Sie Ihre Marke auf der Seite „Aktivitäten“ aus.
1. Wählen Sie unter „Primäres Gebiet“ für Ihre Marke die Optionen **Erstellen** > **Aktivität erstellen** aus.

   Beim Erstellen einer Aktivität geben Sie deren Details, Ziel und Einstellungen an.

   Der Abschnitt „Details“ enthält den Namen, die Targeting-Engine und die Vorgabe. Wenn Sie Adobe Target als Targeting-Engine auswählen, wird die Option für die Target-Cloud-Konfiguration aktiviert. Wählen Sie Ihre Target-Cloud-Konfiguration aus, geben Sie die Zielsetzung der Aktivität ein und wählen Sie **Weiter** aus. Interaktive Kommunikation unterstützt nur den Aktivitätstyp Erlebnis-Targeting.

   Im Abschnitt „Target“ können Sie das Erlebnis für die Zielgruppe hinzufügen und benennen. Klicken Sie auf **Erlebnis hinzufügen**, um die Optionen **Zielgruppe auswählen** und **Erlebnis benennen** zu aktivieren. Wählen Sie **Zielgruppe wählen** aus, um eine Liste der Zielgruppen und ihrer Quelle anzuzeigen. Wählen Sie eine Zielgruppe aus der Liste „Zielgruppenname“ aus. Wählen Sie erst **Erlebnis hinzufügen** aus, um das Erlebnis zu benennen, und dann **Weiter**.

   Im Abschnitt „Ziele und Einstellungen“ können Sie den Zeitplan und die Priorität für Ihre Aktivität festlegen. Legen Sie das Start- und Enddatum, die Priorität für die Aktivität, die Zielmetrik sowie weitere Metriken fest und wählen Sie **Speichern** aus.

   Die Aktivität wird jetzt auf Ihrer Markenseite aufgeführt.

   >[!NOTE]
   >
   >Sie können folgenden Fehler ignorieren: „Ihre Aktivität wurde gespeichert, aber nicht mit Target synchronisiert. Grund: Das folgende Erlebnis enthält keine Angebote“, wenn er beim Speichern der Aktivität auftritt.

1. Um Target zu aktivieren, bearbeiten Sie die.jsp-Datei, wobei Sie die Client-Bibliotheken aufnehmen, die von Ihrer Vorlage für adaptive Formulare verwendet werden.

   In der standardmäßig verfügbaren Implementierung müssten Sie beispielsweise **Tools** > **CRXDE Lite** wählen.

   Geben Sie in die Adressleiste von CRXDE Lite /libs/fd/af/components/page/base/head.jsp ein, um die Datei head.jsp zu bearbeiten.

   Für diese Implementierung wird die Vorlage „simpleEnrollment “ verwendet. In dieser Implementierung müssen Sie die Datei head.jsp wie folgt ändern und dabei die folgenden Client-Bibliotheken aufnehmen:

   `<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>`

   `<cq:include path="clientcontext_optimized" resourceType="/libs/cq/personalization/components/clientcontext_optimized"/>`

   `<cq:include path="config" resourceType="cq/personalization/components/clientcontext_optimized/config"/>`

1. Um das Target-Framework für adaptive Formulare zu aktivieren, navigieren Sie zu Ihrem Formular oder zu der interaktiven Kommunikation und öffnen Sie es bzw. sie im Bearbeitungsmodus.

   Um ein Formular oder eine interaktive Kommunikation im Bearbeitungsmodus zu öffnen, wählen Sie **Auswählen** und dann **Öffnen** aus.

   Alternativ werden vier Schaltflächen angezeigt, wenn Sie den Mauszeiger über das Symbol für das Formular oder die interaktive Kommunikation bewegen, ohne es auszuwählen. Sie können die angezeigte Schaltfläche **Bearbeiten** auswählen, um das Formular im Bearbeitungsmodus zu öffnen.

1. Wählen Sie in der Seitensymbolleiste die Optionen **Seiteninformationen** ![theme-options](assets/theme-options.png) > **Eigenschaften öffnen** aus.
1. Wählen Sie auf der Registerkarte „Allgemein“ eine Konfiguration für das Feld **Adobe Target**. Klicken Sie auf **Speichern und schließen**.

## Anwenden der erstellten Aktivität auf ein Bild eines adaptiven Formulars oder einer interaktiven Kommunikation {#applying-created-activity-to-an-adaptive-form-image-or-an-interactive-communication-image}

1. Öffnen Sie das adaptive Formular und die interaktive Kommunikation zum Bearbeiten. Wenn Sie eine interaktive Kommunikation öffnen, öffnen Sie den Web-Kanal.

1. Fügen Sie im Bearbeitungsmodus Ihrer interaktiven Kommunikation oder Ihres adaptiven Formulars ein Bild hinzu, das als Ziel ausgewählt werden soll.

   >[!NOTE]
   >
   >AEM Forms unterstützt nur Zielgruppenbestimmung von Bildkomponenten. Stellen Sie sicher, dass das Bedienfeld, in dem sich die Bildkomponente befindet, keine andere Komponente enthält und die Anzahl der Spalten für das Bedienfeld auf 1 eingestellt ist.

1. Von **Bearbeiten** zu **Targeting**-Modus wechseln. Die Option zum Wechseln der Modi befindet sich oben rechts.
1. Wählen Sie eine **MARKE** aus, wählen Sie eine **AKTIVITÄT** aus und wählen Sie dann **Zielgruppenbestimmung starten**. Das **Zielgruppen**-Menü wird auf der rechten Seite des Editors angezeigt.

   ![Zielgruppenbestimmungs-Menü](assets/targeting-menu.png)

1. Wählen Sie eine Zielgruppe aus dem Menü **Zielgruppen** aus und wählen Sie das gewünschte Bild. Ein Menü wird angezeigt. Wählen Sie im Menü **Target** aus. Wählen Sie das Bild und dann **Konfigurieren** aus. Wählen Sie im Eigenschaftenfenster das Bild aus, das für die ausgewählte Zielgruppe angezeigt werden soll. Wiederholen Sie den Schritt für alle Zielgruppen. Das Experience-Targeting ist für das Bild in der interaktiven Kommunikation oder im adaptiven Formular aktiviert.

## Überprüfen Sie, ob die erstellte Aktivität mit dem Target-Server synchronisiert wird. {#check-if-the-created-activity-syncs-with-the-target-server}

Aktivitäten, die für das Targeting verwendet werden, werden mit dem Target-Server synchronisiert.  Um zu überprüfen, ob Ihre Aktivität mit dem Target-Server synchron ist, überprüfen Sie den Status Ihrer Aktivität auf Ihrer Markenseite.

Vergewissern Sie sich, dass die Aktivität den Status „Synchronisiert“ aufweist.

## Validieren des Target-Verhaltens {#validate-target-behavior}

So validieren Sie das Target-Verhalten:

* Verwenden Sie Targeting mit `wcmmode preview`-Vorschau im Autor-Modus.
* Verwenden Sie Targeting mit `wcmmode preview` und `wcmmode disabled` im Veröffentlichungsmodus

## Targeting für die Bildkomponente überwachen {#monitor-targeting-for-the-image-component}

Um das Targeting für Bildkomponenten in Ihrem Formular zu überwachen, veröffentlichen Sie Ihre Bilder, Aktivitäten, sowie das adaptive Formular.

## Offene Probleme {#open-issues}

Ausdruck für die Sichtbarkeit: Festlegen des Fokus schlägt für Targeting-Bilder auf adaptiven Formularen fehl.
