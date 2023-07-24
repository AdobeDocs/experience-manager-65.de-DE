---
title: Verwenden des Übersetzungs-Workflows von AEM zum Lokalisieren von adaptiven Formularen und Datensatzdokumenten
seo-title: Using AEM translation workflow to localize adaptive forms and document of record
description: Erfahren Sie, wie Sie mithilfe AEM Übersetzungs-Workflows adaptive Formulare und Datensatzdokumente lokalisieren können.
seo-description: Learn to use AEM translation workflows to localize adaptive forms and document of record.
uuid: 6c87a283-0203-4cf7-989a-3770ddbbbd6e
content-type: reference
topic-tags: develop
discoiquuid: f5642571-9657-4ca1-93c5-4ae2eb91e967
noindex: true
feature: Adaptive Forms
exl-id: ebec03a3-67a0-4ecd-84bb-8580388e048a
source-git-commit: e7a3558ae04cd6816ed73589c67b0297f05adce2
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 50%

---

# Verwenden von AEM-Übersetzungs-Workflow zum Lokalisieren von adaptiven Formularen und DoR {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für [Erstellen neuer adaptiver Forms](/help/forms/using/create-an-adaptive-form-core-components.md) oder [Hinzufügen von Adaptive Forms zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Forms dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von Adaptive Forms mithilfe von Foundation-Komponenten beschrieben. </span>

Mit lokalisierten Formularen können Sie eine größere Zielgruppe über Ländergrenzen hinweg ansprechen. Mit den Adobe Experience Manager-Übersetzungs-Workflows können Sie adaptive Formulare und ihre DoR lokalisieren. Sie können **maschinelle Übersetzung** oder **Übersetzer** um ein adaptives Formular zu lokalisieren.

In diesem Artikel wird die Verwendung AEM Übersetzungs-Workflows mit adaptiven Formularen und Datensatzdokumenten erläutert.

## Lokalisieren eines adaptiven Formulars und Datensatzdokuments mithilfe der maschinellen Übersetzung {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

Der Dienst für maschinelle Übersetzung übersetzt sofort Inhalte Ihrer adaptiven Formulare und DoR. AEM Forms ist für die Verwendung einer Testversion von Microsoft Translator für maschinelle Übersetzung vorkonfiguriert. Führen Sie die folgenden Schritte aus, um die maschinelle Übersetzung für Ihre adaptiven Formulare und Ihr Datensatzdokument zu aktivieren:

1. Wählen Sie auf der Benutzeroberfläche von AEM Forms ein Formular aus und tippen Sie auf die Option **Wörterbuch hinzufügen**.
1. Wählen Sie auf dem Bildschirm **Wörterbuch zum Übersetzungsprojekt hinzufügen** die Option **Neues Übersetzungsprojekt erstellen** oder **Zu vorhandenem Übersetzungsprojekt hinzufügen**.
1. Geben Sie im Feld **Projekttitel** den Titel an. Beispiel: `Government Reference Site - German locale.`
1. Geben Sie im Feld **Zielsprachen** ein Gebietsschema an (beispielsweise `German(de)`) und klicken Sie auf **Fertig**. Sie können mehrere Gebietsschemas angeben. Das Formular wird in alle im Feld **Zielsprachen** angegebenen Gebietsschemas übersetzt.
1. Klicken Sie im Dialogfeld Wörterbuch hinzugefügt auf **Projekte öffnen**. Öffnen Sie im Bildschirm &quot;Projekte&quot;das neu erstellte Projekt.
1. Klicken Sie auf **Ellipsen** am unteren Rand des **Übersetzungszusammenfassung** Kachel. Der Bildschirm Übersetzungszusammenfassung wird geöffnet.
1. Klicken Sie auf **Bearbeiten** -Symbol oben im **Übersetzungszusammenfassung** angezeigt. Öffnen Sie die Registerkarte **Übersetzung** und wählen Sie auf dem Bildschirm **Übersetzungsmethode** die Option „Maschinelle Übersetzung“. Wählen Sie den entsprechenden **Übersetzungsanbieter** und die entsprechende **Cloudkonfiguration**. Klicken Sie am oberen Rand des Bildschirms auf das Symbol **Fertig**.
1. Klicken Sie auf der Kachel **Übersetzungsauftrag** auf das Symbol ![aem62forms_downarrow](assets/aem62forms_downarrow.png) und dann auf **Start**. Der Status der Kachel ändert sich in Entwurf. Nach Abschluss der Übersetzung ändert sich der Status in **Bereit zur Überprüfung**. Aktualisieren Sie die Seite nach einigen Minuten und überprüfen Sie den Status.
1. Nachdem sich der Status auf der Kachel **Übersetzungsauftrag** in **Bereit für Überprüfung** geändert hat, öffnen Sie das Formular in einem Browserfenster. Eine lokalisierte Version des Formulars wird angezeigt.

   >[!NOTE]
   >
   >* Bevor Sie die lokalisierte Version des Formulars im Browserfenster öffnen, stellen Sie sicher, dass das Gebietsschema des Browsers auf das Gebietsschema des Formulars eingestellt ist. Wenn das Formular beispielsweise in die Sprache Deutsch(de) übersetzt wird, setzen Sie das Gebietsschema des Browsers auf Deutsch(de).
   >* Komponenten für adaptive Formulare unterstützen keine RTL-Sprachen (Right to Left – von rechts nach links). Zum Beispiel Hebräisch.

   Zusammen mit dem adaptiven Formular wird das automatisch generierte DoR auch lokalisiert.

   Weitere Informationen zu Einstellungen und Konfigurationen für Datensatzdokumente finden Sie unter:

[Konfiguration von Vorlagen für Datensatzdokumente](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

[Einstellungen für Datensatzdokumente](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [Anpassen der Branding-Informationen des Datensatzdokuments](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) und stellen Sie sicher, dass das Gebietsschema des Browsers auf dieselbe Sprache festgelegt ist, in die Sie das adaptive Formular mithilfe der Maschinensprache lokalisiert haben. Das Browser-Gebietsschema hilft beim Lokalisieren der Branding-Informationen im Datensatzdokument.
1. Um das lokalisierte Datensatzdokument anzuzeigen, tippen Sie auf Vorschau generieren . Die PDF-Datei des Datensatzdokuments wird erstellt und in einer neuen Registerkarte im Browser geöffnet.

## Lokalisieren eines adaptiven Formulars und seines Datensatzdokuments mithilfe der menschlichen Übersetzung {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

Bei der menschlichen Übersetzung werden die Inhalte an einen Übersetzungsanbieter gesendet und von professionellen Übersetzern übersetzt. Wenn die Inhalte übersetzt wurden, werden sie zurückgesendet und in AEM importiert. Ist Ihr Übersetzungsdienstleister in AEM integriert, werden die Inhalte automatisch von AEM an den Übersetzungsdienstleister gesendet.

Für die Übersetzung wird ein Wörterbuch mit Dateien im XLIFF-Format für die professionellen Übersetzer freigegeben. Das Wörterbuch enthält eine separate XLIFF-Datei für jedes Gebietsschema. Jede XLIFF-Datei enthält Text, der den Endbenutzern angezeigt wird, sowie Platzhalter für den entsprechenden lokalisierten Text.

Führen Sie die folgenden Schritte aus, um ein Formular und sein Datensatzdokument mithilfe von Übersetzern zu lokalisieren:

1. [Stellen Sie eine Verbindung zwischen AEM und Ihrem Übersetzungsdienstleister her](/help/sites-administering/tc-tic.md) und [erstellen Sie Konfigurationen für die Integration des Übersetzungs-Frameworks](/help/sites-administering/tc-tic.md).

1. [Verknüpfen Sie die Seiten Ihres Sprachstamms](/help/sites-administering/tc-tic.md) mit dem Übersetzungsdienstleister und den Framework-Konfigurationen.

1. [Identifizieren Sie die Art der zu übersetzenden Inhalte](/help/sites-administering/tc-rules.md).

1. [Bereiten Sie die Inhalte für die Übersetzung vor](/help/sites-administering/tc-prep.md), indem Sie den Sprachstamm und die Stammseiten der Sprachkopien erstellen.

1. [Erstellen Sie Übersetzungsprojekte](/help/sites-administering/tc-manage.md), um die zu übersetzenden Inhalte zusammenzustellen und den Übersetzungsprozess vorzubereiten.

1. Verwenden Sie die Übersetzungsprojekte, um [den Prozess zur Übersetzung der Inhalte zu verwalten](/help/sites-administering/tc-manage.md).

>[!NOTE]
>
>* Komponenten für adaptive Formulare unterstützen keine RTL-Sprachen (Right to Left – von rechts nach links). Zum Beispiel Hebräisch.
>
