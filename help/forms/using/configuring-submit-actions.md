---
title: Konfigurieren der Sendeaktion
seo-title: Configuring the Submit action
description: Mit Forms können Sie eine Übermittlungsaktion konfigurieren, um zu definieren, wie ein adaptives Formular nach der Übermittlung verarbeitet wird. Sie können integrierte Übermittlungsaktionen verwenden oder eigene von Grund auf neu schreiben.
uuid: 4368d648-88ea-4f84-a051-46296a1a084e
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 9d8d7044-ffce-4ab4-9543-a2d2f9da31e3
docset: aem65
feature: Adaptive Forms
exl-id: 04efb4ad-cff6-4e05-bcd2-98102f052452
source-git-commit: d9608d584e822accc0c198fcf1d1b706d065938e
workflow-type: tm+mt
source-wordcount: '1870'
ht-degree: 72%

---

# Konfigurieren der Sendeaktion{#configuring-the-submit-action}

## Einführung in Übermittlungsaktionen {#introduction-to-submit-actions}

Eine Übermittlungsaktion wird ausgelöst, wenn ein Benutzer in einem adaptiven Formular auf die Schaltfläche „Senden“ klickt. Sie können die Übermittlungsaktion in einem adaptiven Formular konfigurieren. Adaptive Formulare umfassen auch einige Übermittlungsaktionen für den sofortigen Einsatz. Sie können die standardmäßigen Sendeaktionen kopieren und erweitern, um eine eigene Sendeaktion zu erstellen. Basierend auf Ihre Anforderungen können Sie eine eigene Übermittlungsaktion schreiben und registrieren, um Daten im gesendeten Formular zu verarbeiten. Die Übermittlungsaktion kann [synchrone oder asynchrone Übermittlung](../../forms/using/asynchronous-submissions-adaptive-forms.md).

Sie können eine Sendeaktion in der Seitenleiste im Bereich **Senden** des „Container für adaptive Formulare“ konfigurieren.

![Konfigurieren der Übermittlungsaktion](assets/thank-you-setting.png)

Konfigurieren der Übermittlungsaktion

Die folgenden Übermittlungsaktionen stehen in adaptiven Formularen standardmäßig zur Verfügung:

* An REST-Endpunkt übermitteln
* E-Mail senden
* PDF mittels E-Mail senden
* Workflow für Formulare aufrufen
* Senden mit Formulardatenmodell
* Übermittlungsaktion für Forms Portal
* AEM Workflow aufrufen

>[!NOTE]
>
>Die Übermittlungsaktion „PDF mittels E-Mail senden“ steht nur in adaptiven Formularen zur Verfügung, die als Formularmodell XFA-Vorlagen verwenden.

>[!NOTE]
>
>Stellen Sie sicher, dass [AEM_Installationsverzeichnis]\crx-quickstart\temp\datamanager\ASM folder
>vorhanden. Das Verzeichnis wird benötigt, um Anhänge vorübergehend zu speichern. Wenn der Ordner nicht vorhanden ist, erstellen Sie ihn.

>[!CAUTION]
>
>Wenn Sie [prefill](../../forms/using/prepopulate-adaptive-form-fields.md) eine Formularvorlage, ein Formulardatenmodell oder ein schemabasiertes adaptives Formular mit XML- oder JSON-Daten, die sich auf ein Schema (XML-Schema, JSON-Schema, Formularvorlage oder Formulardatenmodell) beziehen, das keine Daten enthält &lt;afdata>, &lt;afbounddata>und &lt;/afunbounddata> Tags, dann sind die Daten von nicht gebundenen Feldern (ungebundene Felder sind adaptive Formularfelder ohne [bindref](../../forms/using/prepopulate-adaptive-form-fields.md) -Eigenschaft) des adaptiven Formulars verloren.

Sie können eine benutzerdefinierte Sendeaktion für adaptive Formulare schreiben, um Ihren Anwendungsfall zu erfüllen. Weitere Informationen finden Sie unter[ Schreiben von benutzerdefinierten Übermittlungsaktionen für ein adaptives Formular](../../forms/using/custom-submit-action-form.md).

## An REST-Endpunkt übermitteln {#submit-to-rest-endpoint}

Die Übermittlungsoption **An REST-Endpunkt übermitteln** wird verwendet, wenn Sie die im Formular eingetragenen Daten zu einer konfigurierten Bestätigungsseite im Rahmen der http GET-Anforderung weiterleiten möchten. Sie können den Namen der Felder der Anforderung hinzufügen. Das Format der Anforderung lautet:

`{fieldName}={request parameter name}`

Wie in der Abbildung unten gezeigt, `param1` und `param2` werden als Parameter mit Werten übergeben, die aus dem **Textfeld** und **numerisches Feld** Felder für die nächste Aktion.

Sie können auch **POST-Anforderungen aktivieren** und eine URL eingeben, um die Anforderung zu veröffentlichen. Um Daten an den Experience Manager-Server zu senden, auf dem das Formular gehostet wird, verwenden Sie einen relativen Pfad, der dem Stammpfad des Experience Manager-Servers entspricht. Beispiel: /content/Forms/af/SampleForm.html. Wenn Sie Daten an irgendeinen anderen Server senden, verwenden Sie den absoluten Pfad.

![Konfigurieren der Übermittlungsaktion „An REST-Endpunkt übermitteln“](assets/action-config.png)

Konfigurieren der Übermittlungsaktion „An REST-Endpunkt übermitteln“

>[!NOTE]
Alle Felder müssen über verschiedene Elementnamen verfügen, um als Parameter in der REST-URL weitergeleitet zu werden, auch dann, wenn die Felder in verschiedenen Bereichen platziert sind.

### Veröffentlichen Sie übertragene Daten an eine Ressource oder an einen externen REST-Endpunkt  {#post-submitted-data-to-a-resource-or-external-rest-end-point-nbsp}

Verwenden Sie die Aktion **An REST-Endpunkt übermitteln**, um die übertragenen Daten an eine Rest-URL zu veröffentlichen. Die URL kann sich auf einem internen (dem Server, auf dem das Formular gerendert wird) oder auf einem externen Server befinden.

Stellen Sie den Pfad der Ressource bereit, um Daten an einen internen Server zu veröffentlichen. Die Daten werden an den Pfad der Ressource veröffentlicht. Beispiel: /content/restEndPoint. Für diese POST-Anforderungen werden die Authentifizierungsinformationen der Versandanfrage verwendet.

Stellen Sie die URL bereit, um Daten an einen externen Server zu veröffentlichen. Das Format der URL lautet https://host:port/path_to_rest_end_point. Stellen Sie sicher, dass Sie den Pfad zum Handhaben der POST-Anforderung anonym konfigurieren.

![Zuordnung zur Weitergabe von Feldwerten als Anforderungsparameter für die Dankeseite](assets/post-enabled-actionconfig.png)

Im obigen Beispiel hat der Benutzer Informationen in die `textbox` eingegeben, die mithilfe von Parameter `param1` erfasst werden. Die Syntax zur Veröffentlichung erfasster Daten mithilfe von `param1` lautet:

`String data=request.getParameter("param1");`

Auch Parameter, die Sie für die Veröffentlichung von XML-Daten und Anlagen verwenden, sind `dataXml` und `attachments`.

Beispielsweise können Sie diese beiden Parameter in Ihrem Skript verwenden, um Daten an einem Restendpunkt zu analysieren. Verwenden Sie die folgende Syntax, um Daten zu speichern und zu analysieren:

`String data=request.getParameter("dataXml");`
`String att=request.getParameter("attachments");`

In diesem Beispiel speichert `data` die XML-Daten, und `att` speichert Anlagendaten.

## E-Mail senden {#send-email}

Die **E-Mail senden** bei erfolgreicher Übermittlung des Formulars eine E-Mail an einen oder mehrere Empfänger gesendet wird. Die generierte E-Mail kann Formulardaten in einem vordefinierten Format enthalten.

>[!NOTE]
Alle Formularfelder müssen über verschiedene Elementnamen verfügen, auch wenn sie in verschiedene Fenster platziert werden, um in eine E-Mail Formulardaten einzubinden.

## PDF mittels E-Mail senden {#send-pdf-via-email}

Bei der Übermittlungsaktion **PDF mittels E-Mail senden** wird bei erfolgreicher Übermittlung des Formulars an einen oder mehrere Empfänger eine mit einer PDF-Datei gesendet, die Formulardaten enthält.

>[!NOTE]
Diese Übermittlungsaktion ist für XFA-basierte adaptive Formulare und XSD-basierte adaptive Formulare verfügbar, die über die Vorlage &quot;Datensatzdokument&quot;verfügen.

## Workflow für Formulare aufrufen {#invoke-a-forms-workflow}

Die **An Forms Workflow übermitteln** Die Sendeoption sendet eine Daten-XML und Dateianlagen (falls vorhanden) an einen vorhandenen Adobe LiveCycle- oder AEM Forms on JEE-Prozess.

Informationen zum Konfigurieren der Sendeaktion &quot;An Forms Workflow übermitteln&quot;finden Sie unter [Senden und Verarbeiten Ihrer Formulardaten mithilfe von Formular-Workflows](../../forms/using/submit-form-data-livecycle-process.md).

## Senden mit Formulardatenmodell {#submit-using-form-data-model}

Die **Senden mit Formulardatenmodell** Aktion &quot;submit&quot;schreibt gesendete adaptive Formulardaten für das angegebene Datenmodellobjekt in einem Formulardatenmodell in seine Datenquelle. Beim Konfigurieren der Übermittlungsaktion können Sie ein Datenmodellobjekt auswählen, dessen übermittelte Daten in die Datenquelle zurückgeschrieben werden sollen.

Darüber hinaus können Sie einen Formularanhang mit einem Formulardatenmodell und einem Datensatzdokument (Document of Record) an die Datenquelle senden.

Weitere Informationen zum Formulardatenmodell finden Sie unter [Datenintegration für AEM Forms](../../forms/using/data-integration.md).

## Übermittlungsaktion für Forms Portal {#forms-portal-submit-action}

Die **Übermittlungsaktion für Forms Portal** ermöglicht die Bereitstellung von Formulardaten über ein AEM Forms-Portal.

Weitere Informationen zur Übermittlungsaktion für Forms Portal finden Sie unter [Komponente für Formular und übermittelte Formulare](../../forms/using/draft-submission-component.md).

## AEM-Workflow aufrufen {#invoke-an-aem-workflow}

Die Übermittlungsaktion **[!UICONTROL AEM-Workflow aufrufen]** verknüpft ein adaptives Formular mit einem [AEM-Workflow](/help/sites-developing/workflows-models.md). Wenn ein Formular gesendet wird, startet der verknüpfte Workflow automatisch auf der Autoreninstanz. Sie können die Datendatei, die Anhänge und das Datensatzdokument in dem Ordner relativ oder unter der Payload des Workflows oder in einer Variablen speichern. Wenn der Workflow für die externe Datenspeicherung markiert ist, ist die Variablenoption verfügbar und nicht die Nutzlastoption. Sie können aus der Liste der für das Workflow-Modell verfügbaren Variablen auswählen. Wenn der Workflow für die externe Datenspeicherung zu einem späteren Zeitpunkt und nicht zum Zeitpunkt der Workflow-Erstellung markiert ist, stellen Sie sicher, dass die erforderlichen Variablenkonfigurationen vorhanden sind.

Vor der Verwendung von **Aufrufen eines AEM-Workflows** Sendeaktion, [Konfigurieren der Experience Manager DS-Einstellungen](../../forms/using/configuring-the-processing-server-url-.md). Weitere Informationen zum Erstellen eines AEM-Workflow finden Sie unter [Formularorientierte Workflows auf OSGi](../../forms/using/aem-forms-workflow.md).

Die Übermittlungsaktion platziert Folgendes am Payload-Speicherort des Workflows. Beachten Sie jedoch, dass nur die Option Variable angezeigt wird, wenn das Workflow-Modell für die externe Datenspeicherung markiert ist, und nicht die Payload-Option.

* **Datendatei**: Sie enthält Daten, die an das adaptive Formular gesendet werden. Mit der Option **[!UICONTROL Datendateipfad]** können Sie den Dateinamen und den Dateipfad relativ zur Payload angeben. Beispielsweise erstellt der Pfad `/addresschange/data.xml` einen Ordner mit dem Namen `addresschange` und platziert ihn relativ zur Payload. Sie können auch nur `data.xml` angeben, um nur die übermittelten Daten zu senden, ohne die Erstellung einer Ordnerhierarchie. Verwenden Sie die Variablenoption und wählen Sie die Variable aus der Liste der für das Workflow-Modell verfügbaren Variablen aus.

>[!NOTE]
Variablen können unabhängig davon verwendet werden, ob das Workflow-Modell für die externe Datenspeicherung markiert ist oder nicht.

* **Anlagen**: Mit der Option **[!UICONTROL Anlagenpfad]** können Sie den Ordnernamen zum Speichern der in das adaptive Formular hochgeladenen Anlagen angeben. Der Ordner wird immer relativ zur Payload erstellt. Wenn der Workflow für die externe Datenspeicherung markiert ist, verwenden Sie die Variablenoption und wählen Sie die Variable aus der Liste der Variablen aus, die für das Workflow-Modell verfügbar sind.

* **Datensatzdokument**: Es enthält das Datensatzdokument, das für das adaptive Formular generiert wurde. Mit der Option **[!UICONTROL Pfad des Datensatzdokuments]** können Sie den Dateinamen des Datensatzdokuments sowie den Dateipfad relativ zur Payload angeben. Beispiel: Der Pfad `/addresschange/DoR.pdf` erstellt einen Ordner mit dem Namen `addresschange` relativ zur Payload und platziert `DoR.pdf` relativ zur Payload. Um nur das Datensatzdokument zu speichern, ohne eine Ordnerhierarchie zu erstellen, reicht die Angabe `DoR.pdf`. Wenn der Workflow für die externe Datenspeicherung markiert ist, verwenden Sie die Variablenoption und wählen Sie die Variable aus der Liste der Variablen aus, die für das Workflow-Modell verfügbar sind.

## Server-seitige Überprüfung im adaptiven Formular {#server-side-revalidation-in-adaptive-form}

Normalerweise platzieren Entwickler in jedem Online-Datenerfassungssystem einige Javascript-Validierungen auf Client-Seite, um Geschäftsregeln durchzusetzen. Moderne Browser bieten Endbenutzern jedoch Möglichkeiten, diese Validierungen zu umgehen und Übermittlungen mithilfe verschiedener Techniken wie beispielsweise die Web Browser DevTools-Konsole manuell durchzuführen. Solche Techniken sind auch für adaptive Formulare gültig. Ein Formularentwickler kann verschiedene Validierungslogiken erstellen, aber Endbenutzer können diese Validierungslogiken technisch umgehen und ungültige Daten an den Server leiten. Ungültige Daten verstoßen gegen die Geschäftsregeln, die der Formularautor durchgesetzt hat.

Die Funktion für erneute serverseitige Überprüfung enthält die Möglichkeit, auch Validierungen durchzuführen, die von einem Autor für adaptive Formulare beim Entwerfen eines adaptiven Formulars auf dem Server bereitgestellt wurden. Sie verhindert jede mögliche Beeinträchtigung von Datenübertragungen und Verstöße gegen Geschäftsregeln, die hinsichtlich Formularvalidierungen auftreten können.

### Was soll auf dem Server validiert werden? {#what-to-validate-on-server-br}

Alle vordefinierten Feldvalidierungen (OOTB) eines adaptiven Formulars, die erneut auf dem Server ausgeführt werden, sind:

* Erforderlich
* Validierung-Picture-Klausel
* Überprüfungsausdruck

### Aktivieren von Server-seitiger Validierung {#enabling-server-side-validation-br}

Verwenden Sie das Kontrollkästchen **Auf dem Server erneut überprüfen** im Container für adaptive Formulare in der Seitenleiste, um die Server-seitige Validierung für das aktuelle Formular zu aktivieren oder zu deaktivieren.

![Aktivieren von Server-seitiger Validierung](assets/revalidate-on-server.png)

Aktivieren von Server-seitiger Validierung

Wenn der Endbenutzer diese Validierungen umgeht und die Formulare übermittelt, führt der Server die Validierung erneut aus. Wenn die Validierung Server-seitig fehlschlägt, wird die Übermittlung abgebrochen. Dem Endbenutzer wird das ursprüngliche Formular erneut präsentiert. Die erfassten Daten und die gesendeten Daten werden dem Benutzer als Fehler angezeigt.

>[!NOTE]
Die Server-seitige Validierung prüft das Formularmodell. Es wird empfohlen, eine separate Client-Bibliothek für Überprüfungen zu erstellen und sie nicht mit anderen Elementen wie HTML-Stil und DOM-Manipulation in derselben Client-Bibliothek zu mischen.

### Unterstützende benutzerdefinierte Funktionen in Validierungsausdrücken {#supporting-custom-functions-in-validation-expressions-br}

Bisweilen befindet sich bei komplexen Validierungsregeln das exakte Validierungsskript in den benutzerdefinierten Funktionen. Der Autor kann diese benutzerdefinierten Funktionen über den Ausdruck für die Feldvalidierung abrufen. Um diese benutzerdefinierte Funktionsbibliothek bei Server-seitigen Validierungen bekannt und verfügbar zu machen, kann der Formularautor den Namen der AEM-Client-Bibliothek auf der Registerkarte **Allgemein** des Dialogfelds „Container für adaptive Formulare bearbeiten“, wie nachfolgend dargestellt konfigurieren.

![Unterstützende benutzerdefinierte Funktionen in Validierungsausdrücken](assets/clientlib-cat.png)

Unterstützende benutzerdefinierte Funktionen in Validierungsausdrücken

Der Autor kann die benutzerdefinierte JavaScript-Bibliothek für jedes adaptive Formular konfigurieren. Legen Sie in der Bibliothek nur die wiederverwendbaren Funktionen ab, die von den Drittanbieter-Bibliotheken „jquery“ und „underscore“ abhängen.

## Verhalten bei fehlerhaften Übermittlungsaktionen {#error-handling-on-submit-action}

Konfigurieren Sie als Teil der Experience Manager-Richtlinien für Sicherheit und Härtung benutzerdefinierte Fehlerseiten wie 404.jsp und 500.jsp. Diese Handler werden aufgerufen, wenn beim Übermitteln des Formulars 404 oder 500 Fehler auftreten. Die Handler werden auch aufgerufen, wenn diese Fehler-Codes auf einem Veröffentlichungsknoten ausgelöst werden.

Weitere Informationen finden Sie unter [Anpassen der vom Fehler-Handler angezeigten Seiten](/help/sites-developing/customizing-errorhandler-pages.md).
