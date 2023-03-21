---
title: Entwickeln von AEM-Komponenten
seo-title: Developing AEM Components
description: AEM-Komponenten werden verwendet, um den Inhalt, den Sie auf Ihren Web-Seiten bereitstellen, zu speichern, zu formatieren und zu rendern.
seo-description: AEM components are used to hold, format, and render the content made available on your webpages.
uuid: 1f39daa6-7277-45a2-adcc-74b58c93b8e4
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: 8cdb6db4-adaa-4eda-af7d-310a0b44b80b
docset: aem65
legacypath: /content/docs/en/aem/6-2/develop/components/components-touch-optimized
exl-id: 573cdc36-e9c3-4803-9c4e-cebd0cf0a56f
source-git-commit: 4fa868f3ae4778d3a637e90b91f7c5909fe5f8aa
workflow-type: tm+mt
source-wordcount: '3456'
ht-degree: 59%

---

# Entwickeln von AEM-Komponenten{#developing-aem-components}

AEM-Komponenten werden verwendet, um den Inhalt, den Sie auf Ihren Web-Seiten bereitstellen, zu speichern, zu formatieren und zu rendern.

* Beim [Erstellen von Seiten](/help/sites-authoring/default-components.md) erlauben es die Komponenten den Autoren, den Inhalt zu bearbeiten und zu konfigurieren.

   * Beim Erstellen einer [Commerce](/help/commerce/cif-classic/administering/ecommerce.md)-Site können die Komponenten beispielsweise Informationen aus dem Katalog sammeln und rendern.
Weitere Informationen finden Sie unter [Entwicklung von eCommerce](/help/commerce/cif-classic/developing/ecommerce.md).

   * Wenn Sie eine [Communities](/help/communities/author-communities.md)-Site erstellen, können die Komponenten Informationen für Ihre Besucher bereitstellen und Informationen erfassen.
Weitere Informationen finden Sie unter [Entwicklung von Communities](/help/communities/communities.md).

* Auf der Veröffentlichungsinstanz rendern die Komponenten Ihren Inhalt und stellen ihn Ihren Website-Besuchern wie gewünscht dar.

>[!NOTE]
>
>Diese Seite ist eine Fortsetzung des Dokuments [AEM-Komponenten – Grundlagen](/help/sites-developing/components-basics.md).

>[!CAUTION]
>
>Unter `/libs/cq/gui/components/authoring/dialog` stehende Komponenten sollen nur im Editor (Komponentendialogfelder beim Schreiben) verwendet werden. Wenn sie an anderer Stelle verwendet werden (z. B. in einem Assistenten-Dialogfeld), verhalten sie sich möglicherweise nicht wie erwartet.

## Codebeispiele {#code-samples}

Diese Seite enthält die Referenzdokumentation (oder Links zur Referenzdokumentation) die für die Entwicklung neuer Komponenten für AEM erforderlich sind. Einige praktische Beispiele finden Sie unter [Entwickeln von AEM-Komponenten - Codebeispiele](/help/sites-developing/developing-components-samples.md).

## Struktur {#structure}

Die grundlegende Struktur einer Komponente wird auf der Seite [AEM Komponenten - Grundlagen](/help/sites-developing/components-basics.md#structure) beschrieben. Dieses Dokument gilt sowohl für die Touch-optimierte als auch für die klassische Benutzeroberfläche. Auch wenn Sie die klassischen Einstellungen in Ihrer neuen Komponente nicht verwenden müssen, kann es hilfreich sein, sie beim Erben von vorhandenen Komponenten zu beachten.

## Erweitern vorhandener Komponenten und Dialogfelder {#extending-existing-components-and-dialogs}

Je nach der Komponente, die Sie implementieren möchten, kann es möglich sein, eine vorhandene Instanz zu erweitern oder anzupassen, anstatt die gesamte [structure](#structure) von Grund auf neu.

Beim Erweitern oder Anpassen einer vorhandenen Komponente oder eines vorhandenen Dialogfelds können Sie entweder die gesamte Struktur oder die für das Dialogfeld erforderliche Struktur kopieren oder replizieren, bevor Sie Ihre Änderungen vornehmen.

### Erweitern einer vorhandenen Komponente {#extending-an-existing-component}

Die Erweiterung einer vorhandenen Komponente kann mit [Ressourcentyphierarchie](/help/sites-developing/components-basics.md#component-hierarchy-and-inheritance) und die zugehörigen Vererbungsmechanismen.

>[!NOTE]
>
>Komponenten können mit einer Überlagerung ebenfalls neu definiert werden, die auf der Suchpfadlogik basiert. In diesem Fall ist jedoch die [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) wird nicht ausgelöst und `/apps` muss die gesamte Überlagerung definieren.

>[!NOTE]
>
>Die [Inhaltsfragment-Komponente](/help/sites-developing/customizing-content-fragments.md) kann auch angepasst und erweitert werden, wobei jedoch die vollständige Struktur und die Beziehungen zu Assets berücksichtigt werden müssen.

### Anpassen eines Dialogfelds &quot;Vorhandene Komponente&quot; {#customizing-a-existing-component-dialog}

Es ist auch möglich, ein *Komponentendialogfeld* mithilfe des [Sling Resource Mergers](/help/sites-developing/sling-resource-merger.md) zu überschreiben und die Eigenschaft `sling:resourceSuperType` zu definieren.

Dies bedeutet, dass Sie nur die erforderlichen Unterschiede neu definieren müssen, anstatt das gesamte Dialogfeld neu zu definieren (mit `sling:resourceSuperType`). Diese Methode wird jetzt zum Erweitern eines Komponentendialogfelds empfohlen

Siehe [Sling Resource Merger](/help/sites-developing/sling-resource-merger.md) für weitere Details.

## Markup definieren {#defining-the-markup}

Ihre Komponente wird mit [HTML gerendert](https://www.w3schools.com/htmL/html_intro.asp). Ihre Komponente muss den HTML-Code definieren, der erforderlich ist, um den erforderlichen Inhalt zu übernehmen und anschließend in der Autoren- und Veröffentlichungsumgebung nach Bedarf zu rendern.

### Verwenden der HTML-Vorlagensprache {#using-the-html-template-language}

Die [HTML Vorlagensprache (HTL)](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de), die mit AEM 6.0 eingeführt wurde, löst JSP (JavaServer Pages) als bevorzugtes und empfohlenes serverseitiges Vorlagensystem für HTML ab. Für Webentwickler, die robuste Unternehmenswebsites erstellen müssen, hilft HTL bei der Verbesserung von Sicherheit und Entwicklungseffizienz.

>[!NOTE]
>
>Obwohl sowohl HTL als auch JSP für die Entwicklung von Komponenten verwendet werden können, veranschaulichen wir die Entwicklung mit HTL auf dieser Seite, da dies die empfohlene Skriptsprache für AEM ist.

## Entwickeln der Inhaltslogik {#developing-the-content-logic}

Diese optionale Logik wählt und/oder berechnet den Inhalt, der gerendert werden soll. Sie wird aus HTL-Ausdrücken mit dem entsprechenden Anwendungs-API-Muster aufgerufen.

Der Mechanismus zum Trennen der Logik von der Erscheinung hilft zu verdeutlichen, was für eine gegebene Sicht aufgerufen wird. Es ermöglicht auch eine unterschiedliche Logik für verschiedene Ansichten derselben Ressource.

### Verwendung von Java {#using-java}

[Mit der Java-Anwendungs-API von HTL kann eine HTL-Datei auf Hilfsmethoden in einer benutzerdefinierten Java-Klasse zugreifen. ](https://experienceleague.adobe.com/docs/experience-manager-htl/content/java-use-api.html?lang=de?lang=en) Auf diese Weise können Sie Java-Code verwenden, um die Logik für die Auswahl und Konfiguration des Komponenteninhalts zu implementieren.

### Verwenden von JavaScript   {#using-javascript}

[Die HTL JavaScript Use-API ermöglicht es einer HTL-Datei, auf den in JavaScript geschriebenen Hilfscode zuzugreifen](https://experienceleague.adobe.com/docs/experience-manager-htl/content/java-use-api.html?lang=en). Dies ermöglicht es Ihnen, JavaScript-Code zu verwenden, um die Logik zum Auswählen und Konfigurieren des Komponenteninhalts zu implementieren.

### Verwendung Client-seitiger HTML-Bibliotheken {#using-client-side-html-libraries}

Moderne Websites beruhen in hohem Maße auf der Client-seitigen Verarbeitung durch einen komplexen JavaScript- und CSS-Code. Die Organisation und Optimierung der Bereitstellung dieses Codes kann äußerst kompliziert sein.

Um Abhilfe zu schaffen, stellt AEM **Client-seitige Bibliotheksordner** zur Verfügung, mit denen Sie Ihren Client-seitigen Code im Repository speichern, in Kategorien gruppieren und definieren können, wann und wie jede Codekategorie dem Client bereitgestellt werden soll. Das Client-seitige Bibliotheksystem übernimmt dann das Herstellen der richtigen Links auf der endgültigen Webseite, um den korrekten Code zu laden.

Lesen Sie [Verwendung Client-seitiger HTML-Bibliotheken](/help/sites-developing/clientlibs.md) für weitere Informationen.

## Konfigurieren des Bearbeitungsverhaltens {#configuring-the-edit-behavior}

Sie können das Bearbeitungsverhalten einer Komponente konfigurieren, einschließlich Attributen wie Aktionen, die für die Komponente verfügbar sind, Eigenschaften des Editors für die Bearbeitung im Kontext, die sich auf Ereignisse für die Komponente beziehen. Die Konfiguration ist sowohl für die Touch-optimierte als auch für die klassische Benutzeroberfläche üblich, allerdings mit bestimmten, spezifischen Unterschieden.

Um das [Bearbeitungsverhalten einer Komponente zu konfigurieren](/help/sites-developing/components-basics.md#edit-behavior), fügen Sie einen `cq:editConfig`-Knoten des Typs `cq:EditConfig` unter dem Komponentenknoten (des Typs `cq:Component`) hinzu sowie spezifische Eigenschaften und untergeordnete Knoten.

## Konfigurieren des Vorschauverhaltens {#configuring-the-preview-behavior}

Der [WCM-Modus](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/api/WCMMode.html)-Cookie wird beim Wechsel in den **Vorschaumodus** gesetzt, auch wenn die Seite nicht aktualisiert wird.

Komponenten mit einem Rendering, die für den WCM-Modus empfindlich sind, müssen so definiert werden, dass sie sich selbst aktualisieren und sich dann auf den Wert des Cookies verlassen.

>[!NOTE]
>
>In der Touch-optimierten Benutzeroberfläche werden nur die Werte `EDIT` und `PREVIEW` für den [WCM-Modus](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/api/WCMMode.html)-Cookie verwendet.

## Erstellen und Konfigurieren eines Dialogfelds {#creating-and-configuring-a-dialog}

Dialogfelder werden verwendet, um dem Autor die Interaktion mit der Komponente zu ermöglichen. Mit einem Dialogfeld können Autorinnen und Autoren und/oder Admins Inhalte bearbeiten, die Komponente konfigurieren oder Design-Parameter definieren (mit einem [Design-Dialogfeld](#creating-and-configuring-a-design-dialog))

### Coral- und Granite-Benutzeroberfläche {#coral-ui-and-granite-ui}

[Coral-Benutzeroberfläche](https://developer.adobe.com/experience-manager/reference-materials/6-5/coral-ui/coralui3/index.html) und [Granite-Benutzeroberfläche](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) definieren das moderne Erscheinungsbild von AEM.

[Die Granite-Benutzeroberfläche bietet einen großen Bereich der grundlegenden Komponenten (Widgets)](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html), die zum Erstellen Ihres Dialogfelds in der Autorenumgebung benötigt werden. Bei Bedarf können Sie diese Auswahl erweitern und [Erstellen eines eigenen Widgets](#creatinganewwidget).

Ausführliche Informationen finden Sie unter:

* Coral-Benutzeroberfläche

   * Bietet eine konsistente Benutzeroberfläche für alle Cloud-Lösungen
   * [Konzepte der Touch-optimierten Benutzeroberfläche von AEM - Coral-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#coral-ui)
   * [Coral-Benutzeroberfläche - Handbuch](https://developer.adobe.com/experience-manager/reference-materials/6-5/coral-ui/coralui3/index.html)

* Granite-Benutzeroberfläche

   * Bietet Markup der Coral-Benutzeroberfläche in Sling-Komponenten zum Erstellen von UI-Konsolen und -Dialogfeldern
   * [Konzepte der Touch-optimierten Benutzeroberfläche von AEM - Granite-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#coral-ui)
   * [Dokumentation zur Granite-Benutzeroberfläche](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)

>[!NOTE]
>
>Aufgrund der Eigenschaften der Granite-UI-Komponenten (und der Unterschiede zu den ExtJS-Widgets) gibt es einige Unterschiede zwischen der Interaktion von Komponenten mit der Touch-optimierten Benutzeroberfläche und der [klassische Benutzeroberfläche](/help/sites-developing/developing-components-classic.md).

### Erstellen eines neuen Dialogfelds {#creating-a-new-dialog}

Dialogfelder für die Touch-optimierte Benutzeroberfläche:

* haben den Namen`cq:dialog`.
* sind als Knoten `nt:unstructured` mit der Eigenschaft `sling:resourceType` definiert.

* befinden sich unter ihrem Knoten `cq:Component` und neben ihrer Komponentendefinition.
* werden auf der Serverseite (als Sling-Komponenten) basierend auf ihrer Inhaltsstruktur und der Eigenschaft `sling:resourceType` gerendert.
* Verwenden Sie das Granite-UI-Framework.
* enthalten eine Knotenstruktur, die die Felder im Dialogfeld beschreibt.

   * Diese Knoten sind `nt:unstructured` mit der erforderlichen Eigenschaft `sling:resourceType`.

Eine Beispielknotenstruktur könnte wie folgt aussehen:

```xml
newComponent (cq:Component)
  cq:dialog (nt:unstructured)
    content
      layout
      items
        column
          items
            file
            description
```

Das Anpassen eines Dialogfelds ähnelt der Entwicklung einer Komponente, da das Dialogfeld selbst eine Komponente ist (z. B. Markup, das von einem Komponentenskript zusammen mit dem von einer Client-Bibliothek bereitgestellten Verhalten/Stil gerendert wird).

Beispiele finden Sie hier:

* `/libs/foundation/components/text/cq:dialog`
* `/libs/foundation/components/download/cq:dialog`

>[!NOTE]
>
>Wenn für eine Komponente kein Dialogfeld für die Touch-optimierte Benutzeroberfläche definiert wurde, wird das Dialogfeld für die klassische Benutzeroberfläche als Rückfall innerhalb einer Kompatibilitätsebene verwendet. Um ein solches Dialogfeld anzupassen, müssen Sie das Dialogfeld für die klassische Benutzeroberfläche anpassen. Siehe [AEM-Komponenten für die klassische Benutzeroberfläche](/help/sites-developing/developing-components-classic.md).

### Anpassen von Dialogfeldern {#customizing-dialog-fields}

>[!NOTE]
>
>Siehe:
>
>* AEM-Gems-Session zum [Anpassen von Dialogfeldern](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html?lang=en).
>* Der zugehörige Beispiel-Code wird unter [Codebeispiel – So passen Sie Dialogfelder an](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields) behandelt.
>


#### Erstellen eines neuen Felds {#creating-a-new-field}

Widgets für die Touch-optimierte Benutzeroberfläche werden als Granite-UI-Komponenten implementiert.

Um ein neues Widget zur Verwendung in einem Komponentendialogfeld für die Touch-optimierte Benutzeroberfläche zu erstellen, müssen Sie [Erstellen einer neuen Granite-UI-Feldkomponente](/help/sites-developing/granite-ui-component.md).

>[!NOTE]
>
>Ausführliche Informationen zur Granite-Benutzeroberfläche finden Sie in der [Dokumentation zur Granite-Benutzeroberfläche](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html).

Wenn Sie das Dialogfeld für einen einfachen Container für ein Formularelement halten, können Sie den Primärinhalt Ihres Dialogfeldinhalts als auch Formularfelder sehen. Um ein neues Formularfeld zu erstellen, müssen Sie einen Ressourcentyp erstellen. Dies entspricht dem Erstellen einer neuen Komponente. Um Ihnen bei dieser Aufgabe zu helfen, bietet die Granite-Benutzeroberfläche eine generische Feldkomponente, von der eine Vererbung möglich ist (mithilfe von `sling:resourceSuperType`):

`/libs/granite/ui/components/coral/foundation/form/field`

Genauer gesagt bietet die Granite-Benutzeroberfläche eine Reihe von Feldkomponenten, die für die Verwendung in Dialogfeldern (oder allgemein in [Formularen](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/index.html)) geeignet sind.

>[!NOTE]
>
>Dies unterscheidet sich von der klassischen Benutzeroberfläche, bei der Widgets durch `cq:Widgets`-Knoten mit jeweils einem bestimmten `xtype` repräsentiert werden, um die Beziehung zum entsprechenden ExtJS-Widget herzustellen. Aus Sicht der Implementierung wurden diese Widgets auf der Client-Seite von ExtJS-Framewrrk gerendert.

Sobald Sie Ihren Ressourcentyp erstellt haben, können Sie Ihr Feld instanziieren, indem Sie in Ihrem Dialogfeld einen neuen Knoten hinzufügen, wobei die Eigenschaft `sling:resourceType` auf den Ressourcentyp verweist, den Sie gerade eingeführt haben.

#### Erstellen einer Client-Bibliothek für Stil und Verhalten {#creating-a-client-library-for-style-and-behavior}

Wenn Sie Stil und Verhalten für Ihre Komponente definieren möchten, können Sie eine dedizierte [Client-Bibliothek](/help/sites-developing/clientlibs.md) , das Ihre benutzerdefinierte CSS/LESS- und JS-Datei definiert.

Damit Ihre Client-Bibliothek nur für das Komponentendialogfeld geladen wird (d. h., sie wird nicht für eine andere Komponente geladen), müssen Sie die Eigenschaft **`extraClientlibs`** Ihres Dialogfelds auf den Kategorienamen der gerade erstellten Client-Bibliothek einstellen. Dies empfiehlt sich, wenn die Client-Bibliothek recht groß ist und/oder das Feld für dieses Dialogfeld spezifisch ist und nicht in anderen Dialogfeldern benötigt wird.

Um die Client-Bibliothek für alle Dialogfelder zu laden, legen Sie die Kategorieeigenschaft Ihrer Client-Bibliothek auf `cq.authoring.dialog` fest. Dies ist der Kategoriename der Client-Bibliothek, die beim Rendern aller Dialogfelder standardmäßig enthalten ist. Dies empfiehlt sich, wenn die Client-Bibliothek klein ist und/oder Ihr Feld allgemein ist und in anderen Dialogfeldern wiederverwendet werden kann.

Ein Beispiel finden Sie unter:

* `cqgems/customizingfield/components/colorpicker/clientlibs`

   * gegeben durch das [Code-Beispiel](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

#### Erweitern (Vererben von) eines Felds {#extending-inheriting-from-a-field}

Je nach Ihren Anforderungen haben Sie folgende Möglichkeiten:

* Ein gegebenes Granite-Benutzeroberflächenfeld um Komponentenvererbung (`sling:resourceSuperType`) erweitern
* Erweitern Sie ein bestimmtes Widget aus der zugrunde liegenden Widget-Bibliothek (im Fall der Granite-Benutzeroberfläche ist dies die Coral-Benutzeroberfläche), indem Sie der Widget-Bibliotheks-API (JS-/CSS-Vererbung) folgen.

#### Zugriff auf Dialogfelder {#access-to-dialog-fields}

Sie können auch Render-Bedingungen (`rendercondition`) verwenden, um festzulegen, wer Zugriff auf bestimmte Registerkarten/Felder in Ihrem Dialogfeld hat. Beispielsweise:

```xml
+ mybutton
  - sling:resourceType = granite/ui/components/coral/foundation/button
  + rendercondition
    - sling:resourceType = myapp/components/renderconditions/group
    - groups = ["administrators"]
```

### Umgang mit Feldereignissen {#handling-field-events}

Die Methode zur Behandlung von Ereignissen in Dialogfeldern wird jetzt mit [Listenern in einer benutzerdefinierten Client-Bibliothek](#listeners-in-a-custom-client-library) ausgeführt. Dies ist eine Änderung gegenüber der älteren Methode, [Listener in der Inhaltsstruktur](#listenersinthecontentstructureclassicui).

#### Listener in einer benutzerdefinierten Client-Bibliothek {#listeners-in-a-custom-client-library}

Um Logik in Ihr Feld zu injizieren, sollten Sie Folgendes beachten:

1. Lassen Sie Ihr Feld mit einer bestimmten CSS-Klasse markiert (die *Hook*).
1. Definieren Sie in Ihrer Client-Bibliothek einen JS-Listener, der auf diesen CSS-Klassennamen basiert (dadurch wird sichergestellt, dass Ihre benutzerdefinierte Logik nur auf Ihr Feld angewendet wird und keine anderen Felder desselben Typs betroffen sind).

Um dies zu erreichen, müssen Sie die zugrunde liegende Widget-Bibliothek kennen, mit der Sie interagieren möchten. Informationen darüber, auf welches Ereignis Sie reagieren möchten, finden Sie in der [Dokumentation zur Coral-Benutzeroberfläche](https://developer.adobe.com/experience-manager/reference-materials/6-5/coral-ui/coralui3/index.html). Dies ähnelt dem Prozess, den Sie in der Vergangenheit mit ExtJS durchführen mussten: Suchen Sie die Dokumentationsseite eines bestimmten Widgets und überprüfen Sie dann die Details seiner Ereignis-API.

Ein Beispiel finden Sie unter:

* `cqgems/customizingfield/components/clientlibs/customizingfield`

   * gegeben durch das [Code-Beispiel](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

#### Listener in der Inhaltsstruktur {#listeners-in-the-content-structure}

In der klassischen Benutzeroberfläche mit ExtJS war es üblich, Listener für ein bestimmtes Widget in der Inhaltsstruktur zu haben. Dasselbe in der Touch-optimierten Benutzeroberfläche zu erreichen ist anders, als der JS-Listener-Code (oder jeglicher Code) im Inhalt nicht mehr definiert ist.

Die Inhaltsstruktur beschreibt die semantische Struktur. Sie sollte (muss) nicht die Art des zugrunde liegenden Widget implizieren. Wenn Sie keinen JS-Code in der Inhaltsstruktur haben, können Sie die Implementierungsdetails ändern, ohne die Inhaltsstruktur ändern zu müssen. Mit anderen Worten: Sie können die Widget-Bibliothek ändern, ohne die Inhaltsstruktur zu berühren.

#### Erkennen der Verfügbarkeit des Dialogfelds {#dialog-ready}

Wenn Sie über ein benutzerdefiniertes JavaScript verfügen, das nur ausgeführt werden muss, wenn das Dialogfeld verfügbar und bereit ist, sollten Sie auf das `dialog-ready`-Ereignis achten.

Dieses Ereignis wird ausgelöst, wenn das Dialogfeld geladen (oder erneut geladen) wird und einsatzbereit ist, d. h., wenn eine Änderung (Erstellen/Aktualisieren) im DOM des Dialogfelds erfolgt.

`dialog-ready` kann verwendet werden, um in JavaScript benutzerdefinierten Code einzubinden, der Anpassungen an den Feldern in einem Dialogfeld oder ähnliche Aufgaben durchführt.

### Feldüberprüfung {#field-validation}

#### Obligatorisches Feld {#mandatory-field}

Um ein bestimmtes Feld als Pflichtfeld zu markieren, legen Sie die folgende Eigenschaft im Inhaltsknoten Ihres Felds fest:

* Name: `required`
* Typ: `Boolean`

Ein Beispiel finden Sie unter:

```xml
/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/title/items/title
```

#### Feldvalidierung (Granite-Benutzeroberfläche) {#field-validation-granite-ui}

Die Feldüberprüfung in der Granite-Benutzeroberfläche und den Granite-Benutzeroberflächenkomponenten (entspricht Widgets) erfolgt mithilfe der API `foundation-validation`. [Weitere Informationen finden Sie in der `foundation-valdiation` Granite-Dokumentation.](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/clientlibs/foundation/js/validation/index.html)

Beispiele finden Sie hier:

* `cqgems/customizingfield/components/clientlibs/customizingfield/js/validations.js`

   * im Abschnitt [Codebeispiel](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `/libs/cq/gui/components/authoring/dialog/clientlibs/dialog/js/validations.js`

## Erstellen und Konfigurieren eines Design-Dialogfelds {#creating-and-configuring-a-design-dialog}

Das Design-Dialogfeld wird bereitgestellt, wenn eine Komponente Entwurfsdetails enthält, die im [Entwurfsmodus](/help/sites-authoring/default-components-designmode.md) bearbeitet werden können.

Die Definition ist der eines [Dialogfelds sehr ähnlich, das für die Bearbeitung von Inhalten](#creating-a-new-dialog) verwendet wird, mit dem Unterschied, dass es als Knoten definiert ist:

* Knotenname: `cq:design_dialog`
* Typ: `nt:unstructured`

## Erstellen und Konfigurieren eines Editors für Bearbeitung im Kontext {#creating-and-configuring-an-inplace-editor}

Ein Editor für die Bearbeitung im Kontext ermöglicht es dem Benutzer, Inhalte direkt im Absatzfluss zu bearbeiten, ohne dass ein Dialogfeld geöffnet werden muss. Beispielsweise verfügen die Standardkomponenten Text und Titel über einen Editor für die Bearbeitung im Kontext.

Ein Editor für die Bearbeitung im Kontext ist nicht für jeden Komponententyp erforderlich/sinnvoll.

Siehe [Erweitern der Seitenbearbeitung - Hinzufügen eines neuen Editors für die Bearbeitung im Kontext](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor) für weitere Informationen.

## Anpassen der Komponentensymbolleiste {#customizing-the-component-toolbar}

Die [Komponentensymbolleiste](/help/sites-developing/touch-ui-structure.md#component-toolbar) bietet dem Benutzer Zugriff auf eine Reihe von Aktionen für die Komponente, z. B. Bearbeiten, Konfigurieren, Kopieren und Löschen.

Siehe [Erweitern der Seitenbearbeitung - Hinzufügen einer neuen Aktion zur Komponentensymbolleiste](/help/sites-developing/customizing-page-authoring-touch.md#add-new-action-to-a-component-toolbar) für weitere Informationen.

## Konfigurieren einer Komponente für die Verweisleiste (geliehen/verliehen) {#configuring-a-component-for-the-references-rail-borrowed-lent}

Wenn Ihre neue Komponente auf Inhalte von anderen Seiten verweist, können Sie überlegen, ob sich dies auf die **Geliehener Inhalt** und **Geliehener Inhalt** der [**Verweise**](/help/sites-authoring/basic-handling.md#references) Leiste.

Die Standardinstallation von AEM überprüft nur die Referenzkomponente. Um Ihre Komponente hinzuzufügen, müssen Sie die Referenzkonfiguration für das OSGi-Bundle **WCM Authoring Content** konfigurieren.

Erstellen Sie einen neuen Eintrag in der Definition und geben Sie Ihre Komponente zusammen mit der zu überprüfenden Eigenschaft an. Beispiel:

`/apps/<*your-Project*>/components/reference@parentPath`

>[!NOTE]
>
>Bei der Arbeit mit AEM gibt es verschiedene Methoden, die Konfigurationseinstellungen für solche Services zu verwalten. Weitere Informationen und empfohlene Vorgehensweisen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

## Aktivieren und Hinzufügen Ihrer Komponente zum Absatzsystem {#enabling-and-adding-your-component-to-the-paragraph-system}

Nachdem die Komponente entwickelt wurde, muss sie für die Verwendung in einem geeigneten Absatzsystem aktiviert werden, damit sie auf den erforderlichen Seiten verwendet werden kann.

Dies kann folgendermaßen erfolgen:

* using [Designmodus](/help/sites-authoring/default-components-designmode.md) beim Bearbeiten einer bestimmten Seite.
* [Definieren der Eigenschaft `components` im Absatzsystem einer Vorlage](/help/sites-developing/components-basics.md#adding-your-component-to-the-paragraph-system).

## Konfigurieren eines Absatzsystems, sodass beim Ziehen eines Assets eine Komponenteninstanz erstellt wird {#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance}

AEM bietet die Möglichkeit, ein Absatzsystem auf Ihrer Seite so zu konfigurieren, dass [Eine Instanz der neuen Komponente wird automatisch erstellt, wenn ein Benutzer ein (geeignetes) Asset auf eine Instanz dieser Seite zieht](/help/sites-authoring/editing-content.md#insertingacomponenttouchoptimizedui) (anstatt immer eine leere Komponente auf die Seite ziehen zu müssen).

Dieses Verhalten und die erforderliche Beziehung zwischen Asset und Komponente können konfiguriert werden:

1. Unter der Absatzdefinition Ihres Seitendesigns. Beispiel:

   * `/etc/designs/<myApp>/page/par`

   Erstellen Sie einen neuen Knoten:

   * Name: `cq:authoring`
   * Typ: `nt:unstructured`


1. Erstellen Sie unter diesem einen neuen Knoten, der alle Zuordnungen zwischen Asset und Komponente enthält:

   * Name: `assetToComponentMapping`
   * Typ: `nt:unstructured`

1. Erstellen Sie für jede Zuordnung zwischen Asset und Komponente einen Knoten:

   * Name: Text, es wird empfohlen, dass der Name des Assets und den zugehörigen Komponententyp angibt; zum Beispiel, Bild
   * Typ: `nt:unstructured`

   Jeweils mit den folgenden Eigenschaften:

   * `assetGroup`:

      * Typ: `String`
      * Wert: die Gruppe, zu der das zugehörige Asset gehört; zum Beispiel `media`
   * `assetMimetype`:

      * Typ: `String`
      * Wert: der mime-Typ des zugehörigen Assets; zum Beispiel `image/*`
   * `droptarget`:

      * Typ: `String`
      * Wert: das Ablageziel; zum Beispiel, `image`
   * `resourceType`:

      * Typ: `String`
      * Wert: die zugehörige Komponentenressource; zum Beispiel `foundation/components/image`
   * `type`:

      * Typ: `String`
      * Wert: der Typ, z. B. `Images`






Beispiele finden Sie unter:

* `/etc/designs/geometrixx/jcr:content/page/par/cq:authoring`
* `/etc/designs/geometrixx-outdoors/jcr:content/page/par/cq:authoring`
* `/etc/designs/geometrixx-media/jcr:content/article/article-content-par/cq:authoring`

CODE FÜR GITHUB

Den Code dieser Seite finden Sie auf GitHub.

* [Öffnen Sie das Projekt aem-project-archetype in GitHub](https://github.com/adobe/aem-project-archetype)
* Laden Sie das Projekt als [ZIP-Datei](https://github.com/adobe/aem-project-archetype/archive/master.zip) herunter.

>[!NOTE]
>
>Die automatische Erstellung von Komponenteninstanzen kann jetzt einfach über die Benutzeroberfläche konfiguriert werden, wenn [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) und bearbeitbare Vorlagen verwendet werden. Weitere Informationen zum Definieren der Komponenten, die bestimmten Medientypen automatisch zugeordnet werden, finden Sie unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md#editing-a-template-structure-template-author).

## Verwenden von AEM Brackets-Erweiterungen {#using-the-aem-brackets-extension}

Die [AEM Brackets-Erweiterung](/help/sites-developing/aem-brackets.md) bietet einen reibungslosen Workflow zum Bearbeiten AEM Komponenten und Client-Bibliotheken. Sie basiert auf der [Brackets](https://brackets.io/) Code-Editor.

Die -Erweiterung:

* Erleichtert die Synchronisierung (kein Maven oder File Vault erforderlich), um die Effizienz der Entwickler zu erhöhen, und hilft Frontend-Entwicklern mit begrenztem AEM-Wissen, an Projekten teilzunehmen.
* Bietet [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de)-Unterstützung, die Vorlagensprache, die entwickelt wurde, um die Komponentenentwicklung zu vereinfachen und die Sicherheit zu erhöhen.

>[!NOTE]
>
>Brackets ist der empfohlene Mechanismus zum Erstellen von Komponenten. Sie ersetzt die Funktion CRXDE Lite - Komponente erstellen , die für die klassische Benutzeroberfläche entwickelt wurde.

## Migration von einer klassischen Komponente {#migrating-from-a-classic-component}

Wenn Sie eine Komponente, die für die Verwendung mit der klassischen Benutzeroberfläche konzipiert wurde, zu einer Komponente migrieren, die mit der Touch-optimierten Benutzeroberfläche (einzeln oder gemeinsam) verwendet werden kann, sollten die folgenden Probleme berücksichtigt werden:

* HTL

   * Die Verwendung von [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de) ist nicht obligatorisch, aber wenn Ihre Komponente aktualisiert werden muss, ist es ein idealer Zeitpunkt, eine [Migration von JSP zu HTL](/help/sites-developing/components-basics.md#htl-vs-jsp) in Betracht zu ziehen.

* Komponenten

   * Migrieren Sie [`cq:listener`](/help/sites-developing/developing-components.md#migrating-cq-listener-code)-Code, der klassische benutzeroberflächespezifische Funktionen verwendet
   * RTE-Plug-in, für weitere Informationen siehe [Konfigurieren des Rich-Text-Editors](/help/sites-administering/rich-text-editor.md).
   * [Migrieren Sie `cq:listener`-Code](#migrating-cq-listener-code), der Funktionen verwendet, die für die klassische Benutzeroberfläche spezifisch sind

* Dialogfelder

   * Erstellen Sie ein Dialogfeld zur Verwendung in der Touch-optimierten Benutzeroberfläche. Aus Kompatibilitätsgründen kann die Touch-optimierte Benutzeroberfläche jedoch die Definition eines Dialogfelds der klassischen Benutzeroberfläche verwenden, wenn für die Touch-optimierte Benutzeroberfläche kein Dialogfeld definiert wurde.
   * Die [AEM-Modernisierungs-Tools](/help/sites-developing/modernization-tools.md) werden bereitgestellt, um Unterstützung bei der Erweiterung vorhandener Komponenten zu bieten.
   * Das [Zuordnen von ExtJS zu Granite-UI-Komponenten](/help/sites-developing/touch-ui-concepts.md#extjs-and-corresponding-granite-ui-components) bietet einen praktischen Überblick über ExtJS-Xtypes und Knotentypen mit ihren entsprechenden Ressourcentypen in der Granite-Benutzeroberfläche.
   * Anpassen von Feldern. Weitere Informationen finden Sie in der Sitzung AEM Gems unter [Anpassen von Dialogfeldern](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html?lang=en).
   * Migrieren von Typen zu [Validierung der Granite-Benutzeroberfläche](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/clientlibs/foundation/js/validation/index.html)
   * Verwenden von JS-Listenern finden Sie weitere Informationen unter [Umgang mit Feldereignissen](#handling-field-events) und der Sitzung AEM Gems [Anpassen von Dialogfeldern](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-customizing-dialog-fields-in-touch-ui.html?lang=en).

### Migrieren von cq:listener-Code {#migrating-cq-listener-code}

Wenn Sie ein Projekt migrieren, das für die klassische Benutzeroberfläche konzipiert wurde, verwendet der `cq:listener`-Code (und komponentenbezogene Client-Bibliotheken) möglicherweise Funktionen, die für die klassische Benutzeroberfläche spezifisch sind (z. B. `CQ.wcm.*`). Für die Migration müssen Sie diesen Code mithilfe der entsprechenden Objekte/Funktionen in der Touch-optimierten Benutzeroberfläche aktualisieren.

Wenn Ihr Projekt vollständig in die Touch-optimierte Benutzeroberfläche migriert wird, müssen Sie diesen Code ersetzen, um die Objekte und Funktionen zu verwenden, die für die Touch-optimierte Benutzeroberfläche relevant sind.

Wenn Ihr Projekt jedoch während des Migrationszeitraums sowohl für die klassische als auch für die Touch-optimierte Benutzeroberfläche berücksichtigt werden muss (das übliche Szenario), müssen Sie einen Schalter implementieren, um den separaten Code zu unterscheiden, der auf die entsprechenden Objekte verweist.

Dieser Switch-Mechanismus kann wie folgt implementiert werden:

```
if (Granite.author) {
    // touch UI
} else {
    // classic UI
}
```

## Dokumentation der Komponente {#documenting-your-component}

Als Entwickler möchten Sie einfachen Zugriff auf die Komponentendokumentation, damit Sie Folgendes schnell verstehen können:

* Beschreibung
* Beabsichtigter Verwendungszweck
* Inhaltstruktur und Eigenschaften
* Ausgesetzte APIs und Erweiterungspunkte
* Und so weiter

Aus diesem Grund ist es einfach, alle vorhandenen Dokumentations-Markdown, die Sie in der Komponente selbst verfügbar haben, bereitzustellen.

Platzieren Sie eine `README.md` -Datei in der Komponentenstruktur. Dieses Markdown wird im [Komponentenkonsole](/help/sites-authoring/default-components-console.md).

![chlimage_1-7](assets/chlimage_1-7.png)

Der unterstützte Markdown ist derselbe wie der für [Inhaltsfragmente](/help/assets/content-fragments/content-fragments-markdown.md).
