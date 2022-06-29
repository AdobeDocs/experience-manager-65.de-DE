---
title: Anpassen der Benutzeroberfläche „Korrespondenz erstellen“
seo-title: Customize create correspondence UI
description: Erfahren Sie, wie Sie Benutzeroberfläche „Korrespondenz erstellen“ anpassen.
seo-description: Learn how to customize create correspondence UI.
uuid: 9dee9b6f-4129-4560-9bf8-db48110b76f7
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: 13a93111-c08c-4457-b69a-a6f6eb6da330
docset: aem65
feature: Correspondence Management
exl-id: 9593ca2a-7f9e-4487-a1a5-ca44114bff17
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1088'
ht-degree: 100%

---

# Anpassen der Benutzeroberfläche „Korrespondenz erstellen“{#customize-create-correspondence-ui}

## Übersicht {#overview}

Mit der Correspondence Management können Sie die dazugehörige Lösungsvorlage so umbenennen, dass Sie einen besseren Markenwert erzielen und die Markenstandards Ihres Unternehmens erfüllt werden. Die Umbenennung der Benutzeroberfläche umfasst das Ändern des Unternehmenslogo in der linken oberen Ecke der Benutzeroberfläche „Korrespondenz erstellen“.

Sie können das Logo in der Benutzeroberfläche „Korrespondenz erstellen“ mit Ihrem Firmenlogo ersetzen.

![Das benutzerdefinierte Symbol in der Benutzeroberfläche „Korrespondenz erstellen“](assets/0_1_introscreenshot.png)

Das benutzerdefinierte Symbol in der Benutzeroberfläche „Korrespondenz erstellen“

### Ändern des Logos in der Benutzeroberfläche „Korrespondenz erstellen“ {#changing-the-logo-in-the-create-correspondence-ui}

Um ein Logobild Ihrer Wahl einzurichten, führen Sie die folgenden Schritte durch:

1. Erstellen Sie die entsprechende [Ordnerstruktur in CRX](#creatingfolderstructure).
1. [Laden Sie die neue Logodatei](#uploadlogo) in den Ordner hoch, den Sie in CRX erstellt haben.

1. [Legen Sie das CSS](#createcss) auf CRX fest, um auf das neue Logo zu verweisen.
1. Löschen Sie den Browser-Verlauf und [aktualisieren Sie die Benutzeroberfläche „Korrespondenz erstellen“](#refreshccrui).

## Erstellen der gewünschten Ordnerstruktur {#creatingfolderstructure}

Erstellen Sie die Ordnerstruktur wie nachfolgend beschrieben für das Hosten des benutzerdefinierten Logobilds und des Stylesheets. Die neue Ordnerstruktur mit dem /apps-Stammordner ist ähnlich der Struktur des /libs-Ordners.

Erstellen Sie bei jeder Anpassung eine parallele Ordnerstruktur in der /apps-Verzweigung, wie nachfolgend beschrieben.

Die /apps-Verzweigung (Ordnerstruktur):

* Stellt sicher, dass Ihre Dateien im Falle eines System-Updates sicher sind. Bei einem Upgrade, Feature Pack oder Hotfix wird die /libs-Verzweigung aktualisiert. Wenn Sie Änderungen in der /libs-Verzweigung hosten, werden sie überschrieben.
* Hilft Ihnen dabei, das vorhandene System/die Verzweigung nicht zu beeinträchtigen, was unter Umständen geschehen ist, falls Sie die Standardspeicherorte zum Speichern der benutzerdefinierten Dateien verwendet haben.
* Hilft den Ressourcen, höhere Priorität zu erhalten, wenn AEM nach Ressourcen sucht. AEM ist so konfiguriert, dass bei der Suche nach einer Ressource zuerst die /apps-Verzweigung und dann die /libs-Verzweigung durchsucht wird. Dieser Mechanismus bedeutet, dass das System Ihre Überlagerung (und alle dort definierten Anpassungen) verwendet.

Führen Sie die folgenden Schritte aus, um die gewünschte Ordnerstruktur in der /apps-Verzweigung zu erstellen:

1. Wechseln Sie zu `https://'[server]:[port]'/[ContextPath]/crx/de` und melden Sie sich als „Administrator“ an.
1. Erstellen Sie im Programmordner einen Ordner mit dem Namen `css` mit einem ähnlichen Pfad/einer ähnlichen Struktur wie der css-Ordner (im ccrui-Ordner).

   Schritte zum Erstellen des css-Ordners:

   1. Klicken Sie mit der rechten Maustaste im folgenden Pfad auf den Ordner **css** und wählen Sie **Überlagerungsknoten**: `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css`

      ![Überlagerungsknoten](assets/1_overlaynode_css.png)

   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **Pfad:** /libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css

      **Überlagerungsspeicherort:** /apps/

      **Knotentypen abgleichen:** Überprüft

      ![Überlagerungsknotenpfad](assets/0_1_5ioverlaynodedialog.png)

      >[!NOTE]
      >
      >Ändern Sie die /libs-Verzweigung nicht. Alle Änderungen, die Sie vornehmen, gehen möglicherweise verloren, da diese Verzweigung sich ändern kann, wenn Sie:
      >
      >    
      >    
      >    * Ihre Instanz aktualisieren
      >    * Ein Hotfix anwenden
      >    * Ein Feature Pack installieren


   1. Klicken Sie auf **OK**. Der css-Ordner wird in dem angegebenen Pfad erstellt.

1. Erstellen Sie im Programmordner einen Ordner mit dem Namen `imgs` mit einem ähnlichen Pfad/einer ähnlichen Struktur wie der imgs-Ordner (im ccrui-Ordner).

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **imgs** im folgenden Pfad und wählen Sie **Überlagerungsknoten**: `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs`
   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **Pfad:** /libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs

      **Überlagerungsspeicherort:** /apps/

      **Knotentypen abgleichen:** Überprüft

   1. Klicken Sie auf **OK**.

      >[!NOTE]
      >
      >Sie können die Ordnerstruktur im /apps-Ordner auch manuell erstellen.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

## Hochladen des neuen Logos auf CRX {#uploadlogo}

Laden Sie Ihre benutzerdefinierte Logodatei auf CRX hoch. Standard-HTML-Regeln steuern die Darstellung des Logos. Die unterstützten Bildformate werden vom Browser bestimmt, den Sie verwenden, um auf AEM Forms zuzugreifen. Alle Browser unterstützen JPEG, GIF und PNG. Weitere Informationen finden Sie in der Browser-spezifischen Dokumentation zu den unterstützten Bildformaten.

* Die Standardabmessungen des Logobilds sind 48 Pixel x 48 Pixel. Stellen Sie sicher, dass Ihr Bild ungefähr diese Größe hat oder größer ist als 48 Pixel x 48 Pixel.
* Wenn die Höhe des Logobilds größer ist als 50 Pixel, verkleinert die Benutzeroberfläche „Korrespondenz erstellen“ das Bild auf eine maximale Höhe 50 Pixel, da dies die Höhe der Kopfleiste ist. Beim Verkleinern des Bilds behält die Benutzeroberfläche „Korrespondenz erstellen“ das Seitenverhältnis bei.
* Die Benutzeroberfläche „Korrespondenz erstellen“ vergrößert Ihr Bild nicht, wenn es zu klein ist, daher sollten Sie ein Logobild mit einer Mindesthöhe von 48 Pixel und einer ausreichenden Breite verwenden.

Führen Sie die folgenden Schritte aus, um die benutzerdefinierte Logodatei auf CRX hochzuladen:

1. Wechseln Sie zu `https://'[server]:[port]'/[contextpath]/crx/de`. Falls erforderlich, melden Sie sich als Administrator an.
1. Klicken Sie in CRXDE mit der rechten Maustaste auf den Ordner **imgs** im folgenden Pfad und wählen Sie **Erstellen > Datei erstellen**:

   `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs/`

   ![Erstellen eines neuen Knotens im imgs-Ordner](assets/2_contentexplorernewnode.png)

1. Im Dialogfeld „Datei erstellen“ geben Sie als Namen der Datei „CustomLogo.png“ (oder den Namen Ihrer Logodatei) an.

   ![CustomLogo.png als neuer Knoten](assets/3_contentexplorernewnode_customlogo.png)

1. Klicken Sie auf **Alle speichern**.

   Unter der neuen Datei, die Sie erstellt haben (hier „CustomLogo.png“) erscheint die Eigenschaft „jcr:content“.

1. Klicken Sie auf „jcr:content“ in der Ordnerstruktur.

   Die Eigenschaften von „jcr:content“ werden angezeigt.

   ![jcrcontentproperties](assets/jcrcontentproperties.png)

1. Doppelklicken Sie auf die Eigenschaft **jcr:data**.

   Das Dialogfeld „jcr:data bearbeiten“ wird angezeigt.

   Klicken Sie jetzt an auf den Ordner „newlogo.png“, doppelklicken Sie auf „jcr:content“ (dim-Option) und legen Sie den Typ „nt:resource“ fest. Sofern nicht vorhanden, erstellen Sie zuerst eine Eigenschaft mit dem Namen „jcr:content“.

1. Klicken Sie im Dialogfeld „jcr:data bearbeiten“, auf **Durchsuchen** und wählen Sie die Bilddatei, die Sie als Logo verwenden möchten (hier CustomLogo.png).

   Die unterstützten Bildformate werden vom Browser bestimmt, den Sie verwenden, um auf AEM Forms zuzugreifen. Alle Browser unterstützen JPEG, GIF und PNG. Weitere Informationen finden Sie in der Browser-spezifischen Dokumentation zu den unterstützten Bildformaten.

   ![Beispiele für benutzerdefinierte Logodatei](assets/geometrixx-outdoors.png)

   Beispiel: CustomLogo.png soll als benutzerdefiniertes Logo verwendet

1. Klicken Sie auf **Alle speichern**.

## Erstellen des CSS, um das Logo in der Benutzeroberfläche zu integrieren {#createcss}

Das benutzerdefinierte Logobild ist ein zusätzliches im Inhaltskontext zu ladendes Stylesheet.

Führen Sie die folgenden Schritte aus, um das Stylesheet für die Wiedergabe des Logos einzurichten:

1. Wechseln Sie zu `https://'[server]:[port]'/[contextpath]/crx/de`. Falls erforderlich, melden Sie sich als Administrator an.
1. Erstellen Sie eine Datei mit dem Namen customcss.css (Sie können keinen anderen Dateinamen verwenden) am folgenden Speicherort:

   `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css/`

   Schritte zum Erstellen der customcss.css-Datei:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **css** und wählen Sie **Erstellen > Ordner erstellen**.
   1. Geben Sie im Dialogfeld „Neue Datei“ als Namen des CSS `customcss.css` an (Sie können keinen anderen Dateinamen verwenden) und klicken Sie auf **OK**.
   1. Fügen Sie den folgenden Code zu der neu erstellte CSS-Datei hinzu. Geben Sie unter „content:url“ im Code den Namen des Bildes ein, das Sie in den imgs-Ordner in CRXDE hochgeladen haben.

      ```css
      .logo, .logo:after {
      content:url("../imgs/CustomLogo.png");
      }
      ```

   1. Klicken Sie auf **Alle speichern**.

## Aktualisieren der Benutzeroberfläche „Korrespondenz erstellen“, um das benutzerdefinierte Logo zu sehen {#refreshccrui}

Löschen Sie den Browsercache und öffnen Sie dann die Instanz der Benutzeroberfläche „Korrespondenz erstellen“ in Ihrem Browser. Sie sollten nun Ihr eigenes Logo sehen können.

![Benutzeroberfläche „Korrespondenz erstellen“ mit benutzerdefiniertem Logo](assets/0_1_introscreenshot-1.png)

Das benutzerdefinierte Symbol in der Benutzeroberfläche „Korrespondenz erstellen“
