---
title: Konfigurieren von Video-Tracking für Adobe Analytics
description: Erfahren Sie mehr über die Konfiguration des Video-Trackings für SiteCatalyst.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 5d51f898-b6d1-40ac-bdbf-127cda1dc777
source-git-commit: db0e9d6105484b37e2e21e49bf0f95cef9da2a62
workflow-type: tm+mt
source-wordcount: '1754'
ht-degree: 71%

---

# Konfigurieren von Video-Tracking für Adobe Analytics{#configuring-video-tracking-for-adobe-analytics}

Es gibt verschiedene Methoden zum Verfolgen von Videoereignissen. Zwei davon sind veraltete Optionen für ältere Versionen von Adobe Analytics. Diese veraltete Option sind: Legacy Milestones und Legacy Seconds.

>[!NOTE]
>
>Bevor Sie fortfahren, stellen Sie sicher, dass Sie ein **abspielbares Video** in AEM hochgeladen haben.
>
>Um sicherzustellen, dass Ihre Videos auf der Seite wiedergegeben werden können, informieren Sie sich in **[diesem Tutorial](/help/sites-authoring/default-components-foundation.md#video)**, wie Sie Videodateien in AEM umkodieren.

Mit der folgenden Vorgehensweise können Sie ein Framework für das Videotracking mit jeder dieser Methoden einrichten.

>[!NOTE]
>
>Bei neuen Implementierung empfehlen wir, **nicht** die Legacy-Optionen für das Videotracking zu verwenden. Verwenden Sie die **Milestones** -Methode.

## Allgemeine Schritte {#common-steps}

1. Richten Sie eine Web-Seite ein, indem Sie eine **Videokomponente** aus dem Sidekick ziehen und ein abspielbares **Video als Asset** für die Komponente hinzufügen.

1. [Erstellen Sie eine Konfiguration und ein Framework für Adobe Analytics](/help/sites-administering/adobeanalytics.md).

   * Bei den Beispielen in den folgenden Abschnitten wird **my-sc-configuration** für die Konfiguration genutzt und **videofw** für das Framework.

1. Wählen Sie auf der Framework-Seite eine RSID aus und legen Sie die Nutzung auf „alle“ fest. ([https://localhost:4502/cf#/etc/cloudservices/sitecatalyst/videoconf/videofw.html](https://localhost:4502/cf#/etc/cloudservices/sitecatalyst/videoconf/videofw.html))
1. Ziehen Sie die Videokomponente aus der Komponentenkategorie „Allgemein“ im Sidekick in das Framework.
1. Wählen Sie eine Tracking-Methode aus:

   * [Milestones](/help/sites-administering/adobeanalytics.md)
   * [Non-Legacy Milestones](/help/sites-administering/adobeanalytics.md)
   * [Legacy Milestones](/help/sites-administering/adobeanalytics.md)
   * [Legacy Seconds](/help/sites-administering/adobeanalytics.md)

1. Abhängig von der ausgewählten Tracking-Methode ändert sich auch die Liste der CQ-Variablen. In den folgenden Abschnitten erfahren Sie, wie Sie die Komponente weiter konfigurieren und die CQ-Variablen den Adobe Analytics-Eigenschaften zuordnen.

## Milestones {#milestones}

Die Meilensteinmethode verfolgt die meisten Informationen über das Video, ist stark anpassbar und leicht zu konfigurieren.

Um die Meilensteinmethode zu verwenden, geben Sie zeitbasierte Tracking-Offsets an, um die Meilensteine zu definieren. Wenn eine Videowiedergabe einen Milestone erreicht, ruft die Seite Adobe Analytics auf, um das Ereignis nachzuverfolgen. Für jeden von Ihnen definierten Meilenstein erstellt die Komponente eine CQ-Variable, die Sie einer Adobe Analytics-Eigenschaft zuordnen können. Der Name dieser CQ-Variablen verwendet das folgende Format:

```shell
eventdata.events.milestoneXX
```

Das XX-Suffix ist der Tracking-Offset, der den Meilenstein definiert. So erzeugt die Festlegung der Tracking-Versatzwerte auf 4, 8, 16, 20 und 28 Sekunden die folgenden CQ-Variablen:

* `eventdata.events.milestone4`
* `eventdata.events.milestone8`
* `eventdata.events.milestone16`
* `eventdata.events.milestone20`
* `eventdata.events.milestone28`

In der folgenden Tabelle sind die standardmäßigen CQ-Variablen beschrieben, die für die Milestones-Methode bereitgestellt werden:

<table>
 <tbody>
  <tr>
   <th>CQ-Variablen</th>
   <th>Adobe Analytics-Eigenschaften</th>
  </tr>
  <tr>
   <td>eventdata.videoName </td>
   <td>Variablen, die dieser Eigenschaft zugeordnet sind, enthalten den <strong>Anzeigenamen</strong> (<strong>Titel</strong>) des Videos, sofern dieser im DAM festgelegt ist. Wenn dieser nicht festgelegt ist, wird stattdessen der <strong>Dateiname</strong> gesendet. Nur einmal gesendet, zu Beginn der Videowiedergabe.</td>
  </tr>
  <tr>
   <td>eventdata.videoFileName </td>
   <td>Variablen, die diesem zugeordnet sind, enthalten den Namen der Datei. Wird nur zusammen mit eventdata.events.a.media.view gesendet </td>
  </tr>
  <tr>
   <td>eventdata.videoFilePath </td>
   <td>Variablen, die diesem zugeordnet sind, enthalten den Pfad der Datei auf dem Server. Wird nur zusammen mit eventdata.events.a.media.view gesendet </td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.segmentView </td>
   <td>Wird jedes Mal gesendet, wenn ein Segment-Milestone übergeben wird </td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.timePlayed</td>
   <td>Wird jedes Mal gesendet, wenn ein Milestone ausgelöst wird. Die Anzahl der Sekunden, die Benutzende mit der Wiedergabe des angegebenen Segments verbracht haben, wird ebenfalls zusammen mit diesem Ereignis gesendet, Beispiel: eventX=21<br /> </td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.view </td>
   <td>Wird beim Initialisieren der Videoansicht gesendet</td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.complete </td>
   <td>Wird gesendet, wenn die Videowiedergabe abgeschlossen ist<br /> </td>
  </tr>
  <tr>
   <td>eventdata.events.milestoneX </td>
   <td>Wird gesendet, wenn der angegebene Milestone übergeben wird. X steht für die Sekunde, bei der der Milestone ausgelöst wird.<br /> </td>
  </tr>
  <tr>
   <td>eventdata.a.contentType </td>
   <td>Wird bei jedem Milestone gesendet. Wird im Adobe Analytics-Aufruf als „pev3“ angezeigt und normalerweise als „Video“ gesendet<br /> </td>
  </tr>
  <tr>
   <td>eventdata.a.media.name </td>
   <td>Sucht genau nach eventdata.videoName </td>
  </tr>
  <tr>
   <td>eventdata.a.media.segment </td>
   <td>Enthält Informationen zu dem Segment, das beispielsweise angezeigt wurde: <code>2:O:4-8</code> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Um den **Anzeigename** eines Videos festzulegen, öffnen Sie das Video zur Bearbeitung im DAM-System und geben Sie im Metadatenfeld **Titel** den gewünschten Namen ein.

1. Nachdem Sie Meilensteine als Tracking-Methode ausgewählt haben, geben Sie im Feld &quot;Versatz verfolgen&quot;eine kommagetrennte Liste der Tracking-Versätze in Sekunden ein. Beispielsweise definiert der folgende Wert Meilensteine bei 4, 8, 16, 20 und 28 Sekunden nach dem Anfang des Videos:

   ```xml
   4,8,16,20,24
   ```

   Die Offset-Werte müssen Ganzzahlen größer als 0 sein. Der Standardwert ist `10,25,50,75`.

1. Um die CQ-Variablen zu Adobe Analytics-Eigenschaften zuzuordnen, ziehen Sie die Adobe Analytics-Eigenschaften vom Content Finder neben der CQ-Variablen auf die Komponente.

   Weitere Informationen zum Optimieren der Zuordnungen finden Sie im Leitfaden [Videomessung in Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=de).

1. [Fügen Sie das Framework](/help/sites-administering/adobeanalytics.md) zur Seite hinzu.
1. Um die Einrichtung im **Vorschaumodus** zu testen, geben Sie das Video wieder, damit die Adobe Analytics-Aufrufe ausgelöst werden.

Die folgenden Beispiele für Adobe Analytics-Tracking-Daten gelten für die Milestones-Nachverfolgung mit Tracking-Versätzen von 4, 8, 16, 20 und 24 und den folgenden Zuordnungen für die CQ-Variablen:

<table>
 <tbody>
  <tr>
   <th>CQ-Variable</th>
   <th>Adobe Analytics-Eigenschaft</th>
  </tr>
  <tr>
   <td>eventdata.videoName </td>
   <td>prop2</td>
  </tr>
  <tr>
   <td>eventdata.videoFileName </td>
   <td>prop3 </td>
  </tr>
  <tr>
   <td>eventdata.videoFilePath </td>
   <td>prop4</td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.segmentView </td>
   <td>event1</td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.timePlayed</td>
   <td>event2<br /> </td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.view </td>
   <td>event3</td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.complete </td>
   <td>event4<br /> </td>
  </tr>
  <tr>
   <td>eventdata.events.milestone4</td>
   <td>event10</td>
  </tr>
  <tr>
   <td>eventdata.events.milestone8</td>
   <td>event11</td>
  </tr>
  <tr>
   <td>eventdata.events.milestone16</td>
   <td>event12</td>
  </tr>
  <tr>
   <td>eventdata.events.milestone20</td>
   <td>event13</td>
  </tr>
  <tr>
   <td>eventdata.events.milestone24</td>
   <td>event14</td>
  </tr>
  <tr>
   <td>eventdata.a.contentType </td>
   <td>eVar3</td>
  </tr>
  <tr>
   <td>eventdata.a.media.name </td>
   <td>eVar1, prop1 </td>
  </tr>
  <tr>
   <td>eventdata.a.media.segment </td>
   <td>eVar2</td>
  </tr>
 </tbody>
</table>

Bei diesem Beispiel wird die Videokomponente wie folgt auf der Framework-Seite angezeigt:

![video1](assets/video1.png)

>[!NOTE]
>
>Um die Aufrufe an Adobe Analytics zu sehen, verwenden Sie ein entsprechendes Tool wie DigitalPulse Debugger oder Fiddler.

Aufrufe an Adobe Analytics mit dem gezeigten Beispiel sollten wie folgt aussehen, wenn Sie sie mit DigitalPulse Debugger anzeigen:

![chlimage_1-128](assets/chlimage_1-128.png)

*Dies ist der **erste Aufruf**an Adobe Analytics mit den folgenden Werten:*

* *prop1 und eVar1 für eventdata.a.media.name,*
* *props2–4 zusammen mit eVar2 und eVar3, wobei contentType (video) und segment (1:O:1–4) enthalten sind*
* *event3, das eventdata.events.a.media.view zugeordnet wurde*

![chlimage_1-129](assets/chlimage_1-129.png)

*Dies ist der **dritte Aufruf**an Adobe Analytics:*

* *prop1 und eVar1 enthalten a.media.name;*
* *event1, da ein Segment angesehen wurde*
* *event2, gesendet mit der wiedergegebenen Zeit = 4*
* *event11 gesendet, weil eventdata.events.milestone8 erreicht wurde*
* *prop2 bis 4 wurden nicht gesendet (da eventdata.events.a.media.view nicht ausgelöst wurde)*

## Nicht veraltete Meilensteine {#non-legacy-milestones}

Die Nicht-Legacy-Meilensteinmethode ähnelt der Meilensteinmethode, mit der Ausnahme, dass Meilensteine mit Prozentsätzen der Verfolgungslänge definiert werden. Folgende Gemeinsamkeiten treten auf:

* Wenn eine Videowiedergabe einen Milestone erreicht, ruft die Seite Adobe Analytics auf, um das Ereignis nachzuverfolgen.
* Der [statische Satz an CQ-Variablen](#cqvars), die für die Zuordnung zu Adobe Analytics-Eigenschaften definiert sind.
* Für jeden von Ihnen definierten Meilenstein erstellt die Komponente eine CQ-Variable, die Sie einer Adobe Analytics-Eigenschaft zuordnen können.

Der Name dieser CQ-Variablen verwendet das folgende Format:

Das XX-Suffix ist der Prozentsatz der Verfolgungslänge, der den Meilenstein definiert. Wenn Sie beispielsweise die Prozentsätze 10, 25, 50 und 75 angeben, werden die folgenden CQ-Variablen generiert:

* `eventdata.events.milestone10`
* `eventdata.events.milestone25`
* `eventdata.events.milestone50`
* `eventdata.events.milestone75`

```shell
eventdata.events.milestoneXX
```

1. Nachdem Sie als Tracking-Methode Nicht-Legacy-Meilensteine ausgewählt haben, geben Sie im Feld &quot;Versatz verfolgen&quot;eine kommagetrennte Liste mit Prozentsätzen der Verfolgungslänge ein. Der folgende Standardwert definiert beispielsweise Meilensteine bei 10, 25, 50 und 75 Prozent der Verfolgungslänge:

   ```xml
   10,25,50,75
   ```

   Die Offset-Werte müssen Ganzzahlen größer als 0 sein.

1. Um die CQ-Variablen zu Adobe Analytics-Eigenschaften zuzuordnen, ziehen Sie die Adobe Analytics-Eigenschaften vom Content Finder neben der CQ-Variablen auf die Komponente.

   Weitere Informationen zum Optimieren der Zuordnungen finden Sie im Leitfaden [Videomessung in Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=de).

1. [Fügen Sie das Framework](/help/sites-administering/adobeanalytics.md) zur Seite hinzu.
1. Um die Einrichtung im **Vorschaumodus** zu testen, geben Sie das Video wieder, damit die Adobe Analytics-Aufrufe ausgelöst werden.

## Legacy Milestones {#legacy-milestones}

Diese Methode ähnelt der Milestones-Methode mit dem Unterschied, dass die in der *Tracking-Offset* -Feld sind Prozentsätze anstelle von festgelegten Punkten im Video.

>[!NOTE]
>
>Das Feld Tracking Offset akzeptiert nur eine kommagetrennte Liste mit Ganzzahlen zwischen 1 und 100.

1. Legen Sie den Versatz &quot;Verfolgen&quot;fest.

   * z. B. 10,50,75,100

   Die Informationen, die an Adobe Analytics gesendet werden, sind nur begrenzt anpassbar. Für die Zuordnung stehen nur drei Variablen zur Verfügung:

<table>
 <tbody>
  <tr>
   <td>eventdata.videoName <br /> </td>
   <td>Variablen, die dieser Eigenschaft zugeordnet sind, enthalten den <strong>Anzeigenamen</strong> (<strong>Titel</strong>) des Videos, sofern dieser im DAM festgelegt ist. Wenn dieser nicht festgelegt ist, wird stattdessen der <strong>Dateiname</strong> gesendet. Nur einmal gesendet, zu Beginn der Videowiedergabe.<br /> </td>
  </tr>
  <tr>
   <td>eventdata.videoFileName </td>
   <td>Variablen, die diesem zugeordnet sind, enthalten den Namen der Datei. Nur einmal gesendet, zu Beginn der Videowiedergabe.</td>
  </tr>
  <tr>
   <td>eventdata.videoFilePath </td>
   <td>Die dieser Variablen zugeordnete Variable enthält den Pfad der Datei auf dem Server. Nur einmal gesendet, zu Beginn der Videowiedergabe.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Um den **Anzeigename** eines Videos festzulegen, öffnen Sie das Video zur Bearbeitung im DAM-System und geben Sie im Metadatenfeld **Titel** den gewünschten Namen ein. Wenn Sie fertig sind, müssen Sie die Änderungen speichern.

1. Ordnen Sie diese Variablen zu props 1 bis 3 zu.

   Die **übrigen relevanten Informationen** im Aufruf werden zusammenhängend in **einer** Variablen namens **pev3** gesendet.

   **Beispielaufrufe** an Adobe Analytics mit dem gezeigten Beispiel sollten wie folgt aussehen, wenn Sie sie mit DigitalPulse Debugger anzeigen:

   ![lmilestones1](assets/lmilestones1.png)

   *Die **pev3**-Variable, die bei dem Aufruf gesendet wird, enthält die folgenden Informationen:*

   * *Name*: der Name der Videodatei (*film.avi*)

   * *Length*: die Länge der Videodatei in Sekunden (*100*)

   * *Player Name*: der Video-Player für die Wiedergabe der Videodatei (*HTML5 video*)

   * *Total Seconds Played*: die Gesamtzahl an Sekunden, wie lange das Video wiedergegeben wurde (*25*)

   * *Start Timestamp*: Zeitstempel, der angibt, wann die Videowiedergabe gestartet ist (*1331035567*)

   * *Play Session*: die Details der Wiedergabesitzung. Dieses Feld gibt an, wie Benutzende mit dem Video interagiert haben. Dazu gehören Daten wie: wo haben sie die Wiedergabe des Videos gestartet, haben sie mit dem Videoregler das Video vorgespult, wo haben sie die Wiedergabe angehalten (*L10E24S58L58 – Video wurde bei Sekunde 25 von Abschnitt L10, dann übersprungen auf Sek. 48*)

## Ältere Sekunden {#legacy-seconds}

Bei Nutzung der **Legacy Seconds**-Methode werden Adobe Analytics-Aufrufe alle N Sekunden ausgelöst, wobei N im Feld „Versatz nachverfolgen“ festgelegt ist.

1. Legen Sie den Tracking-Versatz auf eine beliebige Anzahl an Sekunden fest.

   * Beispiel: 6

   >[!NOTE]
   >
   >Das Feld „Versatz nachverfolgen“ akzeptiert nur Ganzzahlen, die größer als 0 sind.

   Die Informationen, die an Adobe Analytics gesendet werden, sind weniger anpassbar. Für die Zuordnung stehen nur drei Variablen zur Verfügung:

<table>
 <tbody>
  <tr>
   <td>eventdata.videoName <br /> </td>
   <td>Variablen, die dieser Eigenschaft zugeordnet sind, enthalten den <strong>Anzeigenamen</strong> (<strong>Titel</strong>) des Videos, sofern dieser im DAM festgelegt ist. Wenn dieser nicht festgelegt ist, wird stattdessen der <strong>Dateiname</strong> gesendet. Nur einmal gesendet, zu Beginn der Videowiedergabe.<br /> </td>
  </tr>
  <tr>
   <td>eventdata.videoFileName </td>
   <td>Die dieser Variablen zugeordnete Variable enthält den Namen der Datei. Nur einmal gesendet, zu Beginn der Videowiedergabe.</td>
  </tr>
  <tr>
   <td>eventdata.videoFilePath </td>
   <td>Die dieser Variablen zugeordnete Variable enthält den Pfad der Datei auf dem Server. Nur einmal gesendet, zu Beginn der Videowiedergabe.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Um den **Anzeigename** eines Videos festzulegen, öffnen Sie das Video zur Bearbeitung im DAM-System und geben Sie im Metadatenfeld **Titel** den gewünschten Namen ein. Wenn Sie fertig sind, müssen Sie die Änderungen speichern.

1. Ordnen Sie diese Variablen prop1, prop2 und prop3 zu

   Die **der übrigen einschlägigen Informationen** im Aufruf wird zusammen mit **one** Variable namens **pev3**.

   Aufrufe an Adobe Analytics mit dem gezeigten Beispiel sollten wie folgt aussehen, wenn Sie sie mit DigitalPulse Debugger anzeigen:

   ![lseconds](assets/lseconds.png)

   *Der Aufruf ähnelt dem obigen Legacy Milestones-Aufruf. Siehe Informationen zu pev3 .**[sofern vorhanden](/help/sites-administering/adobeanalytics.md)**.*

**In diesem Tutorial verwendete Referenzen:**

[0] [https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=de](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=de)
