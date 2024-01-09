---
title: Wie werden Designs für adaptive Formulare erstellt oder angepasst?
description: Erfahren Sie, wie Sie mithilfe von BEM-Spezifikationen Designs für Kernkomponenten adaptiver Formulare erstellen oder anpassen können.
keywords: Design der Kernkomponenten für adaptive Formulare erstellen, neues Design erstellen, Design anpassen, neues Design hochladen, Design in Formularen verwenden, Design löschen, Design in AEM 6.5-Formularen erstellen
contentOwner: Khushwant Singh
topic-tags: Adaptive Forms
docset: aem65
role: Admin, Developer
feature: Adaptive Forms, Core Components
exl-id: 9f9b35a3-0479-4179-9fad-994a482c96b6
source-git-commit: 4a8155f754d1f71354717f5eb22511baab110916
workflow-type: tm+mt
source-wordcount: '1921'
ht-degree: 98%

---

# Erstellen oder Anpassen eines Designs für ein adaptives Formular {#introduction-to-theme}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=de) |
| AEM 6.5 | Dieser Artikel |


<!--**Applies to:** ✅ Adaptive Form Core Components ❎ [Adaptive Form Foundation Components](/help/forms/using/create-adaptive-form.md).-->

In AEM Forms 6.5 ist ein Design eine AEM Client-Bibliothek, mit der Sie die Stile (Look-and-Feel) für ein adaptives Formular definieren. Zu einem Design gehören Stildetails für die Komponenten und Bedienfelder. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegeln die entsprechenden Komponenten den angegebenen Stil wider. Ein Design wird ohne Verweis auf ein adaptives Formular unabhängig verwaltet und kann über mehrere adaptive Formulare hinweg wiederverwendet werden.

## Verfügbare Designs {#available-theme}

Die AEM 6.5-Umgebung bietet die folgenden aufgelisteten Designs für auf Kernkomponenten-basierte adaptive Formulare:

* [Canvas-Design](https://github.com/adobe/aem-forms-theme-canvas)
* [Design „WKND“](https://github.com/adobe/aem-forms-theme-wknd)
* [Design „EASEL“](https://github.com/adobe/aem-forms-theme-easel)

## Grundlegendes zur Struktur der Designs {#understanding-structure-of-theme}

Ein Design ist ein Paket, das die CSS-Datei, JavaScript-Dateien und Ressourcen (wie etwa Symbole) umfasst, die den Stil Ihrer adaptiven Formulare definieren. Ein Design für ein adaptives Formular folgt einer bestimmten Organisation, die aus den folgenden Komponenten besteht:

* `src/theme.scss`: Dieser Ordner enthält die CSS-Datei, die einen großen Einfluss auf das gesamte Thema hat. Sie dient als zentralisierter Speicherort zur Definition und Verwaltung des Stils und Verhaltens Ihres Designs. Durch Bearbeitung dieser Datei können Sie Änderungen vornehmen, die im gesamten Design allgemein angewendet werden und das Erscheinungsbild und die Funktionalität Ihrer adaptiven Formular- und AEM Sites-Seiten beeinflussen.

* `src/site`: Dieser Ordner enthält CSS-Dateien, die auf die gesamte Seite einer AEM-Site angewendet werden. Diese Dateien bestehen aus Code und Stilen, die die Gesamtfunktionalität und das Layout der Seite Ihrer AEM-Site beeinflussen. Alle hier vorgenommenen Änderungen werden auf sämtlichen Seiten Ihrer Site übernommen.

* `src/components`: Die CSS-Dateien in diesem Ordner wurden für einzelne AEM-Kernkomponenten entwickelt. Jeder spezielle Ordner für eine Komponente enthält eine `.scss`-Datei, die die jeweilige Komponente in einem adaptiven Formular formatiert. Die Datei `/src/components/button/_button.scss` enthält zum Beispiel Stilinformationen für die Komponente „Schaltfläche von adaptiven Formularen“.

  ![Struktur des Canvas-Designs](/help/forms/using/assets/component-based-theme-folder-structure.png)

* `src/resources`: Dieser Ordner enthält statische Dateien wie Symbole, Logos und Schriftarten. Diese Ressourcen werden verwendet, um die visuellen Elemente und das gesamte Erscheinungsbild Ihres Designs zu verbessern.

## Erstellen eines Designs

AEM Forms 6.5 bietet die folgenden aufgelisteten Designs für Kernkomponenten-basierte adaptive Formulare.

* [Canvas-Design](https://github.com/adobe/aem-forms-theme-canvas)
* [Design „WKND“](https://github.com/adobe/aem-forms-theme-wknd)
* [Design „EASEL“](https://github.com/adobe/aem-forms-theme-easel)

Sie können [jedes dieser Designs anpassen, um ein Design zu erstellen](#customize-a-theme-core-components).

## Anpassen eines Designs {#customize-a-theme-core-components-based-adaptive-forms}

Das Anpassen eines Designs bezieht sich auf den Prozess der Änderung und Personalisierung des Erscheinungsbilds eines Designs. Wenn Sie ein Design anpassen, ändern Sie dessen Design-Elemente, Layout, Farben, Typografie und manchmal den zugrunde liegenden Code. Auf diese Weise können Sie ein einzigartiges und maßgeschneidertes Erscheinungsbild für Ihre Website oder Anwendung erstellen und dabei die grundlegende Struktur und Funktionalität des Designs beibehalten.

>[!NOTE]
>
> * Verwenden Sie den Package Manager, um ein Design auf allen Autoren- und Veröffentlichungsinstanzen bereitzustellen.
> * Eine Design-Client-Bibliothek wird wie jedes andere Paket über Package Manager importiert oder exportiert.

### Voraussetzungen zum Anpassen eines Designs {#prerequisites}

* [Aktivieren der Kernkomponenten adaptiver Formulare für Ihre Umgebung.](/help/forms/using/enable-adaptive-forms-core-components.md)

* Installieren Sie die neueste Version von [Apache Maven.](https://maven.apache.org/download.cgi) Apache Maven ist ein Tool zur Automatisierung von Builds, das häufig für Java™-Projekte verwendet wird. Durch die Installation der neuesten Version stellen Sie sicher, dass Sie über die erforderlichen Abhängigkeiten für die Design-Anpassung verfügen.

* Erfahren Sie, wie Sie eine [Client-Bibliothek in Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=de) erstellen. AEM stellt Client-Bibliotheken zur Verfügung, mit denen Sie Ihren Client-seitigen Code im Repository speichern, in Kategorien organisieren und definieren können, wann und wie jede Code-Kategorie dem Client bereitgestellt werden soll.

* Installieren Sie einen Nur-Text-Editor. Beispielsweise Microsoft® Visual Studio Code. Die Verwendung eines Texteditors wie Microsoft® Visual Studio Code bietet eine benutzerfreundliche Umgebung zum Bearbeiten und Ändern von Design-Dateien.

* Stellen Sie sicher, dass Ihre AEM Forms-Umgebung betriebsbereit ist.

### Überlegungen zum Anpassen eines Designs {#consideration}

* Stellen Sie sicher, dass Sie [das Archetyp-Projekt verwenden, das zur Aktivierung der Kernkomponenten von adaptiven Formularen](/help/forms/using/enable-adaptive-forms-core-components.md) in Ihrer Umgebung verwendet wird, um Ihre Designs anzupassen.

* Beim Veröffentlichen eines adaptiven Formulars werden die Client-Bibliotheken nicht automatisch in der Veröffentlichungsinstanz veröffentlicht. Stellen Sie sicher, dass Sie die in einem adaptiven Formular referenzierte Client-Bibliothek manuell in Ihren Veröffentlichungsumgebungen veröffentlichen.

* Adobe empfiehlt, die Klassennamen von Client-Bibliotheken nicht zu ändern.

### Anpassen eines Designs {#customize-a-theme-core-components}

Das Erstellen oder Anpassen eines Designs ist ein mehrstufiger Prozess. Führen Sie die Schritte in der angegebenen Reihenfolge aus, um das Design zu erstellen/anzupassen:

1. [Klonen eines Designs](#clone-git-repo-of-theme)
1. [Anpassen der Darstellung des Designs](#customize-the-theme)
1. [Bereitstellen des Designs für die lokale Bereitstellung](#generate-the-clientlib)
1. [Bereitstellen des Designs in einer lokalen Umgebung](#deploy-the-theme-on-a-local-environment)
1. [Bereitstellen des Designs in der Produktionsumgebung](#5-deploy-a-theme-on-your-production-environment)

<!--
 ![Theme Customization workflow](/help/forms/using/assets/custom-theme-steps.png)
-->

Die Beispiele in diesem Dokument basieren auf dem **Canvas**-Design, aber Sie können jedes beliebige Design klonen und es mit denselben Anweisungen anpassen. Diese Anweisungen gelten für jedes Design, sodass Sie Designs entsprechend Ihren spezifischen Anforderungen ändern können.

#### 1. Klonen Sie das Git-Repository des Designs {#clone-git-repo-of-theme}

Um ein Design für die auf Kernkomponenten-basierten adaptiven Formulare zu klonen, wählen Sie eines der folgenden Designs:

* [Canvas-Design](https://github.com/adobe/aem-forms-theme-canvas)
* [Design „WKND“](https://github.com/adobe/aem-forms-theme-wknd)
* [Design „EASEL“](https://github.com/adobe/aem-forms-theme-easel)

Führen Sie die folgenden Anweisungen aus, um ein Design zu klonen:

1. Öffnen Sie die Eingabeaufforderung oder das Terminal-Fenster in Ihrer lokalen Entwicklungsumgebung.

1. Führen Sie den Befehl `git clone` aus, um ein Design zu klonen.

   ```
      git clone [Path of Git Repository of the theme]
   ```

   Ersetzen Sie den [Pfad des Git-Repositorys des Designs] durch die tatsächliche URL des entsprechenden Git-Repositorys des Designs.

   Um beispielsweise das Canvas-Design zu klonen, führen Sie den folgenden Befehl aus:

   ```
      git clone https://github.com/adobe/aem-forms-theme-canvas
   ```

1. Wählen Sie **Trust the authors of all files in the parent folder** und klicken Sie auf **Yes, I trust the authors**.

Nach erfolgreicher Ausführung des Befehls haben Sie eine lokale Kopie des Designs auf Ihrem Rechner im Ordner `aem-forms-theme-canvas` zur Verfügung.

#### 2. Passen Sie das Design an {#customize-the-theme}

Sie haben die Möglichkeit, einzelne Komponenten anzupassen oder Änderungen auf Design-Ebene vorzunehmen, indem Sie die globalen Variablen eines Designs verwenden. Die Änderung globaler Variablen hat einen kaskadierenden Effekt auf alle einzelnen Komponenten. Sie können beispielsweise globale Variablen verwenden, um die Rahmenfarbe aller Komponenten in einem adaptiven Formular zu ändern, oder eine dynamische Füllfarbe auf Aktionsaufruf-Schaltflächen (CTA) anzuwenden. Sie haben folgende Möglichkeiten:

* [Festlegen von Stilen auf Design-Ebene](#theme-customization-global-level)

* [Festlegen von Stilen auf Komponentenebene](#component-based-customization)

##### Festlegen von Stilen auf Design-Ebene {#theme-customization-global-level}

Die Datei `variable.scss` enthält die globalen Variablen des Designs. Durch Aktualisierung dieser Variablen können Sie stilistisch relevante Änderungen auf der Design-Ebene vornehmen. Gehen Sie wie folgt vor, um Stile auf Design-Ebene anzuwenden:

1. Öffnen Sie die Datei `<your-theme-sources>/src/site/_variables.scss` zur Bearbeitung.
1. Ändern Sie den Wert einer beliebigen Eigenschaft. Beispielsweise ist die Standardfehlerfarbe Rot. Um die Fehlerfarbe von Rot auf Blau zu ändern, ändern Sie den Farb-Hex-Code der Variablen `$error`. Zum Beispiel: `$error: #196ee5`.

   ![Beispiel: Fehlerfarbe auf Blau gesetzt](/help/forms/using/assets/theme-level-changes.png)

1. Speichern und schließen Sie die Datei.


In ähnlicher Weise können Sie die Datei `variable.scss` verwenden, um Schriftfamilie und -typ, Design- und Schriftfarben, Schriftgröße, Design-Abstände, Fehlersymbole, Rahmenstile des Designs und weitere Variablen festzulegen, die sich auf mehrere adaptive Formularkomponenten auswirken.

##### Festlegen von Stilen auf Komponentenebene {#component-based-customization}

Sie können auch die Schriftart, Farbe, Größe und andere CSS-Eigenschaften bestimmter Kernkomponenten des adaptiven Formulars anpassen, z. B. Schaltflächen, Kontrollkästchen, Container, Fußzeilen und mehr. Durch Bearbeiten der CSS-Datei, die mit der jeweiligen Komponente verknüpft ist, können Sie deren Stil an das Branding Ihres Unternehmens anpassen. Gehen Sie wie folgt vor, um den Stil einer Komponente anzupassen:

1. Öffnen Sie die Datei `<your-theme-sources>/src/components/<component>/<component.scss>` zur Bearbeitung. Um zum Beispiel die Schriftfarbe der Schaltflächenkomponente zu ändern, öffnen Sie die Datei `<your-theme-sources>/src/components/button/button.scss`.
1. Ändern Sie die Werte entsprechend Ihren Anforderungen. Wenn Sie beispielsweise die Farbe der Schaltflächenkomponente beim Darüberfahren mit der Maus in Grün ändern möchten, ändern Sie den Wert der Eigenschaft `color: $white` in der Klasse `cmp-adaptiveform-button__widget:hover` in den Hex-Code „#12b453“ oder einen anderen Grünton. Der endgültige Code sieht wie folgt aus:

   ```
    .cmp-adaptiveform-button__widget:hover {
    background: $dark-gray;
    color: #12b453;
    }
   ```


1. Speichern und schließen Sie die Datei.

<!--

   ![Example: Hover color set to green](/help/forms/using/assets/button-customization.png)

-->

>[!NOTE]
>
> Wenn ein Stil sowohl auf Design- als auch auf Komponentenebene definiert ist, hat der auf Komponentenebene definierte Stil Priorität.

#### 3. Bereiten Sie das Design für die Bereitstellung vor. {#generate-the-clientlib}

Um ein Design in einer AEM-Instanz bereitzustellen, muss es in eine Client-Bibliothek konvertiert werden. Führen Sie die folgenden Schritte aus, um das Design in eine Client-Bibliothek zu konvertieren:

1. Öffnen Sie die Eingabeaufforderung oder das Terminal-Fenster.
1. Navigieren Sie zum Ordner `<your-theme-sources>`. Zum Beispiel: `C:\aem-forms-theme-canvas`
1. Führen Sie den folgenden Befehl aus:

   ```
      npm run create-clientlib --category=adaptiveform.theme.[yourtheme]
   ```

   Ersetzen Sie `[yourtheme]` durch den Namen Ihres benutzerdefinierten Designs. Wenn der Name des benutzerdefinierten Designs beispielsweise `customcanvastheme` lautet, führen Sie den folgenden Befehl aus:

   ```
       npm run create-clientlib --category=adaptiveform.theme.customcanvastheme
   ```

   Bei erfolgreicher Ausführung des Befehls wird ein Client-Bibliotheksordner unter `themerepo\theme-clientlibs\[yourtheme]` erstellt.

   ![Client-Bibliothekserstellung](/help/forms/using/assets/clientlib_created.png)


   ![Client-Bibliotheksspeicherort](/help/forms/using/assets/adaptiveform.theme.easel.png)

#### 4. Bereitstellen des Designs in einer lokalen Umgebung {#deploy-the-theme-on-a-local-environment}

Gehen Sie wie folgt vor, um das Design in Ihrer lokalen Entwicklungs- oder Testumgebung bereitzustellen:

1. Kopieren Sie die im vorherigen Abschnitt erstellte Client-Bibliothek in Ihr Archetyp-Projekt unter folgendem Pfad:

   `/ui.apps/src/main/content/jcr_root/apps/[AEM Archetype Project Folder]/clientlibs/<yourtheme>`

1. Öffnen Sie die Eingabeaufforderung oder das Terminal.
1. Navigieren Sie zum Stammverzeichnis Ihres AEM Archetyp-Projekts, dem Projekt, das zur Aktivierung der Kernkomponenten des adaptiven Formulars verwendet wird.
1. Führen Sie den folgenden Befehl aus, um das benutzerdefinierte Design in Ihrer Umgebung bereitzustellen:

   `mvn clean install`

   ![Client-Bibliotheks-Build](/help/forms/using/assets/mvndeploy.png)

<!--

#### 5. Test the theme with a local Adaptive Form {#test-the-theme-with-a-local-adaptive-form}

To apply and test the customized theme with an Adaptive Form:

**Apply theme while creating an Adaptive Form**

1. Log in to your AEM Forms author instance. 

1. Select **Adobe Experience Manager** > **Forms** > **Forms & Documents**.

1. Click **Create** > **Adaptive Forms**. The wizard for creating Adaptive Form opens.

1. Select the core component template in the **Source** tab.
1. Select the theme in the **Style** tab.
1. Click **Create**.

An Adaptive Form with the selected theme is created. 

**Apply theme to an existing Adaptive Form**

1. Log in to your AEM Forms author instance. 

1. Select **Adobe Experience Manager** > **Forms** > **Forms & Documents**.

1. Select an Adaptive Form and click Properties. 

1. For the **Theme Client Library** option, select the theme. 

1. Click **Save & Close**.

The selected theme is applied to the Adaptive Form. 
-->

#### 5. Bereitstellen eines Designs in Ihrer Produktionsumgebung {#deploy-theme}

Nachdem Sie das Design in Ihrer lokalen Entwicklungsumgebung erfolgreich getestet haben, können Sie mit der Bereitstellung des Designs in Ihren Produktionsumgebungen fortfahren, einschließlich der Autoren- und der Veröffentlichungsinstanz. Führen Sie die folgenden Schritte aus, um das Design in Ihren Produktionsumgebungen bereitzustellen:

1. Melden Sie sich bei Ihrer AEM-Umgebung an.
1. Öffnen Sie Package Manager. Die Standard-URL ist `https://localhost:4502/crx/packmgr/index.jsp`.
1. Klicken Sie auf **Paket hochladen** und auf **Durchsuchen**.
1. Navigieren Sie zu und wählen Sie `[AEM Archetype Project Folder]\all\target[appid].all-[version].zip` aus. Klicken Sie auf **Öffnen**.
1. Klicken Sie auf „Installieren“. Wiederholen Sie diesen Schritt für alle Produktionsumgebungen.


Wenn das Paket installiert wurde, ist das Design zur Auswahl verfügbar.

![Design-Client-Bibliothek](/help/forms/using/assets/themeclientlibrary.png)

>[!NOTE]
>
>
> Sollten Sie Schwierigkeiten haben, den Anmeldedialog auf einer Veröffentlichungsinstanz aufzurufen, um das Paket über Package Manager zu installieren, versuchen Sie, sich über die folgende URL anzumelden: `http://[Publish Server URL]:[PORT]/system/console`. Dies ermöglicht den Zugriff auf die Veröffentlichungsinstanz, sodass Sie mit dem Installationsprozess fortfahren können.

## Anwenden eines Designs auf ein adaptives Formular {#using-theme-in-adaptive-form}

Schritte zum Anwenden eines Designs auf ein adaptives Formular:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an.
1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein. Auswählen **Adobe Experience Manager** > **Forms** > **Forms und Dokumente**.
1. Klicken Sie auf **Erstellen** > **Adaptive Formulare**.
1. Wählen Sie eine Vorlage mit Kernkomponenten für adaptive Formulare aus und klicken Sie auf **Weiter**. Es wird **Eigenschaften hinzufügen** angezeigt
1. Geben Sie den **Namen** für Ihr adaptives Formular an.


   >[!NOTE]
   >
   > * Standardmäßig wird das Design `adaptiveform.theme.canvas3` ausgewählt.
   > * Sie können im Dropdown-Menü **Design-Client-Bibliothek** ein anderes Design auswählen.

1. Klicken Sie auf **Erstellen**.

Designs für adaptive Formulare werden als Teil einer Vorlage für adaptive Formulare verwendet, um beim Erstellen eines adaptiven Formulars Stile zu definieren.

## Löschen eines Designs {#delete-a-theme}

Entfernen nicht verwendeter oder unerwünschter Designs

1. Melden Sie sich bei Ihrer Autoreninstanz an.
1. Öffnen Sie `http://[Publish Server URL]:[PORT]/crx/de/index.jsp`
1. Navigieren Sie zu `apps/[AEM Archetype Project Folder]/clientlibs/[yourtheme]`.
1. Löschen Sie den Design-Ordner und speichern Sie die Änderungen.


## Häufig gestellte Fragen {#faq}

**F:** Welche Anpassung hat Vorrang, wenn Anpassungen in einem Design-Ordner sowohl auf der globalen Ebene als auch auf der Komponentenebene vorgenommen werden?

**A:** Wenn ein Stil sowohl auf der Design- als auch auf der Komponentenebene definiert ist, hat der auf der Komponentenebene definierte Stil Vorrang.

**F:** Welche Schritte sollten unternommen werden, wenn das benutzerdefinierte Design nicht in der **[!UICONTROL Design-Client-Bibliothek]** sichtbar ist?

**A:** Wenn Ihr benutzerdefiniertes Design nicht in der Dropdown-Liste **[!UICONTROL Design-Client-Bibliothek]** angezeigt wird, führen Sie folgende Schritte aus:

1. Navigieren Sie zu dem Speicherort, an dem Sie Ihre benutzerdefinierte Design-Client-Bibliothek hinzugefügt haben. Der empfohlene Pfad ist `/ui.apps/src/main/content/jcr_root/apps[AEM Archetype Project Folder]/clientlibs/<yourtheme>`.

1. Öffnen Sie die Datei `.content.xml` und fügen Sie die folgenden Metadaten ein:

   ```
       formstheme:true
       allowproxy:true
   ```

1. Speichern Sie die Datei und stellen Sie das Design erneut bereit.

## Siehe auch

* [Erstellen eines auf Kernkomponenten basierenden adaptiven Formulars](create-an-adaptive-form-core-components.md)
* [Verwenden des Regeleditors, um dem Formular dynamisches Verhalten hinzuzufügen](rule-editor.md)
* [Erstellen oder Anpassen von Designs für auf Kernkomponenten basierende adaptive Formulare](create-or-customize-themes-for-adaptive-forms-core-components.md)
* [Erstellen einer Vorlage für auf Kernkomponenten basierende adaptive Formulare](template-editor.md)
* [Erstellen oder Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment](create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Beispielthemenvorlagen und Formulardatenmodelle](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html?lang=de)
