---
title: Exportieren von Erlebnisfragmenten in Adobe Target
seo-title: Exportieren von Erlebnisfragmenten in Adobe Target
description: Exportieren von Erlebnisfragmenten in Adobe Target
seo-description: Exportieren von Erlebnisfragmenten in Adobe Target
uuid: 2df0faab-5d5e-4fc1-93b3-28b7e6f3c306
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: d4152b4d-531b-4b62-8807-a5bc5afe94c6
docset: aem65
translation-type: tm+mt
source-git-commit: 6723b12bebba2f239c0886e5f378f1dc70e5e247

---


# Exportieren von Erlebnisfragmenten in Adobe Target{#exporting-experience-fragments-to-adobe-target}

>[!CAUTION]
>
>Einige Funktionen auf dieser Seite erfordern die Anwendung von AEM 6.5.3.0.
>
>6.5.3.0
>
>* **Externalizer-Domänen** können jetzt ausgewählt werden.
>
>
6.5.2.0:
>
>* Erlebnisfragmente können in Folgendes exportiert werden:
   >   * der Standardarbeitsbereich.
   >   * einen benannten Arbeitsbereich, der in der Cloud-Konfiguration angegeben ist.
>* AEM muss mit Adobe I/O[in Adobe Target ](/help/sites-administering/integration-ims-adobe-io.md)integriert werden.
>
>
AEM 6.5.0.0 und 6.5.1.0:
>
>* Die AEM Experience Fragments werden in den Standardarbeitsbereich von Adobe Target exportiert.
>* AEM muss gemäß den Anweisungen unter [Integration mit Adobe Target](/help/sites-administering/target.md)in Adobe Target integriert werden.


You can export [Experience Fragments](/help/sites-authoring/experience-fragments.md), created in Adobe Experience Manager (AEM), to Adobe Target (Target). Diese können dann als Angebote in Target-Aktivitäten verwendet werden, um Erlebnisse in großem Maßstab zu testen und zu personalisieren.

Es gibt drei Formatoptionen für den Export eines Experience Fragments in Adobe Target:

* HTML (Standard): Unterstützung für die Bereitstellung von Web- und Hybridinhalten
* JSON: Unterstützung für die Bereitstellung kostenloser Inhalte
* HTML und JSON

AEM Experience Fragments können in den Standardarbeitsbereich in Adobe Target oder in benutzerdefinierte Arbeitsbereiche für Adobe Target exportiert werden. Dies erfolgt über Adobe I/O, für die AEM mit Adobe I/O[in Adobe Target ](/help/sites-administering/integration-ims-adobe-io.md)integriert werden muss.

>[!NOTE]
>
>Die Adobe Target-Arbeitsbereiche sind in Adobe Target selbst nicht vorhanden. Sie werden in Adobe IMS (Identitätsverwaltungssystem) definiert und verwaltet und anschließend für die Verwendung in verschiedenen Lösungen mithilfe von Adobe-I/O-Integrationen ausgewählt.

>[!NOTE]
>
>Adobe Target-Arbeitsbereiche können verwendet werden, um Mitgliedern einer Organisation (Gruppe) zu ermöglichen, Angebote und Aktivitäten nur für diese Organisation zu erstellen und zu verwalten. ohne Zugriff auf andere Benutzer. Zum Beispiel länderspezifische Organisationen innerhalb eines globalen Konzerns.

>[!NOTE]
>
>Weitere Informationen unter:
>
>* [Adobe Target-Entwicklung](https://www.adobe.io/apis/experiencecloud/target.html)
>* [Hauptkomponenten - Erlebnisfragmente](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/experience-fragment.html)
>



## Voraussetzungen {#prerequisites}

>[!CAUTION]
>
>Einige Funktionen auf dieser Seite erfordern die Anwendung von AEM 6.5.3.0.

Verschiedene Aktionen sind erforderlich:

1. Sie müssen AEM mit Adobe Target [integrieren, indem Sie Adobe I/O](/help/sites-administering/integration-ims-adobe-io.md)verwenden.
2. Erlebnisfragmente werden aus der AEM-Autoreninstanz exportiert. Daher müssen Sie den AEM Link Externalizer[ auf der Autoreninstanz ](/help/sites-administering/target-requirements.md#configuring-the-aem-link-externalizer)konfigurieren, um sicherzustellen, dass alle Verweise im Experience Fragment für die Web-Bereitstellung extern zugeordnet werden.

   >[!NOTE]
   >
   >Für das Neuschreiben von Links, das nicht standardmäßig erfolgt, ist der [Experience Fragment Link Rewriter Provider](/help/sites-developing/experience-fragments.md#the-experience-fragment-link-rewriter-provider-html) verfügbar. Damit können benutzerspezifische Regeln für Ihre Instanz entwickelt werden.

## Cloud-Konfiguration hinzufügen {#add-the-cloud-configuration}

Bevor Sie ein Fragment exportieren, müssen Sie die **Cloud-Konfiguration** für **Adobe Target** zum Fragment oder Ordner hinzufügen. Dies ermöglicht Ihnen auch Folgendes:

* die für den Export zu verwendenden Formatoptionen angeben
* Target Workspace als Ziel auswählen
* Auswählen einer Externalisiererdomäne zum Umschreiben von Verweisen im Erlebnisfragment (optional)

Die erforderlichen Optionen können in den **Seiteneigenschaften** des erforderlichen Ordners bzw. Fragments ausgewählt werden. Die Spezifikation wird nach Bedarf vererbt.

1. Navigieren Sie zur **Experience Fragment**-Konsole.

1. Öffnen Sie die **Seiteneigenschaften** für den entsprechenden Ordner oder das Fragment.

   >[!NOTE]
   >
   >Wenn Sie die Cloud-Konfiguration zum übergeordneten Ordner „Experience Fragment“ hinzufügen, wird die Konfiguration von allen untergeordneten Elementen geerbt.
   >
   >
   >Wenn Sie die Cloud-Konfiguration zum Experience Fragment selbst hinzufügen, wird die Konfiguration von allen Varianten geerbt.

1. Wählen Sie die Registerkarte **Cloud-Services** aus.

1. Under **Cloud Service Configuration**, select **Adobe Target** from the drop-down list.

1. 
   >[!NOTE]
   >
   >Das JSON-Format eines Experience Fragment-Angebots kann angepasst werden. Definieren Sie dazu eine Komponente des Kundenerlebnisfragments und erläutern Sie dann, wie die Eigenschaften im Komponenten-Sling-Modell exportiert werden.
   >
   >Siehe Kernkomponente:
   >
   >[Hauptkomponenten - Erlebnisfragmente](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/experience-fragment.html)

   Wählen Sie unter **Adobe Target** :

   * die entsprechende Konfiguration
   * die erforderliche Formatoption
   * einen Adobe Target-Arbeitsbereich
   * falls erforderlich - die Externalizer-Domäne
   >[!CAUTION]
   >
   >Die Externalizer-Domäne ist optional. Ein AEM-Externalisierer wird konfiguriert, wenn der exportierte Inhalt auf eine bestimmte *Veröffentlichungsdomäne* verweisen soll. Weitere Informationen finden Sie unter AEM Link Externalizer [konfigurieren](/help/sites-administering/target-requirements.md#configuring-the-aem-link-externalizer).

   Beispiel für einen Ordner:

   ![Ordner - Cloud-](assets/xf-target-integration-01.png "DiensteOrdner - Cloud-Dienste")

1. Klicken Sie auf **Speichern und schließen**.

## Exporting an Experience Fragment to Adobe Target {#exporting-an-experience-fragment-to-adobe-target}

>[!CAUTION]
>
>Für Medienassets wie Bilder wird nur ein Verweis in Target exportiert. Das Asset selbst bleibt in AEM Assets gespeichert und wird aus der AEM-Veröffentlichungsinstanz bereitgestellt.
>
>Daher muss das Experience Fragment mit allen zugehörigen Assets veröffentlicht werden, bevor es in Target exportiert wird.

So exportieren Sie ein Experience Fragment von AEM nach Target (nach dem Angeben der Cloud-Konfiguration):

1. Navigieren Sie zur Experience Fragment-Konsole.
1. Wählen Sie das Experience Fragment, das Sie als Ziel exportieren möchten.

   >[!NOTE]
   >
   >Es muss eine Web-Variante des Experience Fragments sein.

1. Tippen/klicken Sie auf **Nach Adobe Target exportieren**.

   >[!NOTE]
   >
   >Wenn das Experience Fragment bereits exportiert wurde, wählen Sie **In Adobe Target aktualisieren**.

1. Tippen/klicken Sie auf **Exportieren, ohne veröffentlichen** bzw. auf **Veröffentlichen**.

   >[!NOTE]
   >
   >Wenn Sie **Veröffentlichen** auswählen, wird das Experience Fragment sofort veröffentlicht und an Target gesendet.

1. Tap/click **OK** in the confirmation dialog.

   Ihr Experience Fragment sollte jetzt in Target enthalten sein.

   >[!NOTE]
   >
   >In der [Listenansicht](/help/sites-authoring/experience-fragments.md#details-of-your-experience-fragment) der Konsole und in den **Eigenschaften** werden **verschiedene Details** des Exports angezeigt.

   >[!NOTE]
   >
   >Beim Anzeigen eines Experience Fragments in Adobe Target gibt das *Datum der letzten Änderung* an, wann das Fragment zuletzt in AEM geändert wurde. Es ist nicht das Datum, an dem das Fragment zuletzt in Adobe Target exportiert wurde.

>[!NOTE]
>
>Alternativ können Sie den Export aus dem Seiteneditor mithilfe ähnlicher Befehle im Menü [Seiteninformationen](/help/sites-authoring/author-environment-tools.md#page-information) durchführen.

## Using your Experience Fragments in Adobe Target {#using-your-experience-fragments-in-adobe-target}

Nach Ausführung der vorherigen Aufgaben wird das Erlebnisfragment auf der Seite &quot;Angebote&quot;in Target angezeigt. In der [entsprechenden Target-Dokumentation](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html) erfahren Sie, was Sie dort erreichen können.

>[!NOTE]
>
>Beim Anzeigen eines Experience Fragments in Adobe Target gibt das *Datum der letzten Änderung* an, wann das Fragment zuletzt in AEM geändert wurde. Es ist nicht das Datum, an dem das Fragment zuletzt in Adobe Target exportiert wurde.

## Deleting an Experience Fragment already exported to Adobe Target {#deleting-an-experience-fragment-already-exported-to-adobe-target}

Das Löschen eines Experience Fragments, das bereits nach Target exportiert wurde, kann zu Problemen führen, wenn das Fragment bereits in einem Angebot in Target verwendet wird. Durch das Löschen des Fragments ist das Angebot nicht mehr verwendbar, da der Fragmentinhalt von AEM bereitgestellt wird.

So vermeiden Sie solche Situationen:

* Wenn das Experience Fragment derzeit nicht in einer Aktivität verwendet wird, kann der Benutzer das Fragment ohne Warnmeldung in AEM löschen.
* Wenn das Experience Fragment derzeit von einer Aktivität in Target verwendet wird, warnt eine Fehlermeldung den AEM-Benutzer vor möglichen Konsequenzen, die das Löschen des Fragments für die Aktivität nach sich zieht.

   Die Fehlermeldung in AEM verbietet dem Benutzer nicht das (erzwungene) Löschen des Experience Fragments. Wenn das Erlebnisfragment gelöscht wird:

   * Das Target-Angebot mit AEM Experience Fragment zeigt möglicherweise unerwünschtes Verhalten an

      * Das Angebot wird wahrscheinlich weiterhin gerendert, da die HTML des Erlebnisfragments an Target gesendet wurde
      * Verweise im Erlebnisfragment funktionieren möglicherweise nicht ordnungsgemäß, wenn referenzierte Assets auch in AEM gelöscht wurden.
   * Natürlich sind keine weiteren Änderungen am Erlebnisfragment möglich, da das Erlebnisfragment nicht mehr in AEM existiert.