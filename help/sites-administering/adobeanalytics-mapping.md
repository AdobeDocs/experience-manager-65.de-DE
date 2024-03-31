---
title: Zuordnen von Komponentendaten zu Adobe Analytics-Eigenschaften
description: Erfahren Sie, wie Sie Komponentendaten zu SiteCatalyst-Eigenschaften zuordnen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: c7c0c705-ec16-40f5-ad08-193f82d01263
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1449'
ht-degree: 100%

---

# Zuordnen von Komponentendaten zu Adobe Analytics-Eigenschaften{#mapping-component-data-with-adobe-analytics-properties}

Fügen Sie Komponenten zum Framework hinzu, die Daten sammeln, um sie an Adobe Analytics zu senden. Komponenten zur Sammlung von Analysedaten speichern die Daten in der entsprechenden **CQ-Variablen**. Wenn Sie solch eine Komponente zu einem Framework hinzufügen, zeigt das Framework die Liste der CQ-Variablen an, sodass Sie jede Variable der entsprechenden **Analytics-Variablen** zuordnen können.

![aa-11](assets/aa-11.png)

Wenn die **AEM-Ansicht** geöffnet ist, werden die Analytics-Variablen im Content Finder angezeigt.

![aa-12](assets/aa-12.png)

Sie können auch mehrere Analytics-Variablen derselben **CQ-Variablen** zuordnen.

![chlimage_1-68](assets/chlimage_1-68.png)

Die zugeordneten Daten werden an Adobe Analytics gesendet, wenn die Seite geladen wird und die folgenden Bedingungen erfüllt sind:

* Die Seite ist mit dem Framework verknüpft.
* Die Seite nutzt die Komponenten, die zum Framework hinzugefügt werden.

Mit der folgenden Vorgehensweise können Sie Variablen von CQ-Komponenten den Eigenschaften von Adobe Analytics-Berichten zuordnen.

1. Ziehen Sie in der **AEM-Ansicht** eine Tracking-Komponente vom Sidekick auf das Framework. Ziehen Sie z. B. die Komponente **Seite** aus der Kategorie **Allgemein**.

   ![aa-13](assets/aa-13.png)

   Es gibt mehrere Standard-Komponentengruppen: **Allgemein**, **Commerce**, **Communities** und **Andere**. Je nach Konfiguration zeigt Ihre AEM-Instanz möglicherweise andere Gruppen und Komponenten an.

1. Um Adobe Analytics-Variablen den Variablen zuzuordnen, die in der Komponente definiert sind, ziehen Sie eine **Analytics-Variable** vom Content Finder in ein Feld auf der Tracking-Komponente. Ziehen Sie beispielsweise `Page Name (pageName)` auf `pagedata.title`.

   ![aa-14](assets/aa-14.png)

   >[!NOTE]
   >
   >Die für das Framework ausgewählte Report Suite-ID (RSID) bestimmt die Adobe Analytics-Variablen, die im Content Finder angezeigt werden.

1. Wiederholen Sie die vorhergehenden beiden Schritte für andere Komponenten und Variablen.

   >[!NOTE]
   >
   >Sie können mehrere Analytics-Variablen (z. B. `props`, `eVars`, `events`) derselben CQ-Variablen (z. B. `pagedata.title`) zuordnen.

   >[!CAUTION]
   >
   >Wir empfehlen Ihnen dringend Folgendes:
   >
   >* `eVars` und `props` werden CQ-Variablen zugeordnet, die entweder mit `pagedata.X` oder mit `eventdata.X` beginnen.
   >* Ereignisse werden dagegen Variablen zugeordnet, die mit `eventdata.events.X` beginnen.

1. Um das Framework auf der Veröffentlichungsinstanz Ihrer Website bereitzustellen, öffnen Sie im Sidekick die Registerkarte **Seite** und klicken Sie auf **Framework aktivieren**.

## Zuordnen produktbezogener Variablen {#mapping-product-related-variables}

Für die Benennung produktbezogener Variablen und Ereignisse, die produktbezogenen Adobe Analytics-Eigenschaften zugeordnet werden sollen, nutzt AEM eine Konvention:

| CQ-Variable | Analytics-Variable | Beschreibung |
|--- |--- |--- |
| `product.category` | `product.category` (Konversionsvariable) | Die Produktkategorie |
| `product.sku` | `product.sku` (Konversionsvariable) | Die Produkt-SKU |
| `product.quantity` | `product.quantity` (Konversionsvariable) | Die Anzahl an gekauften Produkten |
| `product.price` | `product.price` (Konversionsvariable) | Der Produktpreis |
| `product.events.<eventName>` | Die Erfolgsereignisse, die mit dem Produkt im Bericht verknüpft werden sollen. | `product.events` ist das Präfix für Ereignisse namens *eventName.* |
| `product.evars.<eVarName>` | Die Konversionsvariablen (`eVar`), die mit dem Produkt verknüpft werden sollen. | `product.evars` ist das Präfix für eVar-Variablen namens *eVarName.* |

Mehrere AEM Commerce-Komponenten nutzen diese Variablennamen.

>[!NOTE]
>
>Ordnen Sie keine Adobe Analytics-Produkteigenschaften einer CQ-Variablen zu. Die Konfiguration produktbezogener Zuordnungen, wie in der Tabelle beschrieben, entspricht der Zuordnung der Produktvariablen.

### Prüfen von Berichten in Adobe Analytics {#checking-reports-on-adobe-analytics}

1. Melden Sie sich bei Adobe Analytics mit Ihren AEM-Anmeldedaten an.
1. Stellen Sie sicher, dass Sie dieselbe RSID nutzen wie im vorherigen Schritt.
1. Wählen Sie unter **Berichte** (auf der linken Seite der Seite) die Option **Benutzerspezifische Konversion** und dann **Benutzerspezifische Konversion 1–10** aus. Wählen Sie die Variable aus, die `eVar7` entspricht.

1. Je nach Adobe Analytics-Version müssen Sie durchschnittlich 45 Minuten warten, bis der Bericht mit dem verwendeten Suchbegriff („aubergine“ im Beispiel) aktualisiert wurde.

## Verwenden des Content Finder (cf#) mit Adobe Analytics-Frameworks {#using-the-content-finder-cf-with-adobe-analytics-frameworks}

Wenn Sie ein Adobe Analytics-Framework zum ersten Mal öffnen, enthält der Content Finder vordefinierte Analytics-Variablen unter:

* Traffic
* Konversion
* Ereignisse

Wenn Sie eine RSID auswählen, werden alle zu dieser RSID gehörenden Variablen zur Liste hinzugefügt.\
`cf#` wird benötigt, um Analytics-Variablen den CQ-Variablen in den verschiedenen Tracking-Komponenten zuzuordnen. Siehe „Einrichten eines Frameworks für das grundlegende Tracking“.

Je nach für das Framework ausgewählter Ansicht enthält der Content Finder entweder Analytics-Variablen (in der AEM-Ansicht) oder CQ-Variablen (in der Analytics-Ansicht).

Sie können mit der Liste wie folgt arbeiten:

1. In der **AEM-Ansicht** können Sie abhängig vom ausgewählten Variablentyp die Liste mithilfe von drei Filterschaltflächen filtern:

   * Wenn die *Schaltfläche „Nein“* ausgewählt ist, wird die komplette Liste angezeigt.
   * Wenn die Schaltfläche **Traffic** ausgewählt ist, werden in der Liste nur die Variablen angezeigt, die zum Bereich „Traffic“ gehören.
   * Wenn die Schaltfläche **Konversion** ausgewählt ist, werden in der Liste nur die Variablen angezeigt, die zum Bereich „Konversion“ gehören.
   * Wenn die Schaltfläche **Ereignisse** ausgewählt ist, werden in der Liste nur die Variablen angezeigt, die zum Bereich „Ereignisse“ gehören.

   >[!NOTE]
   >
   >Sie können immer nur eine Filterschaltfläche aktivieren.

   1. Die Liste bietet auch eine Suchfunktion, die die Elemente entsprechend dem im Suchfeld eingegebenen Text filtert.
   1. Wenn bei der Suche nach Elementen in der Liste eine Filteroption aktiviert ist, werden auch die angezeigten Ergebnisse gemäß der aktivierten Schaltfläche gefiltert.
   1. Über die Schaltfläche mit den runden Pfeilen können Sie die Liste jederzeit neu laden.
   1. Wenn Sie mehrere RSIDs im Framework auswählen, werden alle Variablen in der Liste angezeigt. Dabei werden alle Beschriftungen verwendet, die in den ausgewählten RSIDs genutzt werden.

1. In der Adobe Analytics-Ansicht zeigt der Content Finder alle CQ-Variablen an, die zu den Tracking-Komponenten gehören, die in die CQ-Ansicht gezogen wurden.

   * Wenn beispielsweise als einzige Komponente die **Download-Komponente** in die CQ-Ansicht *gezogen wurde* (diese Ansicht umfasst zwei zuordnungsfähige Variablen: *eventdata.downloadLink* und *eventdata.events.startDownload*), sieht die Inhaltssuche nach dem Wechsel zur Adobe Analytics-Ansicht wie folgt aus:

   ![aa-22](assets/aa-22.png)

   * Sie können die Variablen auf jede beliebige Adobe Analytics-Variable ziehen, die zu einer der drei Variablenbereiche (**Traffic**, **Konversion** und **Ereignisse**) gehört.

   * Wenn Sie in der CQ-Ansicht eine neue Tracking-Komponente auf das Framework ziehen, werden die zur Komponente gehörenden CQ-Variablen automatisch zur Inhaltssuche (cf# für „Content Finder“) in der Adobe Analytics-Ansicht hinzugefügt.

   >[!NOTE]
   >
   >Sie können immer nur eine CQ-Variable auf einmal einer Adobe Analytics-Variable zuordnen.

## Verwenden der AEM-Ansicht und der Analytics-Ansicht {#using-aem-view-and-analytics-view}

Auf einer Framework-Seite können Benutzende jederzeit zwischen zwei Ansichten der Adobe Analytics-Zuordnungen wechseln. Diese beiden Ansichten bieten mit ihren beiden unterschiedlichen Perspektiven einen besseren Überblick über die Zuordnungen im Framework.

### AEM-Ansicht {#aem-view}

![aa-23](assets/aa-23.png)

Das obige Bild dient als Beispiel. Die **AEM-Ansicht** hat die folgenden Eigenschaften:

1. Dies ist die Standardansicht, wenn das Framework geöffnet wird.
1. Linke Seite: Der Content Finder (cf#) zeigt basierend auf den ausgewählten RSIDs die Adobe Analytics-Variablen an.
1. Registerkartenkopfzeilen (**AEM-Ansicht** und **Analytics-Ansicht**): Verwenden Sie diese, um zwischen den beiden Ansichten zu wechseln.

1. **AEM-Ansicht**:

   1. Wenn das Framework Komponenten enthält, die vom übergeordneten Framework vererbt wurden, werden sie hier aufgeführt, zusammen mit den Variablen, die den Komponenten zugeordnet sind.

      1. Vererbte Komponenten sind gesperrt.
      1. Doppelklicken Sie zum Entsperren einer vererbten Komponente auf das Vorhängeschloss neben dem Namen der Komponente.
      1. Um die Vererbung rückgängig zu machen, löschen Sie die entsperrte Komponente. Sie erhält daraufhin den Status „gesperrt“ zurück.

   1. **Ziehen Sie Komponenten in diesen Bereich, um sie zum Analytics-Framework hinzuzufügen**: Komponenten können aus dem Sidekick hierhin gezogen werden.
   1. Sie können alle Komponenten finden, die derzeit im Analytics-Framework enthalten sind:

      1. Um eine Komponente hinzuzufügen, ziehen Sie sie aus der Sidekick-Registerkarte „Komponenten“ in das Framework.
      1. Um eine Komponente und alle zugehörigen Zuordnungen zu löschen, wählen Sie im Kontextmenü der Komponente die Option „Löschen“ und akzeptieren Sie den Löschvorgang im Bestätigungsdialogfeld.
      1. Beachten Sie, dass Sie eine Komponente nur aus dem Framework löschen können, in dem sie erstellt wurde, und sie nicht im eigentlichen Sinne aus untergeordneten Frameworks löschen können. (Sie können sie dort nur überschreiben.)

### Analytics-Ansicht {#analytics-view}

![aa-24](assets/aa-24.png)

1. Um auf diese Ansicht zuzugreifen, wechseln Sie im Framework zur Registerkarte **Analytics-Ansicht**.
1. Linke Seite: Content Finder (cf#) mit CQ-Variablen, basierend auf den Komponenten, die in der CQ-Ansicht zum Framework hinzugefügt wurden.
1. Registerkartenkopfzeilen (**AEM-Ansicht** und **Analytics-Ansicht**): Verwenden Sie diese, um zwischen den beiden Ansichten zu wechseln.

1. In den drei Tabellen („Traffic“, „Konversion“, „Ereignis“) sind alle verfügbaren Adobe Analytics-Variablen aufgeführt, die zu den ausgewählten RSIDs gehören. Die hier gezeigten Zuordnungen sollten mit denen in der AEM-Ansicht übereinstimmen:

   * **Traffic**:

      * Traffic-Variable (`prop1`), die einer CQ-Variablen (`eventdata.downloadLink`) zugeordnet ist

      * Wenn neben der Komponente ein Vorhängeschloss angezeigt wird, bedeutet dies, dass sie von einem übergeordneten Framework übernommen wurde und daher nicht bearbeitet werden kann.

   * **Konversion**:

      * Konversionsvariable (`eVar1`), die einer CQ-Variablen (`pagedata.title`) zugeordnet ist

      * Konversionsvariable (`eVar3`), die einem JavaScript-Ausdruck zugeordnet ist, der inline hinzugefügt wurde (durch Doppelklicken auf das CQ-Variablen-Feld und manuelles Eingeben des Codes)

   * **Ereignis**:

      * Ereignisvariable (`event1`), die einem CQ-Ereignis (`eventdata.events.pageView`) zugeordnet ist

>[!NOTE]
>
>Die Spalte der CQ-Variablen in jeder Tabelle kann auch inline ausgefüllt werden, indem auf das Feld doppelgeklickt und dann der gewünschte Text eingegeben wird. In diesen Feldern ist JavaScript als Eingabe möglich.
>
>Beispiel: Neben `prop3` können Sie Folgendes hinzufügen:
>     `'`* `Adobe:'+pagedata.title+':'+pagedata.sitesection`\
>, um den *Titel* einer Seite und ihre *sitesection* verkettet mit einem *:* (Doppelpunkt) und mit dem Präfix *Adobe* als `prop3` zu übermitteln.
>

>[!CAUTION]
>
>Sie können immer nur eine CQ-Variable auf einmal einer Adobe Analytics-Variable zuordnen.
