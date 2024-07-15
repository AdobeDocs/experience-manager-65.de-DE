---
title: Experience Fragments
description: Experience Fragments beim Verfassen mit Adobe Experience Manager Sites
exl-id: 1ff9ac47-9a3a-4a4e-8af8-bc73048e0409
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Experience Fragments
role: User
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 100%

---

# Experience Fragments{#experience-fragments}

In Adobe Experience Manager (AEM) ist ein Experience Fragment eine Gruppe aus einer oder mehreren Komponenten (einschließlich Inhalt und Layout), die innerhalb von Seiten referenziert werden können. Sie können jede beliebige Komponente enthalten.

Ein Experience Fragment:

* ist Teil eines Erlebnisses (Seite).
* kann auf mehreren Seiten verwendet werden (basierend auf bearbeitbaren Vorlagen).
* basiert auf einer (bearbeitbaren) Vorlage, die seine Struktur und Komponenten definiert.
* Diese Vorlage wird verwendet, um die *Stammseite* des Experience Fragments zu erstellen.
* besteht aus einer oder mehreren Komponenten mit Layout in einem Absatzsystem.
* kann andere Experience Fragments enthalten.
* kann mit anderen Komponenten (einschließlich anderen Experience Fragments) kombiniert werden, um eine vollständige Seite (Erlebnis) zu bilden.
* Je nach Stammseite können eine oder mehrere Varianten erstellt werden.
* Diese Varianten können Inhalte und/oder Komponenten gemeinsam nutzen.
* kann in Bausteine untergliedert werden, die sich übergreifend für mehrere Varianten des Fragments verwenden lassen.

Experience Fragments können in folgenden Fällen verwendet werden:

* Wenn Autorinnen oder Autoren die Teile einer Seite (die sogenannten Fragmente eines Erlebnisses) wiederverwenden möchten, müssen sie das entsprechende Fragment kopieren und an der gewünschten Stelle einfügen. Das Erstellen und Verwalten dieser zum Kopieren/Einfügen vorgesehenen Erlebnisse sind zeitaufwendige und fehleranfällige Verfahren. Mit Experience Fragments ersparen Sie sich das Kopieren/Einfügen.
* Zur Unterstützung des Nutzungsszenarios mit Headless-Content-Management-Systemen. Autorinnen und Autoren sollten AEM nur zum Erstellen von Inhalten nutzen, jedoch nicht für deren Bereitstellung für Kundschaft. In diesem Fall würde das Erlebnis über ein System/einen Touchpoint eines Drittanbieters aufgenommen und dann an die Endbenutzerin bzw. den Endbenutzer weitergeben werden.
* Mit [Multi-Site-Management (MSM)](/help/sites-administering/msm.md), da ein Experience Fragment Teil einer Seite ist. Dies gilt sowohl für die einzelnen Fragmente als auch für die Ordner, in denen sie sich befinden.

>[!NOTE]
>
>Damit für Experience Fragments Schreibzugriff besteht, muss das betreffende Benutzerkonto in der folgenden Gruppe registriert sein:
>
>    `experience-fragments-editors`
>
>Falls Probleme auftreten, wenden Sie sich an Ihre Systemadmins.

## Wann ist die Verwendung von Experience Fragments sinnvoll? {#when-should-you-use-experience-fragments}

Experience Fragments sollten in folgenden Fällen verwendet werden:

* Wann immer Sie Erlebnisse wiederverwenden möchten.

   * Erlebnisse, die mit demselben oder ähnlichen Inhalten wiederverwendet werden

* Wenn Sie AEM als Inhaltsbereitstellungs-Plattform für Dritte nutzen möchten.

   * Nutzung durch beliebige Lösungen, bei denen AEM als Plattform zur Inhaltsbereitstellung fungieren soll
   * Beim Einbetten von Inhalten in Touchpoints von Drittanbietern

* Wenn Sie über ein Erlebnis mit unterschiedlichen Varianten oder Ausgabedarstellungen verfügen.

   * Kanal- oder kontextspezifische Varianten
   * Erlebnisse, die als Gruppe sinnvoll eingesetzt werden können (z. B. eine Kampagne, die je nach Kanal unterschiedliche Erlebnisse liefert)

* Wenn Sie Omni-Channel-Commerce betreiben.

   * Skaliertes Teilen von Commerce-bezogenem Inhalt auf [Social-Media-Kanälen](/help/sites-developing/experience-fragments.md#social-variations)
   * Ermöglichen von Transaktionen an Touchpoints

## Organisieren von Experience Fragments {#organizing-your-experience-fragments}

Folgendes wird empfohlen:
* verwenden von Ordnern zum Organisieren der Experience Fragments,

* [Konfigurieren der zulässigen Vorlagen für diese Ordner](#configure-allowed-templates-folder).

Beim Erstellen von Ordnern können Sie:

* eine aussagekräftige Struktur für Ihre Experience Fragments erstellen; zum Beispiel nach Klassifizierung

  >[!NOTE]
  >
  >Es ist nicht erforderlich, die Struktur Ihrer Experience Fragments an der Seitenstruktur Ihrer Site auszurichten.

* [Zuweisen der zulässigen Vorlagen auf Ordnerebene](#configure-allowed-templates-folder)

  >[!NOTE]
  >
  >Verwenden Sie den [Vorlagen-Editor](/help/sites-authoring/templates.md), wenn Sie eine eigene Vorlage erstellen möchten.

Das WKND-Projekt strukturiert einige Experience Fragments nach `Contributors`. Die verwendete Struktur zeigt auch, wie andere Funktionen, wie Multi-Site-Management (einschließlich Sprachkopien), verwendet werden können.

Siehe:

`http://localhost:4502/aem/experience-fragments.html/content/experience-fragments/wknd/language-masters/en/contributors/kumar-selveraj/master`

![Ordner für Experience Fragments](/help/sites-authoring/assets/xf-folders.png)

## Erstellen und Konfigurieren eines Ordners für Ihre Experience Fragments {#creating-and-configuring-a-folder-for-your-experience-fragments}

Um einen Ordner für Ihre Experience Fragments zu erstellen und zu konfigurieren, wird Folgendes empfohlen:

1. [Erstellen eines Ordners](/help/sites-authoring/managing-pages.md#creating-a-new-folder).

1. [Konfigurieren der zulässigen Experience Fragment-Vorlagen für diesen Ordner](#configure-allowed-templates-folder).

>[!NOTE]
>
>Es ist auch möglich, die [zulässigen Vorlagen für Ihre Instanz](#configure-allowed-templates-instance) zu konfigurieren. Diese Methode wird jedoch **nicht** empfohlen, da die Werte bei der Aktualisierung überschrieben werden können.

### Konfigurieren zulässiger Vorlagen für Ihren Ordner {#configure-allowed-templates-folder}

>[!NOTE]
>
>Dies ist die empfohlene Methode zur Angabe der **zulässigen Vorlagen**, da die Werte bei der Aktualisierung nicht überschrieben werden.

1. Navigieren Sie zum gewünschten Ordner mit **Experience Fragments**.

1. Wählen Sie den Ordner und dann **Eigenschaften** aus.

1. Geben Sie den regulären Ausdruck zum Abrufen der erforderlichen Vorlagen im Feld **Zulässige Vorlagen** an.

   Zum Beispiel:
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   Siehe:
   `http://localhost:4502/mnt/overlay/cq/experience-fragments/content/experience-fragments/folderproperties.html/content/experience-fragments/wknd`

   ![Experience Fragment-Eigenschaften – Zulässige Vorlagen](/help/sites-authoring/assets/xf-folders-templates.png)

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Vorlagen für Experience Fragments](/help/sites-developing/experience-fragments.md#templates-for-experience-fragments).

1. Klicken Sie auf **Speichern und schließen**.

### Konfigurieren zulässiger Vorlagen für Ihre Instanz {#configure-allowed-templates-instance}

>[!CAUTION]
>
>Es wird nicht empfohlen, die **zulässigen Vorlagen** mit dieser Methode zu ändern, da die angegebenen Vorlagen bei einer Aktualisierung überschrieben werden können.
>
>Verwenden Sie dieses Dialogfeld nur zu Informationszwecken.

1. Navigieren Sie zur gewünschten Konsole **Experience Fragments**.

1. Wählen Sie **Konfigurationsoptionen** aus:

   ![Schaltfläche „Konfiguration“](assets/ef-02.png)

1. Geben Sie im Dialogfeld **Experience Fragments konfigurieren** die erforderlichen Vorlagen an:

   ![Experience Fragments konfigurieren](assets/ef-01.png)

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Vorlagen für Experience Fragments](/help/sites-developing/experience-fragments.md#templates-for-experience-fragments).

1. Klicken Sie auf **Speichern**.

## Erstellen eines Experience Fragment {#creating-an-experience-fragment}

Gehen Sie zum Erstellen eines Experience Fragment folgendermaßen vor:

1. Wählen Sie in der globalen Navigation die Option „Experience Fragments“ aus.

   ![xf-01](assets/xf-01.png)

1. Gehen Sie zum gewünschten Ordner und klicken Sie auf **Erstellen**.

   ![xf-02](assets/xf-02.png)

1. Wählen Sie **Experience Fragment** aus, um den Assistenten zum **Erstellen von Experience Fragments** zu öffnen.

   Wählen Sie die gewünschte **Vorlage** aus und klicken Sie auf **Weiter**:

   ![xf-03](assets/xf-03.png)

1. Geben Sie die **Eigenschaften** für das **Experience Fragment** ein.

   Ein **Titel** ist zwingend erforderlich. Wenn der **Name** leer gelassen wird, wird er aus dem **Titel** abgeleitet.

   ![xf-04](assets/xf-04.png)

   >[!NOTE]
   >
   >Tags aus der Experience Fragment-Vorlage werden nicht mit Tags auf dieser Experience Fragment-Stammseite zusammengeführt.
   >
   >Diese sind völlig voneinander getrennt.

1. Klicken Sie auf **Erstellen**.

   Daraufhin wird eine Meldung angezeigt. Klicken Sie auf:

   * **Fertig**, um zur Konsole zurückzukehren

   * **Öffnen**, um den Editor für Fragmente zu öffnen

## Bearbeiten eines Experience Fragment {#editing-your-experience-fragment}

Der Experience Fragment Editor bietet Ihnen ähnliche Funktionen wie der normale Seiten-Editor.

>[!NOTE]
>
>Weitere Informationen zur Verwendung des Seiteneditors finden Sie unter [Bearbeiten des Seiteninhalts](/help/sites-authoring/editing-content.md).

Das folgende Beispielverfahren zeigt, wie Sie einen Teaser für ein Produkt erstellen:

1. Ziehen Sie per Drag-and-Drop einen **Teaser** aus dem [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser).

   ![xf-05](assets/xf-05.png)

1. Wählen Sie in der Komponenten-Symbolleiste die Option **[Konfigurieren](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste)**.
1. Fügen Sie das **Asset** hinzu und definieren Sie die **Eigenschaften** nach Bedarf.
1. Bestätigen Sie die Definitionen mit der Option **Fertig** (Häkchen).
1. Fügen Sie bei Bedarf weitere Komponenten hinzu.

## Erstellen einer Experience Fragment-Variante {#creating-an-experience-fragment-variation}

Je nach Ihren Anforderungen können Sie Varianten eines Experience Fragments erstellen:

1. Öffnen Sie ein Fragment zur [Bearbeitung](/help/sites-authoring/experience-fragments.md#editing-your-experience-fragment).
1. Öffnen Sie die Registerkarte **Varianten**.

   ![xf-authoring-06](assets/xf-authoring-06.png)

1. Mit **Erstellen** können Sie Folgendes erstellen:

   * **Variante**
   * **Variante als [Live Copy](/help/sites-administering/msm.md#live-copies)**

     >[!NOTE]
     >
     >Wenn Sie eine erste Variante als Live Copy erstellen, wird der Titel durch die Verwendung der Live Copy-Quelle als primäre Variante übernommen.

1. Definieren Sie die erforderlichen Eigenschaften:

   * **Vorlage**
   * **Titel**
   * **Name** (Wenn Sie das Feld leer lassen, wird der Name vom Titel abgeleitet)
   * **Beschreibung**
   * **Varianten-Tags**

   ![xf-06](assets/xf-06.png)

1. Bestätigen Sie Ihre Auswahl mit der Option **Fertig** (Häkchen-Symbol). Daraufhin wird die neue Variante im Bedienfeld angezeigt:

   ![xf-07](assets/xf-07.png)

## Verwenden eines Experience Fragment {#using-your-experience-fragment}

Sie können Ihr Experience Fragment jetzt beim Erstellen Ihrer Seiten verwenden:

1. Öffnen Sie eine beliebige Seite, um sie zu bearbeiten.

   >[!NOTE]
   >
   >Die Seite muss auf einer bearbeitbaren Vorlage basieren.

   Zum Beispiel: [https://localhost:4502/editor.html/content/we-retail/language-masters/en/products/men.html](https://localhost:4502/editor.html/content/we-retail/language-masters/en/products/men.html)

1. Erstellen Sie eine Instanz der Experience-Fragment-Komponente, indem Sie die Komponente aus dem Komponenten-Browser auf das Seitenabsatzsystem ziehen:

   ![xf-08](assets/xf-08.png)

1. Fügen Sie das eigentliche Experience Fragment zur Komponenteninstanz hinzu, indem Sie einen der folgenden Schritte ausführen:

   * Ziehen Sie das gewünschte Fragment vom Asset-Browser auf die Komponente
   * Wählen Sie in der Komponenten-Symbolleiste die Option **Konfigurieren** und geben Sie das zu verwendende Fragment an. Bestätigen Sie Ihre Auswahl mit der Option **Fertig** (Häkchen).

   ![xf-09](assets/xf-09.png)

   >[!NOTE]
   >
   >In der Komponenten-Symbolleiste dient die Option „Bearbeiten“ als Kurzbefehl zum Öffnen eines Fragments im Editor für Fragmente.

## Bausteine {#building-blocks}

Sie können eine oder mehrere Komponenten auswählen, um einen Baustein zur Wiederverwendung in Ihrem Fragment zu erstellen:

### Erstellen eines Bausteins {#creating-a-building-block}

So erstellen Sie einen neuen Baustein:

1. Wählen Sie im Experience Fragment-Editor die Komponenten aus, die Sie wiederverwenden möchten:

   ![xf-10](assets/xf-10.png)

1. Wählen Sie in der Komponenten-Symbolleiste die Option **In Baustein umwandeln** aus:

   ![xf-authoring-13-icon](assets/xf-authoring-13-icon.png)

1. Geben Sie den **Namen des Bausteins** ein und bestätigen Sie ihn mit der Option **Konvertieren**:

   ![xf-11](assets/xf-11.png)

1. Der **Baustein** wird auf der Registerkarte angezeigt und kann im Absatzsystem ausgewählt werden:

   ![xf-12](assets/xf-12.png)

#### Verwalten eines Bausteins {#managing-a-building-block}

Der Baustein wird auf der Registerkarte **Bausteine** angezeigt. Für jeden Baustein sind die folgenden Aktionen verfügbar:

* Zur Hauptvariante wechseln: zum Öffnen der Stammseiten-Variante in einer neuen Registerkarte
* Umbenennen
* Löschen

![xf-13](assets/xf-13.png)

#### Verwenden eines Bausteins {#using-a-building-block}

Sie können den Baustein wie bei jeder anderen Komponente auch in das Absatzsystem eines beliebigen Fragments ziehen.

## Details Ihres Experience Fragment {#details-of-your-experience-fragment}

Details zu Ihrem Fragment können wie folgt angezeigt werden:

1. Details werden in allen Ansichten der Konsole **Experience Fragments** angezeigt. Dabei enthält die **Listenansicht** Details eines [Exports nach Target](/help/sites-administering/experience-fragments-target.md):

   ![ef-03](assets/ef-03.png)

1. Beim Öffnen der **Eigenschaften** des Experience Fragment gilt Folgendes:

   ![ef-04](assets/ef-04.png)

   Die Eigenschaften werden auf verschiedenen Registerkarten angezeigt:

   >[!CAUTION]
   >
   >Diese Registerkarten werden angezeigt, wenn Sie **Eigenschaften** in der Konsole „Experience Fragments“ öffnen.
   >
   >
   >Wenn Sie beim Bearbeiten eines Experience Fragment **Eigenschaften** öffnen, werden die entsprechenden [Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md) angezeigt.

   ![ef-05](assets/ef-05.png)

   * **Allgemein**

      * **Titel** – erforderlich

      * **Beschreibung**
      * **Tags**
      * **Gesamtanzahl der Varianten** – nur zur Information

      * **Anzahl der Web-Varianten** – nur zur Information
      * **Anzahl der Nicht-Webvarianten** – nur zur Information ****

      * **Anzahl der Seiten, die dieses Fragment verwenden** – nur zur Information

   * **Cloud Services**

      * **Cloud-Konfiguration**
      * **Cloud Service-Konfigurationen**
      * **Facebook-Seiten-ID**
      * **Pinterest-Pinnwand**

   * **Verweise**

      * Eine Liste mit Verweisen.

   * **Social-Media-Status**

      * Details zu Social Media-Varianten

## Einfache HTML-Ausgabedarstellung {#the-plain-html-rendition}

Mit dem `.plain.`-Selektor in der URL können Sie auf die einfache HTML-Ausgabe des Browsers zugreifen.

>[!NOTE]
>
>Diese ist zwar direkt über den Browser verfügbar, [aber ihr Hauptzweck ist es, anderen Anwendungen (beispielsweise Web-Anwendungen von Drittanbietern oder benutzerdefinierten Mobile- Implementierungen) den direkten Zugriff auf den Inhalt des Experience Fragments zu ermöglichen, und zwar allein über die URL](/help/sites-developing/experience-fragments.md#the-plain-html-rendition).

## Exportieren von Experience Fragments {#exporting-experience-fragments}

Standardmäßig werden Experience Fragments im HTML-Format bereitgestellt. Dies kann sowohl von AEM als auch von Drittanbieterkanälen verwendet werden.

Für den Export nach Adobe Target kann auch JSON verwendet werden. Vollständige Informationen finden Sie unter [Target-Integration mit Experience Fragments](/help/sites-administering/experience-fragments-target.md).
