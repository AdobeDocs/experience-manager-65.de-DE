---
title: Variablen in AEM-Workflows
seo-title: Variablen in AEM-Workflows
description: Erstellen Sie eine Variable, legen Sie einen Wert für die Variable fest und verwenden Sie sie in den Arbeitsablaufschritten OR Split und Goto AEM.
seo-description: Erstellen Sie eine Variable, legen Sie einen Wert für die Variable fest und verwenden Sie sie in den Arbeitsablaufschritten OR Split und Goto AEM.
uuid: cc62ff11-51d4-4db4-9c6d-5dc2caa1da52
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: bbb9936e-ecd2-44b3-b4ae-dd62a3160641
docset: aem65
translation-type: tm+mt
source-git-commit: bc042696506bf1691c2eeffc6ab941be85fa274c

---


# Variablen in AEM-Workflows{#variables-in-aem-workflows}

Eine Variable in einem Workflow-Modell ist eine Methode, einen Wert basierend auf seinem Datentyp zu speichern. Anschließend können Sie den Namen der Variablen in jedem Workflow-Schritt verwenden, um den in der Variablen gespeicherten Wert abzurufen. Sie können auch Variablennamen verwenden, um Ausdrücke für Routingentscheidungen zu definieren.

In AEM-Workflow-Modellen können Sie:

* [Erstellen Sie eine Variable](/help/sites-developing/using-variables-in-aem-workflows.md#create-a-variable) eines Datentyps basierend auf dem Informationstyp, den Sie darin speichern möchten.
* [Legen Sie einen Wert für die Variable](/help/sites-developing/using-variables-in-aem-workflows.md#set-a-variable) im Arbeitsablaufschritt &quot;Variable festlegen&quot;fest.
* [Verwenden Sie die Variable](/help/sites-developing/using-variables-in-aem-workflows.md#use-a-variable) in den Arbeitsablaufschritten &quot;OR Split&quot;und &quot;Goto AEM&quot;, um einen Ausdruck für Routing-Entscheidungen zu definieren. Sie können auch Variablen in allen Arbeitsablaufschritten von AEM Forms verwenden.

Das folgende Video zeigt, wie Sie Variablen in AEM-Workflow-Modellen erstellen, festlegen und verwenden können:

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/usevariables_example.mp4)

Variablen sind eine Erweiterung der [MetaDataMap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) -Schnittstelle. Mit [MetaDataMap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) in ECMAScript können Sie auf Metadaten zugreifen, die mit Variablen gespeichert wurden.

## Variable erstellen {#create-a-variable}

Sie erstellen Variablen mithilfe des Abschnitts &quot;Variablen&quot;im Sidekick des Workflow-Modells. AEM-Workflow-Variablen unterstützen die folgenden Datentypen:

* **Primitive-Datentypen**: Long, Double, Boolean, Date und String
* **Komplexe Datentypen**: [XML](https://docs.oracle.com/javase/8/docs/api/org/w3c/dom/Document.html) und [JSON](https://static.javadoc.io/com.google.code.gson/gson/2.3/com/google/gson/JsonObject.html)

>[!NOTE]
>
>Workflows unterstützen nur das ISO8601-Format für Datumsvariablen.

Weitere komplexe Datentypen, die in AEM Forms-Workflows verfügbar sind, finden Sie unter [Variablen in AEM Forms-Workflows](/help/forms/using/variable-in-aem-workflows.md).  Verwenden Sie den ArrayList-Datentyp, um variable Sammlungen zu erstellen. Sie können ArrayList-Variablen für alle primitiven und komplexen Datentypen erstellen. Erstellen Sie beispielsweise eine ArrayList-Variable und wählen Sie String als Untertyp aus, um mehrere Zeichenfolgenwerte mit der Variablen zu speichern.

Führen Sie die folgenden Schritte aus, um eine Variable zu erstellen:

1. Navigieren Sie in einer AEM-Instanz zu &quot;Extras&quot;> &quot;Workflow&quot;> &quot;Modelle&quot;.
1. Tippen Sie auf **[!UICONTROL Erstellen]** und geben Sie den Titel und einen optionalen Namen für das Workflow-Modell an. Wählen Sie das Modell aus und tippen Sie auf **[!UICONTROL Bearbeiten]**.
1. Tippen Sie auf das Variablensymbol im Sidekick des Workflow-Modells und dann auf Variable **[!UICONTROL hinzufügen]**.

   ![Variable hinzufügen](assets/variables_add_variable_new.png)

1. Geben Sie im Dialogfeld &quot;Variable hinzufügen&quot;den Namen ein und wählen Sie den Variablentyp aus.
1. Wählen Sie den Datentyp aus der Dropdownliste **[!UICONTROL Typ]** aus und geben Sie die folgenden Werte an:

   * Primitive-Datentyp - Geben Sie einen optionalen Standardwert für die Variable an.
   * JSON oder XML - Geben Sie einen optionalen JSON- oder XML-Schemapfad an. Das System überprüft den Schemapfad, während die in diesem Schema verfügbaren Eigenschaften einer anderen Variablen zugeordnet und gespeichert werden.
   * Formulardatenmodell: Geben Sie einen Pfad für ein Formulardatenmodell an.
   * ArrayList - Geben Sie einen Untertyp für die Sammlung an.

1. Geben Sie eine optionale Beschreibung für die Variable ein und tippen Sie auf , ![](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) um die Änderungen zu speichern. Die Variable wird in der Liste im linken Bereich angezeigt.

Berücksichtigen Sie beim Erstellen von Variablen die folgenden Vorgehensweisen:

* Erstellen Sie so viele Variablen, wie ein Workflow erfordert. Um jedoch Datenbankressourcen zu schonen, sollten Sie die Anzahl der Variablen auf das erforderliche Minimum beschränken und Variablen nach Möglichkeit wiederverwenden.
* Bei Variablen wird zwischen Groß- und Kleinbuchstaben unterschieden. Vergewissern Sie sich, dass Sie Variablen mit derselben Groß-/Kleinschreibung in Ihrem Workflow referenzieren.
* Verwenden Sie keine Sonderzeichen im Namen der Variablen

## Variable festlegen {#set-a-variable}

Mit dem Schritt &quot;Variable festlegen&quot;können Sie den Wert einer Variablen festlegen und die Reihenfolge festlegen, in der die Werte festgelegt werden. Die Variable wird in der Reihenfolge festgelegt, in der die Variablenzuordnungen im Schritt der set-Variablen aufgeführt werden.

Änderungen an Variablenwerten betreffen nur die Instanz des Prozesses, in der die Änderung erfolgt. Wenn beispielsweise ein Workflow initiiert wird und sich die Variablendaten ändern, wirken sich die Änderungen nur auf diese Instanz des Workflows aus. Die Änderungen wirken sich nicht auf andere Instanzen des Workflows aus, die zuvor initiiert wurden oder später initiiert werden.

Je nach Datentyp der Variablen können Sie die folgenden Optionen verwenden, um den Wert einer Variablen festzulegen:

* **Literal:** Verwenden Sie die Option, wenn Sie den genauen, zu spezifizierenden Wert kennen.
* **** Ausdruck: Verwenden Sie die Option, wenn der zu verwendende Wert auf Grundlage eines Ausdrucks berechnet wird. Der Ausdruck wird im angegebenen Ausdruckseditor erstellt.
* **** JSON-Punktnotiz: Verwenden Sie die Option, um einen Wert aus einer JSON- oder FDM-Typvariablen abzurufen.
* **** XPATH: Verwenden Sie die Option, um einen Wert aus einer XML-Typvariablen abzurufen.
* **** Im Verhältnis zur Nutzlast: Verwenden Sie die Option, wenn der in einer Variablen zu speichernde Wert unter einem Pfad relativ zur Nutzlast verfügbar ist.
* **** Absoluter Pfad: Verwenden Sie die Option, wenn der in einer Variablen zu speichernde Wert unter einem absoluten Pfad verfügbar ist.

Sie können auch bestimmte Elemente einer JSON- oder XML-Typvariablen mithilfe der JSON-DOT-Notation oder XPATH-Notation aktualisieren.

### Zuordnung zwischen Variablen hinzufügen {#add-mapping-between-variables}

Führen Sie die folgenden Schritte aus, um die Zuordnung zwischen Variablen hinzuzufügen:

1. Tippen Sie auf der Seite zum Bearbeiten des Workflows auf das Symbol Schritte, das im Sidekick des Workflow-Modells verfügbar ist.
1. Ziehen Sie den Schritt **Variable** festlegen in den Workflow-Editor, tippen Sie auf den Schritt und wählen Sie ![](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/configure_icon.png) (Konfigurieren).
1. Wählen Sie im Dialogfeld &quot;Variable festlegen&quot; **[!UICONTROL Zuordnung]** > Zuordnung **[!UICONTROL hinzufügen]**.
1. Wählen Sie im Abschnitt **Zuordnungsvariable** die zu speichernde Variable aus, wählen Sie den Zuordnungsmodus und geben Sie einen Wert an, der in der Variablen gespeichert werden soll. Die Zuordnungsmodi variieren je nach Variablentyp.
1. Ordnen Sie weitere Variablen zu, um einen aussagekräftigen Ausdruck zu erstellen. Tap ![](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) to save the changes.

### Beispiel 1: Abfragen einer XML-Variable zum Festlegen eines Werts für eine Zeichenfolgenvariable {#example-query-an-xml-variable-to-set-value-for-a-string-variable}

Wählen Sie eine Variable des XML-Typs aus, um eine XML-Datei zu speichern. Abfragen der XML-Variable, um den Wert für eine Zeichenfolgenvariable für die in der XML-Datei verfügbare Eigenschaft festzulegen. Verwenden Sie **XPATH für das XML-Variablenfeld** angeben, um die Eigenschaft zu definieren, die in der Zeichenfolgenvariablen gespeichert werden soll.

Wählen Sie in diesem Beispiel eine XML-Variable für **Formulardaten** aus, um die Datei &quot; **cc-app.xml** &quot;zu speichern. Abfragen Sie die **Variable &quot;formdata** &quot;, um den Wert für die **Zeichenfolgenvariable &quot;emailaddress** &quot;festzulegen, um den Wert für die Eigenschaft &quot; **emailAddress** &quot;zu speichern, die in der Datei &quot; **cc-app.xml** &quot;verfügbar ist.

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/set_variable_example1.mp4 "Wert einer Variablen festlegen")

### Beispiel 2: Verwenden Sie einen Ausdruck, um Werte basierend auf anderen Variablen zu speichern {#example2}

Verwenden Sie einen Ausdruck, um die Summe der Variablen zu berechnen und das Ergebnis in einer Variablen zu speichern.

In diesem Beispiel verwenden Sie den Ausdruckseditor, um einen Ausdruck zu definieren, um die Summe der **Assetkosten** - und **Bilanzsummenvariablen** zu berechnen und das Ergebnis in der Variablen **totalvalue** zu speichern.

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_expression.mp4)

## Ausdruckseditor verwenden {#use-expression-editor}

Sie können auch Ausdrücke verwenden, um den Wert einer Variablen zur Laufzeit zu berechnen. Variablen bieten einen Ausdruckseditor zum Definieren von Ausdrücken.

Verwenden Sie den Ausdruckseditor, um:

* Legen Sie den Wert von Variablen mit anderen Workflow-Variablen, Zahlen oder mathematischen Ausdrücken fest.
* Verwenden Sie Workflow-Variablen, Zeichenfolge, Zahl oder einen Ausdruck in einem mathematischen Ausdruck
* Fügen Sie Bedingungen hinzu, um Variablenwerte festzulegen.
* Fügen Sie Operatoren zwischen Bedingungen hinzu.

![Ausdruckseditor](assets/variables_expression_editor_new.png)

Er basiert auf dem Regeleditor für adaptive Formulare mit folgenden Änderungen. Regeleditor in Variablen:

* Unterstützt keine Funktionen.
* Bietet keine Benutzeroberfläche zum Anzeigen einer Regelzusammenfassung
* Hat keinen Code-Editor.
* Aktiviert und deaktiviert den Wert eines Objekts nicht.
* Die Eigenschaft zum Festlegen eines Objekts wird nicht unterstützt.
* Der Aufruf eines Webdiensts wird nicht unterstützt.

For more information, see [adaptive forms rule editor](/help/forms/using/rule-editor.md).

## Use a variable {#use-a-variable}

Mithilfe von Variablen können Sie Eingaben und Ausgaben abrufen oder das Ergebnis eines Schritts speichern. Der Workflow-Editor bietet zwei Arten von Workflow-Schritten:

* Arbeitsablaufschritte mit Unterstützung für Variablen
* Arbeitsablaufschritte ohne Unterstützung für Variablen

### Arbeitsablaufschritte mit Unterstützung für Variablen {#workflow-steps-with-support-for-variables}

Der Schritt &quot;Gehe zu&quot;, &quot;ODER teilen&quot;, und alle AEM Forms-Workflow-Schritte unterstützen Variablen.

#### ODER Schritt teilen {#or-split-step}

Die ODER-Teilung erstellt eine Verzweigung im Workflow, nach nur einer der beiden Zweige aktiv bleibt. Mit diesem Schritt können Sie bedingte Prozesspfade in einem Workflow einrichten. Sie fügen jeder Verzweigung nach Bedarf Workflow-Schritte hinzu.

Sie können einen Routingausdruck für eine Verzweigung mithilfe einer Regeldefinition, eines ECMA-Skripts oder eines externen Skripts definieren.

Sie können Variablen verwenden, um den Routingausdruck mit dem Ausdruckseditor zu definieren. Weitere Informationen zur Verwendung von Routing-Ausdrücken für den Schritt &quot;OR-Teilung&quot;finden Sie unter Schritt [ODER-Teilung](/help/sites-developing/workflows-step-ref.md#or-split).

In diesem Beispiel verwenden Sie vor dem Definieren des Routing-Ausdrucks [Beispiel 2](/help/sites-developing/using-variables-in-aem-workflows.md#example2) , um den Wert für die **Variable totalvalue** festzulegen. Zweig 1 ist aktiv, wenn der Wert der Variablen **totalvalue** größer als 50000 ist. Gleichermaßen können Sie eine Regel definieren, mit der die Verzweigung 2 aktiviert wird, wenn der Wert der **Variablen totalvalue** unter 50000 liegt.

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_orsplit_example.mp4)

Wählen Sie entsprechend einen externen Skriptpfad oder geben Sie das ECMA-Skript für Routingausdrücke an, um die aktive Verzweigung auszuwerten. Tippen Sie auf Verzweigung **[!UICONTROL umbenennen]** , um einen alternativen Namen für die Verzweigung anzugeben.

Weitere Beispiele finden Sie unter Workflow-Modell [erstellen](/help/forms/using/aem-forms-workflow.md#create-a-workflow-model).

#### Gehe zu Schritt {#go-to-step}

The **Goto Step** allows you to specify the next step in the workflow model to execute, dependent on the result of a routing expression.

Ähnlich wie beim Schritt OR-Teilung können Sie einen Routingausdruck für Goto-Schritt mit einer Regeldefinition, einem ECMA-Skript oder einem externen Skript definieren.

Sie können Variablen verwenden, um den Routingausdruck mit dem Ausdruckseditor zu definieren. Weitere Informationen zur Verwendung von Routing-Ausdrücken für den Schritt Goto finden Sie unter [Goto Step](/help/sites-developing/workflows-step-ref.md#goto-step).

![Goto-Regel](assets/variables_goto_rule1_new.png)

In diesem Beispiel gibt der Schritt &quot;Gehe zu&quot;den Kreditkartenantrag als nächsten Schritt an, wenn der Wert für die Variable &quot; **Aktion** &quot;gleich **Benötigt weitere Informationen** ist.

Weitere Beispiele zur Verwendung der Regeldefinition im Schritt &quot;Weiter&quot;finden Sie unter [Simulieren einer For-Schleife](/help/sites-developing/workflows-step-ref.md#simulateforloop).

#### Arbeitsablaufschritte für Formulare {#forms-workflow-centric-workflow-steps}

Alle Arbeitsablaufschritte von AEM Forms unterstützen Variablen. For more information, see [Forms-centric workflow on OSGi](/help/forms/using/aem-forms-workflow-step-reference.md).

### Arbeitsablaufschritte ohne Unterstützung für Variablen {#workflow-steps-without-support-for-variables}

Sie können die [MetaDataMap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) -Schnittstelle verwenden, um auf Variablen in Workflow-Schritten zuzugreifen, die keine Variablen unterstützen.

#### Variablenwert abrufen {#retrieve-the-variable-value}

Verwenden Sie die folgenden APIs im ECMA-Skript, um Werte für vorhandene Variablen basierend auf dem Datentyp abzurufen:

| Variablendatentyp | API |
|---|---|
| Primitive (lang, Double, Boolean, Date und String) | workItem.getWorkflowData().getMetaDataMap().get(variableName, type) |
| XML | Packages.org.w3c.dom.Document xmlObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.org.w3c.dom.Document.class); |
| JSON | Packages.com.google.gson.JsonObject jsonObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.com.google.gson.JsonObject.class); |

Informationen zu APIs für zusätzliche komplexe Variablendaten, die in AEM Forms-Workflows verfügbar sind, finden Sie unter [Variablen in AEM Forms-Workflows](/help/forms/using/variable-in-aem-workflows.md).

**Beispiel**

Rufen Sie den Wert des Datentyps string mithilfe der folgenden API ab:

```
workItem.getWorkflowData().getMetaDataMap().get(accname, Packages.java.lang.String)
```

#### Variablenwert aktualisieren {#update-the-variable-value}

Verwenden Sie die folgende API im ECMA-Skript, um den Wert einer Variablen zu aktualisieren:

```
workItem.getWorkflowData().getMetaDataMap().put(variableName, value)
```

**Beispiel**

```
workItem.getWorkflowData().getMetaDataMap().put(salary, 50000)
```

aktualisiert den Wert der **Gehaltsvariablen** auf 50000.

### Variablen zum Aufrufen von Workflows festlegen {#apiinvokeworkflow}

Sie können eine API verwenden, um Variablen festzulegen und sie zum Aufrufen von Workflow-Instanzen zu übergeben.

[workflowSession.startWorkflow](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/WorkflowSession.html#startWorkflow-com.adobe.granite.workflow.model.WorkflowModel-com.adobe.granite.workflow.exec.WorkflowData-java.util.Map-) verwendet model, wfData und metaData als Argumente. Verwenden Sie MetaDataMap, um einen Wert für die Variable festzulegen.

In dieser API ist die Variable **variableName** auf **value **mit metaData.put(variableName, value) eingestellt.

```java
import com.adobe.granite.workflow.model.WorkflowModel;
import com.adobe.granite.workflow.metadata.MetaDataMap;
import com.adobe.aemfd.docmanager.Document;

/*Assume that you already have a workflowSession and modelId along with the payloadType and payload*/
WorkflowData wfData = workflowSession.newWorkflowData(payloadType, payload);
MetaDataMap metaData = wfData.getMetaDataMap();
metaData.put(variableName, value); //Create a variable "variableName" in your workflow model
WorkflowModel model = workflowSession.getModel(modelId);
workflowSession.startWorkflow(model, wfData, metaData);
```

## Bearbeiten einer Variablen {#edit-a-variable}

1. Tippen Sie auf der Seite &quot;Workflow bearbeiten&quot;auf das Symbol &quot;Variablen&quot;im Sidekick des Workflow-Modells. Im Abschnitt &quot;Variablen&quot;im linken Bereich werden alle vorhandenen Variablen angezeigt.
1. Tippen Sie auf das Symbol ![](https://helpx.adobe.com/content/dam/help/images/en/edit.png) (Bearbeiten) neben dem Variablennamen, den Sie bearbeiten möchten.
1. Bearbeiten Sie die Variableninformationen und tippen Sie auf , ![](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) um die Änderungen zu speichern. Sie können die Felder **[!UICONTROL &quot;Name]** &quot;und &quot; **[!UICONTROL Typ]** &quot;für eine Variable nicht bearbeiten.

## Löschen einer Variablen {#delete-a-variable}

Entfernen Sie vor dem Löschen der Variablen alle Verweise der Variablen aus dem Workflow. Stellen Sie sicher, dass die Variable nicht im Workflow verwendet wird.

Führen Sie die folgenden Schritte aus, um eine Variable zu löschen:

1. Tippen Sie auf der Seite &quot;Workflow bearbeiten&quot;auf das Symbol &quot;Variablen&quot;im Sidekick des Workflow-Modells. Im Abschnitt &quot;Variablen&quot;im linken Bereich werden alle vorhandenen Variablen angezeigt.
1. Tippen Sie auf das Symbol Löschen neben dem Variablennamen, den Sie löschen möchten.
1. Tippen Sie ![](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) auf , um die Variable zu bestätigen und zu löschen.

