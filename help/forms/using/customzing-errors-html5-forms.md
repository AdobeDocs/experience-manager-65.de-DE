---
title: Anpassen von Fehlermeldungen für HTML5-Formulare
seo-title: Anpassen von Fehlermeldungen für HTML5-Formulare
description: Erfahren Sie, wie Sie die Anzeige von Fehlermeldungen für HTML5-Formulare anpassen, einschließlich wie Sie deren Position und Aussehen ändern.
seo-description: Erfahren Sie, wie Sie die Anzeige von Fehlermeldungen für HTML5-Formulare anpassen, einschließlich wie Sie deren Position und Aussehen ändern.
uuid: 6f48b64e-858f-4323-ad50-88e25f3c2e3d
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: 44e49789-9075-41b3-bce8-03e8efce2d5a
feature: Mobile Forms
exl-id: c4ae53a3-8de1-4985-a73e-829749de9814
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 84%

---

# Anpassen von Fehlermeldungen für HTML5-Formulare {#customizing-error-messages-for-html-forms}

In den HTML5-Formularen haben die Fehlermeldungen und Warnungen standardmäßig eine feste Position und ein festgelegtes Erscheinungsbild (Schriftart und Farbe). Der Fehler wird nur für ein ausgewähltes Feld angezeigt und es wird nur ein Fehler angezeigt.

Der Artikel stellt die Schritte bereit, um HTML5-Fehlermeldung anzupassen um,

* dass das Erscheinungsbild und die Position der Fehlermeldungen geändert werden. Die Fehlermeldung können oberhalb, unterhalb oder an der rechten Seite eines Felds angezeigt werden.
* Anzeigen von Fehlermeldungen für mehrere Felder jederzeit.
* den Fehler unabhängig davon anzeigen, ob ein Feld ausgewählt ist oder nicht.

## Anpassen von Fehlermeldungen{#customizing-error-messages-nbsp}

Laden Sie vor dem Anpassen der Fehlermeldungen das angehängte Paket herunter und extrahieren Sie es (CustomErrorManager-1.0-SNAPSHOT.zip).

Nachdem Sie das Paket entpackt haben, öffnen Sie den Ordner CustomErrorManager-1.0-SNAPSHOT. Er enthält die Ordner jcr_root und META-INF. Diese Ordner enthalten die CSS- und .JS-Dateien, die zum Anpassen der Fehlermeldung erforderlich sind.

[Datei laden](assets/customerrormanager-1.0-snapshot.zip)

### Anpassen der Position der Fehlermeldungen{#customizing-the-position-of-error-messages-nbsp}

Fügen Sie zum Anpassen der Fehlermeldungsposition für jedes Fehler- und Warnfeld den Tag &lt;div> hinzu. Positionieren Sie den Tag &lt;div> auf der linken oder rechten Seite und wenden Sie auf den Tag &lt;div> CSS-Stile an. Ausführliche Anweisungen finden Sie in unten aufgeführtem Verfahren:

1. Navigieren Sie zum Ordner `CustomErrorManager-1.0-SNAPSHOT`und öffnen Sie den Ordner `etc\clientlibs\mf-custom-error-manager\CustomErrorManager\javascript` .
1. Öffnen Sie die Datei `customErrorManager.js` zur Bearbeitung. Die Funktion `markError` in der Datei akzeptiert die folgenden Parameter:

   |  |  |
   |---|---|
   | jqWidget | jqWidget ist der Griff für das Widget. |
   | msg | enthält die Fehlermeldung |
   | type | gibt an, ob es sich um einen Fehler oder eine Warnung handelt |

1. Bei der standardmäßigen Implementierung werden Fehlermeldungen auf der rechten Seite des Felds angezeigt. Verwenden Sie folgenden Code, um Fehlermeldungen oben anzuzeigen.

   ```javascript
   markError: function (jqWidget, msg, type) {
               var element = jqWidget.element,                                //Gives the div containing widget
                   pos = $(element).offset(),                          //Calculates the position of the div in the view port
                                                                   msgHeight = xfalib.view.util.TextMetrics.measureExtent(msg).height + 5;  //Calculating the height of the Error Message
                   styles = {};
                   styles.left = pos.left + "px";         // Assign the desired left position using pos.left. Here it is calculated for exact left of the field
                   styles.top = pos.top - msgHeight + "px";  // Assign the desired top position using pos.top. Here it is calculated for top of the field
               if (type != "warning") {
                   if(!jqWidget.errorDiv){
                                                                                   //Adding the warning div if it is not present already
                       jqWidget.errorDiv=$("<div id='customError'></div>").appendTo('body');
                   }
                   jqWidget.$css(jqWidget.errorDiv.get(0), styles); // Applying the styles to the warning div
                   jqWidget.errorDiv.text(msg).show();                     //Showing the warning message
               } else {
                   if(!jqWidget.errorDiv){
                                                                                   //Adding the error div if it is not present already
                       jqWidget.errorDiv=$("<div id='customWarning'></div>").appendTo('body');
                   }
                   jqWidget.$css(jqWidget.errorDiv.get(0), styles); // Applying the styles to the error div
                   jqWidget.errorDiv.text(msg).show();                     //Showing the warning message
               }
   
           },
   ```

1. Speichern und schließen Sie die Datei.
1. Navigieren Sie zum Ordner `CustomErrorManager-1.0-SNAPSHOT` und erstellen Sie ein Archiv der Ordner jcr_root und META-INF. Benennen Sie das Archiv in CustomErrorManager-1.0-SNAPSHOT.zip um.
1. Verwenden Sie den Package Manager, um das Paket herunterzuladen und zu installieren.

## Anzeigen von Fehlermeldungen für mehrere Felder{#display-error-messages-for-multiple-fields-nbsp}

Verwenden Sie das angehängte Paket, um die Fehlermeldungen für alle Felder gleichzeitig anzuzeigen. Verwenden Sie zum Anzeigen einer einzelnen Fehlermeldung das Standardprofil.

### Anpassen des Erscheinungsbilds der Fehlermeldungen.{#customizing-the-appearance-of-error-messages-nbsp}

1. Navigieren Sie zum Ordner etc\clientlibs\mf-custom-error-manager\CustomErrorManager\css.

1. Öffnen Sie die Datei sample.css zur Bearbeitung. Die CSS-Datei enthält 2 IDs: #customError und #customWarning. Sie können diese IDs verwenden, um andere Eigenschaften zu ändern, z. B. Farbe, Schriftgrad usw.

    Verwenden Sie den folgenden Code, um Schriftgröße und Farbe der Fehler-/Warnmeldungen zu ändern.

   ```css
   #customError {
   color: #0000FF; // it changes the color of Error Message
   display:none;
   position:absolute;
   opacity:0.85;
   font-size: 24px;  // it changes the font size of Error Message
   z-index:5;
   }
   
   #customWarning {
   color: #00FF00;  // it changes the color of Warning Message
   display:none;
   position:absolute;
   opacity:0.85;
   font-size: 18px;   // it changes the font size of Warning Message
   z-index:5;
   }
   
   Save the changes.
   ```

1. Speichern und schließen Sie die Datei.
1. Navigieren Sie zum Ordner CustomErrorManager-1.0-SNAPSHOT und erstellen Sie ein Archiv der Ordner jcr_root und META-INF. Benennen Sie das Archiv in CustomErrorManager-1.0-SNAPSHOT.zip um.
1. Verwenden Sie den Package Manager, um das Paket herunterzuladen und zu installieren.

## Geben Sie das Formular mit dem neuen Profil wieder.  {#render-the-form-with-the-new-profile-nbsp}

Standardmäßig verwenden HTML5-Formulare ein Standardprofil: https://&lt;server>/content/xfaforms/profiles/default.html?contentRoot=&lt;xdp location>&amp;template=&lt;name of the xdp>

Um ein Formular mit den benutzerdefinierten Fehlermeldungen anzuzeigen, rendern Sie das Formular mit dem Fehlerprofil: https://&lt;server>/content/xfaforms/profiles/error.html?contentRoot=&lt;xdp location>&amp;template=&lt;name of the xdp>

>[!NOTE]
>
>Mit dem angehängten Paket wird das Fehlerprofil installiert.
