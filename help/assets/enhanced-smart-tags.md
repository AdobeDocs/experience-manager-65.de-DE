---
title: Optimierte Smart-Tags
description: Optimierte Smart-Tags
contentOwner: AG
feature: Smart Tags, Search
role: User
exl-id: 5eff4a0f-30b1-4753-ad0b-002656eed972
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 5aff321eb52c97e076c225b67c35e9c6d3371154
workflow-type: tm+mt
source-wordcount: '1581'
ht-degree: 100%

---

# Smart-Tags verstehen, anwenden und kuratieren {#enhanced-smart-tags}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/smart-tags.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Organisationen, die mit digitalen Assets arbeiten, verwenden zunehmend taxonomiegesteuertes Vokabular in Asset-Metadaten. Im Wesentlichen handelt es sich um eine Liste von Schlüsselwörtern, die Angestellte, Partner bzw. Partnerinnen und Kunden bzw. Kundinnen üblicherweise verwenden, um sich auf digitale Assets einer bestimmten Klasse zu beziehen und danach zu suchen. Das Tagging von Assets mit taxonomiegesteuertem Vokabular stellt sicher, dass die Assets leicht identifiziert und abgerufen werden können.

Verglichen mit dem Vokabular natürlicher Sprachen hilft das Tagging digitaler Assets anhand einer Geschäftstaxonomie dabei, sie am Geschäft eines Unternehmens auszurichten, und stellt dabei sicher, dass nur die relevantesten Assets bei der Suche angezeigt werden.

So könnte beispielsweise ein Automobilhersteller Bilder von Autos mit Tags versehen, die die Modellnamen darstellen, sodass nur relevante Bilder angezeigt werden, wenn für das Erstellen einer Werbekampagne nach verschiedenen Modellen gesucht wird.

Damit der Smart Content Service die richtigen Tags anwendet, müssen Sie ihn darauf trainieren, Ihre Taxonomie zu erkennen. Um den Dienst zu trainieren, müssen Sie zunächst einen Satz von Assets sowie Tags kuratieren, die diese Assets bestmöglich beschreiben. Um den Service beim Lernen zu unterstützen, sollten Sie diese Tags auf die Assets anwenden und einen Trainings-Workflow durchführen.

Sobald ein Tag trainiert wurde und bereit ist, kann der Dienst dieses Tag über einen Tagging-Workflow auf Assets anwenden.

Im Hintergrund verwendet der Smart Content Service das KI-Framework von Adobe Sensei und trainiert damit seinen Bilderkennungsalgorithmus auf die Tag-Struktur und Taxonomie Ihres Unternehmens. Diese Content-Intelligenz wird dann verwendet, um relevante Tags auf einen anderen Satz von Assets anzuwenden.

Smart Content Service ist ein Cloud-Service, der auf [!DNL Adobe Developer Console] gehostet wird. Um ihn in [!DNL Adobe Experience Manager] zu verwenden, muss die bzw. der Systemadmin Ihre [!DNL Experience Manager]-Bereitstellung mit [!DNL Adobe Developer Console] integrieren.

Zusammenfassend sind hier die wichtigsten Schritte zur Verwendung des Smart Content Service aufgeführt:

* Onboarding
* Überprüfen von Assets und Tags (Taxonomiedefinition)
* Trainieren des Smart Content Service
* Automatisches Tagging

![Flussdiagramm](assets/flowchart.gif)

## Voraussetzungen und unterstützte Formate {#prerequisites}

Stellen Sie vor der Verwendung des Smart Content Service Folgendes sicher, um eine Integration in [!DNL Adobe Developer Console] zu erstellen:

* Ein Adobe ID-Konto mit Administratorrechten für die Organisation.
* Aktivieren Sie den Smart Content Service-Service für Ihre Organisation.
* Um das Smart Content Services-Basispaket zu einer Bereitstellung hinzuzufügen, lizenzieren Sie das Basispaket [!DNL Adobe Experience Manager Sites] und das Add-on [!DNL Assets].

Der Service wendet Smart-Tags auf Assets der folgenden MIME-Typen an:

* `image/jpeg`
* `image/tiff`
* `image/png`
* `image/bmp`
* `image/gif`
* `image/pjpeg`
* `image/x-portable-anymap`
* `image/x-portable-bitmap`
* `image/x-portable-graymap`
* `image/x-portable-pixmap`
* `image/x-rgb`
* `image/x-xbitmap`
* `image/x-xpixmap`
* `image/x-icon`
* `image/photoshop`
* `image/x-photoshop`
* `image/psd`
* `image/vnd.adobe.photoshop`

Der Service wendet Smart-Tags auf Asset-Ausgabedarstellungen der folgenden MIME-Typen an:

* `image/jpeg`
* `image/pjpeg`
* `image/png`

## Onboarding {#onboarding}

Der Smart Content Service kann als Add-on zu [!DNL Experience Manager] erworben werden. Nach dem Kauf wird eine E-Mail mit einem Link zu [!DNL Adobe I/O] an die oder den Admin Ihres Unternehmens gesendet. 

Die bzw. der Admin kann über diesen Link den Smart Content Service mit [!DNL Experience Manager] integrieren. Weitere Informationen zum Integrieren des Services mit [!DNL Experience Manager Assets] finden Sie im Abschnitt [Konfigurieren von Smart-Tags](config-smart-tagging.md).

Das Onboarding ist abgeschlossen, wenn die bzw. der Admin den Service konfiguriert und Benutzende in [!DNL Experience Manager] hinzufügt.

## Überprüfen von Assets und Tags {#reviewing-assets-and-tags}

Nach dem Onboarding sollten Sie zunächst einen Satz von Tags definieren, die diese Bilder im Kontext Ihres Geschäftsfeldes bestmöglich beschreiben.

Stellen Sie dann einen Satz mit Bildern zusammen, die Ihr Produkt bestmöglich für eine bestimmte Geschäftsanforderung darstellen. Stellen Sie sicher, dass die Assets in Ihrem Satz den [Richtlinien für das Trainieren des Smart Content Service](/help/assets/config-smart-tagging.md#training-the-smart-content-service) entsprechen.

Fügen Sie die Assets zu einem Ordner hinzu und wenden Sie die Tags auf jedes Asset auf der Eigenschaftenseite an. Führen Sie dann den Trainings-Workflow für diesen Ordner aus. Der kuratierte Satz von Assets ermöglicht es dem Smart Content Service, mithilfe Ihrer Taxonomiedefinitionen effektiv mehr Assets zu trainieren.

>[!NOTE]
>
>1. Training ist ein unwiderruflicher Prozess. Adobe empfiehlt Ihnen, die Tags im Asset-Satz zu überprüfen, bevor Sie den Smart Content Service mit den Tags trainieren.
>1. Bevor Sie ein Tag trainieren, lesen Sie [Trainings-Richtlinien für den Smart Content Service](/help/assets/config-smart-tagging.md#training-the-smart-content-service).
>1. Adobe empfiehlt Ihnen, mindestens zwei unterschiedliche Tags zu verwenden, wenn Sie den Smart Content Service zum ersten Mal trainieren.

## Grundlegendes zu [!DNL Experience Manager]-Suchergebnissen mit Smart-Tags {#understandsearch}

Die [!DNL Experience Manager]-Suche kombiniert die Suchbegriffe standardmäßig mit einer `AND`-Klausel. Dieses Standardverhalten ändert sich durch die Verwendung von Smart-Tags nicht. Die Verwendung von Smart-Tags fügt eine zusätzliche `OR`-Klausel hinzu, um alle Suchbegriffe zu finden, die mit den Smart-Tags in Verbindung stehen. Suchen Sie beispielsweise nach `woman running`. Assets, die in den Metadaten nur das Keyword `woman`oder `running` aufweisen, werden standardmäßig nicht in den Suchergebnissen angezeigt. Ein Asset, das über Smart-Tags mit `woman` oder `running` getaggt wurde, wird bei dieser Suchanfrage jedoch angezeigt. Die Suchergebnisse sind also eine Kombination aus

* Assets mit den Keywords `woman` und `running` in den Metadaten.

* Assets, die über Smart-Tags mit einem der Keywords getaggt wurden.

Die Suchergebnisse, die in Metadatenfeldern alle Suchbegriffe aufweisen, werden zuerst angezeigt. Danach folgen die Suchergebnisse, die einem oder mehr Suchbegriffen in den Smart-Tags entsprechen. Im obigen Beispiel werden die Suchergebnisse ungefähr in dieser Reihenfolge angezeigt:

1. Treffer von `woman running` in den verschiedenen Metadatenfeldern.
1. Treffer von `woman running` in den Smart-Tags.
1. Treffer von `woman` oder `running` in Smart-Tags.

>[!CAUTION]
>
>Wenn die Lucene-Indizierung außerhalb von [!DNL Adobe Experience Manager] durchgeführt wird, funktioniert die Suche auf der Grundlage von Smart-Tags nicht wie erwartet.

## Automatisches Taggen von Assets {#tagging-assets-automatically}

Wenn Sie den Smart Content Service trainiert haben, können Sie den Tagging-Workflow starten, um automatisch passende Tags auf einen anderen Satz ähnlicher Assets anzuwenden.

Sie können den Tagging-Workflow periodisch oder nur bei Bedarf ausführen.

>[!NOTE]
>
>Der Tagging-Workflow wird sowohl für Assets als auch für Ordner ausgeführt.

### Regelmäßiges Tagging {#periodic-tagging}

Sie können den Smart Content Service aktivieren, um Assets in einem Ordner regelmäßig mit Tags zu versehen. Öffnen Sie die Eigenschaftsseite Ihres Asset-Ordners, wählen Sie **[!UICONTROL Smart-Tags aktivieren]** in der Registerkarte **[!UICONTROL Details]** aus und speichern Sie die Änderungen.

Wenn diese Option für einen Ordner ausgewählt ist, versieht der Smart Content Service die Assets innerhalb des Ordners automatisch mit Tags. Standardmäßig wird der Tagging-Workflow jeden Tag um 0:00 Uhr ausgeführt.

### Tagging bei Bedarf {#on-demand-tagging}

Sie können den Tagging-Workflow über die Workflow-Konsole oder die Zeitleiste auslösen, um Ihre Assets sofort mit Tags zu versehen.

>[!NOTE]
>
>Wenn Sie den Tagging-Workflow über die Zeitleiste ausführen, können Sie Tags gleichzeitig auf maximal 15 Assets anwenden.

#### Tagging von Assets über die Workflow-Konsole {#tagging-assets-from-the-workflow-console}

1. Gehen Sie in der [!DNL Experience Manager]-Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Wählen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** den Workflow **[!UICONTROL DAM Smart Tags Assets]** aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Workflow starten]**.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. Suchen Sie im Dialogfeld **[!UICONTROL Workflow ausführen]** den Payload-Ordner mit den Assets, auf die Sie automatisch Tags anwenden möchten.
1. Geben Sie einen Titel für den Workflow und optional einen Kommentar an. Klicken Sie auf **[!UICONTROL Ausführen]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   Um zu überprüfen, ob der Smart Content Service Ihre Assets ordnungsgemäß mit Tags versehen hat, gehen Sie zum Asset-Ordner und überprüfen Sie die Tags.

#### Tagging von Assets über die Zeitleiste {#tagging-assets-from-the-timeline}

1. Wählen Sie über die [!DNL Assets]-Benutzeroberfläche den Ordner mit Assets oder bestimmte Assets aus, auf die Sie Smart-Tags anwenden möchten.
1. Öffnen Sie die **[!UICONTROL Zeitleiste]** oben links.
1. Öffnen Sie die Aktionen unten in der linken Seitenleiste und klicken Sie auf **[!UICONTROL Workflow starten]**.

   ![start_workflow](assets/start_workflow.png)

1. Wählen Sie den Workflow **[!UICONTROL DAM Smart-Tag-Assets]** aus und geben Sie einen Titel für den Workflow an.
1. Klicken Sie auf **[!UICONTROL Starten]**. Der Workflow versieht die Assets mit Tags. Um zu überprüfen, ob der Smart Content Service Ihre Assets ordnungsgemäß mit Tags versehen hat, gehen Sie zum Asset-Ordner und überprüfen Sie die Tags.

>[!NOTE]
>
>In zukünftigen Tagging-Zyklen werden nur geänderte Assets mit neu trainierten Tags versehen. Allerdings werden auch unveränderte Assets mit Tags versehen, wenn das Intervall zwischen dem letzten und dem aktuellen Tagging-Zyklus für den Tagging-Workflow 24 Stunden überschreitet. Bei periodischen Tagging-Workflows werden unveränderte Assets mit Tags versehen, wenn das Intervall sechs Monate überschreitet.

## Kuratieren oder Moderieren der angewendeten Smart-Tags {#manage-smart-tags}

Sie können Smart-Tags kuratieren, um ungenaue Tags zu entfernen, die Ihren Markenbildern zugewiesen sind, damit nur die relevantesten Tags angezeigt werden.

Mithilfe der Moderation von Smart-Tags können Sie Tag-basierte Suchen nach Bildern verfeinern, indem Sie sicherstellen, dass Ihr Bild nur in den Suchergebnissen für die relevantesten Tags angezeigt wird. Damit wird verhindert, dass Bilder ohne Zusammenhang in den Suchergebnissen auftauchen.

Darüber hinaus können Sie Tags einen höheren Rang zuweisen, um ihre Relevanz in Bezug auf ein Bild zu erhöhen. Das Hochstufen eines Tags für ein Bild erhöht die Wahrscheinlichkeit, dass das Bild in den Suchergebnissen erscheint, wenn nach dem betreffenden Tag gesucht wird.

1. Suchen Sie im Suchfeld nach Assets, indem Sie ein Tag als Keyword verwenden.
1. Überprüfen Sie die Suchergebnisse, um Bilder zu ermitteln, die Sie für Ihre Suche nicht relevant finden.
1. Wählen Sie ein solches Bild aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Tags verwalten]**.
1. Prüfen Sie die Tags auf der Seite **[!UICONTROL Tags verwalten]**. Wenn Sie nicht möchten, dass das Bild anhand eines bestimmten Tags gesucht wird, wählen Sie das Tag aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Löschen]**. Klicken Sie alternativ auf das `x`-Symbol, das neben einem Tag angezeigt wird.
1. Wenn Sie einem Tag einen höheren Rang zuweisen möchten, wählen Sie optional den Tag aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Hochstufen]**. Das höhergestufte Tag wird in den Abschnitt **[!UICONTROL Tags]** verschoben.
1. Klicken Sie auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL OK]**.
1. Gehen Sie zur Seite **[!UICONTROL Eigenschaften]** des betreffenden Bildes. Beachten Sie, dass das hochgestufte Tag eine hohe Relevanz erhält und es aus diesem Grund höher in den Suchergebnissen angezeigt wird.

## Tipps und Einschränkungen {#tips-best-practices-limitations}

* Verwenden Sie zum Trainieren des Modells die am besten geeigneten Bilder. Das Training kann nicht rückgängig gemacht werden, das Trainings-Modell kann nicht entfernt werden. Ihre Tagging-Genauigkeit hängt von der aktuellen Schulung ab. Gehen Sie daher sorgfältig vor.
* Die Nutzung des Smart Content Services ist auf bis zu 2 Millionen getaggte Bilder pro Jahr beschränkt. Alle doppelten Bilder, die verarbeitet und mit Tags versehen werden, werden als getaggtes Bild gezählt.
* Wenn Sie den Tagging-Workflow über die Zeitleiste ausführen, können Sie Tags gleichzeitig auf maximal 15 Assets anwenden.
* Smart-Tags funktionieren nur für die Bildformate PNG und JPG. Unterstützte Assets, deren Ausgabedarstellungen in diesen beiden Formaten erstellt wurden, werden also mit Smart Tags versehen.

>[!MORELIKETHIS]
>
>* [Überblick über Smart-Tags und deren Training](enhanced-smart-tags.md)
>* [Konfigurieren des Smart-Tagging](config-smart-tagging.md)
>* [Fehlerbehebung für Smart-Tags hinsichtlich OAuth-Anmeldedaten](config-oauth.md)
>* [Video-Tutorial zu Smart-Tags](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/image-smart-tags.html?lang=de)
