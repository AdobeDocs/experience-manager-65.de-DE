---
title: Regeleditor für adaptive Formulare
description: Mit dem Regeleditor für adaptive Formulare können Sie dynamisches Verhalten hinzufügen und komplexe Logik in Formulare ohne Programmierung oder Skripterstellung erstellen.
topic-tags: develop
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Adaptive Forms
exl-id: c611a1f8-9d94-47f3-bed3-59eef722bf98
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '6940'
ht-degree: 75%

---

# Regeleditor für adaptive Formulare {#adaptive-forms-rule-editor}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung für das [Erstellen neuer adaptiver Formulare](/help/forms/using/create-an-adaptive-form-core-components.md) oder das [Hinzufügen von adaptiven Formularen zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html) |
| AEM 6.5 | Dieser Artikel |

## Übersicht {#overview}

Mit der Regeleditor-Funktion in Adobe Experience Manager Forms können Benutzer und Entwickler von Formularen Regeln für adaptive Formularobjekte schreiben. Diese Regeln definieren Aktionen für Formularobjekte, die durch voreingestellte Bedingungen, Benutzereingaben und Benutzeraktionen im Formular ausgelöst werden. Es trägt dazu bei, das Ausfüllen von Formularen weiter zu optimieren und gewährleistet Genauigkeit und Geschwindigkeit.

Der Regeleditor bietet eine intuitive und vereinfachte Benutzeroberfläche zum Schreiben von Regeln. Der Regeleditor bietet einen visuellen Editor für alle Benutzer. Darüber hinaus bietet der Regeleditor nur für Benutzer mit Formularleistung einen Code-Editor zum Schreiben von Regeln und Skripten.
<!-- Some of the key actions that you can perform on adaptive form objects using rules are:

* Show or hide an object
* Enable or disable an object
* Set a value for an object
* Validate the value of an object
* Execute functions to compute the value of an object
* Invoke a form data model service and perform an operation
* Set property of an object -->

Der Regeleditor ersetzt die Skipterstellungs-Funktionen aus AEM 6.1 Forms und früheren Versionen. Ihre vorhandenen Skripte werden jedoch im neuen Regeleditor beibehalten. Weitere Informationen zum Arbeiten mit vorhandenen Skripten im Regeleditor finden Sie unter [Auswirkung des Regeleditors auf vorhandene Skripte](#impact-of-rule-editor-on-existing-scripts).

Benutzer, die der Gruppe &quot;forms-power-users&quot;hinzugefügt wurden, können neue Skripte erstellen und vorhandene bearbeiten. Benutzer in der Gruppe &quot;forms-users&quot;können die Skripte verwenden, aber keine Skripte erstellen oder bearbeiten.

## Grundlegendes zu Regeln {#understanding-a-rule}

Eine Regel ist eine Kombination aus Aktionen und Bedingungen. Im Regeleditor umfassen Aktionen Aktivitäten wie das Ausblenden, Anzeigen, Aktivieren, Deaktivieren oder Berechnen des Werts eines Objekts in einem Formular. Bedingungen sind boolesche Ausdrücke, die durch Prüfungen und Vorgänge für den Status, den Wert oder die Eigenschaft eines Formularobjekts ausgewertet werden. Aktionen werden basierend auf dem bei der Auswertung einer Bedingung zurückgegebenen Wert (`True` oder `False`) ausgeführt.

Der Regeleditor bietet eine Reihe vordefinierter Regeltypen, z. B. „Wenn“, „Anzeigen“, „Ausblenden“, „Aktivieren“, „Deaktivieren“, „Wert einstellen von“ und „Validieren“, um Ihnen beim Schreiben von Regeln zu helfen. Mit jedem Regeltyp können Sie Bedingungen und Aktionen in einer Regel definieren. In diesem Dokument sind die einzelnen Regeltypen im Detail beschrieben.

Eine Regel folgt normalerweise einem der folgenden Konstrukte:

**Bedingung-Aktion** In diesem Konstrukt definiert die Regel zuerst eine Bedingung und dann die auszulösende Aktion. Dieses Konstrukt ist mit einer if-then-Anweisung in Programmiersprachen vergleichbar.

Im Regeleditor wird das Bedingung-Aktion-Konstrukt durch den Regeltyp **Wenn** durchgesetzt.

**Aktion-Bedingung** In diesem Konstrukt definiert die Regel zuerst eine auszulösende Aktion und dann die auszuwertenden Bedingungen. Eine weitere Variante dieses Konstrukts ist Aktion-Bedingung-alternative Aktion, wobei auch dann eine alternative Aktion angegeben wird, die ausgelöst wird, wenn die Bedingung den Wert „False“ zurückgibt.

Die Regeltypen „Anzeigen“, „Ausblenden“, „Aktivieren“, „Deaktivieren“, „Wert festlegen“ und „Validieren“ im Regeleditor setzen das Aktion-Bedingung-Regelkonstrukt um. Standardmäßig lautet die alternative Aktion für &quot;Anzeigen&quot;Ausblenden und für &quot;Aktivieren&quot;Deaktivieren und umgekehrt. Sie können die standardmäßige alternative Aktion nicht ändern.

>[!NOTE]
>
>Die verfügbaren Regeltypen, einschließlich der Bedingungen und Aktionen, die Sie im Regeleditor definieren, hängen auch vom Typ des Formularobjekts ab, für das Sie eine Regel erstellen. Der Regeleditor zeigt nur gültige Regeltypen und Optionen zum Schreiben von Bedingungs- und Aktionsanweisungen für einen bestimmten Formularobjekttyp an. So werden für ein Bereichsobjekt beispielsweise keine Regeln vom Typ „Validieren“, „Wert festlegen“ oder „Deaktivieren“ angezeigt.

Weitere Informationen über die im Regeleditor verfügbaren Regeltypen finden Sie unter [Verfügbare Regeltypen im Regeleditor](#available-rule-types-in-rule-editor).

### Richtlinien für die Auswahl eines Regelkonstrukts {#guidelines-for-choosing-a-rule-construct}

Für die meisten Anwendungsfälle können Sie ein beliebiges Regelkonstrukt verwenden. Nachfolgend finden Sie jedoch einige Richtlinien für die Wahl des am besten geeigneten Konstrukts für Ihre Zwecke. Weitere Informationen über die verfügbaren Regeln im Regeleditor finden Sie unter [Verfügbare Regeltypen im Regeleditor](#available-rule-types-in-rule-editor).

* Eine typische Faustregel bei der Erstellung einer Regel ist, sie im Kontext des Objekts zu betrachten, für das Sie eine Regel schreiben. Stellen Sie sich vor, Sie möchten das Feld B ein- oder ausblenden, basierend auf dem Wert, den eine Person im Feld A angibt. In diesem Fall werten Sie eine Bedingung für das Feld A aus, und basierend auf dem zurückgegebenen Wert lösen Sie eine Aktion für das Feld B aus.

  Daher gilt: Wenn Sie eine Regel für Feld B (das Objekt, für das eine Bedingung ausgewertet wird), verwenden Sie das Konstrukt „Bedingung-Aktion“ oder den Regeltyp „Wenn“. Für Feld A müssten Sie dementsprechend das Konstrukt „Aktion-Bedingung“ oder den Regeltyp „Anzeigen“ oder „Ausblenden“ verwenden.

* Manchmal müssen Sie mehrere Aktionen ausführen, die auf einer Bedingung basieren. In solchen Fällen empfiehlt es sich, das Konstrukt „Bedingung-Aktion“ zu verwenden. In diesem Konstrukt können Sie eine Bedingung einmal auswerten und mehrere Aktionsanweisungen angeben.

  Um beispielsweise die Felder B, C und D basierend auf einer Bedingung auszublenden, die den von der Person im Feld A angegebenen Wert auswertet, genügt eine Regel mit dem Konstrukt „Bedingung-Aktion“ oder dem Regeltyp „Wenn“ für Feld A, wobei Aktionen für die Sichtbarkeit der Felder B, C und D angegeben werden. Andernfalls benötigen Sie drei separate Regeln für die Felder B, C und D, wobei jede Regel die Bedingung prüft und das jeweilige Feld anzeigt oder ausblendet. In diesem Beispiel ist die Erstellung einer Wenn-Regel für ein Objekt effizienter als die Erstellung von Regeln zum Anzeigen und Ausblenden für drei Objekte.

* Um eine Aktion in Abhängigkeit von mehreren Bedingungen auszulösen, empfiehlt es sich, das Konstrukt „Aktion-Bedingung“ zu verwenden. Um beispielsweise Feld A nach Auswertung der Bedingungen für die Felder B, C und D anzuzeigen oder auszublenden, verwenden Sie Regeln des Typs „Anzeigen“ oder „Ausblenden“ für Feld A.
* Für Regeln, die genau eine Aktion für eine Bedingung enthalten, können Sie sowohl Bedingung-Aktion- als auch Aktion-Bedingung-Konstrukte verwenden.
* Wenn eine Regel eine Bedingung prüft und sofort eine Aktion ausführt, wenn ein Wert in ein Feld eingegeben oder ein Feld verlassen wird, empfiehlt es sich, eine Regel mit dem Konstrukt „Bedingung-Aktion“ oder dem Regeltyp „Wenn“ für das Feld zu schreiben, für das die Bedingung ausgewertet wird.
* Die Bedingung in der Wenn-Regel wird ausgewertet, wenn ein Benutzer den Wert des Objekts ändert, auf das die Wenn-Regel angewendet wird. Wenn die Aktion jedoch Trigger werden soll, wenn sich der Wert serverseitig ändert (z. B. wenn der Wert vorausgefüllt wird), wird empfohlen, eine Wenn-Regel zu schreiben, die die Aktion beim Initialisieren des Felds Trigger.
* Beim Schreiben von Regeln für Dropdown-Elemente, Optionsfelder oder Kontrollkästchenobjekte werden die Optionen oder Werte dieser Formularobjekte im Formular im Regeleditor vorbefüllt.

## Verfügbare Typen von Operatoren und Ereignissen im Regeleditor {#available-operator-types-and-events-in-rule-editor}

Der Regeleditor bietet die folgenden logischen Operatoren und Ereignisse, mit denen Sie Regeln erstellen können.

* **entspricht**
* **ist nicht gleich**
* **Beginnt mit**
* **Endet mit**
* **Enthält**
* **Ist leer**
* **Ist nicht leer**
* **Hat ausgewählt:** Gibt „true“ zurück, wenn der Benutzer eine bestimmte Option für ein Kontrollkästchen, ein Dropdown-Element oder ein Optionsfeld auswählt.
* **Ist initialisiert (Ereignis):** Gibt „true“ zurück, wenn ein Formularobjekt im Browser dargestellt wird.
* **Wird geändert (Ereignis):** Gibt „true“ zurück, wenn der Benutzer den eingegebenen Wert oder die ausgewählte Option für ein Formularobjekt ändert.

## Verfügbare Typen von Regeln im Regeleditor {#available-rule-types-in-rule-editor}

Der Regeleditor bietet eine Reihe vordefinierter Regeltypen, mit denen Sie Regeln schreiben können. Im Folgenden werden die einzelnen Regeltypen detailliert dargestellt. Weitere Informationen zum Erstellen von Regeln im Regeleditor finden Sie unter [Regeln schreiben](#write-rules).

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

Eine Liste hat beispielsweise vier Optionen: Rot, Blau, Grün und Gelb. Beim Erstellen der Regel werden die Optionen (Optionsfelder) automatisch abgerufen und dem Regelerstellenden wie folgt zur Verfügung gestellt:

![multivaluefcdisplayOptions](assets/multivaluefcdisplaysoptions.png)

Beim Schreiben der Wenn-Regel können Sie die Aktion „Wert löschen von“ auslösen. Die Aktion „Wert löschen von“ löscht den Wert des angegebenen Objekts. Mit der Option Wert löschen von als Option in der Wenn-Anweisung können Sie komplexe Bedingungen mit mehreren Feldern erstellen.

![clearvalue](assets/clearvalueof.png)

**Ausblenden**: Blendet das angegebene Objekt aus.

**Anzeigen**: Blendet das angegebene Objekt ein.

**Aktivieren**: Aktiviert das angegebene Objekt.

**Deaktivieren**: Deaktiviert das angegebene Objekt.

**Service aufrufen** Ruft einen Service auf, der in einem Formulardatenmodell konfiguriert ist. Wenn Sie den Vorgang „Service aufrufen“ wählen, wird ein Feld angezeigt. Beim Tippen auf das Feld werden alle Dienste angezeigt, die in allen Formulardatenmodellen auf Ihrer AEM konfiguriert sind. Bei der Auswahl eines Formulardatenmodell-Services erscheinen zusätzliche Felder, in denen Sie Formularobjekte mit Ein- und Ausgabeparametern für den angegebenen Service zuordnen können. Siehe Beispielregel für den Aufruf von Formulardatenmodell-Services.

Zusätzlich zum Formulardatenmodelldienst können Sie eine direkte WSDL-URL zum Aufrufen eines Webdienstes angeben. Ein Formulardatenmodelldienst bietet jedoch viele Vorteile und den empfohlenen Ansatz zum Aufrufen eines Dienstes.

Weitere Informationen zum Konfigurieren von Services im Formulardatenmodell finden Sie unter [Datenintegration für AEM Forms](/help/forms/using/data-integration.md).

**Wert festlegen**: Berechnet den Wert des angegebenen Objekts und legt ihn fest. Als Objektwert können Sie eine Zeichenfolge, den Wert eines anderen Objekts, den mithilfe eines mathematischem Ausdrucks oder einer Funktion berechneten Wert oder den Wert einer Eigenschaft eines Objekts oder den Ausgabewert von einem konfigurierten Formulardatenmodell-Service festlegen. Wenn Sie die Option „Webservice“ wählen, werden alle in allen Formulardatenmodellen konfigurierten Services auf Ihrer AEM-Instanz angezeigt. Bei der Auswahl eines Formulardatenmodell-Service erscheinen zusätzliche Felder, in denen Sie Formularobjekte mit Ein- und Ausgabeparametern für den angegebenen Service zuordnen können.

Weitere Informationen zum Konfigurieren von Services im Formulardatenmodell finden Sie unter [Datenintegration für AEM Forms](/help/forms/using/data-integration.md).

Die **[!UICONTROL Eigenschaft festlegen]** Mit dem Regeltyp können Sie den Wert einer Eigenschaft des angegebenen Objekts basierend auf einer Bedingungsaktion festlegen. Sie können die Eigenschaft auf einen der folgenden Werte festlegen:

* visible (Boolesch)
* dorExclusion (Boolesch)
* chartType (String)
* title (String)
* enabled (Boolesch)
* mandatory (Boolesch)
* validationsDisabled (Boolesch)
* validateExpMessage (String)
* value (Number, String, Date)
* items (List)
* valid (Boolesch)
* errorMessage (String)

Damit können Sie Regeln definieren, um Kontrollkästchen dynamisch zum adaptiven Formular hinzuzufügen. Sie können benutzerdefinierte Funktionen, Formularobjekte oder eine Objekteigenschaft verwenden, um eine Regel zu definieren.

![Eigenschaft festlegen](assets/set_property_rule_new.png)

Um eine Regel basierend auf einer benutzerdefinierten Funktion zu definieren, wählen Sie **Funktionsausgabe** in der Dropdown-Liste aus und ziehen Sie eine benutzerdefinierte Funktion mittels Drag-and-Drop aus der Registerkarte **Funktionen**. Wenn die Bedingungsaktion erfüllt ist, wird die Anzahl der in der benutzerdefinierten Funktion definierten Kontrollkästchen dem adaptiven Formular hinzugefügt.

Um eine auf einem Formularobjekt basierende Regel zu definieren, wählen Sie **Formularobjekt** in der Dropdown-Liste aus und ziehen Sie ein Formularobjekt mittels Drag-and-Drop aus der Registerkarte **Formularobjekte**. Wenn die Bedingungsaktion erfüllt ist, wird die Anzahl der im Formularobjekt definierten Kontrollkästchen dem adaptiven Formular hinzugefügt.

Mit einer auf einer Objekteigenschaft basierenden Regel Eigenschaft festlegen können Sie die Anzahl der Kontrollkästchen in einem adaptiven Formular basierend auf einer anderen Objekteigenschaft hinzufügen, die im adaptiven Formular enthalten ist.

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

Die **[!UICONTROL Wert einstellen von]** Mit dem Regeltyp können Sie den Wert eines Formularobjekts in Abhängigkeit davon festlegen, ob die angegebene Bedingung erfüllt ist oder nicht. Als Wert kann der Wert eines anderen Objekts, ein Literal-String, ein aus einem mathematischen Ausdruck oder einer Funktion abgeleiteter Wert oder der Wert einer Eigenschaft eines anderen Objekts oder die Ausgabe eines Formulardatenmodelldiensts sein. In ähnlicher Weise können Sie auf eine Bedingung bei Komponenten, Zeichenfolgen, Eigenschaften oder Werten prüfen, die von Funktionen oder mathematischen Ausdrücken abgeleitet wurden.

Der Regeltyp Wert einstellen steht nicht für alle Formularobjekte zur Verfügung, z. B. Bereiche und Symbolleistenschaltflächen. Eine standardmäßige Regel vom Typ „Wert festlegen“ hat die folgende Struktur:



Wert von Objekt A festlegen auf:

(Zeichenfolge ABC) ODER
(Objekteigenschaft X von Objekt C) ODER
(Wert aus einer Funktion) ODER
(Wert aus einem mathematischen Ausdruck) ODER
(Ausgabewert von einem Datenmodell-Service oder Webservice);

Wenn (optional):

(Bedingung 1 UND Bedingung 2 UND Bedingung 3) „TRUE“ zurückgibt;



Im folgenden Beispiel wird der Wert im Feld `dependentid` als Eingabe genommen und der Wert des Feldes `Relation` auf die Ausgabe des Arguments `Relation` des Formulardatenmodell-Service `getDependent` festgelegt.

![set-value-web-service](assets/set-value-web-service.png)

Beispiel einer Regel zum Festlegen eines Werts mit dem Formulardatenmodelldienst

>[!NOTE]
>
>Darüber hinaus können Sie mithilfe der Regel Wert einstellen alle Werte in einer Dropdown-Listenkomponente aus der Ausgabe eines Formulardatenmodelldienstes oder eines Webdiensts ausfüllen. Stellen Sie jedoch sicher, dass das von Ihnen ausgewählte Ausgabeargument ein Array-Typ ist. Alle Werte, die in einem Array zurückgegeben werden, stehen in der angegebenen Dropdown-Liste zur Verfügung.

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

Ähnlich wie beim Regeltyp &quot;Aktivieren&quot;kann die **Deaktivieren** -Regeltyp können Sie ein Formularobjekt aktivieren oder deaktivieren, je nachdem, ob eine Bedingung erfüllt ist oder nicht. Der Regeltyp „Deaktivieren“ löst auch die Aktion „Aktivieren“ aus, falls die Bedingung nicht erfüllt ist oder `False` zurückgibt.

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
>Wenn der angegebene Wert nicht der Validierungsregel entspricht, können Sie eine Validierungsmeldung für den Benutzer anzeigen lassen. Sie können die Meldung im Feld **[!UICONTROL Skriptüberprüfungsmeldung]** in den Komponenteneigenschaften in der Seitenleiste angeben.

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

Der Regeleditor bietet eine umfangreiche und dennoch einfache Benutzeroberfläche zum Erstellen und Verwalten von Regeln. Sie können die Benutzeroberfläche des Regeleditors in einem adaptiven Formular im Authoring-Modus starten.

So starten Sie die Benutzeroberfläche des Regeleditors:

1. Öffnen Sie ein adaptives Formular im Authoring-Modus.
1. Wählen Sie das Formularobjekt aus, für das Sie eine Regel schreiben möchten, und wählen Sie in der Komponentensymbolleiste die Option ![edit-rules](assets/edit-rules.png). Die Benutzeroberfläche des Regeleditors wird angezeigt.

   ![create-rules](assets/create-rules.png)

   Alle vorhandenen Regeln für die ausgewählten Formularobjekte werden in dieser Ansicht aufgelistet. Weitere Informationen zum Verwalten vorhandener Regeln finden Sie unter [Verwalten von Regeln](#manage-rules).

1. Auswählen **[!UICONTROL Erstellen]** , um eine neue Regel zu erstellen. Wenn Sie den Regeleditor zum ersten Mal starten, wird standardmäßig der Visual Editor der Regeleditor-Benutzeroberfläche geöffnet.

   ![Benutzeroberfläche des Regeleditors](assets/rule-editor-ui.png)

Nachfolgend werden die einzelnen Komponenten der Benutzeroberfläche des Regeleditors im Detail beschrieben.

### A. Ansicht „Komponente und Regel“ {#a-component-rule-display}

Zeigt den Titel des adaptiven Formularobjekts an, über das Sie den Regeleditor gestartet haben, und den derzeit ausgewählten Regeltyp. Im oben gezeigten Beispiel wurde der Regeleditor über ein adaptives Formularobjekt namens „Salary“ gestartet und der Wenn-Regeltyp ist ausgewählt.

### B. Formularobjekte und Funktionen {#b-form-objects-and-functions-br}

Im linken Bereich der Benutzeroberfläche des Regeleditors stehen zwei Registerkarten zur Verfügung: **[!UICONTROL Formularobjekte]** und **[!UICONTROL Funktionen]**.

Die Registerkarte &quot;Formularobjekte&quot;zeigt eine hierarchische Ansicht aller Objekte im adaptiven Formular an. Angezeigt werden Titel und Typ der Objekte. Wenn Sie eine Regel erstellen, können Sie Formularobjekte in den Regeleditor ziehen und dort ablegen. Wenn Sie beim Erstellen oder Bearbeiten einer Regel ein Objekt oder eine Funktion in einen Platzhalter ziehen, übernimmt dieser Platzhalter automatisch den entsprechenden Wertetyp.

Die Formularobjekte, auf die eine oder mehrere gültige Regeln angewendet wurden, sind mit einem grünen Punkt markiert. Wenn eine der auf ein Formularobjekt angewendeten Regeln ungültig ist, wird das Formularobjekt mit einem gelben Punkt markiert.

Die Registerkarte „Funktionen“ enthält eine Reihe integrierter Funktionen (z. B. „Summe von“, „Minimum von“, „Maximum von“, „Durchschnitt von“, „Anzahl von“ und „Formular validieren“). Sie können diese Funktionen verwenden, um Werte in wiederholbaren Bereichen und Tabellenzeilen zu berechnen und sie beim Erstellen von Regeln in den Aktions- und Bedingungsanweisungen zu verwenden. Sie können jedoch auch [benutzerdefinierte Funktionen](#custom-functions) erstellen.

![Die Registerkarte „Funktionen“](assets/functions.png)

>[!NOTE]
>
>Sie können auf den Registerkarten „Formularobjekte“ und „Funktionen“ eine Textsuche nach den Namen und Titeln von Objekten und Funktionen durchführen.

Im linken Baum der Formularobjekte können Sie die Formularobjekte auswählen, um die Regeln anzuzeigen, die auf die einzelnen Objekte angewendet werden. Sie können nicht nur durch die Regeln der verschiedenen Formularobjekte navigieren, sondern auch Regeln zwischen den Formularobjekten kopieren und einfügen. Weitere Informationen finden Sie unter [Kopieren und Einfügen von Regeln](#copy-paste-rules).

### C. Umschalten zwischen Formularobjekten und Funktionen {#c-form-objects-and-functions-toggle-br}

Durch Tippen auf die Schaltfläche schalten Sie zwischen den Bereichen für Formularobjekte und Funktionen um.

### D. Visueller Regeleditor {#d-visual-rule-editor}

Der visuelle Regeleditor ist im visuellen Editormodus der Benutzeroberfläche des Regeleditors der Bereich, in dem Sie Regeln schreiben. Damit können Sie einen Regeltyp auswählen und dementsprechend Bedingungen und Aktionen definieren. Beim Definieren von Bedingungen und Aktionen in einer Regel können Sie Formularobjekte und Funktionen aus dem Bereich „Formularobjekte und Funktionen“ ziehen und ablegen.

Weitere Informationen zur Verwendung des visuellen Regeleditors finden Sie unter [Regeln schreiben](#write-rules).

### E. Umschalter zwischen Visual Code-Editoren {#e-visual-code-editors-switcher}

Benutzer in der Gruppe forms-power-users können auf den Code-Editor zugreifen. Für andere Benutzer ist der Code-Editor nicht verfügbar. Wenn Sie über die Berechtigungen verfügen, können Sie vom Visual Editor-Modus zum Codeeditormodus des Regeleditors wechseln und umgekehrt mithilfe des Schalters direkt über dem Regeleditor. Wenn Sie den Regeleditor zum ersten Mal starten, wird er im Visual Editor-Modus geöffnet. Sie können Regeln im Visual Editor-Modus schreiben oder in den Code-Editor-Modus wechseln, um ein Regelskript zu schreiben. Beachten Sie jedoch, dass Sie beim Ändern einer Regel oder Schreiben einer Regel im Code-Editor nicht zum Visual Editor für diese Regel wechseln können, es sei denn, Sie löschen den Code-Editor.

AEM Forms verfolgt den Regeleditormodus, den Sie zuletzt zum Erstellen einer Regel verwendet haben. Wenn Sie den Regeleditor das nächste Mal starten, wird er in diesem Modus geöffnet. Sie können jedoch auch einen Standardmodus konfigurieren, um den Regeleditor im angegebenen Modus zu öffnen. Gehen Sie dazu wie folgt vor:

1. Wechseln Sie zur AEM-Web-Konsole unter `https://[host]:[port]/system/console/configMgr`.
1. Zum Bearbeiten klicken Sie auf **[!UICONTROL Konfiguration von adaptiven Formularen und Web-Kanälen für interaktive Kommunikation]**.
1. Wählen Sie **[!UICONTROL Visual Editor]** oder **[!UICONTROL Codeeditor]** aus der Dropdownliste für den **[!UICONTROL Standardmodus für den Regeleditor]**.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

### F. Schaltflächen &quot;Fertig&quot;und &quot;Abbrechen&quot; {#f-done-and-cancel-buttons}

Die Schaltfläche **[!UICONTROL Fertig]** wird verwendet, um eine Regel zu speichern. Sie können eine unvollständige Regel speichern. Unvollständige Elemente sind jedoch ungültig und werden nicht ausgeführt. Gespeicherte Regeln für ein Formularobjekt werden aufgelistet, wenn Sie den Regeleditor das nächste Mal von demselben Formularobjekt aus starten. In dieser Ansicht können Sie vorhandene Regeln verwalten. Weitere Informationen finden Sie unter [Verwalten von Regeln](#manage-rules).

Über die Schaltfläche **[!UICONTROL Abbrechen]** verwerfen Sie alle Änderungen, die Sie an einer Regel vorgenommen haben, und der Regeleditor wird geschlossen.

## Regeln schreiben {#write-rules}

Sie können Regeln mit dem visuellen Regeleditor oder dem Code-Editor schreiben. Wenn Sie den Regeleditor zum ersten Mal starten, wird er im visuellen Editormodus geöffnet. Sie können zum Code-Editormodus wechseln und Regeln schreiben. Beachten Sie jedoch, dass Sie beim Schreiben oder Ändern einer Regel im Code-Editor nur dann zum Visual Editor für diese Regel wechseln können, wenn Sie den Code-Editor löschen. Wenn Sie den Regeleditor das nächste Mal starten, wird er in dem Modus geöffnet, den Sie zuletzt zum Erstellen von Regeln verwendet haben.

Sehen wir uns zunächst an, wie Regeln mit dem Visual Editor geschrieben werden.

### Verwenden des Visual Editor {#using-visual-editor}

Anhand des folgenden Beispielformulars soll das Erstellen von Regeln im visuellen Editor verständlich gemacht werden.

![create-rule-example](assets/create-rule-example.png)

Im Abschnitt für die Kreditvoraussetzungen in diesem Beispielformular für einen Kreditantrag müssen die Antragstellenden ihren Familienstand, ihr Gehalt und, falls verheiratet, das Gehalt der Partnerin bzw. des Partners angeben. Basierend auf den Benutzereingaben berechnet die Regel den Kreditanspruchsbetrag und zeigt ihn im Feld für den Kreditanspruch an. Wenden Sie die folgenden Regeln an, um das Szenario zu implementieren:

* Das Gehaltsfeld der Partnerin bzw. des Partners wird nur angezeigt, wenn als Familienstand „Verheiratet“ angegeben wurde.
* Der Kreditanspruchsbetrag beträgt 50 % des Gesamtgehalts.

Führen Sie die folgenden Schritte aus, um Regeln zu schreiben:

1. Schreiben Sie zuerst die Regel, mit der die Sichtbarkeit des Felds „Gehalt des Partners“ entsprechend der vom Benutzer über das Optionsfeld „Familienstand“ gewählten Option gesteuert wird.

   Öffnen Sie das Kreditantragsformular im Autorenmodus. Wählen Sie die **Familienstand** Komponente und wählen Sie ![edit-rules](assets/edit-rules.png). Wählen Sie als Nächstes **[!UICONTROL Erstellen]** , um den Regeleditor zu starten.

   ![write-rules-visual-editor-1](assets/write-rules-visual-editor-1.png)

   Wenn Sie den Regeleditor starten, ist standardmäßig die Wenn-Regel ausgewählt. Darüber hinaus wird in der Wenn-Anweisung das Formularobjekt (in diesem Fall „Familienstand“), von dem aus Sie den Regeleditor gestartet haben, angegeben.

   Sie können zwar das ausgewählte Objekt nicht bearbeiten oder ändern, es ist jedoch möglich, über die Dropdown-Liste für Regeln einen anderen Regeltyp wählen (siehe unten). Wenn Sie eine Regel für ein anderes Objekt erstellen möchten, wählen Sie Abbrechen , um den Regeleditor zu beenden und ihn erneut über das gewünschte Formularobjekt zu starten.

1. Auswählen **[!UICONTROL Status auswählen]** und wählen Sie **[!UICONTROL ist gleich]**. Das Feld **[!UICONTROL Eine Zeichenfolge eingeben]** wird angezeigt.

   ![write-rules-visual-editor-2](assets/write-rules-visual-editor-2.png)

   In dem Optionsfeld „Familienstand“ werden den Optionen **Verheiratet** und **Ledig** die Werte **0** bzw. **1** zugewiesen. Sie können die zugewiesenen Werte auf der Registerkarte „Titel“ des Dialogfelds zum Bearbeiten des Optionsfelds überprüfen, wie unten gezeigt.

   ![Optionsfeldwerte im Regeleditor](assets/radio-button-values.png)

1. Geben Sie in der Regel im Feld **Eine Zeichenfolge eingeben** den Wert **0** an.

   ![write-rules-visual-editor-4](assets/write-rules-visual-editor-4.png)

   Sie haben die Bedingung als `When Marital Status is equal to Married` definiert. Definieren Sie anschließend die Aktion, die ausgeführt werden soll, wenn diese Bedingung erfüllt (True) ist.

1. Wählen Sie für die Dann-Anweisung die Option **[!UICONTROL Anzeigen]** aus der Dropdown-Liste **[!UICONTROL Aktion auswählen]**.

   ![write-rules-visual-editor-5](assets/write-rules-visual-editor-5.png)

1. Ziehen Sie das Feld **Gehalt des Partners** aus der Registerkarte „Formularobjekte“ in das Feld **Legen Sie das Objekt ab oder wählen Sie hier aus**. Alternativ können Sie die **Objekt ablegen oder hier auswählen** und wählen Sie die **Gehalt des Partners** aus dem Popup-Menü, in dem alle Formularobjekte im Formular aufgelistet werden.

   ![write-rules-visual-editor-6](assets/write-rules-visual-editor-6.png)

   Die Regel wird im Regeleditor wie folgt angezeigt.

   ![write-rules-visual-editor-7](assets/write-rules-visual-editor-7.png)

   Auswählen **Fertig** , um die Regel zu speichern.

1. Wiederholen Sie die Schritte 1 bis 5, um eine weitere Regel zu definieren, mit der das Feld für das Gehalt der Partnerin bzw. des Partners ausgeblendet wird, wenn als Familienstand „Ledig“ angegeben wird. Die Regel wird im Regeleditor wie folgt angezeigt.

   ![write-rules-visual-editor-8](assets/write-rules-visual-editor-8.png)

   >[!NOTE]
   >
   >Alternativ zu diesem Verfahren können Sie dieses Verhalten auch implementieren, indem Sie für das Feld „Gehalt des Partners“ lediglich eine Regel vom Typ „Anzeigen“ anstelle zweier Wenn-Regeln für das Feld „Familienstand“ erstellen.

   ![write-rules-visual-editor-9](assets/write-rules-visual-editor-9.png)

1. Als Nächstes erstellen Sie eine Regel für die Berechnung des Kreditanspruchsbetrags (50 % des Gesamtgehalts) und zur Anzeige des Betrags im Feld für den Kreditanspruch. Erstellen Sie dazu **Wert einstellen von** Regeln für das Feld &quot;Kreditanspruch&quot;.

   Wählen Sie im Authoring-Modus die **[!UICONTROL Kreditanspruch]** Feld und wählen Sie ![edit-rules](assets/edit-rules.png). Wählen Sie als Nächstes **[!UICONTROL Erstellen]** , um den Regeleditor zu starten.

1. Wählen Sie in der Dropdown-Liste „Regeln“ die Regel **[!UICONTROL Wert festlegen]** aus.

   ![write-rules-visual-editor-10](assets/write-rules-visual-editor-10.png)

1. Auswählen **[!UICONTROL Option auswählen]** und wählen **[!UICONTROL Mathematischer Ausdruck]**. Ein Feld, in dem Sie mathematische Ausdrücke schreiben können, wird geöffnet.

   ![write-rules-visual-editor-11](assets/write-rules-visual-editor-11.png)

1. Im Ausdrucksfeld:

   * Wählen Sie das Feld **Gehalt** auf der Registerkarte „Formularobjekt“ aus oder ziehen Sie es per Drag-and-Drop in das erste Feld **Objekt hier einfügen oder auswählen**.

   * Wählen Sie **Plus** aus dem Feld **Operator wählen**.

   * Wählen Sie das Feld **Gehalt des Partners** auf der Registerkarte „Formularobjekt“ aus oder ziehen Sie es in das zweite Feld **Legen Sie das Objekt ab oder wählen Sie hier aus** und legen Sie es dort ab.

   ![write-rules-visual-editor-12](assets/write-rules-visual-editor-12.png)

1. Wählen Sie anschließend im markierten Bereich um das Ausdrucksfeld aus und wählen Sie **Ausdruck erweitern**.

   ![write-rules-visual-editor-13](assets/write-rules-visual-editor-13.png)

   Wählen Sie im Feld für den erweiterten Ausdruck **geteilt durch** aus dem Feld **Operator wählen** und **Zahl** aus dem Feld **Option wählen**. Geben Sie **2** in das Zahlenfeld ein.

   ![write-rules-visual-editor-14](assets/write-rules-visual-editor-14.png)

   >[!NOTE]
   >
   >Sie können komplexe Ausdrücke erstellen, indem Sie Komponenten, Funktionen, mathematische Ausdrücke und Eigenschaftswerte aus dem Feld „Option auswählen“ verwenden.

   Als Nächstes erstellen Sie eine Bedingung. Wenn diese „true“ zurückgibt, wird der Ausdruck ausgeführt.

1. Auswählen **Bedingung hinzufügen** , um eine Wenn-Anweisung hinzuzufügen.

   ![write-rules-visual-editor-15](assets/write-rules-visual-editor-15.png)

   Geben Sie in der Wenn-Anweisung Folgendes ein:

   * Wählen Sie auf der Registerkarte „Formularobjekt“ das Feld **Familienstand** im ersten Feld **Objekt hier einfügen oder auswählen**.

   * Wählen Sie i **ist gleich** aus dem **Operator auswählen** -Feld.

   * Wählen Sie in dem anderen Feld **Legen Sie das Objekt ab oder wählen Sie hier aus** den Eintrag „String“ (Zeichenfolge) aus und geben Sie **Verheiratet** in das Feld **Geben Sie eine Zeichenfolge ein** ein.

   Die Regel wird schließlich wie folgt im Regeleditor angezeigt.  ![write-rules-visual-editor-16](assets/write-rules-visual-editor-16.png)

   Auswählen **Fertig** , um die Regel zu speichern.

1. Folgen Sie wiederum Schritt 7 bis 12, um eine andere Regel zu definieren, mit deren Hilfe der Kreditanspruch berechnet wird, sofern der Familienstand „Ledig“ ist. Die Regel wird im Regeleditor wie folgt angezeigt.

   ![write-rules-visual-editor-17](assets/write-rules-visual-editor-17.png)

>[!NOTE]
>
>Alternativ können Sie die Regel „Wert festlegen“ verwenden, um die Kreditanspruchsberechtigung in der Wenn-Regel zu berechnen, die Sie erstellt haben, um das Feld für das Gehalt der Partnerin bzw. des Partners ein-/auszublenden. Die resultierende kombinierte Regel (für den Familienstand „Ledig“) wird wie folgt im Regeleditor angezeigt.
>
>Auf ähnliche Weise können Sie eine kombinierte Regel erstellen, die die Sichtbarkeit des Felds für das Gehalt der Partnerin bzw. des Partners steuert und den Kreditanspruch für den Familienstand „Verheiratet“ berechnet.

![write-rules-visual-editor-18](assets/write-rules-visual-editor-18.png)

### Verwenden des Code-Editors {#using-code-editor}

Benutzer, die zur Gruppe der Formular-Power-User hinzugefügt wurden, können den Code-Editor verwenden. Der Regeleditor generiert automatisch den JavaScript-Code für alle Regeln, die Sie mit dem Visual Editor erstellen. Sie können vom Visual Editor zum Code-Editor wechseln, um den generierten Code anzuzeigen. Wenn Sie jedoch den Regel-Code im Code-Editor ändern, können Sie nicht zum Visual Editor zurückkehren. Wenn Sie Regeln lieber im Code-Editor als im Visual Editor schreiben möchten, können Sie Regeln im Code-Editor neu schreiben. Der Umschalter für Visual Code-Editoren hilft Ihnen beim Umschalten zwischen den beiden Modi.

Das im Code-Editor verwendete JavaScript ist die Ausdruckssprache für adaptive Formulare. Alle Ausdrücke sind gültige JavaScript-Ausdrücke und verwenden Skriptmodell-APIs für adaptive Formulare. Diese Ausdrücke geben Werte bestimmter Typen zurück. Eine vollständige Liste der Klassen, Ereignisse, Objekte und öffentlichen APIs für adaptive Formulare finden Sie unter [API-Referenz der JavaScript-Bibliothek für adaptive Formulare](https://helpx.adobe.com/de/experience-manager/6-5/forms/javascript-api/index.html).

Weitere Informationen zu Richtlinien zum Schreiben von Regeln im Code-Editor finden Sie unter [Adaptive Formularausdrücke](/help/forms/using/adaptive-form-expressions.md).

Beim Schreiben von JavaScript-Code im Regeleditor helfen Ihnen die folgenden visuellen Hinweise bei der Struktur und Syntax:

* Syntaxhervorhebung
* Automatischer Einzug
* Hinweise und Vorschläge für Formularobjekte, Funktionen und deren Eigenschaften
* Automatisches Ausfüllen der Namen von Formularkomponenten und gängigen JavaScript-Funktionen

![javascriptruleeditor](assets/javascriptruleeditor.png)

#### Benutzerdefinierte Funktionen im Regeleditor {#custom-functions}

Zusätzlich zu den vorkonfigurierten Funktionen wie beispielsweise *Summe von*, die unter „Funktionenausgabe“ aufgeführt sind, können Sie auch benutzerdefinierte Funktionen erstellen, die Sie häufig benötigen. Stellen Sie sicher, dass für die Funktion, die Sie schreiben, ein `jsdoc` vorhanden ist.

Dieses dazugehörige `jsdoc` ist aus den folgenden Gründen erforderlich:

* Wenn Sie eine benutzerdefinierte Konfiguration und Beschreibung benötigen.
* Da Funktionen in `JavaScript,` auf unterschiedliche Weise deklariert werden können und Sie mithilfe der Kommentare den Überblick über die Funktionen behalten.

Weitere Informationen finden Sie unter [usejsdoc.org](https://jsdoc.app/).

Unterstützte `jsdoc`-Tags:

* **Private** (Privat)
Syntax: `@private`
Eine private Funktion ist nicht als benutzerdefinierte Funktion enthalten.

* **Name**
Syntax: `@name funcName <Function Name>`
Alternativ dazu `,` kann `@function funcName <Function Name>` **oder** `@func` `funcName <Function Name>` verwenden werden.
  `funcName` ist der Name der Funktion (Leerzeichen sind nicht zulässig).
  `<Function Name>` ist der Anzeigename der Funktion.

* **Member** (Mitglied)
Syntax: `@memberof namespace`
Bindet einen Namespace an die Funktion.

* **Parameter**
Syntax: `@param {type} name <Parameter Description>`
Alternativ dazu kann `@argument` `{type} name <Parameter Description>` **oder** `@arg` `{type}` `name <Parameter Description>` verwenden werden.
Zeigt die von der Funktion verwendeten Parameter an. In einer Funktion können mehrere Parameter-Tags vorhanden sein (je ein Tag für jeden Parameter in der Reihenfolge ihres Auftretens).
  `{type}` gibt den Parametertyp an. Zulässige Parametertypen sind:

   1. String (Zeichenfolge)
   1. Number (Zahl)
   1. Boolean (Boolesch)
   1. Scope (Umfang)

  Der Umfang wird für die Verweise auf Felder eines adaptiven Formulars verwendet. Wenn ein Formular verzögertes Laden (Lazy Loading) verwendet, können Sie `scope` verwenden, um auf dessen Felder zuzugreifen. Sie können auf Felder zugreifen, wenn die Felder geladen wurden oder wenn die Felder als „global“ gekennzeichnet sind.

  Alle anderen Parametertypen fallen in eine der oben genannten Kategorien. „None“ (Keiner) wird nicht unterstützt. Achten Sie darauf, einen der oben genannten Typen zu wählen. Bei Typen wird nicht zwischen Groß- und Kleinschreibung unterschieden. Leerzeichen sind im Parameter `name` unzulässig. `<Parameter Descrption>` `<parameter>  can have multiple words. </parameter>`

* **Return Type** (Rückgabetyp)
Syntax: `@return {type}`
Alternativ können Sie `@returns {type}` benutzen.
Fügt Informationen über die Funktion hinzu (z. B. ihren Zweck).
Die Zeichenfolge „{type}“ gibt den Rückgabetyp der Funktion an. Zulässige Rückgabetypen sind:

   1. String (Zeichenfolge)
   1. Number (Zahl)
   1. Boolean (Boolesch)

  Alle anderen Rückgabetypen fallen in eine der oben genannten Kategorien. „None“ (Keiner) wird nicht unterstützt. Achten Sie darauf, einen der oben genannten Typen zu wählen. Bei Rückgabetypen wird nicht zwischen Groß- und Kleinschreibung unterschieden.

* **Diese**
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
>Kommentare vor benutzerdefinierten Funktionen werden für die Zusammenfassung verwendet. Die Zusammenfassung kann sich über mehrere Zeilen bis zum nächsten Tag erstrecken. Beschränken Sie ihre Länge auf eine einzelne Zeile, wenn Sie eine knappe Beschreibung im Regel-Builder erhalten möchten.

**Hinzufügen einer benutzerdefinierten Funktion**

Angenommen, Sie möchten eine benutzerdefinierte Funktion zur Berechnung der Fläche eines Quadrats hinzufügen. Die Seitenlänge ist der von der Benutzerin bzw. vom Benutzer eingegebene Wert für die benutzerdefinierte Funktion. Dieser Wert muss in ein numerisches Feld im Formular eingegeben werden. Die berechnete Ausgabe wird in einem anderen numerischen Feld im Formular angezeigt. Um eine benutzerdefinierte Funktion hinzuzufügen, müssen Sie zunächst eine Client-Bibliothek erstellen und sie dann zum CRX-Repository hinzufügen.

Führen Sie die folgenden Schritte aus, um eine Client-Bibliothek zu erstellen und sie zum CRX-Repository hinzuzufügen.

1. Erstellen Sie eine Client-Bibliothek. Weitere Informationen finden Sie unter [Verwenden Client-seitiger Bibliotheken](/help/sites-developing/clientlibs.md).
1. Fügen Sie in CRXDE die Eigenschaft `categories` mit dem Wert `customfunction` (vom Typ „String“ (Zeichenfolge)) zum Ordner `clientlib` hinzu.

   >[!NOTE]
   >
   >`customfunction` ist eine Beispielkategorie. Sie können einen beliebigen Namen für die Kategorie wählen, die Sie im Ordner `clientlib`erstellen.

Nachdem Sie die Client-Bibliothek im CRX-Repository hinzugefügt haben, verwenden Sie sie in Ihrem adaptiven Formular. Sie ermöglicht die Verwendung der benutzerdefinierten Funktion als Regel im Formular. Führen Sie die folgenden Schritte durch, um die Client-Bibliothek dem adaptiven Formular hinzuzufügen:

1. Öffnen Sie das Formular im Bearbeitungsmodus.
Um ein Formular im Bearbeitungsmodus zu öffnen, wählen Sie ein Formular aus und wählen Sie **Öffnen**.
1. Wählen Sie im Bearbeitungsmodus eine Komponente aus und wählen Sie dann ![Feldebene](assets/field-level.png) > **Container für adaptive Formulare** und wählen Sie ![cmppr](assets/cmppr.png).
1. Fügen Sie in der Seitenleiste unter „Name der Client-Bibliothek“ Ihre Client-Bibliothek hinzu. (In diesem Beispiel wäre das `customfunction`.)

   ![Hinzufügen der benutzerdefinierten Funktion zur Client-Bibliothek](assets/clientlib.png)

1. Wählen Sie das numerische Eingabefeld aus und wählen Sie ![edit-rules](assets/edit-rules.png) , um den Regeleditor zu öffnen.
1. Auswählen **Regel erstellen**. Erstellen Sie mithilfe der unten gezeigten Optionen eine Regel zum Speichern des Quadratwerts der Eingabe im Ausgabefeld des Formulars.
   [![Verwenden benutzerdefinierter Funktionen zum Erstellen einer Regel](assets/add_custom_rule_new.png)](assets/add-custom-rule.png)Auswählen **Fertig**. Ihre benutzerdefinierte Funktion wird hinzugefügt.

#### Unterstützte Typen von Funktionsdeklarationen {#function-declaration-supported-types}

**Funktionsanweisung**

```javascript
function area(len) {
    return len*len;
}
```

Diese Funktion wird ohne `jsdoc`-Kommentare eingefügt.

**Funktionsausdruck**

```javascript
var area;
//Some codes later
/** */
area = function(len) {
    return len*len;
};
```

**Funktionsausdruck und -anweisung**

```javascript
var b={};
/** */
b.area = function(len) {
    return len*len;
}
```

**Funktionsdeklaration als Variable**

```javascript
/** */
var x1,
    area = function(len) {
        return len*len;
    },
    x2 =5, x3 =true;
```

Einschränkung: Die benutzerdefinierte Funktion wählt nur die erste Funktionsdeklaration aus der Variablenliste aus, wenn sie zusammen vorhanden sind. Sie können den Funktionsausdruck für jede deklarierte Funktion verwenden.

**Funktionsdeklaration als Objekt**

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
>Stellen Sie sicher, dass Sie `jsdoc` für jede benutzerdefinierte Funktion verwenden. Obwohl `jsdoc`-Kommentare empfohlen werden, sollten Sie einen leeren `jsdoc`-Kommentar einfügen, um eine Funktion als benutzerdefinierte Funktion zu kennzeichnen. Dies ermöglicht eine standardmäßige Behandlung Ihrer benutzerdefinierten Funktion.

## Verwalten von Regeln {#manage-rules}

Alle vorhandenen Regeln für ein Formularobjekt werden aufgelistet, wenn Sie das Objekt auswählen und ![edit-rules1](assets/edit-rules1.png). Sie können den Titel und eine Vorschau der Regelzusammenfassung anzeigen. Darüber hinaus können Sie über die Benutzeroberfläche die vollständige Regelzusammenfassung erweitern und anzeigen, die Reihenfolge der Regeln ändern, Regeln bearbeiten und Regeln löschen.

![list-rules](assets/list-rules.png)

Sie können die folgenden Aktionen für Regeln ausführen:

* **Anzeigen/Reduzieren**: Die Inhaltsspalte in der Regelliste zeigt den Regelinhalt an. Wenn der gesamte Regelinhalt nicht in der Standardansicht sichtbar ist, wählen Sie ![expand-rule-content](assets/expand-rule-content.png) um sie zu erweitern.

* **Neu anordnen**: Jede neue Regel, die Sie erstellen, wird am unteren Rand der Regelliste gestapelt. Die Regeln werden von oben nach unten ausgeführt. Die Regel oben wird zuerst ausgeführt, gefolgt von anderen Regeln desselben Typs. Wenn beispielsweise eine Wenn-, Anzeigen-, Aktivieren- und eine weitere Wenn-Regel an den ersten vier Positionen der Liste stehen, werden zuerst die zuoberst stehende Wenn-Regel und dann die Wenn-Regel an der vierten Position ausgeführt. Danach werden die Regeln „Anzeigen“ und „Aktivieren“ ausgeführt.
Sie können die Position einer Regel in der Reihenfolge ändern, indem Sie auf ![sort-rules](assets/sort-rules.png) für die Regel tippen oder die Regel an die gewünschte Stelle in der Liste ziehen und dort ablegen.

* **Bearbeiten**: Zum Bearbeiten einer Regel aktivieren Sie das Kontrollkästchen neben ihrem Titel. Zusätzliche Optionen zum Bearbeiten und Löschen der Regel werden angezeigt. Auswählen **Bearbeiten** , um die ausgewählte Regel im Regeleditor im Visual Editor- oder Codeeditormodus zu öffnen. Dies hängt vom Modus ab, der zum Erstellen der Regel verwendet wird.

* **Löschen**: Um eine Regel zu löschen, wählen Sie sie aus und klicken Sie auf **Löschen**.

* **Aktivieren/Deaktivieren**: Möglicherweise müssen Sie die Verwendung einer Regel vorübergehend aussetzen. Sie können eine oder mehrere Regeln auswählen und in der Aktionssymbolleiste die Option Deaktivieren auswählen, um sie zu deaktivieren. Wenn eine Regel deaktiviert ist, wird sie zur Laufzeit nicht ausgeführt. Um eine Regel zu aktivieren, die deaktiviert ist, können Sie sie auswählen und in der Aktionssymbolleiste die Option Aktivieren auswählen. Die Statusspalte der Regel zeigt an, ob die Regel aktiviert oder deaktiviert ist.

![disablerrule](assets/disablerule.png)

## Kopieren und Einfügen von Regeln {#copy-paste-rules}

Sie können eine Regel aus einem Feld kopieren und in andere ähnliche Felder einfügen, um Zeit zu sparen.

Gehen Sie wie folgt vor, um Regeln zu kopieren und einzufügen:

1. Wählen Sie das Formularobjekt aus, aus dem Sie eine Regel kopieren möchten, und wählen Sie in der Komponentensymbolleiste ![editrule](assets/editrule.png). Die Benutzeroberfläche des Regeleditors wird angezeigt, wobei das Formularobjekt ausgewählt ist und die vorhandenen Regeln angezeigt werden.

   ![copyrule](assets/copyrule.png)

   Weitere Informationen zum Verwalten vorhandener Regeln finden Sie unter [Verwalten von Regeln](#manage-rules).

1. Aktivieren Sie das Kontrollkästchen neben dem Regeltitel. Es werden zusätzliche Optionen zur Verwaltung der Regel angezeigt. Klicken Sie auf **Kopieren**.

   ![copyrule2](assets/copyrule2.png)

1. Wählen Sie ein anderes Formularobjekt aus, in das Sie die Regel einfügen möchten, und wählen Sie **Einfügen**. Außerdem können Sie die Regel bearbeiten, um Änderungen daran vorzunehmen.

   >[!NOTE]
   >
   >Sie können eine Regel nur dann in ein anderes Formularobjekt einfügen, wenn dieses Formularobjekt das Ereignis der kopierten Regel unterstützt. So unterstützt beispielsweise eine Schaltfläche das Klick-Ereignis. Sie können eine Regel mit einem Klick-Ereignis in eine Schaltfläche, nicht aber in ein Kontrollkästchen einfügen.

1. Auswählen **Fertig** , um die Regel zu speichern.

## Verschachtelte Ausdrücke {#nestedexpressions}

Mit dem Regeleditor können Sie mehrere UND- und ODER-Operatoren verwenden, um verschachtelte Regeln zu erstellen. Sie können mehrere UND- und ODER-Operatoren in Regeln kombinieren.

Das folgende Beispiel zeigt eine verschachtelte Regel, die dem Benutzer eine Meldung über den Anspruch auf das Sorgerecht für ein Kind anzeigt, wenn die entsprechenden Bedingungen erfüllt sind.

![complexexpression](assets/complexexpression.png)

Sie können Bedingungen innerhalb einer Regel auch mittels Drag-and-Drop ziehen, um sie zu bearbeiten. Wählen Sie den Ziehpunkt aus und bewegen Sie den Mauszeiger über ( ![handle](assets/handle.png)) vor einer Bedingung. Sobald sich der Zeiger wie unten gezeigt in das Handsymbol verwandelt, ziehen Sie die Bedingung per Drag-and-Drop an eine beliebige Stelle innerhalb der Regel. Die Regelstruktur ändert sich.

![drag-and-drop](assets/drag-and-drop.png)

## Bedingungen für Datumsausdrücke {#dateexpression}

Mit dem Regeleditor können Sie Datumsvergleiche verwenden, um Bedingungen zu erstellen.

Nachfolgend ist eine Beispielbedingung dargestellt, die ein statisches Textobjekt anzeigt, wenn die Hypothek für das Haus bereits abgeschlossen ist, was der Benutzer durch Ausfüllen des Datumsfelds angibt.

Wenn das Datum der Hypothek, das vom Benutzer ausgefüllt wurde, in der Vergangenheit liegt, wird im adaptiven Formular ein Hinweis über die Einkommensberechnung angezeigt. Die folgende Regel vergleicht das Datum, das vom Benutzer eingetragen wurde, mit dem aktuellen Datum. Wenn dieses Datum vor dem aktuellen Datum liegt, zeigt das Formular die Textmeldung (mit der Bezeichnung „Einkommen“) an.

![dateexpressioncondition](assets/dateexpressioncondition.png)

Wenn das eingetragene Datum vor dem aktuellen Datum liegt, zeigt das Formular die Textmeldung (Einkommen) an, wie hier dargestellt:

![dateexpressionconditionmet](assets/dateexpressionconditionmet.png)

## Bedingungen für den Vergleich von Zahlen {#number-comparison-conditions}

Mit dem Regeleditor können Sie Bedingungen erstellen, die zwei Zahlen vergleichen.

Im Folgenden wird eine Beispielbedingung angezeigt, die ein statisches Textobjekt anzeigt, wenn die Anzahl von Monaten, die ein aktueller Benutzer an seiner gegenwärtigen Adresse gewohnt hat, weniger als 36 ist.

![numbercomparisoncondition](assets/numbercomparisoncondition.png)

Wenn der Benutzer angibt, dass er unter seiner derzeitigen Adresse weniger als 36 Monate gewohnt hat, wird im Formular ein Hinweis angezeigt, dass ein zusätzlicher Aufenthaltsnachweis erforderlich ist.

![additionalproofrequent](assets/additionalproofrequested.png)

## Auswirkung des Regeleditors auf vorhandene Skripte {#impact-of-rule-editor-on-existing-scripts}

In AEM Forms-Versionen vor AEM 6.1 Forms Feature Pack 1 schreiben Formularverfasser und -entwickler Ausdrücke auf der Registerkarte &quot;Skripte&quot;des Dialogfelds &quot;Komponente bearbeiten&quot;, um adaptiven Formularen dynamisches Verhalten hinzuzufügen. Die Registerkarte &quot;Skripte&quot;wird jetzt durch den Regeleditor ersetzt.

Alle Skripte oder Ausdrücke, die Sie auf der Registerkarte &quot;Skripte&quot;geschrieben haben, sind im Regeleditor verfügbar. Sie können sie zwar nicht im Visual Editor anzeigen oder bearbeiten, aber wenn Sie Teil der Gruppe der Formular-Hauptbenutzer sind, können Sie Skripte im Code-Editor bearbeiten.

## Beispielregeln {#example}

### Formulardatenmodelldienst aufrufen {#invoke}

Stellen Sie sich einen Webservice `GetInterestRates` vor, der den Darlehensbetrag, die Beschäftigungsdauer und die Kreditwürdigkeit des Antragstellers als Eingabe entgegennimmt und einen Darlehensplan einschließlich EMI-Betrag und Zinssatz zurückgibt. Sie erstellen ein Formulardatenmodell, indem Sie den Web-Service als Datenquelle verwenden. Sie fügen dem Formularmodell Datenmodellobjekte und einen `get`-Service hinzu. Der Service wird auf der Registerkarte „Services“ des Formulardatenmodells angezeigt. Erstellen Sie dann ein adaptives Formular, das Felder aus Datenmodellobjekten enthält, um Benutzereingaben für Darlehensbetrag, Laufzeit und Kreditwürdigkeit zu erfassen. Fügen Sie eine Schaltfläche hinzu, die den Webservice auslöst, um Plandetails abzurufen. Die Ausgabe wird in den entsprechenden Feldern befüllt.

Die folgende Regel zeigt, wie Sie die Aktion &quot;Dienst aufrufen&quot;konfigurieren, um das Beispielszenario auszuführen.

![example-invoke-services](assets/example-invoke-services.png)

Formulardatenmodelldienst mithilfe der adaptiven Formularregel aufrufen

>[!NOTE]
>
>Wenn die Eingabe vom Typ Array ist, sind die Felder, die Arrays unterstützen, im Dropdown-Abschnitt Ausgabe sichtbar.

### Auslösen mehrerer Aktionen mithilfe einer Wenn-Regel {#triggering-multiple-actions-using-the-when-rule}

In einem Kreditantragsformular möchten Sie erfassen, ob der Kreditantrag von Bestandskundinnen bzw. -kunden kommt oder nicht. Das Feld für die Kunden-ID soll basierend auf den von der Benutzerin bzw. vom Benutzer angegebenen Informationen angezeigt oder ausgeblendet werden. Darüber hinaus soll der Fokus auf das Kunden-ID-Feld gelegt werden, wenn es sich um Bestandskundinnen bzw. -kunden handelt. Das Antragsformular für ein Darlehen umfasst die folgenden Komponenten:

* Ein Optionsfeld **Sind Sie bereits Geometrixx-Kunde?**, das die Optionen „Ja“ und „Nein“ anbietet. Der Wert für „Ja“ ist **0**, und der Wert „Nein“ ist **1**.

* Das Textfeld **Geometrixx-Kunden-ID** zur Angabe der Kunden-ID.

Wenn Sie eine Wenn-Regel für das Optionsfeld schreiben, um dieses Verhalten zu implementieren, wird die Regel wie folgt im visuellen Regeleditor angezeigt.  ![when-rule-example](assets/when-rule-example.png)

Regel im Visual Editor

In der Beispielregel ist die Anweisung im Abschnitt „Wenn“ die Bedingung. Wenn diese „True“ zurückgibt, werden die im Abschnitt „Dann“ angegebenen Aktionen ausgeführt.

Die Regel wird wie folgt im Code-Editor angezeigt.

![when-rule-example-code](assets/when-rule-example-code.png)

Regel im Code-Editor

### Verwenden einer Funktionsausgabe in einer Regel {#using-a-function-output-in-a-rule}

In einem Bestellformular haben Sie die folgende Tabelle, in der Benutzer ihre Bestellungen ausfüllen. In dieser Tabelle gilt:

* Die erste Zeile ist wiederholbar, sodass Benutzende mehrere Produkte bestellen und unterschiedliche Mengen angeben können. Ihr Elementname ist `Row1`.
* Der Titel der Zelle in der Spalte „Produktmenge“ der wiederholbaren Zeile lautet „Menge“. Der Elementname für diese Zelle lautet `productquantity`.
* Die zweite Zeile der Tabelle ist nicht wiederholbar, und der Titel der Zelle in der Spalte „Produktmenge“ in dieser Zeile lautet „Menge insgesamt“.

![example-function-table](assets/example-function-table.png)

**A.** Zeile 1 **B.** Menge **C.** Menge insgesamt

Als Nächstes sollen die in der Spalte „Produktmenge“ angegebenen Mengen für alle Produkte addiert und die Summe in der Zelle „Menge insgesamt“ angezeigt werden. Sie können dies erreichen, indem Sie wie unten gezeigt eine Regel zum Festlegen eines Werts für die Zelle &quot;Menge insgesamt&quot;schreiben.

![example-function-output](assets/example-function-output.png)

Regel im visuellen Editor

Die Regel wird wie folgt im Code-Editor angezeigt.

![example-function-output-code](assets/example-function-output-code.png)

Regel im Code-Editor

### Validieren eines Feldwerts mithilfe eines Ausdrucks {#validating-a-field-value-using-expression}

Sie möchten verhindern, dass in dem Bestellformular aus dem vorigen Abschnitt Benutzer mehr als eine Einheit jedes beliebigen Produkts mit einem Preis über 10.000 bestellen. Dazu können Sie wie unten gezeigt eine Validierungsregel schreiben.

![Example-validate](assets/example-validate.png)

Regel im visuellen Editor

Die Regel wird wie folgt im Code-Editor angezeigt.

![example-validate-code](assets/example-validate-code.png)

Regel im Code-Editor
