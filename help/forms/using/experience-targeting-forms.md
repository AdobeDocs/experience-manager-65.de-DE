---
title: Erstellen zielgerichteter Erlebnisse in AEM Forms
seo-title: Erstellen zielgerichteter Erlebnisse in AEM Forms
description: Mithilfe von AEM Forms können Sie personalisierte Erlebnisse für bestimmte Zielgruppen bieten.
seo-description: Mithilfe von AEM Forms können Sie personalisierte Erlebnisse für bestimmte Zielgruppen bieten.
uuid: 174b6054-8fe3-4ab2-8afd-435e5dff9044
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
discoiquuid: 6cf54a08-d429-4a58-8429-a1cb784448d1
translation-type: tm+mt
source-git-commit: 9d90bc5f77f827925e3e1ecd12d56a94a2bbae30
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 32%

---


# Erstellen zielgerichteter Erlebnisse in AEM Forms {#create-targeted-experiences-in-aem-forms}

## Adobe Target mit AEM Forms integrieren {#integrate-adobe-target-with-aem-forms}

Durch die Integration von Adobe Target mit AEM können Sie die personalisierte Erlebnisse für bestimmte Zielgruppen erstellen. Mit Adobe Target können Sie A/B-Tests erstellen, Benutzerreaktionen messen und personalisierte Web-Inhalte für die anzusprechenden Benutzer generieren. Sie können Adobe Target in AEM Forms integrieren, um Bildkomponenten adaptiver Formulare und interaktive Zielgruppen zu erstellen.

Konfigurieren Sie Adobe Target in AEM, um es mit adaptiven Formularen und interaktiven Kommunikationen zu verwenden, siehe [Erstellen einer Zielgruppe-Konfiguration in AEM](/help/sites-administering/target.md) und [Hinzufügen Framework](/help/sites-administering/target.md).

>[!NOTE]
>
>Targeting funktioniert, wenn Ihr adaptives Formular oder Ihre interaktive Kommunikation mit einem Hostnamen oder einer IP-Adresse wiedergegeben wird. Es schlägt fehl, wenn Ihr adaptives Formular oder Ihre interaktive Kommunikation mit localhost wiedergegeben wird.

## Target- Aktivität erstellen {#creating-a-target-activity}

1. Tippen Sie auf **Adobe Experience Manager > Personalization > Aktivitäten**.

   `https://<hostname>:<port>/libs/cq/personalization/touch-ui/content/v2/activities.html`

1. Tippen Sie auf der Seite &quot;Aktivitäten&quot;auf **Erstellen > Marke erstellen**.
1. Sie werden aufgefordert, eine Vorlage auswählen und Eigenschaften einzugeben.

   Wählen Sie eine Vorlage aus und tippen Sie auf **Weiter.** Geben Sie im Abschnitt Eigenschaften den Titel Ihrer Marke ein und tippen Sie auf  **Erstellen.**
Ihre Marke wird jetzt auf der Seite &quot;Aktivitäten&quot;aufgeführt.

1. Tippen Sie auf der Seite „Aktivitäten“ auf Ihre Marke.
1. Tippen Sie im Bereich Ihrer Marke Übergeordnet auf **Erstellen** > **Aktivität erstellen**.

   Beim Erstellen einer Aktivität geben Sie deren Details, Ziel und Einstellungen an.

   Der Detailbereich enthält den Namen, die Targeting-Engine und die Zielsetzung. Wenn Sie Adobe Target als Targeting-Engine wählen, wird die Option für die Target-Cloud-Konfiguration aktiviert. Wählen Sie die Cloud-Konfiguration für Ihre Zielgruppe aus, wählen Sie den Typ der Aktivität, geben Sie das Ziel der Aktivität an und tippen Sie auf **Weiter**. Interaktive Kommunikation unterstützt nur den Erlebnis-Targeting-Aktivitäten-Typ.

   Im Abschnitt „Target“ können Sie das Erlebnis für die Zielgruppe hinzufügen und benennen. Klicken Sie auf **Hinzufügen Erlebnis**, um die Optionen **Audience** und **Erlebnis benennen** zu aktivieren. Tippen Sie auf **Audience** auswählen, um eine Liste der Audiencen und deren Quelle anzuzeigen. Wählen Sie eine Zielgruppe aus der Liste „Zielgruppenname“ aus. Tippen Sie auf **Hinzufügen Erlebnis**, um das Erlebnis zu benennen, und tippen Sie auf **Weiter**.

   Im Abschnitt „Ziele und Einstellungen“ können Sie den Zeitplan und die Priorität für Ihre Aktivität festlegen. Legen Sie Datum, Enddatum und Priorität des Beginns der Aktivität, Zielmetrik und zusätzliche Metrik fest und tippen Sie auf **Speichern**.

   Die Aktivität wird jetzt in Ihrer Markenseite aufgeführt.

   >[!NOTE]
   >
   >Sie können die Fehlermeldung &quot;Ihre Aktivität wurde gespeichert, aber nicht mit der Zielgruppe synchronisiert. Grund: Das folgende Erlebnis hat keine Angebote&quot;, wenn es beim Speichern der Aktivität aufgetreten ist.

1. Um die Zielgruppe zu aktivieren, bearbeiten Sie die JSP-Datei, um Clientbibliotheken einzuschließen, die Ihre Vorlage für adaptive Formulare verwendet.

   Klicken Sie beispielsweise in der vordefinierten Implementierung auf **Tools** > **CRXDE Lite**.

   Geben Sie in der Adressleiste der CRXDE Lite /libs/fd/af/components/page/base/head.jsp ein, um die Datei head.jsp zu bearbeiten.

   Diese Implementierung verwendet die Vorlage simpleEnrollment. In dieser Implementierung müssen Sie die Datei head.jsp wie folgt ändern und dabei die folgenden Clientbibliotheken aufnehmen:

   `<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>`

   `<cq:include path="clientcontext_optimized" resourceType="/libs/cq/personalization/components/clientcontext_optimized"/>`

   `<cq:include path="config" resourceType="cq/personalization/components/clientcontext_optimized/config"/>`

1. Um das Zielgruppe-Framework für adaptive Formulare zu aktivieren, navigieren Sie zu Ihrem Formular oder zu Ihrer interaktiven Kommunikation und öffnen Sie es im Bearbeitungsmodus.

   Um ein Formular oder eine interaktive Kommunikation im Bearbeitungsmodus zu öffnen, tippen Sie auf **Wählen Sie** und dann auf **Öffnen**.

   Alternativ dazu werden vier Schaltflächen angezeigt, wenn Sie den Mauszeiger über das Formular- oder interaktive Kommunikationssymbol bewegen, ohne es auszuwählen. Sie können auf die angezeigte Schaltfläche **Bearbeiten** tippen, um das Formular im Bearbeitungsmodus zu öffnen.

1. Tippen Sie in der Seitensymbolleiste auf **Seiteninformationen** ![Themenoptionen](assets/theme-options.png) > **Eigenschaften öffnen**.
1. Wählen Sie auf der Registerkarte &quot;Allgemein&quot;eine Konfiguration für das Feld **Adobe Target**. Tippen Sie auf **Speichern und Schließen**.

## Anwenden der erstellten Aktivität auf ein adaptives Formularbild oder ein interaktives Kommunikationsbild {#applying-created-activity-to-an-adaptive-form-image-or-an-interactive-communication-image}

1. Öffnen Sie das adaptive Formular und die interaktive Kommunikation zur Bearbeitung. Wenn Sie eine interaktive Kommunikation öffnen, öffnen Sie den Web Kanal.

1. Fügen Sie im Bearbeitungsmodus Ihrer interaktiven Kommunikation oder Ihres adaptiven Formulars ein Bild hinzu, das als Ziel dienen soll.

   >[!NOTE]
   >
   >AEM Forms unterstützt nur Targeting von Bildkomponenten. Stellen Sie sicher, dass das Bedienfeld, in dem sich die Bildkomponente befindet, keine andere Komponente enthält und die Spaltenanzahl für das Bedienfeld auf 1 eingestellt ist.

1. Wechseln Sie von **Bearbeiten** in **Targeting**-Modus. Die Option zum Wechseln der Modi befindet sich in der oberen rechten Ecke.
1. Wählen Sie eine **MARKEN**, wählen Sie **AKTIVITÄT** und tippen Sie auf **Beginn-Targeting**. Das Menü **Audiencen** wird rechts im Editor angezeigt.

   ![targeting-menu](assets/targeting-menu.png)

1. Wählen Sie eine Audience aus dem Menü **Audiencen** und tippen Sie auf das Bild zur Zielgruppe. Ein Menü wird angezeigt. Tippen Sie im Menü auf **Zielgruppe**. Tippen Sie auf das Bild und dann auf **Konfigurieren**. Wählen Sie im Eigenschaftenfenster das für die ausgewählte Audience anzuzeigende Bild aus. Wiederholen Sie den Schritt für alle Audiencen. Das Erlebnis-Targeting ist für das Bild in der interaktiven Kommunikation oder im adaptiven Formular aktiviert.

## Überprüfen Sie, ob die erstellte Aktivität mit dem Target-Server synchronisiert wird.{#check-if-the-created-activity-syncs-with-the-target-server}

Aktivitäten, die für das Targeting verwendet werden, werden mit dem Target-Server synchronisiert. Um zu überprüfen, ob Ihre Aktivität mit dem Zielserver synchron ist, überprüfen Sie den Status Ihrer Aktivität auf Ihrer Markenseite.

Vergewissern Sie sich, dass die Aktivität den Status „Synchronisiert“ aufweist.

## Target-Verhalten validieren {#validate-target-behavior}

Target-Verhalten validieren:

* Targeting mit `wcmmode preview` im Autorenmodus verwenden
* Verwenden Sie das Targeting mit `wcmmode preview` und `wcmmode disabled` im Veröffentlichungsmodus.

## Targeting für die Bildkomponente überwachen {#monitor-targeting-for-the-image-component}

Um das Targeting für Bildkomponenten in Ihrem Formular zu überwachen, veröffentlichen Sie Ihre Bilder und Aktivitäten sowie das adaptive Formular.

## Offene Probleme {#open-issues}

Ausdruck für die Sichtbarkeit: Festlegen des Fokus schläft für Targeting-Bilder auf adaptiven Formularen fehl.
