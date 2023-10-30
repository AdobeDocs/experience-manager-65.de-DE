---
title: Anpassen der Benutzeroberfläche „Korrespondenz erstellen“
description: Erfahren Sie, wie Sie eine Correspondence-Benutzeroberfläche (Benutzeroberfläche) wie das Logo in der AEM Forms-Umgebung anpassen können.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
exl-id: 9593ca2a-7f9e-4487-a1a5-ca44114bff17
source-git-commit: 0e5b89617d481c69882ec5d4658e76855aa9b691
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 37%

---

# Anpassen der Benutzeroberfläche „Korrespondenz erstellen“{#customize-create-correspondence-ui}

## Übersicht {#overview}

Mit Correspondence Management können Sie die zugehörige Lösungsvorlage umbenennen, um einen besseren Markenwert zu erzielen und die Branding-Standards Ihres Unternehmens einzuhalten. Das Rebranding der Benutzeroberfläche umfasst das Ändern des Organisationslogos, das oben links in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;angezeigt wird.

Sie können das Logo in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;mit dem Logo Ihres Unternehmens ändern.

![Das benutzerdefinierte Symbol in der Benutzeroberfläche „Korrespondenz erstellen“](assets/0_1_introscreenshot.png)

Das benutzerdefinierte Symbol in der Benutzeroberfläche „Korrespondenz erstellen“

### Ändern des Logos in der Benutzeroberfläche &quot;Korrespondenz erstellen&quot; {#changing-the-logo-in-the-create-correspondence-ui}

Gehen Sie wie folgt vor, um ein Logo-Bild Ihrer Wahl einzurichten:

1. Erstellen Sie die entsprechende [Ordnerstruktur in CRX](#creatingfolderstructure).
1. [Hochladen der neuen Logodatei](#uploadlogo) in dem Ordner, den Sie in CRX erstellt haben.

1. [Legen Sie das CSS](#createcss) auf CRX fest, um auf das neue Logo zu verweisen.
1. Löschen Sie den Browser-Verlauf und [aktualisieren Sie die Benutzeroberfläche „Korrespondenz erstellen“](#refreshccrui).

## Erstellen der erforderlichen Ordnerstruktur {#creatingfolderstructure}

Erstellen Sie die Ordnerstruktur wie unten beschrieben für das Hosten des benutzerdefinierten Logobilds und des Stylesheets. Die neue Ordnerstruktur mit dem Stammordner /apps ähnelt der Struktur des Ordners /libs .

Erstellen Sie für jede Anpassung eine parallele Ordnerstruktur, wie unten beschrieben, in der Verzweigung /apps .

Die `/apps` Verzweigung (Ordnerstruktur):

* Stellt sicher, dass Ihre Dateien sicher sind, wenn das System aktualisiert wird. Wenn ein Upgrade, ein Feature Pack oder ein Hotfix vorhanden ist, wird die `/libs` -Verzweigung aktualisiert wird und wenn Sie Ihre Änderungen in der `/libs` -Verzweigung, werden sie überschrieben.
* Hilft, das vorhandene System/die Verzweigung nicht zu stören, was Sie möglicherweise versehentlich entschärfen können, wenn Sie die Standardspeicherorte zum Speichern der benutzerdefinierten Dateien verwenden.
* Hilft Ihren Ressourcen bei der Suche nach Ressourcen eine höhere Priorität AEM. AEM ist so konfiguriert, dass die `/apps` zuerst verzweigen und dann `/libs` -Verzweigung, um eine Ressource zu finden. Dieser Mechanismus bedeutet, dass das System Ihre Überlagerung (und alle dort definierten Anpassungen) verwendet.

Führen Sie die folgenden Schritte aus, um die erforderliche Ordnerstruktur im `/apps` branch:

1. Wechseln Sie zu `https://'[server]:[port]'/[ContextPath]/crx/de` und melden Sie sich als „Administrator“ an.
1. Erstellen Sie im Ordner &quot;apps&quot;einen Ordner mit dem Namen `css` mit Pfad/Struktur, die dem Ordner css ähnelt (im Ordner ccrui ).

   Schritte zum Erstellen des css-Ordners:

   1. Klicken Sie mit der rechten Maustaste im folgenden Pfad auf den Ordner **css** und wählen Sie **Überlagerungsknoten**: `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css`

      ![Überlagerungsknoten](assets/1_overlaynode_css.png)

   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **Pfad:** `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css`

      **Pfad für Überlagerung:** `/apps/`

      **Knotentypen abgleichen:** Überprüft

      ![Überlagerungsknotenpfad](assets/0_1_5ioverlaynodedialog.png)

      >[!NOTE]
      >
      >Ändern Sie nicht die `/libs` -Verzweigung. Alle Änderungen, die Sie vornehmen, können verloren gehen, da sich diese Verzweigung ändern kann, wenn Sie:
      >
      >    
      >    
      >    * Aktualisierung Ihrer Instanz
      >    * Hotfix anwenden
      >    * Feature Pack installieren
      >    
      >

   1. Klicken Sie auf **OK**. Der Ordner css wird im angegebenen Pfad erstellt.

1. Erstellen Sie im Ordner &quot;apps&quot;einen Ordner mit dem Namen `imgs` mit einem ähnlichen Pfad/einer ähnlichen Struktur zum imgs-Ordner (im ccrui-Ordner).

   1. Klicken Sie mit der rechten Maustaste auf den Ordner **imgs** im folgenden Pfad und wählen Sie **Überlagerungsknoten**: `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs`
   1. Stellen Sie sicher, dass das Dialogfeld „Überlagerungsknoten“ die folgenden Werte enthält:

      **Pfad:** /libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs

      **Überlagerungsspeicherort:** /apps/

      **Knotentypen abgleichen**: Kontrollkästchen aktiviert

   1. Klicken Sie auf **OK**.

      >[!NOTE]
      >
      >Sie können die Ordnerstruktur auch manuell im Ordner /apps erstellen.

1. Klicken Sie auf **Alle speichern**, um die Änderungen auf dem Server zu speichern.

## Hochladen des neuen Logos in CRX {#uploadlogo}

Laden Sie Ihre benutzerdefinierte Logodatei in CRX hoch. Standard-HTML-Regeln steuern die Darstellung des Logos. Die unterstützten Bilddateiformate hängen vom Browser ab, den Sie für den Zugriff auf AEM Forms verwenden. Alle Browser unterstützen JPEG, GIF und PNG. Weitere Informationen finden Sie in der Browser-spezifischen Dokumentation zu den unterstützten Bildformaten.

* Die Standardabmessungen des Logobilds sind 48 Pixel &#42; 48 Pixel. Stellen Sie sicher, dass Ihr Bild dieser Größe entspricht oder größer als 48 Pixel &#42; 48 Pixel ist.
* Wenn die Höhe Ihres Logobilds größer als 50 Pixel ist, skaliert die Benutzeroberfläche &quot;Korrespondenz erstellen&quot;das Bild auf eine maximale Höhe von 50 Pixel, da dies die Höhe der Kopfzeile ist. Beim Verkleinern des Bildes behält die Benutzeroberfläche &quot;Korrespondenz erstellen&quot;das Seitenverhältnis des Bildes bei.
* Die Benutzeroberfläche „Korrespondenz erstellen“ vergrößert Ihr Bild nicht, wenn es zu klein ist, daher sollten Sie ein Logobild mit einer Mindesthöhe von 48 Pixel und einer ausreichenden Breite verwenden.

Führen Sie die folgenden Schritte aus, um die benutzerdefinierte Logodatei auf CRX hochzuladen:

1. Wechseln Sie zu `https://'[server]:[port]'/[contextpath]/crx/de`. Falls erforderlich, melden Sie sich als Administrator an.
1. Klicken Sie in CRXDE mit der rechten Maustaste auf den Ordner **imgs** im folgenden Pfad und wählen Sie **Erstellen > Datei erstellen**:

   `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs/`

   ![Erstellen eines neuen Knotens im imgs-Ordner](assets/2_contentexplorernewnode.png)

1. Im Dialogfeld „Datei erstellen“ geben Sie als Namen der Datei „CustomLogo.png“ (oder den Namen Ihrer Logodatei) an.

   ![CustomLogo.png als neuer Knoten](assets/3_contentexplorernewnode_customlogo.png)

1. Klicken Sie auf **Alle speichern**.

   Unter der neuen Datei, die Sie erstellt haben (hier CustomLogo.png), wird die Eigenschaft jcr:content angezeigt.

1. Klicken Sie in der Ordnerstruktur auf jcr:content .

   Die Eigenschaften von „jcr:content“ werden angezeigt.

   ![jcrcontentproperties](assets/jcrcontentproperties.png)

1. Doppelklicken Sie auf die Eigenschaft **jcr:data**.

   Das Dialogfeld „jcr:data bearbeiten“ wird angezeigt.

   Klicken Sie nun auf den Ordner newlogo.png , doppelklicken Sie auf jcr:content (dim-Option) und legen Sie den Typ nt:resource fest. Wenn sie nicht vorhanden ist, erstellen Sie eine Eigenschaft mit dem Namen jcr:content.

1. Klicken Sie im Dialogfeld „jcr:data bearbeiten“, auf **Durchsuchen** und wählen Sie die Bilddatei, die Sie als Logo verwenden möchten (hier CustomLogo.png).

   Die unterstützten Bilddateiformate hängen vom Browser ab, den Sie für den Zugriff auf AEM Forms verwenden. Alle Browser unterstützen JPEG, GIF und PNG. Weitere Informationen finden Sie in der Browser-spezifischen Dokumentation zu den unterstützten Bildformaten.

   ![Beispiele für benutzerdefinierte Logodatei](assets/geometrixx-outdoors.png)

   Beispiel: CustomLogo.png als benutzerdefiniertes Logo

1. Klicken Sie auf **Alle speichern**.

## Erstellen Sie die CSS für das Rendern des Logos mit der Benutzeroberfläche {#createcss}

Das benutzerdefinierte Logo-Bild erfordert das Laden eines zusätzlichen Stylesheets im Inhaltskontext.

Führen Sie die folgenden Schritte aus, um das Stylesheet zum Rendern des Logos in der Benutzeroberfläche zu erstellen:

1. Rufen Sie `https://'[server]:[port]'/[contextpath]/crx/de` auf. Falls erforderlich, melden Sie sich als Administrator an.
1. Erstellen Sie eine Datei mit dem Namen customcss.css (Sie können keinen anderen Dateinamen verwenden) am folgenden Speicherort:

   `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css/`

   Schritte zum Erstellen der Datei customcss.css :

   1. Rechtsklicken Sie auf die **css** Ordner und auswählen **Erstellen > Datei erstellen**.
   1. Geben Sie im Dialogfeld „Neue Datei“ als Namen des CSS `customcss.css` an (Sie können keinen anderen Dateinamen verwenden) und klicken Sie auf **OK**.
   1. Fügen Sie der neu erstellten CSS-Datei den folgenden Code hinzu. Geben Sie in content:url im Code den Bildnamen an, den Sie in den imgs-Ordner in CRXDE hochgeladen haben.

      ```css
      .logo, .logo:after {
      content:url("../imgs/CustomLogo.png");
      }
      ```

   1. Klicken Sie auf **Alle speichern**.

## Aktualisieren Sie die Benutzeroberfläche &quot;Korrespondenz erstellen&quot;, damit Sie das benutzerdefinierte Logo sehen können. {#refreshccrui}

Löschen Sie den Browsercache und öffnen Sie dann die Instanz der Benutzeroberfläche &quot;Korrespondenz erstellen&quot;in Ihrem Browser, damit Sie Ihr benutzerdefiniertes Logo sehen können.

![Benutzeroberfläche „Korrespondenz erstellen“ mit benutzerdefiniertem Logo](assets/0_1_introscreenshot-1.png)

Das benutzerdefinierte Symbol in der Benutzeroberfläche „Korrespondenz erstellen“
