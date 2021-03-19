---
title: Verwenden von AEM-Übersetzungs-Workflow zum Lokalisieren von adaptiven Formularen und DoR
seo-title: Verwenden von AEM-Übersetzungs-Workflow zum Lokalisieren von adaptiven Formularen und DoR
description: Erfahren Sie, wie Sie AEM-Übersetzungs-Workflows zum Lokalisieren von adaptiven Formularen und DoR verwenden.
seo-description: Erfahren Sie, wie Sie AEM-Übersetzungs-Workflows zum Lokalisieren von adaptiven Formularen und DoR verwenden.
uuid: 6c87a283-0203-4cf7-989a-3770ddbbbd6e
content-type: reference
topic-tags: develop
discoiquuid: f5642571-9657-4ca1-93c5-4ae2eb91e967
noindex: true
feature: Adaptive Formulare
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 85%

---


# Verwenden von AEM-Übersetzungs-Workflow zum Lokalisieren von adaptiven Formularen und DoR {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

Lokalisierte Formulare helfen Ihnen, eine größere Zielgruppe über Ländergrenzen hinweg anzusprechen. Mit den Adobe Experience Manager-Übersetzungs-Workflows können Sie adaptive Formulare und ihre DoR lokalisieren. Sie können zum Lokalisieren von adaptiven Formularen **maschinelle Übersetzung** nutzen oder **Übersetzer** beauftragen.

In diesem Artikel wird die Vorgehensweise zum Nutzen des AEM-Übersetzungsarbeitsablaufs in Verbindung mit adaptiven Formularen und DoR erläutert.

## Lokalisieren von adaptiven Formulars und DoR mithilfe der maschinellen Übersetzung {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

Der Dienst für maschinelle Übersetzung übersetzt sofort Inhalte Ihrer adaptiven Formulare und DoR. AEM Forms ist für die Verwendung einer Testversion von Microsoft Translator für die maschinelle Übersetzung vorkonfiguriert. Führen Sie zum Aktivieren des Dienstes für Ihre adaptiven Formulare und DoR folgende Schritte durch:

1. Wählen Sie auf der Benutzeroberfläche von AEM Forms ein Formular aus und tippen Sie auf die Option **Wörterbuch hinzufügen**.
1. Wählen Sie auf dem Bildschirm **Wörterbuch zum Übersetzungsprojekt hinzufügen** die Option **Neues Übersetzungsprojekt erstellen** oder **Zu vorhandenem Übersetzungsprojekt hinzufügen**.
1. Geben Sie im Feld **Projekttitel** den Titel an. Beispiel: `Government Reference Site - German locale.`
1. Geben Sie im Feld **Sprachen der Zielgruppe** ein Gebietsschema an (z. B. `German(de)`) und klicken Sie auf **Fertig**. Sie können mehrere Gebietsschemata angeben. Das Formular wird in alle im Feld **Zielsprachen** angegebenen Gebietsschemata übersetzt.
1. Klicken Sie im Dialogfeld „Wörterbuch hinzugefügt“ auf **Projekte öffnen**. Öffnen Sie auf dem Bildschirm „Projekte“ das neu erstellte Projekt.
1. Klicken Sie unten auf der Kachel **Übersetzungszusammenfassung** auf die **Auslassungspunkte**. Der Bildschirm „Übersetzungszusammenfassung“ wird geöffnet.
1. Klicken Sie am oberen Rand des Bildschirms **Übersetzungszusammenfassung** auf das Symbol **Bearbeiten**. Öffnen Sie die Registerkarte **Übersetzung** und wählen Sie auf dem Bildschirm **Übersetzungsmethode** die Option „Maschinelle Übersetzung“. Wählen Sie den entsprechenden **Übersetzungsanbieter** und die entsprechende **Cloud-Konfiguration**. Klicken Sie am oberen Rand des Bildschirms auf das Symbol **Fertig**.
1. Klicken Sie auf der Kachel **Übersetzungsauftrag** auf das Symbol ![aem62forms_downPfeil](assets/aem62forms_downarrow.png) und dann auf **Beginn**. Der Status der Kachel ändert sich in „Entwurf“. Bei Fertigstellung der Übersetzung ändert sich der Status in **Bereit für Überprüfung**. Aktualisieren Sie die Seite nach einigen Minuten und überprüfen Sie den Status.
1. Nachdem der Status auf **Bereit für Überprüfung** auf der Kachel **Übersetzungsauftrag** geändert wurde, öffnen Sie das Formular in einem Browserfenster. Eine lokalisierte Version des Formulars wird angezeigt.

   >[!NOTE]
   >
   >* Stellen Sie vor dem Öffnen der lokalisierten Version des Formulars im Browserfenster sicher, dass das Gebietsschema des Browsers so eingestellt ist, dass es mit dem Gebietsschema des Formulars übereinstimmt. Wenn beispielsweise das Formular in die Sprache Deutsch(de) übersetzt wird, stellen Sie für das Gebietsschema des Browsers „Deutsch(de)“ ein.
   >* Komponenten für adaptive Formulare unterstützen keine RTL-Sprachen (Right to Left). Zum Beispiel Hebräisch.


   Zusammen mit dem adaptiven Formular wird das automatisch generierte DoR auch lokalisiert.

   Weitere Informationen zu Einstellungen und Konfigurationen zu DoR finden Sie unter:

   [Konfiguration von Dokument aus Datensatzvorlage](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

   [Datensatzdokument-Einstellungen](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [Passen Sie die Branding-Informationen des Datensatzdokuments](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) an und stellen Sie sicher, dass das Gebietsschema des Browsers auf die Sprache eingestellt ist, in der Sie das adaptive Formular mithilfe der Maschinensprache lokalisiert haben. Das Browsergebietsschema hilft beim Lokalisieren der Branding-Informationen im Datensatzdokument.
1. Um das lokalisierte Datensatzdokument anzuzeigen, tippen Sie auf „Vorschau generieren“. Das Dokument des PDF-Datensatzes wird in einem neuen Register in Ihrem Browser generiert und geöffnet.

## Lokalisieren von adaptiven Formulars und seines DoR mithilfe professioneller Übersetzung {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

Bei der menschlichen Übersetzung wird der Inhalt an einen Übersetzungsanbieter gesendet und von professionellen Übersetzern übersetzt. Wenn die Inhalte übersetzt wurden, werden sie zurückgesendet und in AEM importiert. Ist Ihr Übersetzungsdienstleister in AEM integriert, werden die Inhalte automatisch von AEM an den Übersetzungsdienstleister gesendet.

Für die Übersetzung wird den professionellen Übersetzern ein Wörterbuch zur Verfügung gestellt, das Dateien im XLIFF-Format enthält. Das Wörterbuch enthält für jedes Gebietsschema eine separate XLIFF-Datei. Jede XLIFF-Datei enthält Text, der den Endbenutzern angezeigt wird, und Platzhalter für den entsprechenden lokalisierten Text.

Führen Sie die folgenden Schritte zum Lokalisieren eines Formulars und seines DoR mit professioneller Übersetzung durch:

1. [Stellen Sie eine Verbindung zwischen AEM und Ihrem Übersetzungsdienstleister her](/help/sites-administering/tc-tic.md) und [erstellen Sie Konfigurationen für die Integration des Übersetzungs-Frameworks](/help/sites-administering/tc-tic.md).

1. [Verknüpfen Sie die Seiten Ihres Sprach-Masters](/help/sites-administering/tc-tic.md) mit dem Übersetzungsdienstleister und den Framework-Konfigurationen.

1. [Identifizieren Sie den Typ des zu übersetzenden ](/help/sites-administering/tc-rules.md) Inhalts.

1. [Bereiten Sie die Inhalte für die Übersetzung vor](/help/sites-administering/tc-prep.md), indem Sie die Sprach-Master und die Stammseiten der Sprachkopien erstellen.

1. [Erstellen Sie Übersetzungsprojekte, ](/help/sites-administering/tc-manage.md) um die zu übersetzenden Inhalte zu sammeln und den Übersetzungsprozess vorzubereiten.

1. Verwenden Sie die Übersetzungsprojekte, um [den Prozess zur Übersetzung der Inhalte zu verwalten](/help/sites-administering/tc-manage.md).

>[!NOTE]
>
>* Komponenten für adaptive Formulare unterstützen keine RTL-Sprachen (Right to Left). Zum Beispiel Hebräisch.

>



