---
title: Optimierte Smart-Tags
description: Optimierte Smart-Tags
contentOwner: AG
translation-type: tm+mt
source-git-commit: e124025295f29d6f3999dc52467301d48bceee75
workflow-type: tm+mt
source-wordcount: '1525'
ht-degree: 65%

---


# Intelligente Tags verstehen, anwenden und kuratieren {#enhanced-smart-tags}

Organisationen, die mit digitalen Assets arbeiten, verwenden zunehmend taxonomiegesteuertes Vokabular in Asset-Metadaten. Im Grunde umfasst dieses eine Liste von Schlüsselbegriffen, die Mitarbeiter, Partner und Kunden häufig verwenden, um sich auf digitale Assets einer bestimmten Klasse zu beziehen und nach diesen zu suchen. Das Tagging mit einem taxonomiegesteuerten Vokabular stellt sicher, dass diese Begriffe im Rahmen von Tag-basierten Suchen einfach identifiziert und abgerufen werden können.

Verglichen mit dem Vokabular natürlicher Sprachen hilft das Tagging digitaler Assets anhand einer Geschäftstaxonomie dabei, sie am Geschäft eines Unternehmens auszurichten, und stellt dabei sicher, dass nur die relevantesten Assets bei der Suche angezeigt werden.

So könnte beispielsweise ein Automobilhersteller Bilder von Autos mit Tags versehen, die die Modellnamen darstellen, sodass nur relevante Bilder angezeigt werden, wenn für das Erstellen einer Werbekampagne nach verschiedenen Modellen gesucht wird.

Damit der Smart Content Service die richtigen Tags anwendet, müssen Sie ihn darauf trainieren, Ihre Taxonomie zu erkennen. Um den Dienst zu trainieren, müssen Sie zunächst einen Satz von Assets sowie Tags kuratieren, die diese Assets bestmöglich beschreiben. Wenden Sie diese Tags auf die Assets an und führen Sie einen Trainings-Workflow aus, damit der Dienst lernen kann.

Sobald ein Tag trainiert wurde und bereit ist, kann der Dienst dieses Tag über einen Tagging-Workflow auf Assets anwenden.

Im Hintergrund verwendet der Smart Content Service das Adobe Sensei AI-Framework, um seinen Bilderkennungsalgorithmus auf Ihre Tag-Struktur und Ihre Geschäftstaxonomie zu trainieren. Diese Content-Intelligenz wird dann verwendet, um relevante Tags auf einen anderen Satz von Assets anzuwenden.

Smart Content Service is a cloud service that is hosted on Adobe I/O. To use it in [!DNL Adobe Experience Manager], the system administrator must integrate your [!DNL Experience Manager] deployment with Adobe I/O.

Die wichtigsten Schritte beim Verwenden des Smart Content Service sind:

* Einstieg
* Überprüfung von Assets und Tags (Taxonomiedefinition)
* Training des Smart Content Service
* Automatisches Tagging

![Flussdiagramm](assets/flowchart.gif)

## Voraussetzungen {#prerequisites}

Stellen Sie vor der Verwendung des Smart Content Service Folgendes sicher, um eine Integration in Adobe I/O zu erstellen:

* Es ist ein Adobe ID-Konto mit Administratorrechten für die Organisation vorhanden.
* Der Smart Content Service ist für Ihre Organisation aktiviert.
* Das Smart Content Services-Basispaket kann nur einer Bereitstellung hinzugefügt werden, für die ein [!DNL Sites] Basispaket und [!DNL Assets] Add-On lizenziert wurden.

## Einstieg {#onboarding}

The Smart Content Service is available for purchase as an add-on to [!DNL Experience Manager]. Nach dem Kauf wird eine E-Mail mit einem Link zur Adobe-E/A an den Administrator Ihres Unternehmens gesendet.

The administrator can follow the link to integrate the Smart Content Service with [!DNL Experience Manager]. To integrate the service with [!DNL Experience Manager Assets], see [Configure Smart Tags](config-smart-tagging.md).

The onboarding process is complete when the administrator configures the service and adds users in [!DNL Experience Manager].

>[!NOTE]
>
>Wenn Sie [!DNL Experience Manager] 6.3 oder eine frühere Version verwenden und einen Tagging-Dienst für Ihre Assets benötigen, finden Sie weitere Informationen unter [Smart-Tags](https://helpx.adobe.com/experience-manager/6-3/assets/using/touch-ui-smart-tags.html). Intelligente Tags verwenden nicht die neuesten AI-Funktionen und sind daher weniger genau als der erweiterte Dienst für intelligentes Tagging.

## Überprüfen von Assets und Tags {#reviewing-assets-and-tags}

Nachdem Sie sich an Bord befinden, sollten Sie als Erstes eine Reihe von Tags identifizieren, die diese Bilder am besten im Kontext Ihres Unternehmens beschreiben.

Stellen Sie dann einen Satz mit Bildern zusammen, die Ihr Produkt bestmöglich für eine bestimmte Geschäftsanforderung darstellen. Stellen Sie sicher, dass die Assets in Ihrem Satz den [Richtlinien für das Trainieren des Smart Content Service](/help/assets/config-smart-tagging.md#training-the-smart-content-service) entsprechen.

Fügen Sie die Assets einem Ordner hinzu und wenden Sie die Tags über die Eigenschaftsseite auf die einzelnen Assets an. Führen Sie anschließend den Trainings-Workflow für diesen Ordner aus. Mit dem Asset-Satz kann der Smart Content Service mithilfe Ihrer Taxonomiedefinitionen mehr Assets effektiv trainieren.

>[!NOTE]
>
>1. Das Training ist ein unwiderruflicher Vorgang. Adobe empfiehlt Ihnen, die Tags im Asset-Satz zu überprüfen, bevor Sie den Smart Content Service mit den Tags trainieren.
>1. Bevor Sie eine Schulung für ein Tag durchführen, lesen Sie die Schulungsrichtlinien für [Smart Content Service](/help/assets/config-smart-tagging.md#training-the-smart-content-service).
>1. Adobe empfiehlt Ihnen, mindestens zwei unterschiedliche Tags zu verwenden, wenn Sie den Smart Content Service zum ersten Mal trainieren.


## Understand [!DNL Experience Manager] search results with smart tags {#understandsearch}

By default, [!DNL Experience Manager] search combines the search terms with an `AND` clause. Dieses Standardverhalten ändert sich durch die Verwendung von Smart-Tags nicht. Durch die Verwendung von Smart-Tags wird eine zusätzliche `OR`-Klausel hinzugefügt. Damit wird jeder Suchbegriff aus den angewandten Smart-Tags gefunden. Suchen Sie beispielsweise nach `woman running`. Assets, die in den Metadaten nur das Schlüsselwort `woman`oder `running` aufweisen, werden standardmäßig nicht in den Suchergebnissen angezeigt. Ein Asset, das über Smart-Tags mit `woman` oder `running` getaggt wurde, wird bei dieser Suchanfrage jedoch angezeigt. Die Suchergebnisse sind also eine Kombination aus

* Assets mit den Keywords `woman` und `running` in den Metadaten.

* Assets, die über Smart-Tags mit einem der Schlüsselwörter getaggt wurden.

Die Suchergebnisse, die in Metadatenfeldern alle Suchbegriffe aufweisen, werden zuerst angezeigt. Danach folgen die Suchergebnisse, die einem oder mehr Suchbegriffen in den Smart-Tags entsprechen. Im obigen Beispiel werden die Suchergebnisse ungefähr in dieser Reihenfolge angezeigt:

1. Treffer von `woman running` in den verschiedenen Metadatenfeldern.
1. Treffer von `woman running` in den Smart-Tags,
1. Treffer von `woman` oder `running` in Smart-Tags.

>[!CAUTION]
>
>Wenn die Lucene-Indizierung abgeschlossen ist, funktioniert [!DNL Adobe Experience Manager] die Suche auf der Grundlage von Smart-Tags nicht wie erwartet.

## Assets automatisch taggen {#tagging-assets-automatically}

Wenn Sie den Smart Content Service trainiert haben, können Sie den Tagging-Workflow starten, um automatisch passende Tags auf einen anderen Satz ähnlicher Assets anzuwenden.

Sie können den Tagging-Workflow periodisch oder nur bei Bedarf ausführen.

>[!NOTE]
>
>Der Tagging-Workflow wird sowohl für Assets als auch für Ordner ausgeführt.

### Periodisches Tagging {#periodic-tagging}

Sie können bestimmen, dass der Smart Content Service Assets in einem Ordner regelmäßig mit Tags versehen soll. Open the properties page of your asset folder, select **[!UICONTROL Enable Smart Tags]** under the **[!UICONTROL Details]** tab, and save the changes.

Wenn diese Option für einen Ordner ausgewählt ist, werden die Assets im Ordner vom Smart Content Service automatisch mit Tags versehen. Standardmäßig wird der Tag-Tag um 12:00 Uhr ausgeführt.

### Tagging bei Bedarf {#on-demand-tagging}

Sie können den Tag-Arbeitsablauf über die Arbeitsablaufkonsole oder die Zeitleiste auslösen, um Ihre Assets sofort zu taggen.

>[!NOTE]
>
>Wenn Sie den Tagging-Workflow über die Timeline ausführen, können Sie Tags gleichzeitig auf maximal 15 Assets anwenden.

#### Tagging von Assets über die Workflow-Konsole {#tagging-assets-from-the-workflow-console}

1. In [!DNL Experience Manager] interface, go to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Wählen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** den Workflow **[!UICONTROL DAM Smart Tags Assets]** aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Workflow starten]**.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. Suchen Sie im Dialogfeld **[!UICONTROL Workflow ausführen]** den Payload-Ordner mit den Assets, auf die Sie automatisch Tags anwenden möchten.
1. Geben Sie einen Titel für den Workflow und optional einen Kommentar an. Klicken Sie auf **[!UICONTROL Ausführen]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   Navigieren Sie zum Asset-Ordner und prüfen Sie die Tags, um sicherzustellen, dass der Smart Content Service Ihre Assets ordnungsgemäß mit Tags versehen hat.

#### Tagging von Assets über die Timeline {#tagging-assets-from-the-timeline}

1. From the [!DNL Assets] user interface, select the folder containing assets or specific assets to which you want to apply smart tags.
1. Öffnen Sie die **[!UICONTROL Timeline]** oben links.
1. Öffnen Sie die Aktionen unten in der linken Seitenleiste und klicken Sie auf **[!UICONTROL Workflow starten]**.

   ![start_workflow](assets/start_workflow.png)

1. Wählen Sie den Workflow **[!UICONTROL DAM Smart-Tag-Assets]** aus und geben Sie einen Titel für den Workflow an.
1. Klicken Sie auf **[!UICONTROL Starten]**. Der Workflow wendet Ihre Tags auf Assets an. Navigieren Sie zum Asset-Ordner und prüfen Sie die Tags, um sicherzustellen, dass der Smart Content Service Ihre Assets ordnungsgemäß mit Tags versehen hat.

>[!NOTE]
>
>In den nachfolgenden Tagging-Zyklen werden nur die geänderten Assets erneut mit neu trainierten Tags markiert. Selbst unveränderte Assets werden jedoch markiert, wenn das Intervall zwischen dem letzten und dem aktuellen Tagging-Zyklus des Tagging-Workflows 24 Stunden überschreitet. Bei periodischen Tagging-Workflows werden unveränderte Assets mit Tags versehen, wenn das Intervall 6 Monate überschreitet.

## Kuratieren oder Moderieren der angewendeten Smarttags {#manage-smart-tags}

Sie können Smart-Tags kuratieren, um alle falschen Tags zu entfernen, die Ihren Markenbildern zugewiesen wurden, sodass nur die relevantesten Tags angezeigt werden.

Mithilfe der Moderation von Smart-Tags können Sie Tag-basierte Suchen nach Bildern verfeinern, indem Sie sicherstellen, dass Ihr Bild nur in den Suchergebnissen für die relevantesten Tags angezeigt wird. Im Grunde wird so ausgeschlossen, dass in den Suchergebnissen Bilder ohne Bezug angezeigt werden.

Darüber hinaus können Sie Tags einen höheren Rang zuweisen, um ihre Relevanz in Bezug auf ein Bild zu erhöhen. Je höher der Rang eines Tags für ein Bild, desto wahrscheinlicher ist bei einer Tag-basierten Suche die Aufnahme des Bildes in die Suchergebnisse.

1. Suchen Sie im OmniSearch-Feld nach Assets, die auf einem Tag basieren.
1. Prüfen Sie die Suchergebnisse auf Bilder, die Ihnen für Ihren Suchvorgang nicht relevant erscheinen.
1. Select the image, and click **[!UICONTROL Manage Tags]** from the toolbar.
1. Prüfen Sie die Tags auf der Seite **[!UICONTROL Tags verwalten]**. If you don&#39;t want the image to be searched based on a specific tag, select the tag and then click **[!UICONTROL Delete]** from the toolbar. Alternativ können Sie auf `x` das Symbol klicken, das neben einem Tag angezeigt wird.
1. Optionally, to assign a higher rank to a tag, select the tag and click **[!UICONTROL Promote]** from the toolbar. Das höhergestufte Tag wird in den Abschnitt **[!UICONTROL Tags]** verschoben.
1. Click **[!UICONTROL Save]** and then click **[!UICONTROL OK]**
1. Navigate to the **[!UICONTROL Properties]** page for the image. Achten Sie darauf, dass dem von Ihnen beworbenen Tag mehr Relevanz zugewiesen wird und es früher in den Suchergebnissen angezeigt wird.

## Tipps und Einschränkungen {#tips-best-practices-limitations}

* Die Verwendung von Smart Content Services ist auf bis zu 2 Millionen getaggte Bilder pro Jahr beschränkt. Alle verarbeiteten und mit Tags versehenen Duplikat-Bilder werden als getaggte Bilder gezählt.
* Wenn Sie den Tagging-Workflow über die Timeline ausführen, können Sie Tags gleichzeitig auf maximal 15 Assets anwenden.
