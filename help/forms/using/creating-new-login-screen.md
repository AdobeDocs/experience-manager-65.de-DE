---
title: Erstellen eines neuen Anmeldungsbildschirms
seo-title: Erstellen eines neuen Anmeldungsbildschirms
description: Gehen Sie wie folgt vor, um die Anmeldeseite von LiveCycle-Modulen zu ändern, beispielsweise AEM Forms oder Forms Manager.
seo-description: Gehen Sie wie folgt vor, um die Anmeldeseite von LiveCycle-Modulen zu ändern, beispielsweise AEM Forms oder Forms Manager.
uuid: 2d4a72f4-cc9a-412d-856d-0fca75f1272b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 35497785-263d-44b1-9ee4-85921997295b
docset: aem65
translation-type: tm+mt
source-git-commit: 81249e13db9bd173d4251683ccaacbb7f71b3209
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 60%

---


# Erstellen eines neuen Anmeldungsbildschirms{#creating-a-new-login-screen}

Sie können den Anmeldungsbildschirm aller Module von AEM Forms ändern, die den AEM Forms-Anmeldungsbildschirm verwenden. Die Änderungen wirken sich beispielsweise auf den Anmeldungsbildschirm, den Formularmanager und AEM Forms aus.

## Voraussetzung {#prerequisite}

1. Log in at `/lc/crx/de` with Administrator permissions.
1. Führen Sie die folgenden Aktionen durch:

   1. Replizieren Sie die hierarchische Struktur: von `/libs/livecycle/core/content` at `/apps/livecycle/core/content`.

      Behalten Sie die Eigenschaften (Knoten/Ordner) und Zugriffssteuerung bei.

   1. Kopieren Sie den Inhaltsordner:

      von: `/libs/livecycle/core`

      in: `/apps/livecycle/core`.

   1. Delete the contents of `/apps/livecycle/core` folder.

1. Führen Sie die folgenden Aktionen durch:

   1. Replizieren Sie die hierarchische Struktur: von `/libs/livecycle/core/components/login` at `/apps/livecycle/core/components/login`. Behalten Sie die Eigenschaften (Knoten/Ordner) und Zugriffssteuerung bei.

   1. Copy the components folder: from `/libs/livecycle/core` to `/apps/livecycle/core`.

   1. Delete the contents of the folder: `/apps/livecycle/core/components/login`.

### Hinzufügen eines neuen Gebietsschemas {#adding-a-new-locale}

1. Kopieren Sie den `i18n` Ordner:

   * von `/libs/livecycle/core/components/login`
   * in `/apps/livecycle/core/components/login`

1. Delete all the folders inside `i18n` except one, say `en`.

1. Mit dem Ordner `en` führen Sie diese Schritte durch:

   1. Benennen Sie den Ordner nach dem Gebietsschema, das unterstützt werden soll. Beispiel: `ar`.

   1. Change the property `jcr:language` value to `ar`(for the `ar` folder).
   >[!NOTE]
   >
   >Wenn das Gebietsschema eine Sprach- und Ländercodekombination ist, beispielsweise `ar-DZ`, ändern Sie den Ordnernamen und den Eigenschaftswert zu `ar-DZ`.

1. Kopieren `login.jsp`:

   * von `/libs/livecycle/core/components/login`
   * in `/apps/livecycle/core/components/login`

1. Modify the following snippet of code for `/apps/livecycle/core/components/login/login.jsp`:

***Gebietsschema ist Sprachcode***

```
String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }

   To

   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("ar")) {
               browserLocale = "ar";
               break;
           }
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
```


***Gebietsschema ist Sprach- und Ländercode***

```
String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }

   To

   String browserLocale = "en";
       for(int i=0; i<locales.length; i++)
       {
           String prioperty = locales[i];
           if(prioperty.trim().equalsIgnoreCase("ar-DZ")) {
               browserLocale = "ar-DZ";
               break;
           }
           if(prioperty.trim().startsWith("en")) {
               browserLocale = "en";
               break;
           }
           if(prioperty.trim().startsWith("de")){
               browserLocale = "de";
               break;
           }
           if(prioperty.trim().startsWith("ja")){
               browserLocale = "ja";
               break;
           }
           if(prioperty.trim().startsWith("fr")){
               browserLocale = "fr";
               break;
           }
       }
```

***Standardgebietsschema ändern***

```
String browserLocale = "en";
   for(int i=0; i<locales.length; i++)

   To

   String browserLocale = "ar";
   for(int i=0; i<locales.length; i++)
```

### Hinzufügen von neuem Text oder Ändern des vorhandenen Texts {#adding-new-text-or-modifying-existing-text}

1. Ordner `i18n` kopieren:

   * von `/libs/livecycle/core/components/login`
   * in `/apps/livecycle/core/components/login`

1. Ändern Sie nun den Wert der Eigenschaft `sling:message` des Knotens (unter dem Codeordner des gewünschten Gebietsschemas) für den Sie den Text ändern möchten. Die Übersetzung wird mit dem Schlüssel durchgeführt, der im Wert der Eigenschaft `sling:key` des Knotens aufgeführt ist.

1. Zum Hinzufügen des neuen Schlüssel-Wert-Paars führen Sie die folgenden Schritte aus. Überprüfen Sie ein Beispiel auf dem darauffolgenden Screenshot.

   1. Erstellen Sie unter den Gebietsschemaordnern einen Knoten vom Typ `sling:MessageEntry` oder kopieren Sie einen vorhandenen Knoten und benennen Sie ihn um.
   1. Kopieren `login.jsp` :

      * von `/libs/livecycle/core/components/login`

      * in `/apps/livecycle/core/components/login`
   1. Modify `/apps/livecycle/core/components/login/login.jsp` to incorporate the newly added text.

   ![Hinzufügen neues Schlüsselwertpaar](assets/capture_new.png)


```
<div class="loginContent">
                       <span class="loginFlow"></code>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></code>
                       <span class="loginTitle"><%= i18n.get("Login") %></code>
                       <% if (loginFailed) {%>

   To

   <div class="loginContent">
                       <span class="loginFlow"></code>
                       <span class="loginVersion"><%= i18n.get("My Welcome Message") %></code>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></code>
                       <span class="loginTitle"><%= i18n.get("Login") %></code>
                       <% if (loginFailed) {%>
```

### Hinzufügen eines neuen Stils oder Ändern des vorhandenen Stils {#adding-new-style-or-modifying-existing-style}

1. Copy `login` node:

   * von `/libs/livecycle/core/content`
   * in `/apps/livecycle/core/content`

1. Löschen von Dateien `login.js` und `jquery-1.8.0.min.js`von der Node `/apps/livecycle/core/content/login.`
1. Ändern Sie die Stile in der CSS-Datei.
1. Neue Stile hinzufügen:

   1. Neue Stile Hinzufügen `/apps/livecycle/core/content/login/login.css`
   1. Kopieren `login.jsp`

      * von `/libs/livecycle/core/components/login`

      * in `/apps/livecycle/core/components/login`
   1. Modify `/apps/livecycle/core/components/login/login.jsp` to incorporate the newly added styles.



Beispiel:

* Add the following to `/apps/livecycle/core/content/login/login.css`.

```
css.newLoginContentArea {
    width: 700px;
    padding: 100px 0px 0px 100px;
   }
```

* Ändern Sie Folgendes in `/apps/livecycle/core/components/login.jsp`.

```
<div class="loginContentArea">

   To

   <div class="newLoginContentArea">
```

>[!NOTE]
>
>If the existing images in `/apps/livecycle/core/content/login` (copied from `/libs/livecycle/core/content/login`) are removed, then remove the corresponding references in CSS.


### Fügen Sie neue Bilder hinzu {#add-new-images}

1. Führen Sie die Schritte zum Hinzufügen eines neuen Stils oder zum Ändern des vorhandenen Stils aus (siehe oben).
1. Add new images in `/apps/livecycle/core/content/login`. Bild hinzufügen:

   1. Installieren Sie den WebDAV-Client.
   1. Navigate to `/apps/livecycle/core/content/login` folder, using webDAV client. For more information, see: [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).

   1. Fügen Sie neue Bilder hinzu.

1. Hinzufügen neue Stile in `/apps/livecycle/core/content/login/login.css,` Übereinstimmung mit neuen Bildern hinzugefügt in `/apps/livecycle/core/content/login`.
1. Use the new styles in `login.jsp` at `/apps/livecycle/core/components`.

Beispiel:

* Add the following to `/apps/livecycle/core/content/login/login.css`

```
css.newLoginContainerBkg {
    background-image: url(my_Bg.gif);
    background-repeat: no-repeat;
    background-position: left top;
    width: 727px;
   }
```

* Ändern Sie Folgendes in `/apps/livecycle/core/components/login.jsp`.

```
<div class="loginContainerBkg">

   To

   <div class="newLginContainerBkg">
```

