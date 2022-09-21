---
title: Integrieren von AEM Forms mit Adobe Analytics
seo-title: Learn how to integrate AEM Forms with Adobe Analytics.
description: AEM Forms kann mit Adobe Analytics integriert werden, um Leistungsmetriken für Ihre veröffentlichten Formulare zu erfassen und zu verfolgen.
seo-description: To discover interaction patterns and problems users face while using adaptive forms.
uuid: e258805c-4da8-4c5d-ae91-7bea78a6a71b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
discoiquuid: 8f776f30-ff93-4d19-94c6-c4bfe6f1fae2
docset: aem65
exl-id: be2444df-c772-4a8e-83f9-0f565c15a44e
source-git-commit: 67d492713d9e2236dbf81c5f3c781c80717ec9a6
workflow-type: tm+mt
source-wordcount: '1806'
ht-degree: 91%

---

# Analytics mit [!DNL Adobe Launch] {#analyticsusingadobelaunch}

AEM Forms ermöglicht die Integration mit [Adobe Analytics](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/overview.html?lang=de), damit Sie Leistungsmetriken für Ihre veröffentlichten Formulare erfassen und verfolgen können. Ziel der Analyse dieser Metriken ist es, Geschäftsanwendern Einblicke in das Verhalten der Endbenutzer zu geben und das Erlebnis der Datenerfassung zu optimieren. Sie können das Verhalten sowohl angemeldeter als auch nicht angemeldeter (anonymer) Benutzer über Adobe Analytics für adaptive Formulare erfassen und verfolgen.

Sie können auch Analysen mithilfe des Cloud Service Framework durchführen. Weitere Informationen zur Integration von AEM Forms in Cloud Service Framework finden Sie unter [Analytics mithilfe von Cloud Service Framework](/help/forms/using/configure-analytics-forms-documents.md). Der Hauptvorteil der Verwendung von Adobe Launch im Vergleich zu Analytics mithilfe des Cloud Service Framework besteht darin, dass Sie zusätzlich zu diesen vordefinierten Ereignissen auch benutzerdefinierte Ereignisse definieren können. Die angepassten Ereignisse werden mithilfe des Regeleditors oder von Client-Bibliotheken definiert und Ereignissen in [!DNL Adobe Analytics].

Nachdem Sie die in diesem Artikel erwähnten Aktionen ausgeführt haben, können Sie Berichte konfigurieren und in [!DNL Adobe Analytics] anzeigen, wie im folgenden Video gezeigt:

>[!VIDEO](https://video.tv.adobe.com/v/337262)

Sie können [!DNL Adobe Analytics] verwenden, um Interaktionsmuster zu entdecken und Probleme zu ermitteln, auf die Benutzer bei der Nutzung adaptiver Formulare stoßen. [!DNL Adobe Analytics] ist so vorkonfiguriert, dass Informationen zu den folgenden Ereignissen nachverfolgt und gespeichert werden:

* **Ausgaben**: Angabe, wie oft ein Formular geöffnet wurde.

* **Übermittlungen**: Angabe, wie oft ein Formular übermittelt wird.

* **Abbruch**: Angabe, wie oft Benutzer das Formular wieder verlassen haben, ohne es auszufüllen.

* **Fehler**: Anzahl der Fehler im Bedienfeld und in dessen Feldern.

* **Hilfe**: Anzahl der Hilfeaufrufe eines Benutzers in einem Bedienfeld und in dessen Feldern.

* **Feldbesuche**: Angabe, wie oft ein Benutzer ein Feld des Formulars besucht.

* **Speicherungen**: Angabe, wie oft Benutzer ein Formular im Formularportal speichern.

Neben diesen vordefinierten Ereignissen können Sie auch benutzerdefinierte Ereignisse definieren.

Die folgende Abbildung veranschaulicht die Aktionen, die Sie durchführen müssen, damit Sie Berichte in [!DNL Adobe Analytics] anzeigen können:

![Überblick über Analytics](/help/forms/using/assets/analyticsworkflow.png)

## 1. Konfiguration von [!DNL Adobe Analytics] {#Configure-adobe-analytics}

Vor dem Konfigurieren von [!DNL Adobe Analytics] erstellen Sie:

* Eine Adobe ID, um sich bei [Adobe Experience Cloud](https://experience.adobe.com/#/home) anzumelden.
* Eine [Report Suite](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html?lang=de).


### Installieren von AEM Forms und [!DNL Adobe Analytics]-Erweiterungen {#install-extensions}

Führen Sie die folgenden Schritte aus, um die Erweiterungen AEM Forms und [Adobe Analytics](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/analytics/overview.html?lang=de) zu konfigurieren:

1. Melden Sie sich bei Adobe Experience Cloud an und wählen Sie einen geeigneten Namen für das Unternehmen.

1. Tippen Sie auf **[!UICONTROL Launch/Datenerfassung]** und dann auf **[!UICONTROL Zu Launch/Datenerfassung gehen]**.

1. Tippen Sie auf **[!UICONTROL Neue Eigenschaft]** und geben Sie einen Namen für die Konfiguration an.

1. Geben Sie einen Domain-Namen an und tippen Sie auf **[!UICONTROL Speichern]**, um die Eigenschaft zu speichern.

1. Tippen Sie auf den Konfigurationsnamen, der in der Liste der Tag-Eigenschaften verfügbar ist.

1. Tippen Sie im Abschnitt **[!UICONTROL Authoring]** auf **[!UICONTROL Erweiterungen]**.

1. Tippen Sie auf **[!UICONTROL Katalog]** und dann auf **[!UICONTROL Installieren]** für die Erweiterung **[!UICONTROL Adobe Experience Manager Forms]**. **[!UICONTROL Adobe Experience Manager Forms]** wird in der Liste der installierten Erweiterungen auf der Registerkarte **Installiert** angezeigt.

1. Tippen Sie auf **[!UICONTROL Installieren]** für die Erweiterung **[!UICONTROL Adobe Analytics]**.
1. Wählen Sie den Namen der Report Suite in den Dropdown-Listen **[!UICONTROL Entwicklungs-Report Suites]**, **[!UICONTROL Staging-Report Suites]** und **[!UICONTROL Produktions-Report Suites]** aus und tippen Sie auf **[!UICONTROL Speichern]**, um die Erweiterung zu speichern.

### Konfigurieren von Datenelementen {#configure-data-elements}

Sie können jedes dieser konfigurierten Datenelemente in einer für ein Ereignis erstellten Regel auswählen. Wenn ein Ereignis in einem adaptiven Formular auftritt, sendet AEM Forms diese Datenelemente an [!DNL Adobe Analytics].

Nach der Installation der Erweiterung **[!UICONTROL Adobe Experience Manager Forms]** können Sie die folgenden Datenelemente erstellen:

<table>
 <tbody>
  <tr>
   <td>FieldName</th>
   <td>FieldTitle</th>
   <td>FormInstance</th>
  </tr>
  <tr>
   <td>FormName<br /> </td>
   <td>FormTitle<br /> </td>
   <td>PageName</td>
  </tr>
  <tr>
   <td>PageURL<br /> </td>
   <td>PanelTitle<br /> </td>
   <td>TimeSpent</td>
  </tr>
 </tbody>
</table>

Führen Sie die folgenden Schritte aus, um Datenelemente zu konfigurieren:

1. Tippen Sie im Abschnitt **[!UICONTROL Authoring]** auf **[!UICONTROL Datenelemente]**.

1. Tippen Sie auf **[!UICONTROL Neues Datenelement erstellen]**.

1. Geben Sie einen Namen für das Datenelement an. Zum Beispiel „Formulartitel“ für ein Datenelement vom Typ Formulartitel.

1. Geben Sie **[!UICONTROL Adobe Experience Manager Forms]** als Name der Erweiterung an.

1. Wählen Sie den **[!UICONTROL Datenelementtyp]** aus.

1. Tippen Sie auf **[!UICONTROL Speichern]**, um das Datenelement zu speichern.

   >[!VIDEO](https://video.tv.adobe.com/v/337472)

### Konfigurieren von Regeln {#configure-rules}

Führen Sie die folgenden Schritte aus, um Regeln auf der Grundlage der Erweiterung **[!UICONTROL Adobe Experience Manager Forms]** zu erstellen:

1. Tippen Sie im Abschnitt **[!UICONTROL Authoring]** auf **[!UICONTROL Regeln]**.

1. Tippen Sie auf **[!UICONTROL Neue Regel erstellen]**.

1. Geben Sie einen Namen für die Regel an. Zum Beispiel „Formularübermittlung“, um Formularübermittlungen aufzuzeichnen.

1. Tippen Sie im Abschnitt **[!UICONTROL Ereignisse]** auf **[!UICONTROL Hinzufügen]**.

1. Geben Sie **[!UICONTROL Adobe Experience Manager Forms]** als Name der Erweiterung an.

1. Wählen Sie den Ereignistyp aus. Die Eingabe für das Feld **[!UICONTROL Name]** wird automatisch auf der Grundlage des ausgewählten Ereignistyps ausgefüllt.

1. Tippen Sie auf **[!UICONTROL Änderungen beibehalten]**, um das Ereignis zu speichern.

1. Tippen Sie im Abschnitt **[!UICONTROL Aktionen]** auf **[!UICONTROL Hinzufügen]**.

1. Geben Sie **[!UICONTROL Adobe Analytics]** als Namen der Erweiterung an.

1. Wählen Sie als Aktionstyp **[!UICONTROL Variablen festlegen]** aus. In der Dropdown-Liste sind folgende Optionen verfügbar:

   * **[!UICONTROL Variablen festlegen]**: Verwenden Sie diesen Aktionstyp, um den Ereignistyp zu definieren, für den die ausgewählten Datenelemente von AEM Forms an [!DNL Adobe Analytics] gesendet werden.

   * **[!UICONTROL Beacon senden]**: Verwenden Sie diesen Aktionstyp, um Daten von AEM Forms an [!DNL Adobe Analytics] zu senden.

   * **[!UICONTROL Variablen löschen]**: Verwenden Sie diesen Aktionstyp, um den Datenpfad zu löschen, damit das Ereignis nur einmal in [!DNL Adobe Analytics] registriert wird.

      Es wird empfohlen, den Aktionstyp **[!UICONTROL Variablen festlegen]** zu verwenden, um die Ereignis- und Datenelemente zu konfigurieren, dann **[!UICONTROL Beacon senden]** zu verwenden, um Daten zu senden, und dann **[!UICONTROL Variablen löschen]** zu verwenden, um den Datenpfad zu löschen.

1. Im Abschnitt **[!UICONTROL Props]** ordnen Sie die in der Dropdown-Liste verfügbaren Report Suite-Optionen den Datenelementen zu, die mit [Datenelemente konfigurieren](#configure-data-elements) definiert wurden.

   Zum Beispiel, um das Datenelement **Formulartitel** von AEM Forms an zu senden, wenn Sie ein Formular übermitteln:[!DNL Adobe Analytics]
   1. Wählen Sie im Abschnitt **[!UICONTROL Props]** ein in der Report Suite verfügbares Prop für Formulartitel und tippen Sie dann auf das ![Datenbanksymbol](/help/forms/using/assets/database-icon.svg), um es dem in [Datenelemente konfigurieren](#configure-data-elements) erstellten Formulartitel zuzuordnen.

      ![define-props](/help/forms/using/assets/define-props.png)

   1. Tippen Sie auf **[!UICONTROL Weiteres hinzufügen]**, um der Liste weitere Datenelemente hinzuzufügen.

1. Wählen Sie im Abschnitt **[!UICONTROL Ereignisse]** ein Ereignis aus den in der Report Suite verfügbaren Optionen aus und tippen Sie auf **[!UICONTROL Änderungen beibehalten]**.

1. Tippen Sie im Bereich **[!UICONTROL Aktionen]** auf „+“ und geben Sie **[!UICONTROL Adobe Analytics]** als Namen der Erweiterung an.

1. Wählen Sie als Aktionstyp **[!UICONTROL Beacon senden]** aus. Wählen Sie im rechten Bereich **[!UICONTROL s.t()]**, um Daten an [!DNL Adobe Analytics] zu senden und als Seitenansicht zu behandeln, oder **[!UICONTROL s.tl()]**, um Daten an [!DNL Adobe Analytics] zu senden und nicht als Seitenansicht zu behandeln. Tippen Sie auf **[!UICONTROL Änderungen beibehalten]**.

1. Tippen Sie im Bereich **[!UICONTROL Aktionen]** auf „+“ und geben Sie **[!UICONTROL Adobe Analytics]** als Namen der Erweiterung an.

1. Wählen Sie als Aktionstyp **[!UICONTROL Variablen löschen]** aus. Tippen Sie auf **[!UICONTROL Änderungen beibehalten]**. Nachdem Sie diese Schritte durchgeführt haben, wird der Abschnitt **[!UICONTROL Aktionen]** wie folgt angezeigt:
   ![Konfiguration von Aktionen](/help/forms/using/assets/actions-config.png)

   Passen Sie den Abschnitt **[!UICONTROL Aktionen]** Ihren Anforderungen entsprechend an. Sie können beispielsweise zwei Schritte **Beacon senden** in einem Aktionsfluss definieren, um in einem Schritt Daten an [!DNL Adobe Analytics] zu senden und als Seitenansicht zu behandeln und im zweiten Schritt Daten an [!DNL Adobe Analytics] zu senden und nicht als Seitenansicht zu behandeln.

   ![Konfiguration von Aktionen](/help/forms/using/assets/actions-config-2.png)

1. Tippen Sie auf **[!UICONTROL Speichern]**, um die Regel zu speichern.

   Sie können Regeln für alle Ereignistypen erstellen, wie z. B. Abbruch, Fehler, Außendienstbesuche, Hilfe, Ausgaben, Speicherungen und Übermittlungen.

   >[!VIDEO](https://video.tv.adobe.com/v/337425)


### Flüsse veröffentlichen {#publish-flow}

Nachdem Sie die Datenelemente erstellt und in Regeln verwendet haben, müssen Sie die Konfiguration veröffentlichen, um Formulardaten in [!DNL Adobe Analytics] zu erfassen.

Führen Sie zur Veröffentlichung der Konfiguration folgende Schritte aus:

1. Tippen Sie im Abschnitt **[!UICONTROL Veröffentlichen]** auf **[!UICONTROL Fluss veröffentlichen]**.

1. Tippen Sie auf **[!UICONTROL Bibliothek hinzufügen]**, geben Sie einen Namen an und wählen Sie die Umgebung für die Bibliothek aus.

1. Tippen Sie auf **[!UICONTROL Alle geänderten Ressourcen hinzufügen]** und dann auf **[!UICONTROL Für Entwicklung speichern und erstellen]**.

1. Tippen Sie im Abschnitt **[!UICONTROL Entwicklung]** auf ![Weitere Optionen](/help/forms/using/assets/more-options-icon.svg) und dann auf **[!UICONTROL Genehmigen und zur Produktion veröffentlichen]**.

1. Bestätigen Sie die Änderungen. Der Veröffentlichungsfluss wird kurz darauf im Abschnitt **[!UICONTROL Veröffentlicht]** angezeigt.

![Flüsse veröffentlichen](/help/forms/using/assets/publish-flow.png)

## 2. Konfiguration von AEM Forms {#configure-aem-forms}

Bevor Sie eine Adobe Launch-Konfiguration erstellen, erstellen Sie eine [Adobe IMS-Konfiguration mit Adobe Launch als Cloud-Lösung](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/connect-aem-launch-adobe-io.html?lang=de).

### Erstellen einer Adobe Launch-Konfiguration {#create-adobe-launch-configuration}

Führen Sie die folgenden Schritte aus, um eine Adobe Launch-Konfiguration zu erstellen:

1. Gehen Sie in der AEM Forms-Autoreninstanz zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Launch-Konfigurationen]**.

1. Wählen Sie einen Ordner aus, um die Konfiguration zu erstellen, und tippen Sie auf **[!UICONTROL Erstellen]**.

1. Geben Sie im Feld **[!UICONTROL Titel]** einen Titel für die Konfiguration an.

1. Wählen Sie die [zugehörige Adobe IMS-Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/connect-aem-launch-adobe-io.html) aus.

1. Wählen Sie den Namen des Unternehmens, der bei der [Konfiguration von Adobe Analytics](#Configure-adobe-analytics) verwendet wurde.

1. Wählen Sie den Namen der erstellten Eigenschaft, der bei der [Konfiguration von Adobe Analytics](#install-extensions) verwendet wurde.

1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**.

1. Veröffentlichen Sie die Konfiguration.

### Aktivieren von [!DNL Adobe Analytics] für ein adaptives Formular {#enable-analytics-adaptive-form}

Verwenden der [!DNL Adobe Launch]-Konfiguration in einem vorhandenen adaptiven Formular:

1. Gehen Sie in der AEM Forms-Autoreninstanz zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie das adaptive Formular aus und tippen Sie auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Standard]** den [Konfigurations-Container](#create-adobe-launch-configuration) aus, der bei der Erstellung der Adobe Launch-Konfiguration verwendet wurde.
1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**. Das adaptive Formular ist für [!DNL Adobe Analytics] aktiviert.
1. Formulare veröffentlichen.

Nachdem Sie [!DNL Adobe Analytics] für ein adaptives Formular aktiviert haben, können Sie [überprüfen](https://experienceleague.adobe.com/docs/launch-learn/implementing-in-websites-with-launch/implement-solutions/analytics.html?lang=de#validate-the-page-view-beacon), ob ein geeigneter Datenereignisfluss zwischen AEM Forms und [!DNL Adobe Analytics] vorhanden ist. Die Integration von AEM Forms mit Adobe Analytics ist nun abgeschlossen. Sie können jetzt [Berichte in Adobe Analytics konfigurieren und anzeigen](#view-reports-adobe-analytics).

>[!NOTE]
>Wenn beide [Analytics mithilfe von Cloud Service Framework](/help/forms/using/configure-analytics-forms-documents.md) und **Analytics mit Adobe Launch** Funktionen gleichzeitig aktiviert sind, **Analytics mit Adobe Launch** hat Vorrang.

### Erstellen von Regeln zur Erfassung benutzerdefinierter Ereignisse (optional) {#capture-custom-events}

Erstellen Sie mit dem Regeleditor Regeln für bestimmte Felder eines adaptiven Formulars, um Analytics-Daten aus einem adaptiven Formular an [!DNL Adobe Analytics] zu senden.

In einem zweistufigen Prozess definieren Sie eine Regel für ein Feld in einem adaptiven Formular. Die Regel löst ein Ereignis aus. Der Name des Ereignisses wird einem benutzerdefinierten Erfassungsereignis in Adobe Launch zugeordnet.

So erstellen Sie mit dem Regeleditor Regeln in einem adaptiven Formular:

1. Tippen Sie auf das Feld und wählen Sie ![Regeleditor](/help/forms/using/assets/rule-editor-icon.svg), um die Seite mit dem Regeleditor zu öffnen.
1. Definieren Sie eine Bedingung im Abschnitt [!UICONTROL Wenn] der Regel.
1. Wählen Sie im Abschnitt [!UICONTROL Dann] der Regel die Option **[!UICONTROL Dispatch-Ereignis]** aus der Dropdown-Liste **[!UICONTROL Aktion auswählen]**.
1. Geben Sie den Namen des Ereignisses im Feld **[!UICONTROL Ereignisname eingeben]** an.

Wenn beispielsweise das Geburtsdatum vor einem bestimmten Datum liegt, sendet AEM Forms das Ereignis **Sicherheit**.

![Dispatch-Ereignis](/help/forms/using/assets/security-event.png)

So ordnen Sie das Ereignis einem benutzerdefinierten Erfassungsereignis in [!DNL Adobe Analytics] zu:

1. [Erstellen einer Regel](#configure-rules).

1. Tippen Sie im Abschnitt **[!UICONTROL Ereignisse]** auf **[!UICONTROL Hinzufügen]**.

1. Geben Sie **[!UICONTROL Adobe Experience Manager Forms]** als Name der Erweiterung an.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Ereignistyp]** die Option **[!UICONTROL Benutzerdefiniertes Ereignis erfassen]** aus.

1. Geben Sie den Namen des Ereignisses an, den Sie in Schritt 4 beim Erstellen einer Regel mit dem Regeleditor angegeben haben.

1. Tippen Sie auf **Änderungen beibehalten** und führen Sie die restlichen unter [Regeln konfigurieren](#configure-rules) angegebenen Aktionen aus.

## 3. Konfigurieren und Anzeigen von Berichten in [!DNL Adobe Analytics] {#view-reports-adobe-analytics}

Nachdem Sie ein adaptives Formular zum Senden von Ereignisdaten an [!DNL Adobe Analytics] konfiguriert haben, können Sie in [!DNL Adobe Analytics] Berichte anzeigen.

1. Tippen Sie auf ![Produkt auswählen](/help/forms/using/assets/select-analytics.png) und wählen Sie **[!UICONTROL Analytics]** aus.

1. Tippen Sie auf **[!UICONTROL Projekt erstellen]** und wählen Sie **[!UICONTROL Leeres Projekt]** aus.

1. Wählen Sie den Namen der Report Suite aus der Dropdown-Liste oben rechts im Freiformformular.

1. Geben Sie den **Formulartitel** im Text von **[!UICONTROL Dimensionselemente durchsuchen]** an, um alle Formulartitel anzuzeigen.

1. Fügen Sie den Titel des adaptiven Formulars in das Textfeld **[!UICONTROL Segment (oder eine andere Komponente) hier ablegen]** ein.

1. Legen Sie im Abschnitt **[!UICONTROL Metriken]** die zu verfolgenden Ereignisse in das Textfeld **[!UICONTROL Metrik (oder eine andere Komponente) hier ablegen]** ab.

1. Tippen Sie auf ![Visualisierungen](/help/forms/using/assets/visualization-icon.svg) und legen Sie einen Diagrammtyp im Abschnitt „Freiform“ ab. In ähnlicher Weise können Sie mehrere Diagrammtypen zum Abschnitt „Freiform“ hinzufügen.

1. Drücken Sie die Tasten Strg+S und geben Sie einen Namen an, um das Projekt zu speichern.

Detaillierte Informationen zum Anzeigen von Formularanalyseberichten finden Sie unter [Anzeigen und Verstehen der Analyseberichte in AEM Forms](../../forms/using/view-understand-aem-forms-analytics-reports.md).