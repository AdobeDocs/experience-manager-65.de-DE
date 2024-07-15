---
title: Exportieren von Experience Fragments nach Adobe Target
description: Erfahren Sie, wie Sie Adobe Experience Manager (AEM) Experience Fragments in Adobe Target exportieren.
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: f2921349-de8f-4bc1-afa2-aeace99cfc5c
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: dcb55b3b185fe5dccf52377a12556e33d818e410
workflow-type: tm+mt
source-wordcount: '1438'
ht-degree: 100%

---

# Exportieren von Experience Fragments nach Adobe Target{#exporting-experience-fragments-to-adobe-target}

Sie können [Experience Fragments](/help/sites-authoring/experience-fragments.md), die in Adobe Experience Manager (AEM) erstellt wurden, nach Adobe Target (Target) exportieren. Diese können dann als Angebote in Target-Aktivitäten verwendet werden, um Erlebnisse im benötigten Umfang zu testen und zu personalisieren.

Es gibt drei Formatoptionen für den Export eines Experience Fragments in Adobe Target:

* HTML (Standard): Unterstützung der Bereitstellung von Web- und Hybridinhalten
* JSON: Unterstützung der Headless-Inhaltsbereitstellung
* HTML und JSON

AEM Experience Fragments können in den Standardarbeitsbereich in Adobe Target oder in benutzerdefinierte Arbeitsbereiche für Adobe Target exportiert werden. Dies erfolgt über die Adobe Developer Console, für die AEM [mit Adobe Target über IMS integriert](/help/sites-administering/setting-up-ims-integrations-for-aem.md) sein muss.

>[!NOTE]
>
>[IMS-Integrationen sind jetzt mit S2S OAuth konfiguriert](/help/sites-administering/setting-up-ims-integrations-for-aem.md).
>
>Frühere Konfigurationen wurden mit [JWT-Berechtigungen, die in der Adobe Developer Console nicht mehr unterstützt werden](/help/sites-administering/jwt-credentials-deprecation-in-adobe-developer-console.md), erstellt.

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
>* [Adobe Target-Entwicklung](https://developers.adobetarget.com/)
>* [Kernkomponenten – Experience Fragments](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/experience-fragment.html?lang=de)
>

## Voraussetzungen {#prerequisites}

Verschiedene Aktionen sind erforderlich:

1. Sie müssen [AEM mit Adobe Target über IMS integrieren](/help/sites-administering/setting-up-ims-integrations-for-aem.md).

   >[!NOTE]
   >
   >[IMS-Integrationen sind jetzt mit S2S OAuth konfiguriert](/help/sites-administering/setting-up-ims-integrations-for-aem.md).
   >
   >Frühere Konfigurationen wurden mit [JWT-Berechtigungen erstellt, die in der Adobe Developer Console nicht mehr unterstützt werden](/help/sites-administering/jwt-credentials-deprecation-in-adobe-developer-console.md).

1. Experience Fragments werden aus der AEM-Autoreninstanz exportiert. Daher müssen Sie auf der Autoreninstanz [den AEM Link Externalizer konfigurieren](/help/sites-administering/target-requirements.md#configuring-the-aem-link-externalizer), um sicherzustellen, dass alle Verweise im Experience Fragment für die Web-Bereitstellung externalisiert werden.

   >[!NOTE]
   >
   >Für das Umschreiben von Links, die nicht von der Standardeinstellung abgedeckt werden, ist der [Experience Fragment Link Rewriter Provider](/help/sites-developing/experience-fragments.md#the-experience-fragment-link-rewriter-provider-html) verfügbar. Dadurch können für Ihre Instanz benutzerdefinierte Regeln entwickelt werden.

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
   >Wenn Sie die Cloud-Konfiguration zum übergeordneten Ordner des Experience Fragments hinzufügen, wird die Konfiguration von allen untergeordneten Elementen geerbt.
   >
   >
   >Wenn Sie die Cloud-Konfiguration zum Experience Fragment selbst hinzufügen, wird die Konfiguration an alle Varianten vererbt.

1. Wählen Sie die Registerkarte **Cloud-Services** aus.

1. Wählen Sie unter **Cloud Service-Konfiguration** in der Dropdown-Liste den Eintrag **Adobe Target**.

   >[!NOTE]
   >
   >Das JSON-Format eines Experience Fragment-Angebots kann angepasst werden. Definieren Sie dazu eine kundenspezifische Experience Fragment-Komponente und kommentieren Sie dann, wie die Eigenschaften im Komponenten-Sling-Modell exportiert werden.
   >
   >Beachten Sie die Kernkomponente:
   >
   >[Kernkomponenten – Experience Fragments](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/experience-fragment.html?lang=de)

   Wählen Sie unter **Adobe Target** Folgendes aus:

   * die passende Konfiguration
   * die Option für das erforderliche Format
   * einen Adobe Target-Arbeitsbereich
   * falls erforderlich – die Externalizer-Domain

   >[!CAUTION]
   >
   >Die Externalizer-Domain ist optional.
   >
   >Ein AEM Externalizer wird konfiguriert, wenn die exportierten Inhalte auf eine bestimmte *Veröffentlichungs*-Domain verweisen sollen. Weitere Informationen finden Sie unter [Konfigurieren des AEM Link Externalizers](/help/sites-administering/target-requirements.md#configuring-the-aem-link-externalizer).
   >
   >Beachten Sie außerdem, dass Externalizer-Domains nur für den Inhalt des Experience Fragments, das an Target gesendet wird, relevant sind und nicht Metadaten wie Inhalte zum Anzeigen von Angeboten.

   Zum Beispiel für einen Ordner:

   ![Ordner – Cloud Services](assets/xf-target-integration-01.png "Ordner – Cloud Services")

1. **Speichern und schließen**.

## Ein Experience Fragment nach Adobe Target exportieren {#exporting-an-experience-fragment-to-adobe-target}

>[!CAUTION]
>
>Für Medien-Assets wie Bilder wird nur ein Verweis nach Target exportiert. Das Asset selbst bleibt in AEM Assets gespeichert und wird von der AEM-Veröffentlichungsinstanz bereitgestellt.
>
>Daher muss das Experience Fragment mit allen zugehörigen Assets veröffentlicht werden, bevor es in Target exportiert wird.

Exportieren eines Experience Fragments aus AEM in Target (nach Angabe der Cloud-Konfiguration):

1. Navigieren Sie zur Experience Fragment-Konsole.
1. Wählen Sie das Experience Fragment aus, das Sie in nach Target exportieren möchten.

   >[!NOTE]
   >
   >Es muss sich um eine Experience Fragment Web-Variante handeln.

1. Klicken Sie auf **In Adobe Target exportieren**.

   >[!NOTE]
   >
   >Wenn das Experience Fragment bereits exportiert wurde, wählen Sie **In Adobe Target aktualisieren**.

1. Klicken Sie auf **Exportieren ohne Veröffentlichung** bzw. auf **Veröffentlichen**.

   >[!NOTE]
   >
   >Wenn Sie **Veröffentlichen** auswählen, wird das Experience Fragment sofort veröffentlicht und an Target gesendet.

1. Klicken Sie im Bestätigungsdialogfeld auf **OK**.

   Ihr Experience Fragment sollte jetzt in Target enthalten sein.

   >[!NOTE]
   >
   >In der [Listenansicht](/help/sites-authoring/experience-fragments.md#details-of-your-experience-fragment) der Konsole und in den **Eigenschaften** werden **verschiedene Details** des Exports angezeigt.

   >[!NOTE]
   >
   >Beim Anzeigen eines Experience Fragments in Adobe Target gibt *Zuletzt geändert* an, wann das Fragment zuletzt in AEM geändert wurde. Es ist nicht das Datum, an dem das Fragment zuletzt in Adobe Target exportiert wurde.

>[!NOTE]
>
>Alternativ können Sie den Export auch über den Seiteneditor durchführen, indem Sie vergleichbare Befehle im Menü [Seiteninformationen](/help/sites-authoring/author-environment-tools.md#page-information) verwenden.

## Ihre Experience Fragments in Adobe Target verwenden {#using-your-experience-fragments-in-adobe-target}

Nach dem Ausführen der zuvor genannten Aufgaben wird das Experience Fragment auf der Seite „Angebote“ in Adobe Target angezeigt. Schauen Sie sich die [spezifische Target-Dokumentation](https://experienceleague.adobe.com/docs/target/using/experiences/offers/aem-experience-fragments.html?lang=de) an, um zu erfahren, was Sie dort erreichen können.

>[!NOTE]
>
>Beim Anzeigen eines Experience Fragments in Adobe Target gibt *Zuletzt geändert* an, wann das Fragment zuletzt in AEM geändert wurde. Es ist nicht das Datum, an dem das Fragment zuletzt in Adobe Target exportiert wurde.

## Löschen eines bereits nach Adobe Target exportierten Experience Fragments {#deleting-an-experience-fragment-already-exported-to-adobe-target}

Das Löschen eines Experience Fragments, das bereits in Target exportiert wurde, kann Probleme verursachen, wenn das Fragment bereits in einem Angebot in Adobe Target verwendet wird. Durch das Löschen des Fragments wird das Angebot unbrauchbar, da der Fragmentinhalt von AEM bereitgestellt wird.

So vermeiden Sie solche Situationen:

* Wenn das Experience Fragment derzeit nicht in einer Aktivität verwendet wird, ermöglicht AEM es den Benutzenden, das Fragment ohne Warnmeldung zu löschen.
* Wenn das Experience Fragment derzeit von einer Aktivität in Adobe Target verwendet wird, werden AEM-Benutzende durch eine Fehlermeldung über die möglichen Auswirkungen eines Löschens des Fragments auf die Aktivität gewarnt.

  Die Fehlermeldung in AEM untersagt den Benutzenden nicht das (erzwungene) Löschen des Experience Fragments. Wenn das Experience Fragment gelöscht wurde, gilt Folgendes:

   * Das Target-Angebot mit dem AEM Experience Fragment kann unerwünschtes Verhalten zeigen

      * Das Angebot wird wahrscheinlich noch gerendert, da das Experience Fragment-HTML nach Target verschoben wurde
      * Verweise im Experience Fragment funktionieren möglicherweise nicht ordnungsgemäß, wenn referenzierte Assets auch in AEM gelöscht wurden.

   * Es sind keine weiteren Änderungen am Experience Fragment möglich, da es nicht mehr in AEM vorhanden ist.


## Entfernen von Client-Bibliotheken aus nach Target exportierten Experience Fragments {#removing-clientlibs-from-fragments-exported-target}

Experience Fragments enthalten vollständige HTML-Tags und alle erforderlichen Client-Bibliotheken (CSS/JS), um das Fragment genau so wiederzugeben, wie es von dem Inhaltsautor bzw. der Inhaltsautorin des Experience Fragments erstellt wurde. Dies ist beabsichtigt.

Wenn Sie ein Experience Fragment-Angebot mit Adobe Target auf einer Seite verwenden, die von AEM bereitgestellt wird, enthält die Zielseite bereits alle erforderlichen Client-Bibliotheken. Außerdem wird das überflüssige HTML im Experience Fragment-Angebot ebenfalls nicht benötigt (siehe [Überlegungen](#considerations)).

Im Folgenden finden Sie ein Pseudobeispiel für HTML in einem Experience Fragment-Angebot:

```html
<!DOCTYPE>
<html>
   <head>
      <title>…</title>
      <!-- all the client libraries (css/js) -->
      …
   </head>
   <body>
        <!--/* Actual XF Offer content would appear here... */-->
   </body>
</html>
```

Wenn AEM ein Experience Fragment in Adobe Target exportiert, verwendet es mehrere zusätzliche Sling-Selektoren. Beispielsweise könnte die URL für das exportierte Experience Fragment wie folgt aussehen (beachten Sie `nocloudconfigs.atoffer`):

* http://www.your-aem-instance.com/content/experience-fragments/my-offers/my-xf-offer.nocloudconfigs.atoffer.html

Der Selektor `nocloudconfigs` wird mithilfe von HTL definiert und kann überlagert werden, indem er aus der folgenden Quelle kopiert wird:

* /libs/cq/experience-fragments/components/xfpage/nocloudconfigs.html

Der Selektor `atoffer` wird bei der Nachbearbeitung mit [Sling Rewriter](/help/sites-developing/experience-fragments.md#the-experience-fragment-link-rewriter-provider-html) angewendet. Beide können verwendet werden, um die Client-Bibliotheken zu entfernen.

### Beispiel {#example}

Für unsere Zwecke veranschaulichen wir dies mit `nocloudconfigs`.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Bearbeitbare Vorlagen](/help/sites-developing/templates.md#editable-templates).

#### Überlagerungen {#overlays}

In diesem Beispiel werden die [Überlagerungen](/help/sites-developing/overlays.md) eingefügt, um die Client-Bibliotheken *und* die überflüssige HTML zu entfernen. Es wird davon ausgegangen, dass Sie den Experience Fragment-Vorlagentyp bereits erstellt haben. Zu den notwendigen Dateien, die von `/libs/cq/experience-fragments/components/xfpage/` kopiert werden müssen, gehören:

* `nocloudconfigs.html`
* `head.nocloudconfigs.html`
* `body.nocloudconfigs.html`

#### Überlagerungen vom Vorlagentyp {#template-type-overlays}

Für dieses Beispiel verwenden wir die folgende Struktur:

![Überlagerungen vom Vorlagentyp](assets/xf-target-integration-02.png "Überlagerungen vom Vorlagentyp")

Diese Dateien enthalten folgende Inhalte:

* `body.nocloudconfigs.html`

  ![body.nocloudconfigs.html](assets/xf-target-integration-03.png "body.nocloudconfigs.html")

* `head.nocloudconfigs.html`

  ![head.nocloudconfigs.html](assets/xf-target-integration-04.png "head.nocloudconfigs.html")

* `nocloudconfigs.html`

  ![nocloudconfigs.html](assets/xf-target-integration-05.png "nocloudconfigs.html")

>[!NOTE]
>
>Um `data-sly-unwrap` zum Entfernen des Body-Tags zu verwenden, benötigen Sie `nocloudconfigs.html`.

### Überlegungen {#considerations}

Wenn Sie sowohl AEM-Sites als auch Nicht-AEM-Sites mit Experience Fragment-Angeboten in Adobe Target unterstützen möchten, müssen Sie zwei Experience Fragments (zwei verschiedene Vorlagentypen) erstellen:

* Eins mit der Überlagerung zum Entfernen von clientlibs/extra HTML

* Eins, das nicht über die Überlagerung verfügt und daher die erforderlichen clientlibs enthält