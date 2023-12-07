---
title: Formularsatz in AEM Forms
description: In diesem Artikel erhalten Sie eine Einführung in Formularsätze und deren Erstellung durch Zusammenfügen von HTML5-Formularen. In diesem Artikel wird auch erläutert, wie Sie XML-Daten in einen Formularsatz vorab ausfüllen können und wie Sie Formularsätze in der Prozessverwaltung verwenden können.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: Mobile Forms
exl-id: 039afdf3-013b-41b2-8821-664d28617f61
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '2804'
ht-degree: 40%

---

# Formularsatz in AEM Forms{#form-set-in-aem-forms}

## Übersicht {#overview}

Ihre Kunden müssen oft mehrere Formulare senden, um sich bei einem Dienst oder anzumelden. Dazu gehört die Suche aller relevanter Formular sowie das Ausfüllen und Nachverfolgen. Außerdem müssen sie allgemeine Details mehrmals in allen Formularen ausfüllen. Der gesamte Prozess wird schwerfällig und fehleranfällig, wenn er eine große Anzahl von Formularen umfasst. Die Formularsatzfunktion von AEM Forms kann dazu beitragen, das Benutzererlebnis in solchen Fällen zu vereinfachen.

Ein Formularsatz ist eine Sammlung von HTML5 Formularen, die gruppiert sind und Endbenutzern als ein Formularsatz präsentiert werden. Wenn der Benutzer ein Formularsatz ausfüllt, werden diese Informationen von einem Formular zu einem anderen übertragen. Am Ende können sie alle Formulare mit nur einem Klick senden.

AEM Forms bietet Formularverfassern eine intuitive Benutzeroberfläche zum Erstellen, Konfigurieren und Verwalten von Formularsätzen. Als Autor können Sie Formulare in einer bestimmten Reihenfolge anfordern, in der Endanwender sie ausfüllen sollen. Sie können auch Bedingungen oder Berechtigungsausdrücke in einzelnen Formularen verwenden, um ihre Sichtbarkeit aufgrund Benutzereingaben zu steuern. Beispielsweise können Sie das Formular für die Ehedetails so konfigurieren, dass es nur angezeigt wird, wenn der Familienstand als &quot;Verheiratet&quot;angegeben ist.

Darüber hinaus können Sie gemeinsame Felder in verschiedenen Formularen konfigurieren, um gemeinsame Datenbindungen vorzunehmen. Wenn geeignete Datenbindungen vorhanden sind, müssen Endbenutzer allgemeine Informationen nur einmal ausfüllen. Diese werden dann in nachfolgenden Formularen automatisch ausgefüllt.

Formularsätze werden auch in der AEM Forms-App unterstützt, sodass Ihre Außendienstmitarbeiter einen Formularsatz offline bearbeiten, Kunden besuchen, Daten eingeben und später mit dem AEM Forms-Server synchronisieren können, um Formulardaten an Geschäftsprozesse zu senden.

## Formularsatz erstellen und verwalten {#creating-and-managing-form-set}

Sie können mehrere XDPs oder Formularvorlagen, die unter Verwendung von Designer erstellt wurden, in einen Formularsatz zuordnen. Formularsätze können dann selektiv verwendet werden, um die XDPs zu rendern, basierend auf den Werten, die von den Benutzern in den anfänglichen Formularen und deren Profilen eingegeben wurden.

Verwenden Sie die [AEM Forms-Benutzeroberfläche](../../forms/using/introduction-managing-forms.md), um alle Formulare, Formularsätze und zugehörigen Assets zu verwalten.

### Formularsatz erstellen {#create-a-form-set}

Gehen Sie wie folgt vor, um einen Formularsatz zu erstellen:

1. Wählen Sie Forms > Forms und Dokumente aus.
1. Klicken Sie auf „Erstellen“ > „Formularsatz“. 

1. Fügen Sie auf der Seite Eigenschaften hinzufügen die folgenden Details hinzu und klicken Sie auf Weiter.

   * Titel: Geben Sie den Titel des Dokuments an. Der Titel erleichtert Ihnen die Identifizierung des Formularsatzes in der Benutzeroberfläche von AEM Forms.
   * Beschreibung: Geben Sie detaillierte Informationen zum Dokument an.
   * Tags: Gibt Tags an, mit denen der Formularsatz eindeutig identifiziert werden kann. Tags helfen bei der Suche nach dem Formularsatz. Um die Tags zu erstellen, geben Sie neue Tag-Namen in das Feld Tags ein.
   * Übermittlungs-URL: URL, unter der die übermittelten Daten bei eigenständiger Ausgabedarstellung eines Formularsatzes veröffentlicht werden (Anwendungsfall ohne AEM Forms -App). Die Daten werden als mehrteilige Formulardaten mit folgendem Anforderungsparameter an diesen Endpunkt gesendet:
   * dataXML: Dieser Parameter enthält eine XML-Darstellung der gesendeten Formularsatzdaten. Wenn alle Formulare im Formularsatz ein gemeinsames Schema verwenden, wird die XML gemäß diesem Schema generiert. Andernfalls enthält der XML-Stamm-Tag einen untergeordneten Tag für jedes ausgefüllte Formular im Formularsatz, das Daten für die Formularanlagen enthält.
   * formsetPath: Der Pfad des Formularsatzes in CRXDE, der gesendet wurde.
   * HTML Render Profile: Sie können bestimmte Optionen wie schwebende Felder, Anlagen und Entwurfsunterstützung konfigurieren (für eigenständige Formularsatzwiedergabe), um Erscheinungsbild, Verhalten und Interaktionen des Formularsatzes anzupassen. Sie können das bestehende Profil anpassen oder erweitern, um alle HTML Form-Profileinstellungen zu ändern.

   ![Formularsatz: Eigenschaften hinzufügen](assets/createformset1.png)

1. Im Bildschirm &quot;Formular(e) auswählen&quot;werden die verfügbaren XDP-Formulare oder XDP-Dateien angezeigt. Suchen Sie nach den Formularen, die Sie den Formularsatz aufnehmen möchten, wählen Sie sie aus und klicken Sie auf „Zum Formularsatz hinzufügen“. Suchen Sie nötigenfalls nach weiteren hinzuzufügenden Formularen. Nachdem Sie alle Formulare zum Formularsatz hinzugefügt haben, klicken Sie auf Weiter.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass die Feldnamen in den XDP-Formularen keinen Punkt enthalten. Andernfalls können die Skripte, die versuchen, die Felder zu beheben, in denen Punkte enthalten sind, diese nicht beheben.

1. Auf der Seite „Formular(e) konfigurieren“ haben Sie folgende Möglichkeiten:

   * Reihenfolge der Formulare: Ziehen Sie die Formulare per Drag&amp;Drop, um die Anordnung zu ändern. Dieses Formular definiert die Reihenfolge, in der die Formulare dem Endbenutzer in der AEM Forms-App und in der eigenständigen Ausgabedarstellung angezeigt werden.
   * Formular-ID: Gibt eine eindeutige Identität für die Formulare an, die in Berechtigungsausdrücken verwendet werden sollen.
   * Datenstamm: Der Autor kann für jedes Formular im Formularsatz den XPATH konfigurieren, in dem sich die Daten dieses bestimmten Formulars in der gesendeten XML befinden. Standardmäßig ist der Wert „/“. Wenn alle Formulare im Formularsatz schemagebunden sind und dasselbe XML-Schema nutzen, können Sie diesen Wert ändern. Es wird empfohlen, für jedes Feld im Formular eine ordnungsgemäße Datenbindung in der XDP-Datei anzugeben. Wenn zwei Felder in zwei verschiedenen Formularen die gemeinsame Datenbindung teilen, zeigt das Feld im zweiten Formular vorausgefüllte Werte aus dem ersten Formular an. Binden Sie nicht zwei Teilformulare mit demselben internen Inhalt an denselben XML-Knoten. Weitere Informationen zur XML-Struktur von Formularsätzen finden Sie unter [Vorausfüllen von XML für Formularsätze](../../forms/using/formset-in-aem-forms.md#p-prefill-xml-for-form-set-p).
   * Berechtigungsausdruck: Gibt einen JavaScript-Ausdruck an, der einen booleschen Wert auswertet und angibt, ob ein Formular im Formularsatz ausgefüllt werden darf. Wenn dies „false“ ist, wird der Benutzer nicht gefragt und es wird ihm auch nicht das Formular zum Ausfüllen angezeigt. Der Ausdruck basiert normalerweise auf den Werten der Felder, die in den diesem Formular vorangehenden Formularen erfasst werden. Ausdrücke enthalten auch Aufrufe der Formularsatz-API fs.valueOf, um die vom Benutzer in einem Feld eines Formulars im Formularsatz eingegebenen Werte zu extrahieren:

   *fs.valueOf(&lt;Formularkennung>, &lt;fieldSom-Ausdruck>) > &lt;Wert>*

   Wenn Sie beispielsweise zwei Formulare im Formularsatz haben: Geschäftsausgaben und Reisekosten, können Sie im Feld Berechtigungsausdruck ein JavaScript-Snippet hinzufügen, damit beide Formulare die Benutzereingabe auf Kosten in einem Formular überprüfen können. Wenn der Benutzer Geschäftsausgaben wählt, wird das Formular „Geschäftsausgaben“ für den Endbenutzer gerendert. Wenn der Benutzer „Reisekosten“ wählt, wird ein anderes Formular gerendert und angezeigt. Weitere Informationen finden Sie unter „Berechtigungsausdruck“.

   Darüber hinaus kann der Verfasser ein Formular mithilfe des Löschsymbols am rechten Ende jeder Zeile aus dem Formularsatz entfernen oder einen weiteren Formularsatz mit der Funktion **+**&#39; in der Symbolleiste. Dies **+** Das Symbol &quot; leitet den Benutzer zurück zum vorherigen Schritt im Assistenten, der zum Auswählen von Formularen verwendet wurde.&quot; Die vorhandenen Auswahlmöglichkeiten bleiben erhalten und alle zusätzlichen Auswahlmöglichkeiten müssen dem Formularsatz über das Symbol &quot;Zum Formularsatz hinzufügen&quot;auf dieser Seite hinzugefügt werden.

   ![Formularsatz: Formular(e) konfigurieren](assets/createformset2.png)

   >[!NOTE]
   >
   >Alle Formulare, die in Formularsätzen verwendet werden, werden von der Benutzeroberfläche von AEM Forms verwaltet.

### Formularsatz verwalten {#managing-a-form-set}

Nachdem ein Formularsatz erstellt wurde, können Sie folgende Aktionen für diesen Formularsatz durchführen:

* Einfaches Klicken: Wenn der Formularsatz erstellt wurde und auf der Asset-Hauptseite angezeigt wird, können Sie ihn durch einfaches Klicken anzeigen. Ein Formularsatz wird geöffnet und alle darin enthaltenen Formularvorlagen (XDPs) werden angezeigt.
* Bearbeiten: Wenn Sie einen Formularsatz auswählen und anschließend auf „Bearbeiten“ klicken, wird der oben unter „Schritte zum Erstellen eines Formularsatzes“ gezeigte Bildschirm „Formular(e) konfigurieren“ geöffnet. Sie können alle hier beschriebenen Funktionen ausführen.
* Kopieren und Einfügen: Mithilfe dieser Funktion können Sie den gesamten Formularsatz von einem Speicherort kopieren und am gewünschten Speicherort bzw. Ordner einfügen.
* Herunterladen: Sie können den Formularsatz mit allen seinen Abhängigkeiten herunterladen.
* Prüfung starten/verwalten: Nachdem der Formularsatz erstellt wurde, können Sie dessen Überprüfung durch Klicken auf das Symbol zum Starten einer Überprüfung einrichten. Sobald die Überprüfung für einen Formularsatz gestartet wurde, wird die Option zum Verwalten der Überprüfung angezeigt. Im Bildschirm zum Verwalten einer Überprüfung können Sie diese aktualisieren oder beenden. Für die von Ihnen hinzugefügten Überprüfungen können Sie die Überprüfung prüfen und bei Bedarf Kommentare hinzufügen.
* Löschen: Löscht den vollständigen Formularsatz. Die Formulare im gelöschten Formularsatz verbleiben im Repository.
* Veröffentlichen/Veröffentlichung rückgängig machen: Dadurch wird der Formularsatz zusammen mit allen darin enthaltenen Formularen und den zugehörigen Assets dieser Formulare veröffentlicht bzw. dessen Veröffentlichung rückgängig gemacht.
* Vorschau: Die Vorschau bietet zwei Optionen: Vorschau als HTML (ohne Daten) und benutzerdefinierte Vorschau mit Beispieldaten.
* Eigenschaften anzeigen/bearbeiten: Sie können die Metadateneigenschaften eines ausgewählten Formularsatzes anzeigen/bearbeiten.

![createformset3](assets/createformset3.png)

### Formularsatz bearbeiten {#edit-a-form-set}

Gehen Sie wie folgt vor, um Formularsätze zu bearbeiten:

1. Wählen Sie Forms > Forms und Dokumente aus.
1. Suchen Sie den Formularsatz, den Sie bearbeiten möchten. Bewegen Sie den Cursor darüber und wählen Sie „Bearbeiten“ ( ![editicon](assets/editicon.png)).
1. Auf der Seite „Formular(e) konfigurieren“ können Sie Folgendes bearbeiten:

   * Formular-Reihenfolge 
   * Formularkennung
   * Datenstamm
   * Berechtigungsausdruck

   Sie können auch auf das entsprechende Symbol Löschen klicken, um das Formular aus dem Formularsatz zu löschen.

## Formularsätze in der Prozessverwaltung {#form-set-in-process-management}

Nachdem Sie einen Formularsatz in der Benutzeroberfläche von AEM Forms Management erstellt haben, können Sie ihn in Workbench in der Aktivität &quot;Ausgangspunkt&quot;oder &quot;Aufgabe zuweisen&quot;verwenden.

### Verwenden des Formularsatzes im Aufgaben- oder Ausgangspunkt {#using-form-set-in-task-or-start-point}

1. Wählen Sie beim Entwickeln eines Prozesses im Bereich „Präsentation und Daten“ von „Ausgangspunkt“ bzw. „Aufgabe zuweisen“ die Option zum **Verwenden eines CRX-Assets**. Der Browser für CRX-Assets wird angezeigt.

   ![Entwickeln eines Prozesses: Ein CRX-Element verwenden](assets/formsetinprocessmgmt1.png)

1. Wählen Sie den Formularsatz, um den Formularsatz im AEM-Repository (CRX) zu filtern.

   ![Entwickeln eines Prozesses: Dialogfeld „Formularelement“ wählen.](assets/formsetinprocessmgmt2.png)

1. Wählen Sie einen Formularsatz aus und klicken Sie auf „OK“.

## Berechtigungsausdrücke {#eligibility-expressions}

Mithilfe von Berechtigungsausdrücken können Sie die Formulare, die für bestimmte Benutzer angezeigt werden sollen, definieren und dynamisch steuern. So können Sie beispielsweise festlegen, dass ein bestimmtes Formular nur für Benutzer angezeigt werden soll, die zu einer bestimmten Altersgruppe gehören. Geben Sie einen Berechtigungsausdruck mithilfe von Forms Manager an und bearbeiten Sie ihn.

Ein Berechtigungsausdruck kann jede gültige JavaScript-Anweisung sein, die einen booleschen Wert zurückgibt. Die letzte Anweisung im JavaScript-Codefragment wird als boolescher Wert behandelt, der die Berechtigung des Formulars anhand der Verarbeitung im Rest (vorherige Zeilen) des JavaScript-Codeausschnitts bestimmt. Wenn der Wert des Ausdrucks „wahr“ ist, bedeutet dies, dass das Formular für den Benutzer angezeigt werden soll. Solche Formulare werden als geeignete Formulare bezeichnet.

>[!NOTE]
>
>Der Berechtigungsausdruck für das erste Formular im Formularsatz wird nicht ausgeführt. Das erste Formular wird unabhängig vom Berechtigungsausdruck immer angezeigt.

Neben der normalen JavaScript-Funktion wird im Formularsatz die fs.valueOf-API genutzt, die Zugriff auf den Wert eines Formularfelds in einem Formularsatz bietet. Verwenden Sie diese API, um auf den Wert eines Formularfelds in einem Formularsatz zuzugreifen. Die API-Syntax lautet fs.valueOf (formUid, fieldSOM), wobei:

* formUid (String): Eine eindeutiger ID eines Formulars im Formularsatz. Sie können dies beim Erstellen des Formularsatzes in der Benutzeroberfläche von Forms Manager angeben. Standardmäßig ist dies der Name des Formulars.
* fieldSOM (string): Ein SOM-Ausdruck des Felds im durch formUid angegebenen Formular. SOM-Ausdruck- oder Skriptobjekt-Modellausdruck wird verwendet, um die Werte, Eigenschaften und Methoden innerhalb eines bestimmten Dokumentobjektmodells (DOM) zu referenzieren. Sie können es in Form Designer auf der Registerkarte &quot;Skripte&quot;anzeigen, während das Feld ausgewählt ist.

>[!NOTE]
>
>Die Parameter formUid und fieldSOM müssen ein Zeichenfolgenliteral sein.

### Beispiele {#examples}

Gültige Verwendung der API:

`fs.valueOf("form1", "xfa.form.form1.subform1.field1")`

Ungültige Verwendung der API:

```javascript
var formUid = "form1";
 var fieldSOM = "xfa.form.form1.subform1.field1"; fs.valueOf(formUid, fieldSOM);
```

## XML zum Vorausfüllen in Formularsätzen {#prefill-xml-for-form-set}

Ein Formularsatz ist eine Sammlung mehrerer HTML5-Formulare mit einem gemeinsamen oder mehreren unterschiedlichen Schemata. Der Formularsatz unterstützt das Vorausfüllen von Formularfeldern mithilfe einer XML-Datei. Sie können eine XML-Datei mit einem Formularsatz verknüpfen, sodass, wenn Sie ein Formular in einem Formularsatz öffnen, einige der Felder im Formular voraufgefüllt werden.

Das Vorauffüllen einer XML-Datei wird mithilfe des dataRef-Parameters der URL des Formularsatzes angegeben. Der dataRef-Parameter gibt den absoluten Pfad der XML-Datendatei an, die mit dem Formularsatz zusammengeführt wird.

Sie haben beispielsweise drei Formulare (Formular1, Formular2 und Formular3) im Formularsatz mit der folgenden Struktur:

form1

Field form1field

form2

Field form2field

form3

Field form3field

Jedes Formular verfügt über ein Feld mit gemeinsamem Namen namens &quot;Feld&quot;und ein eindeutig benanntes Feld namens &quot;formfield&quot;.

Sie können diesen Formularsatz mithilfe einer XML-Datei mit der folgenden Struktur im Voraus ausfüllen lassen:

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<formSetRootTag>
 <field>common field value</field>
 <form1field>value1</form1field>
 <form2field>value2</form2field>
 <form3field>value3</form3field>
</formSetRootTag>
```

>[!NOTE]
>
>Das XML-Stamm-Tag kann einen beliebigen Namen haben, aber die Element-Tags, die den Feldern entsprechen, müssen denselben Namen wie das Feld haben. Die Hierarchie der XML-Datei muss die Hierarchie des Formulars nachahmen. Das bedeutet, dass die XML-Datei entsprechende Tags für das Eingliedern von Teilformularen haben muss.

Das obige XML-Codefragment zeigt an, dass die XML zum Vorausfüllen des Formularsatzes eine Vereinigung der XML-Codefragmente zum Vorausfüllen der einzelnen Formulare darstellt. Wenn bestimmte Felder in unterschiedlichen Formularen eine ähnliche Datenhierarchie/Schema haben, werden die Felder mit den gleichen Werten vorausgefüllt. In diesem Beispiel werden alle drei Formulare mit dem gleichen Wert für das gemeinsame Datenfeld „Feld“ vorausgefüllt. Dies ist eine einfache Möglichkeit, Daten von einem Formular zum nächsten weiterzuleiten. Dies kann auch erreicht werden, indem die Felder an dasselbe Schema oder dieselbe Datenreferenz gebunden werden. Wenn Sie die Formularsatzdaten basierend auf dem Formularschema trennen möchten. Dies kann durch Angabe des Attributs &quot;data root&quot;des Formulars während der Formularsatzerstellung erreicht werden (der Standardwert ist &quot;/&quot;, der dem Formularsatz-Stamm-Tag zugeordnet ist).

Wenn Sie im vorherigen Beispiel die Datenstämme für die drei Formulare angeben: &quot;/form1&quot;, &quot;/form2&quot;und &quot;/form3&quot;, müssen Sie eine XML zum Vorausfüllen mit der folgenden Struktur verwenden:

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<formSetRootTag>
 <form1>
  <field>field value1</field>
  <form1field>value1</form1field>
 </form1>
 <form2>
  <field>field value2</field>
  <form2field>value2</form2field>
 </form2>
 <form3>
  <field>field value3</field>
  <form3field>value3</form3field>
 </form3>
</formSetRootTag>
```

In einem Formularsatz definierte die XML ein XML-Schema mit der folgenden Syntax:

```xml
<formset>
 <fs_data>
  <xdp:xdp xmlns:xdp="https://ns.adobe.com/xdp/">
  <xfa:datasets xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
   <xfa:data>
   <rootElement>
    ... data ....
   </rootElement>
   </xfa:data>
  </xfa:datasets>
  </xdp:xdp>
 </fs_data>
 <fs_draft>
  ... private data...
 </fs_draft>
</formset>
```

>[!NOTE]
>
>Wenn es zwei Formulare mit überlappenden Datenstämmen gibt oder sich die Elementhierarchie eines Formulars mit der Datenstamm-Hierarchie eines anderen Formulars überschneidet, werden die Werte der überlappenden Elemente in der XML zum Vorausfüllen zusammengeführt. Die Sende-XML weist eine ähnliche Struktur wie die XML zum Vorausfüllen auf, doch die Sende-XML hat mehr Wrapper-Tags und am Ende sind einige Kontextdaten-Tags für Formularsätze angehängt.

### Beschreibung der XML-Elemente vorfüllen {#prefill-xml-elements-description}

Syntaxregeln zum Erstellen einer XML-Datei zum Vorbefüllen:

* Übergeordnete Elemente: Elemente, die dem betreffenden Element übergeordnet sein können, wobei null angibt, dass das Element im Stammverzeichnis der XML-Datei liegen kann.
* Kardinalität: Gibt an, wie oft das Element innerhalb des ihm übergeordneten Elements verwendet werden kann.
* submitXML: Gibt an, ob das Element in der Sende-XML immer vorhanden (P) oder optional (O) ist.
* prefillXML: Gibt an, ob das Element in der XML zum Vorbefüllen erforderlich (R) oder optional (O) ist.
* Untergeordnete Elemente: Gibt an, welche Elemente untergeordnet sein können.

### FORMSET {#formset}

`parent elements:`

`null`

`cardinality: [0,1]`

`submitXML: P`

`prefillXML: O`

`children: fs_data`

Das Stammelement der XML für den Formularsatz. Es wird empfohlen, dieses Wort nicht als Namen des rootSubform-Formulars im Formularsatz zu verwenden.

### FS_DATA {#fs-data}

`parent elements:`

`formset`

Kardinalität: [1]

submitXML: P

prefillXML: O

`children: xdp:xdp/rootElement`

Die Unterstruktur gibt die Daten der Formulare im Formularsatz an. Das Element ist in der XML zum Vorausfüllen nur dann optional, wenn das Formularsatzelement nicht vorhanden ist

### XDP:XDP {#xdp-xdp}

`parent elements: fs_data/null`

`cardinality: [0,1]`

`submitXML: O`

`prefillXML: O`

`children: xfa:datasets`

Dieses Tag gibt den Anfang der XML für das HTML5-Formular an. Dies wird in der Sende-XML hinzugefügt, sofern es in der der XML zum Vorausfüllen angegeben wurde oder diese nicht vorhanden ist. Dieses Tag kann aus der XML zum Vorausfüllen entfernt werden.

### XFA:DATASETS {#xfa-datasets}

`parent elements: xdp:xdp`

`cardinality: [1]`

`submitXML: O`

`prefillXML: O`

`children: xfa:data`

### XFA:DATA {#xfa-data}

`parent elements: xfa:datasets`

`cardinality: [1]`

`submitXML: O`

`prefillXML: O`

`children: rootElement`

### ROOTELEMENT {#rootelement}

`parent elements: xfa:datasets/fs_data/null`

`cardinality: [0,1]`

`submitXML: P`

`prefillXML: O`

`children: controlled by the Forms in Form set`

Der Name „rootElement“ dient hier lediglich als Platzhalter. Der tatsächliche Name wird aus den im Formularsatz verwendeten Formularen übernommen. Die mit dem rootElement beginnende Unterstruktur enthält die Daten aus den Feldern und Unterformularen innerhalb der im Formularsatz enthaltenen Formulare. Es gibt mehrere Faktoren, die die Struktur des rootElement und seiner untergeordneten Elemente bestimmen.

In der XML zum Vorausfüllen ist dieses Tag optional, fehlt es jedoch, wird die gesamte XML ignoriert.

NAME DES STAMMELEMENT-TAGS

Ist in der XML zum Vorausfüllen ein Stammelement vorhanden, wird der Name dieses Elements auch für die Senden-XML übernommen. Falls keine XML zum Vorausfüllen vorhanden ist, wird der Name des Unterformulars auf der Stammebene des ersten Formulars im Formularsatz, dessen dataRoot-Eigenschaft auf „/“ eingestellt wurde, als Name für das rootElement übernommen. Wenn kein solches Formular vorhanden ist, lautet der Name des rootElement . **fs_dummy_root**, ein reserviertes Keyword.

## Formularsatz in der AEM Forms-App {#formset-in-workspace-app}

Die AEM Forms-App ermöglicht es Außendienstmitarbeitern, ihre Mobilgeräte mit einem AEM Forms-Server zu synchronisieren und Aufgaben zu bearbeiten. Die Anwendung funktioniert auch dann, wenn das Gerät offline ist, indem Daten lokal auf dem Gerät gespeichert werden. Mithilfe von Anmerkungsfunktionen wie Fotos können Außendienstmitarbeiter genaue Informationen bereitstellen, die in die Geschäftsprozesse integriert werden können.

<!-- Update link as it is a 404 - For more information on AEM Forms app, see [AEM Forms app overview](/help/forms/using/mobile-workspace-overview.md).-->

## Bekannte Einschränkungen - Muster werden im Formularsatz nicht vollständig unterstützt {#known-limitations-patterns-not-fully-supported-in-form-set}

Die folgenden Datenmuster werden im Formularsatz nicht vollständig unterstützt:

<table>
 <tbody>
  <tr>
   <td><strong>Muster werden nicht vollständig in Formularsätzen unterstützt </strong></td>
   <td><strong>Beispiel</strong></td>
  </tr>
  <tr>
   <td>Nicht übereinstimmende Eingabegröße und Mustergröße</td>
   <td><p>Wenn pattern= num{z,zzz}</p> <p>Und input=</p> <p>12.345 oder</p> <p>1,23</p> </td>
  </tr>
  <tr>
   <td>Muster für Picture-Klausel mit Klammern "(" ")"</td>
   <td>num{(zz,zzz)}</td>
  </tr>
  <tr>
   <td>Mehrere Datenmuster</td>
   <td>num{zz,zzz} | num{z,zzz,zzz}</td>
  </tr>
  <tr>
   <td>Kurzschriftmuster </td>
   <td><p>num.integer{},</p> <p>num.decimal{},</p> <p>num.percent{}oder</p> <p>num.currency{}</p> </td>
  </tr>
 </tbody>
</table>
