---
title: Wie werden Themen für adaptive Formulare erstellt oder angepasst?
seo-title: How to create a theme for Adaptive Forms Core Components?
description: Erfahren Sie, wie Sie Designs für adaptive Forms-Kernkomponenten mithilfe von BEM-Spezifikationen erstellen oder anpassen.
seo-description: Learn to create or customize themes for Adaptive Forms Core Components using BEM specifications
keywords: Design der Kernkomponenten für adaptive Formulare erstellen, neues Design erstellen, Design anpassen, neues Design hochladen, Design in Formularen verwenden, Design löschen, Design in AEM 6.5 Formularen erstellen
contentOwner: Khushwant Singh
topic-tags: Adaptive Forms
docset: aem65
role: Admin, Developer
source-git-commit: 00f8b2c72aab37a57ab76e684f432250d2de3470
workflow-type: tm+mt
source-wordcount: '1968'
ht-degree: 9%

---


# Erstellen oder Anpassen eines Designs für ein adaptives Formular {#introduction-to-theme}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | Dieser Artikel |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html) |

**Gilt für:** ✅ Kernkomponenten des adaptiven Formulars ❎ [Foundation-Komponenten für adaptive Formulare](/help/forms/using/themes.md).

In AEM Forms 6.5 ist ein Design eine AEM Client-Bibliothek, mit der Sie die Stile (Erscheinungsbild) für ein adaptives Formular definieren. Zu einem Design gehören Stildetails für die Komponenten und Bedienfelder. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegeln die entsprechenden Komponenten den angegebenen Stil wider. Ein Design wird unabhängig voneinander ohne Verweis auf ein adaptives Formular verwaltet und kann über mehrere adaptive Forms hinweg wiederverwendet werden.

## Verfügbare Designs {#available-standard-theme}

AEM Umgebung 6.5 bietet die folgenden aufgelisteten Designs für Kernkomponenten-basierte adaptive Forms:

* [Arbeitsflächendesign](https://github.com/adobe/aem-forms-theme-canvas)
* [WKND-Design](https://github.com/adobe/aem-forms-theme-wknd)
* [EASEL-Design](https://github.com/adobe/aem-forms-theme-easel)

## Grundlegendes zur Struktur der Themen {#understanding-structure-of-theme}

Ein Design ist ein Paket, das die CSS-Datei, JavaScript-Dateien und Ressourcen (wie Symbole) umfasst, die den Stil Ihres adaptiven Forms definieren. Ein Design für adaptives Formular folgt einer bestimmten Organisation, die aus den folgenden Komponenten besteht:

* `src/theme.scss`: Dieser Ordner enthält die CSS-Datei, die sich auf das gesamte Design auswirkt. Es dient als zentralisierter Ort zur Definition und Verwaltung des Stils und Verhaltens Ihres Designs. Durch Bearbeitung dieser Datei können Sie Änderungen vornehmen, die im gesamten Design allgemein angewendet werden und das Erscheinungsbild und die Funktionalität Ihrer adaptiven Forms- und AEM Sites-Seiten beeinflussen.

* `src/site`: Dieser Ordner enthält CSS-Dateien, die auf die Seite einer gesamten AEM Site angewendet werden. Diese Dateien bestehen aus Code und Stilen, die sich auf die Funktionalität und das Layout der Seite Ihrer AEM auswirken. Alle hier vorgenommenen Änderungen werden auf allen Seiten Ihrer Site übernommen.

* `src/components`: Die CSS-Dateien in diesem Ordner sind für einzelne AEM Kernkomponenten konzipiert. Jeder dedizierte Ordner für eine Komponente enthält eine `.scss` -Datei, die diese bestimmte Komponente in einem adaptiven Formular formatiert. Beispielsweise wird die `/src/components/button/_button.scss` -Datei enthält Stilinformationen für die Komponente &quot;Adaptive Forms-Schaltfläche&quot;.

  ![Canvas-Design-Struktur](/help/forms/using/assets/component-based-theme-folder-structure.png)

* `src/resources`: Dieser Ordner enthält statische Dateien wie Symbole, Logos und Schriftarten. Diese Ressourcen werden verwendet, um die visuellen Elemente und das Gesamtdesign Ihres Designs zu verbessern.

## Erstellen von Designs

AEM Forms 6.5 bietet die folgenden Standardthemen für Kernkomponenten-basierte adaptive Forms.

* [Arbeitsflächendesign](https://github.com/adobe/aem-forms-theme-canvas)
* [WKND-Design](https://github.com/adobe/aem-forms-theme-wknd)
* [EASEL-Design](https://github.com/adobe/aem-forms-theme-easel)

Sie können [Anpassen dieser Standarddesigns, um ein Design zu erstellen](#customize-a-theme-core-components).

## Anpassen eines Designs {#customize-a-theme-core-components-based-adaptive-forms}

Das Anpassen eines Designs bezieht sich auf den Prozess der Änderung und Personalisierung des Erscheinungsbilds eines Designs. Wenn Sie ein Design anpassen, nehmen Sie Änderungen an seinen Designelementen, Layout, Farben, Typografie und manchmal am zugrunde liegenden Code vor. Dadurch können Sie ein einzigartiges und maßgeschneidertes Erscheinungsbild für Ihre Website oder Anwendung erstellen und dabei die grundlegende Struktur und Funktionalität des Designs beibehalten.

>[!NOTE]
>
> * Verwenden Sie den Package Manager, um ein Design auf allen Autoren- und Veröffentlichungsinstanzen bereitzustellen.
> * Eine Design-Client-Bibliothek wird wie jedes andere Paket über Package Manager importiert oder exportiert.

### Voraussetzungen für die Anpassung eines Designs {#prerequisites}

* [Aktivieren der adaptiven Forms-Kernkomponenten](/help/forms/using/enable-adaptive-forms-core-components.md) für Ihre Umgebung.

* Installieren Sie die neueste Version von [Apache Maven.](https://maven.apache.org/download.cgi) Apache Maven ist ein Werkzeug zur Automatisierung von Builds, das häufig für Java™-Projekte verwendet wird. Durch die Installation der neuesten Version wird sichergestellt, dass Sie über die erforderlichen Abhängigkeiten für die Designanpassung verfügen.

* Erfahren Sie, wie Sie eine [Client-Bibliothek in Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=de). AEM bietet Client-Bibliotheken, mit denen Sie Ihren clientseitigen Code im Repository speichern, in Kategorien organisieren und definieren können, wann und wie jede Codekategorie dem Client bereitgestellt werden soll.

* Installieren Sie einen Nur-Text-Editor. Beispielsweise Microsoft® Visual Studio-Code. Die Verwendung eines Texteditors wie Microsoft® Visual Studio Code bietet eine benutzerfreundliche Umgebung zum Bearbeiten und Ändern von Designdateien.

* Stellen Sie sicher, dass die AEM Forms-Umgebung aktiv ist.

### Überlegungen zum Anpassen eines Designs {#consideration}

* Stellen Sie sicher, dass Sie [das Archetyp-Projekt, das zur Aktivierung der adaptiven Forms-Kernkomponenten verwendet wird](/help/forms/using/enable-adaptive-forms-core-components.md) in Ihrer Umgebung, um Ihre Designs anzupassen.

* Beim Veröffentlichen eines adaptiven Formulars werden die Client-Bibliotheken nicht automatisch in der Veröffentlichungsinstanz veröffentlicht. Stellen Sie sicher, dass Sie die in einem adaptiven Formular referenzierte Client-Bibliothek manuell in Ihren Veröffentlichungsumgebungen veröffentlichen.

* Adobe empfiehlt, die Klassennamen von Client-Bibliotheken nicht zu ändern.

### Anpassen eines Designs {#customize-a-theme-core-components}

Das Erstellen oder Anpassen eines Designs ist ein mehrstufiger Prozess. Führen Sie die Schritte in der angegebenen Reihenfolge aus, um das Design zu erstellen/anzupassen:

1. [Klonen eines Standarddesigns](#clone-git-repo-of-theme)
1. [Anpassen der Darstellung des Designs](#customize-the-theme)
1. [Design für lokale Bereitstellung bereitstellen](#generate-the-clientlib)
1. [Bereitstellen des Designs in einer lokalen Umgebung](#deploy-the-theme-on-a-local-environment)
1. [Bereitstellen des Designs in der Produktionsumgebung](#5-deploy-a-theme-on-your-production-environment)

<!--
 ![Theme Customization workflow](/help/forms/using/assets/custom-theme-steps.png)
-->

Die im Dokument bereitgestellten Beispiele basieren auf dem **Arbeitsfläche** -Design, Sie können jedoch jedes Standarddesign klonen und es mit denselben Anweisungen anpassen. Diese Anweisungen gelten für jedes Thema, sodass Sie Designs entsprechend Ihren spezifischen Anforderungen ändern können.

#### 1. Klonen Sie das Git-Repository des Designs {#clone-git-repo-of-theme}

Um ein Standarddesign für auf Kernkomponenten basierende adaptive Forms zu klonen, wählen Sie eines der folgenden Standardthemen aus:

* [Arbeitsflächendesign](https://github.com/adobe/aem-forms-theme-canvas)
* [WKND-Design](https://github.com/adobe/aem-forms-theme-wknd)
* [EASEL-Design](https://github.com/adobe/aem-forms-theme-easel)

Führen Sie die folgenden Anweisungen aus, um ein Standarddesign zu klonen:

1. Öffnen Sie die Eingabeaufforderung oder das Terminal-Fenster in Ihrer lokalen Entwicklungsumgebung.

1. Führen Sie die `git clone` -Befehl zum Klonen eines Designs.

   ```
      git clone [Path of Git Repository of the theme]
   ```

   Ersetzen Sie die [Pfad des Git-Repositorys des Designs] mit der tatsächlichen URL des entsprechenden Git-Repositorys des Designs

   Um beispielsweise das Canvas-Design zu klonen, führen Sie den folgenden Befehl aus:

   ```
      git clone https://github.com/adobe/aem-forms-theme-canvas
   ```

1. Wählen Sie **Trust the authors of all files in the parent folder** und klicken Sie auf **Yes, I trust the authors**.

Nachdem Sie den Befehl erfolgreich ausgeführt haben, steht auf Ihrem Computer eine lokale Kopie des Designs im  `aem-forms-theme-canvas` Ordner.

#### 2. Passen Sie das Design an {#customize-the-theme}

Sie haben die Flexibilität, einzelne Komponenten anzupassen oder Änderungen auf Designebene mithilfe der globalen Variablen eines Designs vorzunehmen. Die Änderung globaler Variablen hat einen kaskadierenden Effekt auf alle einzelnen Komponenten. Sie können beispielsweise globale Variablen verwenden, um die Rahmenfarbe aller Komponenten in einem adaptiven Formular zu ändern, oder eine dynamische Füllfarbe auf Aktionsaufruf-Schaltflächen (CTA) anwenden. Sie haben folgende Möglichkeiten:

* [Festlegen von Stilen auf Designebene](#theme-customization-global-level)

* [Festlegen von Stilen auf Komponentenebene](#component-based-customization)

##### Festlegen von Stilen auf Designebene {#theme-customization-global-level}

Die `variable.scss` -Datei enthält die globalen Variablen des Designs. Durch Aktualisierung dieser Variablen können Sie stilistisch relevante Änderungen auf der Designebene vornehmen. Gehen Sie wie folgt vor, um Stile auf Designebene anzuwenden:

1. Öffnen Sie die Datei `<your-theme-sources>/src/site/_variables.scss`, um sie zu bearbeiten.
1. Ändern Sie den Wert einer beliebigen Eigenschaft. Beispielsweise ist die Standardfehlerfarbe Rot. Um die Fehlerfarbe von Rot in Blau zu ändern, ändern Sie den Farb-Hex-Code der `$error`-Variable. Beispiel: `$error: #196ee5`.

   ![Beispiel: Fehlerfarbe auf blau eingestellt](/help/forms/using/assets/theme-level-changes.png)

1. Speichern und schließen Sie die Datei.


Auf ähnliche Weise können Sie die `variable.scss` -Datei, um Schriftfamilie und -typ, Design- und Schriftfarben, Schriftgröße, Designabstand, Fehlersymbol, Designrahmenstile und mehr Variablen festzulegen, die sich auf mehrere adaptive Formularkomponenten auswirken.

##### Festlegen von Stilen auf Komponentenebene {#component-based-customization}

Sie können auch die Schriftart, Farbe, Größe und andere CSS-Eigenschaften bestimmter Kernkomponenten des adaptiven Formulars anpassen, z. B. Schaltflächen, Kontrollkästchen, Container, Fußzeilen und mehr. Durch Bearbeiten der CSS-Datei, die mit der jeweiligen Komponente verknüpft ist, können Sie deren Stil an das Branding Ihres Unternehmens anpassen. Gehen Sie wie folgt vor, um den Stil einer Komponente anzupassen:

1. Öffnen Sie die Datei `<your-theme-sources>/src/components/<component>/<component.scss>` zur Bearbeitung. Um beispielsweise die Schriftfarbe der Schaltflächenkomponente zu ändern, öffnen Sie die `<your-theme-sources>/src/components/button/button.scss`, Datei .
1. Ändern Sie den Wert von beliebig gemäß Ihren Anforderungen. Um beispielsweise die Farbe der Schaltflächenkomponente beim Bewegen der Maus auf Grün zu ändern, ändern Sie den Wert der `color: $white` -Eigenschaft in `cmp-adaptiveform-button__widget:hover` -Klasse zu Hexadezimalcode 12b453 oder einer anderen grünen Schattierung. Der endgültige Code sieht wie folgt aus:

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

>
>
> Wenn ein Stil sowohl auf Design- als auch auf Komponentenebene definiert ist, hat der auf Komponentenebene definierte Stil Priorität.


#### 3. Bereiten Sie das Design für die Bereitstellung vor. {#generate-the-clientlib}

Um ein Design in einer AEM-Instanz bereitzustellen, muss es in eine Client-Bibliothek konvertiert werden. Führen Sie die folgenden Schritte aus, um das Design in eine Client-Bibliothek zu konvertieren:

1. Öffnen Sie die Eingabeaufforderung oder das Terminal-Fenster.
1. Navigieren Sie zum Ordner `<your-theme-sources>`. Beispiel: `C:\aem-forms-theme-canvas`
1. Führen Sie den folgenden Befehl aus:

   ```
      npm run create-clientlib --category=adaptiveform.theme.[yourtheme]
   ```

   Ersetzen `[yourtheme]` mit dem Namen Ihres benutzerdefinierten Designs. Wenn beispielsweise der Name des benutzerdefinierten Designs `customcanvastheme`, führen Sie den folgenden Befehl aus

   ```
       npm run create-clientlib --category=adaptiveform.theme.customcanvastheme
   ```

   Bei erfolgreicher Ausführung des Befehls wird ein Client-Bibliotheksordner unter `themerepo\theme-clientlibs\[yourtheme]`.

   ![Client-Bibliothekserstellung](/help/forms/using/assets/clientlib_created.png)


   ![Client-Bibliotheksspeicherort](/help/forms/using/assets/adaptiveform.theme.easel.png)

#### 4. Bereitstellen des Designs in einer lokalen Umgebung {#deploy-the-theme-on-a-local-environment}

Gehen Sie wie folgt vor, um das Design in Ihrer lokalen Entwicklungs- oder Testumgebung bereitzustellen:

1. Kopieren Sie die im vorherigen Abschnitt erstellte Client-Bibliothek in Ihr Archetypprojekt unter folgendem Pfad:

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

1. Tap **Adobe Experience Manager** > **Forms** > **Forms & Documents**.

1. Click **Create** > **Adaptive Forms**. The wizard for creating Adaptive Form opens.

1. Select the core component template in the **Source** tab.
1. Select the theme in the **Style** tab.
1. Click **Create**.

An Adaptive Form with the selected theme is created. 

**Apply theme to an existing Adaptive Form**

1. Log in to your AEM Forms author instance. 

1. Tap **Adobe Experience Manager** > **Forms** > **Forms & Documents**.

1. Select an Adaptive Form and click Properties. 

1. For the **Theme Client Library** option, select the theme. 

1. Click **Save & Close**.

The selected theme is applied to the Adaptive Form. 
-->

#### 5. Bereitstellen eines Designs in Ihrer Produktionsumgebung {#deploy-theme}

Nachdem Sie das Design in Ihrer lokalen Entwicklungsumgebung erfolgreich getestet haben, können Sie mit der Bereitstellung des Designs in Ihren Produktionsumgebungen fortfahren, einschließlich der Autoren- und der Veröffentlichungsinstanz. Führen Sie die folgenden Schritte aus, um das Design in Ihren Produktionsumgebungen bereitzustellen:

1. Melden Sie sich bei Ihrer AEM an.
1. Öffnen Sie Package Manager. Die Standard-URL ist `https://localhost:4502/crx/packmgr/index.jsp`.
1. Klicken **Paket hochladen** und klicken Sie auf **Durchsuchen**.
1. Navigieren Sie zu und wählen Sie `[AEM Archetype Project Folder]\all\target[appid].all-[version].zip`. Klicken **Öffnen**.
1. Klicken Sie auf Installieren. Wiederholen Sie diesen Schritt für alle Produktionsumgebungen.


Nachdem das Paket installiert wurde, ist das Design zur Auswahl verfügbar.

![Themen-Clientbibliothek](/help/forms/using/assets/themeclientlibrary.png)

>
>
>Falls Sie Schwierigkeiten beim Zugriff auf das Anmeldedialogfeld auf einer Veröffentlichungsinstanz haben, um das Paket über Package Manager zu installieren, versuchen Sie, sich über die folgende URL anzumelden: `http://[Publish Server URL]:[PORT]/system/console`. Dies ermöglicht den Zugriff auf die Anmeldung bei der Veröffentlichungsinstanz, sodass Sie mit dem Installationsprozess fortfahren können.

## Anwenden eines Designs auf ein adaptives Formular {#using-theme-in-adaptive-form}

Schritte zum Anwenden eines Designs auf ein adaptives Formular:

1. Melden Sie sich bei Ihrer lokalen AEM-Autoreninstanz an.
1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein. Tippen Sie auf **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**. 
1. Klicken Sie auf **Erstellen** > **Adaptive Formulare**.
1. Wählen Sie eine Vorlage für adaptive Forms-Kernkomponenten aus und klicken Sie auf **Nächste**. Die **Eigenschaften hinzufügen** erscheint
1. Geben Sie die **Name** für Ihr adaptives Formular.


   >[!NOTE]
   >
   > * Standardmäßig wird die `adaptiveform.theme.canvas3` Design ausgewählt ist.
   > * Sie können ein anderes Design als das **Design-Client-Bibliothek** Dropdown-Menü.

1. Klicken Sie auf **Erstellen**.

Designs für adaptive Formulare werden als Teil einer Vorlage für adaptive Formulare verwendet, um beim Erstellen eines adaptiven Formulars Stile zu definieren.

## Löschen eines Designs {#delete-a-theme}

So entfernen Sie nicht verwendete oder unerwünschte Designs:

1. Melden Sie sich bei Ihrer -Autoreninstanz an.
1. Öffnen Sie `http://[Publish Server URL]:[PORT]/crx/de/index.jsp`
1. Navigieren Sie zu `apps/[AEM Archetype Project Folder]/clientlibs/[yourtheme]`.
1. Löschen Sie den Designordner und speichern Sie die Änderungen.


## Häufig gestellte Fragen {#faq}

**F:** Welche Anpassung hat bei der Anpassung in einem Designordner sowohl auf globaler Ebene als auch auf Komponentenebene Priorität?

**Ans:** Wenn ein Stil sowohl auf Design- als auch auf Komponentenebene definiert ist, hat der auf Komponentenebene definierte Stil Vorrang.

**F:** Welche Schritte sollten unternommen werden, wenn das benutzerdefinierte Design nicht im **[!UICONTROL Design-Client-Bibliothek]**?

**Ans:**  Wenn Ihr benutzerdefiniertes Design nicht im **[!UICONTROL Design-Client-Bibliothek]** Gehen Sie wie folgt vor:

1. Navigieren Sie zu dem Speicherort, an dem Sie Ihre benutzerdefinierte Design-Client-Bibliothek hinzugefügt haben. Der empfohlene Pfad lautet `/ui.apps/src/main/content/jcr_root/apps[AEM Archetype Project Folder]/clientlibs/<yourtheme>`.

1. Öffnen Sie die `.content.xml` und die folgenden Metadaten einschließen:

   ```
       formstheme:true
       allowproxy:true
   ```

1. Speichern Sie die Datei und stellen Sie das Design erneut bereit.

## Siehe auch

* [Erstellen eines auf Kernkomponenten basierenden adaptiven Formulars](create-an-adaptive-form-core-components.md)
* [Verwenden Sie den Regeleditor, um dem Formular dynamisches Verhalten hinzuzufügen](rule-editor.md)
* [Erstellen oder Anpassen von Designs für auf Kernkomponenten basierende adaptive Forms](create-or-customize-themes-for-adaptive-forms-core-components.md)
* [Erstellen einer Vorlage für auf Kernkomponenten basierende adaptive Forms](template-editor.md)
* [Erstellen oder Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment](create-or-add-an-adaptive-form-to-aem-sites-page.md)

