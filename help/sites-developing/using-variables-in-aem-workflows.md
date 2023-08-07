---
title: Variablen in AEM-Workflows
description: Erstellen Sie eine Variable, legen Sie einen Wert für die Variable fest und verwenden Sie sie in den Workflow-Schritten „ODER-Aufspaltung“ und „Goto“ von AEM.
uuid: cc62ff11-51d4-4db4-9c6d-5dc2caa1da52
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: bbb9936e-ecd2-44b3-b4ae-dd62a3160641
docset: aem65
exl-id: c8aeceec-860c-49ee-b681-d7107e52020d
source-git-commit: 4fd5e9a1bc603202ee52e85a1c09125b13cec315
workflow-type: tm+mt
source-wordcount: '2096'
ht-degree: 100%

---

# Variablen in AEM-Workflows{#variables-in-aem-workflows}

Eine Variable in einem Workflow-Modell bietet die Möglichkeit, einen Wert basierend auf seinem Datentyp zu speichern. Sie können den Namen der Variablen in jedem Workflow-Schritt verwenden, um den in der Variablen gespeicherten Wert abzurufen. Sie können auch Variablennamen verwenden, um Ausdrücke für Routing-Entscheidungen zu definieren.

In AEM-Workflow-Modellen haben Sie folgende Möglichkeiten:

* [Erstellen Sie eine Variable](/help/sites-developing/using-variables-in-aem-workflows.md#create-a-variable) eines Datentyps basierend auf dem Typ von Information, die Sie darin speichern möchten.
* [Legen Sie einen Wert für die Variable fest](/help/sites-developing/using-variables-in-aem-workflows.md#set-a-variable), indem Sie den Workflow-Schritt „Variable festlegen“ verwenden.
* [Verwenden Sie die Variable](/help/sites-developing/using-variables-in-aem-workflows.md#use-a-variable) in den Workflow-Schritten „ODER-Aufspaltung“ und „Goto“ von AEM zum Definieren eines Ausdrucks für Routing-Entscheidungen. In allen AEM Forms-Workflow-Schritten können Sie auch Variablen verwenden.

Das folgende Video zeigt, wie Sie Variablen in AEM-Workflow-Modellen erstellen, festlegen und verwenden können:

<!-- FUTURE ERROR: YouTube and mp4 videos are not supported -->

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/usevariables_example.mp4)

Variablen sind eine Erweiterung der [MetaDataMap](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html)-Schnittstelle. Sie können [MetaDataMap](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) in ECMAScript verwenden, um auf Metadaten zuzugreifen, die mithilfe von Variablen gespeichert wurden.

## Erstellen einer Variablen {#create-a-variable}

Variablen erstellen Sie mithilfe des Abschnitts „Variablen“ im Sidekick des Workflow-Modells. AEM-Workflow-Variablen unterstützen die folgenden Datentypen:

* **Primitive Datentypen**: Long, Double, Boolesch, Datum und Zeichenfolge
* **Komplexe Datentypen**: [XML](https://docs.oracle.com/javase/8/docs/api/org/w3c/dom/Document.html) und [JSON](https://www.javadoc.io/doc/com.google.code.gson/gson/2.3/com/google/gson/JsonObject.html)

>[!NOTE]
>
>Workflows unterstützen für Datumsvariablen nur das ISO8601-Format.

Weitere komplexe Datentypen, die in AEM Forms-Workflows verfügbar sind, finden Sie unter [Variablen in AEM Forms-Workflows](/help/forms/using/variable-in-aem-workflows.md). Verwenden Sie den Datentyp „ArrayList“, um Variablenauflistungen zu erstellen. Sie können eine ArrayList-Variable für alle primitiven und komplexen Datentypen erstellen. Beispiel: Erstellen Sie eine ArrayList-Variable und wählen Sie als Untertyp „String“ aus, um mehrere Zeichenfolgenwerte in der Variablen zu speichern.

Um eine Variable zu erstellen:

1. Navigieren Sie in einer AEM-Instanz zu „Tools“ > „Workflows“ > „Modelle“.
1. Tippen Sie auf **[!UICONTROL Erstellen]** und geben Sie den Titel und einen optionalen Namen für das Workflow-Modell an. Wählen Sie das Modell aus und tippen Sie auf **[!UICONTROL Bearbeiten]**.
1. Tippen Sie auf das Variablensymbol im Sidekick des Workflow-Modells und tippen Sie dann auf **[!UICONTROL Variable hinzufügen]**.

   ![Variable hinzufügen](assets/variables_add_variable_new.png)

1. Geben Sie im Dialogfeld „Variable hinzufügen“ den Namen an und wählen Sie den Typ der Variable aus.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Typ]** den Datentyp aus und geben Sie die folgenden Werte an:

   * Primitiver Datentyp: Geben Sie einen optionalen Standardwert für die Variable an.
   * JSON oder XML – Geben Sie einen optionalen JSON- oder XML-Schema-Pfad an. Das System überprüft den Schemapfad, während es die in diesem Schema verfügbaren Eigenschaften einer anderen Variablen zuordnet und speichert.
   * Formulardatenmodell – Geben Sie einen Pfad für ein Formulardatenmodell an.
   * ArrayList – Geben Sie einen Untertyp für die Auflistung an.

1. Geben Sie eine optionale Beschreibung für die Variable an und tippen Sie auf das ![Symbol „Speichern“, dargestellt durch einen Haken in einem Kästchen.](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png), um die Änderungen zu speichern. Die Variable wird in der im linken Bereich verfügbaren Liste angezeigt.

Berücksichtigen Sie beim Erstellen von Variablen die folgenden Punkte:

* Erstellen Sie so viele Variablen, wie ein Workflow erfordert. Allerdings sollten Sie, um Datenbankressourcen zu sparen, die Anzahl der Variablen auf das erforderliche Minimum beschränken und Variablen nach Möglichkeit wiederverwenden.
* Bei Variablen wird zwischen Groß- und Kleinbuchstaben unterschieden. Stellen Sie sicher, dass Sie in Ihrem Workflow immer mit identischer Groß- und Kleinschreibung auf Variablen verweisen.
* Verwenden Sie im Namen der Variablen keine Sonderzeichen.

## Festlegen einer Variablen {#set-a-variable}

Mit dem Schritt „Variable festlegen“ können Sie den Wert einer Variablen festlegen und die Reihenfolge definieren, in der die Werte festgelegt werden. Die Variable wird in der Reihenfolge festgelegt, in der die Variablenzuordnungen im Schritt „Variable festlegen“ aufgeführt sind.

Änderungen an Variablenwerten betreffen nur die Instanz des Prozesses, in dem die Änderung erfolgt. Wenn beispielsweise ein Prozess initiiert wird und Variablendaten geändert werden, betreffen die Änderungen nur diese Instanz des Prozesses. Die Änderungen wirken sich nicht auf andere Instanzen des Prozesses aus, die davor oder danach initiiert werden.

Je nach Datentyp der Variablen können Sie die folgenden Optionen verwenden, um den Wert einer Variablen festzulegen:

* **Literal:** Verwenden Sie die Option, wenn Sie den genauen Wert kennen, der angegeben werden soll.
* **Ausdruck:** Verwenden Sie die Option, wenn der zu verwendende Wert in einem Ausdruck berechnet wird. Der Ausdruck wird im bereitgestellten Ausdruckseditor erstellt.
* **JSON-Punktnotation:** Verwenden Sie die Option, um einen Wert aus einer Variablen vom Typ JSON oder FDM abzurufen.
* **XPATH:** Verwenden Sie die Option, um einen Wert aus einer Variablen vom Typ XML abzurufen.
* **Relativ zur Payload:** Verwenden Sie die Option, wenn der Wert, der in einer Variablen gespeichert werden soll, unter einem Pfad relativ zur Payload verfügbar ist.
* **Absoluter Pfad:** Verwenden Sie die Option, wenn der Wert, der in einer Variablen gespeichert werden soll, unter einem absoluten Pfad verfügbar ist.

Sie können bestimmte Elemente einer JSON- oder XML-Typvariablen auch mittels JSON-Punktnotation oder XPATH-Notation aktualisieren.

### Hinzufügen einer Zuordnung zwischen Variablen {#add-mapping-between-variables}

Gehen Sie wie folgt vor, um eine Zuordnung zwischen Variablen hinzuzufügen:

1. Tippen Sie auf der Seite für das Bearbeiten des Workflows auf das Symbol „Schritte“, das im Sidekick des Workflow-Modells verfügbar ist.
1. Ziehen Sie den Schritt **Variable festlegen** per Drag-and-Drop in den Workflow-Editor, tippen Sie darauf und wählen Sie das ![Symbol „Konfigurieren“ aus, das durch einen Schraubenschlüssel dargestellt wird.](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/configure_icon.png) (Konfigurieren).
1. Wählen Sie im Dialogfeld „Variable festlegen“ die Option **[!UICONTROL Zuordnung]** > **[!UICONTROL Zuordnung hinzufügen]** aus.
1. Wählen Sie im Abschnitt **Variable zuordnen** die Variable aus, in der Daten gespeichert werden sollen, wählen Sie den Zuordnungsmodus aus und geben Sie einen Wert an, der in der Variablen gespeichert werden soll. Die Zuordnungsmodi variieren je nach Variablentyp.
1. Ordnen Sie weitere Variablen zu, damit Sie einen aussagekräftigen Ausdruck bilden können. Tippen Sie auf das ![Symbol „Speichern“, dargestellt durch einen Haken in einem Kästchen.](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png), um die Änderungen zu speichern.

### Beispiel 1: Abfragen einer XML-Variablen, um den Wert für eine Zeichenfolgenvariable festzulegen {#example-query-an-xml-variable-to-set-value-for-a-string-variable}

Wählen Sie eine Variable vom Typ XML aus, in der Sie eine XML-Datei speichern möchten. Fragen Sie die XML-Variable ab, um den Wert für eine Zeichenfolgenvariable für die in der XML-Datei verfügbare Eigenschaft festzulegen. Verwenden Sie das Feld **XPATH für die XML-Variable angeben**, um die Eigenschaft zu definieren, die in der Zeichenfolgenvariablen gespeichert werden soll.

In diesem Beispiel wählen Sie eine XML-Variable **formdata** aus, um die Datei **cc-app.xml** zu speichern. Fragen Sie die Variable **formdata** ab, damit Sie den Wert für die String-Variable **emailaddress** setzen können, um den Wert für die Eigenschaft **emailAddress** zu speichern, die in der Datei **cc-app.xml** verfügbar ist.

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/set_variable_example1.mp4 "Festlegen des Wertes einer Variablen")

### Beispiel 2: Verwenden eines Ausdrucks, um einen Wert basierend auf anderen Variablen zu speichern {#example2}

Verwenden Sie einen Ausdruck, um die Summe der Variablen zu berechnen und das Ergebnis in einer Variablen zu speichern.

In diesem Beispiel verwenden Sie den Ausdruckseditor, um einen Ausdruck zu definieren, mit dem die Summe der Variablen **assetscost** und **balanceamount** zu berechnet und das Ergebnis in der Variablen **totalvalue** gespeichert wird.

<!-- FUTURE ERROR: YouTube and mp4 videos are not supported -->

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_expression.mp4)

## Verwenden des Ausdruckseditors {#use-expression-editor}

Sie können Ausdrücke auch dazu verwenden, den Wert einer Variablen zur Laufzeit zu berechnen. Variablen verfügen über einen Ausdruckseditor für das Definieren von Ausdrücken.

Den Ausdruckseditor verwenden Sie, um:

* den Wert von Variablen mithilfe anderer Workflow-Variablen, Zahlen oder mathematischer Ausdrücke festzulegen.
* Workflow-Variablen, Zeichenfolgen, Zahlen oder einen Ausdruck in einem mathematischen Ausdruck zu verwenden.
* Fügen Sie Bedingungen hinzu, damit Sie Werte von Variablen festlegen können.
* Operatoren zwischen Bedingungen hinzuzufügen.

![Ausdruckseditor](assets/variables_expression_editor_new.png)

Sie basiert auf dem Regeleditor für adaptive Formulare, mit den folgenden Änderungen. Regeleditor in Variablen:

* Unterstützt Funktionen nicht.
* Stellt keine Benutzeroberfläche zum Anzeigen einer Regelzusammenfassung bereit.
* Verfügt über keinen Code-Editor.
* Unterstützt nicht das Aktivieren und Deaktivieren des Wertes eines Objekts.
* Unterstützt nicht das Festlegen einer Eigenschaft eines Objekts.
* Unterstützt nicht das Aufrufen eines Webservice.

Weitere Informationen finden Sie unter [Regeleditor für adaptive Formulare](/help/forms/using/rule-editor.md).

## Verwenden einer Variablen {#use-a-variable}

Sie können Variablen verwenden, um Eingaben und Ausgaben abzurufen oder um das Ergebnis eines Schritts zu speichern. Der Workflow-Editor bietet zwei Arten von Workflow-Schritten:

* Workflow-Schritte mit Unterstützung für Variablen
* Workflow-Schritte ohne Unterstützung für Variablen

### Workflow-Schritte mit Unterstützung für Variablen {#workflow-steps-with-support-for-variables}

Die Schritte „Goto“ und „ODER-Teilung“ sowie alle AEM Forms Workflow-Schritte unterstützen Variablen.

#### ODER-Teilungs-Schritt {#or-split-step}

Die ODER-Teilung erstellt eine Verzweigung im Workflow, nach der nur einer der beiden Zweige aktiv bleibt. Mit diesem Schritt können Sie bedingte Verarbeitungspfade in einem Workflow einrichten. Sie fügen jeder Verzweigung nach Bedarf Workflow-Schritte hinzu.

Sie können Routing-Ausdrücke für eine Verzweigung mithilfe einer Regeldefinition, eines ECMA-Skripts oder eines externen Skripts definieren.

Sie können Variablen verwenden, um den Routing-Ausdruck mit dem Ausdruckseditor zu definieren. Weitere Informationen zur Verwendung von Routing-Ausdrücken für den Schritt „ODER-Teilung“ finden Sie unter [ODER-Teilungs-Schritt](/help/sites-developing/workflows-step-ref.md#or-split).

In diesem Beispiel verwenden Sie vor dem Definieren des Routing-Ausdrucks das [Beispiel 2](/help/sites-developing/using-variables-in-aem-workflows.md#example2), um den Wert für die Variable **totalvalue** festzulegen. Zweig 1 ist aktiv, wenn der Wert der Variablen **totalvalue** größer als 50000 ist. Auf ähnliche Weise können Sie eine Regel definieren, die den Zweig 2 aktivieren soll, wenn der Wert der Variablen **totalvalue** kleiner als 50000 ist.

<!-- FUTURE ERROR: YouTube and mp4 videos are not supported -->

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_orsplit_example.mp4)

Wählen Sie auf ähnliche Weise einen externen Skriptpfad aus oder geben Sie das ECMA-Skript an, damit Routing-Ausdrücke die aktive Verzweigung auswerten können. Tippen Sie auf **[!UICONTROL Verzweigung umbenennen]**, um einen alternativen Namen für die Verzweigung anzugeben.

Weitere Beispiele finden Sie unter [Erstellen eines Workflow-Modells](/help/forms/using/aem-forms-workflow.md#create-a-workflow-model).

#### GOTO-Schritt (Wechseln zu Schritt)  {#go-to-step}

Mit der Option **Goto-Schritt** können Sie den nächsten auszuführenden Schritt im Workflow-Modell angeben, abhängig vom Ergebnis eines Routing-Ausdrucks.

Ähnlich wie beim ODER-Teilungs-Schritt können Sie Routing-Ausdrücke für einen GOTO-Schritt (Wechseln zu Schritt) mithilfe einer Regeldefinition, eines ECMA-Skripts oder eines externen Skripts definieren.

Sie können Variablen verwenden, um den Routing-Ausdruck mit dem Ausdruckseditor zu definieren. Weitere Informationen zur Verwendung von Routing-Ausdrücken für den GOTO-Schritt finden Sie unter [GOTO-Schritt (Wechseln zu Schritt)](/help/sites-developing/workflows-step-ref.md#goto-step).

![GOTO-Regel](assets/variables_goto_rule1_new.png)

In diesem Beispiel gibt der GOTO-Schritt (Wechseln zu Schritt) als nächsten Schritt den Schritt „Kreditkartenantrag prüfen“ an, wenn der Wert für die Variable **actiontaken** gleich **Need more info** (Weitere Informationen erforderlich) ist.

Weitere Beispiele zur Verwendung der Regeldefinition im GOTO-Schritt (Wechseln zu Schritt) finden Sie unter [Simulieren einer For-Schleife](/help/sites-developing/workflows-step-ref.md#simulateforloop).

#### Forms-Workflow-zentrierte Arbeitsschritte {#forms-workflow-centric-workflow-steps}

Alle AEM Forms-Workflow-Schritte unterstützen Variablen. Weitere Informationen finden Sie unter [Formularzentrierte Workflows in OSGi](/help/forms/using/aem-forms-workflow-step-reference.md).

### Workflow-Schritte ohne Unterstützung für Variablen {#workflow-steps-without-support-for-variables}

Sie können die Schnittstelle [MetaDataMap](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) verwenden, um auf Variablen in Workflow-Schritten zuzugreifen, die keine Variablen unterstützen.

#### Abrufen des Variablenwerts {#retrieve-the-variable-value}

Um Werte für vorhandene Variablen basierend auf dem Datentyp abzurufen, verwenden Sie die folgenden APIs im ECMA-Skript.

| Datentyp der Variablen | API |
|---|---|
| Primitive (Long, Double, Boolesch, Datum und Zeichenfolge) | workItem.getWorkflowData().getMetaDataMap().get(variableName, type) |
| XML | Packages.org.w3c.dom.Document xmlObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.org.w3c.dom.Document.class); |
| JSON | Packages.com.google.gson.JsonObject jsonObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.com.google.gson.JsonObject.class); |

Informationen zu APIs für zusätzliche komplexe Variablendatentypen, die in AEM Forms-Workflows verfügbar sind, finden Sie unter [Variablen in AEM Forms-Workflows](/help/forms/using/variable-in-aem-workflows.md).

**Beispiel**

Rufen Sie den Wert vom Datentyp „String“ (Zeichenfolge) über die folgende API ab:

```
workItem.getWorkflowData().getMetaDataMap().get(accname, Packages.java.lang.String)
```

#### Aktualisieren des Variablenwertes {#update-the-variable-value}

Um den Wert einer Variablen zu aktualisieren, verwenden Sie die folgende API im ECMA-Skript.

```
workItem.getWorkflowData().getMetaDataMap().put(variableName, value)
```

**Beispiel**

```
workItem.getWorkflowData().getMetaDataMap().put(salary, 50000)
```

Aktualisiert den Wert der Variablen **salary** (Gehalt) auf 50000.

### Festlegen von Variablen zum Aufrufen von Workflows {#apiinvokeworkflow}

Sie können eine API verwenden, um Variablen festzulegen und sie dann zu übergeben, um Workflow-Instanzen aufzurufen.

[workflowSession.startWorkflow](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/workflow/WorkflowSession.html?lang=de#startWorkflow-com.adobe.granite.workflow.model.WorkflowModel-com.adobe.granite.workflow.exec.WorkflowData-java.util.Map-) verwendet „model“, „wfData“ und „metaData“ als Argumente. Verwenden Sie MetaDataMap, um einen Wert für die Variable festzulegen.

In dieser API wird die Variable **variableName** mithilfe von metaData.put(variableName, value) auf **value** festgelegt.

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

1. Tippen Sie auf der Seite „Workflow bearbeiten“ auf das Symbol „Variablen“ im Sidekick des Workflow-Modells. Im Abschnitt „Variablen“ im linken Bereich werden alle vorhandenen Variablen angezeigt.
1. Tippen Sie auf das ![Bearbeitungssymbol, dargestellt durch ein Bleistiftsymbol.Symbol ](https://helpx.adobe.com/content/dam/help/images/en/edit.png) (Bearbeiten) neben dem Namen der Variablen, die Sie bearbeiten möchten.
1. Bearbeiten Sie die Variableninformationen und tippen Sie auf das Symbol ![„Speichern“, das durch ein Häkchen dargestellt wird.](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png), um die Änderungen zu speichern. Die Felder **[!UICONTROL Name]** und **[!UICONTROL Typ]** für eine Variable können Sie nicht bearbeiten.

## Löschen einer Variablen {#delete-a-variable}

Bevor Sie eine Variable löschen, müssen Sie alle Verweise der Variablen aus dem Workflow entfernen. Stellen Sie sicher, dass die Variable im Workflow nicht verwendet wird.

So löschen Sie eine Variable,

1. Tippen Sie auf der Seite „Workflow bearbeiten“ auf das Symbol „Variablen“ im Sidekick des Workflow-Modells. Im Abschnitt „Variablen“ im linken Bereich werden alle vorhandenen Variablen angezeigt.
1. Tippen Sie auf das Symbol „Löschen“ neben dem Namen der Variablen, die Sie löschen möchten.
1. Tippen Sie auf das Symbol ![„Fertig“, dargestellt durch ein Häkchen.](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png), um zu bestätigen, dass die Variable gelöscht werden soll.
