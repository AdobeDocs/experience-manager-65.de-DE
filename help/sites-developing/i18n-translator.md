---
title: Verwalten von Wörterbüchern mithilfe des Übersetzers
seo-title: Using Translator to Manage Dictionaries
description: AEM bietet eine Konsole für die Verwaltung der verschiedenen Übersetzungen von Texten, die in der Komponentenbenutzeroberfläche verwendet werden
seo-description: AEM provides a console for managing the various translations of texts used in component UI
uuid: 4eea3110-e958-473e-8d22-c84fa435edbd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: components
discoiquuid: adf3364c-11f1-45c6-b41d-2c7d48b626f9
exl-id: a8d50c09-72d0-406e-874e-50a985227a56
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '2327'
ht-degree: 43%

---

# Verwalten von Wörterbüchern mithilfe des Übersetzers{#using-translator-to-manage-dictionaries}

AEM bietet eine Konsole für die Verwaltung der verschiedenen Übersetzungen von Texten, die in der Komponenten-Benutzeroberfläche verwendet werden. Diese Konsole ist verfügbar unter

`https://<hostname>:<port-number>/libs/cq/i18n/translator.html`

Mithilfe des Übersetzer-Tools können Sie englischsprachige Zeichenfolgen und die dazugehörigen Übersetzungen verwalten. Die Wörterbücher werden im Repository erstellt (beispielsweise in /apps/myproject/i18n).

Hinweis: Das Übersetzer-Tool und die Wörterbücher, die Sie verwalten, dienen zur Darstellung der Komponentenbenutzeroberfläche in verschiedenen Sprachen. Wenn Sie Seiten oder benutzergenerierte Inhalte übersetzen möchten, lesen Sie [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md) und [Übersetzung benutzergenerierter Inhalte](/help/communities/translate-ugc.md).

>[!CAUTION]
>
>Bearbeiten Sie nur Wörterbücher, die für Ihr Projekt erstellt werden und sich unter `/apps` befinden.
>
>AEM Systemwörterbücher sind auch in diesem Tool verfügbar. Ändern Sie nicht die AEM Systemwörterbücher, da dies Probleme mit der AEM Benutzeroberfläche verursachen kann. Außerdem können Änderungen bei der Aktualisierung verloren gehen. AEM-Systemwörterbücher befinden sich unter `/libs`.

>[!NOTE]
>
>Das Übersetzer-Tool eignet sich ungeachtet seiner klassischen Benutzeroberfläche zur Übersetzung von Phrasen beliebiger Benutzeroberflächen.

Das Übersetzer-Tool zeigt die in AEM verwendeten Texte zusammen mit den verschiedenen Übersetzungen nebeneinander an:

![chlimage_1-205](assets/chlimage_1-205.png)

Sie können die englischen und übersetzten Texte durchsuchen, filtern und bearbeiten. Sie können auch Wörterbücher zur Übersetzung in das XLIFF-Format exportieren und die Übersetzungen dann wieder in die Wörterbücher importieren.

Sie können die i18n-Wörterbücher auch über diese Konsole zu einem Übersetzungsprojekt hinzufügen. Sie können entweder eine neue erstellen oder einem vorhandenen Projekt hinzufügen.

1. Klicken **Wörterbuch übersetzen**.

   ![chlimage_1-206](assets/chlimage_1-206.png)

1. Wählen Sie je nach Bedarf die Option Erstellen oder Hinzufügen aus. Ein Dialogfeld wird geöffnet.

   ![chlimage_1-207](assets/chlimage_1-207.png)

1. Füllen Sie die Felder nach Bedarf aus und klicken Sie auf „OK“. ![chlimage_1-208](assets/chlimage_1-208.png)

1. Nun können Sie auf **OK** klicken oder das Zielwörterbuch anzeigen.

   >[!NOTE]
   >
   >Weitere Informationen zu Übersetzungsprojekten finden Sie unter [Verwalten von Übersetzungsprojekten](/help/sites-administering/tc-manage.md).

## Erstellen eines Wörterbuchs {#creating-a-dictionary}

Erstellen Sie ein Wörterbuch zur Verwaltung Ihrer lokalisierten Benutzeroberflächen-Zeichenfolgen. Nach der Erstellung kann das Wörterbuch mithilfe des Übersetzungs-Tools verwaltet werden.

1. Fügen Sie mithilfe von CRXDE Lite den Stammknoten (`sling:Folder`) für Ihr neues Wörterbuch als Struktur für die Sprachdefinitionen hinzu:

   ` /apps/<projectName>/i18n`

   Beispiel: `/apps/myProject/i18n`

1. Fügen Sie die erforderliche Sprachstruktur unter diesem Stamm hinzu. Beispiel:

   ```shell
   /apps/myProject/i18n [sling:Folder]
       - de.json [nt:file] [mix:language]
           + jcr:language = de
       - fr.json [nt:file] [mix:language]
           + jcr:language = fr
   ```

   >[!NOTE]
   >
   >Dies ist die Struktur des [Sling-i18n-Moduls](https://sling.apache.org/site/internationalization-support.html).

1. Laden Sie den Übersetzer und den Wörterbuchpfad neu (z. B. `/apps/myProject/i18n`) in der Dropdown-Auswahl in der Symbolleiste verfügbar. Wählen Sie diese aus, um mit dem Hinzufügen von Zeichenfolgen und deren Übersetzungen zu beginnen.

   >[!NOTE]
   >
   >Der Übersetzer speichert nur Übersetzungen für Sprachen, die tatsächlich unter dem Pfad vorhanden sind (z. B. `/apps/myProject/i18n`).
   >
   >Achten Sie darauf, dass diese den im Raster dargestellten Sprachen entsprechen.

## Verwalten von Wörterbuchzeichenfolgen {#managing-dictionary-strings}

Verwenden Sie das Übersetzungs-Tool, um die Zeichenfolgen in Ihren Wörterbüchern zu verwalten. Sie können englische Zeichenfolgen hinzufügen, ändern und entfernen sowie übersetzte Zeichenfolgen angeben.

>[!CAUTION]
>
>Bearbeiten Sie nur Wörterbücher, die für Ihr Projekt erstellt werden und sich unter `/apps` befinden.
>
>Ändern Sie nicht die AEM Systemwörterbücher, da dies Probleme mit der AEM Benutzeroberfläche verursachen kann. Außerdem können Änderungen bei der Aktualisierung verloren gehen. AEM-Systemwörterbücher befinden sich unter `/libs`.

### Hinzufügen, Ändern und Entfernen von Zeichenfolgen {#adding-changing-and-removing-strings}

Fügen Sie englische Zeichenfolgen zu einem Wörterbuch hinzu, das Ihre Komponente internationalisiert hat. Fügen Sie nur internationalisierte Zeichenfolgen hinzu, damit Sie keine Ressourcen verschwenden, indem Sie nicht verwendete Zeichenfolgen übersetzen.

Die Zeichenfolgen, die Sie einem Wörterbuch hinzufügen, müssen genau mit der im Code angegebenen Zeichenfolge übereinstimmen. Wenn die standardmäßige englische Zeichenfolge, die im Code verwendet wird, nicht mit der englischen Zeichenfolge in einem Wörterbuch übereinstimmt, wird die übersetzte Zeichenfolge bei Bedarf nicht in der Benutzeroberfläche angezeigt. Bei Zeichenfolgen wird zwischen Groß- und Kleinschreibung unterschieden.

**Bereitstellen von Übersetzungshinweisen**

Verwenden Sie die Eigenschaft Kommentar der Wörterbuchzeichenfolge, um dem Übersetzer Informationen zur Klärung der Bedeutung der Zeichenfolge bereitzustellen. Normalerweise unterstützt die Benutzeroberfläche Benutzer bei der Bestimmung der Bedeutung mehrdeutiger Wörter. Der Übersetzer sieht die Zeichenfolge jedoch nicht im Kontext der Benutzeroberfläche. Der Übersetzungshinweis entfernt die Uneindeutigkeit. So kann ein Übersetzer mithilfe eines Kommentars beispielsweise darauf hingewiesen werden, dass das englische Wort „Request“ nicht als Verb, sondern als Substantiv verwendet wird.

Übersetzungshinweise unterscheiden auch Zeichenfolgen, die identisch sind und unterschiedliche Bedeutungen haben. Zum Beispiel kann das Wort &quot;Suche&quot;ein Substantiv oder ein Verb sein, das zwei &quot;Suche&quot;-Einträge im Wörterbuch mit zwei verschiedenen Übersetzungshinweisen erfordert. Der Code, der die Zeichenfolge anfordert, enthält auch den Übersetzungshinweis, sodass die richtige Zeichenfolge in der Benutzeroberfläche verwendet wird.

**Einschließen indizierter Variablen**

Sie können Variablen in die lokalisierte Zeichenfolge einfügen, um dem Satz Kontextbedeutung zu geben. Ein Beispiel: Nach der Anmeldung bei einer Webanwendung wird auf der Homepage folgende Nachricht angezeigt: „Willkommen zurück, Administrator. Sie haben zwei Nachrichten in Ihrem Posteingang.“ Der Seitenkontext bestimmt den Benutzernamen und die Anzahl der Nachrichten.

Wenn Sie Variablen in die lokalisierte Zeichenfolge aufnehmen möchten, platzieren Sie in Klammern eingeschlossene Indizes an der Position der Variablen im ersten Argument der GET-Methode. Beschreiben Sie die Werte in einem Übersetzungshinweis. Der Übersetzer muss die Bedeutung der Variablen kennen, da andere Sprachen ggf. eine andere Satzstruktur erfordern.

[Der Code, der die übersetzte Zeichenfolge anfordert](/help/sites-developing/i18n-dev.md#including-variables-in-localized-sentences), gibt abhängig vom Kontext entsprechende Werte für die indizierten Variablen an.

Wenn sich ein Benutzer also beispielsweise bei einer Website anmeldet, wird folgende Zeichenfolge angezeigt und diese Zeichenfolge ist auch im Wörterbuch enthalten:

`Welcome back {0}. You have {1} messages.`

Der folgende Kommentar beschreibt die Variablen:

`{0} = the user name, {1} = the number of items in the user's inbox`

**Ändern von Zeichenfolgen**

Ändern oder entfernen Sie englische Zeichenfolgen, da sie im Code geändert oder entfernt werden. Wenn Sie eine Zeichenfolge ändern, wird die ursprüngliche Zeichenfolge beibehalten und eine neue Zeichenfolge erstellt, die die Änderung widerspiegelt. Bevor Sie eine Zeichenfolge entfernen, stellen Sie sicher, dass sie von keinem Code verwendet wird.

Gehen Sie wie folgt vor, um eine Zeichenfolge hinzuzufügen.

1. Wählen Sie im Dropdown-Menü Wörterbücher das Wörterbuch aus, dem Sie eine Zeichenfolge hinzufügen möchten. Im Dropdown-Menü werden Wörterbücher durch ihren Pfad im Repository dargestellt.
1. Klicken Sie über der Tabelle mit den Zeichenfolgen und Übersetzungen auf „Hinzufügen“.

   ![chlimage_1-209](assets/chlimage_1-209.png)

1. Geben Sie im Feld &quot;String&quot;des Dialogfelds &quot;String hinzufügen&quot;die englische Zeichenfolge ein. Geben Sie bei Bedarf im Feld Kommentar einen Übersetzungshinweis für den Übersetzer ein.
1. Klicken Sie auf „OK“.
1. Klicken Sie auf „Speichern“.

   ![chlimage_1-210](assets/chlimage_1-210.png)

Gehen Sie wie folgt vor, um eine Zeichenfolge in einem Wörterbuch zu ändern.

1. Wählen Sie im Dropdown-Menü Wörterbücher das Wörterbuch aus, das die zu ändernde Zeichenfolge enthält.
1. Doppelklicken Sie auf die zu ändernde Zeichenfolge.
1. Wählen Sie im Dialogfeld &quot;Zeichenfolge bearbeiten&quot;die Option &quot;Zeichenfolge oder Kommentar ändern&quot;(erstellt eine Kopie).

   ![chlimage_1-211](assets/chlimage_1-211.png)

1. Ändern Sie die Zeichenfolge oder den Kommentar und klicken Sie auf &quot;OK&quot;.
1. Klicken Sie auf „Speichern“.

   ![chlimage_1-212](assets/chlimage_1-212.png)

Gehen Sie wie folgt vor, um eine Zeichenfolge aus einem Wörterbuch zu entfernen.

1. Wählen Sie im Dropdownmenü Wörterbücher das Wörterbuch aus, aus dem Sie eine Zeichenfolge entfernen möchten.
1. Klicken Sie auf „Entfernen“.

   ![chlimage_1-213](assets/chlimage_1-213.png)

1. Klicken Sie auf „Speichern“.

   ![chlimage_1-214](assets/chlimage_1-214.png)

### Suchen nach Zeichenfolgen {#searching-for-strings}

Die Suchleiste am unteren Rand des Übersetzer-Tools bietet verschiedene Auswahloptionen für Zeichenfolgen:

* **Nach Text filtern:** Ein Muster, das mit der englischen Zeichenfolge, mit dem Kommentar oder mit Übersetzungen abgeglichen wird. Nur Elemente, die dem Muster ganz oder teilweise entsprechen, werden in der Tabelle angezeigt.
* **Änderungen: Beliebig, Geändert, Neu, Gelöscht:** Zeigt Elemente an, die geändert und nicht gespeichert wurden.

   * Any: Zeigt Elemente an, die geändert, hinzugefügt oder entfernt wurden.
   * Geändert: Zeigt geänderte Elemente an.
   * Neu: Zeigt hinzugefügte Elemente an.
   * Gelöscht: Zeigt Elemente an, die entfernt werden sollen.
   * Mehrfachauswahl: Zeigt Elemente mit allen ausgewählten Eigenschaften an.

* **Hat Kommentar**: Zeigt Elemente an, die Kommentare für Übersetzer enthalten.
* **Fehlende Übersetzungen:** Zeigt Elemente an, bei denen für mindestens eine Sprache keine Übersetzung vorliegt.

![chlimage_1-215](assets/chlimage_1-215.png)

1. Wählen Sie in der Suchleiste die Filteroptionen aus.
1. Um mithilfe der Optionen zu filtern, klicken Sie auf &quot;Filter&quot;.
1. Um die Filter zu entfernen und alle Elemente im Wörterbuch anzuzeigen, klicken Sie auf &quot;Löschen&quot;.

### Bearbeiten übersetzter Zeichenfolgen {#editing-translated-strings}

Nachdem Sie die englische Zeichenfolge zu einem Wörterbuch hinzugefügt haben, können Sie Übersetzungen der Zeichenfolge hinzufügen. Sie können auch [Wörterbuch exportieren](/help/sites-developing/i18n-translator.md#exporting-a-dictionary) , damit es von einem Dritten übersetzt werden kann.

1. Auswählen [Ihr projektspezifisches Wörterbuch](#creating-a-dictionary) da es den Pfad im Repository angibt, das die Übersetzungen enthält. Wählen Sie beispielsweise **Wörterbücher** as:

   `/apps/myProject/i18n`

   >[!CAUTION]
   >
   >Bearbeiten Sie nur Wörterbücher, die für Ihr Projekt erstellt werden und sich unter `/apps` befinden.
   >
   >AEM Systemwörterbücher sind auch in diesem Tool verfügbar. Ändern Sie nicht die AEM Systemwörterbücher, da dies Probleme mit der AEM Benutzeroberfläche verursachen kann. Außerdem können Änderungen bei der Aktualisierung verloren gehen. AEM-Systemwörterbücher befinden sich unter `/libs`.

1. Die übersetzten Texte für die Zeichenfolgen können wie folgt bearbeitet werden:

   * Doppelklicken Sie auf die entsprechende Sprache für die erforderliche Zeichenfolge, um diesen einzelnen Text zu bearbeiten:

   ![chlimage_1-216](assets/chlimage_1-216.png)

   * Doppelklicken Sie auf die **Zeichenfolge** oder **Kommentar** -Felder für die erforderliche Zeichenfolge zum Öffnen der **Zeichenfolge bearbeiten** Dialogfeld, bearbeiten Sie die Übersetzung(en) nach Bedarf und klicken Sie auf **OK** zum Schließen des Dialogfelds:

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. Klicken Sie auf der Symbolleiste auf **Speichern**, um die Änderungen zu übernehmen.

   >[!NOTE]
   >
   >Wenn Sie anstelle von **Speichern** auf **Zurücksetzen und aktualisieren** klicken, werden alle Änderungen an den vorherigen Texten rückgängig gemacht.

## Verwenden von Übersetzern von Drittanbietern {#using-third-party-translators}

Mit dem Übersetzungs-Tool können Sie Wörterbücher für externe Übersetzungsdienste exportieren und anschließend wieder importieren.

### Wörterbücher exportieren {#exporting-a-dictionary}

Exportieren Sie ein Wörterbuch in eine XLIFF-Datei, damit ein Drittanbieterdienst die Wörterbuchzeichenfolgen übersetzen kann.

* Exportieren Sie ein Wörterbuch und fügen Sie die englische Sprache und die übersetzten Begriffe für eine Sprache hinzu.
* Exportieren Sie nur einige oder alle englischen Zeichenfolgen.

Wenn Sie eine XLIFF-Datei exportieren und eine Sprache einschließen, muss die Knotenstruktur des Wörterbuchs im Repository diese Sprache enthalten. Wenn die Sprache nicht enthalten ist, treten Fehler auf. Wenn Sie also beispielsweise die XLIFF-Datei für Französisch exportieren möchten, muss der Wörterbuchordner unter `mix:language` den untergeordneten Knoten `fr` enthalten. (Siehe [Erstellen eines Wörterbuchs](/help/sites-developing/i18n-translator.md#creating-a-dictionary).)

Gehen Sie wie folgt vor, um eine XLIFF-Datei für eine bestimmte Sprache zu exportieren:

1. Öffnen Sie das Übersetzungs-Tool `http://<host>:<port>/libs/cq/i18n/translator.html`
1. Wählen Sie im Dropdown-Menü Wörterbücher das zu exportierende Wörterbuch aus.
1. Klicken Sie auf „Exportieren“ > „Vollständige XLIFF-Optionen für *XX* exportieren“, wobei *XX* der aus zwei Buchstaben bestehende Sprach-Code (etwa „DE“ oder „FR“) ist.

   Die XLIFF-Datei wird in einer neuen Registerkarte oder einem neuen Fenster geöffnet.

1. Verwenden Sie die Befehle des Webbrowsers, um die Seite als Datei in Ihrem Dateisystem zu speichern, z. B. &quot;Datei&quot;> &quot;Seite speichern unter&quot;.

Führen Sie die folgenden Schritte aus, um alle oder nur einige der englischen Zeichenfolgen zu exportieren.

1. Öffnen Sie das Übersetzungs-Tool. `http://<host>:<port>/libs/cq/i18n/translator.html`
1. Wählen Sie im Dropdown-Menü Wörterbücher das zu exportierende Wörterbuch aus.
1. Wenn Sie eine Teilmenge der Strings exportieren, wählen Sie die Elemente im Wörterbuch aus, die exportiert werden sollen. Wenn Sie keine Elemente auswählen, werden alle Elemente exportiert.
1. Klicken Sie auf Exportieren > Auswahl als XLIFF exportieren (nur Zeichenfolgen).
1. Kopieren Sie im angezeigten Dialogfeld den Text und fügen Sie ihn in eine Textdatei ein.

### Wörterbücher importieren {#importing-a-dictionary}

Importieren Sie eine XLIFF-Datei in ein Wörterbuch, um das Wörterbuch zu füllen. Wenn das Wörterbuch eine Übersetzung für eine englische Zeichenfolge enthält und die XLIFF-Datei eine andere Übersetzung für dieselbe Zeichenfolge enthält, wird die Wörterbuchübersetzung ersetzt.

1. Öffnen Sie das Übersetzungs-Tool `http://<host>:<port>/libs/cq/i18n/translator.html`
1. Klicken Sie auf Importieren > XLIFF-Übersetzungen.
1. Wählen Sie die zu importierende Datei aus und klicken Sie auf OK.

## Verwalten unterstützter Sprachen {#managing-supported-lanuages}

Fügen Sie vom Übersetzungs-Tool unterstützte Sprachen hinzu, die Benutzern auf Ihren Webseiten angezeigt werden, oder entfernen Sie sie.

### Ändern der in der Wörterbuchtabelle aufgelisteten Sprachen {#changing-languages-listed-in-the-dictionary-table}

Die Wörterbuchtabelle des Übersetzer-Tools umfasst folgende Sprachen:

* de – Deutsch
* fr – Französisch
* it – Italienisch
* es – Spanisch
* ja – Japanisch
* pt-br - Brasilianisches Portugiesisch
* zh-cn - Vereinfachtes Chinesisch
* zh-tw - Traditionelles Chinesisch (begrenzte Unterstützung)
* ko-kr - Koreanisch

Gehen Sie wie folgt vor, um Sprachen hinzuzufügen oder zu entfernen.

1. Erstellen Sie mit CRXDE Lite einen neuen Knoten:

   `/etc/languages`

1. Erstellen Sie in diesem Knoten eine Eigenschaft:

   * **Name**: `languages`
   * **Typ**: `Multi-String`
   * **Wert**: die Liste der Sprachen, die angezeigt werden sollen. Beispiel:

      * fr
      * es

   >[!NOTE]
   >
   >Die Sprach-Codes müssen in Kleinbuchstaben geschrieben sein.

1. Klicken Sie in CRXDE Lite auf **Alle speichern** und laden Sie den Übersetzer neu. Das Raster wird aktualisiert und zeigt nun die definierten Sprachen an.

   >[!NOTE]
   >
   >Der Übersetzer speichert nur Übersetzungen für Sprachen, die tatsächlich [im Wörterbuch vorhanden](#creating-a-dictionary) sind (sich also unter dem Wörterbuchpfad befinden; zum Beispiel `/apps/myProject/i18n`).
   >
   >Achten Sie darauf, dass diese den im Raster dargestellten Sprachen entsprechen.

### Verfügbarmachen von Sprachen für Autoren {#making-languages-available-to-authors}

Nachdem Sie ein Wörterbuch für eine neue Sprache in Ihrer AEM-Instanz definiert haben, müssen Sie sie für die Autoren verfügbar machen, damit diese sie auswählen können (zum Beispiel zur Nutzung in **Voreinstellungen**):

1. Gehen Sie wie folgt vor, um die Liste mit den Sprachen zu ändern, die in der **Sicherheitskonsole** unter **Voreinstellungen** verfügbar sind:

   1. Erstellen Sie eine Überlagerung in Ihrem Anwendungs-Code für:

      ```
              /libs/cq/security/widgets/source/widgets/security/Preferences.js
       and update as required.
      ```

1. Nehmen Sie an Ihrer Anwendung folgende Änderungen vor, um die Sprache in den **Voreinstellungen** Ihrer **Websites-Konsole** verfügbar zu machen:

   1. Erstellen Sie eine Überlagerung für die Struktur unter:

      `/libs/cq/security/content/tools/userProperties`

   1. Aktualisieren Sie die Sprachliste innerhalb der Überlagerung unter:

      `items/common/items /lang/options`

1. Speichern Sie alles und laden Sie die entsprechende Konsole neu.

### Ändern von Sprachnamen und Standardländern {#changing-language-names-and-default-countries}

Verschiedene Länder verwenden dieselbe Sprache, zum Beispiel die USA, Großbritannien und Australien, alle verwenden Englisch. Dies wird durch einen Code angegeben, der sowohl die Sprache als auch das Land umfasst – beispielsweise `en_GB`, `en_US` und `en_AU`.

Die Standardländer werden verwendet, wenn Flags angezeigt werden (z. B. im Dialogfeld &quot;Sprachkopie&quot;), um das Land für einen Sprachcode aufzulösen.

>[!NOTE]
>
>Bei Lokalisierungen, die vom Übersetzer oben verwaltet werden, funktioniert nur die genaue Sprache. Wenn im Dropdown-Menü mit den Spracheinstellungen `en_uk` verwendet wird, muss auch das Repository ein Wörterbuch für `en_uk` enthalten.

So ändern Sie die Standarddefinitionen:

1. Eine Sprachliste ist unter dem folgenden Pfad gespeichert:

   `/libs/wcm/core/resources/languages`

   Überlagern Sie sie, indem Sie sie in das folgende Verzeichnis kopieren:

   `/apps/wcm/core/resources/languages`

   Ändern oder erweitern Sie die Liste dort. Die Eigenschaft `defaultCountry` auf einem Sprachknoten (z. B. `ja`) muss den vollständigen Code enthalten, z. B. `ja_jp`, die `jp` als Standardland für die Sprache `ja`.

1. Aktualisieren Sie den **CQ WCM Language Manager**.

   * **Sprachliste**:

     Der Pfad zur Sprachliste im Repository Legen Sie diese Option auf den Ort für die Überlagerung fest:

     ```
            /apps/wcm/core/resources/languages
     ```

   Dies ist über die OSGi-Web-Konsole möglich:

   ```shell
   https://<hostname>:<port-number>/system/console/configMgr/com.day.cq.wcm.core.impl.LanguageManagerImpl
   ```

## Veröffentlichen von Wörterbüchern {#publishing-dictionaries}

Integrieren Sie Ihre Wörterbücher in die Versionsverwaltung Ihrer AEM. Schließen Sie beispielsweise das Wörterbuch in das Inhaltspaket Ihrer Anwendung ein, um es für die Veröffentlichungsinstanz bereitzustellen. Diese Strategie bietet die folgenden Vorteile:

* Wörterbücher sind für Komponenten in ihrer Veröffentlichungsumgebung verfügbar.
* Änderungen an Komponenten-UI-Zeichenfolgen werden zusammen mit den aktualisierten Übersetzungen bereitgestellt.

Des Weiteren empfiehlt es sich, Wörterbuchzeichenfolgen im Rahmen des regulären Software-Entwicklungszyklus zu testen.

>[!NOTE]
>
>Regelmäßige Veröffentlichungsfunktionen oder Replikation sollten nicht für Wörterbücher verwendet werden. Stattdessen sollten Wörterbücher genauso behandelt werden wie Code und Konfiguration. Dazu gehört die Verwendung der Quell-Code-Kontrolle zur Verfolgung von Änderungen und die Verwendung von Inhaltspaketen zur Anwendung von Änderungen auf die Autoren- und Veröffentlichungsinstanz.

>[!NOTE]
>
>Bei Verwendung von Dispatcher müssen Sie [zwischengespeicherte Seiten ungültig machen](https://helpx.adobe.com/de/experience-manager/dispatcher/using/page-invalidate.html), um neue Wörterbuchzeichenfolgen in gerenderte Komponenten-Zeichenfolgen einzuschließen.
