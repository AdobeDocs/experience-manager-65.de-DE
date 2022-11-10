---
title: Exportieren von Experience Fragments nach Adobe Target
seo-title: Exporting Experience Fragments to Adobe Target
description: Exportieren von Experience Fragments nach Adobe Target
seo-description: Exporting Experience Fragments to Adobe Target
uuid: 2df0faab-5d5e-4fc1-93b3-28b7e6f3c306
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: d4152b4d-531b-4b62-8807-a5bc5afe94c6
docset: aem65
exl-id: f2921349-de8f-4bc1-afa2-aeace99cfc5c
source-git-commit: 63f066013c34a5994e2c6a534d88db0c464cc905
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 100%

---

# Exportieren von Experience Fragments nach Adobe Target{#exporting-experience-fragments-to-adobe-target}

>[!CAUTION]
>
>Einige Funktionen auf dieser Seite erfordern die Anwendung von AEM 6.5.3.0 (oder höher).
>
>6.5.3.0:
>
>* **Externalizer-Domains** können jetzt ausgewählt werden.
   >  **Hinweis:** Externalizer-Domains sind nur für den Inhalt des Experience Fragments, das an Target gesendet wird, relevant und nicht Metadaten wie Inhalte zum Anzeigen von Angeboten.
>
>6.5.2.0:
>
>* Experience Fragments können in Folgendes exportiert werden:
   >
   >   * den Standardarbeitsbereich
   >   * einen benannten Arbeitsbereich, der in der Cloud-Konfiguration angegeben ist.
   >   * **Hinweis:** Für den Export in bestimmte Arbeitsbereiche ist Adobe Target Premium erforderlich.
>
>* AEM muss [mit Adobe Target über IMS integriert](/help/sites-administering/integration-target-ims.md) sein.
>
>AEM 6.5.0.0 und 6.5.1.0:
>
>* Die AEM Experience Fragments werden in den Standardarbeitsbereich von Adobe Target exportiert.
>* AEM muss gemäß den Anweisungen unter [Integration mit Adobe Target](/help/sites-administering/target.md) mit Adobe Target integriert werden.


Sie können [Experience Fragments](/help/sites-authoring/experience-fragments.md), die in Adobe Experience Manager (AEM) erstellt wurden, nach Adobe Target (Target) exportieren. Diese können dann als Angebote in Target-Aktivitäten verwendet werden, um Erlebnisse in großem Maßstab zu testen und zu personalisieren.

Es gibt drei Formatoptionen für den Export eines Experience Fragments in Adobe Target:

* HTML (Standard): Unterstützung der Bereitstellung von Web- und Hybridinhalten
* JSON: Unterstützung der Headless-Inhaltsbereitstellung
* HTML und JSON

AEM Experience Fragments können in den Standardarbeitsbereich in Adobe Target oder in benutzerdefinierte Arbeitsbereiche für Adobe Target exportiert werden. Dies erfolgt über die Adobe Developer Console, für die AEM [mit Adobe Target über IMS integriert](/help/sites-administering/integration-target-ims.md) sein muss.

>[!NOTE]
>
>Die Adobe Target-Arbeitsbereiche sind nicht in Adobe Target selbst vorhanden. Sie werden in Adobe IMS (Identity Management System) definiert und verwaltet und dann zur lösungsübergreifenden Verwendung mithilfe der Adobe Developer Console ausgewählt.

>[!NOTE]
>
>Adobe Target-Arbeitsbereiche können verwendet werden, um es Mitgliedern einer Organisation (Gruppe) zu ermöglichen, Angebote und Aktivitäten nur für diese Organisation zu erstellen und zu verwalten, ohne anderen Benutzern Zugriff zu gewähren. Zum Beispiel länderspezifische Organisationen innerhalb eines globalen Konzerns.

>[!NOTE]
>
>Weitere Informationen finden Sie auch unter:
>
>* [Adobe Target-Entwicklung](https://www.adobe.io/apis/experiencecloud/target.html)
>* [Kernkomponenten – Experience Fragments](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/experience-fragment.html?lang=de)
>


## Voraussetzungen {#prerequisites}

>[!CAUTION]
>
>Einige Funktionen auf dieser Seite erfordern die Anwendung von AEM 6.5.3.0.

Verschiedene Aktionen sind erforderlich:

1. Sie müssen [AEM mit Adobe Target über IMS integrieren](/help/sites-administering/integration-target-ims.md).
2. Experience Fragments werden aus der AEM-Autoreninstanz exportiert. Daher müssen Sie auf der Autoreninstanz [den AEM Link Externalizer konfigurieren](/help/sites-administering/target-requirements.md#configuring-the-aem-link-externalizer), um sicherzustellen, dass alle Verweise im Experience Fragment für die Webbereitstellung externalisiert werden.

   >[!NOTE]
   >
   >Für das Neuschreiben von Links, das nicht standardmäßig erfolgt, ist der [Experience Fragment Link Rewriter Provider](/help/sites-developing/experience-fragments.md#the-experience-fragment-link-rewriter-provider-html) verfügbar. Damit können benutzerspezifische Regeln für Ihre Instanz entwickelt werden.

## Hinzufügen der Cloud-Konfiguration {#add-the-cloud-configuration}

Bevor Sie ein Fragment exportieren, müssen Sie die **Cloud-Konfiguration** für **Adobe Target** zum Fragment oder Ordner hinzufügen. Dies ermöglicht Ihnen auch:

* die für den Export zu verwendenden Formatoptionen anzugeben
* einen Target-Arbeitsbereich als Ziel auszuwählen
* eine Externalizer-Domain zum Umschreiben von Verweisen im Experience Fragment auszuwählen (optional)

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

1. Wählen Sie unter **Cloud Service-Konfiguration** in der Dropdown-Liste den Eintrag **Adobe Target**.

   >[!NOTE]
   >
   >Das JSON-Format eines Experience Fragment-Angebots kann angepasst werden. Definieren Sie dazu eine kundenspezifische Experience Fragment-Komponente und kommentieren Sie dann, wie die Eigenschaften im Komponenten-Sling-Modell exportiert werden.
   >
   >Beachten Sie die Kernkomponente:
   >
   >[Kernkomponenten – Experience Fragments](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/experience-fragment.html)

   Wählen Sie unter **Adobe Target** Folgendes aus:

   * die passende Konfiguration
   * die Option für das erforderliche Format
   * einen Adobe Target-Arbeitsbereich
   * falls erforderlich – die Externalizer-Domain

   >[!CAUTION]
   >
   >Die Externalizer-Domain ist optional.
   >
   >Ein AEM Externalizer wird konfiguriert, wenn die exportierten Inhalte auf eine bestimmte *publish* Domain verweisen sollen. Weitere Informationen finden Sie unter [Konfigurieren des AEM Link Externalizer](/help/sites-administering/target-requirements.md#configuring-the-aem-link-externalizer).
   >
   >Beachten Sie außerdem, dass Externalizer-Domains nur für den Inhalt des Experience Fragments, das an Target gesendet wird, relevant sind und nicht Metadaten wie Inhalte zum Anzeigen von Angeboten.

   Zum Beispiel für einen Ordner:

   ![Ordner – Cloud Services](assets/xf-target-integration-01.png "Ordner – Cloud Services")

1. **Speichern und schließen**.

## Ein Experience Fragment nach Adobe Target exportieren {#exporting-an-experience-fragment-to-adobe-target}

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

1. Tippen/klicken Sie im Bestätigungsdialogfeld auf **OK**.

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

## Ihre Experience Fragments in Adobe Target verwenden {#using-your-experience-fragments-in-adobe-target}

Nach dem Ausführen der zuvor genannten Aufgaben wird das Experience Fragment auf der Seite „Angebote“ in Target angezeigt. In der [entsprechenden Target-Dokumentation](https://experiencecloud.adobe.com/resources/help/de_DE/target/target/aem-experience-fragments.html) erfahren Sie, was Sie dort erreichen können.

>[!NOTE]
>
>Beim Anzeigen eines Experience Fragments in Adobe Target gibt das *Datum der letzten Änderung* an, wann das Fragment zuletzt in AEM geändert wurde. Es ist nicht das Datum, an dem das Fragment zuletzt in Adobe Target exportiert wurde.

## Löschen eines bereits nach Adobe Target exportierten Experience Fragments {#deleting-an-experience-fragment-already-exported-to-adobe-target}

Das Löschen eines Experience Fragments, das bereits nach Target exportiert wurde, kann zu Problemen führen, wenn das Fragment bereits in einem Angebot in Target verwendet wird. Durch das Löschen des Fragments ist das Angebot nicht mehr verwendbar, da der Fragmentinhalt von AEM bereitgestellt wird.

So vermeiden Sie solche Situationen:

* Wenn das Experience Fragment derzeit nicht in einer Aktivität verwendet wird, kann der Benutzer das Fragment ohne Warnmeldung in AEM löschen.
* Wenn das Experience Fragment derzeit von einer Aktivität in Target verwendet wird, warnt eine Fehlermeldung den AEM-Benutzer vor möglichen Konsequenzen, die das Löschen des Fragments für die Aktivität nach sich zieht.

   Die Fehlermeldung in AEM verbietet dem Benutzer nicht das (erzwungene) Löschen des Experience Fragments. Wenn das Experience Fragment gelöscht wurde, gilt Folgendes:

   * Das Target-Angebot mit dem AEM Experience Fragment kann unerwünschtes Verhalten zeigen

      * Das Angebot wird wahrscheinlich noch gerendert, da das Experience Fragment-HTML nach Target verschoben wurde
      * Verweise im Experience Fragment funktionieren möglicherweise nicht ordnungsgemäß, wenn referenzierte Assets auch in AEM gelöscht wurden.
   * Natürlich sind keine weiteren Änderungen am Experience Fragment möglich, da es nicht mehr in AEM vorhanden ist.
