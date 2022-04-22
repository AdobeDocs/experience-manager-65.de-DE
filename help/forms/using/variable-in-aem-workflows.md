---
title: Variablen in AEM Forms-Workflows
seo-title: Variables in AEM Forms Workflows
description: Erstellen Sie eine Variable, legen Sie einen Wert für die Variable fest und verwenden Sie sie in den AEM Forms-Workflow-Schritten.
seo-description: Create a variable, set a value for the variable, and use it in AEM Forms workflow steps.
uuid: 634a75c4-4899-478f-9e5d-a870f5efa583
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: cbf4e35a-7905-44ab-ab68-fb443443f02d
docset: aem65
exl-id: beb2b83e-e8db-40bb-915f-cb6ba3140947
source-git-commit: 3d0eb55eb35fcf5da1212b8be7c0aeee11307bb6
workflow-type: tm+mt
source-wordcount: '2208'
ht-degree: 81%

---

# Variablen in AEM Forms-Workflows{#variables-in-aem-forms-workflows}

Eine Variable in einem Workflow-Modell bietet die Möglichkeit, einen Wert basierend auf seinem Datentyp zu speichern. Anschließend können Sie den Namen der Variablen in einem beliebigen Workflow-Schritt verwenden, um den in der Variablen gespeicherten Wert abzurufen. Sie können auch Variablennamen verwenden, um Ausdrücke für Routing-Entscheidungen zu definieren.

In AEM Workflow-Modellen haben Sie folgende Möglichkeiten:

* [Erstellen Sie eine Variable](../../forms/using/variable-in-aem-workflows.md#create-a-variable) eines Datentyps basierend auf dem Typ von Information, die Sie darin speichern möchten.
* [Legen Sie einen Wert für die Variable fest](../../forms/using/variable-in-aem-workflows.md#set-a-variable), indem Sie den Workflow-Schritt „Variable festlegen“ verwenden.
* [Variable verwenden](../../forms/using/variable-in-aem-workflows.md#use-a-variable) in allen AEM Forms-Workflow-Schritten zum Abrufen des gespeicherten Werts sowie in ODER-Teilung und zum Definieren eines Routing-Ausdrucks.

Das folgende Video zeigt, wie Sie Variablen in AEM Workflow-Modellen erstellen, festlegen und verwenden können:

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_introduction_1_1.mp4)

Variablen sind eine Erweiterung der vorhandenen [MetaDataMap](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html)-Schnittstelle. Sie können [MetaDataMap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) in ECMAScript verwenden, um auf Metadaten zuzugreifen, die mithilfe von Variablen gespeichert wurden.

## Erstellen einer Variablen {#create-a-variable}

Variablen erstellen Sie mithilfe des Abschnitts „Variablen“ im Sidekick des Workflow-Modells. AEM Workflow-Variablen unterstützen die folgenden Datentypen:

* **Primitive Datentypen**: Long, Double, Boolesch, Datum und Zeichenfolge
* **Komplexe Datentypen**: [Dokument](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/aemfd/docmanager/Document.html)-, [XML](https://docs.oracle.com/javase/8/docs/api/org/w3c/dom/Document.html)-, [JSON](https://static.javadoc.io/com.google.code.gson/gson/2.3/com/google/gson/JsonObject.html)- und Formulardatenmodell-Instanz.

>[!NOTE]
>
>Workflows unterstützen für Datumsvariablen nur das ISO8601-Format.

Sie benötigen [AEM Forms Add-On-Paket](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) für die Datentypen &quot;Dokument&quot;und &quot;Formulardatenmodell&quot;.  Verwenden Sie den Datentyp „ArrayList“, um Variablenauflistungen zu erstellen. Sie können eine ArrayList-Variable für alle primitiven und komplexen Datentypen erstellen. Erstellen Sie beispielsweise eine ArrayList-Variable und wählen Sie String als Untertyp aus, um mehrere Zeichenfolgenwerte mit der -Variablen zu speichern.

Führen Sie die folgenden Schritte aus, um eine Variable zu erstellen:

1. Navigieren Sie in einer AEM-Instanz zu „Tools“ ![](/help/forms/using/assets/hammer.png) > „Workflows“ > „Modelle“.
1. Tippen Sie auf **[!UICONTROL Erstellen]** und geben Sie den Titel und einen optionalen Namen für das Workflow-Modell an. Wählen Sie das Modell aus und tippen Sie auf **[!UICONTROL Bearbeiten]**.
1. Tippen Sie auf das Variablensymbol im Sidekick des Workflow-Modells und tippen Sie dann auf **[!UICONTROL Variable hinzufügen]**.

   ![Variable hinzufügen](assets/variables_add_variable_new.png)

1. Geben Sie im Dialogfeld „Variable hinzufügen“ den Namen an und wählen Sie den Variablentyp aus.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Typ]** den Datentyp aus und geben Sie die folgenden Werte an:

   * Primitiver Datentyp: Geben Sie einen optionalen Standardwert für die Variable an.
   * JSON oder XML – Geben Sie einen optionalen JSON- oder XML-Schema-Pfad an. Das System überprüft den Schemapfad, während es die in diesem Schema verfügbaren Eigenschaften einer anderen Variablen zuordnet und speichert.
   * Formulardatenmodell – Geben Sie einen Pfad für ein Formulardatenmodell an.
   * ArrayList - Geben Sie einen Untertyp für die Sammlung an.

1. Geben Sie eine optionale Beschreibung für die Variable ein und tippen Sie auf ![done_icon](assets/done_icon.png), um die Änderungen zu speichern. Die Variable wird in der im linken Bereich verfügbaren Liste angezeigt.

Berücksichtigen Sie beim Erstellen von Variablen die folgenden Punkte:

* Erstellen Sie so viele Variablen, wie ein Workflow erfordert. Allerdings sollten Sie, um Datenbankressourcen zu sparen, die Anzahl der Variablen auf das erforderliche Minimum beschränken und Variablen nach Möglichkeit wiederverwenden.
* Bei Variablen wird zwischen Groß- und Kleinbuchstaben unterschieden. Stellen Sie sicher, dass Sie in Ihrem Workflow immer mit identischer Groß- und Kleinschreibung auf Variablen verweisen.
* Verwenden Sie im Namen der Variablen keine Sonderzeichen.

## Festlegen einer Variablen {#set-a-variable}

Mit dem Schritt „Variable festlegen“ können Sie den Wert einer Variablen festlegen und die Reihenfolge definieren, in der die Werte festgelegt werden. Die Variable wird in der Reihenfolge festgelegt, in der die Variablenzuordnungen im Schritt „Variable festlegen“ aufgeführt sind.

Änderungen an Variablenwerten betreffen nur die Instanz des Prozesses, in dem die Änderung erfolgt. Wenn beispielsweise ein Prozess initiiert wird und Variablendaten geändert werden, betreffen die Änderungen nur diese Instanz des Prozesses. Die Änderungen wirken sich nicht auf andere Instanzen des Workflows aus, die zuvor initiiert wurden oder später initiiert werden.

Je nach Datentyp der Variablen können Sie die folgenden Optionen verwenden, um den Wert einer Variablen festzulegen:

* **Literal:** Verwenden Sie die Option, wenn Sie den genauen Wert kennen, der angegeben werden soll.

* **Ausdruck:** Verwenden Sie die Option, wenn der zu verwendende Wert in einem Ausdruck berechnet wird. Der Ausdruck wird im bereitgestellten Ausdruckseditor erstellt.

* **JSON-Punktnotation:** Verwenden Sie die Option, um einen Wert aus einer Variablen vom Typ JSON oder FDM abzurufen.
* **XPATH:** Verwenden Sie die Option, um einen Wert aus einer Variablen vom Typ XML abzurufen.

* **Relativ zur Payload:** Verwenden Sie die Option, wenn der Wert, der in einer Variablen gespeichert werden soll, unter einem Pfad relativ zur Payload verfügbar ist.

* **Absoluter Pfad:** Verwenden Sie die Option, wenn der Wert, der in einer Variablen gespeichert werden soll, unter einem absoluten Pfad verfügbar ist.

Sie können bestimmte Elemente einer JSON- oder XML-Typvariablen auch mittels JSON-Punktnotation oder XPATH-Notation aktualisieren.

### Hinzufügen einer Zuordnung zwischen Variablen {#add-mapping-between-variables}

Führen Sie die folgenden Schritte aus, um die Zuordnung zwischen Variablen hinzuzufügen:

1. Tippen Sie auf der Seite für das Bearbeiten des Workflows auf das Symbol „Schritte“, das im Sidekick des Workflow-Modells verfügbar ist.
1. Ziehen Sie den Schritt **Variable festlegen** in den Workflow-Editor, tippen Sie auf den Schritt und wählen Sie ![configure_icon](assets/configure_icon.png) (Konfigurieren) aus.
1. Wählen Sie im Dialogfeld „Variable festlegen“ die Option **[!UICONTROL Zuordnung]** > **[!UICONTROL Zuordnung hinzufügen]** aus.
1. Wählen Sie im Abschnitt **Variable zuordnen** die Variable aus, in der Daten gespeichert werden sollen, wählen Sie den Zuordnungsmodus aus und geben Sie einen Wert an, der in der Variablen gespeichert werden soll. Die Zuordnungsmodi variieren je nach Variablentyp.
1. Ordnen Sie weitere Variablen zu, um einen aussagekräftigen Ausdruck zu erstellen. Tippen Sie auf ![done_icon](assets/done_icon.png), um die Änderungen zu speichern.

### Beispiel 1: Abfragen einer XML-Variablen, um den Wert für eine Zeichenfolgenvariable festzulegen {#example-query-an-xml-variable-to-set-value-for-a-string-variable}

Wählen Sie eine Variable vom Typ „XML“ aus, um eine XML-Datei zu speichern. Fragen Sie die XML-Variable ab, um den Wert für eine Zeichenfolgenvariable für die in der XML-Datei verfügbare Eigenschaft festzulegen. Verwenden Sie das Feld **XPATH für die XML-Variable angeben**, um die Eigenschaft zu definieren, die in der Zeichenfolgenvariablen gespeichert werden soll.

In diesem Beispiel wählen Sie eine XML-Variable **formdata** aus, um die Datei **cc-app.xml** zu speichern. Fragen Sie die Variable **formdata** ab, um den Wert für die Zeichenfolgenvariable **emailaddress** festzulegen, um den Wert für die Eigenschaft **emailAddress** zu speichern, die in der Datei **cc-app.xml** verfügbar ist.

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/set_variable_example1.mp4 "Festlegen des Wertes einer Variablen")

### Beispiel 2: Verwenden eines Ausdrucks, um einen Wert basierend auf anderen Variablen zu speichern {#example2}

Verwenden Sie einen Ausdruck, um die Summe der Variablen zu berechnen und das Ergebnis in einer Variablen zu speichern.

In diesem Beispiel verwenden Sie den Ausdruckseditor, um einen Ausdruck zu definieren, mit dem die Summe der Variablen **assetscost** und **balanceamount** zu berechnet und das Ergebnis in der Variablen **totalvalue** gespeichert wird.

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_expression.mp4)

## Verwenden des Ausdruckseditors {#use-expression-editor}

Sie können Ausdrücke auch dazu verwenden, den Wert einer Variablen zur Laufzeit zu berechnen. Variablen verfügen über einen Ausdruckseditor für das Definieren von Ausdrücken.

Den Ausdruckseditor verwenden Sie, um:

* den Wert von Variablen mithilfe anderer Workflow-Variablen, Zahlen oder mathematischer Ausdrücke festzulegen.
* Workflow-Variablen, Zeichenfolgen, Zahlen oder einen Ausdruck in einem mathematischen Ausdruck zu verwenden.
* Bedingungen zum Festlegen von Variablenwerten hinzuzufügen.
* Operatoren zwischen Bedingungen hinzuzufügen.

![Ausdruckseditor](assets/variables_expression_editor_new.png)

Sie basiert auf dem Regeleditor für adaptive Formulare mit folgenden Änderungen. Regeleditor in Variablen:

* Unterstützt Funktionen nicht.
* Stellt keine Benutzeroberfläche zum Anzeigen einer Regelzusammenfassung bereit.
* Verfügt über keinen Code-Editor.
* Unterstützt nicht das Aktivieren und Deaktivieren des Wertes eines Objekts.
* Unterstützt nicht das Festlegen einer Eigenschaft eines Objekts.
* Unterstützt nicht das Aufrufen eines Webservice.

Weitere Informationen finden Sie unter [Regeleditor für adaptive Formulare](../../forms/using/rule-editor.md).

## Verwenden einer Variablen {#use-a-variable}

Sie können Variablen verwenden, um Eingaben und Ausgaben abzurufen oder um das Ergebnis eines Schritts zu speichern. Der Workflow-Editor bietet zwei Arten von Workflow-Schritten:

* Workflow-Schritte mit Unterstützung für Variablen
* Workflow-Schritte ohne Unterstützung für Variablen

### Workflow-Schritte mit Unterstützung für Variablen {#workflow-steps-with-support-for-variables}

Der Schritt Gehe zu oder Aufspaltung und alle AEM Forms-Workflow-Schritte unterstützen Variablen.

#### ODER-Teilungs-Schritt {#or-split-step}

Die ODER-Teilung erstellt eine Verzweigung im Workflow, nach der nur einer der beiden Zweige aktiv bleibt. Mit diesem Schritt können Sie bedingte Verarbeitungspfade in einem Workflow einrichten. Sie fügen jeder Verzweigung nach Bedarf Workflow-Schritte hinzu.

Sie können Routing-Ausdrücke für eine Verzweigung mithilfe einer Regeldefinition, eines ECMA-Skripts oder eines externen Skripts definieren.

Sie können Variablen verwenden, um den Routing-Ausdruck mit dem Ausdruckseditor zu definieren. Weitere Informationen zur Verwendung von Routing-Ausdrücken für den Schritt „ODER-Teilung“ finden Sie unter [ODER-Teilungs-Schritt](/help/sites-developing/workflows-step-ref.md#or-split).

In diesem Beispiel verwenden Sie vor dem Definieren des Routing-Ausdrucks das [Beispiel 2](../../forms/using/variable-in-aem-workflows.md#example2), um den Wert für die Variable **totalvalue** festzulegen. Zweig 1 ist aktiv, wenn der Wert der Variablen **totalvalue** größer als 50000 ist. Auf ähnliche Weise können Sie eine Regel definieren, die den Zweig 2 aktivieren soll, wenn der Wert der Variablen **totalvalue** kleiner als 50000 ist.

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_orsplit_example.mp4)

Wählen Sie auf ähnliche Weise einen externen Skriptpfad aus oder geben Sie das ECMA-Skript an, damit Routing-Ausdrücke die aktive Verzweigung auswerten können. Tippen Sie auf **[!UICONTROL Verzweigung umbenennen]**, um einen alternativen Namen für die Verzweigung anzugeben.

Weitere Beispiele finden Sie unter [Erstellen eines Workflow-Modells](../../forms/using/aem-forms-workflow.md#create-a-workflow-model).

#### Go-To-Schritt {#go-to-step}

Mit **GOTO** (Wechseln zu Schritt) können Sie den nächsten Schritt im Workflow-Modell angeben, der je nach dem Ergebnis eines Routing-Ausdrucks ausgeführt werden soll.

Ähnlich wie beim ODER-Teilungs-Schritt können Sie Routing-Ausdrücke für einen GOTO-Schritt (Wechseln zu Schritt) mithilfe einer Regeldefinition, eines ECMA-Skripts oder eines externen Skripts definieren.

Sie können Variablen verwenden, um den Routing-Ausdruck mit dem Ausdruckseditor zu definieren. Weitere Informationen zur Verwendung von Routing-Ausdrücken für den GOTO-Schritt finden Sie unter [GOTO-Schritt (Wechseln zu Schritt)](/help/sites-developing/workflows-step-ref.md#goto-step).

![GOTO-Regel](assets/variables_goto_rule1_new.png)

In diesem Beispiel gibt der GOTO-Schritt (Wechseln zu Schritt) als nächsten Schritt den Schritt „Kreditkartenantrag prüfen“ an, wenn der Wert für die Variable **actiontaken** gleich **Need more info** (Weitere Informationen erforderlich) ist.

Weitere Beispiele zur Verwendung der Regeldefinition im GOTO-Schritt (Wechseln zu Schritt) finden Sie unter [Simulieren einer For-Schleife](/help/sites-developing/workflows-step-ref.md#simulateforloop).

#### Workflow-Schritte mit Forms {#forms-workflow-centric-workflow-steps}

Alle AEM Forms-Workflow-Schritte unterstützen Variablen. Weitere Informationen finden Sie unter [Formularzentrierte Workflows in OSGi](../../forms/using/aem-forms-workflow-step-reference.md).

### Workflow-Schritte ohne Unterstützung für Variablen {#workflow-steps-without-support-for-variables}

Sie können die Schnittstelle [MetaDataMap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) verwenden, um auf Variablen in Workflow-Schritten zuzugreifen, die keine Variablen unterstützen.

#### Abrufen des Variablenwerts {#retrieve-the-variable-value}

Verwenden Sie die folgenden APIs im ECMA-Skript, um Werte für vorhandene Variablen basierend auf dem Datentyp abzurufen:

| Datentyp der Variablen | API |
|---|---|
| Primitive (Long, Double, Boolesch, Datum und Zeichenfolge) | workItem.getWorkflowData().getMetaDataMap().get(variableName, type) |
| Dokument | Packages.com.adobe.aemfd.docmanager.Document doc = workItem.getWorkflowData().getMetaDataMap().get(&quot;docVar&quot;, Packages.com.adobe.aemfd.docmanager.Document.class); |
| XML | Packages.org.w3c.dom.Document xmlObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.org.w3c.dom.Document.class); |
| Formulardatenmodell | Packages.com.adobe.aem.dermis.api.FormDataModelInstance fdmObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.com.adobe.aem.dermis.api.FormDataModelInstance.class); |
| JSON | Packages.com.google.gson.JsonObject jsonObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.com.google.gson.JsonObject.class); |

Sie benötigen [AEM Forms Add-On-Paket](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) für die Variablentypen &quot;Dokument&quot;und &quot;Formulardatenmodell&quot;.

**Beispiel**

Rufen Sie den Wert vom Datentyp „String“ (Zeichenfolge) über die folgende API ab:

```javascript
workItem.getWorkflowData().getMetaDataMap().get(accname, Packages.java.lang.String)
```

#### Aktualisieren des Variablenwertes {#update-the-variable-value}

Verwenden Sie die folgende API im ECMA-Skript, um den Wert einer Variablen zu aktualisieren:

```javascript
workItem.getWorkflowData().getMetaDataMap().put(variableName, value)
```

**Beispiel**

```javascript
workItem.getWorkflowData().getMetaDataMap().put(salary, 50000)
```

aktualisiert den Wert für **Gehalt** auf 50000.

### Festlegen von Variablen zum Aufrufen von Workflows {#apiinvokeworkflow}

Sie können eine API verwenden, um Variablen festzulegen und sie dann zu übergeben, um Workflow-Instanzen aufzurufen.

[workflowSession.startWorkflow](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/WorkflowSession.html#startWorkflow-com.adobe.granite.workflow.model.WorkflowModel-com.adobe.granite.workflow.exec.WorkflowData-java.util.Map-) verwendet „model“, „wfData“ und „metaData“ als Argumente. Verwenden Sie MetaDataMap, um einen Wert für die Variable festzulegen.

In dieser API wird die Variable **variableName** mithilfe von metaData.put(variableName, value) auf **value** festgelegt.

```javascript
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

**Beispiel**

Initialisieren Sie das Dokumentobjekt **doc** auf einen Pfad („a/b/c“) und legen Sie den Wert der Variablen **docVar** auf den Pfad fest, der in dem Dokumentobjekt gespeichert ist.

```javascript
import com.adobe.granite.workflow.WorkflowSession;
import com.adobe.granite.workflow.exec.WorkflowData;
import com.adobe.granite.workflow.model.WorkflowModel;
import com.adobe.granite.workflow.metadata.MetaDataMap;
import com.adobe.aemfd.docmanager.Document;

/*This example assumes that you already have a workflowSession and modelId along with the payloadType and payload */
WorkflowData wfData = workflowSession.newWorkflowData(payloadType, payload);
MetaDataMap metaData = wfData.getMetaDataMap();
Document doc = new Document("/a/b/c");// initialize a document object
metaData.put("docVar",doc); //Assuming that you have created a variable "docVar" of type Document in your workflow model
WorkflowModel model = workflowSession.getModel(modelId);
workflowSession.startWorkflow(model, wfData, metaData);
```

### Speichern vertraulicher Benutzerdaten außerhalb von JCR mithilfe von Workflow-Variablen {#jcr-independent-persistance}

Daten, die mit dem Arbeitsablauf für Formulare verarbeitet werden, können vertrauliche Benutzerdaten wie personenbezogene Daten und vertrauliche personenbezogene Daten enthalten. Unternehmen können die Daten, die von verschiedenen Workflow-Schritten verarbeitet (und mithilfe von Workflow-Variablen weitergegeben werden), aus dem JCR-Speicher in einen externen Datenspeicher speichern, der ihnen gehört und von ihnen verwaltet wird. Weitere Informationen zum Beibehalten von Workflow-Daten in einem externen Speicher finden Sie unter [Verwenden von Workflow-Variablen für kundeneigene Datenspeicher](/help/sites-administering/workflows-administering.md#using-workflow-variables-customer-datastore).
[!DNL Adobe Experience Manager] bietet Workflow-API [UserMetaDataPersistenceProvider](https://github.com/adobe/workflow-variable-externalizer) , um Workflow-Variablen in externen Azure-Blob-Speichern zu speichern. Weitere Informationen zur Verwendung der API finden Sie unter [Verwenden Sie Workflow-Variablen, um sensible Daten zu parametrisieren und in externen Datenspeichern zu speichern.](/help/forms/using/aem-forms-workflow.md#externalize-wf-variables).

## Bearbeiten einer Variablen {#edit-a-variable}

1. Tippen Sie auf der Seite „Workflow bearbeiten“ auf das Symbol „Variablen“ im Sidekick des Workflow-Modells. Im Abschnitt „Variablen“ im linken Bereich werden alle vorhandenen Variablen angezeigt.
1. Tippen Sie auf das Symbol ![edit](assets/edit.png) (Bearbeiten) neben dem Namen der Variablen, die Sie bearbeiten möchten.
1. Bearbeiten Sie die Variableninformationen und tippen Sie auf ![done_icon](assets/done_icon.png), um die Änderungen zu speichern. Die Felder **[!UICONTROL Name]** und **[!UICONTROL Typ]** für eine Variable können Sie nicht bearbeiten.

## Löschen einer Variablen {#delete-a-variable}

Bevor Sie eine Variable löschen, müssen Sie alle Verweise der Variablen aus dem Workflow entfernen. Stellen Sie sicher, dass die Variable im Workflow nicht verwendet wird.

Führen Sie die folgenden Schritte aus, um eine Variable zu löschen:

1. Tippen Sie auf der Seite „Workflow bearbeiten“ auf das Symbol „Variablen“ im Sidekick des Workflow-Modells. Im Abschnitt „Variablen“ im linken Bereich werden alle vorhandenen Variablen angezeigt.
1. Tippen Sie auf das Symbol „Löschen“ neben dem Namen der Variablen, die Sie löschen möchten.
1. Tippen Sie auf ![done_icon](assets/done_icon.png), um zu bestätigen, dass die Variable gelöscht werden soll.

## Verweise {#references}

Weitere Beispiele zur Verwendung von Variablen in AEM Forms-Workflow-Schritten finden Sie unter [Variablen in AEM Workflows](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/variables-aem-workflow/introduction.html?lang=de).
