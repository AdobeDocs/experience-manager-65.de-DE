---
title: Regeleditor für adaptive Formulare
description: Der Regeleditor für adaptive Formulare ermöglicht es Ihnen, ohne Programmierung oder Scripting dynamisches Verhalten und komplexe Logik in Ihre Formulare zu integrieren.
topic-tags: develop
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Adaptive Forms,Foundation Components
discoiquuid: 1b905e66-dc05-4f14-8025-62a78feef12a
docset: aem65
exl-id: c611a1f8-9d94-47f3-bed3-59eef722bf98
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '6607'
ht-degree: 100%

---

# Regeleditor für adaptive Formulare {#adaptive-forms-rule-editor}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

## Überblick {#overview}

Der Regeleditor in Adobe Experience Manager Forms ermöglicht es Geschäftsbenutzenden und Entwickelnden, Regeln für adaptive Formularobjekte zu schreiben. Diese Regeln definieren Aktionen für Formularobjekte, die durch voreingestellte Bedingungen, Benutzereingaben und Benutzeraktionen im Formular ausgelöst werden. Dies ermöglicht noch größere Effizienz für ein schnelles und korrektes Ausfüllen der Formulare.

Der Regeleditor bietet eine intuitive und vereinfachte Benutzeroberfläche zum Schreiben von Regeln. Der Regeleditor bietet einen visuellen Editor für alle Benutzer. Darüber hinaus bietet der Regeleditor einen Code-Editor, mit dem Regeln und Skripte geschrieben werden können.
<!-- Some of the key actions that you can perform on adaptive form objects using rules are:

* Show or hide an object
* Enable or disable an object
* Set a value for an object
* Validate the value of an object
* Execute functions to compute the value of an object
* Invoke a form data model service and perform an operation
* Set property of an object -->

Der Regeleditor ersetzt die Skipterstellungs-Funktionen aus AEM 6.1 Forms und früheren Versionen. Ihre bereits vorhandenen Skripte werden allerdings im neuen Regeleditor beibehalten. Weitere Informationen zum Arbeiten mit vorhandenen Skripten im Regeleditor finden Sie unter [Einfluss des Regeleditors auf bereits vorhandene Skripte](#impact-of-rule-editor-on-existing-scripts).

Benutzende, die zur Gruppe der Formular-Hauptbenutzenden hinzugefügt wurden, können neue Skripte erstellen und bestehende Skripte bearbeiten. Benutzende in der Gruppe „forms-users“ können die Skripte verwenden, aber keine Skripte erstellen oder bearbeiten.

## Grundlegendes zu Regeln {#understanding-a-rule}

Eine Regel ist eine Kombination aus Aktionen und Bedingungen. Im Regeleditor umfassen Aktionen Aktivitäten wie das Ausblenden, Anzeigen, Aktivieren, Deaktivieren oder Berechnen des Werts eines Objekts in einem Formular. Bedingungen sind boolesche Ausdrücke, die durch Prüfungen und Vorgänge für den Status, den Wert oder die Eigenschaft eines Formularobjekts ausgewertet werden. Aktionen werden basierend auf dem bei der Auswertung einer Bedingung zurückgegebenen Wert (`True` oder `False`) ausgeführt.

Der Regeleditor bietet eine Reihe vordefinierter Regeltypen, z. B. „Wenn“, „Anzeigen“, „Ausblenden“, „Aktivieren“, „Deaktivieren“, „Wert einstellen von“ und „Validieren“, um Ihnen beim Schreiben von Regeln zu helfen. Mit jedem Regeltyp können Sie Bedingungen und Aktionen in einer Regel definieren. In diesem Dokument sind die einzelnen Regeltypen im Detail beschrieben.

Eine Regel folgt normalerweise einem der folgenden Konstrukte:

**Bedingung-Aktion** In diesem Konstrukt definiert die Regel zuerst eine Bedingung und dann die auszulösende Aktion. Dieses Konstrukt ist mit einer if-then-Anweisung in Programmiersprachen vergleichbar.

Im Regeleditor wird das Bedingung-Aktion-Konstrukt durch den Regeltyp **Wenn** durchgesetzt.

**Aktion-Bedingung** In diesem Konstrukt definiert die Regel zuerst eine auszulösende Aktion und dann die auszuwertenden Bedingungen. Eine weitere Variante dieses Konstrukts ist Aktion-Bedingung-alternative Aktion, wobei auch dann eine alternative Aktion angegeben wird, die ausgelöst wird, wenn die Bedingung den Wert „False“ zurückgibt.

Die Regeltypen „Anzeigen“, „Ausblenden“, „Aktivieren“, „Deaktivieren“, „Wert festlegen“ und „Validieren“ im Regeleditor setzen das Aktion-Bedingung-Regelkonstrukt um. Die alternative Aktion für „Anzeigen“ ist standardmäßig „Ausblenden“, für „Aktivieren“ ist es „Deaktivieren“ und umgekehrt. Sie können die standardmäßige alternative Aktion nicht ändern.

>[!NOTE]
>
>Die verfügbaren Regeltypen, einschließlich der Bedingungen und Aktionen, die Sie im Regeleditor definieren, hängen auch vom Typ des Formularobjekts ab, für das Sie eine Regel erstellen. Der Regeleditor zeigt nur gültige Regeltypen und Optionen zum Schreiben von Bedingungs- und Aktionsanweisungen für einen bestimmten Formularobjekttyp an. So werden für ein Bereichsobjekt beispielsweise keine Regeln vom Typ „Validieren“, „Wert festlegen“ oder „Deaktivieren“ angezeigt.

Weitere Informationen über die im Regeleditor verfügbaren Regeltypen finden Sie unter [Verfügbare Regeltypen im Regeleditor](#available-rule-types-in-rule-editor).

### Richtlinien für die Auswahl eines Regelkonstrukts {#guidelines-for-choosing-a-rule-construct}

Für die meisten Anwendungsfälle können Sie ein beliebiges Regelkonstrukt verwenden. Nachfolgend finden Sie jedoch einige Richtlinien für die Wahl des am besten geeigneten Konstrukts für Ihre Zwecke. Weitere Informationen über die verfügbaren Regeln im Regeleditor finden Sie unter [Verfügbare Regeltypen im Regeleditor](#available-rule-types-in-rule-editor).

* Eine typische Faustregel bei der Erstellung einer Regel ist, sie im Kontext des Objekts zu betrachten, für das Sie eine Regel schreiben. Angenommen, Feld B soll in Abhängigkeit von einem Wert, den eine Benutzerin oder ein Benutzer in Feld A eingibt, angezeigt oder ausgeblendet werden. In diesem Fall wird eine Bedingung für Feld A ausgewertet und basierend auf dem zurückgegebenen Wert eine Aktion für Feld B ausgelöst.

  Verwenden Sie daher beim Schreiben einer Regel für Feld B (das Objekt, für das eine Bedingung ausgewertet wird) das Konstrukt „Bedingung-Aktion“ oder den Regeltyp „Wenn“. Für Feld A müssten Sie dementsprechend das Konstrukt „Aktion-Bedingung“ oder den Regeltyp „Anzeigen“ oder „Ausblenden“ verwenden.

* In manchen Fällen müssen Sie mehrere Aktionen für dieselbe Bedingung ausführen. In solchen Fällen empfiehlt es sich, das Konstrukt „Bedingung-Aktion“ zu verwenden. In diesem Konstrukt können Sie eine Bedingung einmal auswerten und mehrere Aktionsanweisungen angeben.

  Um beispielsweise die Felder B, C und D basierend auf einer Bedingung auszublenden, durch die der von einer Benutzerin oder einem Benutzer in Feld A angegebenen Wert geprüft wird, genügt eine Regel mit dem Konstrukt „Bedingung-Aktion“ oder dem Regeltyp „Wenn“ für Feld A, wobei Aktionen für die Sichtbarkeit der Felder B, C und D angegeben werden. Andernfalls benötigen Sie drei separate Regeln für die Felder B, C und D, wobei jede Regel die Bedingung prüft und das jeweilige Feld angezeigt oder ausgeblendet wird. In diesem Beispiel ist das Schreiben einer Wenn-Regel für ein Objekt effizienter als die Erstellung von Regeln zum Anzeigen und Ausblenden für drei Objekte.

* Um eine Aktion in Abhängigkeit von mehreren Bedingungen auszulösen, empfiehlt es sich, das Konstrukt „Aktion-Bedingung“ zu verwenden. Um beispielsweise Feld A nach Auswertung der Bedingungen für die Felder B, C und D anzuzeigen oder auszublenden, verwenden Sie Regeln des Typs „Anzeigen“ oder „Ausblenden“ für Feld A.
* Für Regeln, die genau eine Aktion für eine Bedingung enthalten, können Sie sowohl Bedingung-Aktion- als auch Aktion-Bedingung-Konstrukte verwenden.
* Für Regeln, bei denen auf eine Bedingung geprüft und sofort nach Eingabe eines Werts in ein Feld oder beim Verlassen des Felds eine Aktion ausgeführt wird, empfiehlt es sich, eine Regel mit dem Konstrukt „Bedingung-Aktion“ oder dem Regeltyp „Wenn“ für das Feld zu schreiben, für das die Bedingung ausgewertet wird.
* Die Bedingung in der Wenn-Regel wird ausgewertet, wenn ein Benutzer den Wert des Objekts ändert, auf das die Wenn-Regel angewendet wird. Soll die Aktion jedoch ausgelöst werden, wenn der Wert Server-seitig geändert wird (z. B. wenn der Wert vorab ausgefüllt wird), empfehlen wir, eine Wenn-Regel zu erstellen, die die Aktion beim Initialisieren des Felds auslöst.
* Beim Schreiben von Regeln für Dropdown-Elemente, Optionsfelder oder Kontrollkästchenobjekte werden die Optionen oder Werte dieser Formularobjekte im Formular im Regeleditor vorbefüllt.

## Verfügbare Typen von Operatoren und Ereignissen im Regeleditor {#available-operator-types-and-events-in-rule-editor}

Der Regeleditor bietet die folgenden logischen Operatoren und Ereignisse, mit deren Hilfe Sie Regeln erstellen können.

* **Ist gleich**
* **Ist nicht gleich**
* **Beginnt mit**
* **Endet mit**
* **Enthält**
* **Ist leer**
* **Ist nicht leer**
* **Hat ausgewählt:** Gibt „true“ zurück, wenn der Benutzer eine bestimmte Option für ein Kontrollkästchen, ein Dropdown-Element oder ein Optionsfeld auswählt.
* **Ist initialisiert (Ereignis):** Gibt „true“ zurück, wenn ein Formularobjekt im Browser dargestellt wird.
* **Wird geändert (Ereignis):** Gibt „true“ zurück, wenn der Benutzer den eingegebenen Wert oder die ausgewählte Option für ein Formularobjekt ändert.

## Verfügbare Typen von Regeln im Regeleditor {#available-rule-types-in-rule-editor}

Der Regeleditor bietet eine Reihe vordefinierter Regeltypen, mit denen Sie Regeln schreiben können. Im Folgenden werden die einzelnen Regeltypen detailliert dargestellt. Weitere Informationen zum Erstellen von Regeln im Regeleditor finden Sie unter [Schreiben von Regeln](#write-rules).

### Wenn {#whenruletype}

Der **Wenn**-Regeltyp nutzt das Konstrukt **Bedingung-Aktion-Alternative Aktion**, in manchen Fällen auch nur das Konstrukt **Bedingung-Aktion**. Für diesen Regeltyp geben Sie zunächst eine auszuwertende Bedingung an und dann eine Aktion, die ausgelöst werden soll, wenn die Bedingung erfüllt ist (`True`). Bei Einsatz der Wenn-Regel können Sie mehrere UND- und ODER-Operatoren verwenden, um [verschachtelte Ausdrücke](#nestedexpressions) zu erstellen.

Mit dem Wenn-Regeltyp können Sie eine Bedingung für ein Formularobjekt auswerten und Aktionen für ein oder mehrere Objekte ausführen.

Einfach ausgedrückt: Eine typische Wenn-Regel ist wie folgt aufgebaut:

`When on Object A:`

`(Condition 1 AND Condition 2 OR Condition 3) is TRUE;`

`Then, do the following:`

Aktion 2 auf Objekt B anwenden;
UND
Aktion 3 auf Objekt C anwenden;

_

Beim Erstellen einer Regel für Komponenten mit mehreren Werten (z. B. Optionsfelder oder Listen) werden die Optionen automatisch abgerufen und dem Regelersteller zur Verfügung gestellt. Sie müssen die Optionswerte nicht erneut eingeben.

Eine Liste hat beispielsweise vier Optionen: „Rot“, „Blau“, „Grün“ und „Gelb“. Beim Erstellen der Regel werden die Optionen (Optionsfelder) automatisch abgerufen und der Person, die die Regel erstellt, wie folgt zur Verfügung gestellt:

![multivaluefcdisplayOptions](assets/multivaluefcdisplaysoptions.png)

Beim Schreiben der Wenn-Regel können Sie die Aktion „Wert löschen von“ auslösen. Die Aktion „Wert löschen von“ löscht den Wert des angegebenen Objekts. Mit „Wert löschen von“ als Option in der Wenn-Anweisung können Sie komplexe Bedingungen mit mehreren Feldern erstellen.

![clearvalue](assets/clearvalueof.png)

**Ausblenden**: Blendet das angegebene Objekt aus.

**Anzeigen**: Blendet das angegebene Objekt ein.

**Aktivieren**: Aktiviert das angegebene Objekt.

**Deaktivieren**: Deaktiviert das angegebene Objekt.

**Service aufrufen** Ruft einen Service auf, der in einem Formulardatenmodell konfiguriert ist. Wenn Sie den Vorgang „Service aufrufen“ wählen, wird ein Feld angezeigt. Beim Klicken auf das Feld werden alle in sämtlichen Formulardatenmodellen konfigurierten Dienste in Ihrer AEM-Instanz angezeigt. Bei der Auswahl eines Formulardatenmodell-Services erscheinen zusätzliche Felder, in denen Sie Formularobjekte mit Ein- und Ausgabeparametern für den angegebenen Service zuordnen können. Siehe Beispielregel für den Aufruf von Formulardatenmodell-Services.

Zusätzlich zum Formulardatenmodelldienst können Sie eine direkte WSDL-URL angeben, um einen Web-Dienst aufzurufen. Ein Formulardatenmodelldienst hat jedoch viele Vorteile und verfolgt den empfohlenen Ansatz, einen Dienst aufzurufen.

Weitere Informationen zum Konfigurieren von Services im Formulardatenmodell finden Sie unter [Datenintegration für AEM Forms](/help/forms/using/data-integration.md).

**Wert festlegen**: Berechnet den Wert des angegebenen Objekts und legt ihn fest. Als Objektwert können Sie eine Zeichenfolge, den Wert eines anderen Objekts, den mithilfe eines mathematischem Ausdrucks oder einer Funktion berechneten Wert oder den Wert einer Eigenschaft eines Objekts oder den Ausgabewert von einem konfigurierten Formulardatenmodell-Service festlegen. Wenn Sie die Option „Webservice“ wählen, werden alle in allen Formulardatenmodellen konfigurierten Services auf Ihrer AEM-Instanz angezeigt. Bei der Auswahl eines Formulardatenmodell-Service erscheinen zusätzliche Felder, in denen Sie Formularobjekte mit Ein- und Ausgabeparametern für den angegebenen Service zuordnen können.

Weitere Informationen zum Konfigurieren von Services im Formulardatenmodell finden Sie unter [Datenintegration für AEM Forms](/help/forms/using/data-integration.md).

Mit dem Regeltyp **[!UICONTROL Eigenschaft festlegen]** können Sie den Wert einer Eigenschaft des angegebenen Objekts basierend auf einer Bedingungsaktion festlegen. Sie können die Eigenschaft für eines der folgenden Elemente festlegen:

* visible (Boolescher Wert)
* dorExclusion (Boolescher Wert)
* chartType (Zeichenfolge)
* title (Zeichenfolge)
* aktiviert (Boolescher Wert)
* mandatory (Boolescher Wert)
* validationsDisabled (Boolescher Wert)
* validateExpMessage (Zeichenfolge)
* value (Zahl, Zeichenfolge, Datum)
* items (Liste)
* valid (Boolescher Wert)
* errorMessage (Zeichenfolge)

Damit können Sie Regeln definieren, um Kontrollkästchen dynamisch zum adaptiven Formular hinzuzufügen. Sie können benutzerdefinierte Funktionen, Formularobjekte oder eine Objekteigenschaft verwenden, um eine Regel zu definieren.

![Eigenschaft festlegen](assets/set_property_rule_new.png)

Um eine Regel basierend auf einer benutzerdefinierten Funktion zu definieren, wählen Sie **Funktionsausgabe** in der Dropdown-Liste aus und ziehen Sie eine benutzerdefinierte Funktion mittels Drag-and-Drop aus der Registerkarte **Funktionen**. Wenn die Bedingungsaktion erfüllt ist, wird die Anzahl der in der benutzerdefinierten Funktion definierten Kontrollkästchen dem adaptiven Formular hinzugefügt.

Um eine auf einem Formularobjekt basierende Regel zu definieren, wählen Sie **Formularobjekt** in der Dropdown-Liste aus und ziehen Sie ein Formularobjekt mittels Drag-and-Drop aus der Registerkarte **Formularobjekte**. Wenn die Bedingungsaktion erfüllt ist, wird die Anzahl der im Formularobjekt definierten Kontrollkästchen dem adaptiven Formular hinzugefügt.

Mit einer Regel vom Typ „Eigenschaft festlegen“, die auf einer Objekteigenschaft basiert, können Sie die Anzahl der Kontrollkästchen in einem adaptiven Formular auf der Grundlage einer anderen Objekteigenschaft hinzufügen, die im adaptiven Formular enthalten ist.

Die folgende Abbildung zeigt ein Beispiel für das dynamische Hinzufügen von Kontrollkästchen auf der Grundlage der Anzahl der Dropdown-Listen im adaptiven Formular:

![Objekteigenschaft](assets/object_property_set_property_new.png)

**Wert löschen von**: Löscht den Wert des angegebenen Objekts.

**Fokus festlegen**: Legt den Fokus auf das angegebene Objekt.

**Formular speichern**: Speichert das Formular.

**Formulare senden**: Sendet das Formular.

**Formular zurücksetzen**: Setzt das Formular zurück.

**Formular validieren**: Überprüft das Formular.

**Instanz hinzufügen**: Fügt eine Instanz des angegebenen wiederholbaren Bereichs oder der Tabellenzeile hinzu.

**Instanz entfernen**: Entfernt eine Instanz des angegebenen wiederholbaren Bereichs oder der Tabellenzeile.

**Navigieren zu**: Navigiert zu anderen adaptiven Formularen, anderen Assets (wie Bildern oder Dokument-Fragmenten) oder zu einer externen URL. Weitere Informationen finden Sie unter [Hinzufügen einer Schaltfläche zur interaktiven Kommunikation](../../forms/using/create-interactive-communication.md#addbuttontothewebchannel).

### Wert festlegen {#set-value-of}

Regeln vom Typ **[!UICONTROL Wert einstellen von]** ermöglichen es, den Wert eines Formularobjekts abhängig davon festzulegen, ob die angegebene Bedingung erfüllt ist oder nicht. Als Wert kann der Wert eines anderen Objekts, ein Literal-String, ein aus einem mathematischen Ausdruck oder einer Funktion abgeleiteter Wert oder der Wert einer Eigenschaft eines anderen Objekts oder die Ausgabe eines Formulardatenmodelldiensts sein. In ähnlicher Weise können Sie auf eine Bedingung bei Komponenten, Zeichenfolgen, Eigenschaften oder Werten prüfen, die von Funktionen oder mathematischen Ausdrücken abgeleitet wurden.

Der Regeltyp „Wert festlegen“ steht für manche Formularobjekte nicht zur Verfügung (z. B. nicht für Bereiche und Schaltflächen von Symbolleisten). Eine standardmäßige Regel vom Typ „Wert festlegen“ hat die folgende Struktur:



Wert von Objekt A festlegen auf:

(Zeichenfolge ABC) ODER
(Objekteigenschaft X von Objekt C) ODER
(Wert aus einer Funktion) ODER
(Wert aus einem mathematischen Ausdruck) ODER
(Ausgabewert von einem Datenmodell-Service oder Webservice);

When (optional):

(Condition 1 AND Condition 2 AND Condition 3) is TRUE;



Im folgenden Beispiel wird der Wert im Feld `dependentid` als Eingabe genommen und der Wert des Feldes `Relation` auf die Ausgabe des Arguments `Relation` des Formulardatenmodell-Service `getDependent` festgelegt.

![set-value-web-service](assets/set-value-web-service.png)

Beispiel für die Regel „Wert einstellen von“ unter Verwendung des Formulardatenmodelldienstes

>[!NOTE]
>
>Darüber hinaus können Sie die Regel „Wert einstellen von“ verwenden, um alle Werte in einer Dropdown-Listenkomponente mit der Ausgabe eines Formulardatenmodelldienstes oder eines Web-Dienstes aufzufüllen. Stellen Sie jedoch sicher, dass es sich bei dem von Ihnen ausgewählten Ausgabeargument um einen Array-Typ handelt. Alle Werte, die in einem Array zurückgegeben werden, stehen in der angegebenen Dropdown-Liste zur Verfügung.

### Anzeigen {#show}

Mithilfe des Regeltyps **Anzeigen** können Sie eine Regel schreiben, die ein Formularobjekt je nachdem, ob eine Bedingung erfüllt ist oder nicht, anzeigt oder ausblendet. Der Regeltyp „Anzeigen“ löst auch die Aktion „Ausblenden“ aus, falls die Bedingung nicht erfüllt ist oder `False` zurückgibt.

Eine typische Regel vom Typ „Anzeigen“ ist wie folgt strukturiert:



`Show Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Hide Object A;`



### Ausblenden {#hide}

Regeln vom Typ **Ausblenden** können ähnlich wie Regeln vom Typ „Anzeigen“ dazu verwendet werden, Formularobjekte je nachdem, ob eine Bedingung erfüllt ist oder nicht, anzuzeigen oder auszublenden. Der Regeltyp „Ausblenden“ löst auch die Aktion „Anzeigen“ aus, falls die Bedingung nicht erfüllt ist oder `False` zurückgibt.

Eine typische Regel vom Typ „Ausblenden“ ist wie folgt strukturiert:



`Hide Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Show Object A;`



### Aktivieren {#enable}

Mithilfe des Regeltyps **Aktivieren** können Sie ein Formularobjekt in Abhängigkeit davon aktivieren oder deaktivieren, ob eine Bedingung erfüllt ist oder nicht. Der Regeltyp „Aktivieren“ löst auch die Aktion „Deaktivieren“ aus, falls die Bedingung nicht erfüllt ist oder `False` zurückgibt.

Eine typische Regel vom Typ „Aktivieren“ ist wie folgt strukturiert:



`Enable Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Disable Object A;`



### Deaktivieren {#disable}

Mit Regeln vom Typ **Deaktivieren** können Sie ähnlich wie mit Regeln vom Typ „Aktivieren“ Formularobjekte in Abhängigkeit davon, ob eine Bedingung erfüllt ist oder nicht, aktivieren oder deaktivieren. Der Regeltyp „Deaktivieren“ löst auch die Aktion „Aktivieren“ aus, falls die Bedingung nicht erfüllt ist oder `False` zurückgibt.

Eine typische Regel vom Typ „Deaktivieren“ ist wie folgt strukturiert:



`Disable Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Enable Object A;`

### Validieren {#validate}

Regeln vom Typ **Validieren** überprüfen den Wert in einem Feld mithilfe eines Ausdrucks. So können Sie beispielsweise einen Ausdruck erstellen, der ein Textfeld zur Eingabe eines Namens daraufhin überprüft, dass dort keine Sonderzeichen oder Zahlen eingegeben wurden.

Eine typische Regel vom Typ „Validieren“ ist wie folgt strukturiert:

`Validate Object A;`

`Using:`

`(Expression 1 AND Expression 2 AND Expression 3) is TRUE;`

>[!NOTE]
>
>Wenn der angegebene Wert nicht der Validierungsregel entspricht, können Sie eine Validierungsmeldung für die Benutzenden anzeigen lassen. Sie können die Meldung im Feld **[!UICONTROL Skriptüberprüfungsmeldung]** in den Komponenteneigenschaften in der Seitenleiste angeben.

![script-validation](assets/script-validation.png)

### Optionen festlegen {#setoptionsof}

Mit dem Regeltyp **Optionen festlegen von** können Sie Regeln definieren, um Kontrollkästchen dynamisch zum adaptiven Formular hinzuzufügen. Sie können ein Formulardatenmodell oder eine benutzerdefinierte Funktion verwenden, um die Regel zu definieren.

Um eine Regel basierend auf einer benutzerdefinierten Funktion zu definieren, wählen Sie **Funktionsausgabe** in der Dropdown-Liste aus und ziehen Sie eine benutzerdefinierte Funktion mittels Drag-and-Drop aus der Registerkarte **Funktionen**. Die in der benutzerdefinierten Funktion definierte Anzahl von Kontrollkästchen wird dem adaptiven Formular hinzugefügt.

![Benutzerdefinierte Funktionen](assets/custom_functions_set_options_new.png)

Informationen über das Erstellen einer benutzerdefinierten Funktion finden Sie unter [Benutzerdefinierte Funktionen im Regeleditor](#custom-functions).

So definieren Sie eine auf einem Formulardatenmodell basierende Regel:

1. Wählen Sie **Service-Ausgabe** in der Dropdown-Liste aus.
1. Wählen Sie das Datenmodellobjekt aus.
1. Wählen Sie in der Dropdown-Liste **Wert anzeigen** eine Datenmodell-Objekteigenschaft aus. Die Anzahl der Kontrollkästchen im adaptiven Formular wird von der Anzahl der Instanzen abgeleitet, die für diese Eigenschaft in der Datenbank definiert wurden.
1. Wählen Sie in der Dropdown-Liste **Wert speichern** eine Datenmodell-Objekteigenschaft.

![FDM-Set-Optionen](assets/fdm_set_options_new.png)

## Grundlegendes zur Benutzeroberfläche des Regeleditors {#understanding-the-rule-editor-user-interface}

Der Regeleditor bietet eine umfangreiche und dennoch einfache Benutzeroberfläche zum Erstellen und Verwalten von Regeln. Sie können die Benutzeroberfläche des Regeleditors im Authoring-Modus von einem adaptiven Formular aus aufrufen.

So starten Sie die Benutzeroberfläche des Regeleditors:

1. Öffnen Sie ein adaptives Formular im Authoring-Modus.
1. Wählen Sie das Formularobjekt aus, für das Sie eine Regel erstellen möchten, und wählen Sie in der Komponentensymbolleiste ![edit-rules](assets/edit-rules.png) aus. Die Benutzeroberfläche des Regeleditors wird angezeigt.

   ![create-rules](assets/create-rules.png)

   Alle vorhandenen Regeln für die ausgewählten Formularobjekte werden in dieser Ansicht aufgelistet. Weitere Informationen zum Verwalten vorhandener Regeln finden Sie unter [Verwalten von Regeln](#manage-rules).

1. Wählen Sie **[!UICONTROL Erstellen]**, um eine neue Regel zu erstellen. Wenn Sie den Regeleditor zum ersten Mal starten, wird standardmäßig der Visual Editor der Regeleditor-Benutzeroberfläche geöffnet.

   ![Benutzeroberfläche des Regeleditors](assets/rule-editor-ui.png)

Nachfolgend werden die einzelnen Komponenten der Benutzeroberfläche des Regeleditors im Detail beschrieben.

### A. Ansicht „Komponente und Regel“ {#a-component-rule-display}

Hier werden der Titel des adaptiven Formularobjekts, über das Sie den Regeleditor aufgerufen haben, sowie der derzeit ausgewählte Regeltyp angezeigt. Im oben gezeigten Beispiel wurde der Regeleditor über ein adaptives Formularobjekt namens „Salary“ gestartet und der Wenn-Regeltyp ist ausgewählt.

### B. Formularobjekte und Funktionen {#b-form-objects-and-functions-br}

Im linken Bereich der Benutzeroberfläche des Regeleditors stehen zwei Registerkarten zur Verfügung: **[!UICONTROL Formularobjekte]** und **[!UICONTROL Funktionen]**.

Die Registerkarte „Formularobjekte“ zeigt eine hierarchische Ansicht aller Objekte an, die in dem adaptiven Formular enthalten sind. Angezeigt werden Titel und Typ der Objekte. Wenn Sie eine Regel erstellen, können Sie Formularobjekte in den Regeleditor ziehen und dort ablegen. Wenn Sie beim Erstellen oder Bearbeiten einer Regel ein Objekt oder eine Funktion in einen Platzhalter ziehen, übernimmt dieser Platzhalter automatisch den entsprechenden Wertetyp.

Die Formularobjekte, auf die eine oder mehrere gültige Regeln angewendet wurden, sind mit einem grünen Punkt markiert. Wenn eine der auf ein Formularobjekt angewendeten Regeln ungültig ist, ist das Formularobjekt mit einem gelben Punkt markiert.

Die Registerkarte „Funktionen“ enthält eine Reihe integrierter Funktionen (z. B. „Summe von“, „Minimum von“, „Maximum von“, „Durchschnitt von“, „Anzahl von“ und „Formular validieren“). Sie können diese Funktionen verwenden, um Werte in wiederholbaren Bereichen und Tabellenzeilen zu berechnen und sie beim Erstellen von Regeln in den Aktions- und Bedingungsanweisungen zu verwenden. Sie können jedoch auch [benutzerdefinierte Funktionen](#custom-functions) erstellen.

![Die Registerkarte „Funktionen“](assets/functions.png)

>[!NOTE]
>
>Sie können auf den Registerkarten „Formularobjekte“ und „Funktionen“ eine Textsuche nach den Namen und Titeln von Objekten und Funktionen durchführen.

In der linken Baumstruktur der Formularobjekte können Sie die Formularobjekte auswählen, um die Regeln anzuzeigen, die auf die einzelnen Objekte angewendet werden. Sie können nicht nur durch die Regeln der verschiedenen Formularobjekte navigieren, sondern auch Regeln zwischen den Formularobjekten kopieren und einfügen. Weitere Informationen finden Sie unter [Kopieren und Einfügen von Regeln](#copy-paste-rules).

### C. Umschalten zwischen Formularobjekten und Funktionen {#c-form-objects-and-functions-toggle-br}

Durch Tippen auf die Schaltfläche schalten Sie zwischen den Bereichen für Formularobjekte und Funktionen um.

### D. Visueller Regeleditor {#d-visual-rule-editor}

Der visuelle Regeleditor ist im visuellen Editormodus der Benutzeroberfläche des Regeleditors der Bereich, in dem Sie Regeln schreiben. Sie können hier einen Regeltyp auswählen und die entsprechenden Bedingungen und Aktionen definieren. Beim Definieren von Bedingungen und Aktionen in einer Regel können Sie Formularobjekte und Funktionen aus dem Bereich „Formularobjekte und Funktionen“ ziehen und ablegen.

Weitere Informationen zur Verwendung des visuellen Regeleditors finden Sie unter [Regeln schreiben](#write-rules).

### E. Umschalter zwischen Visual Editor und Code-Editor {#e-visual-code-editors-switcher}

Benutzende in der Gruppe „forms-power-users“ können auf den Code-Editor zugreifen. Für andere Benutzende ist der Code-Editor nicht verfügbar. Mit dem direkt über dem Regeleditor befindlichen Umschalter können Sie zwischen den Modi „Visual Editor“ und „Code-Editor“ wechseln, sofern Sie dazu berechtigt sind. Wenn Sie den Regeleditor zum ersten Mal starten, wird er im Modus „Visual Editor“ geöffnet. Sie können Regeln im Modus „Visual Editor“ erstellen oder in den Modus „Code-Editor“ wechseln, um ein Regelskript zu schreiben. Wenn Sie eine Regel im Code-Editor ändern oder schreiben, ist es jedoch nicht möglich, für diese Regel in den Visual Editor zurückzuwechseln, es sei denn, Sie löschen den Inhalt des Code-Editors.

AEM Forms zeichnet den zuletzt von Ihnen zum Schreiben einer Regel verwendeten Regeleditor-Modus auf. Wenn Sie den Regeleditor das nächste Mal starten, wird er in diesem Modus geöffnet. Sie können jedoch auch einen Standardmodus konfigurieren, sodass der Regeleditor immer in diesem Modus geöffnet wird. Gehen Sie dazu wie folgt vor:

1. Wechseln Sie zur AEM-Web-Konsole unter `https://[host]:[port]/system/console/configMgr`.
1. Zum Bearbeiten klicken Sie auf **[!UICONTROL Konfiguration von adaptiven Formularen und Web-Kanälen für interaktive Kommunikation]**.
1. Wählen Sie **[!UICONTROL Visual Editor]** oder **[!UICONTROL Codeeditor]** aus der Dropdownliste für den **[!UICONTROL Standardmodus für den Regeleditor]**.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

### F. Schaltflächen „Fertig“ und „Abbrechen“ {#f-done-and-cancel-buttons}

Die Schaltfläche **[!UICONTROL Fertig]** wird verwendet, um eine Regel zu speichern. Sie können eine unvollständige Regel speichern. Unvollständige Regeln sind jedoch ungültig und werden nicht ausgeführt. Gespeicherte Regeln für ein Formularobjekt werden aufgelistet, wenn Sie den Regeleditor das nächste Mal von demselben Formularobjekt aus starten. In dieser Ansicht können Sie vorhandene Regeln verwalten. Weitere Informationen finden Sie unter [Verwalten von Regeln](#manage-rules).

Über die Schaltfläche **[!UICONTROL Abbrechen]** verwerfen Sie alle Änderungen, die Sie an einer Regel vorgenommen haben, und der Regeleditor wird geschlossen.

## Regeln schreiben {#write-rules}

Zum Schreiben von Regeln können Sie den visuellen Regeleditor oder den Code-Editor verwenden. Wenn Sie den Regeleditor zum ersten Mal starten, wird er im Modus „Visual Editor“ geöffnet. Sie können zum Code-Editormodus wechseln und Regeln schreiben. Wenn Sie eine Regel im Code-Editor schreiben oder ändern, ist es jedoch nicht möglich, für diese Regel zum Visual Editor zu wechseln, es sei denn, Sie löschen den Inhalt des Code-Editors. Wenn Sie den Regeleditor das nächste Mal starten, wird er im zuletzt zum Erstellen von Regeln verwendeten Modus geöffnet.

Im Folgenden wird zunächst das Schreiben von Regeln im Visual Editor beschrieben.

### Verwenden des Visual Editor {#using-visual-editor}

Anhand des folgenden Beispielformulars soll das Erstellen von Regeln im visuellen Editor verständlich gemacht werden.

![create-rule-example](assets/create-rule-example.png)

Im Abschnitt für die Kreditanforderungen in diesem beispielhaften Kreditantrag müssen die Antragstellenden ihren Familienstand, ihr Gehalt und, falls verheiratet, das Gehalt der Partnerin bzw. des Partners angeben. Basierend auf den Benutzereingaben wird mithilfe der Regel der Kreditanspruchsbetrag berechnet und im Feld für den Kreditanspruch angegeben. Wenden Sie die folgenden Regeln an, um dieses Szenario zu implementieren:

* Das Feld für das Gehalt der Partnerin bzw. des Partners wird nur angezeigt, wenn als Familienstand „Verheiratet“ angegeben wurde.
* Der Kreditanspruchsbetrag ist 50 % des Gesamtgehalts.

Führen Sie die folgenden Schritte aus, um die Regeln zu schreiben:

1. Schreiben Sie zuerst die Regel, mit der die Sichtbarkeit des Felds „Gehalt des Partners“ entsprechend der vom Benutzer über das Optionsfeld „Familienstand“ gewählten Option gesteuert wird.

   Öffnen Sie das Kreditantragsformular im Autorenmodus. Wählen Sie die Komponente **Familienstand** und ![edit-rules](assets/edit-rules.png) aus. Wählen Sie als Nächstes **[!UICONTROL Erstellen]** aus, um den Regeleditor zu starten.

   ![write-rules-visual-editor-1](assets/write-rules-visual-editor-1.png)

   Wenn Sie den Regeleditor starten, ist standardmäßig die Wenn-Regel ausgewählt. Darüber hinaus wird das Formularobjekt (in diesem Fall „Familienstand“), von dem aus Sie den Regeleditor gestartet haben, in der Wenn-Anweisung angegeben.

   Sie können zwar das ausgewählte Objekt nicht bearbeiten oder ändern, es ist jedoch möglich, über die Dropdown-Liste für Regeln einen anderen Regeltyp wählen (siehe unten). Wenn Sie eine Regel für ein anderes Objekt erstellen möchten, wählen Sie „Abbrechen“ aus, um den Regeleditor zu beenden, und starten Sie ihn erneut über das gewünschte Formularobjekt.

1. Wählen Sie die Dropdown-Liste **[!UICONTROL Status auswählen]** und **[!UICONTROL Ist gleich]** aus. Das Feld **[!UICONTROL Eine Zeichenfolge eingeben]** wird angezeigt.

   ![write-rules-visual-editor-2](assets/write-rules-visual-editor-2.png)

   In dem Optionsfeld „Familienstand“ werden den Optionen **Verheiratet** und **Ledig** die Werte **0** bzw. **1** zugewiesen. Sie können die zugewiesenen Werte auf der Registerkarte „Titel“ des Dialogfelds zum Bearbeiten des Optionsfelds überprüfen, wie unten gezeigt.

   ![Optionsfeldwerte im Regeleditor](assets/radio-button-values.png)

1. Geben Sie in der Regel im Feld **Eine Zeichenfolge eingeben** den Wert **0** an.

   ![write-rules-visual-editor-4](assets/write-rules-visual-editor-4.png)

   Sie haben die Bedingung als `When Marital Status is equal to Married` definiert. Definieren Sie anschließend die Aktion, die ausgeführt werden soll, wenn diese Bedingung „True“ lautet.

1. Wählen Sie für die Dann-Anweisung die Option **[!UICONTROL Anzeigen]** aus der Dropdown-Liste **[!UICONTROL Aktion auswählen]**.

   ![write-rules-visual-editor-5](assets/write-rules-visual-editor-5.png)

1. Ziehen Sie das Feld **Gehalt des Partners** aus der Registerkarte „Formularobjekte“ in das Feld **Legen Sie das Objekt ab oder wählen Sie hier aus**. Stattdessen können Sie auch das Feld **Objekt hier einfügen oder auswählen** auswählen und das Feld **Gehalt des Partners** aus dem Popup-Menü wählen, in dem sämtliche Formularobjekte im Formular aufgeführt sind.

   ![write-rules-visual-editor-6](assets/write-rules-visual-editor-6.png)

   Die Regel wird im Regeleditor wie folgt angezeigt.

   ![write-rules-visual-editor-7](assets/write-rules-visual-editor-7.png)

   Wählen Sie **Fertig** aus, um die Regel zu speichern.

1. Wiederholen Sie die Schritte 1 bis 5, um eine weitere Regel zu definieren, mit der das Feld für das Gehalt der Partnerin bzw. des Partners ausgeblendet wird, wenn unter Familienstand „Ledig“ angegeben ist. Die Regel wird im Regeleditor wie folgt angezeigt.

   ![write-rules-visual-editor-8](assets/write-rules-visual-editor-8.png)

   >[!NOTE]
   >
   >Alternativ zu diesem Verfahren können Sie dieses Verhalten auch implementieren, indem Sie für das Feld „Gehalt des Partners“ lediglich eine Regel vom Typ „Anzeigen“ anstelle zweier Wenn-Regeln für das Feld „Familienstand“ erstellen.

   ![write-rules-visual-editor-9](assets/write-rules-visual-editor-9.png)

1. Als Nächstes erstellen Sie eine Regel für die Berechnung des Kreditanspruchsbetrags (50 % des Gesamtgehalts) und zur Anzeige des Betrags im Feld für den Kreditanspruch. Erstellen Sie hierzu Regeln des Typs **Wert einstellen von** für das Feld „Kreditanspruch“.

   Wählen Sie im Autorenmodus das Feld **[!UICONTROL Kreditanspruch]** und dann![edit-rules](assets/edit-rules.png) aus. Wählen Sie anschließend **[!UICONTROL Erstellen]** aus, um den Regeleditor zu starten.

1. Wählen Sie in der Dropdown-Liste „Regeln“ die Regel **[!UICONTROL Wert festlegen]** aus.

   ![write-rules-visual-editor-10](assets/write-rules-visual-editor-10.png)

1. Wählen Sie **[!UICONTROL Option auswählen]** und dann **[!UICONTROL Mathematischer Ausdruck]** aus. Ein Feld, in dem Sie mathematische Ausdrücke schreiben können, wird geöffnet.

   ![write-rules-visual-editor-11](assets/write-rules-visual-editor-11.png)

1. Gehen Sie in diesem Ausdrucksfeld wie folgt vor:

   * Wählen Sie das Feld **Gehalt**   im ersten Feld **Legen Sie das Objekt ab oder wählen Sie hier aus** aus oder ziehen Sie es von der Registerkarte „Formularobjekt“ hierhin.

   * Wählen Sie aus dem Feld **Operator auswählen** die Option **plus** aus.

   * Wählen Sie das Feld **Gehalt des Partners** auf der Registerkarte „Formularobjekt“ aus oder ziehen Sie es in das zweite Feld **Legen Sie das Objekt ab oder wählen Sie hier aus** und legen Sie es dort ab.

   ![write-rules-visual-editor-12](assets/write-rules-visual-editor-12.png)

1. Wählen Sie als Nächstes etwas im hervorgehobenen Bereich um das Ausdrucksfeld und wählen Sie dann **Ausdruck erweitern** aus.

   ![write-rules-visual-editor-13](assets/write-rules-visual-editor-13.png)

   Wählen Sie im Feld für den erweiterten Ausdruck im Feld **Operator auswählen** die Option **geteilt durch** und im Feld **Option auswählen** die Option **Zahl** aus. Geben Sie **2** in das Zahlenfeld ein.

   ![write-rules-visual-editor-14](assets/write-rules-visual-editor-14.png)

   >[!NOTE]
   >
   >Sie können mithilfe von Komponenten, Funktionen, mathematischen Ausdrücken und Eigenschaftswerten aus dem Feld „Option auswählen“ komplexe Ausdrücke erstellen.

   Erstellen Sie als Nächstes eine Bedingung, bei der bei Rückgabe von „True“ der Ausdruck ausgeführt wird.

1. Wählen Sie **Bedingung hinzufügen** aus, um eine Wenn-Anweisung hinzuzufügen.

   ![write-rules-visual-editor-15](assets/write-rules-visual-editor-15.png)

   Gehen Sie in der Wenn-Anweisung wie folgt vor:

   * Wählen Sie im ersten Feld **Legen Sie das Objekt ab oder wählen Sie hier aus** das Feld **Familienstand** aus oder ziehen Sie es von der Registerkarte „Formularobjekt“ hierhin.

   * Wählen Sie im Feld **Operator auswählen** die Option **ist gleich** aus.

   * Wählen Sie in dem anderen Feld **Legen Sie das Objekt ab oder wählen Sie hier aus** den Eintrag „String“ (Zeichenfolge) aus und geben Sie **Verheiratet** in das Feld **Geben Sie eine Zeichenfolge ein** ein.

   Die Regel wird schließlich wie folgt im Regeleditor angezeigt.  ![write-rules-visual-editor-16](assets/write-rules-visual-editor-16.png)

   Wählen Sie **Fertig** aus, um die Regel zu speichern.

1. Folgen Sie wiederum Schritt 7 bis 12, um eine andere Regel zu definieren, mit deren Hilfe der Kreditanspruch berechnet wird, sofern der Familienstand „Ledig“ ist. Die Regel wird im Regeleditor wie folgt angezeigt.

   ![write-rules-visual-editor-17](assets/write-rules-visual-editor-17.png)

>[!NOTE]
>
>Sie können auch die Regel „Wert einstellen von“ verwenden, um den Kreditanspruch über die Wenn-Regel zu berechnen, die Sie erstellt haben, um das Feld für das Gehalt der Partnerin bzw. des Partners ein- bzw. auszublenden. Die resultierende kombinierte Regel (für den Familienstand „Ledig“) wird wie folgt im Regeleditor angezeigt.
>
>Auf ähnliche Weise können Sie eine kombinierte Regel erstellen, die die Sichtbarkeit des Felds für das Gehalt der Partnerin bzw. des Partners steuert und den Kreditanspruch berechnet, wenn unter Familienstand „Verheiratet“ angegeben ist.

![write-rules-visual-editor-18](assets/write-rules-visual-editor-18.png)

### Verwenden des Code-Editors {#using-code-editor}

Benutzende, die zur Gruppe der Formular-Hauptbenutzenden hinzugefügt wurden, können den Code-Editor verwenden. Der Regeleditor generiert automatisch den JavaScript-Code für jede Regel, die Sie mit dem Visual Editor erstellen. Indem Sie vom Visual Editor zum Code-Editor wechseln, können Sie den generierten Code anzeigen. Wenn Sie jedoch den Code einer Regel im Code-Editor ändern, können Sie nicht mehr zum Visual Editor zurückwechseln. Sie können neue Regeln auch von Anfang an im Code-Editor schreiben, wenn Sie diesen dem Visual Editor vorziehen. Mit dem Umschalter zwischen Visual Editor und Code-Editor können Sie zwischen den beiden Modi wechseln. 

Das im Code-Editor verwendete JavaScript ist die Ausdruckssprache für adaptive Formulare. Alle Ausdrücke sind gültige JavaScript-Ausdrücke und nutzen Scripting-Modell-APIs für adaptive Formulare. Diese Ausdrücke geben Werte bestimmter Typen zurück. Eine vollständige Liste der Klassen, Ereignisse, Objekte und öffentlichen APIs für adaptive Formulare finden Sie unter [API-Referenz der JavaScript-Bibliothek für adaptive Formulare](https://helpx.adobe.com/de/experience-manager/6-5/forms/javascript-api/index.html).

Weitere Informationen zu Richtlinien zum Schreiben von Regeln im Code-Editor finden Sie unter [Adaptive Formularausdrücke](/help/forms/using/adaptive-form-expressions.md).

Beim Schreiben von JavaScript-Code in den Regeleditor helfen Ihnen die folgenden visuellen Hinweise bei der Strukturierung und Syntax:

* Syntaxhervorhebungen
* automatischer Einzug
* Hinweise und Vorschläge für Formularobjekte, Funktionen und deren Eigenschaften
* automatisches Ausfüllen von Formularkomponentennamen und Fertigstellen gängiger JavaScript-Funktionen

![javascriptruleeditor](assets/javascriptruleeditor.png)

#### Benutzerdefinierte Funktionen im Regeleditor {#custom-functions}

Zusätzlich zu den vorkonfigurierten Funktionen wie beispielsweise *Summe von*, die unter „Funktionenausgabe“ aufgeführt sind, können Sie auch benutzerdefinierte Funktionen erstellen, die Sie häufig benötigen. Stellen Sie sicher, dass für die Funktion, die Sie schreiben, ein `jsdoc` vorhanden ist.

Dieses dazugehörige `jsdoc` ist aus den folgenden Gründen erforderlich:

* Wenn Sie benutzerdefinierte Konfigurationen und Beschreibungen verwenden möchten.
* Da Funktionen in `JavaScript,` auf unterschiedliche Weise deklariert werden können und Sie mithilfe der Kommentare den Überblick über die Funktionen behalten.

Weitere Informationen finden Sie unter [usejsdoc.org](https://jsdoc.app/).

Unterstützte `jsdoc`-Tags:

* **Private** (Privat)
Syntax: `@private`  
Eine Private-Funktion ist nicht als benutzerdefinierte Funktion enthalten.

* **Name**
Syntax: `@name funcName <Function Name>`
Alternativ dazu ist es möglich`,``@function funcName <Function Name>` **oder** `@func` `funcName <Function Name>` zu verwenden.
  `funcName` ist der Name der Funktion (Leerzeichen sind nicht zulässig).
  `<Function Name>` ist der Anzeigename der Funktion.

* **Member** (Mitglied)
Syntax: `@memberof namespace`
Bindet einen Namespace an die Funktion.

* **Parameter**
Syntax: `@param {type} name <Parameter Description>`
Alternativ dazu ist es möglich, `@argument` `{type} name <Parameter Description>` **oder** `@arg` `{type}` `name <Parameter Description>` zu verwenden.
Zeigt die von der Funktion verwendeten Parameter an. In einer Funktion können mehrere Parameter-Tags vorhanden sein (je ein Tag für jeden Parameter in der Reihenfolge ihres Auftretens).
  `{type}` gibt den Parametertyp an. Zulässige Parametertypen sind:

   1. String (Zeichenfolge)
   1. Number (Zahl)
   1. Boolean (Boolesch)
   1. Scope (Umfang)

  Der Umfang wird für die Verweise auf Felder eines adaptiven Formulars verwendet. Wenn ein Formular verzögertes Laden (Lazy Loading) verwendet, können Sie `scope` verwenden, um auf dessen Felder zuzugreifen. Sie können auf Felder zugreifen, wenn die Felder geladen wurden oder wenn die Felder als „global“ gekennzeichnet sind.

  Alle anderen Parametertypen fallen in eine der oben genannten Kategorien. Keine Angabe wird nicht unterstützt. Achten Sie darauf, einen der oben genannten Typen zu wählen. Bei den Typen wird nicht zwischen Groß- und Kleinschreibung unterschieden. Leerzeichen sind im Parameter `name` unzulässig. `<Parameter Descrption>` `<parameter>  can have multiple words. </parameter>`

* **Return Type** (Rückgabetyp)
Syntax: `@return {type}`
Alternativ ist es möglich, `@returns {type}` zu verwenden.
Fügt Informationen über die Funktion hinzu (z. B. ihren Zweck).
Die Zeichenfolge „{type}“ gibt den Rückgabetyp der Funktion an. Zulässige Rückgabetypen sind:

   1. String (Zeichenfolge)
   1. Number (Zahl)
   1. Boolean (Boolesch)

  Alle anderen Rückgabetypen fallen in eine der oben genannten Kategorien. Keine Angabe wird nicht unterstützt. Achten Sie darauf, einen der oben genannten Typen zu wählen. Bei Rückgabetypen wird nicht zwischen Groß- und Kleinschreibung unterschieden.

* **This** (Dieses)
Syntax: `@this currentComponent`

  Verwenden Sie @this, um auf die Komponente des adaptiven Formulars zu verweisen, in der die Regel geschrieben wird.

  Das folgende Beispiel basiert auf dem Feldwert. In dem folgenden Beispiel blendet die Regel ein Feld im Formular aus. Der `this`-Teil von `this.value` bezieht sich auf die zugrunde liegende Komponente des adaptiven Formulars, für die die Regel geschrieben wird.

  ```
     /**
     * @function myTestFunction
     * @this currentComponent
     * @param {scope} scope in which code inside function will be executed.
     */
     myTestFunction = function (scope) {
        if(this.value == "O"){
              scope.age.visible = true;
        } else {
           scope.age.visible = false;
        }
     }
  ```

>[!NOTE]
>
>Kommentare vor benutzerdefinierten Funktionen werden für die Zusammenfassung verwendet. Die Zusammenfassung kann sich über mehrere Zeilen bis zum nächsten Tag erstrecken. Beschränken Sie ihre Länge auf eine einzelne Zeile, um eine kurze Beschreibung im Regel-Builder zu erhalten.

<!--
**Adding a custom function**

For example, you want to add a custom function which calculates area of a square. Side length is the user input to the custom function, which is accepted using a numeric box in your form. The calculated output is displayed in another numeric box in your form. To add a custom function, you have to first create a client library, and then add it to the CRX repository.

Perform the following steps to create a client library and add it in the CRX repository.

1. Create a client library. For more information, see [Using Client-Side Libraries](/help/sites-developing/clientlibs.md).
2. In CRXDE, add a property `categories`with string type value as `customfunction` to the `clientlib` folder.

   >[!NOTE]
   >
   >`customfunction`is an example category. You can choose any name for the category you create in the `clientlib`folder.

After you have added your client library in the CRX repository, use it in your adaptive form. It lets you use your custom function as a rule in your form. Perform the following steps to add the client library in your adaptive form.

1. Open your form in edit mode.
   To open a form in edit mode, select a form and select **Open**.
1. In the edit mode, select a component, then select ![field-level](assets/field-level.png) &gt; **Adaptive Form Container**, and then select ![cmppr](assets/cmppr.png).
1. In the sidebar, under Name of Client Library, add your client library. ( `customfunction` in the example.)

   ![Adding the custom function client library](assets/clientlib.png)

1. Select the input numeric box, and select ![edit-rules](assets/edit-rules.png) to open the rule editor.
1. Select **Create Rule**. Using options shown below, create a rule to save the squared value of the input in the Output field of your form.
   [ ![Using custom functions to create a rule](assets/add_custom_rule_new.png)](assets/add-custom-rule.png)Select **Done**. Your custom function is added.

#### Function declaration supported types {#function-declaration-supported-types}

**Function Statement**

```javascript
function area(len) {
    return len*len;
}
```

This function is included without `jsdoc` comments.

**Function Expression**

```javascript
var area;
//Some codes later
/** */
area = function(len) {
    return len*len;
};
```

**Function Expression and Statement**

```javascript
var b={};
/** */
b.area = function(len) {
    return len*len;
}
```

**Function Declaration as Variable**

```javascript
/** */
var x1,
    area = function(len) {
        return len*len;
    },
    x2 =5, x3 =true;
```

Limitation: custom function picks only the first function declaration from the variable list, if together. You can use function expression for every function declared.

**Function Declaration as Object**

```javascript
var c = {
    b : {
        /** */
        area : function(len) {
            return len*len;
        }
    }
};
```

>[!NOTE]
>
>Ensure that you use `jsdoc` for every custom function. Although `jsdoc`comments are encouraged, include an empty `jsdoc`comment to mark your function as custom function. It enables default handling of your custom function.
-->

Sie können auch benutzerdefinierte Funktionen in Ihrem Regeleditor verwenden. Anweisungen zum Erstellen benutzerdefinierter Funktionen finden Sie im Artikel [Benutzerdefinierte Funktionen in adaptiven Formularen](/help/forms/using/create-and-use-custom-functions.md).

## Verwalten von Regeln {#manage-rules}

Wenn Sie das Objekt und dann ![edit-rules1](assets/edit-rules1.png) auswählen, werden alle vorhandenen Regeln für ein Formularobjekt aufgelistet. Sie können den Titel und eine Vorschau der Regelzusammenfassung anzeigen. Darüber hinaus können Sie in der Benutzeroberfläche die vollständige Regelzusammenfassung erweitern und anzeigen, die Reihenfolge der Regeln ändern, Regeln bearbeiten und Regeln löschen.

![list-rules](assets/list-rules.png)

Sie können die folgenden Aktionen für Regeln durchführen:

* **Anzeigen/Reduzieren**: Die Inhaltsspalte in der Regelliste zeigt den Regelinhalt an. Wenn in der Standardansicht nicht der gesamte Regelinhalt sichtbar ist, wählen Sie ![expand-rule-content](assets/expand-rule-content.png) aus, um die Ansicht zu erweitern.

* **Anordnung ändern**: Jede neue Regel, die Sie erstellen, wird am unteren Rand der Regelliste gestapelt. Die Regeln werden von oben nach unten ausgeführt. Die Regel oben wird zuerst ausgeführt, gefolgt von anderen Regeln desselben Typs. Wenn beispielsweise eine Wenn-, Anzeigen-, Aktivieren- und eine weitere Wenn-Regel an den ersten vier Positionen der Liste stehen, werden zuerst die zuoberst stehende Wenn-Regel und dann die Wenn-Regel an vierter Stelle ausgeführt. Danach werden die Regeln „Anzeigen“ und „Aktivieren“ ausgeführt.
Sie können die Position einer Regel in der Reihenfolge ändern, indem Sie auf ![sort-rules](assets/sort-rules.png) für die Regel tippen oder die Regel an die gewünschte Stelle in der Liste ziehen und dort ablegen.

* **Bearbeiten**: Zum Bearbeiten einer Regel aktivieren Sie das Kontrollkästchen neben ihrem Titel. Weitere Optionen zum Bearbeiten und Löschen der Regel werden angezeigt. Wählen Sie **Bearbeiten** aus, um die ausgewählte Regel im Regeleditor im Visual Editor- oder im Code-Editormodus zu öffnen. Dies ist davon abhängig, welcher Modus zum Erstellen der Regel verwendet wurde.

* **Löschen**: Wählen Sie zum Löschen einer Regel die Regel und dann **Löschen** aus.

* **Aktivieren/Deaktivieren**: Möglicherweise müssen Sie eine Regel vorübergehend aussetzen. Sie können eine oder mehrere Regeln und dann in der Aktionssymbolleiste „Deaktivieren“ auswählen, um sie zu deaktivieren. Wenn eine Regel deaktiviert ist, wird sie zur Laufzeit nicht ausgeführt. Um eine deaktivierte Regel zu aktivieren, können Sie sie auswählen und dann in der Aktionssymbolleiste „Aktivieren“ auswählen. Über die Statusspalte für die Regel wird angezeigt, ob diese aktiviert oder deaktiviert ist.

![disablerrule](assets/disablerule.png)

## Kopieren und Einfügen von Regeln {#copy-paste-rules}

Es ist möglich, Regeln aus einem Feld zu kopieren und in andere, ähnliche Felder einzufügen, um Zeit zu sparen.

Gehen Sie wie folgt vor, um Regeln zu kopieren und einzufügen:

1. Wählen Sie das Formularobjekt aus, von dem Sie eine Regel kopieren möchten, und wählen Sie dann in der Komponentensymbolleiste ![Regel bearbeiten](assets/editrule.png) aus. Die Benutzeroberfläche des Regeleditors wird angezeigt, wobei das Formularobjekt ausgewählt ist und die vorhandenen Regeln angezeigt werden.

   ![copyrule](assets/copyrule.png)

   Weitere Informationen zum Verwalten vorhandener Regeln finden Sie unter [Verwalten von Regeln](#manage-rules).

1. Aktivieren Sie das Kontrollkästchen neben dem Titel der Regel. Es werden weitere Optionen zum Verwalten der Regel angezeigt. Klicken Sie auf **Kopieren**.

   ![copyrule2](assets/copyrule2.png)

1. Wählen Sie ein anderes Formularobjekt aus, in das Sie die Regel einfügen möchten, und wählen Sie dann **Einfügen** aus. Darüber hinaus können Sie die Regel bearbeiten, um Änderungen daran vorzunehmen.

   >[!NOTE]
   >
   >Sie können eine Regel nur dann in ein anderes Formularobjekt einfügen, wenn dieses Formularobjekt das Ereignis der kopierten Regel unterstützt. So unterstützt beispielsweise eine Schaltfläche das Klickereignis. Sie können eine Regel, die ein Klickereignis enthält, in eine Schaltfläche, nicht jedoch in ein Kontrollkästchen einfügen.

1. Wählen Sie **Fertig** aus, um die Regel zu speichern.

## Verschachtelte Ausdrücke {#nestedexpressions}

Mit dem Regeleditor können Sie mehrere UND- und ODER-Operatoren verwenden, um verschachtelte Regeln zu erstellen. Sie können mehrere UND- und ODER-Operatoren in Regeln kombinieren.

Das folgende Beispiel zeigt eine verschachtelte Regel, die dem Benutzer eine Meldung über den Anspruch auf das Sorgerecht für ein Kind anzeigt, wenn die entsprechenden Bedingungen erfüllt sind.

![complexexpression](assets/complexexpression.png)

Sie können Bedingungen innerhalb einer Regel auch mittels Drag-and-Drop ziehen, um sie zu bearbeiten. Wählen Sie den Ziehgriff vor einer Bedingung aus und bewegen Sie den Mauszeiger über den Griff (![handle](assets/handle.png)). Sobald sich der Zeiger wie unten gezeigt in das Handsymbol verwandelt, ziehen Sie die Bedingung per Drag &amp; Drop an eine beliebige Stelle innerhalb der Regel. Die Regelstruktur ändert sich.

![drag-and-drop](assets/drag-and-drop.png)

## Bedingungen für Datumsausdrücke {#dateexpression}

Im Regeleditor können Sie Datenvergleiche verwenden, um Bedingungen zu erstellen.

Nachfolgend ist eine Beispielbedingung dargestellt, die ein statisches Textobjekt anzeigt, wenn die Hypothek für das Haus bereits abgeschlossen ist, was der Benutzer durch Ausfüllen des Datumsfelds angibt.

Wenn das Datum der Hypothek, das vom Benutzer ausgefüllt wurde, in der Vergangenheit liegt, wird im adaptiven Formular ein Hinweis über die Einkommensberechnung angezeigt. Die folgende Regel vergleicht das Datum, das vom Benutzer eingetragen wurde, mit dem aktuellen Datum. Wenn dieses Datum vor dem aktuellen Datum liegt, zeigt das Formular die Textmeldung (mit der Bezeichnung „Einkommen“) an.

![dateexpressioncondition](assets/dateexpressioncondition.png)

Wenn das eingetragene Datum vor dem aktuellen Datum liegt, zeigt das Formular die Textmeldung (Einkommen) an, wie hier dargestellt:

![dateexpressionconditionmet](assets/dateexpressionconditionmet.png)

## Bedingungen für den Vergleich von Zahlen {#number-comparison-conditions}

Im Regeleditor können Sie Bedingungen erstellen, mit denen zwei Zahlen verglichen werden.

Im Folgenden wird eine Beispielbedingung angezeigt, die ein statisches Textobjekt anzeigt, wenn die Anzahl von Monaten, die ein aktueller Benutzer an seiner gegenwärtigen Adresse gewohnt hat, weniger als 36 ist.

![numbercomparisoncondition](assets/numbercomparisoncondition.png)

Wenn der Benutzer angibt, dass er unter seiner derzeitigen Adresse weniger als 36 Monate gewohnt hat, wird im Formular ein Hinweis angezeigt, dass ein zusätzlicher Aufenthaltsnachweis erforderlich ist.

![additionalproofrequent](assets/additionalproofrequested.png)

## Einfluss des Regeleditors auf vorhandene Skripte {#impact-of-rule-editor-on-existing-scripts}

In AEM Forms-Versionen vor AEM 6.1 Forms Feature Pack 1 haben Autorinnen und Autoren sowie Entwicklerinnen und Entwickler von Formularen Ausdrücke auf der Registerkarte „Skripte“ des Dialogfelds „Komponente bearbeiten“ geschrieben, um adaptiven Formularen dynamisches Verhalten hinzuzufügen. Die Registerkarte „Skripte“ ist nun durch den Regeleditor ersetzt worden.

Alle Skripte oder Ausdrücke, die Sie auf der Registerkarte „Skripte“ geschrieben haben, sind im Regeleditor verfügbar. Sie können sie zwar nicht im Visual Editor anzeigen oder bearbeiten, aber wenn Sie Teil der Gruppe der Formular-Hauptbenutzer sind, können Sie Skripte im Code-Editor bearbeiten.

## Beispielregeln {#example}

### Aufrufen des Formulardatenmodelldienstes {#invoke}

Stellen Sie sich einen Webservice `GetInterestRates` vor, der den Darlehensbetrag, die Beschäftigungsdauer und die Kreditwürdigkeit des Antragstellers als Eingabe entgegennimmt und einen Darlehensplan einschließlich EMI-Betrag und Zinssatz zurückgibt. Sie erstellen ein Formulardatenmodell, indem Sie den Web-Service als Datenquelle verwenden. Sie fügen dem Formularmodell Datenmodellobjekte und einen `get`-Service hinzu. Der Service wird auf der Registerkarte „Services“ des Formulardatenmodells angezeigt. Erstellen Sie dann ein adaptives Formular, das Felder aus Datenmodellobjekten enthält, um Benutzereingaben für den Darlehensbetrag, die Darlehenslaufzeit und die Kreditwürdigkeit zu erfassen. Fügen Sie eine Schaltfläche hinzu, die den Webservice auslöst, um Plandetails abzurufen. Die Ausgabe wird in die entsprechenden Felder eingetragen.

Die folgende Regel zeigt, wie Sie die Aktion „Dienst aufrufen“ konfigurieren, um das Beispielszenario durchzuführen.

![example-invoke-services](assets/example-invoke-services.png)

Aufrufen des Formulardatenmodelldienstes mithilfe einer Regel für adaptive Formulare

>[!NOTE]
>
>Wenn die Eingabe vom Typ „Array“ ist, sind die Felder, die Arrays unterstützen, im Dropdown-Abschnitt „Ausgabe“ sichtbar.

### Auslösen mehrerer Aktionen mithilfe einer Wenn-Regel {#triggering-multiple-actions-using-the-when-rule}

Sie möchten in einem Kreditantrag erfassen, ob dieser von einer Bestandskundin oder einem Bestandskunden gestellt wurde. Das Feld für die Kunden-ID soll basierend auf den von der Benutzerin bzw. dem Benutzer angegebenen Informationen angezeigt oder ausgeblendet werden. Darüber hinaus soll der Fokus auf das Feld für die Kunden-ID gelegt werden, wenn es sich um eine Bestandskundin oder einen Bestandskunden handelt. Der Kreditantrag umfasst die folgenden Komponenten:

* Ein Optionsfeld **Sind Sie bereits Geometrixx-Kunde?**, das die Optionen „Ja“ und „Nein“ anbietet. Der Wert für „Ja“ ist **0**, und der Wert „Nein“ ist **1**.

* das Textfeld **Geometrixx-Kunden-ID** zur Angabe der Kunden-ID.

Wenn Sie eine Wenn-Regel für das Optionsfeld schreiben, um dieses Verhalten zu implementieren, wird die Regel wie folgt im visuellen Regeleditor angezeigt.  ![when-rule-example](assets/when-rule-example.png)

Regel im Visual Editor

In der Beispielregel ist die Anweisung im Wenn-Abschnitt die Bedingung, durch die bei Rückgabe von „True“ die im Dann-Abschnitt angegebenen Aktionen ausgeführt werden.

Die Regel wird wie folgt im Code-Editor angezeigt.

![when-rule-example-code](assets/when-rule-example-code.png)

Regel im Code-Editor

### Verwenden einer Funktionsausgabe in einer Regel {#using-a-function-output-in-a-rule}

Ein Bestellformular enthält die folgende Tabelle, in der die Benutzenden ihre Bestellungen eingeben. In dieser Tabelle gilt:

* Die erste Zeile ist wiederholbar, sodass Benutzende mehrere Produkte bestellen und unterschiedliche Mengen angeben können. Ihr Elementname ist `Row1`.
* Der Titel der Zelle in der Spalte „Produktmenge“ der wiederholbaren Zeile lautet „Menge“. Der Elementname für diese Zelle lautet `productquantity`.
* Die zweite Zeile der Tabelle ist nicht wiederholbar, und der Titel der Zelle in der Spalte „Produktmenge“ in dieser Zeile lautet „Menge insgesamt“.

![example-function-table](assets/example-function-table.png)

**A.** Zeile 1 **B.** Menge **C.** Menge insgesamt

Als Nächstes sollen die in der Spalte „Produktmenge“ angegebenen Mengen für alle Produkte addiert und die Summe in der Zelle „Menge insgesamt“ angezeigt werden. Schreiben Sie hierzu wie unten gezeigt eine Regel des Typs „Wert einstellen von“ für die Zelle „Menge insgesamt“.

![example-function-output](assets/example-function-output.png)

Regel im visuellen Editor

Die Regel wird wie folgt im Code-Editor angezeigt.

![example-function-output-code](assets/example-function-output-code.png)

Regel im Code-Editor

### Validieren eines Feldwerts mithilfe eines Ausdrucks {#validating-a-field-value-using-expression}

Sie möchten verhindern, dass in dem Bestellformular aus dem vorigen Abschnitt Benutzer mehr als eine Einheit jedes beliebigen Produkts mit einem Preis über 10.000 bestellen. Um dies zu erreichen, können Sie wie unten gezeigt eine Regel „Validieren“ schreiben.

![Example-validate](assets/example-validate.png)

Regel im visuellen Editor

Die Regel wird wie folgt im Code-Editor angezeigt.

![example-validate-code](assets/example-validate-code.png)

Regel im Code-Editor
