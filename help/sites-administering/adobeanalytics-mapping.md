---
title: Zuordnen von Komponentendaten zu Adobe Analytics-Eigenschaften
description: Erfahren Sie, wie Sie Komponentendaten mit SiteCatalyst-Eigenschaften zuordnen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: c7c0c705-ec16-40f5-ad08-193f82d01263
source-git-commit: 260f71acd330167572d817fdf145a018b09cbc65
workflow-type: tm+mt
source-wordcount: '1440'
ht-degree: 53%

---

# Zuordnen von Komponentendaten zu Adobe Analytics-Eigenschaften{#mapping-component-data-with-adobe-analytics-properties}

Fügen Sie Komponenten zum Framework hinzu, die die Daten erfassen, die an Adobe Analytics gesendet werden sollen. Komponenten, die zum Sammeln von Analysedaten entwickelt wurden, speichern die Daten in den entsprechenden **CQ-Variable**. Wenn Sie solch eine Komponente zu einem Framework hinzufügen, zeigt das Framework die Liste der CQ-Variablen an, sodass Sie jede Variable der entsprechenden **Analytics-Variablen** zuordnen können.

![aa-11](assets/aa-11.png)

Wenn die **AEM-Ansicht** geöffnet ist, werden die Analytics-Variablen im Content Finder angezeigt.

![aa-12](assets/aa-12.png)

Sie können auch mehrere Analytics-Variablen derselben **CQ-Variablen** zuordnen.

![chlimage_1-68](assets/chlimage_1-68.png)

Die zugeordneten Daten werden an Adobe Analytics gesendet, wenn die Seite geladen wird und die folgenden Bedingungen erfüllt sind:

* Die Seite ist mit dem Framework verknüpft.
* Die Seite verwendet die Komponenten, die dem Framework hinzugefügt werden.

Mit der folgenden Vorgehensweise können Sie Variablen von CQ-Komponenten den Eigenschaften von Adobe Analytics-Berichten zuordnen.

1. Ziehen Sie in der **AEM-Ansicht** eine Tracking-Komponente vom Sidekick auf das Framework. Ziehen Sie beispielsweise die **Seite** -Komponente aus **Allgemein** Kategorie.

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
   >Sie können mehrere Analytics-Variablen zuordnen (z. B. `props`, `eVars`, `events`) auf dieselbe CQ-Variable (z. B. `pagedata.title`)

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

1. Abhängig von der verwendeten Adobe Analytics-Version müssen Sie durchschnittlich 45 Minuten warten, bis der Bericht mit dem verwendeten Suchbegriff aktualisiert wird. Beispiel: Aubergine im Beispiel

## Verwenden des Content Finder (cf#) mit Adobe Analytics-Frameworks {#using-the-content-finder-cf-with-adobe-analytics-frameworks}

Wenn Sie ein Adobe Analytics-Framework zum ersten Mal öffnen, enthält der Content Finder vordefinierte Analytics-Variablen unter:

* Traffic
* Konversion
* Ereignisse

Wenn Sie eine RSID auswählen, werden alle zu dieser RSID gehörenden Variablen zur Liste hinzugefügt.\
Die `cf#` ist erforderlich, um Analytics-Variablen den CQ-Variablen zuzuordnen, die in den verschiedenen Tracking-Komponenten vorhanden sind. Siehe „Einrichten eines Frameworks für das grundlegende Tracking“.

Je nach für das Framework ausgewählter Ansicht enthält der Content Finder entweder Analytics-Variablen (in der AEM-Ansicht) oder CQ-Variablen (in der Analytics-Ansicht).

Die Liste kann wie folgt bearbeitet werden:

1. Wann **AEM** kann die Liste anhand der drei Filterschaltflächen nach ausgewähltem Variablentyp gefiltert werden:

   * Wenn die *Schaltfläche „Nein“* ausgewählt ist, wird die komplette Liste angezeigt.
   * Wenn die Schaltfläche **Traffic** ausgewählt ist, werden in der Liste nur die Variablen angezeigt, die zum Bereich „Traffic“ gehören.
   * Wenn die Schaltfläche **Konversion** ausgewählt ist, werden in der Liste nur die Variablen angezeigt, die zum Bereich „Konversion“ gehören.
   * Wenn die Variable **Veranstaltungen** ausgewählt ist, werden in der Liste nur die Variablen angezeigt, die zum Bereich Ereignisse gehören.

   >[!NOTE]
   >
   >Sie können immer nur eine Filterschaltfläche aktivieren.

   1. Die Liste verfügt außerdem über eine Suchfunktion, mit der die Elemente nach dem im Suchfeld eingegebenen Text gefiltert werden.
   1. Wenn bei der Suche nach Elementen in der Liste eine Filteroption aktiviert ist, werden die angezeigten Ergebnisse auch nach der aktiven Schaltfläche gefiltert.
   1. Die Liste kann jederzeit mit der Schaltfläche mit den kreisförmigen Pfeilen neu geladen werden.
   1. Wenn mehrere RSIDs im Framework ausgewählt sind, werden alle Variablen in der Liste mit allen Beschriftungen angezeigt, die innerhalb der ausgewählten RSIDs verwendet werden.

1. In der Adobe Analytics-Ansicht zeigt der Content Finder alle CQ-Variablen an, die zu den Tracking-Komponenten gehören, die in die CQ-Ansicht gezogen wurden.

   * Beispiel: Wenn die Variable **Komponente herunterladen** ist die *nur eine gezogen* in der CQ-Ansicht (die über zwei zuordnbare Variablen verfügt) *eventdata.downloadLink* und *eventdata.events.startDownload*), sieht der Content Finder beim Wechsel zur Adobe Analytics-Ansicht wie folgt aus:

   ![aa-22](assets/aa-22.png)

   * Die Variablen können per Drag-and-Drop auf eine beliebige Adobe Analytics-Variable gezogen werden, die zu einem der drei Variablenabschnitte (**Traffic**, **Konversion** und **Veranstaltungen**).

   * Wenn Sie in der CQ-Ansicht eine neue Tracking-Komponente auf das Framework ziehen, werden die zur Komponente gehörenden CQ-Variablen automatisch zum Content Finder (cf#) in der Adobe Analytics-Ansicht hinzugefügt.

   >[!NOTE]
   >
   >Es kann immer nur eine CQ-Variable einer Adobe Analytics-Variablen zugeordnet werden.

## Verwenden der AEM-Ansicht und der Analytics-Ansicht {#using-aem-view-and-analytics-view}

Benutzer können jederzeit zwischen zwei Möglichkeiten wechseln, die Adobe Analytics-Zuordnungen auf einer Framework-Seite anzuzeigen. Die beiden Ansichten bieten aus zwei unterschiedlichen Perspektiven einen besseren Überblick über die Zuordnungen innerhalb des Frameworks.

### AEM {#aem-view}

![aa-23](assets/aa-23.png)

Wenn Sie das obige Bild als Beispiel verwenden, wird das **AEM** weist die folgenden Eigenschaften auf:

1. Dies ist die Standardansicht beim Öffnen des Frameworks.
1. Linke Seite: Der Content Finder (cf#) zeigt basierend auf den ausgewählten RSIDs die Adobe Analytics-Variablen an.
1. Registerkartenkopfzeilen (**AEM-Ansicht** und **Analytics-Ansicht**): Verwenden Sie diese, um zwischen den beiden Ansichten zu wechseln.

1. **AEM-Ansicht**:

   1. Wenn das Framework Komponenten enthält, die von seinem übergeordneten Framework vererbt werden, werden sie hier aufgeführt, zusammen mit den den Komponenten zugeordneten Variablen.

      1. Vererbte Komponenten sind gesperrt.
      1. Doppelklicken Sie zum Entsperren einer geerbten Komponente auf das Vorhängeschloss neben dem Namen der Komponente
      1. Um die Vererbung wiederherzustellen, löschen Sie die entsperrte Komponente. danach wird er wieder gesperrt.

   1. **Komponenten hierher ziehen, um sie in das Analytics-Framework einzuschließen**: Komponenten können aus dem Sidekick gezogen und hier abgelegt werden.
   1. Sie finden alle Komponenten, die derzeit im Analytics-Framework enthalten sind:

      1. Um eine Komponente hinzuzufügen, ziehen Sie sie aus der Registerkarte Komponenten des Sidekicks
      1. Um eine Komponente und alle zugehörigen Zuordnungen zu löschen, wählen Sie im Kontextmenü der Komponente die Option „Löschen“ und akzeptieren Sie den Löschvorgang im Bestätigungsdialogfeld.
      1. Beachten Sie, dass eine Komponente nur aus dem Framework gelöscht werden kann, in dem sie erstellt wurde, und nicht aus untergeordneten Frameworks im herkömmlichen Sinne gelöscht werden kann (sie kann nur überschrieben werden).

### Analytics-Ansicht {#analytics-view}

![aa-24](assets/aa-24.png)

1. Um auf diese Ansicht zuzugreifen, wechseln Sie im Framework zur Registerkarte **Analytics-Ansicht**.
1. Linke Seite: Content Finder (cf#) wird von CQ-Variablen basierend auf den Komponenten, die in der CQ-Ansicht auf das Framework gezogen wurden, gefüllt.
1. Registerkartenkopfzeilen (**AEM-Ansicht** und **Analytics-Ansicht**): Verwenden Sie diese, um zwischen den beiden Ansichten zu wechseln.

1. In den drei Tabellen („Traffic“, „Konversion“, „Ereignis“) sind alle verfügbaren Adobe Analytics-Variablen aufgeführt, die zu den ausgewählten RSIDs gehören. Die hier gezeigten Zuordnungen sollten mit denen in der AEM übereinstimmen:

   * **Traffic**:

      * Traffic-Variable (`prop1`), die einer CQ-Variablen (`eventdata.downloadLink`) zugeordnet ist

      * Wenn neben der Komponente ein Vorhängeschloss steht, bedeutet dies, dass sie von einem übergeordneten Framework übernommen wird und daher nicht bearbeitet werden kann

   * **Konversion**:

      * Konversionsvariable (`eVar1`), die einer CQ-Variablen (`pagedata.title`) zugeordnet ist

      * Konversionsvariable ( `eVar3`), die einem inline hinzugefügten JavaScript-Ausdruck zugeordnet sind, indem Sie auf das CQ-Variablenfeld doppelklicken und den Code manuell eingeben

   * **Ereignis**:

      * Ereignisvariable (`event1`), die einem CQ-Ereignis (`eventdata.events.pageView`) zugeordnet ist

>[!NOTE]
>
>Die Spalte &quot;CQ-Variable&quot;einer beliebigen Tabelle kann auch inline ausgefüllt werden, indem Sie auf das Feld doppelklicken und Text hinzufügen. Diese Felder akzeptieren JavaScript als Eingabe.
>
>Beispiel: Neben `prop3` können Sie Folgendes hinzufügen:
>     `'`* `Adobe:'+pagedata.title+':'+pagedata.sitesection`\
, um den *Titel* einer Seite und ihre *sitesection* verkettet mit einem *:* (Doppelpunkt) und mit dem Präfix *Adobe* als `prop3` zu übermitteln.
>

>[!CAUTION]
>
Es kann immer nur eine CQ-Variable einer Adobe Analytics-Variablen zugeordnet werden.
