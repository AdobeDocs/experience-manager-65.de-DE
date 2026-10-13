---
title: Anpassen von Fehlermeldungen für HTML5-Formulare
description: Erfahren Sie, wie Sie die Anzeige von Fehlermeldungen für HTML5-Formulare anpassen, auch wie Sie deren Position und Erscheinungsbild ändern.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
feature: HTML5 Forms,Mobile Forms
exl-id: c4ae53a3-8de1-4985-a73e-829749de9814
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 97aafc4b-2598-52d6-9012-295a95969e38
    internal-label: HTML5 Forms
  - id: 59f95943-e802-56ac-990d-21ab923984c1
    internal-label: Mobile Forms
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 100%
---
# Anpassen von Fehlermeldungen für HTML5-Formulare {#customizing-error-messages-for-html-forms}

In den HTML5-Formularen haben Fehlermeldungen und Warnungen standardmäßig eine feste Position und ein festgelegtes Erscheinungsbild (Schrift und Farbe). Der jeweilige Fehler wird nur für ein ausgewähltes Feld ausgegeben und es wird nur ein Fehler angezeigt.

Dieser Artikel enthält die Schritte zum Anpassen von Fehlermeldungen für HTML5-Formulare, sodass Sie folgende Möglichkeiten haben:

* dass das Erscheinungsbild und die Position der Fehlermeldungen geändert werden. Die Fehlermeldung können oberhalb, unterhalb oder an der rechten Seite eines Felds angezeigt werden.
* Anzeigen von Fehlermeldungen für mehrere Felder jederzeit.
* Anzeigen des Fehlers unabhängig davon, ob ein Feld ausgewählt ist oder nicht.

## Anpassen von Fehlermeldungen  {#customizing-error-messages-nbsp}

Laden Sie vor dem Anpassen der Fehlermeldungen das angehängte Paket herunter und extrahieren Sie es (CustomErrorManager-1.0-SNAPSHOT.zip).

Öffnen Sie den Ordner „CustomErrorManager-1.0-SNAPSHOT“, nachdem Sie das Paket extrahiert haben. Er enthält die Ordner „jcr_root“ und „META-INF“. Diese Ordner enthalten die CSS- und JS-Dateien, die zum Anpassen der Fehlermeldung erforderlich sind.

[Datei laden](assets/customerrormanager-1.0-snapshot.zip)

### Anpassen der Position der Fehlermeldungen  {#customizing-the-position-of-error-messages-nbsp}

Fügen Sie zum Anpassen der Fehlermeldungsposition für jedes Fehler- und Warnfeld das Tag &lt;div> hinzu. Positionieren Sie das Tag &lt;div> auf der linken oder rechten Seite und wenden Sie CSS-Stile auf das Tag &lt;div> an. Ausführliche schrittweise Anweisungen finden Sie im unten aufgeführten Verfahren:

1. Navigieren Sie zum Ordner `CustomErrorManager-1.0-SNAPSHOT` und öffnen Sie den Ordner `etc\clientlibs\mf-custom-error-manager\CustomErrorManager\javascript`.
1. Öffnen Sie die Datei `customErrorManager.js` zum Bearbeiten. Die `markError`-Funktion in der Datei akzeptiert folgende Parameter:

   |   |  |
   |---|---|
   | jqWidget | jqWidget ist der Handle für ein Widget. |
   | msg | enthält die Fehlermeldung |
   | Typ | Gibt an, ob es sich um einen Fehler oder eine Warnung handelt. |

1. Bei der vorkonfigurierten Implementierung werden Fehlermeldungen auf der rechten Seite des Felds angezeigt. Verwenden Sie folgenden Code, um Fehlermeldungen oben anzuzeigen.

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
1. Verwenden Sie den Paket-Manager, um das Paket herunterzuladen und zu installieren.

## Anzeigen von Fehlermeldungen für mehrere Felder  {#display-error-messages-for-multiple-fields-nbsp}

Verwenden Sie das beigefügte Paket, um Fehlermeldungen für alle Felder gleichzeitig anzuzeigen. Verwenden Sie das Standardprofil, um eine einzelne Fehlermeldung anzuzeigen.

### Anpassen des Erscheinungsbilds von Fehlermeldungen  {#customizing-the-appearance-of-error-messages-nbsp}

1. Navigieren Sie zum Ordner etc\clientlibs\mf-custom-error-manager\CustomErrorManager\css.

1. Öffnen Sie die Datei „sample.css“ zum Bearbeiten. Die CSS-Datei enthält zwei IDs: „#customError“ und „#customWarning“. Sie können diese IDs verwenden, um andere Eigenschaften zu ändern, z. B. Farbe und Schriftgrad.

   Verwenden Sie den folgenden Code, um Schriftgrad und Farbe der Fehler-/Warnmeldungen zu ändern.

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
1. Navigieren Sie zum Ordner „CustomErrorManager-1.0-SNAPSHOT“ und erstellen Sie ein Archiv der Ordner „jcr_root“ und „META-INF“. Benennen Sie das Archiv in CustomErrorManager-1.0-SNAPSHOT.zip um.
1. Verwenden Sie den Paket-Manager, um das Paket herunterzuladen und zu installieren.

## Rendern Sie das Formular mit dem neuen Profil.  {#render-the-form-with-the-new-profile-nbsp}

Standardmäßig verwenden HTML5-Formulare ein Standardprofil: `https://&lt;server&gt;/content/xfaforms/profiles/default.html?contentRoot=&lt;xdp location&gt;&template=&lt;name of the xdp&gt;`

Um ein Formular mit den benutzerdefinierten Fehlermeldungen anzuzeigen, rendern Sie das Formular mit dem folgenden Fehlerprofil: `https://&lt;server&gt;/content/xfaforms/profiles/error.html?contentRoot=&lt;xdp location&gt;&template=&lt;name of the xdp&gt;`

>[!NOTE]
>
>Mit dem angehängten Paket wird das Fehlerprofil installiert.
