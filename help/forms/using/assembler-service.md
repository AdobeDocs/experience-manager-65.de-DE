---
title: Verwenden des Assembler-Dienstes
description: Mit dem Assembler-Dienst können Sie PDF- und XDP-Dokumente kombinieren, neu anordnen und erweitern sowie Informationen zu PDF-Dokumenten erhalten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
docset: aem65
feature: Document Services
exl-id: 84c8125d-0f16-432a-9567-63b868667537
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '2118'
ht-degree: 100%

---

# Verwenden des Assembler-Dienstes{#using-assembler-service}

Mit dem Assembler-Dienst können Sie PDF- und XDP-Dokumente kombinieren, neu anordnen und erweitern sowie Informationen zu PDF-Dokumenten erhalten. Jeder an den Assembler-Dienst übermittelte Auftrag umfasst ein DDX-Dokument (Document Description XML), Quelldokumente und externe Ressourcen (Zeichenfolgen und Grafiken). Weitere Informationen zum Assembler-Dienst finden Sie in der [Übersicht über den Assembler-Dienst](../../forms/using/overview-aem-document-services.md#p-assembler-service-p).

Sie können den Assembler-Dienst für die folgenden Vorgänge verwenden:

## Zusammenstellen von PDF-Dokumenten {#assemble-pdf-documents}

Mithilfe des Assembler-Dienstes können Sie zwei oder mehr PDF-Dokumente zu einem einzigen PDF-Dokument oder PDF-Portfolio zusammenführen. Sie können dem PDF-Dokument auch Funktionen hinzufügen, die die Navigation unterstützen oder die Sicherheit erhöhen. Im Folgenden finden Sie einige Möglichkeiten, wie Sie PDF-Dokumente zusammenführen können:

### Zusammenführen eines einzelnen PDF-Dokuments {#assemble-a-simple-pdf-document}

Die folgende Abbildung zeigt, wie drei Quelldokumente zu einem einzelnen Zieldokument zusammengeführt werden.

![Assemblieren eines einzelnen PDF-Dokuments aus mehreren PDF-Dokumenten](assets/as_document_assembly.png)

Zusammenstellen eines einzelnen PDF-Dokuments aus mehreren PDF-Dokumenten

Das folgende Beispiel macht Gebrauch von einem einfachen DDX-Dokument, das zum Zusammenführen des Dokuments verwendet wird. Es gibt die Namen der Quelldokumente, mit deren Hilfe das Zieldokument generiert werden soll, sowie den Namen des Zieldokuments an.

```xml
<PDF result="Doc4">
<PDF source="Doc1"/>
<PDF source="Doc2"/>
<PDF source="Doc3"/>
</PDF>
```

Die Dokumentzusammenführung erstellt ein Zieldokument mit folgendem Inhalt und folgenden\
Eigenschaften:

* Jedes Quelldokument (vollständig oder teilweise)
* Lesezeichen aller Quelldokumente (vollständig oder teilweise), die für das zusammengeführte Zieldokument normalisiert wurden.
* Andere aus dem Basisdokument (Doc1) übernommene Merkmale, einschließlich Metadaten, Seitenbeschriftungen und Seitengröße.
* Das Zieldokument enthält optional ein Inhaltsverzeichnis, das aus den Lesezeichen in den Quelldokumenten erstellt wird.

### Erstellen eines PDF-Portfolios {#create-a-pdf-portfolio}

Der Assembler-Dienst kann PDF-Portfolios erstellen, die eine Sammlung von Dokumenten und eine in sich geschlossene Benutzeroberfläche enthalten. Die Oberfläche wird als PDF-Portfolio-Layout oder als PDF-Portfolio-Navigator (Navigator) bezeichnet. PDF-Portfolios erweitern die Funktionen von PDF-Paketen durch Hinzufügen eines Navigators sowie von Ordnern und Begrüßungsseiten. Die Oberfläche kann die Benutzererfahrung durch Nutzung von lokalisierten Textzeichenfolgen, benutzerdefinierten Farbschemata und grafischen Ressourcen verbessern. Das PDF-Portfolio kann außerdem Ordner zum Organisieren der Dateien im Portfolio enthalten.

Wenn der Assembler-Dienst das folgende DDX-Dokument interpretiert, führt er ein PDF-Portfolio zusammen, das einen PDF-Portfolio Navigator und ein Paket mit zwei Dateien enthält. Der Dienst ruft den Navigator von dem in der myNavigator-Quelle angegebenen Speicherort ab. Er ändert das standardmäßige Farbschema des Navigators in das pinkScheme-Farbschema.

```xml
<DDX xmlns="https://ns.adobe.com/DDX/1.0/">
<PDF result="Untitled 1">
<Portfolio>
<Navigator source="myNavigator"/>
<ColorScheme scheme="pinkScheme"/>
</Portfolio>
<PackageFiles>
<PDF source="sourcePDF1"/>
<PDF source="sourcePDF2"/>
</PackageFiles>
</PDF>
</DDX>
```

### Zusammenstellen von verschlüsselten Dokumenten {#assemble-encrypted-documents}

Beim Zusammenstellen eines Dokuments kann das PDF-Dokument auch mit einem Kennwort verschlüsselt werden. Nachdem ein PDF-Dokument mit einem Kennwort verschlüsselt wurde, müssen Sie das Kennwort angeben, damit das PDF-Dokument in Adobe Reader oder Acrobat angezeigt werden kann. Zum Verschlüsseln eines PDF-Dokuments mit einem Kennwort muss das DDX-Dokument Verschlüsselungselementwerte enthalten, die für die Verschlüsselung eines PDF-Dokuments erforderlich sind.

Der Verschlüsselungsdienst braucht nicht Bestandteil Ihrer LiveCycle-Installation zu sein, um ein PDF-Dokument mit einem Kennwort verschlüsseln zu können.

Wenn mindestens eines der Eingabedokumente verschlüsselt ist, geben Sie zum Öffnen des Dokuments als Teil des DDX-Dokuments ein Kennwort an.

### Zusammenstellen von Dokumenten mithilfe der Bates-Nummerierung {#assemble-documents-using-bates-numbering}

Beim Zusammenführen eines Dokuments können Sie die Bates-Nummerierung verwenden, um für jede Seite eine eindeutige Seitenkennung zu vergeben. Bei Verwendung der Bates-Nummerierung wird jeder Seite im Dokument (bzw. im Dokumentensatz) eine Zahl zugewiesen, die diese Seite eindeutig identifiziert. Beispielsweise können Fertigungsdokumente, die Materialaufstellungsinformationen enthalten und mit der Herstellung einer Baugruppe verbunden sind, eine Kennung enthalten. Eine Bates-Nummer enthält einen numerischen Wert, der sequenziell inkrementiert wird, sowie ein optionales Präfix und Suffix. Die Abfolge „Präfix + numerischer Wert + Suffix“ wird als Bates-Muster bezeichnet.

Die folgende Illustration zeigt ein PDF-Dokument, das eine eindeutige Kennung enthält, die sich in der Kopfzeile des Dokuments befindet.

![Ein PDF-Dokument, das eine eindeutige Kennung enthält, die sich in der Kopfzeile des Dokuments befindet.](do-not-localize/as_batesnumber.png)

Ein PDF-Dokument, das eine eindeutige Kennung enthält, die sich in der Kopfzeile des Dokuments befindet.

### Reduzieren und Zusammenstellen von Dokumenten {#flatten-and-assemble-documents}

Mit dem Assembler-Dienst können Sie ein interaktives PDF-Dokument (z. B. ein Formular) in ein nicht interaktives PDF-Dokument umwandeln. Mit einem interaktiven PDF-Dokument können Benutzende Daten in die PDF-Dokumentfelder eingeben bzw. darin ändern. Der Prozess der Umwandlung eines interaktiven PDF-Dokuments in ein nicht interaktives PDF-Dokument wird als Reduzieren bezeichnet. Beim Reduzieren eines PDF-Dokuments behalten Formularfelder ihre grafische Darstellung, sind aber nicht mehr interaktiv. Dies kann ein Grund dafür sein, PDF-Dokumente zu reduzieren. Darüber hinaus funktionieren den Feldern zugeordnete Skripte nicht mehr.

Wenn Sie ein PDF-Dokument erstellen, das aus interaktiven PDF-Dokumenten zusammengestellt wurde, reduziert der Assembler-Dienst diese Formulare, bevor er sie in dem Zieldokument zusammenführt.

>[!NOTE]
>
>Der Assembler-Dienst verwendet den Ausgabe-Service zum Reduzieren von dynamischen XFA-Formularen. Wenn der Assembler-Dienst eine DDX-Datei verarbeitet, die die Reduzierung eines dynamischen XFA-Formulars durch den Dienst erfordert, und der Ausgabe-Service nicht verfügbar ist, wird eine Ausnahme ausgelöst. Der Assembler-Dienst kann ein Acrobat-Formular oder ein statisches XFA-Formular reduzieren, ohne den Ausgabe-Service zu verwenden.

## Zusammenführen von XDP-Dokumenten {#assemble-xdp-documents}

Mithilfe des Assembler-Dienstes können Sie mehrere XDP-Dokumente in ein einziges XDP-Dokument oder in ein PDF-Dokument zusammenführen. Bei XDP-Quelldateien, die Einfügemarken enthalten, können Sie die einzufügenden Fragmente angeben.

Im Folgenden finden Sie einige Möglichkeiten, wie Sie XDP-Dokumente zusammenführen können:

### Zusammenführen eines einfachen XDP-Dokuments {#assemble-a-simple-xdp-document}

Die folgende Abbildung zeigt, wie drei XDP-Quelldokumente zu einem einzigen XDP-Zieldokument zusammengeführt werden. Das XDP-Zieldokument enthält drei XDP-Quelldokumente und die dazugehörigen Daten. Das Zieldokument ruft grundlegende Basisattribute von dem Basisdokument ab, bei dem es sich um das erste XDP-Quelldokument handelt.

![Assemblieren eines einzelnen XDP-Dokuments aus mehreren XDP-Dokumenten](assets/as_assembler_xdpassembly.png)

Zusammenstellen eines einzelnen XDP-Dokuments aus mehreren XDP-Dokumenten

Nachfolgend finden Sie ein DDX-Dokument, das zu dem oben gezeigten Ergebnis führt.

```xml
<DDX xmlns="https://ns.adobe.com/DDX/1.0/">
<XDP result="MyXDPResult">
<XDP source="sourceXDP1"/>
<XDP source="sourceXDP2"/>
<XDP source="sourceXDP3"/>
</XDP>
</DDX>
```

### Auflösen von Verweisen während der Zusammenführung {#resolving-references-during-assembly}

Normalerweise können XDP-Dokumente Bilder enthalten, die entweder durch absolute oder durch relative Verweise referenziert werden. Der Assembler-Dienst behält standardmäßig die Verweise auf die Bilder im resultierenden XDP-Dokument bei.

Sie können festlegen, wie der Assembler-Dienst die Bilder, die in den XDP-Quelldokumenten entweder durch absolute oder durch relative Verweise referenziert werden, beim Zusammenführen in den XDP-Dateien verarbeitet. Sie können bestimmen, dass alle Bilder im Zieldokument eingebettet werden, sodass es keine relativen oder absoluten Verweise enthält. Hierzu legen Sie den Wert des resolveAssets-Tags fest, das eine oder mehrere der folgenden Optionen annehmen kann. Standardmäßig werden keine Verweise im Zieldokument aufgelöst.

<table>
 <tbody> 
  <tr> 
   <th>Wert</th> 
   <th>Beschreibung</th> 
  </tr> 
  <tr> 
   <td>keine</td> 
   <td>Löst keine Verweise auf.</td> 
  </tr> 
  <tr> 
   <td>alle</td> 
   <td>Bettet alle referenzierten Bilder in das XDP-Quelldokument ein.</td> 
  </tr> 
  <tr> 
   <td>relativ</td> 
   <td>Bettet alle Bilder, die durch relative Verweise referenziert werden, im XDP-<br />Quelldokument ein.</td> 
  </tr> 
  <tr> 
   <td>absolut oder</td> 
   <td>Bettet alle Bilder, die durch absolute Verweise referenziert werden, im XDP-<br />Quelldokument ein.</td> 
  </tr> 
 </tbody> 
</table>

Sie können den Wert des resolveAssets-Attributs entweder im XDP-Quell-Tag oder im Ergebnis-Tag des übergeordneten XDP-Elements angeben. Wenn das Attribut im XDP-Ergebnis-Tag angegeben ist, wird es von allen XDP-Quellelementen übernommen, die untergeordnete Objekte vom XDP-Ergebnis sind. Die explizite Angabe des Attributs für ein Quellelement überschreibt jedoch einzig die Einstellung des Ergebniselements für dieses Quelldokument.

#### Auflösen aller Quellverweise in einem XDP-Dokument {#resolve-all-source-references-in-an-xdp-document}

Um alle Verweise in den Quell-XDP-Dokumenten aufzulösen, geben Sie das Attribut resolveAssets für das\
aus allen resultierend Dokument wie im nachstehenden Beispiel gezeigt an:

```xml
<DDX xmlns="https://ns.adobe.com/DDX/1.0/">
<XDP result="result.xdp" resolveAssets="all">
<XDP source="input1.xdp" />
<XDP source="input2.xdp" />
<XDP source="input3.xdp" />
</XDP>
</DDX
```

Sie können das Attribut auch für alle Quell-XDP-Dokumente separat festlegen, um das gleiche Ergebnis zu erzielen\
Ergebnis.

```xml
<DDX xmlns="https://ns.adobe.com/DDX/1.0/">
<XDP result="result.xdp">
<XDP source="input1.xdp" resolveAssets="all"/>
<XDP source="input2.xdp" resolveAssets="all"/>
<XDP source="input3.xdp" resolveAssets="all"/>
</XDP>
</DDX>
```

#### Auflösen ausgewählter Quellverweise in einem XDP-Dokument {#resolve-selected-source-references-in-an-xdp-document}

Sie können die Quellverweise, die Sie auflösen möchten, selektiv angeben, indem Sie das Attribut resolveAssets für sie festlegen. Die Attribute für einzelne Quelldokumente überschreiben die Einstellung des XDP-Zieldokuments. In diesem Beispiel werden die enthaltenen Fragmente ebenfalls aufgelöst.

```xml
<DDX xmlns="https://ns.adobe.com/DDX/1.0/">
<XDP result="result.xdp" resolveAssets="all">
<XDP source="input1.xdp" >
<XDPContent source="fragment.xdp" insertionPoint="MyInsertionPoint"
fragment="myFragment"/>
</XDP>
<XDP source="input2.xdp" />
</XDP>
</DDX>
```

#### Selektives Auflösen absoluter oder relativer Verweise {#selectively-resolve-absolute-or-relative-references}

Sie können die absoluten oder relativen Verweise in allen oder in einigen Quelldokumenten selektiv auflösen, wie im Beispiel unten gezeigt:

```xml
<DDX xmlns="https://ns.adobe.com/DDX/1.0/">
<XDP result="result.xdp" resolveAssets="absolute">
<XDP source="input1.xdp" />
<XDP source="input2.xdp" />
</XDP>
</DDX
```

### Dynamisches Einfügen von Formularfragmenten in ein XFA-Formular {#dynamically-insert-form-fragments-into-an-xfa-form}

Mit dem Assembler-Dienst können Sie ein XFA-Formular erstellen, das von einem anderen XFA-Formular erstellt wurde, in das Fragmente eingefügt wurden. Mithilfe dieser Funktion können Sie Fragmente zum Erstellen mehrerer Formulare verwenden.

Unterstützung für dynamisches Einfügen von Formularfragmenten unterstützt die Steuerung durch eine Quelle. Sie verwalten eine einzige Quelle von häufig verwendeten Komponenten. Sie können beispielsweise ein Fragment für Ihr Firmenbanner erstellen. Wenn sich das Banner ändert, müssen Sie nur das Fragment ändern. Die anderen Formulare, die das Fragment enthalten, bleiben unverändert.

Formularentwickler verwenden LiveCycle Designer, um Formularfragmente zu erstellen. Diese Fragmente sind Teilformulare mit eindeutigen Namen innerhalb eines XFA-Formulars. Formularentwicklerinnen und -entwickler verwenden Designer auch zum Erstellen von XFA-Formularen, die über Einfügemarken mit eindeutigem Namen verfügen. Sie (die Person, die programmiert) schreiben DDX-Dokumente, die angeben, wie Fragmente in das XFA-Formular eingefügt werden.

Die folgende Abbildung zeigt zwei XML-Formulare (XFA-Vorlagen). Das Formular auf der linken Seite enthält eine Einfügemarke mit dem Namen myInsertionPoint. Das Formular auf der rechten Seite enthält ein Fragment mit dem Namen myFragment.

![Einfügen von Formularfragmenten in ein XFA-Formular](assets/as_assembler_fragment_assy_assembled.png)

Einfügen von Formularfragmenten in ein XFA-Formular

Wenn der Assembler-Dienst das folgende DDX-Dokument interpretiert, erstellt er ein XML-Formular, das ein anderes XML-Formular enthält. Das Teilformular myFragment aus dem Dokument myFragmentSource wird an der Einfügemarke myInsertionPoint in dem Dokument myFormSource eingefügt.

```xml
<DDX xmlns="https://ns.adobe.com/DDX/1.0/">
<XDP result="myFormResult">
<XDP source="myFormSource">
<XDPContent fragment="myFragment" insertionPoint="myInsertionPoint"
source="myFragmentSource"/>
</XDP>
</XDP>
</DDX
```

### Verpacken eines XDP-Dokuments als PDF {#package-an-xdp-document-as-pdf}

Mithilfe des Assembler-Dienstes können Sie ein XDP-Dokument als PDF-Dokument verpacken, wie in diesem DDX-Dokument gezeigt.

```xml
<DDX xmlns="https://ns.adobe.com/DDX/1.0/">
<PDF result="Untitled 1" encryption="passEncProfile1">
<XDP>
<XDP source="sourceXDP3"/>
<XDP source="sourceXDP4"/>
</XDP>
</PDF>
</DDX>
```

## Aufteilen von PDF-Dokumenten {#disassemble-pdf-documents}

Mit dem Assembler-Dienst können Sie ein PDF-Dokument aufteilen. Der Dienst kann Seiten aus dem Quelldokument extrahieren oder ein Quelldokument basierend auf Lesezeichen aufteilen. Diese Aufgabe ist normalerweise hilfreich, wenn das PDF-Dokument ursprünglich aus vielen Einzeldokumenten erstellt wurde, wie z. B. einer Sammlung von Aussagen.

### Extrahieren von Seiten aus einem Quelldokument {#extract-pages-from-a-source-document}

In den folgenden Abbildungen werden die Seiten1 bis 3 aus dem Quelldokument extrahiert und in einem neuen Zieldokument abgelegt.

![Extrahieren von bestimmten Seiten aus einem Quelldokument](assets/as_intro_page_extraction.png)

Extrahieren von bestimmten Seiten aus einem Quelldokument

Das folgende Beispiel stellt ein DDX-Dokument dar, das zum Aufteilen des Dokuments verwendet wird.

```xml
<PDF result="Doc4">
<PDF source="Doc2" pages="1-3"/>
</PDF>
```

### Aufteilen eines Quelldokuments basierend auf Lesezeichen {#divide-a-source-document-based-on-bookmarks}

In der folgenden Abbildung ist DocA in mehrere Zieldokumente unterteilt. Das Lesezeichen der Stufe 1 auf einer Seite gibt den Beginn eines neuen resultierenden Dokuments an.

![Aufteilen eines Quelldokuments in mehrere Dokumente basierend auf Lesezeichen](assets/as_intro_pdfsfrombookmarks.png)

Aufteilen eines Quelldokuments in mehrere Dokumente basierend auf Lesezeichen

Das folgende Beispiel stellt ein DDX-Dokument dar, das Lesezeichen zum Aufteilen eines Quelldokuments verwendet.

```xml
<PDFsFromBookmarks prefix="A">
<PDF source="DocA"/>
</PDFsFromBookmarks>
```

## Bestimmen der PDF/A-Kompatibilität von Dokumenten {#determine-whether-documents-are-pdf-a-compliant}

Mit dem Assembler-Dienst können Sie ermitteln, ob ein PDF-Dokument PDF/A-kompatibel ist. PDF/A ist ein Archivierungsformat für die langfristige Speicherung von Dokumentinhalten. Die Schriftarten werden im Dokument eingebettet und die Datei bleibt unkomprimiert. PDF/A-Dokumente sind daher in der Regel größer als normale PDF-Dokumente. Außerdem enthalten PDF/A-Dokumente keine Audio- und Videoinhalte.

## Abrufen von Informationen zu einem PDF-Dokument {#obtain-information-about-a-pdf-document}

Mit dem Assembler-Dienst können Sie die folgenden Informationen über ein PDF-Dokument abrufen:

* Textinformationen.

   * Wörter auf jeder Seite des Dokuments
   * Position jedes Wortes auf jeder Seite des Dokuments
   * Sätze in jedem Absatz auf jeder Seite des Dokuments

* Lesezeichen, einschließlich der Seitenanzahl, des Titels, Ziels und Erscheinungsbildes. Sie können dies exportieren\
  Daten aus einem PDF-Dokument in ein PDF-Dokument importieren.

* Dateianlagen, einschließlich Dateiinformationen. Bei Anlagen auf Seitenebene ist auch der\
  Speicherort der Dateianlageanmerkung enthalten. Sie können diese Daten aus einem PDF-Dokument exportieren und\
  in ein PDF-Dokument importieren.

* Paketdateien, einschließlich Dateiinformationen, Ordner-, Paket-, Schema- und Felddaten. Sie können diese Daten aus einem PDF-Dokument exportieren und in ein PDF-Dokument importieren.

## Validieren von DDX-Dokumenten {#validate-ddx-documents}

Mit dem Assembler-Dienst können Sie ermitteln, ob ein DDX-Dokument gültig ist. Wenn Sie beispielsweise von einer früheren LiveCycle-Version aktualisiert haben, stellt die Validierung sicher, dass Ihr DDX-Dokument gültig ist.

## Aufrufen anderer Dienste {#call-other-services}

Sie können DDX-Dokumente verwenden, die dazu führen, dass der Assembler-Dienst die folgenden LiveCycle-Dienste aufruft. Der Assembler-Dienst kann nur die mit LiveCycle installierten Dienste aufrufen.

**Reader Extensions-Dienst**: Ermöglicht Adobe Reader-Benutzenden, das erstellte PDF-Dokument mit einer digitalen Signatur zu versehen.

**Forms-Dienst**: Führt eine XDP-Datei und eine XML-Datendatei zusammen, um ein PDF-Dokument zu erstellen, das das ausgefüllte interaktive Formular enthält.

**Output-Dienst**: Konvertiert ein dynamisches XML-Formular in ein PDF-Dokument, das ein nicht interaktives Formular enthält (reduziert das Formular). Der Assembler-Dienst reduziert statische XML-Formulare und Acrobat-Formulare, ohne den Output-Dienst aufzurufen.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<DDX xmlns="https://ns.adobe.com/DDX/1.0/">
<PDF result="outDoc">
<PDF source="doc1"/>
<PDF source="doc2"/>
<ReaderRights
credentialAlias="LCESCred"
digitalSignatures="true"/>
</PDF>
</DDX>
```

Die Verwendung von DDX und dem Assembler-Dienst zum Aufrufen anderer LiveCycle-Dienste kann Ihr Prozessdiagramm vereinfachen. Sie kann sogar die Zeit und die Arbeit reduzieren, die Sie für das Anpassen Ihrer Workflows aufwenden. (Siehe auch
