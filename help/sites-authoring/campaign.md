---
title: Arbeiten mit Adobe Campaign Classic und Adobe Campaign Standard
description: Sie können E-Mail-Inhalte in AEM erstellen und diese in Adobe Campaign-E-Mails verarbeiten
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
exl-id: d7e4d424-0ca7-449f-95fb-c4fe19dd195d
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '2770'
ht-degree: 93%

---

# Arbeiten mit Adobe Campaign Classic und Adobe Campaign Standard{#working-with-adobe-campaign-classic-and-adobe-campaign-standard}

Sie können E-Mail-Inhalte in AEM erstellen und diese in Adobe Campaign-E-Mails verarbeiten. Gehen Sie dazu wie folgt vor:

1. Erstellen Sie einen Newsletter in AEM aus einer Adobe Campaign-spezifischen Vorlage.
1. Wählen Sie [einen Adobe Campaign-Service](#selecting-the-adobe-campaign-cloud-service-and-template) aus, bevor Sie die Inhalte bearbeiten, um Zugriff auf alle Funktionen zu erhalten.
1. Bearbeiten Sie den Inhalt.
1. Überprüfen Sie den Inhalt.

Der Inhalt kann anschließend mit einer Bereitstellung in Adobe Campaign synchronisiert werden. Detaillierte Anweisungen finden Sie in diesem Dokument.

Siehe auch [Erstellen von Adobe Campaign-Formularen in AEM](/help/sites-authoring/adobe-campaign-forms.md).

>[!NOTE]
>
>Bevor Sie diese Funktion verwenden können, müssen Sie AEM so konfigurieren, dass es sich entweder mit [Adobe Campaign](/help/sites-administering/campaignonpremise.md) oder [Adobe Campaign Standard](/help/sites-administering/campaignstandard.md) integrieren lässt.

## Senden von E-Mail-Inhalten über Adobe Campaign {#sending-email-content-via-adobe-campaign}

Nachdem Sie AEM und Adobe Campaign konfiguriert haben, können Sie E-Mail-Versandinhalte direkt in AEM erstellen und sie dann in Adobe Campaign verarbeiten.

Wenn Sie Adobe Campaign-Inhalte in AEM erstellen, müssen Sie sich mit einem Adobe Campaign-Service verbinden, damit für die Bearbeitung der Inhalte sämtliche Funktionen bereitstehen.

Es gibt zwei mögliche Fälle:

* Inhalte können mit einem Versand aus Adobe Campaign synchronisiert werden. So können Sie AEM-Inhalte in einem Versand verwenden.
* (Nur Adobe Campaign Classic) Inhalte können direkt an Adobe Campaign gesendet werden, wodurch automatisch eine neue E-Mail-Bereitstellung generiert wird. Dieser Modus weist Einschränkungen auf.

Detaillierte Anweisungen finden Sie in diesem Dokument.

### Erstellen neuer E-Mail-Inhalte {#creating-new-email-content}

>[!NOTE]
>
>Stellen Sie sicher, dass E-Mail-Vorlagen unter **/content/campaigns** hinzugefügt werden, sodass sie sich verwenden lassen.

#### Erstellen neuer E-Mail-Inhalte {#creating-new-email-content-1}

1. Wählen Sie in AEM **Sites** und anschließend **Kampagnen** aus und navigieren Sie zu dem Ort, an dem Ihre E-Mail-Kampagnen verwaltet werden. Im folgenden Beispiel lautet der Pfad **Sites** > **Kampagnen** > **Geometrixx Outdoors** > **E-Mail-Kampagnen**.

   >[!NOTE]
   >
   >[E-Mail-Muster stehen nur in Geometrixx zur Verfügung](/help/sites-developing/we-retail.md). Laden Sie Beispielinhalt aus Package Share herunter.

   ![chlimage_1-15](assets/chlimage_1-15a.png)

1. Wählen Sie **Erstellen** und dann **Seite erstellen** aus.
1. Wählen Sie je nach der Adobe Campaign, mit der Sie sich verbinden möchten, eine der verfügbaren Vorlagen aus und klicken Sie auf **Weiter**. Standardmäßig sind drei Vorlagen verfügbar:

   * **Adobe Campaign Classic-E-Mail**: Hiermit können Sie einer Vorlage (mit zwei Spalten) eigene Inhalte hinzufügen, bevor sie zur Bereitstellung an Adobe Campaign Classic übermittelt wird.
   * **Adobe Campaign Standard-E-Mail**: Hiermit können Sie einer Vorlage (mit zwei Spalten) eigene Inhalte hinzufügen, bevor sie zur Bereitstellung an Adobe Campaign Standard übermittelt wird.

1. Geben Sie den **Titel** und optional die **Beschreibung** ein und klicken Sie auf **Erstellen**. Der Titel wird als Betreff des Newsletters/der E-Mail verwendet, falls er beim Bearbeiten der E-Mail nicht überschrieben wird.

### Auswählen des Adobe Campaign-Cloud-Service und der Vorlage {#selecting-the-adobe-campaign-cloud-service-and-template}

Zur Integration mit Adobe Campaign müssen Sie der Seite einen Adobe Campaign-Cloud-Service hinzufügen. Auf diese Weise erhalten Sie Zugriff auf Personalisierung und andere Adobe Campaign-Informationen.

Darüber hinaus müssen Sie möglicherweise auch die Adobe Campaign-Vorlage auswählen, den Betreff ändern und Textinhalte für die Benutzerinnen bzw. Benutzer hinzufügen, die die E-Mail nicht in HTML anzeigen.

Sie können den Cloud-Service entweder über die Registerkarte **Sites** oder aus der E-Mail/dem Newsletter auswählen, nachdem Sie diese(n) erstellt haben.

Die Auswahl des Cloud-Service über die Registerkarte **Sites** wird hierfür empfohlen. Die Auswahl des Cloud-Service über die E-Mail/den Newsletter ist ein deutlich komplizierteres Verfahren.

Auf der Seite **Sites**:

1. Wählen Sie in AEM die E-Mail-Seite aus und klicken Sie auf **Eigenschaften anzeigen**.

   ![chlimage_1-16](assets/chlimage_1-16a.png)

1. Wählen Sie **Bearbeiten** und anschließend die Registerkarte **Cloud-Services** aus und blättern Sie bis zum Ende. Klicken Sie auf das Pluszeichen (+), um eine Konfiguration hinzuzufügen, und wählen Sie dann **Adobe Campaign** aus.

   ![chlimage_1-17](assets/chlimage_1-17a.png)

1. Wählen Sie aus einer Dropdown-Liste die Konfiguration aus, die Ihrer Adobe Campaign-Konfiguration entspricht, und bestätigen Sie Ihre Auswahl durch einen Klick auf **Speichern**.
1. Sie können die auf die E-Mail angewendete Vorlage anzeigen, indem Sie auf die Registerkarte **Adobe Campaign** klicken. Möchten Sie die Vorlage wechseln, können Sie diese während der Bearbeitung in der E-Mail selbst ändern.

   Möchten Sie anstatt der Standardvorlage eine bestimmte E-Mail-Versandvorlage (aus Adobe Campaign) verwenden, wählen Sie unter **Eigenschaften** die Registerkarte **Adobe Campaign** aus. Geben Sie den internen Namen der E-Mail-Vorlage in der betreffenden Adobe Campaign-Instanz ein.

   Welche Vorlage Sie auswählen, bestimmt, welche Personalisierungsfelder in Adobe Campaign verfügbar sind.

   ![chlimage_1-18](assets/chlimage_1-18a.png)

Möglicherweise können Sie bei der Bearbeitung des Newsletters/der E-Mail aufgrund eines Layout-Problems den Adobe Campaign-Cloud-Service nicht direkt unter **Seiteneingenschaften** auswählen. Stattdessen können Sie dieses Problem wie folgt umgehen:

1. Wählen Sie in AEM die E-Mail-Seite aus und klicken Sie auf **Bearbeiten**. Klicken Sie auf **Eigenschaften öffnen**.

   ![chlimage_1-19](assets/chlimage_1-19a.png)

1. Wählen Sie **Cloud-Services** aus und klicken Sie auf **+**, um eine Konfiguration hinzufügen. Wählen Sie eine sichtbare Konfiguration aus (es spielt keine Rolle welche). Klicken Sie auf **+** signieren, um eine weitere Konfiguration hinzuzufügen, und wählen Sie dann **Adobe Campaign**.

   >[!NOTE]
   >
   >Alternativ können Sie die Cloud-Services durch Auswahl der Option **Eigenschaften anzeigen** auf der Registerkarte **Sites** auswählen.

1. Wählen Sie aus der Dropdown-Liste die Konfiguration aus, die Ihrer Adobe Campaign-Instanz entspricht, löschen Sie die erste erstellte Konfiguration, die nicht für Adobe Campaign war, und bestätigen Sie die Einstellungen durch einen Klick auf das Häkchen.
1. Fahren Sie nun mit Schritt 4 des zuvor beschriebenen Verfahrens fort, um eine Vorlage auszuwählen und einfachen Text hinzuzufügen.

### Bearbeiten von E-Mail-Inhalten {#editing-email-content}

So bearbeiten Sie E-Mail-Inhalte:

1. Beim Öffnen der E-Mail wechseln Sie automatisch in den Bearbeitungsmodus.

   ![chlimage_1-20](assets/chlimage_1-20a.png)

1. Möchten Sie den Betreff der E-Mail ändern oder für Benutzer, die die E-Mail nicht im HTML-Format anzeigen, einfachen Text hinzufügen, wählen Sie **E-Mail** aus und fügen Sie Betreff und Text hinzu. Wählen Sie das Seitensymbol aus, um automatisch aus der HTML-Version eine Version mit einfachem Text zu generieren. Klicken Sie nach Abschluss auf das Häkchen.

   Sie können den Newsletter mithilfe von Adobe Campaign-Personalisierungsfeldern personalisieren. Möchten Sie ein Personalisierungsfeld hinzufügen, klicken Sie auf die Schaltfläche mit dem Adobe Campaign-Logo, um die Auswahl für Personalisierungsfelder zu öffnen. Sie können dann aus allen Feldern auswählen, die für diesen Newsletter verfügbar sind.

   >[!NOTE]
   >
   >Wenn die Personalisierungsfelder in den Eigenschaften im Editor ausgegraut sind, überprüfen Sie Ihre Konfiguration erneut.

   ![chlimage_1-21](assets/chlimage_1-21a.png)

1. Öffnen Sie das Komponentenfeld auf der linken Bildschirmseite und wählen Sie **Adobe Campaign-Newsletter** aus dem Dropdown-Menü aus, um diese Komponenten zu finden.

   ![chlimage_1-22](assets/chlimage_1-22a.png)

1. Ziehen Sie die Komponenten direkt auf die Seite und bearbeiten Sie sie entsprechend. Sie können beispielsweise eine Komponente des Typs **Text und Personalisierung (Kampagne)** auf die Seite ziehen und personalisierten Text einfügen.

   ![chlimage_1-23](assets/chlimage_1-23a.png)

   Detaillierte Beschreibungen der Komponenten finden Sie unter [Adobe Campaign-Komponenten](/help/sites-authoring/adobe-campaign-components.md).

   ![chlimage_1-24](assets/chlimage_1-24a.png)

### Einfügen von Personalisierungen {#inserting-personalization}

Beim Bearbeiten Ihrer Inhalte können Sie Folgendes einfügen:

* Adobe Campaign-Kontextfelder. Hierbei handelt es sich um Felder, die Sie in Ihren Text einfügen können und die sich entsprechend den Empfängerdaten anpassen (z. B. Vorname, Nachname oder beliebige Daten der Zieldimension).
* Adobe Campaign-Personalisierungsblöcke. Hierbei handelt es sich um vordefinierte Inhaltsbausteine, die nicht mit den Empfängerdaten in Zusammenhang stehen, wie z. B. ein Markenlogo oder ein Link zu einer Mirrorseite.

Eine ausführliche Beschreibung der Campaign-Komponenten finden Sie unter [Adobe Campaign-Komponenten](/help/sites-authoring/adobe-campaign-components.md).

>[!NOTE]
>
>* Nur die Felder der Adobe Campaign-Zielgruppendimension **Profile** werden berücksichtigt.
>* Wenn Sie Eigenschaften von **Sites** anzeigen, haben Sie keinen Zugriff auf die Adobe Campaign-Kontextfelder. Sie können bei deren Bearbeitung direkt aus E-Mails darauf zugreifen.

So fügen Sie Personalisierung ein:

1. Fügen Sie eine neue Komponente aus **Newsletter-** > **Text und Personalisierung (Kampagne)** ein, indem Sie sie auf die Seite ziehen.

   ![chlimage_1-25](assets/chlimage_1-25a.png)

1. Öffnen Sie die Komponente, indem Sie auf das Stiftsymbol klicken. Der Editor für die Bearbeitung im Kontext wird geöffnet.

   ![chlimage_1-26](assets/chlimage_1-26a.png)

   >[!NOTE]
   >
   >**Für Adobe Campaign Standard:**
   >
   >* Die verfügbaren Kontextfelder entsprechen dem **Profil** der Zielgruppendimension in Adobe Campaign.
   >* Weitere Informationen finden Sie unter [Verknüpfen von AEM-Seiten mit Adobe Campaign-E-Mails](#linking-an-aem-page-to-an-adobe-campaign-email-adobe-campaign-standard).
   >
   >**Adobe Campaign Classic:**
   >
   >* Verfügbare Kontextfelder werden dynamisch aus dem Adobe Campaign-Schema **nms:seedMember** abgerufen. Erweiterungsdaten des Zieldatensatzes werden dynamisch aus dem Workflow abgerufen, der die mit dem Inhalt synchronisierte Bereitstellung enthält. (Siehe den Abschnitt [Synchronisieren von in AEM erstelltem Inhalt mit einer Bereitstellung von Adobe Campaign](#synchronizing-content-created-in-aem-with-a-delivery-from-adobe-campaign-classic).)
   >
   >* Informationen zum Hinzufügen oder Ausblenden von Personalisierungselementen finden Sie unter [Verwalten von Personalisierungsfeldern und -blöcken](/help/sites-administering/campaignonpremise.md#managing-personalization-fields-and-blocks).
   >* **Wichtig**: Alle Seed-Tabellenfelder müssen sich ebenfalls in der Empfängertabelle (oder der entsprechenden Kontakttabelle) befinden.

1. Geben Sie Text ein. Fügen Sie Kontextfelder oder Gestaltungsbausteine ein, indem Sie auf die Adobe Campaign-Komponenten klicken und sie auswählen. Wählen Sie zum Abschluss das Häkchen aus.

   ![chlimage_1-27](assets/chlimage_1-27a.png)

   Nach dem Einfügen der Kontextfelder und Personalisierungsblöcke können Sie eine Vorschau des Newsletters anzeigen und die Felder testen. Siehe [Newslettervorschau](#previewing-a-newsletter).

### Newsletter-Vorschau {#previewing-a-newsletter}

Sie können eine Vorschau des Newsletters anzeigen und eine Vorschau der Personalisierung anzeigen.

1. Klicken Sie bei geöffnetem Newsletter oben rechts in AEM auf **Vorschau**. In AEM wird nun angezeigt, wie der Newsletter für Empfänger aussieht.

   ![chlimage_1-28](assets/chlimage_1-28a.png)

   >[!NOTE]
   >
   >Wenn Sie Adobe Campaign Standard und die Beispielvorlage verwenden, führen zwei Gestaltungsbausteine mit anfänglichen Inhalten – **&quot;&lt;%@ include view=&quot;MirrorPage&quot; %>&quot;** und **&quot;&lt;%@ include view=&quot;UnsubscriptionLink&quot; %>&quot;** – beim Import des Inhalts während der Bereitstellung zu Fehlermeldungen. Dies lässt sich anpassen, indem Sie mithilfe der Gestaltungsbaustein-Auswahl die entsprechenden Bausteine auswählen.

1. Um eine Vorschau der Personalisierung anzuzeigen, öffnen Sie ContextHub, indem Sie auf das entsprechende Symbol in der Symbolleiste klicken bzw. tippen. Die Tags der Personalisierungsfelder werden nun durch die Seed-Daten der ausgewählten Rolle ersetzt. Beachten Sie, wie die Variablen beim Wechsel von Rollen in ContextHub angepasst werden.

   ![chlimage_1-29](assets/chlimage_1-29a.png)

1. Sie können die Seed-Daten aus Adobe Campaign anzeigen, die mit der aktuell ausgewählten Rolle verknüpft sind. Klicken Sie dazu auf das Adobe Campaign-Modul in der ContextHub-Leiste. Dadurch wird ein Dialogfeld geöffnet, in dem alle Seed-Daten des aktuell gewählten Profils angezeigt werden. Die Daten ändern sich entsprechend, wenn ein neues Profil gewählt wird.

   ![chlimage_1-30](assets/chlimage_1-30a.png)

### Genehmigen von Inhalten in AEM {#approving-content-in-aem}

Nach der Bearbeitung der Inhalte kann mit deren Genehmigung begonnen werden. Rufen Sie in der Toolbox die Registerkarte **Workflow** auf und wählen Sie den Workflow **Für Adobe Campaign genehmigen** aus.

Dieser Standard-Workflow besteht aus zwei Schritten: Prüfung und Genehmigung oder Prüfung und Ablehnung. Dieser Workflow kann jedoch erweitert und komplexer gestaltet werden.

![chlimage_1-31](assets/chlimage_1-31a.png)

Um Inhalt für Adobe Campaign zu genehmigen, wenden Sie den Workflow an, indem Sie **Workflow** auswählen. Wählen Sie dann **Für Adobe Campaign genehmigen** aus und klicken Sie auf **Workflow starten**. Führen Sie die vorgegebenen Schritte aus und genehmigen Sie den Inhalt. Sie können Inhalte auch ablehnen, indem Sie im letzten Schritt des Workflows statt **Genehmigen** die Option **Ablehnen** auswählen.

![chlimage_1-32](assets/chlimage_1-32a.png)

Nachdem der Inhalt genehmigt wurde, wird er in Adobe Campaign als genehmigt angezeigt. Die E-Mail kann dann gesendet werden.

Adobe Campaign Standard:

![chlimage_1-33](assets/chlimage_1-33a.png)

Adobe Campaign Classic:

![chlimage_1-34](assets/chlimage_1-34a.png)

>[!NOTE]
>
Es ist zwar möglich, nicht genehmigte Inhalte mit einem Versand in Adobe Campaign zu synchronisieren, es ist jedoch nicht möglich, einen solchen Versand durchzuführen. Ein Versand mit Campaign lässt sich nur mit genehmigten Inhalten versenden.

## Verknüpfen von AEM mit Adobe Campaign Standard und Adobe Campaign Classic {#linking-aem-with-adobe-campaign-standard-and-adobe-campaign-classic}

Wie Sie AEM mit Adobe Campaign verknüpfen oder synchronisieren, hängt davon ab, ob Sie das Adobe Campaign Standard-Abonnement oder die On-Premise-Version von Adobe Campaign Classic verwenden.

Weitere Informationen basierend auf Ihrer Adobe Campaign-Version finden Sie in folgenden Abschnitten:

* [Verknüpfen von AEM-Seiten mit Adobe Campaign-E-Mails (Adobe Campaign Standard)](#linking-an-aem-page-to-an-adobe-campaign-email-adobe-campaign-standard)
* [Synchronisieren von in AEM erstelltem Inhalt mit einer Bereitstellung von Adobe Campaign Classic](#synchronizing-content-created-in-aem-with-a-delivery-from-adobe-campaign-classic)

### Verknüpfen von AEM-Seiten mit Adobe Campaign-E-Mails (Adobe Campaign Standard) {#linking-an-aem-page-to-an-adobe-campaign-email-adobe-campaign-standard}

In Adobe Campaign Standard können Sie in AEM erstellte Inhalte mithilfe der folgenden Optionen verknüpfen und wiederherstellen:

* Eine E-Mail.
* Eine E-Mail-Vorlage.

Auf diese Weise können Sie den Inhalt versenden.  Ob ein Newsletter mit einem einzelnen Versand verknüpft ist, erkennen Sie am Code, der auf der Seite angezeigt wird.

![chlimage_1-35](assets/chlimage_1-35a.png)

>[!NOTE]
>
Ist ein Newsletter mit mehreren Bereitstellungen verknüpft, wird die Anzahl der verknüpften Bereitstellungen (nicht jedoch jede ID) angezeigt.

So verknüpfen Sie in AEM erstellte Seiten mit Adobe Campaign-E-Mails:

1. Erstellen Sie eine E-Mail basierend auf einer AEM E-Mail-Vorlage. Weitere Informationen finden Sie unter [Erstellen von E-Mails in Adobe Campaign Standard](https://helpx.adobe.com/de/campaign/standard/channels/using/creating-an-email.html).

   ![chlimage_1-36](assets/chlimage_1-36a.png)

1. Öffnen Sie den **Inhaltsblock** über das Bereitstellungs-Dashboard.

   ![chlimage_1-37](assets/chlimage_1-37a.png)

1. Wählen Sie **Mit Adobe Experience Manager-Inhalt verknüpfen** auf der Symbolleiste aus, um auf die Liste der in AEM verfügbaren Inhalte zuzugreifen.

   >[!NOTE]
   >
   Wenn die Option **Mit Adobe Experience Manager-Inhalt verknüpfen** nicht in der Aktionsleiste angezeigt wird, prüfen Sie, ob der **Inhaltsbearbeitungsmodus** ordnungsgemäß konfiguriert und in den E-Mail-Einstellungen **Adobe Experience Manager** festgelegt wurde.

   ![chlimage_1-38](assets/chlimage_1-38a.png)

1. Wählen Sie den Inhalt aus, den Sie in Ihrer E-Mail verwenden möchten.

   Diese Liste enthält:

   * Die Bezeichnung des Inhalts in AEM.
   * Der Genehmigungsstatus des Inhalts in AEM. Wenn der Inhalt nicht genehmigt wurde, können Sie den Inhalt synchronisieren, doch er muss vor dem Versand genehmigt werden. Sie können jedoch bestimmte Optionen verwenden, beispielsweise Versenden eines Nachweises oder die Vorschau.
   * Das Datum der letzten Änderung des Inhalts.
   * Alle bereits mit einem Versand verknüpften Inhalte.

   >[!NOTE]
   >
   Standardmäßig werden die Inhalte ausgeblendet, die bereits mit einem Versand synchronisiert wurden. Sie können sie jedoch anzeigen und verwenden. Wenn Sie beispielsweise Inhalt als Vorlage für mehrere Sendungen verwenden möchten.

   Wurde die E-Mail mit AEM-Inhalten verknüpft, können ihre Inhalte nicht in Adobe Campaign bearbeitet werden.

1. Geben Sie andere E-Mail-Parameter (Zielgruppen, Ausführungsplan) im Dashboard an.
1. Führen Sie den E-Mail-Versand aus.  Während der Versandsanalyse wird die aktuelle Version des AEM-Inhalts abgerufen.

   >[!NOTE]
   >
   Wenn der Inhalt in AEM aktualisiert wird, während er mit einer E-Mail verknüpft ist, wird er in Adobe Campaign automatisch während der Analyse aktualisiert.  Die Synchronisierung kann auch manuell mithilfe der Option **Adobe Experience Manager-Inhalt aktualisieren** in der Inhaltsaktionsleiste durchgeführt werden.
   >
   Sie können die Verknüpfung einer E-Mail mit AEM-Inhalten löschen, indem Sie **Verknüpfung mit Adobe Experience Manager-Inhalt löschen** aus der Inhaltsaktionsleiste auswählen. Diese Schaltfläche steht nur zur Verfügung, wenn der Inhalt bereits mit dem Versand verknüpft ist.  Um einen anderen Inhalt mit einem Versand zu verknüpfen, müssen Sie die aktuelle Verknüpfung des Inhalts löschen, bevor Sie eine neue Verknüpfung erstellen können.
   >
   Ist die Verknüpfung gelöscht, werden lokale Inhalte beibehalten und diese können in Adobe Campaign bearbeitet werden.  Wenn Sie den Inhalt nach der Änderung wieder verknüpfen, gehen alle Änderungen verloren.

### Synchronisieren von in AEM erstelltem Inhalt mit einem Versand von Adobe Campaign Classic {#synchronizing-content-created-in-aem-with-a-delivery-from-adobe-campaign-classic}

In Adobe Campaign können Sie in AEM erstellte Inhalte mithilfe der folgenden Optionen synchronisieren und wiederherstellen:

* Eine Kampagnenversand
* Eine Versandsaktivität in einem Kampagnenarbeitsablauf
* Ein wiederkehrender Versand
* Ein fortlaufender Versand
* Ein Message Center-Versand
* Eine Versandvorlage

Ist ein Newsletter in AEM mit einer Bereitstellung verknüpft, wird der Bereitstellungs-Code auf der Seite angezeigt.

![chlimage_1-39](assets/chlimage_1-39a.png)

>[!NOTE]
>
Ist der Newsletter mit mehreren Bereitstellungen verknüpft, wird die Anzahl der verknüpften Bereitstellungen (nicht jedoch jede ID) angezeigt.
>
[!NOTE]
>
Der Workflow-Schritt **In Adobe Campaign veröffentlichen** ist in AEM 6.1 veraltet. Dieser Schritt war Teil der Integration von AEM 6.0 in Adobe Campaign und ist nicht mehr erforderlich.

So synchronisieren Sie in AEM erstellte Inhalte mit einem Versand von Adobe Campaign:

1. Erstellen Sie eine Bereitstellung oder fügen Sie einem Kampagnen-Workflow eine Bereitstellung hinzu, indem Sie die Versandvorlage **E-Mail-Bereitstellung mit AEM-Inhalten (mailAEMContent)** auswählen.

   ![chlimage_1-40](assets/chlimage_1-40a.png)

1. Wählen Sie **Synchronisieren** auf der Symbolleiste aus, um auf die Liste der in AEM verfügbaren Inhalte zuzugreifen.

   >[!NOTE]
   >
   Sollte die Option **Synchronisieren** nicht in der Bereitstellungssymbolleiste angezeigt werden, prüfen Sie, ob das Feld **Inhaltsbearbeitungsmodus** in **AEM** richtig konfiguriert ist, indem Sie **Eigenschaften** > **Erweitert** auswählen.

   ![chlimage_1-41](assets/chlimage_1-41a.png)

1. Wählen Sie den Inhalt aus, den Sie mit Ihrem Versand synchronisieren möchten.

   Diese Liste enthält:

   * Die Bezeichnung des Inhalts in AEM.
   * Der Genehmigungsstatus des Inhalts in AEM. Wenn der Inhalt nicht genehmigt wurde, können Sie den Inhalt synchronisieren, doch er muss vor dem Versand genehmigt werden. Sie können allerdings bestimmte Vorgänge ausführen, z. B. Senden einer BAT-Datei oder den Vorschautest.
   * Das Datum der letzten Inhaltsänderung.
   * Alle bereits mit einem Versand verknüpften Inhalte.

   >[!NOTE]
   >
   Standardmäßig werden die Inhalte ausgeblendet, die bereits mit einem Versand synchronisiert wurden. Sie können sie jedoch anzeigen und verwenden. Wenn Sie beispielsweise Inhalt als Vorlage für mehrere Sendungen verwenden möchten.

   ![chlimage_1-42](assets/chlimage_1-42a.png)

1. Geben Sie die anderen Versandparameter (Zielgruppe usw.) an
1. Starten Sie, falls erforderlich, den Genehmigungsprozess für Bereitstellungen in Adobe Campaign. Die Inhaltsvalidierung in AEM ist zusätzlich zu den in Adobe Campaign konfigurierten Genehmigungen (Budget, Ziel usw.) erforderlich. Der Inhalt kann nur dann in Adobe Campaign genehmigt werden, wenn er bereits in AEM genehmigt worden ist.
1. Führen Sie den Versand aus. Während der Versandanalyse wird die aktuellste Version des AEM-Inhalts wiederherstellt.

   >[!NOTE]
   >
   * Nachdem Versand und Inhalt synchronisiert worden sind, wird der Versandinhalt in Adobe Campaign schreibgeschützt. Betreff und Inhalt der E-Mail können nicht mehr geändert werden.
   * Wenn der Inhalt in AEM aktualisiert wird, während er mit einem Versand in Adobe Campaign verknüpft ist, wird er während der Versandanalyse automatisch in dem Versand aktualisiert. Die Synchronisierung kann mithilfe der Schaltfläche **Inhalt jetzt aktualisieren** auch manuell durchgeführt werden.
   * Die Synchronisierung von Bereitstellung und AEM-Inhalten kann mithilfe der Schaltfläche **Synchronisierung aufheben** abgebrochen werden. Dies ist nur verfügbar, wenn bereits ein Inhalt mit dem Versand synchronisiert wurde. Um einen anderen Inhalt mit einem Versand zu synchronisieren, müssen Sie die Synchronisierung des aktuellen Inhalts abbrechen, bevor Sie eine neue Verknüpfung erstellen können.
   * Wenn die Synchronisierung aufgehoben wird, wird der lokale Inhalt beibehalten und kann in Adobe Campaign bearbeitet werden. Wenn Sie den Inhalt nach einer Änderung erneut synchronisieren, gehen alle Änderungen verloren.
   * Bei wiederkehrenden und kontinuierlichen Sendungen wird die Synchronisierung mit AEM-Inhalten bei jeder Ausführung des Versands angehalten.
