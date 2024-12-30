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
ht-degree: 4%

---

# Analytics-Konfiguration für Communities-Funktionen {#analytics-configuration-for-communities-features}

## Überblick {#overview}

Adobe Analytics und Adobe Experience Manager (AEM) sind beides Lösungen von Adobe Experience Cloud.

Adobe Analytics kann für AEM Communities konfiguriert werden, sodass bei der Interaktion eines Mitglieds mit unterstützten Communities-Funktionen Ereignisse an Adobe Analytics gesendet werden, aus denen Berichte generiert werden.

Beispielsweise können Admins auf der Community-Website verschiedene Berichte zur Wiedergabe des Videos anzeigen.

Außerdem ist die Analyse für Folgendes erforderlich:

* In der Publish-Umgebung:

   * Berichterstattung über Community [Trends](/help/communities/trends.md)
   * Website-Besuchern ermöglichen, nach „am häufigsten angezeigt“, „am aktivsten“ und „am meisten geliked“ zu sortieren
   * Anzeigen der Anzahl von UGC-Listen (benutzergenerierte Inhalte)

* In der Autorenumgebung:

   * Anzeige von Teilnahmedaten in der [Mitglieder-Management-Konsole](/help/communities/members.md) (Ansichten, Beiträge, Follows, Likes)
   * Trend-Zusammenfassung, Video-Heartbeat und Videogerät für die Aktivierung der Ressource [Berichte](/help/communities/reports.md)

Zu den unterstützten Communities-Funktionen gehören:

* [Forum](/help/communities/forum.md)
* [Fragen und Antworten](/help/communities/working-with-qna.md)
* [Blog](/help/communities/blog-feature.md)
* [Dateibibliothek](/help/communities/file-library.md)
* [Kalender](/help/communities/calendar.md)

In diesem Abschnitt der Dokumentation wird beschrieben, wie Sie eine Analytics Report Suite mit Communities-Funktionen verbinden. Die grundlegenden Schritte sind:

1. [Replizieren Sie den ](#replicate-the-crypto-key), um sicherzustellen, dass die Verschlüsselung/Entschlüsselung auf allen AEM-Instanzen ordnungsgemäß erfolgt.
1. Adobe Analytics ([ Suite) ](#adobe-analytics-report-suite-for-video-reporting)
1. Erstellen eines AEM Analytics [Cloud-Service](#aem-analytics-cloud-service-configuration) und [Frameworks](#aem-analytics-framework-configuration)

1. [Analytics aktivieren](#enable-analytics-for-a-community-site) für eine Community-Site
1. [**Überprüfen**](#verify-analytics-to-aem-variable-mapping) Analytics zur AEM-Variablenzuordnung
1. Identifizieren [primären Herausgebers](#primary-publisher)
1. [Publish](#publish-community-site-and-analytics-cloud-service) Die Community-Site
1. Konfigurieren [Importierens von Berichtsdaten](#obtaining-reports-from-analytics) von Adobe Analytics zur Community-Site

## Voraussetzungen {#prerequisites}

Zum Konfigurieren der Funktionen von Analytics for Communities müssen Sie ein Adobe Analytics-Konto und eine [Report Suite“ ](#adobe-analytics-report-suite-for-video-reporting) Ihrem Kontobeauftragten einrichten. Nach ihrer Festlegung sollten folgende Informationen verfügbar sein:

* **Firmenname**

  Das Unternehmen, das mit dem Adobe Analytics-Konto verknüpft ist.

* **Benutzername**

  Der Anmeldename des Benutzers, der zur Verwaltung des Analytics-Kontos autorisiert ist
(sollte Zugriffsberechtigungen für Webdienste enthalten).

* **Kennwort**

  Das Anmeldekennwort für den autorisierten Benutzer.

* **Analytics-Rechenzentrum**

  Die URL des Analytics-Rechenzentrums für das Konto.

* **Report Suite**

  Der Name der zu verwendenden Analytics Report Suite.

## Adobe Analytics Report Suite für Videoberichte {#adobe-analytics-report-suite-for-video-reporting}

Mithilfe des Adobe Experience Cloud [Report Suite Manager](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/c-new-report-suite/new-report-suite.html?lang=de) können Analytics-Report Suites so konfiguriert werden, dass eine Community-Site für die Bereitstellung von Berichten für Communities-Funktionen aktiviert werden kann.

Durch die Anmeldung bei [Adobe Experience Cloud](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=de) mit [Firmenname und Benutzername](/help/communities/analytics.md#prerequisites) ist es möglich, eine neue oder vorhandene Report Suite so zu konfigurieren, dass sie Folgendes aufweist:

* [11-Konversionsvariablen](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/conversion-variables/conversion-var-admin.html?lang=de) (eVars)

   * **`evar1`** durch **`evar11`** aktiviert

   * Kann vorhandene eVars umbenennen oder solche erstellen, die für Communities-Funktionen verwendet werden können

* [7 Erfolgsereignisse](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/conversion-variables/success-events/success-event.html?lang=de) (Ereignisse)

   * **`event1`** durch **`event7`** aktiviert

   * type **`Counter`**

      * Nicht **`Counter (no subrelations)`**

   * Kann vorhandene Ereignisse umbenennen oder solche erstellen, die für Communities-Funktionen verwendet werden

* [Video-Management](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=de)

   * Konsole für Videoberichte

      * `Video Core` aktivieren
      * Wählen Sie „Speichern“ aus

   * Video Core-Messkonsole

      * Klicken Sie auf `Use Solution Variables`
      * Wählen Sie „Speichern“ aus

Bei Verwendung einer **neuen Report Suite** darf eine neue Report Suite nur 4 eVars und 6 Ereignisvariablen haben, während 11 eVars und 7 Ereignisvariablen für Communities erforderlich sind.

Bei Verwendung einer **vorhandenen Report Suite** kann es erforderlich sein, die Variablenzuordnung zu [ändern](#modifying-analytics-variable-mapping) bevor das Analytics-Framework für eine Community-Site aktiviert wird.

Wenden Sie sich an Ihren Kundenbetreuer, wenn Sie Bedenken bezüglich der für Communities reservierten Variablen haben.

>[!CAUTION]
>
>**Bei Verwendung einer vorhandenen Report Suite, die bereits Variablen innerhalb von verwendet**
>
>* **`evar1`** bis **`evar11`**
>
>* **`event1`** bis **`event7`**
>
>**Bevor die Community-Site veröffentlicht wird,** Sie die bereits vorhandene Zuordnung wiederherstellen, indem Sie die AEM-Variablen verschieben, die automatisch Analytics-Variablen zugeordnet wurden, wenn Analytics für eine Community-Site aktiviert war.
>
>Informationen zum Wiederherstellen der bereits vorhandenen Zuordnung und Verschieben von AEM-Variablen in andere Analytics-Variablen finden Sie im Abschnitt [Ändern der Analytics-Variablenzuordnung](#modifying-analytics-variable-mapping).
>
>Andernfalls kann es zu einem nicht wiederherstellbaren Datenverlust kommen.

### Video Heartbeat Analytics {#video-heartbeat-analytics}

Wenn Video Heartbeat Analytics lizenziert ist, wird ein `Marketing Cloud Org Id` zugewiesen.

So aktivieren Sie Video Heartbeat-Berichte nach [Konfigurieren der Analytics Report Suite für Videoberichte](#adobe-analytics-report-suite-for-video-reporting):

* Erstellen Sie einen [Analytics Cloud-Service](#aem-analytics-cloud-service-configuration)
* Aktivieren [Analytics für eine Community-Site](#enable-analytics-for-a-community-site)
* Verknüpfen der `Marketing Cloud Org Id` mit der Community-Site

Die `Marketing Cloud Org Id` kann zum Zeitpunkt der Erstellung der [-Community-Site ](/help/communities/sites-console.md) später durch [ der Eigenschaften ](/help/communities/sites-console.md#modifying-site-properties) Community-Site eingegeben werden.

![marketing-org-id](assets/marketing-org-id.png)

Wenn Video Heartbeat Analytics aktiviert ist, instanziiert der JavaScript-Code (JS) für den Video-Player den Video-Heartbeat-Bibliothekscode (auch in JS). Der Code handhabt die gesamte Logik zum Senden von Videostatusaktualisierungen an die Analytics-Videotracking-Server alle 10 Sekunden (nicht konfigurierbar). Schließlich sendet sie einen kumulativen Bericht der Videositzung an die wichtigsten Analytics-Server.

Wenn er nicht aktiviert ist, wird der Video-Heartbeat-Code nie instanziiert und nur der Videofortschritt und das Tracking der Wiederaufnahme-Position werden zum Reporting in SRP beibehalten.

## AEM Analytics Cloud-Dienstkonfiguration {#aem-analytics-cloud-service-configuration}

So erstellen Sie eine Analytics-Integration, die Adobe Analytics mit der AEM-Community-Site integriert, indem Sie die Standardbenutzeroberfläche auf der Autoreninstanz verwenden:

* In der globalen Navigation: **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Cloud Service]**
* Scrollen Sie nach unten zu **[!UICONTROL Adobe Analytics]**
* Wählen Sie **[!UICONTROL Jetzt konfigurieren]** oder **[!UICONTROL Konfigurationen anzeigen]**

![cloud-config](assets/cloud-config1.png)

### Dialogfeld „Konfiguration erstellen“ {#create-configuration-dialog}

* Wählen Sie `[+]` Symbol neben **[!UICONTROL Verfügbare Konfigurationen]** aus, um eine Konfiguration zu erstellen.

Im Dialogfeld Konfiguration erstellen identifizieren die einzugebenden Werte die Konfiguration.

![create-cloud-config](assets/cloud-config2.png)

* **Titel**

  (Erforderlich) Ein Anzeigetitel für die Konfiguration.
Geben Sie beispielsweise *Community-Analyse* ein

* **Name**

  (Optional) Wenn kein Name angegeben ist, wird standardmäßig ein gültiger, aus dem Titel abgeleiteter Knotenname verwendet.
Geben Sie beispielsweise &quot;*&quot;*

* **Vorlage**

  Klicken Sie auf `Adobe Analytics Configuration`

* Wählen Sie **Erstellen** aus

   * Startet die Konfigurationsseite und öffnet `Analytics Settings` Dialogfeld

### Dialogfeld „Analytics-Einstellungen“ {#analytics-settings-dialog}

Die anfängliche Erstellung einer neuen Analytics-Konfiguration führt zur Anzeige der Konfiguration und zu einem neuen Dialogfeld für die Eingabe der Analytics-Einstellungen. Dieses Dialogfeld erfordert die [vorausgesetzte Kontoinformationen](#prerequisites) die vom Kontobeauftragten abgerufen werden.

![analytics-settings](assets/analytics-settings.png)

* **Firma**

  Das Unternehmen, das mit dem Adobe Analytics-Konto verknüpft ist.

* **Benutzername**

  Der Anmeldename des Benutzers, der zur Verwaltung des Analytics-Kontos autorisiert ist.

* **Kennwort**

  Das Anmeldekennwort für den autorisierten Benutzer.

* **Rechenzentrum**

  Wählen Sie das Analytics-Rechenzentrum aus, in dem die Report Suite gehostet wird.

* **Tracking-Tag nicht zur Seite hinzufügen**

  Als Standard beibehalten (deaktiviert).

* **AppMeasurement verwenden**

  Als Standard beibehalten (deaktiviert).

* **Seitenimpressionen nicht jede Nacht importieren (Autor)**

  Als Standard beibehalten (deaktiviert).

* **Seitenimpressionen nicht jede Nacht importieren (veröffentlichen)**

  Als Standard beibehalten (deaktiviert).

So speichern Sie die Einstellungen:

* Wählen Sie **Mit Analytics verbinden**

   * Wenn nicht erfolgreich,

      * Stellen Sie sicher, dass Einträge keine führenden Leerzeichen enthalten.
      * Testen Sie ein anderes Rechenzentrum.

* Wählen Sie **OK** aus.

  ![analytics-settings](assets/analytics-settings1.png)

### Framework erstellen {#create-framework}

Nach erfolgreicher Konfiguration der Basisverbindung zu Adobe Analytics ist es erforderlich, ein Framework für die Community-Site zu erstellen oder zu bearbeiten. Ziel des Frameworks ist die Zuordnung von AEM-Variablen (Communities Feature) zu Analytics-Variablen (Report Suite).

* Wählen Sie `[+]` Symbol neben **[!UICONTROL Verfügbare Frameworks]**, um ein Framework zu erstellen.

  ![analytics-framework](assets/analytics-framework.png)

* **Titel**

  (Erforderlich) Ein Anzeigetitel für das Framework
Geben Sie beispielsweise *Community-Framework* ein.

* **Name**

  (Optional) Wenn kein Name angegeben ist, wird standardmäßig ein gültiger, aus dem Titel abgeleiteter Knotenname verwendet.
Geben Sie beispielsweise &quot;*&quot;*.

* *Vorlage*

  Wählen Sie `Adobe Analytics Framework`.

* Wählen Sie **Erstellen** aus.

Durch Erstellen des Analytics-Frameworks wird das Framework zur Konfiguration geöffnet.

## AEM Analytics Framework-Konfiguration {#aem-analytics-framework-configuration}

Das Framework ordnet AEM-Variablen Analytics-Variablen (eVars und Ereignisse) zu. Die für die Zuordnung verfügbaren Analytics-Variablen sind [in der Report Suite definiert](#adobe-analytics-report-suite-for-video-reporting).

![analytics-framework](assets/analytics-framework1.png)

### Report Suite auswählen {#select-report-suite}

Wählen Sie die Report Suite aus, die für Videoberichte eingerichtet wurde.

Wenn eine Report Suite noch nicht erstellt oder nicht ordnungsgemäß eingerichtet wurde, lesen Sie den vorherigen Abschnitt:
[Adobe Analytics Report Suite für Videoberichte](#adobe-analytics-report-suite-for-video-reporting)

Die Sidekick ist nicht erforderlich und kann minimiert werden, sodass sie den Zugriff auf die Report Suites-Einstellungen nicht behindert.

#### Report Suites-Dialog vor und nach der Auswahl von „Element hinzufügen“ {#report-suites-dialog-before-and-after-selecting-add-item}

![Report Suite](assets/report-suite.png)

1. Wählen Sie **Element hinzufügen +**.

   Es werden zwei Dropdown-Felder angezeigt.

1. `Report suite.` auswählen

   Die mit dem Unternehmenskonto verknüpften Report Suites stehen zur Auswahl.

1. Wählen Sie **daraufhin** Ja“ aus:

   ```
   Load default server settings?
    Do you want to load the default server settings and overwrite current values in the Server section?
   ```

1. Wählen Sie eine `Run Mode`.

1. Wählen Sie **Veröffentlichen** aus.

![analytics-framework2](assets/analytics-framework2.png)

Der Analytics-Cloud-Service und das Framework sind jetzt abgeschlossen. Die Zuordnungen werden definiert, nachdem eine Community-Site mit diesem aktivierten Analytics-Service erstellt wurde.

## Aktivieren von Analytics für eine Community-Site {#enable-analytics-for-a-community-site}

### Für neue Community-Site aktivieren {#enable-for-new-community-site}

So fügen Sie den Analytics Cloud-Service beim [ einer Community-Site hinzu](/help/communities/sites-console.md):

* In Schritt 3 auf der [Registerkarte ANALYTICS](/help/communities/sites-console.md#analytics):
   * Aktivieren Sie das **Analytics aktivieren**.
   * Wählen Sie das Framework aus der Dropdownliste aus.

* Kehren Sie optional zur Analytics-Framework-Konfiguration zurück, um die Variablenzuordnungen anzupassen.

### Für vorhandene Community-Site aktivieren {#enable-for-existing-community-site}

So fügen Sie den Analytics Cloud-Service zu einer [ Community-Site hinzu](/help/communities/sites-console.md#modifying-site-properties):

* Navigieren Sie zur Konsole **Communities > Sites** .
* Wählen Sie das Symbol Website bearbeiten der Community-Website aus.
* Wählen Sie die Einstellungen aus.
* Im Abschnitt Analytics :
   * Aktivieren Sie das **Analytics aktivieren**.
   * Wählen Sie das Framework aus der Dropdown-Liste aus.

* Kehren Sie optional zur Analytics-Framework-Konfiguration zurück, um die Variablenzuordnungen anzupassen.

### Für benutzerdefinierte Sites aktivieren {#enable-for-customized-sites}

Damit das Analytics-Tracking und der Import für eine Community-Site ordnungsgemäß funktionieren, muss ein Seitenelement mit den Attributen &quot;`scf-js-site-title`&quot; und „href“ vorhanden sein. Auf der Seite sollte nur ein solches Element vorhanden sein, z. B. in einem unveränderten `sitepage.hbs` für eine Community-Site. Der Wert von `siteUrl` wird extrahiert und als „Site *Pfad“ an Adobe Analytics*.

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

Stellen Sie bei **benutzerdefinierten Community** Site, die das `sitepage.hbs`-Skript überlagert, sicher, dass das Element vorhanden ist. Die `siteUrl`-Variable wird festgelegt, wenn sie auf dem Server gerendert wird, bevor sie an den Client gesendet wird.

Für eine **generische AEM-Site** die Communities-Komponenten enthält, aber nicht mit dem [Site-Erstellungsassistenten](/help/communities/sites-console.md) erstellt wird, muss das Element hinzugefügt werden. Der Wert von href sollte der Pfad zur Site sein. Wenn der Site-Pfad beispielsweise `/content/my/company/en` ist, verwenden Sie:

```xml
<div
    class="navbar-brand scf-js-site-title"
    href="/content/my/company/en.html"
    style="visibility: hidden;"
>
</div>
```

## Funktionen von Analytics for Communities {#analytics-for-communities-features}

Analytics wird automatisch für mehrere Communities-Funktionen verwendet.

Die OSGi[Konfiguration der Autorenumgebung ](/help/sites-deploying/configuring-osgi.md), `AEM Communities Analytics Component Configuration`, bietet eine Liste der Komponenten, die für Analytics instrumentiert wurden. Die automatische Zuordnung von Variablen wird durch die aufgelisteten Komponenten bestimmt.

Wenn neue benutzerdefinierte Komponenten erstellt werden, die für Analytics instrumentiert sind, sollten sie dieser Liste der konfigurierten Komponenten hinzugefügt werden.

### Komponentenkonfiguration {#component-configuration}

![component-configuration1](assets/component-configuration1.png)

>[!NOTE]
>
>Die Journalkomponenten werden verwendet, um die Blog-Funktion zu implementieren.

### Analytics AEM-Variablen zugeordnet {#mapped-analytics-to-aem-variables}

Nachdem die Community-Site gespeichert und Analytics aktiviert sowie das Cloud-Konfigurations-Framework ausgewählt wurde, werden die AEM-Variablen automatisch den Analytics-eVars und -Ereignissen zugeordnet. Sie beginnt mit eVar1 bzw. event1 und wird um 1 inkrementiert.

Wenn Sie eine vorhandene Report Suite verwenden, die eine der Variablen in eVar1 über eVar11 und event1 bis event7 zugeordnet hat, ist es erforderlich, [die AEM-Variablen neu zuzuordnen](#modifying-analytics-variable-mapping) und die ursprüngliche Zuordnung wiederherzustellen.

Im Folgenden finden Sie ein Beispiel für Standardzuordnungen:

![map-analytics](assets/map-analytics1.png)

#### Zuordnung der eVars, die mit jedem Ereignis gesendet werden {#map-of-evars-sent-with-each-event}

<table>
 <tbody>
  <tr>
   <td><strong> </strong></td>
   <td><strong>Aktivierung<br /> Ressource<br /> Typ</strong></td>
   <td><strong>Site<br /> Titel</strong></td>
   <td><strong>Funktion<br /> Typ</strong></td>
   <td><strong><br /></strong></td>
   <td><strong>Gruppe<br /> Pfad</strong></td>
   <td><strong>UGC<br />-Typ</strong></td>
   <td><strong>UGC<br />-Titel</strong></td>
   <td><strong>Benutzer<br /> (Mitglied)</strong></td>
   <td><strong>UGC<br />-Pfad</strong></td>
   <td><strong>Site<br /> Pfad</strong></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><strong>eVar1</strong></td>
   <td><strong>eVar2</strong></td>
   <td><strong>eVar3</strong></td>
   <td><strong>EVAR4</strong></td>
   <td><strong>EVAR5</strong></td>
   <td><strong>EVAR6</strong></td>
   <td><strong>EVAR7</strong></td>
   <td><strong>EVAR8</strong></td>
   <td><strong>EVAR9</strong></td>
   <td><strong>eVar10</strong></td>
  </tr>
  <tr>
   <td><strong>event1<br /> Ressourcenwiedergabe</strong></td>
   <td><em>(a)</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>(i)</em></td>
   <td><em>–</em></td>
  </tr>
  <tr>
   <td><strong>event2<br /> SCFView</strong></td>
   <td><em>(a)</em></td>
   <td><em>(b)</em></td>
   <td><em>(c)</em></td>
   <td><em>(d)</em></td>
   <td><em>(e)</em></td>
   <td><em>(f)</em></td>
   <td><em>(g)</em></td>
   <td><em>(h)</em></td>
   <td><em>(i)</em></td>
   <td><em>(j)</em></td>
  </tr>
  <tr>
   <td><strong>event3<br /> SCFCreate (Post)</strong></td>
   <td><em>–</em></td>
   <td><em>(b)</em></td>
   <td><em>(c)</em></td>
   <td><em>(d)</em></td>
   <td><em>(e)</em></td>
   <td><em>(f)</em></td>
   <td><em>(g)</em></td>
   <td><em>(h)</em></td>
   <td><em>(i)</em></td>
   <td><em>(j)</em></td>
  </tr>
  <tr>
   <td><strong>event4<br /> SCFFollow</strong></td>
   <td><em>–</em></td>
   <td><em>(b)</em></td>
   <td><em>(c)</em></td>
   <td><em>(d)</em></td>
   <td><em>(e)</em></td>
   <td><em>(f)</em></td>
   <td><em>(g)</em></td>
   <td><em>(h)</em></td>
   <td><em>(i)</em></td>
   <td><em>(j)</em></td>
  </tr>
  <tr>
   <td><strong>event5<br /> SCFVoteUp</strong></td>
   <td><em>–</em></td>
   <td><em>(b)</em></td>
   <td><em>(c)</em></td>
   <td><em>(d)</em></td>
   <td><em>(e)</em></td>
   <td><em>(f)</em></td>
   <td><em>(g)</em></td>
   <td><em>(h)</em></td>
   <td><em>(i)</em></td>
   <td><em>(j)</em></td>
  </tr>
  <tr>
   <td><strong>event6<br /> SCFVoteDown</strong></td>
   <td><em>–</em></td>
   <td><em>(b)</em></td>
   <td><em>(c)</em></td>
   <td><em>(d)</em></td>
   <td><em>(e)</em></td>
   <td><em>(f)</em></td>
   <td><em>(g)</em></td>
   <td><em>(h)</em></td>
   <td><em>(i)</em></td>
   <td><em>(j)</em></td>
  </tr>
  <tr>
   <td><strong>event7<br /> SCFRate</strong></td>
   <td><em>–</em></td>
   <td><em>(b)</em></td>
   <td><em>(c)</em></td>
   <td><em>(d)</em></td>
   <td><em>(e)</em></td>
   <td><em>(f)</em></td>
   <td><em>(g)</em></td>
   <td><em>(h)</em></td>
   <td><em>(i)</em></td>
   <td><em>(j)</em></td>
  </tr>
 </tbody>
</table>

**Beispiele für eVar-Werte :**

* *[MIME-Typ](https://www.iana.org/assignments/media-types/media-types.xhtml)*: video/mp4
* *[Community-Site-Titel](/help/communities/sites-console.md#step13asitetemplate)*: Geometrixx Communities
* *[Community-Funktionsname](/help/communities/functions.md)*: Forum
* *[Name der Community](/help/communities/creating-groups.md#creating-a-new-group)*: Wandern
* *Pfad zum Community-Gruppeninhalt*: `/content/sites/<site name>/en/groups/hiking`
* *[UGC-Komponente resourceType](/help/communities/essentials.md)*: `social/forum/components/hbs/topic`
* *UGC-Komponententitel*: Wanderthemen
* *login (authorizableId)*: `aaron.mcdonald@mailinator.com`
* *SRP-Pfad zum UGC*: `/content/usergenerated/asi/.../forum/jmtz-topic3`
oder *Pfad der zu folgenden Komponente*: `/content/sites/<site name>/en/jcr:content/content/primary/forum`

* *Pfad zum Inhalt der Community-Site*: `/content/sites/<site name>/en`

### Ändern der Analytics-Variablenzuordnung {#modifying-analytics-variable-mapping}

Die Zuordnung von Analytics-eVars und -Ereignissen zu AEM-Variablen ist in der Framework-Konfiguration sichtbar, nachdem Analytics für eine Community-Site aktiviert wurde.

Nachdem Analytics aktiviert wurde und bevor die Community-Site veröffentlicht wurde, kann die Zuordnung im Framework geändert werden. Ziehen Sie einfach die gewünschte Analytics-eVar oder das gewünschte Ereignis aus der linken Leiste und legen Sie sie in der entsprechenden Zeile in der Zuordnungstabelle ab.

Um doppelte Zuordnungen zu vermeiden, entfernen Sie unbedingt die ersetzte Analytics-eVar oder das ersetzte Ereignis aus der Zeile, indem Sie den Mauszeiger darüber bewegen und das „X“ auswählen, das rechts neben dem Analytics-Variablenelement angezeigt wird.

Wenn Communities-eVars und -Ereignisse Zuordnungen überschreiben, die bereits in der Report Suite vorhanden waren, weisen Sie zur Vermeidung von Datenverlust die AEM-Variablen für Communities-Funktionen anderen Analytics-eVars oder -Ereignissen zu und stellen Sie die ursprünglichen Zuordnungen wieder her.

>[!CAUTION]
>
>Es ist wichtig, eine Neuzuordnung vorzunehmen, bevor die Community[Site veröffentlicht wird](#publishing-the-community-site) wobei Analytics aktiviert ist, da andernfalls das Risiko von Datenverlust besteht.

#### Beispiel Schritt 1: Ziehen von Analytics eVar14 in die Zuordnungstabelle {#example-step-dragging-analytics-evar-into-mapping-table}

![analytics-mapping-evar](assets/analytics-mapping-evar.png)

#### Beispiel Schritt 2: Auswahl von „x“ zum Entfernen der ersetzten eVar11 {#example-step-selecting-x-to-remove-replaced-evar}

![analytics-mapping-evar1](assets/analytics-mapping-evar1.png)

#### Beispiel: Schritt 3: AEM var eventdata.siteId wurde zu Analytics evar14 neu zugeordnet {#example-step-aem-var-eventdata-siteid-remapped-to-analytics-evar}

![analytics-mapping-evar2](assets/analytics-mapping-evar2.png)

## Veröffentlichen der Community-Site {#publishing-the-community-site}

### Überprüfen der Analytics-zu-AEM-Variablenzuordnung {#verify-analytics-to-aem-variable-mapping}

Es empfiehlt sich, die Variablenzuordnung zu überprüfen, bevor Sie die Community-Site veröffentlichen, auf der auch der Analytics Cloud-Service und das Framework veröffentlicht werden.

Siehe Abschnitte:

* [Analytics AEM-Variablen zugeordnet](#mapped-analytics-to-aem-variables)
* [Ändern der Analytics-Variablenzuordnung](#modifying-analytics-variable-mapping)

>[!CAUTION]
>
>**Bei Verwendung einer vorhandenen Report Suite, die bereits Variablen innerhalb von verwendet**
>
>* **`evar1`** bis **`evar11`**
>
>* **`event1`** bis **`event7`**
>
>**Stellen Sie dann vor der Veröffentlichung der Community-Site** bereits vorhandene Zuordnung wieder her. Verschieben von Communities-AEM-Variablen, die automatisch (bei aktivierter Analytics für die Community-Site) anderen Analytics-Variablen zugeordnet wurden. Diese Neuzuordnung sollte über alle Communities-Komponenten hinweg konsistent sein.
>
>Andernfalls kann es zu einem nicht wiederherstellbaren Datenverlust kommen.

### Primärer Herausgeber {#primary-publisher}

Wenn es sich bei der ausgewählten Bereitstellung um [Veröffentlichungsfarm](/help/communities/topologies.md#tarmk-publish-farm) handelt, muss eine AEM-Veröffentlichungsinstanz als primärer Herausgeber identifiziert werden, der Adobe Analytics zum Schreiben von Berichtsdaten in [SRP](/help/communities/working-with-srp.md) abfragt.

Standardmäßig identifiziert die `AEM Communities Publisher Configuration` OSGi-Konfiguration ihre Veröffentlichungsinstanz als primären Herausgeber, sodass alle Veröffentlichungsinstanzen in einer Veröffentlichungsfarm sich selbst als primär identifizieren.

Daher müssen Sie die Konfiguration auf allen sekundären Veröffentlichungsinstanzen bearbeiten, um die Auswahl des Kontrollkästchens **Primärer Herausgeber** aufzuheben.

Spezifische Anweisungen finden Sie im Abschnitt zum primären Herausgeber von [Bereitstellen von Communities](/help/communities/deploy-communities.md#primary-publisher).

>[!CAUTION]
>
>Es ist wichtig, dass der primäre Herausgeber so konfiguriert ist, dass das Abrufen von mehreren Veröffentlichungsinstanzen verhindert wird.

### Replizieren des Crypto-Schlüssels {#replicate-the-crypto-key}

Die Adobe Analytics-Anmeldeinformationen werden verschlüsselt. Um die Replikation oder Übertragung verschlüsselter Analytics-Anmeldeinformationen zwischen Autoren- und Herausgebern zu erleichtern, müssen alle AEM-Instanzen denselben primären Verschlüsselungsschlüssel verwenden.

Befolgen Sie dazu die Anweisungen unter [Replizieren Sie den Crypto-Schlüssel](/help/communities/deploy-communities.md#replicate-the-crypto-key).

### Publish-Community-Site und Analytics Cloud Service {#publish-community-site-and-analytics-cloud-service}

Nachdem der Analytics Cloud-Service für eine Community-Site aktiviert und bei Bedarf die [Zuordnung von Analytics zu AEM-Variablen angepasst“ wurde](#mapped-analytics-to-aem-variables) replizieren Sie die Konfiguration in der Veröffentlichungsumgebung, indem Sie die Community-Site [(erneut)](/help/communities/sites-console.md#publishing-the-site).

## Abrufen von Berichten aus Analytics {#obtaining-reports-from-analytics}

### Berichtverwaltung {#report-management}

Die OSGi-Konfiguration [ Autors und ](/help/sites-deploying/configuring-osgi.md) primären Herausgebers, `AEM Communities Analytics Report Management`, wird zur Abfrage von Analytics verwendet.

Auf der Autoreninstanz sind die Abfragen für Echtzeitberichte.

Auf dem primären Herausgeber dienen die Abfragen der Bereitstellung von Informationen zur Vorbereitung auf den Analytics-Datenimport des Report Importers.

Das Abfrageintervall ist standardmäßig auf 10 Sekunden festgelegt.

### Report Importer {#report-importer}

Sobald eine für Analytics aktivierte Community-Site veröffentlicht wurde, kann die [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) des primären Herausgebers `AEM Communities Analytics Report Importer` so konfiguriert werden, dass das standardmäßige Abrufintervall für die Konfigurationen festgelegt wird, die nicht einzeln in CRXDE konfiguriert sind.

Das Abrufintervall steuert die Häufigkeit der Anfragen an Adobe Analytics für Daten, die abgerufen und in [SRP](/help/communities/working-with-srp.md) gespeichert werden sollen.

Wenn die Daten als „Big Data“ kategorisiert werden können, kann eine häufigere Abfrage die Community-Site stark belasten.

Die Standardabfrage **Importintervall** ist auf 12 Stunden festgelegt.

![report-importer](assets/report-importer.png)

### Anpassung von Komponentenberichten {#component-report-customization}

Zur Anpassung der zu verfolgenden Metriken werden derzeit Knoten im Repository erstellt, die Zeiträume definieren, für die ein Bericht zu dieser Metrik generiert werden soll.

Das Forenthema ist derzeit das einzige Beispiel für diese Anpassung:

* Melden Sie sich auf dem primären Herausgeber mit Administratorrechten an.
* Gehen Sie zu [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md). Beispiel: [https://localhost:4503/crx/de](https://localhost:4503/crx/de).

* Navigieren Sie unter dem `jcr:content` Knoten des Sprachstamms (z. B. `/content/sites/engage/en/jcr:content`) zu der für Analytics-Berichte konfigurierten Komponente.
Zum Beispiel: **`analytics/reportConfigs/social_forum_components_hbs_topic`**

* Beachten Sie die erstellten Zeiträume:

   * `last30Days`
   * `last90Days`
   * `thisYear`

* Beachten Sie den `total`Knoten .

   * Durch Ändern der **`interval`**-Eigenschaft wird das Report Importer-Intervall überschrieben.
   * Der Wert ist in Sekunden angegeben und auf vier Stunden (14400 Sekunden) festgelegt.

![component-report](assets/component-report.png)

## Verwalten von Benutzerdaten in Analytics {#manage-user-data-in-analytics}

Adobe Analytics stellt APIs bereit, mit denen Sie auf Benutzerdaten zugreifen, diese exportieren und löschen können. Weitere Informationen finden Sie unter [Senden von Zugriffs- und Löschanfragen](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/data-governance/an-gdpr-workflow.html?lang=de).

## Ressourcen {#resources}

* Adobe Experience Cloud: [Analytics-Hilfe und -Referenz](https://experienceleague.adobe.com/docs/analytics.html)
* AEM: [Integration mit Adobe Analytics](/help/sites-administering/adobeanalytics.md)
* AEM: [Analytics mit externen Anbietern](/help/sites-administering/external-providers.md)
