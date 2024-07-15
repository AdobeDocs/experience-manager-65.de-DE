---
title: Analytics-Konfiguration für Communities-Funktionen
description: Erfahren Sie, wie Sie Adobe Analytics für AEM Communities so konfigurieren, dass bei der Interaktion eines Mitglieds mit unterstützten Communities-Funktionen Ereignisse an Adobe Analytics gesendet werden.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 7d54928b-6512-4da9-a209-eb4488bf2b64
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '2658'
ht-degree: 2%

---

# Analytics-Konfiguration für Communities-Funktionen {#analytics-configuration-for-communities-features}

## Überblick {#overview}

Adobe Analytics und Adobe Experience Manager (AEM) sind beide Lösungen von Adobe Experience Cloud.

Adobe Analytics kann für AEM Communities so konfiguriert werden, dass bei der Interaktion eines Mitglieds mit unterstützten Communities-Funktionen Ereignisse an Adobe Analytics gesendet werden, aus denen Berichte generiert werden.

Auf der Community-Site können Administratoren beispielsweise verschiedene Berichte zur Videowiedergabe sehen.

Außerdem ist die Analyse erforderlich für:

* In der Publish-Umgebung:

   * Berichte zu Community [Trends](/help/communities/trends.md)
   * Ermöglicht Besuchern der Site die Sortierung nach &quot;am häufigsten angesehen&quot;, &quot;am aktivsten&quot;, &quot;am beliebtesten&quot;
   * Anzeigen von Zählungen in Listen für benutzergenerierte Inhalte

* In der Autorenumgebung:

   * Anzeige der Beitragsdaten in der Verwaltungskonsole der [Mitglieder} (Ansichten, Beiträge, folgt, &quot;Gefällt mir&quot;-Klicks)](/help/communities/members.md)
   * Trendzusammenfassung, Video Heartbeat und Videogerät für Aktivierungsressource [Berichte](/help/communities/reports.md)

Zu den unterstützten Communities-Funktionen gehören:

* [Forum](/help/communities/forum.md)
* [Fragen und Antworten](/help/communities/working-with-qna.md)
* [Blog](/help/communities/blog-feature.md)
* [Dateibibliothek](/help/communities/file-library.md)
* [Kalender](/help/communities/calendar.md)

In diesem Abschnitt der Dokumentation wird beschrieben, wie Sie eine Analytics Report Suite mit Communities-Funktionen verbinden. Die grundlegenden Schritte sind:

1. [Replizieren Sie den Verschlüsselungsschlüssel](#replicate-the-crypto-key), damit Sie sicherstellen können, dass Verschlüsselung/Entschlüsselung auf allen AEM Instanzen korrekt ausgeführt wird.
1. Vorbereiten einer Adobe Analytics [Report Suite](#adobe-analytics-report-suite-for-video-reporting)
1. Erstellen eines AEM Analytics [Cloud-Service](#aem-analytics-cloud-service-configuration) und [Framework](#aem-analytics-framework-configuration)

1. [ Analytics aktivieren](#enable-analytics-for-a-community-site) für eine Community-Site
1. [**Überprüfen**](#verify-analytics-to-aem-variable-mapping) Analytics auf AEM Variablenzuordnung
1. Identifizieren von [primärem Herausgeber](#primary-publisher)
1. [Publish](#publish-community-site-and-analytics-cloud-service) die Community-Site
1. Konfigurieren des [Imports von Berichtsdaten](#obtaining-reports-from-analytics) aus Adobe Analytics auf die Community-Site

## Voraussetzungen {#prerequisites}

Um die Funktionen von Analytics for Communities zu konfigurieren, müssen Sie sich an Ihren Kundenbetreuer wenden, um ein Adobe Analytics-Konto und eine [Report Suite](#adobe-analytics-report-suite-for-video-reporting) einzurichten. Nach der Feststellung sollten folgende Informationen verfügbar sein:

* **Firmenname**

  Das mit dem Adobe Analytics-Konto verknüpfte Unternehmen.

* **Benutzername**

  Der Anmeldename des Benutzers, der zur Verwaltung des Analytics-Kontos berechtigt ist
(sollte Zugriffsberechtigungen für Webdienste enthalten).

* **Kennwort**

  Das Anmeldekennwort für den autorisierten Benutzer.

* **Analytics Data Center**

  Die URL des Analytics-Rechenzentrums für das Konto.

* **Report Suite**

  Der Name der zu verwendenden Analytics Report Suite.

## Adobe Analytics Report Suite für Videoberichte {#adobe-analytics-report-suite-for-video-reporting}

Mithilfe des Adobe Experience Clouds [Report Suite Manager](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/c-new-report-suite/new-report-suite.html?lang=de) können Analytics-Report Suites so konfiguriert werden, dass eine Community-Site Berichte für Communities-Funktionen bereitstellen kann.

Durch Anmeldung bei [Adobe Experience Cloud](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=de) mit [Firmenname und Benutzername](/help/communities/analytics.md#prerequisites) können Sie eine neue oder vorhandene Report Suite so konfigurieren, dass sie Folgendes aufweist:

* [11 Konversionsvariablen](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/conversion-variables/conversion-var-admin.html?lang=de) (eVars)

   * **`evar1`** bis **`evar11`** aktiviert

   * Kann vorhandene eVars wiederverwenden (umbenennen) oder für Communities-Funktionen verwenden

* [7 Erfolgsereignisse](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/conversion-variables/success-events/success-event.html?lang=de) (Ereignisse)

   * **`event1`** bis **`event7`** aktiviert

   * type **`Counter`**

      * not **`Counter (no subrelations)`**

   * Kann vorhandene Ereignisse wiederverwenden (umbenennen) oder Ereignisse erstellen, die für Communities-Funktionen verwendet werden können

* [Videomanagement](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=de)

   * Videoberichterkonsole

      * `Video Core` aktivieren
      * Wählen Sie „Speichern“ aus

   * Video Core Measurement Console

      * Klicken Sie auf `Use Solution Variables`
      * Wählen Sie „Speichern“ aus

Bei Verwendung einer **neuen Report Suite** darf eine neue Report Suite nur über 4 eVars und 6 Ereignisvariablen verfügen, während für Communities 11 eVars und 7 Ereignisvariablen erforderlich sind.

Bei Verwendung einer **vorhandenen Report Suite** kann es erforderlich sein, die Variablenzuordnung zu ändern [, bevor das Analytics-Framework für eine Community-Site aktiviert wird.](#modifying-analytics-variable-mapping)

Wenden Sie sich an Ihren Kundenbetreuer, wenn Sie Fragen zu den Communities-Variablen haben.

>[!CAUTION]
>
>**Bei Verwendung einer vorhandenen Report Suite, die bereits Variablen innerhalb von** verwendet
>
>* **`evar1`** bis **`evar11`**
>
>* **`event1`** bis **`event7`**
>
>**Bevor die Community-Site veröffentlicht wird,** muss die bereits vorhandene Zuordnung wiederhergestellt werden, indem die AEM Variablen verschoben werden, die automatisch Analytics-Variablen zugeordnet wurden, wenn Analytics für eine Community-Site aktiviert war.
>
>Informationen zum Wiederherstellen der bereits vorhandenen Zuordnung und Verschieben AEM Variablen in andere Analytics-Variablen finden Sie im Abschnitt zum [Ändern der Analytics-Variablenzuordnung](#modifying-analytics-variable-mapping).
>
>Andernfalls kann es zu nicht wiederherstellbaren Datenverlusten kommen.

### Video Heartbeat Analytics {#video-heartbeat-analytics}

Wenn Video Heartbeat Analytics lizenziert ist, wird ein `Marketing Cloud Org Id` zugewiesen.

So aktivieren Sie die Video Heartbeat-Berichterstellung nach [Konfiguration der Analytics Report Suite für Videoberichte](#adobe-analytics-report-suite-for-video-reporting):

* Erstellen eines [Analytics Cloud-Dienstes](#aem-analytics-cloud-service-configuration)
* Aktivieren Sie [Analytics für eine Community-Site](#enable-analytics-for-a-community-site)
* Verknüpfen Sie die `Marketing Cloud Org Id` mit der Community-Site.

Der `Marketing Cloud Org Id` kann zum Zeitpunkt der [Erstellung der Community-Site](/help/communities/sites-console.md) oder neuer eingegeben werden, indem [die Eigenschaften der Community-Site geändert](/help/communities/sites-console.md#modifying-site-properties) werden.

![marketing-org-id](assets/marketing-org-id.png)

Wenn Video Heartbeat Analytics aktiviert ist, instanziiert der JavaScript (JS)-Code für den Videoplayer den Video Heartbeat-Bibliothekscode (auch in JS). Der Code verarbeitet alle Logiken zum Senden von Videostatusaktualisierungen an die Analytics-Video-Tracking-Server alle 10 Sekunden (nicht konfigurierbar). Schließlich wird ein kumulativer Bericht der Videositzung an die wichtigsten Analytics-Server gesendet.

Wenn dies nicht aktiviert ist, wird der Video Heartbeat-Code nie instanziiert und nur das Video-Fortschritts- und das Tracking der Wiederaufnahmeposition wird zur Berichterstellung in SRP persistiert.

## Analytics Cloud-Dienstkonfiguration AEM {#aem-analytics-cloud-service-configuration}

So erstellen Sie eine Analytics-Integration, die Adobe Analytics mit der AEM Community-Site integriert, mithilfe der standardmäßigen Benutzeroberfläche in der Autoreninstanz:

* Von der globalen Navigation: **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Cloud Service]**
* Scrollen Sie nach unten zu **[!UICONTROL Adobe Analytics]**
* Wählen Sie **[!UICONTROL Jetzt konfigurieren]** oder **[!UICONTROL Konfigurationen anzeigen]** aus.

![cloud-config](assets/cloud-config1.png)

### Dialogfeld &quot;Konfiguration erstellen&quot; {#create-configuration-dialog}

* Wählen Sie das Symbol `[+]` neben **[!UICONTROL Verfügbare Konfigurationen]** aus, damit Sie eine Konfiguration erstellen können.

Im Dialogfeld &quot;Konfiguration erstellen&quot;geben die eingegebenen Werte die Konfiguration an.

![create-cloud-config](assets/cloud-config2.png)

* **Titel**

  (Erforderlich) Ein Anzeigetitel für die Konfiguration.
Geben Sie beispielsweise *Community Analytics* ein.

* **Name**

  (Optional) Wenn kein Name angegeben ist, wird standardmäßig ein gültiger Knotenname verwendet, der aus dem Titel abgeleitet wurde.
Geben Sie beispielsweise *communities* ein.

* **Vorlage**

  Klicken Sie auf `Adobe Analytics Configuration`

* Wählen Sie **Erstellen** aus

   * Startet die Konfigurationsseite und öffnet das Dialogfeld `Analytics Settings`

### Dialogfeld &quot;Analytics-Einstellungen&quot; {#analytics-settings-dialog}

Die erste Erstellung einer neuen Analytics-Konfiguration führt zur Anzeige der Konfiguration und eines neuen Dialogfelds für die Eingabe der Analytics-Einstellungen. Für dieses Dialogfeld sind die vom Kundenbetreuer erhaltenen [erforderlichen Kontoinformationen](#prerequisites) erforderlich.

![analytics-settings](assets/analytics-settings.png)

* **Firma**

  Das mit dem Adobe Analytics-Konto verknüpfte Unternehmen.

* **Benutzername**

  Der Anmeldename des Benutzers, der zur Verwaltung des Analytics-Kontos berechtigt ist.

* **Kennwort**

  Das Anmeldekennwort für den autorisierten Benutzer.

* **Rechenzentrum**

  Wählen Sie das Analytics-Rechenzentrum aus, in dem die Report Suite gehostet wird.

* **Fügen Sie der Seite** kein Tracking-Tag hinzu

  Behalten Sie die Standardeinstellung bei (deaktiviert).

* **AppMeasurement** verwenden

  Behalten Sie die Standardeinstellung bei (deaktiviert).

* **Importieren Sie keine Seitenimpressionen nächtlich (Autor)**

  Behalten Sie die Standardeinstellung bei (deaktiviert).

* **Importieren Sie keine Seitenimpressionen nächtlich (veröffentlichen)**

  Behalten Sie die Standardeinstellung bei (deaktiviert).

Speichern der Einstellungen:

* Wählen Sie **Verbindung zu Analytics herstellen**

   * Wenn dies nicht erfolgreich war,

      * Vergewissern Sie sich, dass Einträge keine führenden Leerzeichen enthalten.
      * Testen Sie ein anderes Rechenzentrum.

* Wählen Sie **OK** aus.

  ![analytics-settings](assets/analytics-settings1.png)

### Framework erstellen {#create-framework}

Nach erfolgreicher Konfiguration der Basisverbindung mit Adobe Analytics muss ein Framework für die Community-Site erstellt oder bearbeitet werden. Der Zweck des Frameworks besteht darin, Communities-Funktionsvariablen (AEM) Analytics-Variablen (Report Suite) zuzuordnen.

* Wählen Sie das Symbol `[+]` neben **[!UICONTROL Verfügbare Frameworks]** aus, damit Sie ein Framework erstellen können.

  ![analytics-framework](assets/analytics-framework.png)

* **Titel**

  (Erforderlich) Ein Anzeigetitel für das Framework
Geben Sie beispielsweise *Community-Framework* ein.

* **Name**

  (Optional) Wenn kein Name angegeben ist, wird standardmäßig ein gültiger Knotenname verwendet, der aus dem Titel abgeleitet wurde.
Geben Sie beispielsweise *communities* ein.

* *Vorlage*

  Wählen Sie `Adobe Analytics Framework`.

* Wählen Sie **Erstellen** aus.

Durch Erstellen des Analytics-Frameworks wird das Framework zur Konfiguration geöffnet.

## AEM Analytics-Framework-Konfiguration {#aem-analytics-framework-configuration}

Das Framework dient der Zuordnung AEM Variablen zu Analytics-Variablen (eVars und Ereignisse). Die für die Zuordnung verfügbaren Analytics-Variablen sind [in der Report Suite definiert](#adobe-analytics-report-suite-for-video-reporting).

![analytics-framework](assets/analytics-framework1.png)

### Report Suite auswählen {#select-report-suite}

Wählen Sie die Report Suite aus, die für Videoberichte eingerichtet wurde.

Wenn eine Report Suite noch nicht erstellt oder nicht ordnungsgemäß eingerichtet wurde, lesen Sie den vorherigen Abschnitt:
[Adobe Analytics Report Suite für Videoberichte](#adobe-analytics-report-suite-for-video-reporting)

Die Sidekick ist nicht erforderlich und kann so minimiert werden, dass sie den Zugriff auf die Report Suites-Einstellungen nicht behindert.

#### Dialogfeld &quot;Report Suites&quot;vor und nach der Auswahl von &quot;Element hinzufügen&quot; {#report-suites-dialog-before-and-after-selecting-add-item}

![Report-Suite](assets/report-suite.png)

1. Wählen Sie **Element hinzufügen +** aus.

   Es werden zwei Dropdown-Felder angezeigt.

1. Wählen Sie eine `Report suite.`

   Die mit dem Unternehmenskonto verknüpften Report Suites stehen zur Auswahl zur Verfügung.

1. Wählen Sie **Ja** im sich öffnenden Dialogfeld aus:

   ```
   Load default server settings?
    Do you want to load the default server settings and overwrite current values in the Server section?
   ```

1. Wählen Sie eine `Run Mode`.

1. Wählen Sie **Veröffentlichen** aus.

![analytics-framework2](assets/analytics-framework2.png)

Der Analytics-Cloud-Service und das -Framework sind jetzt abgeschlossen. Die Zuordnungen werden definiert, nachdem eine Community-Site mit diesem Analytics-Dienst erstellt wurde.

## Aktivieren von Analytics für eine Community-Site {#enable-analytics-for-a-community-site}

### Aktivieren für neue Community-Site {#enable-for-new-community-site}

So fügen Sie den Analytics Cloud-Dienst hinzu, während Sie [eine Community-Site erstellen](/help/communities/sites-console.md):

* In Schritt 3 unter der Registerkarte [ANALYTICS](/help/communities/sites-console.md#analytics):
   * Aktivieren Sie das Kontrollkästchen **Analytics aktivieren** .
   * Wählen Sie das Framework aus der Dropdown-Liste aus.

* Kehren Sie optional zur Analytics-Framework-Konfiguration zurück, um die Variablenzuordnungen anzupassen.

### Aktivieren für bestehende Community-Site {#enable-for-existing-community-site}

So fügen Sie den Analytics Cloud-Dienst einer [vorhandenen Community-Site](/help/communities/sites-console.md#modifying-site-properties) hinzu:

* Navigieren Sie zur Konsole **Communities > Sites** .
* Wählen Sie das Symbol Site bearbeiten der Community-Site aus.
* Wählen Sie EINSTELLUNGEN aus.
* Im Abschnitt Analytics :
   * Aktivieren Sie das Kontrollkästchen **Analytics aktivieren** .
   * Wählen Sie das Framework aus der Dropdown-Liste aus.

* Kehren Sie optional zur Analytics-Framework-Konfiguration zurück, um die Variablenzuordnungen anzupassen.

### Aktivieren für benutzerdefinierte Sites {#enable-for-customized-sites}

Damit das Analytics-Tracking und -Import für eine Community-Site ordnungsgemäß funktionieren, muss ein Seitenelement mit den Attributen `scf-js-site-title` class und href vorhanden sein. Auf der Seite sollte nur ein solches Element vorhanden sein, wie es beispielsweise in einem unveränderten `sitepage.hbs`-Skript für eine Community-Site der Fall ist. Der Wert von `siteUrl` wird extrahiert und als *Site-Pfad* an Adobe Analytics gesendet.

```xml
# present in default sitepage.hbs
# only one scf-js-site-title class should be included
# this example sets it to be hidden as it serves no visual purpose
<div
    class="navbar-brand scf-js-site-title"
    href="{{siteUrl}}.html"
    style="visibility: hidden;"
>
</div>
```

Stellen Sie bei einer **angepassten Community-Site**, die das `sitepage.hbs`-Skript überlagert, sicher, dass das Element vorhanden ist. Die Variable `siteUrl` wird festgelegt, wenn sie auf dem Server gerendert wird, bevor sie an den Client gesendet wird.

Für eine **generische AEM Site**, die Communities-Komponenten enthält, aber nicht mit dem [Website-Erstellungsassistenten](/help/communities/sites-console.md) erstellt wird, muss das Element hinzugefügt werden. Der Wert von href sollte der Pfad zur Site sein. Wenn der Sitepfad beispielsweise `/content/my/company/en` lautet, verwenden Sie:

```xml
<div
    class="navbar-brand scf-js-site-title"
    href="/content/my/company/en.html"
    style="visibility: hidden;"
>
</div>
```

## Funktionen von Analytics for Communities {#analytics-for-communities-features}

Analytics wird automatisch für verschiedene Communities-Funktionen verwendet.

Die [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md), `AEM Communities Analytics Component Configuration` der Autorenumgebung enthält eine Liste der Komponenten, die für Analytics instrumentiert wurden. Die automatische Zuordnung von Variablen wird durch die aufgeführten Komponenten bestimmt.

Wenn neue benutzerdefinierte Komponenten erstellt werden, die für Analytics instrumentiert werden, sollten sie dieser Liste der konfigurierten Komponenten hinzugefügt werden.

### Komponentenkonfiguration {#component-configuration}

![component-configuration1](assets/component-configuration1.png)

>[!NOTE]
>
>Die Journalkomponenten werden zur Implementierung der Blog-Funktion verwendet.

### Analytics AEM Variablen zugeordnet {#mapped-analytics-to-aem-variables}

Nachdem die Community-Site gespeichert wurde und Analytics aktiviert ist und das Cloud-Konfigurations-Framework ausgewählt ist, werden die AEM Variablen automatisch den Analytics-eVars und -Ereignissen zugeordnet. Er beginnt mit evar1 bzw. event1 und wird um 1 inkrementiert.

Wenn Sie eine vorhandene Report Suite verwenden, die eine der Variablen in evar1 bis evar11 und event1 bis event7 zugeordnet hat, müssen Sie die AEM Variablen ](#modifying-analytics-variable-mapping) neu zuordnen und die ursprüngliche Zuordnung wiederherstellen.[

Im Folgenden finden Sie ein Beispiel für standardmäßige Zuordnungen:

![map-analytics](assets/map-analytics1.png)

#### Zuordnung der mit jedem Ereignis gesendeten eVars {#map-of-evars-sent-with-each-event}

<table>
 <tbody>
  <tr>
   <td><strong> </strong></td>
   <td><strong>Aktivierungstyp<br /> Resource<br /></strong></td>
   <td><strong>Site<br /> Titel</strong></td>
   <td><strong>Funktion<br /> Typ</strong></td>
   <td><strong>Gruppe<br /> Titel</strong></td>
   <td><strong>Group<br /> path</strong></td>
   <td><strong>UGC<br /> Type</strong></td>
   <td><strong>UGC<br /> Title</strong></td>
   <td><strong>Benutzer<br /> (Mitglied)</strong></td>
   <td><strong>UGC<br />-Pfad</strong></td>
   <td><strong>Site<br />-Pfad</strong></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><strong>eVar1</strong></td>
   <td><strong>eVar2</strong></td>
   <td><strong>eVar3</strong></td>
   <td><strong>eVar4</strong></td>
   <td><strong>eVar5</strong></td>
   <td><strong>eVar6</strong></td>
   <td><strong>eVar7</strong></td>
   <td><strong>eVar8</strong></td>
   <td><strong>eVar9</strong></td>
   <td><strong>eVar10</strong></td>
  </tr>
  <tr>
   <td><strong>event1<br /> Resource Play</strong></td>
   <td><em>a)</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>i)</em></td>
   <td><em>-</em></td>
  </tr>
  <tr>
   <td><strong>event2<br /> SCFView</strong></td>
   <td><em>a)</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>d)</em></td>
   <td><em>e)</em></td>
   <td><em>f)</em></td>
   <td><em>g)</em></td>
   <td><em>h)</em></td>
   <td><em>i)</em></td>
   <td><em>j)</em></td>
  </tr>
  <tr>
   <td><strong>event3<br /> SCFCreate (Post)</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>d)</em></td>
   <td><em>e)</em></td>
   <td><em>f)</em></td>
   <td><em>g)</em></td>
   <td><em>h)</em></td>
   <td><em>i)</em></td>
   <td><em>j)</em></td>
  </tr>
  <tr>
   <td><strong>event4<br /> SCFFollow</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>d)</em></td>
   <td><em>e)</em></td>
   <td><em>f)</em></td>
   <td><em>g)</em></td>
   <td><em>h)</em></td>
   <td><em>i)</em></td>
   <td><em>j)</em></td>
  </tr>
  <tr>
   <td><strong>event5<br /> SCFVoteUp</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>d)</em></td>
   <td><em>e)</em></td>
   <td><em>f)</em></td>
   <td><em>g)</em></td>
   <td><em>h)</em></td>
   <td><em>i)</em></td>
   <td><em>j)</em></td>
  </tr>
  <tr>
   <td><strong>event6<br /> SCFVoteDown</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>d)</em></td>
   <td><em>e)</em></td>
   <td><em>f)</em></td>
   <td><em>g)</em></td>
   <td><em>h)</em></td>
   <td><em>i)</em></td>
   <td><em>j)</em></td>
  </tr>
  <tr>
   <td><strong>event7<br /> SCFRate</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>d)</em></td>
   <td><em>e)</em></td>
   <td><em>f)</em></td>
   <td><em>g)</em></td>
   <td><em>h)</em></td>
   <td><em>i)</em></td>
   <td><em>j)</em></td>
  </tr>
 </tbody>
</table>

**Beispiele für eVar :**

* *[MIME type](https://www.iana.org/assignments/media-types/media-types.xhtml)*: video/mp4
* *[Community-Site-Titel](/help/communities/sites-console.md#step13asitetemplate)*: Geometrixx Communities
* *[Community-Funktionsname](/help/communities/functions.md)*: Forum
* *[Community-Gruppenname](/help/communities/creating-groups.md#creating-a-new-group)*: Wandern
* *Pfad zum Community-Gruppeninhalt*: `/content/sites/<site name>/en/groups/hiking`
* *[UGC component resourceType](/help/communities/essentials.md)*: `social/forum/components/hbs/topic`
* *UGC-Komponententitel*: Wanderthemen
* *login (authorizableId)*: `aaron.mcdonald@mailinator.com`
* *SRP-Pfad zu UGC*: `/content/usergenerated/asi/.../forum/jmtz-topic3`
oder *Pfad der Komponente, der folgen soll*: `/content/sites/<site name>/en/jcr:content/content/primary/forum`

* *Pfad zum Community-Site-Inhalt*: `/content/sites/<site name>/en`

### Ändern der Analytics-Variablenzuordnung {#modifying-analytics-variable-mapping}

Die Zuordnung von Analytics-eVars und -Ereignissen zu AEM Variablen ist in der Framework-Konfiguration sichtbar, nachdem Analytics für eine Community-Site aktiviert wurde.

Nachdem Analytics aktiviert wurde und bevor die Community-Site veröffentlicht wird, kann die Zuordnung im Framework geändert werden. Ziehen Sie einfach die gewünschte Analytics-eVar oder das gewünschte Ereignis aus der linken Leiste und legen Sie sie in der Zuordnungstabelle in der entsprechenden Zeile ab.

Um doppelte Zuordnungen zu vermeiden, müssen Sie die ersetzte Analytics-eVar oder das ersetzte Analytics-Ereignis aus der Zeile entfernen, indem Sie den Mauszeiger darüber bewegen und das &quot;X&quot;auswählen, das rechts neben dem Analytics-Variablenelement angezeigt wird.

Wenn Community-eVars und -Ereignisse Zuordnungen überschreiben, die bereits in der Report Suite vorhanden waren, weisen Sie zur Vermeidung von Datenverlust die AEM Variablen für Communities-Funktionen anderen Analytics-eVars oder -Ereignissen zu und stellen Sie die ursprünglichen Zuordnungen wieder her.

>[!CAUTION]
>
>Es ist wichtig, dass Sie eine Verknüpfung vornehmen, bevor die Community-Site [veröffentlicht](#publishing-the-community-site) ist und Analytics aktiviert ist. Andernfalls besteht das Risiko eines Datenverlusts.

#### Beispiel Schritt 1: Ziehen von Analytics eVar14 in eine Zuordnungstabelle {#example-step-dragging-analytics-evar-into-mapping-table}

![analytics-mapping-evar](assets/analytics-mapping-evar.png)

#### Beispiel Schritt 2: Auswählen von &quot;x&quot;zum Entfernen der ersetzten evar11 {#example-step-selecting-x-to-remove-replaced-evar}

![analytics-mapping-evar1](assets/analytics-mapping-evar1.png)

#### Beispiel Schritt 3: AEM var eventdata.siteId wurde der Analytics-eVar14 zugeordnet {#example-step-aem-var-eventdata-siteid-remapped-to-analytics-evar}

![analytics-mapping-evar2](assets/analytics-mapping-evar2.png)

## Veröffentlichen der Community-Site {#publishing-the-community-site}

### Überprüfen der Zuordnung von Analytics zu AEM Variablen {#verify-analytics-to-aem-variable-mapping}

Es ist ratsam, die Variablenzuordnung zu überprüfen, bevor Sie die Community-Site veröffentlichen, auf der auch der Analytics Cloud-Dienst und das Framework veröffentlicht werden.

Siehe Abschnitte:

* [Analytics AEM Variablen zugeordnet](#mapped-analytics-to-aem-variables)
* [Ändern der Analytics-Variablenzuordnung](#modifying-analytics-variable-mapping)

>[!CAUTION]
>
>**Bei Verwendung einer vorhandenen Report Suite, die bereits Variablen innerhalb von** verwendet
>
>* **`evar1`** bis **`evar11`**
>
>* **`event1`** bis **`event7`**
>
>**Stellen Sie dann vor der Veröffentlichung der Community-Site** die bereits vorhandene Zuordnung wieder her. Verschieben Sie Communities AEM Variablen, die automatisch zugeordnet wurden (wenn Analytics für die Community-Site aktiviert war), zu anderen Analytics-Variablen. Diese Neukodifizierung sollte für alle Communities-Komponenten einheitlich sein.
>
>Andernfalls kann es zu nicht wiederherstellbaren Datenverlusten kommen.

### Primärer Herausgeber {#primary-publisher}

Wenn es sich bei der ausgewählten Bereitstellung um eine [Veröffentlichungsfarm](/help/communities/topologies.md#tarmk-publish-farm) handelt, muss eine AEM Veröffentlichungsinstanz als primärer Herausgeber für die Abfrage von Adobe Analytics für Berichtsdaten identifiziert werden, die in [SRP](/help/communities/working-with-srp.md) geschrieben werden sollen.

Standardmäßig identifiziert die OSGi-Konfiguration `AEM Communities Publisher Configuration` die Veröffentlichungsinstanz als primären Herausgeber, sodass sich alle Veröffentlichungsinstanzen in einer Veröffentlichungsfarm selbst als primär identifizieren.

Daher müssen Sie die Konfiguration in allen sekundären Veröffentlichungsinstanzen bearbeiten, um das Kontrollkästchen **Primärer Herausgeber** zu deaktivieren.

Spezifische Anweisungen finden Sie im Abschnitt für den primären Herausgeber von [Communities bereitstellen](/help/communities/deploy-communities.md#primary-publisher).

>[!CAUTION]
>
>Es ist wichtig, dass der primäre Herausgeber so konfiguriert ist, dass die Abfrage von mehreren Veröffentlichungsinstanzen verhindert wird.

### Replizieren des Crypto-Schlüssels {#replicate-the-crypto-key}

Die Adobe Analytics-Anmeldeinformationen werden verschlüsselt. Um die Replikation oder Übertragung verschlüsselter Analytics-Anmeldeinformationen zwischen Autor und Herausgebern zu erleichtern, müssen alle AEM Instanzen denselben Primärverschlüsselungsschlüssel verwenden.

Befolgen Sie dazu die Anweisungen unter [Replizieren des Crypto-Schlüssels](/help/communities/deploy-communities.md#replicate-the-crypto-key).

### Publish-Community-Site und Analytics Cloud-Dienst {#publish-community-site-and-analytics-cloud-service}

Nachdem der Analytics Cloud-Dienst für eine Community-Site aktiviert wurde und bei Bedarf die [Zuordnung von Analytics zu AEM Variablen angepasst wurde](#mapped-analytics-to-aem-variables), replizieren Sie die Konfiguration in der Veröffentlichungsumgebung durch [ (erneutes Veröffentlichen der Community-Site](/help/communities/sites-console.md#publishing-the-site).

## Abrufen von Berichten aus Analytics {#obtaining-reports-from-analytics}

### Berichtverwaltung {#report-management}

Die [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) des Autors und des primären Herausgebers `AEM Communities Analytics Report Management` wird zur Abfrage von Analytics verwendet.

Auf der Autoreninstanz werden die Abfragen für Echtzeitberichte erstellt.

Beim primären Herausgeber werden die Abfragen verwendet, um Informationen bei der Vorbereitung des Analytics-Datenimports durch Report Importer bereitzustellen.

Das Abfrageintervall beträgt standardmäßig 10 Sekunden.

### Report Importer {#report-importer}

Sobald eine für Analytics aktivierte Community-Site veröffentlicht wurde, kann die [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) des primären Herausgebers `AEM Communities Analytics Report Importer` so konfiguriert werden, dass das standardmäßige Abrufintervall für die Konfigurationen festgelegt wird, die in CRXDE nicht einzeln konfiguriert sind.

Das Abrufintervall steuert die Häufigkeit von Anfragen an Adobe Analytics, damit Daten abgerufen und in [SRP](/help/communities/working-with-srp.md) gespeichert werden.

Wenn die Daten als &quot;Big Data&quot;kategorisiert werden können, kann eine häufigere Abfrage eine große Belastung für die Community-Site verursachen.

Der standardmäßige Abruf **Importintervall** wird auf 12 Stunden festgelegt.

![report-importer](assets/report-importer.png)

### Anpassung von Komponentenberichten {#component-report-customization}

Derzeit werden zur Anpassung der zu verfolgenden Metriken Knoten im Repository erstellt, die Zeiträume definieren, für die ein Bericht zu dieser Metrik erstellt werden soll.

Das Forenthema ist derzeit das einzige Beispiel für diese Anpassung:

* Melden Sie sich beim primären Herausgeber mit Administratorrechten an.
* Gehen Sie zu [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md). Beispiel: [https://localhost:4503/crx/de](https://localhost:4503/crx/de).

* Navigieren Sie unter dem Knoten `jcr:content` des Sprachstamms (z. B. `/content/sites/engage/en/jcr:content`) zur für die Analytics-Berichterstellung konfigurierten Komponente.
Zum Beispiel: **`analytics/reportConfigs/social_forum_components_hbs_topic`**

* Beachten Sie die erstellten Zeiträume:

   * `last30Days`
   * `last90Days`
   * `thisYear`

* Beachten Sie den Knoten `total`.

   * Durch Ändern der Eigenschaft **`interval`** wird das Report Importer-Intervall überschrieben.
   * Der Wert wird in Sekunden angegeben und auf vier Stunden (14400 Sekunden) festgelegt.

![component-report](assets/component-report.png)

## Benutzerdaten in Analytics verwalten {#manage-user-data-in-analytics}

Adobe Analytics bietet APIs, mit denen Sie Benutzerdaten aufrufen, exportieren und löschen können. Weitere Informationen finden Sie unter [Zugriffs- und Löschanfragen einreichen](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/data-governance/an-gdpr-workflow.html?lang=de).

## Ressourcen {#resources}

* Adobe Experience Cloud: [Hilfe und Referenz zu Analytics](https://experienceleague.adobe.com/docs/analytics.html)
* AEM: [Integrieren mit Adobe Analytics](/help/sites-administering/adobeanalytics.md)
* AEM: [Analytics mit externen Anbietern](/help/sites-administering/external-providers.md)
