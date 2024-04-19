---
title: Konfigurieren des Linktrackings für Adobe Analytics
description: Erfahren Sie mehr über die Konfiguration von Linktracking für SiteCatalyst.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 9fa3e531-11b3-4b8d-a87c-a08faf06f5b7
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '1615'
ht-degree: 98%

---


# Konfigurieren des Linktrackings für Adobe Analytics{#configuring-link-tracking-for-adobe-analytics}

Wenn Benutzende auf Links auf Seiten Ihrer Website klicken, können Sie zugehörige Informationen in Adobe Analytics erfassen.  Verwenden Sie beispielsweise Linktracking, um zu erfahren, wie Benutzende mit Ihrer Site interagieren, und Datei-Downloads sowie Ausstiegs-Links nachzuverfolgen.

## Konfigurieren von Linktracking für ein Adobe Analytics-Framework {#configuring-link-tracking-for-an-adobe-analytics-framework}

1. Gehen Sie unter **Navigation** über **Bereitstellung** > **Cloud-Services** zum Abschnitt **Adobe Analytics**.

1. Öffnen Sie mit **Konfigurationen anzeigen** das erforderliche Adobe Analytics-Framework.
1. Erweitern Sie den Abschnitt **Konfiguration von Linktracking** und nehmen Sie die erforderlichen Konfigurationen vor (auf dieser Seite werden weitere Informationen bereitgestellt):

   ![Analytics-Framework](assets/aa-08.png)

## Nachverfolgen von Datei-Downloads {#tracking-file-downloads}

Konfigurieren Sie das Adobe Analytics-Framework, damit heruntergeladene Dateien von zugehörigen Seiten automatisch als Downloads in Adobe Analytics nachverfolgt werden. Wenn Sie das Tracking von Downloads aktivieren, werden nur die von Ihnen angegebenen Dateitypen nachverfolgt.

Downloads der folgenden Dateitypen werden standardmäßig nachverfolgt:

* exe
* zip
* wav
* mp3
* mov
* mpg
* avi
* wmv
* doc
* pdf
* xls

Wenn also etwa für PDF-Dateien das Download-Tracking aktiviert ist, wird beim Klicken auf Links zu PDF-Dateien der Download des PDFs nachverfolgt.

Die Eigenschaften für die Download-Nachverfolgung werden als Code in der für eine Seite erstellten Datei `analytics.sitecatalyst.js` implementiert. Das folgende Code-Beispiel steht für eine standardmäßige Konfiguration zur Download-Nachverfolgung:

```
s.trackDownloadLinks= true;
s.linkDownloadFileTypes= 'exe,zip,wav,mp3,mov,mpg,avi,wmv,doc,pdf,xls';
```

So aktivieren Sie die Download-Nachverfolgung für Ihr Adobe Analytics-Framework:

1. [Öffnen Sie das Adobe Analytics-Framework und erweitern Sie den Abschnitt Konfiguration der Link-Überwachung](#configuring-link-tracking-for-an-adobe-analytics-framework).
1. Aktivieren Sie **Downloads nachverfolgen**.
1. Geben Sie im Feld **Download-Dateitypen** die Dateinamenserweiterungen für die nachzuverfolgenden Dateitypen ein.

## Tracking externer Links {#tracking-external-links}

Sie können das Klicken auf externe Links (Ausstiegs-Links) auf Ihren Seiten nachverfolgen.

So verfolgen Sie externe Links für Ihr Adobe Analytics-Framework nach:

1. [Öffnen Sie das Adobe Analytics-Framework und erweitern Sie den Abschnitt **Konfiguration der Link-Überwachung**](#configuring-link-tracking-for-an-adobe-analytics-framework).
1. Konfigurieren Sie die folgenden Eigenschaften gemäß Ihren Anforderungen.

Eigenschaften zum Nachverfolgen beim Klicken auf externe Links:

* **Externe nachverfolgen**
Aktiviert die Nachverfolgung externer Links.

* **Externe Filter**
(Optional) Definiert Filter zum Abgleichen der externen URLs von Link-Zielen. Wenn die Link-Ziele dem Filter entsprechen, wird der Link nachverfolgt.  Externe Filter sind nützlich, um nur einige externe Links auf Ihren Seiten nachzuverfolgen.

  Um die nachzuverfolgenden externen Links festzulegen, geben Sie die URL des Link-Ziels vollständig oder teilweise ein. Trennen Sie mehrere Filter durch Kommas.  Schließen Sie Zeichenfolgenliterale in einfache Anführungszeichen ein.  Ist kein Wert angegeben (Standardwert `''`, zwei einfache Anführungszeichen), werden alle externen Links nachverfolgt.

* **Interne Filter**
Definiert Filter zum Abgleichen der URLs interner Links. Wenn der Link URLs zum Ziel hat, die diesem Filter entsprechen, wird der Link nicht nachverfolgt.  Der Standardwert ist ein JavaScript-Befehl, der den Host-Namen der URL für die aktuelle Fensteradresse zurückgibt.

  Um die nicht nachverfolgten internen Links festzulegen, geben Sie die interne URL des Link-Ziels vollständig oder teilweise ein. Trennen Sie mehrere Filter durch Kommas.  Schließen Sie Zeichenfolgenliterale in einfache Anführungszeichen ein.

  Der Standardwert ist `'javascript:,'+window.location.hostname`

* **Suchbegriff belassen**
Schließt URL-Parameter ein, wenn Übereinstimmungen mit internen und externen Filtern bewertet werden.

  Aktivieren Sie diese Eigenschaft, um URL-Parameter beim Bewerten von Link-Ziel-URLs gegenüber externen und internen Filtern einzuschließen.

Die Eigenschaften für die Nachverfolgung externer Links werden als Code in der für eine Seite erstellten Datei `analytics.sitecatalyst.js` implementiert. Der folgende Beispiel-Code wird für eine Seite mit einem Framework generiert, für das die Nachverfolgung externer Links aktiviert ist – mit folgender Konfiguration:

* Der externe Filter ist: `'google.com'`
* Der interne Filter entspricht dem Standardwert: `'javascript:,'+window.location.hostname`
* Suchbegriffe sind nicht beim Bewerten des Link-Ziels gegenüber den Filtern eingeschlossen.

```
s.trackExternalLinks= false;
s.linkExternalFilters= 'google.com';
s.linkInternalFilters= 'javascript:,'+window.location.hostname;
s.linkLeaveQueryString= false;
```

## Senden von Variablendaten bei Link-Klicks {#sending-variable-data-with-link-clicks}

Sie können AEM so konfigurieren, dass Ereignis- und Variablendaten an Adobe Analytics gesendet werden, wenn Benutzende auf einen Link klicken. Über die Eigenschaften **Konfiguration der Link-Überwachung** können Sie die Adobe Analytics-Ereignisse und -Variablen angeben, die bei Link-Klicks nachverfolgt werden sollen.

Die Framework-Zuordnungen bestimmen die Ereignis- und Variablenwerte. Sie können Adobe Analytics-Variablen den Variablen Ihrer Inhaltskomponenten zuordnen, die die bei Link-Klicks nachzuverfolgenden Daten speichern.

So senden Sie Variablendaten bei Link-Klicks:

1. [Öffnen Sie das Adobe Analytics-Framework und erweitern Sie den Abschnitt Konfiguration der Link-Überwachung](#configuring-link-tracking-for-an-adobe-analytics-framework).
1. Konfigurieren Sie die folgenden Eigenschaften gemäß Ihren Anforderungen.

Eigenschaften zum Senden von Variablendaten bei Link-Klicks:

* **Ereignisse für Hyperlink-Überwachung**
Geben Sie die Adobe Analytics-Ereignisvariablen ein, die zum Zählen der Link-Klicks verwendet werden sollen.

  Trennen Sie mehrere Variablennamen durch Kommas.

  Beim Standardwert `None` werden keine Ereignisse nachverfolgt.

* **Vars für Hyperlink-Überwachung**
Geben Sie die Adobe Analytics-Variablen ein, die bei Link-Klicks an Adobe Analytics gesendet werden sollen. Trennen Sie mehrere Variablennamen durch Kommas.

  Beim Standardwert `None` werden keine Variablendaten gesendet.

Wenn Sie die zu sendenden Ereignisse und Variablen angeben, wird die Konfiguration als Code in der für eine Seite generierten Datei `analytics.sitecatalyst.js` implementiert. Der folgende Beispiel-Code wird für eine Seite generiert, wenn das Framework das Ereignis `event10` und die Eigenschaft `prop4` nachverfolgt:

```
s.linkTrackEvents= 'event10';
s.linkTrackVars= 'prop4';
```

## Beispielhafte Konfiguration der Link-Überwachung {#example-link-tracking-configuration}

Gehen Sie wie folgt vor, um sich mit dem Verhalten bei der Link-Überwachung der Adobe Analytics-Integration vertraut zu machen. Die Vorgehensweisen enthalten Ergebnisse von [Adobe Marketing Cloud Debugger](https://experienceleague.adobe.com/docs/debugger/using/experience-cloud-debugger.html?lang=de).

### Allgemeine Konfiguration {#general-configuration}

Dieses Beispiel zeigt, wie die Zuordnung im Zusammenhang mit der Überwachung und dem Debugger erfolgt:

1. Öffnen Sie das mit einer Web-Seite verknüpfte Framework.
1. Ziehen Sie die **Seitenkomponente** in den Zuordnungsbereich des Frameworks. Die **Seitenkomponente** gehört zur Komponentengruppe **Allgemein** im Sidekick.

   >[!NOTE]
   >
   >Die Komponente, die Sie in einem realen Szenario verwenden sollten, hängt von der Komponente ab, von der (falls überhaupt) geerbt wird.
   >
   >Ist dies nicht der Fall, sollten Sie dort Ihre eigene Komponente bereitstellen (indem Sie einen Unterknoten „analytics“ in der zugehörigen Seitenkomponente definieren).

   Konfigurieren Sie die Zuordnung gemäß der folgenden Tabelle, indem Sie die Analytics-Variable (SiteCatalyst-Variable) aus dem linken Seitenbereich ziehen:

<table>
 <tbody>
  <tr>
   <th>CQ-Variable<br /> </th>
   <th>Eintrag im Variablen-Browser<br /> </th>
   <th>Adobe Analytics-Variable</th>
  </tr>
  <tr>
   <td>pagedata.title</td>
   <td>Benutzerspezifisches eVar 1 (evar1)</td>
   <td>eVar1</td>
  </tr>
  <tr>
   <td>eventdata.events.pageView</td>
   <td>Benutzerdefiniertes Ereignis 1 (event1)</td>
   <td>event1</td>
  </tr>
 </tbody>
</table>

1. Ziehen Sie die Suchkomponente in den Zuordnungsbereich des Frameworks.  Die Suchkomponente gehört zur allgemeinen Komponentengruppe im Sidekick.  Konfigurieren Sie die Zuordnung gemäß der folgenden Tabelle, indem Sie die Analytics-Variable (SiteCatalyst-Variable) aus dem linken Seitenbereich ziehen:

<table>
 <tbody>
  <tr>
   <th>CQ-Variable<br /> </th>
   <th>Eintrag im Variablen-Browser</th>
   <th>Adobe Analytics-Variable</th>
  </tr>
  <tr>
   <td>eventdata.keyword</td>
   <td>Benutzerspezifisches eVar 2 (evar2)</td>
   <td>eVar2</td>
  </tr>
  <tr>
   <td>eventdata.results</td>
   <td>Benutzerspezifisches eVar 3 (evar3)</td>
   <td>eVar3</td>
  </tr>
  <tr>
   <td>eventdata.events.search</td>
   <td>Benutzerdefiniertes Ereignis 2 (event2)</td>
   <td>event2</td>
  </tr>
 </tbody>
</table>

### Konfigurieren von externem Linktracking {#configure-external-link-tracking}

1. Erweitern Sie in Ihrem Framework den Bereich **Linktracking-Konfiguration**.
1. Heben Sie die Auswahl für **Downloads nachverfolgen** auf.

1. Wählen Sie **Externe nachverfolgen** aus.
1. Heben Sie die Auswahl für **Abfragezeichenfolge belassen** auf.
1. Verwenden Sie den folgenden Wert für die Liste **Externe Filter**, um diesen als externe URL anzugeben:

   `'yahoo.com'`

1. Fügen Sie dem Feld **Ereignisse für Hyperlink-Überwachung** den folgenden Wert hinzu:

   ```
       event1,event2
   ```

1. Fügen Sie dem Feld **Vars für Hyperlink-Überwachung** den folgenden Wert hinzu:

   ```
       eVar1,eVar2
   ```

1. Fügen Sie auf der mit dem Framework verknüpften Seite eine **Textkomponente** hinzu. Fügen Sie innerhalb der **Textkomponente** einen Hyperlink zur folgenden Adresse hinzu:

   `https://search.yahoo.com/?p=this`

1. Wechseln Sie in den **Vorschaumodus** und klicken Sie auf den Link.

Der Abruf sieht bei der Anzeige mit Adobe Marketing Cloud Debugger wie folgt aus:

![Adobe Marketing Cloud Debugger](assets/aa-leavequerysearch-blank.png)

>[!NOTE]
>
>Die URL umfasst nicht die Abfragezeichenfolge: `?p=this`

### Einschließen von URL-Parametern {#include-the-url-parameter}

1. Erweitern Sie im Framework den Bereich **Linktracking-Konfiguration**.
1. Aktivieren Sie **Abfragezeichenfolge belassen**.
1. Laden Sie die Seitenvorschau neu und klicken Sie auf den Link.

Die in Adobe Marketing Cloud Debugger angezeigten Aufrufdetails ähneln dem folgenden Beispiel:

![Erneut Adobe Marketing Cloud Debugger](assets/aa-leavequerysearch-active.png)

>[!NOTE]
>
>Dieses Mal umfasst die URL die Abfragezeichenfolge: `?p=this`

## Ad-hoc-Linktracking {#ad-hoc-link-tracking}

Mit Ad-hoc-Linktracking können Inhaltsautorinnen und Inhaltsautoren das Linktracking für eine Komponente konfigurieren.  Die Konfiguration der Komponente setzt die **Linktracking-Konfiguration** des Frameworks außer Kraft. Auf mit dem Framework verknüpften Seiten können daher **Textkomponenten** für das Linktracking von URLs konfiguriert werden.

Durch eine Ad-hoc-Hyperlink-Überwachung können Sie Download-Links und externe Links zusammen mit Ereignis- und Variablendaten nachverfolgen.

Zum Aktivieren der Ad-hoc-Hyperlink-Überwachung müssen Sie wie folgt vorgehen:

* [Verknüpfen Sie die Seite, die die **Textkomponente** enthält, mit dem Framework](/help/sites-administering/adobeanalytics-connect.md#associating-a-page-with-a-adobe-analytics-framework).
* [Konfigurieren Sie das Adobe Analytics-Framework, um Ad-hoc-Linktracking zu aktivieren](#enabling-ad-hoc-link-tracking).
* [Konfigurieren Sie die Link-Überwachung für eine Textkomponente](#configuring-link-tracking-for-a-text-component).

### Aktiveren der Ad-hoc-Hyperlink-Überwachung {#enabling-ad-hoc-link-tracking}

Konfigurieren Sie das Adobe Analytics-Framework, um die Ad-hoc-Hyperlink-Überwachung zu aktivieren.

1. Öffnen Sie das Adobe Analytics-Framework und erweitern Sie den Abschnitt **Konfiguration der Link-Überwachung**.

1. Aktivieren Sie **Ad-hoc-Linktracking**.

   >[!NOTE]
   >
   >Nicht alle Benutzertypen haben Zugriff auf dieses Kontrollkästchen.  Wenden Sie sich an Ihre Site-Administratorin bzw. Ihren Site-Administrator, wenn Sie Zugriff benötigen.

>[!NOTE]
>
>Die XSS Antisamy-Konfiguration befindet sich jetzt in SLING unter dem Pfad **/libs/sling/xss.config.xml** und die folgenden Regeln müssen zu Ad-hoc hinzugefügt werden, damit die Verknüpfung funktioniert:

#### Anker-Tag-Regelerweiterung {#anchor-tag-rule-extension}

```xml
<attribute name="onclick">
    <literal-list>
        <literal value="CQ_Analytics.Sitecatalyst.customTrack(this)"/>
    </literal-list>
</attribute>
<attribute name="adhocenable">
    <literal-list>
        <literal value="true"/>
        <literal value="false"/>
    </literal-list>
</attribute>
<attribute name="adhocevents">
    <regexp-list>
        <regexp name="anything"/>
    </regexp-list>
</attribute>
<attribute name="adhocevars">
    <regexp-list>
        <regexp name="anything"/>
    </regexp-list>
</attribute>
```

### Konfigurieren von Linktracking für eine Textkomponente {#configuring-link-tracking-for-a-text-component}

Um die Ad-hoc-Link-Überwachung für **Textkomponenten** konfigurieren zu können, müssen die folgenden Konfigurationen bereits implementiert worden sein:

* Das [Adobe Analytics-Framework ist zur Aktivierung von Ad-hoc-Linktracking konfiguriert](#enabling-ad-hoc-link-tracking).
* Die [Seite, die die **Textkomponente** enthält, ist mit dem Framework verknüpft](/help/sites-administering/adobeanalytics-connect.md#associating-a-page-with-a-adobe-analytics-framework).

Gehen Sie wie folgt vor, um die Link-Überwachung für eine **Textkomponente** zu konfigurieren:

1. Öffnen Sie die Seite im Bearbeitungsmodus und bearbeiten Sie die **Textkomponente**.

1. Wählen Sie den als Hypertext zu verwendenden Text aus und klicken Sie auf die Schaltfläche „Hyperlink“.

   ![Link-Symbol](do-not-localize/chlimage_1.png)

1. Fügen Sie die Ziel-URL dem Feld „Verknüpfung zu“ hinzu und erweitern Sie dann den Bereich für die Link-Verfolgung.

   >[!NOTE]
   >
   >„Tracking benutzerdefinierter Links“ erscheint als separate Aktion neben der Aktion „Verknüpfen“/„Verknüpfung aufheben“ (Analytics-Symbol).
   >
   >Die Option wird nur aktiviert, wenn Sie einen gültigen Link im RTE ausgewählt haben.

   ![Aktivieren von Linktracking](assets/aa-17.png)

1. Aktivieren Sie **Tracking benutzerdefinierter Links**, um die Konfiguration der Link-Überwachung des Adobe Analytics-Frameworks außer Kraft zu setzen und die Link-Überwachung für den aktuellen Link zu aktivieren.

1. (Optional) Zum Nachverfolgen von Ereignissen mit dem Link-Klick fügen Sie dem Feld **Adobe Analytics-Variablen einschließen** Adobe Analytics-Ereignisnamen hinzu. Trennen Sie mehrere Ereignisnamen durch Kommas, z. B.

   `event1, event22`.

1. (Optional) Zum Nachverfolgen von Variablendaten mit dem Link-Klick fügen Sie dem Feld **Adobe Analytics-Variablen einschließen** Adobe Analytics-Variablen hinzu. Verwenden Sie eines der folgenden Formate:

   * *`<Variable-name>`*: *`<Dynamic Value>`*
   * *`<Variable-name>`*: *`'CONSTANT'`*

   Beispiele für das jeweilige Format:

   * `eVar10:pagedata.title`
   * `prop1: 'Aubergine'`

   Trennen Sie mehrere Werte durch Kommas.

1. Klicken Sie auf **OK**.
