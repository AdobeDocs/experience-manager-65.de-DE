---
title: Integrieren von AEM Forms mit Adobe Analytics
description: AEM Forms lässt sich mit Adobe Analytics integrieren, um Leistungsdaten für Ihre veröffentlichten Formulare zu erfassen und zu verfolgen.
docset: aem65
exl-id: 030fe9f2-cd41-4290-b8a6-2f9ade6b5789
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
feature: Adaptive Forms
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: tm+mt
source-wordcount: '1762'
ht-degree: 100%

---

# Analytics mit [!DNL Adobe Launch] {#analyticsusingadobelaunch}

AEM Forms lässt sich mit [Adobe Analytics](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/overview.html?lang=de) integrieren, damit Sie Leistungsmetriken für Ihre veröffentlichten Formulare erfassen und nachverfolgen können. Ziel der Analyse dieser Metriken ist es, Geschäftsanwendern Einblicke in das Verhalten der Endbenutzer zu geben und das Erlebnis der Datenerfassung zu optimieren. Sie können das Verhalten sowohl angemeldeter als auch nicht angemeldeter (anonymer) Benutzer über Adobe Analytics für adaptive Formulare erfassen und verfolgen.

Sie können auch Analysen mithilfe des Cloud Service-Frameworks durchführen. Weitere Informationen über die Integration von AEM Forms mit Cloud Service Framework finden Sie unter [Analytics mit Cloud Service-Framework](/help/forms/using/configure-analytics-forms-documents.md). Der Hauptvorteil von Adobe Launch gegenüber Analytics mit dem Cloud Service-Framework ist, dass Sie zusätzlich zu den Standardereignissen auch vorkonfigurierte Ereignisse definieren können. Die benutzerdefinierten Ereignisse werden mit dem Regeleditor oder den Kunden-Clientlibs definiert und den Ereignissen in [!DNL Adobe Analytics] zugeordnet.

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

1. Wählen Sie **[!UICONTROL Launch/Datenerfassung]** und dann **[!UICONTROL Zu Launch/Datenerfassung gehen]** aus.

1. Wählen Sie **[!UICONTROL Neue Eigenschaft]** aus und geben Sie einen Namen für die Konfiguration an.

1. Geben Sie einen Domain-Namen an und wählen Sie **[!UICONTROL Speichern]** aus, um die Eigenschaft zu speichern.

1. Wählen Sie den Konfigurationsnamen aus, der in der Liste der Tag-Eigenschaften verfügbar ist.

1. Wählen Sie im Abschnitt **[!UICONTROL Authoring]** die Option **[!UICONTROL Erweiterungen]** aus.

1. Wählen Sie **[!UICONTROL Katalog]** und dann **[!UICONTROL Installieren]** für die Erweiterung **[!UICONTROL Adobe Experience Manager Forms]** aus. **[!UICONTROL Adobe Experience Manager Forms]** wird in der Liste der installierten Erweiterungen auf der Registerkarte **Installiert** angezeigt.

1. Wählen Sie **[!UICONTROL Installieren]** für die **[!UICONTROL Adobe Analytics]**-Erweiterung aus.
1. Wählen Sie den Namen der Report Suite in den Dropdown-Listen **[!UICONTROL Entwicklungs-Report Suites]**, **[!UICONTROL Staging-Report Suites]** und **[!UICONTROL Produktions-Report Suites]** und dann **[!UICONTROL Speichern]** aus, um die Erweiterung zu speichern.

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

1. Wählen Sie im Abschnitt **[!UICONTROL Authoring]** die Option **[!UICONTROL Datenelemente]** aus.

1. Wählen Sie **[!UICONTROL Neues Datenelement erstellen]** aus.

1. Geben Sie einen Namen für das Datenelement an. Zum Beispiel „Formulartitel“ für ein Datenelement vom Typ Formulartitel.

1. Geben Sie **[!UICONTROL Adobe Experience Manager Forms]** als Name der Erweiterung an.

1. Wählen Sie den **[!UICONTROL Datenelementtyp]** aus.

1. Wählen Sie **[!UICONTROL Speichern]** aus, um das Datenelement zu speichern.

   >[!VIDEO](https://video.tv.adobe.com/v/337472)

### Konfigurieren von Regeln {#configure-rules}

Führen Sie die folgenden Schritte aus, um Regeln auf der Grundlage der Erweiterung **[!UICONTROL Adobe Experience Manager Forms]** zu erstellen:

1. Wählen Sie im Abschnitt **[!UICONTROL Authoring]** die Option **[!UICONTROL Regeln]** aus.

1. Wählen Sie **[!UICONTROL Neue Regel erstellen]** aus.

1. Geben Sie einen Namen für die Regel an. Zum Beispiel „Formularübermittlung“, um Formularübermittlungen aufzuzeichnen.

1. Wählen Sie im Abschnitt **[!UICONTROL Ereignisse]** die Option **[!UICONTROL Hinzufügen]** aus.

1. Geben Sie **[!UICONTROL Adobe Experience Manager Forms]** als Name der Erweiterung an.

1. Wählen Sie den Ereignistyp aus. Die Eingabe für das Feld **[!UICONTROL Name]** wird automatisch auf der Grundlage des ausgewählten Ereignistyps ausgefüllt.

1. Wählen Sie **[!UICONTROL Änderungen beibehalten]** aus, um das Ereignis zu speichern.

1. Wählen Sie im Abschnitt **[!UICONTROL Aktionen]** die Option **[!UICONTROL Hinzufügen]** aus.

1. Geben Sie **[!UICONTROL Adobe Analytics]** als Namen der Erweiterung an.

1. Wählen Sie als Aktionstyp **[!UICONTROL Variablen festlegen]** aus. In der Dropdown-Liste sind folgende Optionen verfügbar:

   * **[!UICONTROL Variablen festlegen]**: Verwenden Sie diesen Aktionstyp, um den Ereignistyp zu definieren, für den die ausgewählten Datenelemente von AEM Forms an [!DNL Adobe Analytics] gesendet werden.

   * **[!UICONTROL Beacon senden]**: Verwenden Sie diesen Aktionstyp, um Daten von AEM Forms an [!DNL Adobe Analytics] zu senden.

   * **[!UICONTROL Variablen löschen]**: Verwenden Sie diesen Aktionstyp, um den Datenpfad zu löschen, damit das Ereignis nur einmal in [!DNL Adobe Analytics] registriert wird.

     Es wird empfohlen, den Aktionstyp **[!UICONTROL Variablen festlegen]** zu verwenden, um die Ereignis- und Datenelemente zu konfigurieren, dann **[!UICONTROL Beacon senden]** zu verwenden, um Daten zu senden, und dann **[!UICONTROL Variablen löschen]** zu verwenden, um den Datenpfad zu löschen.

1. Im Abschnitt **[!UICONTROL Props]** ordnen Sie die in der Dropdown-Liste verfügbaren Report Suite-Optionen den Datenelementen zu, die mit [Datenelemente konfigurieren](#configure-data-elements) definiert wurden.

   Zum Beispiel, um das Datenelement **Formulartitel** von AEM Forms an zu senden, wenn Sie ein Formular übermitteln:[!DNL Adobe Analytics]
   1. Wählen Sie im Abschnitt **[!UICONTROL Props]** ein in der Report Suite verfügbares Prop für Formulartitel und dann das ![Datenbanksymbol](/help/forms/using/assets/database-icon.svg) aus, um es dem unter [Datenelemente konfigurieren](#configure-data-elements) erstellten Formulartitel zuzuordnen.

      ![define-props](/help/forms/using/assets/define-props.png)

   1. Wählen Sie **[!UICONTROL Weiteres hinzufügen]** aus, um der Liste weitere Datenelemente hinzuzufügen.

1. Wählen Sie im Abschnitt **[!UICONTROL Ereignisse]** ein Ereignis aus den in der Report Suite verfügbaren Optionen und dann **[!UICONTROL Änderungen beibehalten]** aus.

1. Wählen Sie im Abschnitt **[!UICONTROL Aktionen]** das Pluszeichen (+) aus und geben Sie **[!UICONTROL Adobe Analytics]** als Namen der Erweiterung an.

1. Wählen Sie als Aktionstyp **[!UICONTROL Beacon senden]** aus. Wählen Sie im rechten Bereich **[!UICONTROL s.t()]**, um Daten an [!DNL Adobe Analytics] zu senden und als Seitenansicht zu behandeln, oder **[!UICONTROL s.tl()]**, um Daten an [!DNL Adobe Analytics] zu senden und nicht als Seitenansicht zu behandeln. Wählen Sie **[!UICONTROL Änderungen beibehalten]** aus.

1. Wählen Sie im Abschnitt **[!UICONTROL Aktionen]** das Pluszeichen (+) aus und geben Sie **[!UICONTROL Adobe Analytics]** als Namen der Erweiterung an.

1. Wählen Sie als Aktionstyp **[!UICONTROL Variablen löschen]** aus. Wählen Sie **[!UICONTROL Änderungen beibehalten]** aus. Nachdem Sie diese Schritte durchgeführt haben, wird der Abschnitt **[!UICONTROL Aktionen]** wie folgt angezeigt:
   ![Konfiguration von Aktionen](/help/forms/using/assets/actions-config.png)

   Passen Sie den Abschnitt **[!UICONTROL Aktionen]** Ihren Anforderungen entsprechend an. Sie können beispielsweise zwei Schritte **Beacon senden** in einem Aktionsfluss definieren, um in einem Schritt Daten an [!DNL Adobe Analytics] zu senden und als Seitenansicht zu behandeln und im zweiten Schritt Daten an [!DNL Adobe Analytics] zu senden und nicht als Seitenansicht zu behandeln.

   ![Konfiguration von Aktionen](/help/forms/using/assets/actions-config-2.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus, um die Regel zu speichern.

   Sie können Regeln für alle Ereignistypen erstellen, wie z. B. Abbruch, Fehler, Außendienstbesuche, Hilfe, Ausgaben, Speicherungen und Übermittlungen.

   >[!VIDEO](https://video.tv.adobe.com/v/337425)


### Flüsse veröffentlichen {#publish-flow}

Nachdem Sie die Datenelemente erstellt und in Regeln verwendet haben, müssen Sie die Konfiguration veröffentlichen, um Formulardaten in [!DNL Adobe Analytics] zu erfassen.

Führen Sie zum Veröffentlichen der Konfiguration folgende Schritte aus:

1. Wählen Sie im Abschnitt **[!UICONTROL Veröffentlichung]** die Option für den **[!UICONTROL Veröffentlichungsfluss]** aus.

1. Wählen Sie **[!UICONTROL Bibliothek hinzufügen]** aus, geben Sie einen Namen an und wählen Sie die Umgebung für die Bibliothek aus.

1. Wählen Sie **[!UICONTROL Alle geänderten Ressourcen hinzufügen]** und dann **[!UICONTROL Für Entwicklung speichern und erstellen]** aus.

1. Wählen Sie im Abschnitt **[!UICONTROL Entwicklung]** das Element ![Weitere Optionen](/help/forms/using/assets/more-options-icon.svg) und dann **[!UICONTROL Genehmigen und zur Produktion veröffentlichen]** aus.

1. Bestätigen Sie die Änderungen. Der Veröffentlichungsfluss wird kurz darauf im Abschnitt **[!UICONTROL Veröffentlicht]** angezeigt.

![Veröffentlichungsfluss](/help/forms/using/assets/publish-flow.png)

## 2. Konfiguration von AEM Forms {#configure-aem-forms}

Bevor Sie eine Adobe Launch-Konfiguration erstellen, erstellen Sie eine [Adobe IMS-Konfiguration mit Adobe Launch als Cloud-Lösung](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/connect-aem-launch-adobe-io.html?lang=de).

### Erstellen einer Adobe Launch-Konfiguration {#create-adobe-launch-configuration}

Führen Sie die folgenden Schritte aus, um eine Adobe Launch-Konfiguration zu erstellen:

1. Gehen Sie in der AEM Forms-Autoreninstanz zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Launch-Konfigurationen]**.

1. Wählen Sie einen Ordner aus, um die Konfiguration zu erstellen, und dann **[!UICONTROL Erstellen]**.

1. Geben Sie im Feld **[!UICONTROL Titel]** einen Titel für die Konfiguration an.

1. Wählen Sie die [zugehörige Adobe IMS-Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/connect-aem-launch-adobe-io.html?lang=de) aus.

1. Wählen Sie den Namen des Unternehmens, der bei der [Konfiguration von Adobe Analytics](#Configure-adobe-analytics) verwendet wurde.

1. Wählen Sie den Namen der erstellten Eigenschaft, der bei der [Konfiguration von Adobe Analytics](#install-extensions) verwendet wurde.

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

1. Veröffentlichen Sie die Konfiguration.

### Aktivieren von [!DNL Adobe Analytics] für ein adaptives Formular {#enable-analytics-adaptive-form}

Verwenden der [!DNL Adobe Launch]-Konfiguration in einem vorhandenen adaptiven Formular:

1. Navigieren Sie in der AEM Forms-Autoreninstanz zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie das adaptive Formular und dann **[!UICONTROL Eigenschaften]** aus.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Standard]** den [Konfigurations-Container](#create-adobe-launch-configuration) aus, der bei der Erstellung der Adobe Launch-Konfiguration verwendet wurde.
1. Wählen Sie **[!UICONTROL Speichern und schließen]** aus. Das adaptive Formular ist für [!DNL Adobe Analytics] aktiviert.
1. Formulare veröffentlichen.

Nachdem Sie [!DNL Adobe Analytics] für ein adaptives Formular aktiviert haben, können Sie [überprüfen](https://experienceleague.adobe.com/docs/launch-learn/implementing-in-websites-with-launch/implement-solutions/analytics.html?lang=de#validate-the-page-view-beacon), ob ein geeigneter Datenereignisfluss zwischen AEM Forms und [!DNL Adobe Analytics] vorhanden ist. Die Integration von AEM Forms mit Adobe Analytics ist nun abgeschlossen. Sie können jetzt [Berichte in Adobe Analytics konfigurieren und anzeigen](#view-reports-adobe-analytics).

>[!NOTE]
>Wenn beide Funktionen [Analytics mit Cloud Service Framework](/help/forms/using/configure-analytics-forms-documents.md) und **Analytics mit Adobe Launch** gleichzeitig aktiviert sind, hat **Analytics mit Adobe Launch** Vorrang.
> 

### Erstellen von Regeln zur Erfassung benutzerdefinierter Ereignisse (optional) {#capture-custom-events}

Erstellen Sie mit dem Regeleditor Regeln für bestimmte Felder eines adaptiven Formulars, um Analytics-Daten aus einem adaptiven Formular an [!DNL Adobe Analytics] zu senden.

In einem zweistufigen Prozess definieren Sie eine Regel für ein Feld in einem adaptiven Formular. Die Regel löst ein Ereignis aus. Der Name des Ereignisses wird einem benutzerdefinierten Erfassungsereignis in Adobe Launch zugeordnet.

So erstellen Sie mit dem Regeleditor Regeln in einem adaptiven Formular:

1. Wählen Sie das Feld und dann ![Regeleditor](/help/forms/using/assets/rule-editor-icon.svg) aus, um die Seite mit dem Regeleditor zu öffnen.
1. Definieren Sie eine Bedingung im Abschnitt [!UICONTROL Wenn] der Regel.
1. Wählen Sie im Abschnitt [!UICONTROL Dann] der Regel die Option **[!UICONTROL Dispatch-Ereignis]** aus der Dropdown-Liste **[!UICONTROL Aktion auswählen]**.
1. Geben Sie den Namen des Ereignisses im Feld **[!UICONTROL Ereignisname eingeben]** an.

Wenn beispielsweise das Geburtsdatum vor einem bestimmten Datum liegt, sendet AEM Forms das Ereignis **Sicherheit**.

![Dispatch-Ereignis](/help/forms/using/assets/security-event.png)

So ordnen Sie das Ereignis einem benutzerdefinierten Erfassungsereignis in [!DNL Adobe Analytics] zu:

1. [Erstellen einer Regel](#configure-rules).

1. Wählen Sie im Abschnitt **[!UICONTROL Ereignisse]** die Option **[!UICONTROL Hinzufügen]** aus.

1. Geben Sie **[!UICONTROL Adobe Experience Manager Forms]** als Name der Erweiterung an.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Ereignistyp]** die Option **[!UICONTROL Benutzerdefiniertes Ereignis erfassen]** aus.

1. Geben Sie den Namen des Ereignisses an, den Sie in Schritt 4 beim Erstellen einer Regel mit dem Regeleditor angegeben haben.

1. Wählen Sie **Änderungen beibehalten** aus und führen Sie die restlichen unter [Konfigurieren von Regeln](#configure-rules) angegebenen Aktionen aus.

## 3. Konfigurieren und Anzeigen von Berichten in [!DNL Adobe Analytics] {#view-reports-adobe-analytics}

Nachdem Sie ein adaptives Formular zum Senden von Ereignisdaten an [!DNL Adobe Analytics] konfiguriert haben, können Sie in [!DNL Adobe Analytics] Berichte anzeigen.

1. Wählen Sie ![Produkt auswählen](/help/forms/using/assets/select-analytics.png) und dann **[!UICONTROL Analytics]** aus.

1. Wählen Sie **[!UICONTROL Projekt erstellen]** und dann **[!UICONTROL Leeres Projekt]** aus.

1. Wählen Sie den Namen der Report Suite aus der Dropdown-Liste oben rechts im Freiformformular.

1. Geben Sie den **Formulartitel** im Text von **[!UICONTROL Dimensionselemente durchsuchen]** an, um alle Formulartitel anzuzeigen.

1. Fügen Sie den Titel des adaptiven Formulars in das Textfeld **[!UICONTROL Segment (oder eine andere Komponente) hier ablegen]** ein.

1. Legen Sie im Abschnitt **[!UICONTROL Metriken]** die zu verfolgenden Ereignisse in das Textfeld **[!UICONTROL Metrik (oder eine andere Komponente) hier ablegen]** ab.

1. Wählen Sie ![Visualisierungen](/help/forms/using/assets/visualization-icon.svg) aus und legen Sie einen Diagrammtyp im Abschnitt „Freiform“ ab. In ähnlicher Weise können Sie mehrere Diagrammtypen zum Abschnitt „Freiform“ hinzufügen.

1. Drücken Sie die Tasten Strg+S und geben Sie einen Namen an, um das Projekt zu speichern.

Ausführliche Informationen zur Anzeige von Formularanalyseberichten finden Sie unter [Anzeigen und Verstehen von AEM Forms-Analyseberichten](../../forms/using/view-understand-aem-forms-analytics-reports.md).
