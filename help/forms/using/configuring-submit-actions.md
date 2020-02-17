---
title: Konfigurieren der Sendeaktion
seo-title: Konfigurieren der Sendeaktion
description: Mit AEM Forms können Sie eine Übermittlungsaktion konfigurieren, um zu definieren, wie ein adaptives Formular nach der Übermittlung verarbeitet wird. Sie können integrierte Übermittlungsaktionen verwenden oder eigene von Grund auf neu schreiben.
seo-description: Mit AEM Forms können Sie eine Übermittlungsaktion konfigurieren, um zu definieren, wie ein adaptives Formular nach der Übermittlung verarbeitet wird. Sie können integrierte Übermittlungsaktionen verwenden oder eigene von Grund auf neu schreiben.
uuid: 4368d648-88ea-4f84-a051-46296a1a084e
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 9d8d7044-ffce-4ab4-9543-a2d2f9da31e3
docset: aem65
translation-type: tm+mt
source-git-commit: 6bd09bca68ea1fcec2dca7694dd3d39dc5153bfc

---


# Konfigurieren der Sendeaktion{#configuring-the-submit-action}

## Einführung in Übermittlungsaktionen {#introduction-to-submit-actions}

Eine Übermittlungsaktion wird ausgelöst, wenn ein Benutzer in einem adaptiven Formular auf die Schaltfläche „Senden“ klickt. Sie können die Übermittlungsaktion in einem adaptiven Formular konfigurieren. Adaptive Formulare umfassen auch einige Übermittlungsaktionen für den sofortigen Einsatz. Sie können die standardmäßige Übermittlungsaktion kopieren und erweitern und so eine eigene Übermittlungsaktion erstellen. Basierend auf Ihre Anforderungen können Sie eine eigene Übermittlungsaktion schreiben und registrieren, um Daten im gesendeten Formular zu verarbeiten. Die Übermittlungsaktion kann [synchrones oder asynchrones Senden](../../forms/using/asynchronous-submissions-adaptive-forms.md)verwenden.

Sie können eine Sendeaktion in der Seitenleiste im Bereich **Senden** des „Container für adaptive Formulare“ konfigurieren.

![Konfigurieren der Sendeaktion](assets/thank-you-setting.png)

Konfigurieren der Sendeaktion

Die folgenden Übermittlungsaktionen stehen in adaptiven Formularen standardmäßig zur Verfügung:

* An REST-Endpunkt übermitteln
* E-Mail senden
* PDF mittels E-Mail senden
* Workflow für Formulare aufrufen
* Senden mit Formulardatenmodell
* Übermittlungsaktion für Forms Portal
* AEM-Workflow aufrufen

>[!NOTE]
>
>Die Übermittlungsaktion „PDF mittels E-Mail senden“ steht nur in adaptiven Formularen zur Verfügung, die als Formularmodell XFA-Vorlagen verwenden.

>[!NOTE]
>
>Ensure that the [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder
>vorhanden. Das Verzeichnis wird benötigt, um Anhänge vorübergehend zu speichern. Wenn der Ordner nicht vorhanden ist, erstellen Sie ihn.

>[!CAUTION]
>
>If you [prefill](../../forms/using/prepopulate-adaptive-form-fields.md) a form template, form data model, or schema based adaptive form with XML or JSON data complaint to a schema (XML schema, JSON schema, form template, or form data model) that is data does not contain &lt;afData>, &lt;afBoundData>, and &lt;/afUnboundData> tags, then the data of unbounded fields (Unbounded fields are adaptive form fields without [bindref](../../forms/using/prepopulate-adaptive-form-fields.md) property) of the adaptive form is lost.

Sie können eine benutzerdefinierte Übermittlungsaktion für adaptive Formulare entsprechend des Anwendungsfalls schreiben. Weitere Informationen finden Sie unter[ Schreiben von benutzerdefinierten Übermittlungsaktionen für ein adaptives Formular](../../forms/using/custom-submit-action-form.md).

## An REST-Endpunkt übermitteln {#submit-to-rest-endpoint}

Die Übermittlungsoption **An REST-Endpunkt übermitteln** wird verwendet, wenn Sie die im Formular eingetragenen Daten zu einer konfigurierten Bestätigungsseite im Rahmen der http GET-Anforderung weiterleiten möchten. Sie können den Namen der Felder der Anforderung hinzufügen. Das Format der Anforderung lautet:

`{fieldName}={request parameter name}`

Wie in der folgenden Abbildung dargestellt, werden `param1` und `param2` als Parameter mit Werten weitergeleitet, die für die nächste Aktion aus den Feldern **textbox** und **numericbox** kopiert wurden.

Sie können auch **POST-Anforderungen aktivieren** und eine URL eingeben, um die Anforderung zu veröffentlichen. Um Daten an den AEM-Server, auf dem sich das Formular befindet, zu senden, verwenden Sie einen relativen Pfad entsprechend dem Stammpfad des AEM-Servers. Beispiel: /content/Forms/af/SampleForm.html. Wenn Sie Daten an einen Server senden, verwenden Sie den absoluten Pfad. 

![Konfigurieren der Sendeaktion „An REST-Endpunkt übermitteln“](assets/action-config.png)

Konfigurieren der Sendeaktion „An REST-Endpunkt übermitteln“

>[!NOTE]
Alle Felder müssen über verschiedene Elementnamen verfügen, um als Parameter in der REST-URL weitergeleitet zu werden, und zwar auch dann, wenn die Felder in verschiedene Bereiche platziert wurden.

### Veröffentlichen Sie übertragene Daten an eine Ressource oder an einen externen REST-Endpunkt  {#post-submitted-data-to-a-resource-or-external-rest-end-point-nbsp}

Verwenden Sie die Aktion **An REST-Endpunkt übermitteln**, um die übertragenen Daten an eine Rest-URL zu veröffentlichen. Die URL kann sich auf einem internen (der Server, auf dem das Formular wiedergegeben wird) oder auf einem externen Server befinden.

Stellen Sie den Pfad der Ressource bereit, um Daten an einen internen Server zu veröffentlichen. Die Daten werden an den Pfad der Ressource veröffentlicht. Beispiel: /content/restEndPoint. Für diese POST-Anforderungen werden die Authentifizierungsinformationen der Versandanfrage verwendet.

Stellen Sie die URL bereit, um Daten an einen externen Server zu veröffentlichen. Das Format der URL lautet https://host:port/path_to_rest_end_point. Stellen Sie sicher, dass Sie den Pfad zum Konfigurieren der POST-Anforderung anonym bearbeiten.

![Zuordnung zur Weitergabe von Feldwerten als Anforderungsparameter für die Danksagungsseite](assets/post-enabled-actionconfig.png)

In the example above, user entered information in `textbox` is captured using parameter `param1`. Syntax to post data captured using `param1` is:

`String data=request.getParameter("param1");`

Similarly, paramenters that you use for posting XML data and attachments are `dataXml` and `attachments`.

Beispielsweise können Sie diese beiden Parameter in Ihrem Skript verwenden, um Daten an einem Restendpunkt zu analysieren. Verwenden Sie die folgende Syntax, um Daten zu speichern und zu analysieren: 

`String data=request.getParameter("dataXml");`
`String att=request.getParameter("attachments");`

In diesem Beispiel speichert `data` die XML-Daten und `att` speichert Anlagendaten.

## E-Mail senden {#send-email}

The **Send Email** submit action sends an email to one or more recipients on successful submission of the form. Die generierte E-Mail kann Formulardaten in einem vordefinierten Formaten enthalten.

>[!NOTE]
Alle Formularfelder müssen über verschiedene Elementnamen verfügen, auch wenn sie in verschiedene Fenster platziert werden, um in eine E-Mail Formulardaten einzubinden.

## PDF mittels E-Mail senden {#send-pdf-via-email}

Bei der Übermittlungsaktion **PDF mittels E-Mail senden** wird bei erfolgreicher Übermittlung des Formulars an einen oder mehrere Empfänger eine mit einer PDF-Datei gesendet, die Formulardaten enthält.

**Hinweis:** Diese Übermittlungsaktion ist für XFA-basierte adaptive Formulare und XSD-basierte adaptive Formulare verfügbar, die das Dokument aus Datensatzvorlage enthalten.

## Workflow für Formulare aufrufen {#invoke-a-forms-workflow}

Bei der Übermittlungsoption **An Formular-Workflow übermitteln** werden eine Daten-XML und Dateianlagen (falls vorhanden) an einen vorhandenen Adobe LiveCycle- oder AEM Forms on JEE-Prozess gesendet.

Weitere Informationen zum Konfigurieren der Sendeaktion „An Formular-Workflow übermitteln“ finden Sie unter [Senden und Verarbeiten Ihrer Formulardaten mit Formular-Workflows](../../forms/using/submit-form-data-livecycle-process.md).

## Senden mit Formulardatenmodell {#submit-using-form-data-model}

The **Submit using Form Data Model** submit action writes submitted adaptive form data for the specified data model object in a form data model to its data source. Beim Konfigurieren der Übermittlungsaktion können Sie ein Datenmodellobjekt auswählen, dessen übermittelte Daten in die Datenquelle zurückgeschrieben werden sollen.

Darüber hinaus können Sie einen Formularanhang mit einem Formulardatenmodell und einem Datensatzdokument (Document of Record) an die Datenquelle senden.

Weitere Informationen zum Formulardatenmodell finden Sie unter [Datenintegration für AEM Forms](../../forms/using/data-integration.md).

## Übermittlungsaktion für Forms Portal {#forms-portal-submit-action}

Mit der Option **Übermittlungsaktion für Forms Portal** werden über das AEM Forms-Portal Formulardaten zur Verfügung gestellt.

Weitere Informationen zur Übermittlungsaktion für Forms Portal finden Sie unter [Komponente für Formular und übermittelte Formulare](../../forms/using/draft-submission-component.md).

## AEM-Workflow aufrufen {#invoke-an-aem-workflow}

Die Übermittlungsaktion **AEM-Workflow aufrufen** verknüpft ein adaptives Formular mit einem AEM-Workflow. Wenn ein Formular gesendet wird, startet der verknüpfte Workflow automatisch auf dem Verarbeitungsknoten. Darüber hinaus speichert er die Datendatei, Anhänge und das Datensatzdokument (falls vorhanden) im Nutzlastspeicherort des Workflows.

Vor der Verwendung von **AEM-Workflow aufrufen** [konfigurieren Sie die AEM-DS-Einstellungen](../../forms/using/configuring-the-processing-server-url-.md). Weitere Informationen zum Erstellen eines AEM-Workflow finden Sie unter [Formularorientierte Workflows auf OSGi](../../forms/using/aem-forms-workflow.md).

## Serverseitige Überprüfung im adaptiven Formular {#server-side-revalidation-in-adaptive-form}

Normalerweise platzieren Entwickler in jedem Onlinedatenerfassungssystem einige Javascript-Validierungen auf der Clientseite, um Geschäftsregeln durchzusetzen. Moderne Browser bieten Endbenutzern Möglichkeiten, diese Validierungen zu umgehen und Übermittlungen mithilfe verschiedener Techniken wie beispielsweise die Web Browser DevTools-Konsole manuell durchzuführen. Diese Techniken sind auch für adaptive Formulare gültig. Ein Formularentwickler kann verschiedene Validierungslogiken erstellen, aber Endbenutzer können diese Validierungslogiken technisch umgehen und ungültige Daten an den Server leiten. Ungültige Daten verstoßen gegen die Geschäftsregeln, die der Formularautor durchgesetzt hat.

Die Funktion für erneute serverseitige Überprüfung enthält die Möglichkeit, auch Validierungen durchzuführen, die von einem Autor für adaptive Formulare beim Entwerfen eines adaptiven Formulars auf dem Server bereitgestellt wurden. Sie verhindert jede mögliche Beeinträchtigung von Datenübertragungen und Verstöße gegen Geschäftsregeln, die in Form von Formularvalidierungen auftreten können.

### Was soll auf dem Server validiert werden? {#what-to-validate-on-server-br}

Alle sofort einsetzbaren Feldvalidierungen eines adaptiven Formulars, die erneut auf dem Server ausgeführt werden:

* Erforderlich
* Validierung-Picture-Klausel
* Überprüfungsausdruck

### Aktivieren von serverseitiger Validierung {#enabling-server-side-validation-br}

Verwenden Sie das Kontrollkästchen **Auf dem Server erneut überprüfen** im „Container für adaptive Formulare“ in der Seitenleiste, um die serverseitige Validierung für das aktuelle Formular zu aktivieren oder zu deaktivieren.

![Aktivieren von serverseitiger Validierung](assets/revalidate-on-server.png)

Aktivieren von serverseitiger Validierung

Wenn der Endbenutzer diese Validierungen umgeht und die Formulare übermittelt, führt der Server die Validierung erneut aus. Wenn die Überprüfung serverseitig fehlschlägt, wird die Übermittlung abgebrochen. Dem Endbenutzer wird wieder das ursprüngliche Formular präsentiert. Die erfassten Daten und die gesendeten Daten werden dem Benutzer als Fehler angezeigt. 

### Unterstützende benutzerdefinierte Funktionen in Überprüfungsausdrücken {#supporting-custom-functions-in-validation-expressions-br}

Bisweilen befindet sich bei komplexen **Validierungsregeln** das exakte Validierungsskript in den benutzerdefinierten Funktionen. Der Autor kann diese benutzerdefinierten Funktionen über den Ausdrück für die Feldvalidierung abrufen. To make this custom function library known and available while performing server-side validations, the form author can configure the name of AEM client library under the **Basic** tab of Adaptive Form Container properties as shown below.

![Unterstützende benutzerdefinierte Funktionen in Überprüfungsausdrücken](assets/clientlib-cat.png)

Unterstützende benutzerdefinierte Funktionen in Überprüfungsausdrücken

Autor kann benutzerdefinierte JavaScript-Bibliothek pro adaptivem Formular konfigurieren. Bewahren Sie in der Bibliothek nur die wiederverwendbaren Funktionen, die von den Drittanbieter-Bibliotheken „jquery“ und „underscore“ abhängen.

## Verhalten bei fehlerhaften Übermittlungsaktionen {#error-handling-on-submit-action}

Konfigurieren Sie im Rahmen der AEM-Richtlinie für Sicherheit und Beschränkungen benutzerdefinierte Seiten für die Fehler 404.jsp und 500.jsp. Diese Handler werden aufgerufen, wenn beim Übermitteln des Formulars 404 oder 500 Fehler auftreten. Die Handler werden auch aufgerufen, wenn diese Fehlercodes auf einem Veröffentlichungsknoten ausgelöst werden.

For more information, see [Customizing Pages shown by the Error Handler](/help/sites-developing/customizing-errorhandler-pages.md).
