---
title: Erstellen benutzerdefinierter Themen für adaptive Formulare
seo-title: Creating custom adaptive form themes
description: Ein Design für adaptives Formular ist eine AEM-Clientbibliothek, mit der Sie die Stile (Erscheinungsbild) für ein adaptives Formular definieren. Erfahren Sie, wie Sie benutzerdefinierter Designs für adaptive Formulare erstellen können.
seo-description: An adaptive form theme is an AEM client library that you use to define the styles (look and feel) for an adaptive form. Learn how you can create custom adaptive form themes.
uuid: b25df10e-b07c-4e9d-a799-30f1c6fb3c44
content-type: reference
topic-tags: customization
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 437e6581-4eb1-4fbd-a6da-86b9c90cec89
exl-id: 73b0057f-082d-4502-90e2-5e41b52c1185
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 100%

---

# Erstellen benutzerdefinierter Themen für adaptive Formulare {#creating-custom-adaptive-form-themes}

>[!CAUTION]
>
>AEM Forms bietet die Funktion [Design-Editor](/help/forms/using/themes.md) zum Erstellen und Ändern der [Designs](/help/forms/using/themes.md) von adaptiven Formularen. Führen Sie die in diesem Artikel aufgeführten Schritte nur aus, wenn Sie von einer Version ohne [Design-Editor](/help/forms/using/themes.md) aus aktualisiert haben und bereits Designs angelegt haben, die mithilfe von Less/CSS-Dateien (Methode vor dem Design-Editor) erstellt wurden.

## Voraussetzungen {#prerequisites}

* Kenntnisse des LESS (Leaner CSS)-Frameworks
* Erstellen einer Client-Bibliothek in Adobe Experience Manager
* [Erstellen einer adaptiven Formularvorlage](/help/forms/using/custom-adaptive-forms-templates.md) zur Verwendung des Designs, das Sie erstellen

## Design für adaptives Formular {#adaptive-form-theme}

Ein **Design für adaptives Formular** ist eine AEM-Clientbibliothek, mit der Sie die Stile (Erscheinungsbild) für ein adaptives Formular definieren.

Sie erstellen ein **adaptives Formular** und wenden das Design auf das Formular an. Anschließend verwenden Sie diese benutzerdefinierte Vorlage, um ein **adaptives Formular** zu erstellen.

![Adaptives Formular und Clientbibliothek](assets/hierarchy.png)

## So erstellen Sie ein Design für ein adaptives Formular {#to-create-an-adaptive-form-theme}

>[!NOTE]
>
>Das folgende Verfahren wird mithilfe von Musternamen für AEM-Objekte wie Knoten, Eigenschaften und Ordner beschrieben.
>
>Wenn Sie diesen Schritten mithilfe der Namen folgen, sollte die resultierende Vorlage in etwa dem folgenden Snapshot ähneln:

![Momentaufnahme des adaptiven Formulars mit Waldthemen](assets/thumbnail.png)
**Abbildung**: *Beispiel für Waldthemen*

1. Erstellen Sie einen Knoten des Typs `cq:ClientLibraryFolder` unter dem Knoten `/apps`.

   Erstellen Sie beispielsweise den folgenden Knoten:

   `/apps/myAfThemes/forestTheme`

1. Fügen Sie dem Knoten `categories` eine Zeichenfolgeneigenschaft mit mehreren Eigenschaften hinzu und stellen Sie seinen Wert entsprechend ein.

   Legen Sie beispielsweise die Eigenschaft fest auf: `af.theme.forest`.

   ![Snapshot zum CRX-Repository](assets/3-2.png)

1. Fügen Sie zwei Ordner, `less` und `css`, und eine Datei `css.txt` zu dem in Schritt 1 erstellten Knoten hinzu:

   * Ordner `less`: Enthält die Variablendateien `less`, in denen Sie die Variablen `less` und `less mixins` definieren, die für die Verwaltung der .css-Stile verwendet werden.

      Dieser Ordner besteht aus den Variablendateien `less`, mixin-Dateien `less` und den Dateien `less`, mit deren Hilfe Stile mit Mixins und Variablen definiert werden. Diese Dateien werden dann alle in „styles.less“ importiert.

   * Ordner `css`: Enthält die .css-Dateien, in denen Sie die im Thema zu verwendenden statischen Stile definieren.

   **Less-Variablendateien:** Das sind die Dateien, in denen Variablen definieren oder überschreiben, die beim Definieren von CSS-Stilen verwendet werden.

   Adaptive Formulare stellen OTTB-Variablen bereit, die in den folgenden .less-Dateien festgelegt werden:

   * `/apps/clientlibs/fd/af/guidetheme/common/less/globalvariables.less`
   * `/apps/clientlibs/fd/af/guidetheme/common/less/layoutvariables.less`

   Adaptive Formulare stellen auch Drittanbieter-Variablen bereit, die definiert wurden in:

   `/apps/clientlibs/fd/af/third-party/less/variables.less`

   Sie können die mit den adaptiven Formularen bereitgestellten „less“-Variablen verwenden, Sie können diese Variablen überschreiben oder Sie können neue „less“-Variablen erstellen.

   >[!NOTE]
   >
   >Beim Importieren der Dateien des niedrigeren Präprozessors in der Import-Anweisung müssen Sie den relativen Pfad der Dateien angeben.

   Variablen überschreibendes Muster:

   ```css
   @button-background-color: rgb(19, 102, 44);
   @button-border-color: rgb(19, 102, 44);
   @button-border-size: 0px;
   @button-padding: 10px 15px;
   @button-font-color: #ffffff;
   ```

   So überschreiben Sie die `less`-Variablen:

   1. So importieren Sie Standardvariablen für adaptive Formulare:

      `/apps/clientlibs/fd/af/guidetheme/common/less/globalvariables.less/apps/clientlibs/fd/af/guidetheme/common/less/layoutvariables.less`

   1. Importieren Sie dann die less-Datei, die überschriebene Variablen einbezieht.

   Muster für neue Variablendefinitionen:

   ```css
   @button-focus-bg-color: rgb(40, 208, 90);
   @button-hover-bg-color: rgb(30, 156, 67);
   ```

   **Less mixin-Dateien:** Sie können die Funktionen definieren, die Variablen als Argumente akzeptieren. Die Ausgabe dieser Funktionen sind die resultierenden Stile. Verwenden Sie diese mixins mit verschiedenen Stilen, um sich wiederholende CSS-Stile zu vermeiden.

   Adaptive Formulare stellen OTTB-Mixins bereit, die festgelegt werden in:

   * `/apps/clientlibs/fd/af/guidetheme/common/less/adaptiveforms-mixins.less`

   Adaptive Formulare stellen auch Drittanbieter-Mixins bereit, die definiert wurden in:

   * `/apps/clientlibs/fd/af/third-party/less/mixins.less`

   Definition für Muster-mixin:

   ```css
   .rounded-corners (@radius) {
     -webkit-border-radius: @radius;
     -moz-border-radius: @radius;
     -ms-border-radius: @radius;
     -o-border-radius: @radius;
     border-radius: @radius;
   }
   
   .border(@color, @type, @size) {
      border: @color @size @type;
   }
   ```

   **Styles.less-Datei:** Verwenden Sie diese Datei, um alle less-Dateien (Variablen, Mixins, Stile) einzubeziehen, die Sie in der Clientbibliothek verwenden müssen.

   In der folgenden Musterdatei `styles.less` kann die Importanweisung in jeder beliebigen Reihenfolge platziert werden.

   Die Anweisungen zum Importieren der folgenden .less-Dateien sind obligatorisch:

   * `globalvariables.less`
   * `layoutvariables.less`
   * `components.less`
   * `layouts.less`

   ```css
   @import "../../../clientlibs/fd/af/guidetheme/common/less/globalvariables.less";
   @import "../../../clientlibs/fd/af/guidetheme/common/less/layoutvariables.less";
   @import "forestTheme-variables";
   @import "../../../clientlibs/fd/af/guidetheme/common/less/components.less";
   @import "../../../clientlibs/fd/af/guidetheme/common/less/layouts.less";
   
   /* custom styles */
   
   .guidetoolbar {
     input[type="button"], button, .button {
       .rounded-corners (@button-radius);
       &:hover {
         background-color: @button-hover-bg-color;
       }
       &:focus {
         background-color: @button-focus-bg-color;
       }
     }
   }
   
   form {
       background-image: url(../images/forest.png);
    background-repeat: no-repeat;
    background-size: 100%;
   }
   ```

   Die `css.txt` enthält den Pfad der .css-Dateien, die für die Bibliothek heruntergeladen werden soll.

   Beispiel:

   ```javascript
   #base=/apps/clientlibs/fd/af/third-party/css
   bootstrap.css
   
   #base=less
   styles.less
   
   #base=/apps/clientlibs/fd/xfaforms/xfalib/css
   datepicker.css
   listboxwidget.css
   scribble.css
   dialog.css
   ```

   >[!NOTE]
   >
   >Die styles.less-Datei ist nicht obligatorisch: Das bedeutet, dass Sie diese Datei nicht erstellen können, wenn Sie keine benutzerdefinierten Stile, Variablen oder Mixins definiert haben.
   >
   >Wenn Sie jedoch keine style.less-Datei erstellen, müssen Sie den Kommentar für folgende Linie löschen:
   >
   >**`#base=less`**
   >
   >Und geben Sie für die folgende Linie einen Kommentar ein:
   >
   >**`styles.less`**

## So verwenden Sie ein Thema in einem adaptiven Formular {#to-use-a-theme-in-an-adaptive-form}

Nachdem Sie das Thema für adaptives Formular erstellt haben, führen Sie die folgenden Schritte durch, um dieses Thema in einem adaptiven Formular zu verwenden:

1. Wenn Sie ein Thema einbeziehen möchten, das im Abschnitt [Erstellen eines Themas für ein adaptives Formular](/help/forms/using/creating-custom-adaptive-form-themes.md#p-to-create-an-adaptive-form-theme-p) erstellt wurde, erstellen Sie eine benutzerdefinierte Seite des Typs `cq:Component`.

   Beispiel: `/apps/myAfCustomizations/myAfPages/forestPage`

   1. Fügen Sie eine `sling:resourceSuperType`-Eigenschaft hinzu und stellen Sie ihren Wert auf `fd/af/components/page/base` ein.

      ![Snapshot zum CRX-Repository](assets/1-2.png)

   1. Wenn Sie auf einer Seite ein Thema verwenden möchten, müssen Sie dem Knoten eine überschreibende library.jsp-Datei hinzufügen.

      Anschließend können Sie das Thema importieren, das im Abschnitt „So erstellen Sie ein Thema für ein adaptives Formular“ dieses Artikels erstellt wurde.

      Das folgende Muster-Codefragment importiert das Thema `af.theme.forest`.

      ```jsp
      <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
      <cq:includeClientLib categories="af.theme.forest"/>
      ```

   1. **Optional:** Überschreiben Sie die benutzerdefinierte Seite, überschreiben Sie je nach Bedarf „header.hsp“, „footer.jsp“ und „body.jsp“.

1. Erstellen Sie eine benutzerdefinierte Vorlage (zum Beispiel: `/apps/myAfCustomizations/myAfTemplates/forestTemplate`/) deren „jcr:content“ auf die benutzerdefinierte Seite zeigt, die im vorangehenden Schritt erstellt wurde (zum Beispiel: `myAfCustomizations/myAfPages/forestPage)`.

   ![Snapshot zum CRX-Repository](assets/2-1.png)

1. Erstellen Sie ein adaptives Formular mithilfe der im vorherigen Schritt erstellten Vorlage. Das Erscheinungsbild des adaptiven Formulars wird durch das Thema definiert, das im Abschnitt „So erstellen Sie ein Thema für ein adaptives Formular“ dieses Artikels erstellt wurde.
