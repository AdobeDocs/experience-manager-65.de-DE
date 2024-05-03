---
title: Erstellen eines Anmeldebildschirms
description: Gehen Sie wie folgt vor, um die Anmeldeseite von LiveCycle-Modulen zu ändern, z. B. AEM Forms Workspace oder Forms Manager.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 5cb906b6-6a3c-498c-94f5-27a9071ea934
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 100%

---

# Erstellen eines Anmeldebildschirms{#creating-a-new-login-screen}

Sie können den Anmeldebildschirm aller AEM Forms-Module ändern, die den AEM Forms-Anmeldebildschirm verwenden. Beispielsweise wirken sich die Änderungen auf den Anmeldebildschirm von Forms Manager und AEM Forms Workspace aus.

## Voraussetzung {#prerequisite}

1. Melden Sie sich mit Administratorberechtigungen bei `/lc/crx/de` an.
1. Führen Sie die folgenden Aktionen durch:

   1. Replizieren Sie die hierarchische Struktur: von `/libs/livecycle/core/content` in `/apps/livecycle/core/content`.

      Behalten Sie die Eigenschaften (Knoten/Ordner) und Zugriffssteuerung bei.

   1. Kopieren Sie den Inhaltsordner:

      von: `/libs/livecycle/core`

      in: `/apps/livecycle/core`.

   1. Löschen Sie den Inhalt des Ordners `/apps/livecycle/core`.

1. Führen Sie die folgenden Aktionen durch:

   1. Replizieren Sie die hierarchische Struktur von `/libs/livecycle/core/components/login` in `/apps/livecycle/core/components/login`. Behalten Sie die Eigenschaften (Knoten/Ordner) und Zugriffssteuerung bei.

   1. Kopieren Sie den Komponentenordner von `/libs/livecycle/core` nach `/apps/livecycle/core`.

   1. Löschen Sie den Inhalt des Ordners `/apps/livecycle/core/components/login`.

### Hinzufügen eines neuen Gebietsschemas {#adding-a-new-locale}

1. Kopieren Sie den Ordner `i18n`:

   * von `/libs/livecycle/core/components/login`
   * nach `/apps/livecycle/core/components/login`

1. Löschen Sie alle Ordner in `i18n` bis auf einem, beispielsweise `en`.

1. Mit dem Ordner `en` führen Sie diese Schritte durch:

   1. Benennen Sie den Ordner nach dem Gebietsschema, das unterstützt werden soll. Beispiel: `ar`.

   1. Ändern Sie den Wert der Eigenschaft `jcr:language` in `ar` (für den Ordner `ar`).

   >[!NOTE]
   >
   >Wenn das Gebietsschema eine Sprach- und Ländercodekombination ist, beispielsweise `ar-DZ`, ändern Sie den Ordnernamen und den Eigenschaftswert zu `ar-DZ`.

1. Kopieren `login.jsp`:

   * von `/libs/livecycle/core/components/login`
   * nach `/apps/livecycle/core/components/login`

1. Ändern Sie das folgende Code-Fragment für `/apps/livecycle/core/components/login/login.jsp`:

***Gebietsschema ist Sprachcode***

```jsp
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
```

To

```jsp
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

```jsp
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
```

To

```jsp
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

***So ändern Sie das Standardgebietsschema***

```jsp
   String browserLocale = "en";
   for(int i=0; i<locales.length; i++)

   To

   String browserLocale = "ar";
   for(int i=0; i<locales.length; i++)
```

### Hinzufügen von neuem Text oder Ändern von vorhandenem Text {#adding-new-text-or-modifying-existing-text}

1. Kopieren Sie den Ordner `i18n`:

   * von `/libs/livecycle/core/components/login`
   * nach `/apps/livecycle/core/components/login`

1. Ändern Sie nun den Wert der Eigenschaft `sling:message` des Knotens (unter dem Codeordner des gewünschten Gebietsschemas) für den Sie den Text ändern möchten. Die Übersetzung wird mit dem Schlüssel durchgeführt, der im Wert der Eigenschaft `sling:key` des Knotens aufgeführt ist.

1. Um ein neues Schlüssel-Wert-Paar hinzuzufügen, führen Sie die folgenden Aktionen aus. Sehen Sie sich ein Beispiel im folgenden Screenshot an.

   1. Erstellen Sie unter den Gebietsschemaordnern einen Knoten vom Typ `sling:MessageEntry` oder kopieren Sie einen vorhandenen Knoten und benennen Sie ihn um.
   1. Kopieren `login.jsp` :

      * von `/libs/livecycle/core/components/login`

      * nach `/apps/livecycle/core/components/login`

   1. Ändern Sie `/apps/livecycle/core/components/login/login.jsp`, um den neu hinzugefügten Text einzubinden.

   ![Hinzufügen eines neuen Schlüssel-Wert-Paares](assets/capture_new.png)

   ```jsp
   div class="loginContent">
   
                       <span class="loginFlow"></code>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></code>
                       <span class="loginTitle"><%= i18n.get("Login") %></code>
                       <% if (loginFailed) {%>
   ```

   To

   ```jsp
   div class="loginContent">
   
                       <span class="loginFlow"></code>
                       <span class="loginVersion"><%= i18n.get("My Welcome Message") %></code>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></code>
                       <span class="loginTitle"><%= i18n.get("Login") %></code>
                       <% if (loginFailed) {%>
   ```

### Hinzufügen eines neuen Stils oder Ändern des vorhandenen Stils {#adding-new-style-or-modifying-existing-style}

1. Kopieren Sie den Knoten `login`:

   * von `/libs/livecycle/core/content`
   * nach `/apps/livecycle/core/content`

1. Löschen Sie die Dateien `login.js` und `jquery-1.8.0.min.js` vom Knoten `/apps/livecycle/core/content/login.`
1. Ändern Sie die Stile in der CSS-Datei.
1. So fügen Sie neue Stile hinzu:

   1. Fügen Sie neue Stile zu `/apps/livecycle/core/content/login/login.css` hinzu
   1. Kopieren `login.jsp`

      * von `/libs/livecycle/core/components/login`

      * nach `/apps/livecycle/core/components/login`

   1. Ändern Sie `/apps/livecycle/core/components/login/login.jsp`, um die neu hinzugefügten Stile einzubinden.


Beispiel:

* Hinzufügen von Folgendem zu `/apps/livecycle/core/content/login/login.css`.

```
css.newLoginContentArea {
    width: 700px;
    padding: 100px 0px 0px 100px;
   }
```

* Ändern Sie Folgendes in `/apps/livecycle/core/components/login.jsp`.


  ```jsp
  <div class="loginContentArea">
  ```

  To

  ```jsp
  <div class="newLoginContentArea">
  ```

>[!NOTE]
>
>Wenn die vorhandenen Bilder in `/apps/livecycle/core/content/login` (kopiert von `/libs/livecycle/core/content/login`) gelöscht sind, löschen Sie auch die entsprechenden Verweise in CSS.

### Fügen Sie neue Bilder hinzu {#add-new-images}

1. Führen Sie die Schritte zum Hinzufügen eines neuen Stils oder Ändern des vorhandenen Stils durch (oben beschrieben).
1. Fügen Sie neue Bilder in `/apps/livecycle/core/content/login` hinzu. So fügen Sie ein Bild hinzu:

   1. Installieren Sie den WebDAV-Client.
   1. Navigieren Sie mithilfe eines WebDAV-Clients zum Ordner `/apps/livecycle/core/content/login`. Weitere Informationen finden Sie unter [WebDAV-Zugriff](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/webdav-access.html?lang=de).

   1. Fügen Sie neue Bilder hinzu.

1. Fügen Sie neue Stile in `/apps/livecycle/core/content/login/login.css,` hinzu, die den in `/apps/livecycle/core/content/login` hinzugefügten neuen Bildern entsprechen.
1. Verwenden Sie die neuen Stile in `login.jsp` unter `/apps/livecycle/core/components`.

Beispiel:


```css
.newLoginContainerBkg {

 background-image: url(my_Bg.gif);
 background-repeat: no-repeat;
 background-position: left top;
 width: 727px;
}
```


    * Ändern Sie Folgendes in /apps/livecycle/core/components/login.jsp.

```jsp
<div class="loginContainerBkg">
```

To

```jsp
<div class="newLginContainerBkg">
```
