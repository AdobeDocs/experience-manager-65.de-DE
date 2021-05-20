---
title: Regeleditor für adaptive Formulare
seo-title: Regeleditor für adaptive Formulare
description: Der Regeleditor für adaptive Formulare ermöglicht es Ihnen, ohne Programmierung oder Scripting dynamisches Verhalten und komplexe Logik in Ihre Formulare zu integrieren.
seo-description: Der Regeleditor für adaptive Formulare ermöglicht es Ihnen, ohne Programmierung oder Scripting dynamisches Verhalten und komplexe Logik in Ihre Formulare zu integrieren.
uuid: c1b3d6e4-6f36-4352-ab57-9850d718e47c
topic-tags: develop
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 1b905e66-dc05-4f14-8025-62a78feef12a
docset: aem65
feature: Adaptive Formulare
exl-id: c611a1f8-9d94-47f3-bed3-59eef722bf98
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '6820'
ht-degree: 76%

---

# Regeleditor für adaptive Formulare{#adaptive-forms-rule-editor}

## Überblick {#overview}

Die Regeleditorfunktion in Adobe Experience Manager Forms ermöglicht es Geschäftsbenutzern und Entwicklern, Regeln für adaptive Formularobjekte zu erstellen. Diese Regeln definieren Aktionen für Formularobjekte, die durch voreingestellte Bedingungen, Benutzereingaben und Benutzeraktionen im Formular ausgelöst werden. Dies ermöglicht noch größere Effizienz beim schnellen und korrekten Ausfüllen der Formulare.

Der Regeleditor bietet eine intuitive und einfache Oberfläche zum Entwickeln der Regeln. Regeleditor bietet einen grafischen Editor für alle Benutzer. Darüber hinaus bietet der Regeleditor einen Code-Editor, mit dem Regeln und Skripte geschrieben werden können. Zu den wichtigsten Aktionen, die Sie mithilfe von Regeln in adaptiven Formularobjekten ausführen können, gehören die folgenden:

* Objekt ein- oder ausblenden
* Objekt aktivieren oder deaktivieren
* Wert für ein Objekt festlegen
* Wert eines Objekts prüfen
* Funktionen zur Berechnung des Werts eines Objekts ausführen
* Rufen Sie einen Formular-Datenmodelldienst auf und führen Sie einen Vorgang aus
* Eigenschaft eines Objekts festlegen

Der Regeleditor ersetzt die Skriptfunktionen in AEM 6.1 Forms und früheren Versionen. Ihre bereits vorhandenen Skripts werden allerdings im neuen Regeleditor beibehalten. Weitere Informationen zum Arbeiten mit vorhandenen Skripten im Regeleditor finden Sie unter [Auswirkungen des Regeleditors auf bereits vorhandene Skripte](../../forms/using/rule-editor.md#p-impact-of-rule-editor-on-existing-scripts-p).

Benutzer, die zur Gruppe der Formular-Hauptbenutzer hinzugefügt wurden, können neue Skripte erstellen und bestehende Skripte bearbeiten. Benutzer in der Gruppe der Formularbenutzer können die Skripte verwenden, aber keine Skripte erstellen oder bearbeiten.

## Grundlegendes zu Regeln {#understanding-a-rule}

Eine Regel ist eine Kombination von Aktionen und Bedingungen. Aktionen im Regeleditor sind Vorgänge wie Ausblenden, Anzeigen, Aktivieren, Deaktivieren oder Berechnen des Werts eines Objekts in einem Formular. Bedingungen sind boolesche Ausdrücke, die durch Prüfungen und Operationen für Status, Wert oder Eigenschaft eines Formularobjekts ausgewertet werden. Aktionen werden basierend auf dem bei der Auswertung einer Bedingung zurückgegebenen Wert (`True` oder `False`) ausgeführt.

Im Regeleditor steht eine Reihe vordefinierter Regeltypen zur Verfügung, z. B. Wenn, Anzeigen, Ausblenden, Aktivieren, Deaktivieren, Wert einstellen und Validieren, um Ihnen die Erstellung von Regeln zu erleichtern. Jeder Regeltyp ermöglicht es Ihnen, Bedingungen und Aktionen einer Regel zu definieren. In diesem Dokument werden die einzelnen Regeltypen im Detail beschrieben.

Eine Regel entspricht normalerweise einem der folgenden Konstrukte: 

**Bedingung-** AktionIn diesem Konstrukt definiert eine Regel zuerst eine Bedingung, gefolgt von einer Aktion zum Trigger. Dieses Konstrukt ist mit einer if-then-Anweisung in Programmiersprachen vergleichbar.

Im Regeleditor wird das Bedingung-Aktion-Konstrukt durch den Regeltyp **Wenn** durchgesetzt.

**Action-** ConditionIn diesem Konstrukt definiert eine Regel zuerst eine Aktion für den Trigger, gefolgt von Bedingungen für die Auswertung. Eine weitere Variante dieses Konstrukts ist Aktion-Bedingung-alternative Aktion, wobei auch eine alternative Aktion angegeben wird, die ausgelöst wird, wenn die Bedingung den Wert False zurückgibt.

Die Regeltypen zum Anzeigen, Ausblenden, Aktivieren, Deaktivieren und Wert einstellen im Regeleditor setzen das Aktion-Bedingung-Regelkonstrukt um. Die alternative Aktion für „Anzeigen“ ist standardmäßig „Ausblenden“, für „Aktivieren“ ist es „Deaktivieren“ und umgekehrt. Sie können die standardmäßige alternative Aktion nicht ändern.

>[!NOTE]
>
>Die verfügbaren Regeltypen, einschließlich der Bedingungen und Aktionen, die Sie im Regeleditor definieren, sind außerdem vom Typ des Formularobjekts abhängig, für das Sie die Regel erstellen. Im Regeleditor werden nur die zum Erstellen von Bedingungs- und Aktionsanweisungen für den jeweiligen Formularobjekttyp gültigen Regeltypen und Optionen angezeigt. So werden beispielsweise für ein Bereichsobjekt keine Regeln zum Validieren, Wert einstellen oder Deaktivieren angezeigt.

Weitere Informationen über die im Regeleditor verfügbaren Regeltypen finden Sie unter[ Verfügbare Regeltypen im Regeleditor](../../forms/using/rule-editor.md#p-available-rule-types-in-rule-editor-p).

### Richtlinien für die Auswahl eines Regelkonstrukts {#guidelines-for-choosing-a-rule-construct}

Für die meisten Anwendungsfälle können Sie ein beliebiges Regelkonstrukt verwenden. Im Folgenden finden Sie jedoch einige Richtlinien zur Wahl des am besten geeigneten Konstrukts für Ihre Zwecke. Weitere Informationen zu den verfügbaren Regeln im Regeleditor finden Sie unter [Verfügbare Regeltypen im Regeleditor](../../forms/using/rule-editor.md#p-available-rule-types-in-rule-editor-p).

* Als Faustregel zum Erstellen von Regeln ist es typischerweise sinnvoll, sie im Kontext des Objekts zu betrachten, für das die Regel erstellt werden soll. Angenommen, das Feld B soll in Abhängigkeit von einem Wert, den der Benutzer in Feld A eingibt, ein- oder ausgeblendet werden. In diesem Fall wird eine Bedingung für Feld A ausgewertet und basierend auf dem zurückgegebenen Wert eine Aktion für Feld B ausgelöst.

   Daher gilt: Wenn Sie eine Regel für Feld B (das Objekt, für das eine Bedingung ausgewertet wird), verwenden Sie das Konstrukt „Bedingung-Aktion“ oder den Regeltyp „Wenn“. Für Feld A müssten Sie dementsprechend das Konstrukt „Aktion-Bedingung“ oder den Regeltyp „Anzeigen“ oder „Ausblenden“ verwenden.

* In manchen Fällen müssen Sie mehrere Aktionen für dieselbe Bedingung ausführen. In solchen Fällen empfiehlt es sich, das Konstrukt „Bedingung-Aktion“ zu verwenden. In diesem Konstrukt können Sie eine Bedingung einmal auswerten und mehrere Aktionsanweisungen angeben.

   Um beispielsweise die Felder B, C und D basierend auf einer Bedingung auszublenden, die den vom Benutzer im Feld A angegebenen Wert auswertet, genügt eine Regel mit dem Konstrukt „Bedingung-Aktion“ oder dem Regeltyp „Wenn“ für Feld A, wobei Aktionen für die Sichtbarkeit der Felder B, C und D angegeben werden. Andernfalls benötigen Sie drei separate Regeln für die Felder B, C und D, wobei jede Regel die Bedingung prüft und das jeweilige Feld anzeigt oder ausblendet. In diesem Beispiel ist die Erstellung einer Wenn-Regel für ein Objekt effizienter als die Erstellung von Regeln zum Anzeigen und Ausblenden für drei Objekte.

* Um eine Aktion in Abhängigkeit von mehreren Bedingungen auszulösen, empfiehlt es sich, das Konstrukt „Aktion-Bedingung“ zu verwenden. Um beispielsweise Feld A nach Auswertung der Bedingungen für die Felder B, C und D anzuzeigen oder auszublenden, verwenden Sie Regeln des Typs „Anzeigen“ oder „Ausblenden“ für Feld A.
* Für Regeln, die genau eine Aktion für eine Bedingung enthalten, können Sie sowohl Bedingung-Aktion- als auch Aktion-Bedingung-Konstrukte verwenden.
* Für Regeln, bei denen eine Bedingung geprüft und sofort nach Eingabe eines Werts in ein Feld oder beim Verlassen des Felds eine Aktion ausgeführt wird, empfehlen wir, das Konstrukt „Bedingung-Aktion“ oder den Wenn-Regeltyp für das Feld zu verwenden, für das die Bedingung geprüft wird.
* Die Bedingung in der Wenn-Regel wird ausgewertet, wenn ein Benutzer den Wert des Objekts ändert, auf das die Wenn-Regel angewendet wird. Soll die Aktion jedoch bei einer serverseitigen Änderung des Wert ausgelöst werden, etwa bei voreingestellten Werten, empfehlen wir, eine Wenn-Regel zu erstellen, die die Aktion beim Initialisieren des Felds auslöst.
* Beim Erstellen von Regeln für Dropdown-, Optionsfeld- oder Kontrollkästchen-Objekte werden die Optionen oder Werte dieser Formularobjekte im Formular im Regeleditor vorausgefüllt.

## Verfügbare Operatortypen und Ereignisse im Regeleditor {#available-operator-types-and-events-in-rule-editor}

Der Regeleditor bietet die folgenden logischen Operatoren und Ereignisse, mit deren Hilfe Sie Regeln erstellen können.

* **Ist gleich**
* **Ist nicht gleich**
* **Beginnt mit**
* **Endet mit**
* **Enthält**
* **Ist leer**
* **Ist nicht leer**
* **Hat ausgewählt:** Gibt „true“ zurück, wenn der Benutzer eine bestimmte Option für ein Kontrollkästchen, eine Dropdownliste oder ein Optionsfeld wählt.
* **Ist initialisiert (Ereignis):** Gibt „true“ zurück, wenn ein Formularobjekt im Browser gerendert wird.
* **Wird geändert (Ereignis):** Gibt „true“ zurück, wenn der Benutzer den eingegebenen Wert oder die ausgewählte Option für ein Formularobjekt ändert.

## Verfügbare Regeltypen im Regeleditor {#available-rule-types-in-rule-editor}

Im Regeleditor steht eine Reihe vordefinierter Regeltypen zur Verfügung, die Sie verwenden können, um Regeln zu erstellen. Im Folgenden werden die einzelnen Regeltypen im Detail beschrieben. Weitere Informationen zum Erstellen von Regeln im Regeleditor finden Sie unter [Regeln schreiben](../../forms/using/rule-editor.md#p-write-rules-p).

### Wenn {#whenruletype}

Der **Wenn**-Regeltyp nutzt das Konstrukt **Bedingung-Aktion-Alternative Aktion**, in manchen Fällen auch nur das Konstrukt **Bedingung-Aktion**. Für diesen Regeltyp geben Sie zunächst eine auszuwertende Bedingung und dann eine Aktion an, die ausgelöst werden soll, wenn die Bedingung erfüllt ist (`True`„). Bei Verwendung des Wenn-Regeltyps können Sie mehrere UND- und ODER-Operatoren verwenden, um [verschachtelte Ausdrücke](#nestedexpressions) zu erstellen.

Mit dem Wenn-Regeltyp können Sie können Sie eine Bedingung für ein Formularobjekt auswerten und Aktionen für ein oder mehrere Objekte ausführen.

Einfach ausgedrückt: Eine typische Wenn-Regel ist wie folgt aufgebaut:

`When on Object A:`

`(Condition 1 AND Condition 2 OR Condition 3) is TRUE;`

`Then, do the following:`

Aktion 2 auf Objekt B; UND Aktion 3 auf Objekt C;

_

Wenn Sie über eine Komponente mit mehreren Werten verfügen, z. B. Optionsfelder oder Listen, während Sie eine Regel für diese Komponente erstellen, werden die Optionen automatisch abgerufen und dem Regelersteller zur Verfügung gestellt. Sie müssen die Optionswerte nicht erneut eingeben.

Eine Liste könnte beispielsweise vier Optionen enthalten: Rot, Blau, Grün und Gelb. Beim Erstellen der Regel werden die Optionen (Optionsfelder) automatisch abgerufen und dem Regelersteller wie folgt zur Verfügung gestellt:

![multivaluefcdisplayOptions](assets/multivaluefcdisplaysoptions.png)

Beim Schreiben der Wenn-Regel können Sie die Aktion „Wert löschen von“ auslösen. Wert löschen von: Löscht den Wert des angegebenen Objekts. Wenn Sie in der Wenn-Anweisung die Option Wert löschen von verwenden, können Sie komplexe Bedingungen mit mehreren Feldern erstellen.

![clearvalue](assets/clearvalueof.png)

**** HideBlendet das angegebene Objekt aus.

**** ShowZeigt das angegebene Objekt an.

**** EnableAktiviert das angegebene Objekt.

**** DisableDeaktiviert das angegebene Objekt.

**Rufen Sie** serviceInvokes einen Dienst auf, der in einem Formulardatenmodell konfiguriert ist. Wenn Sie den Vorgang „Dienst aufrufen“ wählen, wird ein Feld angezeigt. Beim Antippen des Feldes zeigt es alle in allen Formulardatenmodellen konfigurierten Dienste auf Ihrer AEM-Instanz an. Bei der Auswahl eines Formulardatenmodell-Diensts erscheinen zusätzliche Felder, in denen Sie Formularobjekte mit Ein- und Ausgabeparametern für den angegebenen dienst zuordnen können. Siehe Beispielregel zum Aufrufen von Formulardatendiensten.

Zusätzlich zum Formulardatenmodelldienst können Sie eine direkte WSDL-URL angeben, um einen Web-Dienst aufzurufen. Ein Formulardatenmodelldienst hat jedoch viele Vorteile und den empfohlenen Ansatz, einen Dienst aufzurufen.

Weitere Informationen zum Konfigurieren von Diensten im Formulardatenmodell finden Sie unter [AEM Forms Data Integration](/help/forms/using/data-integration.md).

**Legen Sie den Wert** vonComputes fest und legt den Wert des angegebenen Objekts fest. Sie können den Objektwert auf eine Zeichenfolge, den Wert eines anderen Objekts, den mithilfe eines mathematischen Ausdrucks oder einer Funktion berechneten Wert, den Wert einer Eigenschaft eines Objekts oder den Ausgabewert eines konfigurierten Formulardatenmodelldienstes setzen. Wenn Sie die Webdienstoption auswählen, werden alle in allen Formulardatenmodellen konfigurierten Dienste auf Ihrer AEM angezeigt. Bei der Auswahl eines Formulardatenmodell-Diensts erscheinen zusätzliche Felder, in denen Sie Formularobjekte mit Ein- und Ausgabeparametern für den angegebenen dienst zuordnen können.

Weitere Informationen zum Konfigurieren von Diensten im Formulardatenmodell finden Sie unter [AEM Forms Data Integration](/help/forms/using/data-integration.md).

Mit dem Regeltyp **Eigenschaft** können Sie den Wert einer Eigenschaft des angegebenen Objekts basierend auf einer Bedingungsaktion festlegen.

Damit können Sie Regeln definieren, um Kontrollkästchen dynamisch zum adaptiven Formular hinzuzufügen. Sie können eine Regel mithilfe einer benutzerdefinierten Funktion, eines Formularobjekts oder einer Objekteigenschaft definieren.

![Eigenschaft festlegen](assets/set_property_rule_new.png)

Um eine Regel basierend auf einer benutzerdefinierten Funktion zu definieren, wählen Sie **Funktionsausgabe** aus der Dropdown-Liste aus und ziehen Sie eine benutzerdefinierte Funktion aus der Registerkarte **Funktionen** . Wenn die Bedingungsaktion erfüllt ist, wird die Anzahl der in der benutzerdefinierten Funktion definierten Kontrollkästchen zum adaptiven Formular hinzugefügt.

Um eine auf einem Formularobjekt basierende Regel zu definieren, wählen Sie **Formularobjekt** aus der Dropdownliste aus und ziehen Sie ein Formularobjekt aus der Registerkarte **Formularobjekte**. Wenn die Bedingungsaktion erfüllt ist, wird die Anzahl der im Formularobjekt definierten Kontrollkästchen zum adaptiven Formular hinzugefügt.

Mit einer auf einer Objekteigenschaft basierenden Set Property-Regel können Sie die Anzahl der Kontrollkästchen in einem adaptiven Formular basierend auf einer anderen Objekteigenschaft hinzufügen, die im adaptiven Formular enthalten ist.

Die folgende Abbildung zeigt ein Beispiel für das dynamische Hinzufügen von Kontrollkästchen basierend auf der Anzahl der Dropdown-Listen im adaptiven Formular:

![Objekteigenschaft](assets/object_property_set_property_new.png)

**Wert löschen** von Löscht den Wert des angegebenen Objekts.

**Fokus** auf das angegebene Objekt legen

**Formular speichern** Speichert das Formular.

**Submit** FormsSendet das Formular.

**Zurücksetzen** FormSetzt das Formular zurück.

**Validieren Sie** FormValidiert das Formular.

**** Instanz hinzufügenFügt eine Instanz des angegebenen wiederholbaren Bereichs oder der Tabellenzeile hinzu.

**Entfernen** InstanceEntfernt eine Instanz des angegebenen wiederholbaren Bereichs oder der Tabellenzeile.

**Navigieren Sie** zu Navigiert zu anderen interaktiven Kommunikationen, adaptiven Formularen, anderen Assets wie Bildern oder Dokumentfragmenten oder zu einer externen URL. Weitere Informationen finden Sie unter [Schaltfläche zum Hinzufügen zur interaktiven Kommunikation](../../forms/using/create-interactive-communication.md#addbuttontothewebchannel).

### Einstellen des Wertes von {#set-value-of}

Mit dem Regeltyp **[!UICONTROL Wert von]** können Sie den Wert eines Formularobjekts abhängig davon festlegen, ob die angegebene Bedingung erfüllt ist oder nicht. Als Wert kann der Wert eines anderen Objekts, ein Literal-String, ein aus einem mathematischen Ausdruck oder einer Funktion abgeleiteter Wert oder der Wert einer Eigenschaft eines anderen Objekts oder die Ausgabe eines Formulardatenmodelldiensts sein. In ähnlicher Weise können Sie Bedingungen für Komponenten, Strings, Eigenschaften oder Werte prüfen, die aus Funktionen oder mathematischen Ausdrücken abgeleitet sind.

Der Regeltyp „Wert einstellen“ steht für manche Formularobjekte nicht zur Verfügung, etwa für Bereiche und Schaltflächen der Symbolleiste. Eine standardmäßige Regel des Typs „Wert einstellen“ hat die folgende Struktur:



Wert von Objekt A einstellen auf:

(Zeichenfolge ABC) ODER
(Objekteigenschaft X des Objekts C) ODER
(Wert aus einer Funktion) ODER
(Wert aus einem mathematischen Ausdruck) ODER
(Ausgabewert eines Datenmodelldienstes oder Webdienstes);

Wenn (optional):

(Bedingung 1 UND Bedingung 2 UND Bedingung 3) TRUE zurückgibt;



Im folgenden Beispiel wird der Wert im Feld `dependentid` als Eingabe verwendet und der Wert des Felds `Relation` auf die Ausgabe des Arguments `Relation` des Formulardatenmodelldienstes `getDependent` gesetzt.

![set-value-web-service](assets/set-value-web-service.png)

Beispiel, wie die Regel „Wert festlegen“ den Formulardatenmodelldienst verwendet

>[!NOTE]
>
>Darüber hinaus können Sie mit „Wert festlegen von“ alle Werte in einer Dropdown-Listenkomponente aus der Ausgabe eines Formulardatenmodelldienstes oder eines Web-Dienstes befüllen. Stellen Sie jedoch sicher, dass das von Ihnen gewählte Ausgabeargument vom Typ „Array“ ist. Alle Werte, die in einem Array zurückgegeben werden, stehen in der angegebenen Dropdown-Liste zur Verfügung.

### Anzeigen {#show}

Mithilfe des Regeltyps **Anzeigen** können Sie eine Regel zum Anzeigen oder Ausblenden eines Formularobjekts in Abhängigkeit davon erstellen, ob eine Bedingung erfüllt ist oder nicht. Beim Regeltyp „Anzeigen“ wird zugleich die Aktion „Ausblenden“ ausgelöst, falls die Bedingung nicht erfüllt oder `False` zurückgibt.

Eine typische Regel zum Anzeigen ist wie folgt strukturiert:



`Show Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Hide Object A;`



### Ausblenden {#hide}

Regeln des Typs **Ausblenden** können ähnlich wie Regeln des Typs „Anzeigen“ dazu verwendet werden, Formularobjekte in Abhängigkeit davon, ob eine Bedingung erfüllt ist oder nicht, anzuzeigen oder auszublenden. Beim Regeltyp „Ausblenden“ wird zugleich die Aktion „Anzeigen“ ausgelöst, falls die Bedingung nicht erfüllt oder `False` zurückgibt.

Eine typische Regel zum Ausblenden ist wie folgt strukturiert:



`Hide Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Show Object A;`



### Aktivieren {#enable}

Mithilfe des Regeltyps **Aktivieren** können Sie ein Formularobjekt in Abhängigkeit davon aktivieren oder deaktivieren, ob eine Bedingung erfüllt ist oder nicht. Beim Regeltyp „Aktivieren“ wird zugleich die Aktion „Deaktivieren“ ausgelöst, falls die Bedingung nicht erfüllt oder `False` zurückgibt.

Eine typische Regel zum Aktivieren ist wie folgt strukturiert:



`Enable Object A;`

`When:`

`(Condition 1 AND Condition 2 AND Condition 3) is TRUE;`

`Else:`

`Disable Object A;`



### Deaktivieren {#disable}

Regeln des Typs **Deaktivieren** können ähnlich wie Regeln des Typs „Aktivieren“ dazu verwendet werden, Formularobjekte in Abhängigkeit davon, ob eine Bedingung erfüllt ist oder nicht, zu aktivieren oder zu deaktivieren.. Beim Regeltyp „Deaktivieren“ wird zugleich die Aktion „Aktivieren“ ausgelöst, falls die Bedingung nicht erfüllt oder `False` zurückgibt.

Eine typische Regel zum Deaktivieren ist wie folgt strukturiert:



`Disable Object A;`

`When:`

`(Condition 1 OR Condition 2 OR Condition 3) is TRUE;`

`Else:`

`Enable Object A;`

### Validieren {#validate}

Regeln des Typs **Validieren** validieren den Wert in einem Feld mithilfe eines Ausdrucks. Sie können z. B. einen Ausdruck erstellen, mit dem ein Textfeld zur Eingabe eines Namens geprüft wird, um sicherzustellen, dass dort keine Sonderzeichen oder Zahlen eingegeben wurden.

Eine typische Regel zum Validieren ist wie folgt strukturiert:

`Validate Object A;`

`Using:`

`(Expression 1 AND Expression 2 AND Expression 3) is TRUE;`

>[!NOTE]
>
>Wenn der angegebene Wert nicht der Validierungsregel entspricht, können Sie eine Validierungsmeldung für den Benutzer anzeigen lassen. Sie können die Meldung im Feld **[!UICONTROL Skriptüberprüfungsmeldung]** in den Komponenteneigenschaften in der Seitenleiste angeben.

![script-validation](assets/script-validation.png)

### Festlegen von Optionen für {#setoptionsof}

Mit dem Regeltyp **Optionen von** können Sie Regeln definieren, um Kontrollkästchen dynamisch zum adaptiven Formular hinzuzufügen. Sie können ein Formulardatenmodell oder eine benutzerdefinierte Funktion verwenden, um die Regel zu definieren.

Um eine Regel basierend auf einer benutzerdefinierten Funktion zu definieren, wählen Sie **Funktionsausgabe** aus der Dropdown-Liste aus und ziehen Sie eine benutzerdefinierte Funktion aus der Registerkarte **Funktionen** . Die Anzahl der in der benutzerdefinierten Funktion definierten Kontrollkästchen wird dem adaptiven Formular hinzugefügt.

![Benutzerdefinierte Funktionen](assets/custom_functions_set_options_new.png)

Informationen zum Erstellen einer benutzerdefinierten Funktion finden Sie unter [Benutzerdefinierte Funktionen im Regeleditor](#custom-functions).

So definieren Sie eine auf einem Formulardatenmodell basierende Regel:

1. Wählen Sie **Dienstausgabe** aus der Dropdown-Liste aus.
1. Wählen Sie das Datenmodellobjekt aus.
1. Wählen Sie eine Datenmodellobjekteigenschaft aus der Dropdownliste **Anzeigewert** aus. Die Anzahl der Kontrollkästchen im adaptiven Formular wird von der Anzahl der für diese Eigenschaft in der Datenbank definierten Instanzen abgeleitet.
1. Wählen Sie eine Datenmodellobjekteigenschaft aus der Dropdownliste **Wert speichern** aus.

![Optionen für FDM-Sets](assets/fdm_set_options_new.png)

## Grundlegendes zur Benutzeroberfläche des Regeleditors {#understanding-the-rule-editor-user-interface}

Der Regeleditor bietet eine umfassende, aber einfache Benutzeroberfläche zum Erstellen und Verwalten von Regeln. Sie können die Benutzeroberfläche des Regeleditors im Autorenmodus von einem adaptiven Formular aus aufrufen.

Benutzeroberfläche des Regeleditors starten

1. Öffnen Sie ein adaptives Formular im Autorenmodus.
1. Tippen Sie auf das Formularobjekt, für das Sie eine Regel schreiben möchten, und tippen Sie in der Komponentensymbolleiste auf ![edit-rules](assets/edit-rules.png). Die Benutzeroberfläche des Regeleditors wird angezeigt.

   ![create-rules](assets/create-rules.png)

   Alle vorhandenen Regeln für die ausgewählten Formularobjekte sind in dieser Ansicht aufgelistet. Weitere Informationen zum Verwalten vorhandener Regeln finden Sie unter [Regeln verwalten](../../forms/using/rule-editor.md#p-manage-rules-p).

1. Tippen Sie auf **[!UICONTROL Erstellen]** , um eine neue Regel zu schreiben. Wenn Sie den Regeleditor zum ersten Mal starten, wird standardmäßig der Visual Editor der Regeleditor-Benutzeroberfläche geöffnet.

   ![Benutzeroberfläche des Regeleditors](assets/rule-editor-ui.png)

Im Folgenden werden die einzelnen Komponenten der Benutzeroberfläche des Regeleditors im Detail beschrieben.

### A. Komponenten und -Regelanzeige {#a-component-rule-display}

Zeigt den Titel des adaptiven Formularobjekts, über das Sie den Regeleditor aufgerufen haben, sowie den momentan ausgewählten Regeltyp an. Im oben gezeigten Beispiel wurde der Regeleditor über ein adaptives Formularobjekt namens „Salary“ gestartet und der Wenn-Regeltyp ist ausgewählt.

### B. Formularobjekte und Funktionen {#b-form-objects-and-functions-br}

Im linken Bereich der Benutzeroberfläche des Regeleditors stehen zwei Registerkarten zur Verfügung: **[!UICONTROL Formularobjekte]** und **[!UICONTROL Funktionen]**.

Die Registerkarte „Formularobjekte“ zeigt eine hierarchische Ansicht aller Objekte, die im adaptiven Formular enthalten sind. Dabei werden Titel und Typ der Objekte angezeigt. Wenn Sie eine Regel erstellen, können Sie Formularobjekte in den Regeleditor ziehen und dort ablegen.  Beim Erstellen oder Bearbeiten einer Regel, wenn Sie ein Objekt oder eine Funktion per Drag-and-Drop in einen Platzhalter ziehen, nimmt der Platzhalter automatisch den entsprechenden Werttyp an.

Die Formularobjekte, für die eine oder mehrere gültige Regeln angewendet wurden, sind mit einem grünen Punkt markiert. Wenn eine der auf ein Formularobjekt angewendeten Regeln ungültig ist, ist das Formularobjekt mit einem gelben Punkt markiert.

Die Registerkarte „Funktionen“ enthält eine Reihe integrierter Funktionen, z. B. für Summe von, Minimum von, Maximum von, Durchschnitt von, Anzahl von und Formular überprüfen. Sie können diese Funktionen verwenden, um Werte in wiederholbaren Bereichen und Tabellenzeilen zu berechnen und sie beim Schreiben von Regeln in Aktions- und Bedingungsanweisungen zu verwenden. Sie können jedoch auch [benutzerdefinierte Funktionen](#custom-functions) erstellen.

![Registerkarte „Funktionen“](assets/functions.png)

>[!NOTE]
>
>Sie können auf den Registerkarten „Formularobjekte“ und „Funktionen“ eine Textsuche nach den Namen und Titeln von Objekten und Funktionen durchführen.

In der Strukturansicht auf der linken Seite können Sie durch Tippen auf die darin enthaltenen Formularobjekte die Regeln anzeigen, die auf das jeweilige Objekt angewendet wurden. Sie können durch die Regeln der verschiedenen Formularobjekte navigieren und darüber hinaus Regeln zwischen Formularobjekten kopieren und einfügen. Weitere Informationen finden Sie unter [Regeln kopieren und einfügen](../../forms/using/rule-editor.md#p-copy-paste-rules-p).

### C. Umschalten zwischen Formularobjekten und Funktionen {#c-form-objects-and-functions-toggle-br}

Durch Tippen auf Schaltfläche schalten Sie zwischen den Bereichen für Formularobjekte und Funktionen um.

### D. Visueller Regeleditor  {#d-visual-rule-editor}

Der visuelle Regeleditor ist im visuellen Editormodus der Regeleditor-Benutzeroberfläche der Bereich, in dem Sie Regeln erstellen. Sie können hier einen Regeltyp wählen und die entsprechenden Bedingungen und Aktionen definieren. Beim Definieren von Bedingungen und Aktionen in einer Regel können Sie Formularobjekte und Funktionen aus dem Bereich „Formularobjekte und Funktionen“ ziehen und ablegen.

Weitere Informationen zur Verwendung des visuellen Regeleditors finden Sie unter [Regeln schreiben](../../forms/using/rule-editor.md#p-write-rules-p).

### E. Umschalter zwischen Visual Editor und Codeeditor {#e-visual-code-editors-switcher}

Benutzer können in der Gruppe der Formular-Hauptbenutzer auf den Code-Editor zugreifen. Bei anderen Benutzern ist der Code-Editor nicht verfügbar. Mithilfe des Umschalters rechts oberhalb des Regeleditors können Sie zwischen Visual Editor- und Codeeditormodus für den Regeleditor wechseln, wenn Sie dazu berechtigt sind. Wenn Sie den Regeleditor zum ersten Mal starten, wird er im Visual Editor-Modus geöffnet. Sie können Regeln im Visual Editor-Modus erstellen oder in den Codeeditormodus wechseln, um ein Regelskript zu schreiben. Wenn Sie eine Regel im Codeeditor ändern oder schreiben, ist es jedoch nicht möglich, für diese Regel zum Visual Editor zurückzuschalten, es sei denn, Sie löschen den Inhalt des Codeeditors.

AEM Forms zeichnet den zuletzt von Ihnen zum Erstellen einer Regel verwendeten Modus des Regeleditors auf. Wenn Sie den Regeleditor das nächste Mal starten, wird er in diesem Modus geöffnet. Sie können jedoch auch einen Standardmodus konfigurieren, sodass der Regeleditor immer in diesem Modus geöffnet wird. Gehen Sie dazu wie folgt vor:

1. Wechseln Sie unter `https://[host]:[port]/system/console/configMgr` zur AEM Web-Konsole.
1. Klicken Sie auf **[!UICONTROL Webkanalkonfiguration für adaptive Formulare und interaktive Kommunikation]**, um sie zu bearbeiten.
1. Wählen Sie **[!UICONTROL Visual Editor]** oder **[!UICONTROL Codeeditor]** aus der Dropdownliste für den **[!UICONTROL Standardmodus für den Regeleditor]**.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

### F. Schaltflächen „Fertig“ und „Abbrechen“  {#f-done-and-cancel-buttons}

Die Schaltfläche **[!UICONTROL Fertig]** wird zum Speichern einer Regel verwendet. Sie können eine unvollständige Regel speichern. Unvollständige Regeln sind allerdings ungültig und werden nicht ausgeführt. Eine Liste mit gespeicherten Regeln für ein Formularobjekt wird angezeigt, wenn Sie den Regeleditor das nächste Mal aus demselben Formularobjekt starten. Sie können bestehende Regeln in dieser Ansicht verwalten. Weitere Informationen hierzu finden Sie unter[ Regeln verwalten](../../forms/using/rule-editor.md#p-manage-rules-p).

Über die Schaltfläche **[!UICONTROL Abbrechen]** verwerfen Sie alle Änderungen, die Sie an einer Regel vorgenommen haben, und der Regeleditor wird geschlossen.

## Regeln schreiben  {#write-rules}

Zum Schreiben von Regeln können Sie den visuellen Regeleditor oder den Codeeditor verwenden. Wenn Sie den Regeleditor zum ersten Mal starten, wird er im Visual Editor-Modus geöffnet. Sie können zum Codeeditormodus wechseln und Regeln schreiben. Wenn Sie eine Regel im Codeeditor schreiben oder ändern, ist es jedoch nicht möglich, für diese Regel zum Visual Editor zu wechseln, es sei denn, Sie löschen den Inhalt des Codeeditors. Wenn Sie den Regeleditor das nächste Mal starten, wird er im zuletzt zum Erstellen von Regeln verwendeten Modus geöffnet.

Im Folgenden wird zunächst das Schreiben von Regeln im Visual Editor beschrieben.

### Verwenden des Visual Editor  {#using-visual-editor}

Mithilfe des folgenden Beispielformulars wird das Erstellen von Regeln im Visual Editor gezeigt.

![create-rule-example](assets/create-rule-example.png)

Im Abschnitt für die Kreditvoraussetzungen in diesem Beispielformular für einen Kreditantrag müssen die Antragsteller ihren Familienstand, ihr Gehalt und, falls verheiratet, das Gehalt des Partners/der Partnerin angeben. Die Regel berechnet basierend auf den Eingaben der Benutzer den Kreditanspruchsbetrag und zeigt das Feld für den Kreditanspruch an. Wenden Sie die folgenden Regeln an, um dieses Szenario zu implementieren:

* Das Gehaltsfeld des Partners/der Partnerin wird nur angezeigt, wenn als Familienstand „Verheiratet“ angegeben wurde.
* Der Kreditanspruchsbetrag ist 50 % des Gesamtgehalts.

Führen Sie die folgenden Schritte aus, um die Regeln zu schreiben:

1. Schreiben Sie zuerst die Regel, mit der die Sichtbarkeit des Felds für das Gehalt des Partners bzw. der Partnerin entsprechend der vom Benutzer über das Optionsfeld „Familienstand“ gewählten Option gesteuert wird.

   Öffnen Sie das Kreditantragsformular im Autorenmodus. Tippen Sie auf die Komponente **Familienstand** und dann auf ![edit-rules](assets/edit-rules.png). Tippen Sie als Nächstes auf **[!UICONTROL Erstellen]**, um den Regeleditor zu starten.

   ![write-rules-visual-editor-1](assets/write-rules-visual-editor-1.png)

   Wenn Sie den Regeleditor starten, ist standardmäßig die Wenn-Regel ausgewählt. Darüber hinaus wird das Formularobjekt (in diesem Fall „Familienstand“), von dem aus Sie den Regeleditor gestartet haben, in der Wenn-Anweisung angegeben.

   Sie können zwar das ausgewählte Objekt nicht bearbeiten oder ändern, es ist jedoch möglich, über die Dropdownliste für Regeln einen anderen Regeltyp wählen (siehe unten). Wenn Sie eine Regel für ein anderes Objekt erstellen möchten, tippen Sie auf „Abbrechen“, um den Regeleditor zu beenden, und starten Sie ihn erneut über das gewünschte Formularobjekt.

1. Tippen Sie auf die Dropdown-Liste **[!UICONTROL Status]** auswählen und wählen Sie **[!UICONTROL ist gleich]** aus. Das Feld **[!UICONTROL String eingeben]** wird angezeigt.

   ![write-rules-visual-editor-2](assets/write-rules-visual-editor-2.png)

   Im Optionsfeld Familienstand werden den Optionen **Verheiratet** und **Einfach** die Werte **0** bzw. **1** zugewiesen. Sie können die zugewiesenen Werte auf der Registerkarte „Titel“ des Dialogfelds zum Bearbeiten des Optionsfelds überprüfen, wie unten gezeigt.

   ![Optionsfeldwerte im Regeleditor](assets/radio-button-values.png)

1. Geben Sie im Feld **String eingeben** in der Regel den Wert **0** ein.

   ![write-rules-visual-editor-4](assets/write-rules-visual-editor-4.png)

   Sie haben die Bedingung als `When Marital Status is equal to Married` definiert. Definieren Sie anschließend die Aktion, die ausgeführt werden soll, wenn diese Bedingung erfüllt ist.

1. Wählen Sie für die Dann-Anweisung die Option **[!UICONTROL Anzeigen]** aus der Dropdownliste **[!UICONTROL Aktion auswählen]**.

   ![write-rules-visual-editor-5](assets/write-rules-visual-editor-5.png)

1. Ziehen Sie das Feld **Gehalt des Partners** aus der Registerkarte &quot;Formularobjekte&quot;in das Feld **Objekt ablegen oder hier** auswählen. Tippen Sie alternativ auf das Feld **Legen Sie das Objekt ab oder wählen Sie hier** aus und wählen Sie das Feld **Gehalt des Partners** aus dem Popup-Menü aus, in dem alle Formularobjekte im Formular aufgelistet werden.

   ![write-rules-visual-editor-6](assets/write-rules-visual-editor-6.png)

   Die Regel wird wie folgt im Regeleditor angezeigt.

   ![write-rules-visual-editor-7](assets/write-rules-visual-editor-7.png)

   Tippen Sie auf **Fertig**, um die Regel zu speichern.

1. Wiederholen Sie die Schritte 1 bis 5, um eine weitere Regel zu definieren, mit der das Feld für das Gehalt des Partners ausgeblendet wird, wenn als Familienstand „Ledig“ angegeben wird. Die Regel wird wie folgt im Regeleditor angezeigt.

   ![write-rules-visual-editor-8](assets/write-rules-visual-editor-8.png)

   >[!NOTE]
   >
   >Alternativ zu diesem Verfahren können Sie dieses Verhalten auch implementieren, indem Sie lediglich eine Regel des Typs „Anzeigen“ für das Feld für das Gehalt des Partners anstelle zweier Wenn-Regeln für das Feld „Familienstand“ erstellen.

   ![write-rules-visual-editor-9](assets/write-rules-visual-editor-9.png)

1. Als Nächstes erstellen Sie eine Regel für die Berechnung des Kreditanspruchsbetrags (50 % des Gesamtgehalts) und zur Anzeige des Betrags im Feld für den Kreditanspruch. Dies erreichen Sie, indem Sie Regeln des Typs **Wert einstellen** für das Kreditanspruchsfeld erstellen.

   Tippen Sie im Authoring-Modus auf das Feld **[!UICONTROL Kreditanspruch]** und tippen Sie auf ![edit-rules](assets/edit-rules.png). Tippen Sie als Nächstes auf **[!UICONTROL Erstellen]**, um den Regeleditor zu starten.

1. Wählen Sie die Regel **[!UICONTROL Wert einstellen]** aus der Dropdownliste mit den Regeln.

   ![write-rules-visual-editor-10](assets/write-rules-visual-editor-10.png)

1. Tippen Sie auf **[!UICONTROL Wählen Sie Option]** und wählen Sie **[!UICONTROL Mathematischer Ausdruck]** aus. Ein Feld, in dem Sie mathematische Ausdrücke schreiben können, wird geöffnet.

   ![write-rules-visual-editor-11](assets/write-rules-visual-editor-11.png)

1. Führen Sie in diesem Ausdrucksfeld Folgendes aus:

   * Wählen Sie das Feld **Gehalt** auf der Registerkarte „Formularobjekt“ aus oder ziehen Sie es in das erste Feld **Legen Sie das Objekt ab oder wählen Sie hier aus** und legen Sie es dort ab.

   * Wählen Sie **Plus** aus dem Feld **Operator wählen**.

   * Wählen Sie auf der Registerkarte Forms-Objekt das Feld **Gehalt des Partners** aus oder ziehen Sie es in das andere Feld **Objekt ablegen oder hier** auswählen.

   ![write-rules-visual-editor-12](assets/write-rules-visual-editor-12.png)

1. Tippen Sie anschließend auf den markierten Bereich um das Ausdrucksfeld und tippen Sie auf **Ausdruck erweitern**.

   ![write-rules-visual-editor-13](assets/write-rules-visual-editor-13.png)

   Wählen Sie im erweiterten Ausdrucksfeld **geteilt durch** aus dem Feld **Operator wählen** und **Zahl** aus dem Feld **Option auswählen**. Geben Sie das **2** in das Zahlenfeld ein.

   ![write-rules-visual-editor-14](assets/write-rules-visual-editor-14.png)

   >[!NOTE]
   >
   >Sie können mithilfe von Komponenten, Funktionen, mathematischen Ausdrücken und Eigenschaftswerten aus dem Feld „Option auswählen“ komplexe Ausdrücke erstellen.

   Als Nächstes erstellen Sie eine Bedingung. Wenn diese „true“ zurückgibt, wird der Ausdruck ausgeführt.

1. Tippen Sie auf **Bedingung** hinzufügen , um eine Wenn-Anweisung hinzuzufügen.

   ![write-rules-visual-editor-15](assets/write-rules-visual-editor-15.png)

   Geben Sie in der Wenn-Anweisung Folgendes ein:

   * Wählen Sie das Feld **Familienstand** auf der Registerkarte „Formularobjekt“ aus oder ziehen Sie es in das erste Feld **Legen Sie das Objekt ab oder wählen Sie hier aus** und legen Sie es dort ab.

   * Wählen Sie **Ist gleich** aus dem Feld **Operator wählen**.

   * Wählen Sie im anderen Feld **Objekt ablegen oder wählen Sie hier** aus und geben Sie **Verheiratet** im Feld **Geben Sie einen String** ein.

   Die Regel wird schließlich wie folgt im Regeleditor angezeigt.  ![write-rules-visual-editor-16](assets/write-rules-visual-editor-16.png)

   Tippen Sie auf **Fertig**, um die Regel zu speichern.

1. Wiederholen Sie die Schritte 7 bis 12, um eine weitere Regel zu definieren, mit deren Hilfe der Kreditanspruch für den Familienstand „Ledig“ berechnet wird. Die Regel wird wie folgt im Regeleditor angezeigt.

   ![write-rules-visual-editor-17](assets/write-rules-visual-editor-17.png)

>[!NOTE]
>
>Alternativ dazu können Sie den Kreditanspruch mithilfe der Regel „Werte festlegen von“ in der Wenn-Regel berechnen, die Sie zum Anzeigen oder Ausblenden des Felds für das Gehalt des Partners oder der Partnerin erstellt haben. Die resultierende kombinierte Regel (für den Familienstand „Ledig“) wird wie folgt im Regeleditor angezeigt.
>
>Auf ähnliche Weise können Sie eine kombinierte Regel erstellen, die die Sichtbarkeit des Felds für das Gehalt des Partners oder der Partnerin steuert und den Kreditanspruch für den Familienstand „Verheiratet“ berechnet.

![write-rules-visual-editor-18](assets/write-rules-visual-editor-18.png)

### Verwenden des Codeeditors {#using-code-editor}

Benutzer, die zur Gruppe der Formular-Hauptbenutzer hinzugefügt wurden, können den Code-Editor verwenden. Der Regeleditor generiert automatisch den JavaScript-Code für jede Regel, die Sie mithilfe des Visual Editor erstellen. Indem Sie vom Visual Editor zum Codeeditor wechseln, können Sie den generierten Code anzeigen. Wenn Sie jedoch den Code einer Regel im Codeeditor ändern, können Sie nicht mehr zurück zum Visual Editor wechseln. Sie können neue Regeln auch von Anfang an im Codeeditor schreiben, wenn Sie diesen dem Visual Editor vorziehen. Mithilfe des Schalters zwischen dem Visual Editor und dem Codeeditor können Sie zwischen den beiden Modi wechseln.

Das Code-Editor-JavaScript ist die Ausdruckssprache für adaptive Formulare. Alle Ausdrücke sind gültige JavaScript-Ausdrücke und verwenden Skriptmodell-APIs für adaptive Formulare. Diese Ausdrücke geben Werte bestimmter Typen zurück. Eine vollständige Liste der Klassen, Ereignisse, Objekte und öffentlichen APIs für adaptive Formulare finden Sie unter [JavaScript Library API-Referenz für adaptive Formulare](https://helpx.adobe.com/de/experience-manager/6-5/forms/javascript-api/index.html).

Weitere Informationen zu Richtlinien für das Schreiben von Regeln im Codeeditor finden Sie unter [Adaptive Formularausdrücke](/help/forms/using/adaptive-form-expressions.md).

Beim Schreiben von JavaScript-Code in den Regeleditor helfen Ihnen die visuellen Hinweise bei der Strukturierung und Syntax:

* Syntaxmarkierungen
* Automatische Einrückung
* Hinweise und Vorschläge für Formularobjekte, Funktionen und deren Eigenschaften
* Automatisches Ausfüllen von Formularkomponentennamen und gängigen JavaScript-Funktionen

![javascriptruleeditorEditor](assets/javascriptruleeditor.png)

#### Benutzerdefinierte Funktionen im Regeleditor {#custom-functions}

Neben den vordefinierten Funktionen wie *Summe von*, die unter &quot;Funktionenausgabe&quot;aufgeführt sind, können Sie auch benutzerdefinierte Funktionen schreiben, die Sie häufig benötigen. Stellen Sie sicher, dass für die Funktion, die Sie schreiben, ein `jsdoc` vorhanden ist.

Begleitende `jsdoc` ist erforderlich:

* Wenn Sie benutzerdefinierte Konfigurationen und Beschreibungen verwenden möchten.
* Da es mehrere Möglichkeiten gibt, eine Funktion in `JavaScript,` zu deklarieren, können Sie mit Kommentaren die Funktionen verfolgen.

Weitere Informationen finden Sie unter [usejsdoc.org](https://usejsdoc.org/).

Unterstützte `jsdoc` -Tags:

* ****
PrivateSyntax: Eine private Funktion ist nicht als benutzerdefinierte Funktion enthalten.`@private`
Eine private Funktion ist nicht als benutzerdefinierte Funktion enthalten.

* ****
NameSyntax: Alternativ  `@name funcName <Function Name>`
können  `,` Sie Folgendes verwenden:  `@function funcName <Function Name>` **oder** `@func` `funcName <Function Name>`.
   `funcName` ist der Name der Funktion (Leerzeichen sind nicht zulässig).
   `<Function Name>` ist der Anzeigename der Funktion.

* ****
MemberSyntax: Hängt einen Namespace an die Funktion an.`@memberof namespace`
Hängt einen Namespace an die Funktion an.

* ****
ParameterSyntax: Alternativ können Sie Folgendes verwenden:  `@param {type} name <Parameter Description>`
Alternativ können Sie Folgendes verwenden:  `@argument` `{type} name <Parameter Description>` **oder** `@arg` `{type}` `name <Parameter Description>`.
Zeigt die von der Funktion verwendeten Parameter an. In einer Funktion können mehrere Parameter-Tags vorhanden sein (je ein Tag für jeden Parameter in der Reihenfolge ihres Auftretens). 
   `{type}` stellt den Parametertyp dar. Zugelassene Parametertypen sind: 

   1. Zeichenfolge
   1. number
   1. Boolesch

   Alle anderen Parametertypen fallen in eine der oben genannten Kategorien.  „None“ wird nicht unterstützt. Achten Sie darauf, einen der oben genannten Typen zu wählen. Für die Typen wird nicht zwischen Groß- und Kleinschreibung unterschieden. Leerzeichen sind im Parameter `name` nicht zulässig. `<Parameter Descrption>` `<parameter>  can have multiple words. </parameter>`

* **Return**
TypeSyntax: Alternativ können Sie  `@return {type}`
als Alternative  `@returns {type}`verwenden.
Fügt Informationen zur Funktion hinzu, z. B. ihren Zweck.
{type} stellt den Rückgabetyp der Funktion dar. Zugelassene Rückgabetypen sind: 

   1. Zeichenfolge
   1. number
   1. Boolesch

   Alle anderen Rückgabetypen fallen in eine der oben genannten Kategorien.  „None“ wird nicht unterstützt. Achten Sie darauf, einen der oben genannten Typen zu wählen. Für Rückgabetypen wird nicht zwischen Groß- und Kleinschreibung unterschieden.

>[!NOTE]
>
>Kommentare vor benutzerdefinierten Funktionen werden für die Zusammenfassung verwendet. Die Zusammenfassung kann sich über mehrere Zeilen bis zum nächsten Tag erstrecken. Beschränken Sie ihre Länge auf eine einzelne Zeile, um eine knappe Beschreibung im Regel-Builder zu erhalten.

**Hinzufügen einer benutzerdefinierten Funktion**

Angenommen, Sie möchten eine benutzerdefinierte Funktion zur Berechnung der Fläche eines Quadrats hinzufügen. Die Seitenlänge ist der vom Benutzer eingegebene Wert für die benutzerdefinierte Funktion. Dieser Wert wird in ein Zahlenfeld im Formular eingegeben. Die berechnete Ausgabe wird in einem anderen Zahlenfeld im Formular angezeigt. Um eine benutzerdefinierte Funktionen hinzuzufügen, müssen Sie zuerst eine Client-Bibliothek erstellen und diese anschließend dem CRX-Repository hinzufügen.

Führen Sie die folgenden Schritte aus, um eine Client-Bibliothek zu erstellen und sie dem CRX-Repository hinzuzufügen:

1. Erstellen Sie eine Client-Bibliothek. Weitere Informationen finden Sie unter [Verwenden clientseitiger Bibliotheken](/help/sites-developing/clientlibs.md).
1. Fügen Sie in CRXDE eine Eigenschaft `categories`mit dem Zeichenfolgentyp value `customfunction` zum Ordner `clientlib` hinzu.

   >[!NOTE]
   >
   >`customfunction`ist eine Beispielkategorie. Sie können einen beliebigen Namen für die Kategorie wählen, die Sie im Ordner `clientlib` erstellen.

Nachdem Sie die Client-Bibliothek im CRX-Repository hinzugefügt haben, verwenden Sie sie in Ihrem adaptiven Formular. Sie ermöglicht die Verwendung der benutzerdefinierten Funktion als Regel im Formular. Führen Sie die folgenden Schritte aus, um die Client-Bibliothek zu Ihrem adaptiven Formular hinzuzufügen.

1. Öffnen Sie das Formular im Bearbeitungsmodus.
Um ein Formular im Bearbeitungsmodus zu öffnen, wählen Sie ein Formular aus und tippen Sie auf **Öffnen**.
1. Wählen Sie im Bearbeitungsmodus eine Komponente aus, tippen Sie auf ![Feldebene](assets/field-level.png) > **Container für adaptive Formulare** und tippen Sie dann auf ![cmppr](assets/cmppr.png).
1. Fügen Sie in der Seitenleiste unter „Name der Client-Bibliothek“ Ihre Client-Bibliothek hinzu. ( `customfunction` im Beispiel)

   ![Benutzerdefinierte Client-Bibliothek für Funktion](assets/clientlib.png)

1. Wählen Sie das numerische Eingabefeld aus und tippen Sie auf ![edit-rules](assets/edit-rules.png), um den Regeleditor zu öffnen.
1. Tippen Sie auf **Regel erstellen**. Erstellen Sie mithilfe der unten gezeigten Optionen eine Regel zum Speichern des quadrierten Eingabewerts im Ausgabefeld des Formulars.
   [ ![Verwenden benutzerdefinierter Funktionen zum Erstellen einer ](assets/add_custom_rule_new.png)](assets/add-custom-rule.png)RegelTippen Sie auf  **Fertig**. Ihre benutzerdefinierte Funktion wird hinzugefügt.

#### Unterstützte Typen für Funktionsdeklarationen {#function-declaration-supported-types}

**Funktionsanweisung**

```javascript
function area(len) {
    return len*len;
}
```

Diese Funktion wird ohne `jsdoc`-Kommentare einbezogen.

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

Einschränkung: Die benutzerdefinierte Funktion wählt nur die erste Funktionsdeklaration aus der Variablenliste, wenn zusammen verwendet. Der Funktionsausdruck kann für jede deklarierte Funktion verwendet werden.

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
>Stellen Sie sicher, dass Sie `jsdoc` für jede benutzerdefinierte Funktion verwenden. Obwohl `jsdoc`-Kommentare empfohlen werden, sollten Sie bei Bedarf einen leeren `jsdoc`-Kommentar einbeziehen, um eine Funktion als benutzerdefinierte Funktion zu markieren. Dies ermöglicht eine standardmäßige Behandlung Ihrer benutzerdefinierten Funktion.

## Regeln verwalten {#manage-rules}

Alle vorhandenen Regeln für ein Formularobjekt werden aufgelistet, wenn Sie auf das Objekt tippen und auf ![edit-rules1](assets/edit-rules1.png) tippen. Sie können den Titel und eine Vorschau der Regelübersicht anzeigen. Darüber hinaus können Sie in der Benutzeroberfläche die vollständige Regelübersicht erweitern und anzeigen, die Reihenfolge der Regeln ändern, Regeln bearbeiten und Regeln löschen.

![list-rules](assets/list-rules.png)

Sie können die folgenden Aktionen für Regeln durchführen:

* **Anzeigen/Reduzieren**:Die Inhaltsspalte in der Regelliste zeigt den Regelinhalt an. Wenn der gesamte Regelinhalt nicht in der Standardansicht sichtbar ist, tippen Sie auf ![expand-rule-content](assets/expand-rule-content.png) , um ihn zu erweitern.

* **Neuanordnung**: Jede neue Regel, die Sie erstellen, wird am unteren Ende der Regelliste eingefügt. Die Regeln werden in der Reihenfolge von oben nach unten ausgeführt. Dabei wird zuerst die Regel ganz oben in der Liste ausgeführt, darauf folgen andere Regeln desselben Typs. Wenn beispielsweise eine Wenn-, Anzeigen-, Aktivieren- und eine weitere Wenn-Regel an den ersten vier Positionen der Liste stehen, werden zuerst die zuoberst stehende Wenn-Regel und dann die Wenn-Regel an vierter Stelle ausgeführt. Danach werden die Anzeigen- und die Aktivieren-Regel ausgeführt.
Sie können die Reihenfolge einer Regel ändern, indem Sie auf ![Sortierregeln](assets/sort-rules.png) tippen oder sie in die gewünschte Reihenfolge in der Liste ziehen.

* **Bearbeiten**: Zum Bearbeiten einer Regel aktivieren Sie das Kontrollkästchen neben ihrem Titel. Weitere Optionen zum Bearbeiten und Löschen der Regel werden angezeigt. Tippen Sie auf **Bearbeiten** , um die ausgewählte Regel im Regeleditor im Visual Editor- oder Codeeditormodus zu öffnen, je nach dem Modus, der zum Erstellen der Regel verwendet wird.

* **Löschen**: Um eine Regel zu löschen, wählen Sie die Regel aus und tippen Sie auf  **Löschen**.

* **Aktivieren/Deaktivieren:** Möglicherweise müssen Sie eine Regel vorübergehend aussetzen. Sie können eine oder mehrere Regeln auswählen und in der Aktionssymbolleiste auf „Deaktivieren“ tippen, um sie zu deaktivieren. Wenn eine Regel deaktiviert ist, wird sie zur Laufzeit nicht ausgeführt. Um eine Regel zu aktivieren, die deaktiviert ist, können Sie sie auswählen und auf „Aktivieren“ in der Symbolleiste „Aktionen“ tippen. Die Statusspalte für die Regel zeigt an, ob diese aktiviert oder deaktiviert ist.

![disablerrule](assets/disablerule.png)

## Regeln und einfügen {#copy-paste-rules}

Es ist möglich, Regeln aus einem Feld zu kopieren und in andere, ähnliche Felder einzufügen, um Zeit zu sparen.

Gehen Sie zum Kopieren und Einfügen von Regeln wie folgt vor:

1. Tippen Sie auf das Formularobjekt, aus dem Sie eine Regel kopieren möchten, und tippen Sie in der Komponentensymbolleiste auf ![editrule](assets/editrule.png). Die Benutzeroberfläche des Regeleditors wird angezeigt, wobei das Formularobjekt ausgewählt ist und die vorhandenen Regeln angezeigt werden.

   ![copyrule](assets/copyrule.png)

   Weitere Informationen zum Verwalten vorhandener Regeln finden Sie unter [Regeln verwalten](../../forms/using/rule-editor.md#p-manage-rules-p).

1. Aktivieren Sie das Kontrollkästchen neben dem Titel der Regel. Weitere Optionen zum Verwalten der Regel werden angezeigt. Tippen Sie auf **Kopieren**.

   ![copyrule2](assets/copyrule2.png)

1. Wählen Sie ein anderes Formularobjekt aus, in das Sie die Regel einfügen möchten, und tippen Sie auf **Einfügen**. Sie können die Regel darüber hinaus bearbeiten, um Änderungen daran vorzunehmen.

   >[!NOTE]
   >
   >Sie können Regeln nur dann in ein anderes Formularobjekt einfügen, wenn das Zielobjekt das Ereignis der kopierten Regel unterstützt. So unterstützt beispielsweise eine Schaltfläche das Klickereignis. Sie können eine Regel, die ein Klickereignis enthält, in eine Schaltfläche, nicht jedoch in ein Kontrollkästchen einfügen.

1. Tippen Sie auf **Fertig**, um die Regel zu speichern.

## Eingebettete Ausdrücke {#nestedexpressions}

Im Regeleditor können Sie mehrere UND- und ODER-Operatoren verwenden, um eingebettete Regeln zu erstellen. Sie können mehrere UND- und ODER-Operatoren in Regeln kombinieren.

Das folgende Beispiel zeigt eine eingebettete Regel, die dem Benutzer eine Meldung über den Anspruch auf das Sorgerecht für ein Kind anzeigt, wenn die entsprechenden Bedingungen erfüllt sind.

![Komplexausdruck](assets/complexexpression.png)

Sie können auch die Bedingung per Drag &amp; Drop innerhalb einer Regel zum Bearbeiten ziehen. Tippen und bewegen Sie den Mauszeiger über den Griff ( ![handle](assets/handle.png)) vor einer Bedingung. Nachdem der Cursor in ein Handsymbol konvertiert wird, wie unten gezeigt, ziehen Sie die Bedingung an eine beliebige Stelle in der Regel. Die Regelstruktur ändert sich.

![Drag &amp; Drop](assets/drag-and-drop.png)

## Bedingungen für den Datumsausdruck {#dateexpression}

Im Regeleditor können Sie Datenvergleiche verwenden, um Bedingungen zu erstellen.

Im Folgenden finden Sie eine Beispielbedingung, die ein statisches Textobjekt anzeigt, wenn die Hypothek für das Haus bereits aufgenommen wurde, was der Benutzer durch Ausfüllen des Datumsfelds angibt.

Wenn das Datum der Hypothek, das vom Benutzer ausgefüllt wurde, in der Vergangenheit liegt, wird im adaptiven Formular ein Hinweis über die Einkommensberechnung angezeigt.  Die folgende Regel vergleicht das Datum, das vom Benutzer ausgefüllt wurde, mit dem aktuellen Datum, und wenn das Datum, das vom Benutzer ausgefüllt wurde, vor dem aktuellen Datum liegt, dann zeigt das Formular die Textmeldung (benanntes Einkommen) an.

![dateexpressionCondition](assets/dateexpressioncondition.png)

Wenn das ausgefüllte Datum früher als das aktuelle Datum ist, zeigt das Formular die Textmeldung (Einkommen) aus, wie hier gezeigt:

![dateexpressionConditionmet](assets/dateexpressionconditionmet.png)

## Bedingungen zum Zahlenvergleich {#number-comparison-conditions}

Im Regeleditor können Sie Bedingungen erstellen, die zwei Zahlen vergleichen.

Im Folgenden finden Sie eine Beispielbedingung, die ein statisches Textobjekt anzeigt, wenn die Anzahl der Monate, in denen sich ein Antragsteller in seiner aktuellen Adresse befindet, unter 36 liegt.

![numberComparisoncondition](assets/numbercomparisoncondition.png)

Wenn der Benutzer angibt, dass er unter seiner derzeitigen Adresse weniger als 36 Monate gewohnt hat, wird im Formular ein Hinweis angezeigt, dass ein zusätzlicher Aufenthaltsnachweis erforderlich ist.

![additionalproofrequent](assets/additionalproofrequested.png)

## Einfluss des Regeleditors auf vorhandene Skripte {#impact-of-rule-editor-on-existing-scripts}

In Versionen von AEM Forms vor Version AEM 6.1 Forms Feature Pack 1 schrieben Formularverfasser und Entwickler Ausdrücke auf der Registerkarte „Skripte“ im Dialogfeld „Komponente bearbeiten“, um adaptiven Formularen dynamisches Verhalten hinzuzufügen. Die Registerkarte „Skripte“ wird nun durch den Regeleditor ersetzt.

Alle Skripts oder Ausdrücke, die Sie in die Registerkarte „Skripte“ geschrieben haben, sind im Regeleditor verfügbar. Sie können sie zwar nicht im Visual Editor anzeigen oder bearbeiten, aber wenn Sie Teil der Gruppe der Formular-Hauptbenutzer sind, können Sie Skripte im Code-Editor bearbeiten.

## Beispielregeln {#example}

### Formulardatenmodelldienst aufrufen {#invoke}

Denken Sie an einen Webdienst`GetInterestRates` , , der Darlehensbetrag, Amtszeit und den Kredit-Score des Antragstellers als Eingabe verwendet und einen Darlehensplan einschließlich EMI-Menge und Zinssatz zurückgibt. Sie erstellen ein Formulardatenmodell, indem Sie den Web-Dienst als Datenquelle verwenden. Sie fügen dem Formularmodell Datenmodellobjekte und einen `get`-Dienst hinzu. Der Dienst erscheint auf der Registerkarte „Dienste“ des Formulardatenmodells. Anschließend erstellen Sie ein adaptives Formular, das Felder aus Datenmodellobjekten enthält, um Benutzereingaben für Darlehensbetrag, Amtsdauer und Kreditwürdigkeit zu erfassen. Fügen Sie eine Schaltfläche hinzu, die den Web-Dienst auslöst, um Plandetails abzurufen. Die Ausgabe wird in die entsprechenden Felder befüllt.

Die folgende Regel zeigt, wie Sie die Aktion „Dienst aufrufen“ konfigurieren, um das Beispielszenario durchzuführen.

![example-invoke-services](assets/example-invoke-services.png)

Formulardatenmodelldienst mit Regel für adaptives Formular aufrufen

### Auslösen mehrerer Aktionen mithilfe einer Wenn-Regel  {#triggering-multiple-actions-using-the-when-rule}

Angenommen, in einem Kreditantragsformular soll angegeben werden, ob der Antragsteller ein bestehender Kunde ist oder nicht. Das Feld für die Kunden-ID soll basierend auf den vom Benutzer angegebenen Informationen angezeigt oder ausgeblendet werden. Darüber hinaus soll der Fokus auf das Kunden-ID-Feld gelegt werden, wenn der Benutzer ein bestehender Kunde ist. Das Antragsformular umfasst die folgenden Komponenten:

* Ein Optionsfeld: **Sind Sie bereits Geometrixx-Kunde?** mit den Optionen „Ja“ und „Nein“. Der Wert für „Ja“ ist **0** und der Wert „Nein“ ist **1**.

* Das Textfeld **Geometrixx-Kunde-ID** zur Angabe der Kunden-ID.

Wenn Sie eine Wenn-Regel für das Optionsfeld schreiben, um dieses Verhalten zu implementieren, wird die Regel wie folgt im visuellen Regeleditor angezeigt.  ![when-rule-example](assets/when-rule-example.png)

Regel im Visual Editor

In der Beispielregel ist die Anweisung im Wenn-Abschnitt die Bedingung. Wenn diese „True“ zurückgibt, werden die im Dann-Abschnitt angegebenen Aktionen ausgeführt.

Die Regel wird wie folgt im Codeeditor angezeigt.

![when-rule-example-code](assets/when-rule-example-code.png)

Regel im Codeeditor

### Verwenden einer Funktionsausgabe in einer Regel  {#using-a-function-output-in-a-rule}

Ein Bestellformular enthält die folgende Tabelle, in der die Benutzer ihre Bestellungen eingeben. In dieser Tabelle gilt:

* Die erste Zeile ist wiederholbar, sodass die Benutzer mehrere Produkte bestellen und unterschiedliche Mengen angeben können. Der Elementname lautet `Row1`.
* Der Titel der Zelle in der Spalte „Produktmenge“ der wiederholbaren Zelle ist „Menge“. Der Elementname für diese Zelle ist `productquantity`.
* Die zweite Zeile der Tabelle ist nicht-wiederholbar und der Titel der Zelle in der Spalte „Produktmenge“ in dieser Zelle ist „Menge insgesamt“.

![example-function-table](assets/example-function-table.png)

**A.** Zeile1  **B.** Menge  **C.** Menge insgesamt

Als Nächstes sollen die in der Spalte „Produktmenge“ angegebenen Mengen für alle Produkte addiert und die Summe in der Zelle „Menge insgesamt“ angezeigt werden. Dies erreichen Sie, indem Sie wie unten gezeigt eine Regel des Typs „Wert einstellen“ für die Zelle „Menge insgesamt“ schreiben.

![example-function-output](assets/example-function-output.png)

Regel im Visual Editor

Die Regel wird wie folgt im Codeeditor angezeigt.

![example-function-output-code](assets/example-function-output-code.png)

Regel im Codeeditor

### Validieren eines Feldwerts mithilfe eines Ausdrucks  {#validating-a-field-value-using-expression}

Sie möchten in dem im vorherigen Abschnitt erläuterten Bestellformular verhindern, dass Benutzer mehr als 1 Einheit von Produkten mit einem Preis über 10.000 bestellen. Um dies zu erreichen, können Sie wie unten gezeigt eine Validierungsregel schreiben.

![example-validate](assets/example-validate.png)

Regel im Visual Editor

Die Regel wird wie folgt im Codeeditor angezeigt.

![example-validate-code](assets/example-validate-code.png)

Regel im Codeeditor
