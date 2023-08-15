---
title: Erstellen oder Hinzufügen eines adaptiven Formulars zur AEM Sites-Seite
description: Erfahren Sie, wie Sie mühelos ein adaptives Formular erstellen oder nahtlos zu Ihrer AEM Sites-Seite hinzufügen können. Lernen Sie schrittweise Techniken und Best Practices für die Integration dynamischer und anpassbarer Formulare in Ihre Website kennen, um Ihre digitalen Erlebnisse für eine maximale Wirkung zu optimieren.
Keywords: AEM Forms in sites, AF in Sites editor, af in aem sites, aem sites af, add af to a sites page, af aem sites, af sites, create af in a sites page, adaptive form in aem sites, forms aem sites, add form to a sites page, adaptive forms aem sites, add adaptive forms to aem page, create forms in an aem sites page
feature: Adaptive Forms
exl-id: 1813ccfc-87ce-46fa-a1d5-5edffd91efb0
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '2960'
ht-degree: 89%

---

# Erstellen oder Hinzufügen eines adaptiven Formulars zur AEM Sites-Seite {#create-or-add-an-adaptive-form-to-aem-sites-page}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für [Erstellen neuer adaptiver Forms](/help/forms/using/create-an-adaptive-form-core-components.md) oder [Hinzufügen von Adaptive Forms zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Forms dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von Adaptive Forms mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | Dieser Artikel |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/create-or-add-an-adaptive-form-to-aem-sites-page.html?lang=de) |

Mit AEM Forms können Sie adaptive Formulare nahtlos in Ihre Web-Seiten integrieren. Dadurch können Ihre Besuchenden bequem Formulare ausfüllen und senden, ohne jemals die Seite verlassen zu müssen, auf der sie sich befinden. Dadurch können sie mühelos mit anderen Elementen der Website interagieren und gleichzeitig aktiv mit dem Formular interagieren.

Mit dem AEM-Seiteneditor können Sie schnell mehrere Formulare erstellen und zu Ihren AEM Sites-Seiten hinzufügen. Durch die Verwendung vom AEM-Seiteneditor können Inhaltsautoren und -autorinnen nahtlose Erlebnisse zur Datenerfassung auf einer Sites-Seite erstellen, indem sie die Leistung adaptiver Formularkomponenten nutzen, einschließlich dynamischem Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Außerdem können Sie damit verschiedene Funktionen von AEM Sites-Seiten verwenden, z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager.

AEM Forms bietet Container für adaptive Formulare und die „Adaptive Formulare – Einbettungskomponente“. Sie können den Container für adaptive Formulare verwenden, um ein neues Formular auf einer Experience Fragment- oder AEM Sites-Seite zu erstellen, während Sie mit der Komponente Adaptive Forms - Embed ein vorhandenes adaptives Formular hinzufügen oder ein neues Formular mit dem Adaptive Forms Editor erstellen können.

![Adaptives Formular auf der Siteseite](/help/forms/using/assets/adaptive-form-in-sites-page.png)

## Vorteile der Verwendung der Container-Komponente für adaptive Formulare im AEM Seiten-Editor oder im Experience Fragment

Mit dem Container für adaptive Formulare im Seiteneditor können Sie nahtlose Erlebnisse zur Datenerfassung in einer Sites-Seite erstellen, indem Sie adaptive Forms-Komponenten nutzen, einschließlich dynamischer Verhaltensweisen, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Darüber hinaus können Sie verschiedene Funktionen von AEM Sites-Seiten verwenden, wie z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager, wodurch die Erstellung und Verwaltung von Formularen insgesamt verbessert wird. Sehen wir uns einige dieser Funktionen an:

* **Versionierung:** AEM Sites-Seiten bieten [robuste Versionierungsfunktionen](/help/sites-authoring/working-with-page-versions.md), mit denen Sie verschiedene Versionen Ihrer Formulare verfolgen und verwalten können. Dadurch können Sie Änderungen und Verbesserungen an Formularen vornehmen und gleichzeitig bei Bedarf frühere Versionen wiederherstellen. Die Versionierung gewährleistet eine kontrollierte und organisierte Vorgehensweise bei der Entwicklung und Weiterentwicklung von Formularen.
* **Targeting (Integration mit Adobe Target):** Mit den Targeting-Funktionen von AEM Sites-Seiten können Sie auch [das Formularerlebnis für verschiedene Zielgruppen personalisieren](/help/sites-administering/target.md). Mithilfe von Benutzersegmenten und Targeting-Kriterien können Sie den Inhalt, das Design oder das Verhalten des Formulars an bestimmte Benutzergruppen anpassen. Auf diese Weise können Sie ein personalisiertes und relevantes Formularerlebnis bereitstellen und die Interaktions- und Konversionsraten steigern.
* **Übersetzung:** AEM Sites gewährleistet [nahtlose Integration mit Übersetzungsdiensten](/help/sites-administering/translation.md), sodass Sie Formulare problemlos in mehrere Sprachen übersetzen können. Diese Funktion vereinfacht den Lokalisierungsprozess und stellt sicher, dass Ihre Formulare für eine globale Zielgruppe zugänglich sind. Sie können Übersetzungen effizient in AEM-Übersetzungsprojekten verwalten und so Zeit und Aufwand für die Unterstützung mehrsprachiger Formulare reduzieren. Weitere Informationen zur Übersetzung finden Sie im Abschnitt „Überlegungen“.
* **Multi-Site-Management und Live Copy:** AEM Sites bietet robuste [Multi-Site-Management- und Live Copy-Funktionen](/help/sites-administering/msm.md), mit denen Sie mehrere Websites in einer einzigen Umgebung erstellen und verwalten können. Mit dieser Funktion können Sie jetzt Formulare über verschiedene Sites hinweg wiederverwenden, um Konsistenz zu gewährleisten und doppelte Arbeit zu vermeiden. Mit zentralisierter Kontrolle und Verwaltung können Sie Formulare effizient über mehrere Websites hinweg verwalten und aktualisieren.
* **Themen:** AEM Sites-Seiten bieten ein Framework für das Entwerfen und Verwalten konsistenter visueller Stile auf mehreren Web-Seiten. Diese definieren Farben, Schriftarten, Stylesheets und andere visuelle Elemente, die zum allgemeinen Erscheinungsbild der Website beitragen. [Sie können die Designs verwenden, die für eine AEM Sites-Seite für ein adaptives Formular entwickelt wurden, wodurch Zeit und Mühe gespart werden.](/help/sites-authoring/style-system.md).
* **Tagging:** Mit AEM Sites-Seiten können Sie [Zuweisen von Tags oder Beschriftungen zu einer Seite, einem Asset oder anderen Inhalten](/help/sites-authoring/tags.md). Tags sind Schlüsselwörter oder Metadatenbeschriftungen, die eine Möglichkeit bieten, Inhalte basierend auf bestimmten Kriterien zu kategorisieren und zu organisieren. Sie können Seiten, Assets oder anderen Inhaltselementen in AEM ein oder mehrere Tags zuweisen, um die Suche zu verbessern und die Assets zu kategorisieren.
* **Sperren und Freigeben von Inhalten:** AEM Sites ermöglicht Benutzenden die [Kontrolle des Zugriffs und der Änderungen an Seiten](/help/sites-authoring/editing-content.md#locking-a-page-locking-a-page) innerhalb der AEM Sites-Umgebung. Wenn eine Seite gesperrt ist, bedeutet dies, dass sie von anderen Benutzenden vor unbefugten Änderungen oder Bearbeitungen geschützt ist. Nur Benutzende, die den Inhalt gesperrt haben, oder Admins können ihn entsperren, um Änderungen zuzulassen.


## Verschiedene Optionen zum Hinzufügen eines adaptiven Formulars im AEM-Seiteneditor

Sie können diese Funktion voll nutzen, indem Sie die folgenden Optionen verwenden:

* **[Fügen Sie ein benutzerdefiniertes adaptives Formular zu einer AEM Sites-Seite hinzu:](#create-an-adaptive-form-in-sites-editor)** Erstellen Sie ein ganz neues Formular, passen Sie es speziell an Ihre Anforderungen und Design-Vorlieben an.

* **[Fügen Sie ein benutzerdefiniertes adaptives Formular zu einem Experience Fragments hinzu:](#create-an-adaptive-form-in-experience-fragment)** Erweitern Sie die Reichweite Ihrer Formulare, indem Sie sie zu AEM Experience Fragments hinzufügen, sodass sie nahtlos über mehrere Seiten oder Sites hinweg wiederverwendet werden können.

* **[Konvertieren eines adaptiven Formulars in ein Experience Fragment:](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)** Konvertieren Sie ein adaptives Formular, das zu einer AEM Sites-Seite hinzugefügt wurde, in ein Experience Fragment, um das Formular auf mehreren AEM Sites-Seiten wiederzuverwenden.

* **Erstellen Sie Formulare basierend auf genehmigten Vorlagen und fügen Sie sie einer AEM Sites-Seite hinzu:** Nutzen Sie vorab genehmigte Vorlagen, um schnell Formulare zu erstellen, die den Branding-Richtlinien und Design-Standards Ihres Unternehmens entsprechen. Die Option ist nur für adaptive Formulare verfügbar, die mit dem adaptiven Formular-Editor oder der „Adaptiven Formular – Einbettungskomponente“ erstellt wurde.

* **Fügen Sie vorhandene Formulare zu einer AEM Sites-Seite hinzu:** Einfache Integration von bereits erstellten Formularen in Ihre Websites, sodass Besuchende direkt mit ihnen interagieren können. Die Option ist nur für adaptive Formulare verfügbar, die mit dem adaptiven Formular-Editor oder der „Adaptiven Formular – Einbettungskomponente“ erstellt wurde.

* **Fügen Sie einer AEM Sites-Seite oder einem Experience Fragment mehrere Formulare hinzu:** Fügen Sie einer Seite mehrere Formulare hinzu, um Benutzenden basierend auf ihren Voreinstellungen und Anforderungen mehrere Optionen zur Verfügung zu stellen. Diese können eine Kombination aus neuen und vorhandenen Formularen darstellen.

## Überlegungen {#consideration}

* Wenn Sie den Container für adaptive Formulare verwenden, um ein Formular zu erstellen oder hinzuzufügen, werden die Formulare über den AEM Sites-Übersetzungsfluss übersetzt und lokalisiert. Für jede Sprache wird eine separate Kopie (Sprachkopie) der Sites-Seite und der entsprechenden Formulare generiert. Wenn eine Inhaltsautorin bzw. ein Inhaltsautor eine Regel in einem Formular auf der übergeordneten Seite ändert, müssen dieselben Änderungen in allen Sprachkopien des Formulars vorgenommen werden. Mit dem Container für adaptive Formulare können Sie außerdem verschiedene Funktionen von AEM Sites-Seiten verwenden, z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager.

* Wenn Sie ein Formular mithilfe der Einbettungskomponente für adaptive Formulare erstellen oder hinzufügen, werden die Formulare mithilfe des AEM Forms-Übersetzungsflusses übersetzt und lokalisiert. In diesem Fall wird ein einzelnes Formular beibehalten und in allen Sprachkopien der Sites-Seiten referenziert. Die Einbettungskomponente für adaptive Formulare bietet keinen Zugriff auf verschiedene Funktionen von AEM Sites-Seiten wie Versionierung, Targeting, Übersetzung und Multi-Site-Manager.


## Bevor Sie beginnen {#before-you-start}

+++  Aktivieren der Kernkomponenten adaptiver Formulare für Ihre Umgebung

Stellen Sie sicher, dass die [Kernkomponenten adaptiver Formulare für Ihre Umgebung aktiviert sind](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/quick-setup/enable-headless-adaptive-forms-and-core-components.html?lang=de).

+++

+++  Hinzufügen von Client-Bibliotheken adaptiver Formulare zu Ihren AEM Sites-Seiten- und Experience Fragment-Seitenkomponenten

Um die vollständige Funktionalität der adaptiven Formular-Container-Komponente zu aktivieren, fügen Sie die Client-Bibliotheken „customHeaderlibs“ und „customfooterlibs“ mithilfe der Bereitstellungs-Pipeline zu Ihrer AEM Sites-Seite hinzu. So fügen Sie die Bibliotheken hinzu:

1. Melden Sie sich bei Ihrer AEM Authoring-Instanz an und öffnen Sie CRX DE. Die Standard-URL für eine lokal ausgeführte Authoring-Instanz lautet: `http://localhost:4502/crx/de`.

1. Öffnen Sie die Datei `/apps/[your-sites-project]/components/page/customheaderlibs.html` und fügen Sie ihr den folgenden Code hinzu:

       ```
     //Customheaderlibs.html
     &lt;sly data-sly-use.clientlib=&quot;core/wcm/components/commons/v1/templates/clientlib.html&quot;>
     &lt;sly data-sly-call=&quot;${clientlib.css @ categories=&#39;core.forms.components.runtime.all&#39;}&quot;/>
     &lt;/sly>
     
     ```
   
1. Öffnen Sie die Datei `/apps/[your-sites-project]/components/page/customfooterlibs.html` und fügen Sie ihr den folgenden Code hinzu:

       ```
     
     //customfooterlibs.html
     &lt;sly data-sly-use.clientlib=&quot;core/wcm/components/commons/v1/templates/clientlib.html&quot;>
     &lt;sly data-sly-test=&quot;${!wcmmode.edit}&quot; data-sly-call=&quot;${clientlib.js @ categories=&#39;core.forms.components.runtime.all&#39;, async=true}&quot;/>
     &lt;/sly>
     ```
   
1. Öffnen Sie die Datei `/apps/[your-sites-project]/components/xfpage/customheaderlibs.html` und fügen Sie ihr den folgenden Code hinzu:

       ```
     //Customheaderlibs.html
     &lt;sly data-sly-use.clientlib=&quot;core/wcm/components/commons/v1/templates/clientlib.html&quot;>
     &lt;sly data-sly-call=&quot;${clientlib.css @ categories=&#39;core.forms.components.runtime.all&#39;}&quot;/>
     &lt;/sly>
     
     ```
   
1. Öffnen Sie die Datei `/apps/[your-sites-project]/components/customfooterlibs.html` und fügen Sie ihr den folgenden Code hinzu:

       ```
     
     //customfooterlibs.html
     &lt;sly data-sly-use.clientlib=&quot;core/wcm/components/commons/v1/templates/clientlib.html&quot;>
     &lt;sly data-sly-test=&quot;${!wcmmode.edit}&quot; data-sly-call=&quot;${clientlib.js @ categories=&#39;core.forms.components.runtime.all&#39;, async=true}&quot;/>
     &lt;/sly>
     ```
   
1. Wiederholen Sie die obigen Schritte für alle Authoring- und Publishing-Instanzen in Ihrer Umgebung.

+++

+++ Aktivieren der Container-Komponente adaptiver Formulare

Um die Komponente [!UICONTROL Container für adaptive Formulare] in der Richtlinie der Vorlage zu aktivieren, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die AEM Sites-Seite oder das Experience Fragment zur Bearbeitung. Um die Seite zur Bearbeitung zu öffnen, wählen Sie sie aus und klicken Sie auf „Bearbeiten“.
1. Öffnen Sie die Vorlage Ihrer Sites- oder Experience Fragment-Seite. Um die Vorlage zu öffnen, gehen Sie zu [!UICONTROL Seiteninformationen] ![Seiteninformationen](/help/forms/using/assets/Smock_Properties_18_N.svg) > [!UICONTROL Vorlage bearbeiten]. Dadurch wird die entsprechende Vorlage im Vorlageneditor geöffnet.
1. Klicken Sie in der Strukturansicht auf das Symbol **[!UICONTROL Richtlinie]** ![Richtlinie](/help/forms/using/assets/Smock_FeedManagement_18_N.svg) in der Menüleiste. Wählen Sie in der Liste **[!UICONTROL Zugelassene Komponenten]** das Kontrollkästchen **[!UICONTROL Container für adaptive Formulare]** unter dem **[AEM Archetyp-Projektname] – Adaptives Formular**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

## Erstellen eines adaptiven Formulars {#create-an-adaptive-form-in-sites-editor-or-experience-fragment}

Sie können ein brandneues Formular von Grund auf neu erstellen und es speziell an Ihre Anforderungen und Design-Voreinstellungen anpassen – direkt auf einer AEM Sites-Seite oder im Experience Fragment. Für Formulare, die nur einmal verwendet werden, wird die direkte Erstellung auf einer AEM Sites-Seite empfohlen, während Experience Fragments ideal für Formulare sind, die auf mehreren Seiten Ihrer Website wiederverwendet werden müssen.

* [Erstellen eines Formulars auf einer AEM Sites-Seite](#create-an-adaptive-form-in-sites-editor)
* [Erstellen eines Formulars in einem Experience Fragment](#create-an-adaptive-form-in-experience-fragment)
* [Konvertieren eines adaptiven Formulars in einer AEM Sites-Seite in ein Experience-Fragment](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### Erstellen eines Formulars auf einer AEM Sites-Seite {#create-an-adaptive-form-in-sites-editor}

Sie können die Container-Komponente adaptiver Formulare im AEM-Seiteneditor verwenden, um ein benutzerdefiniertes Formular zu erstellen. Mit der Komponente können Sie ein Formular durch Ziehen und Ablegen der Formularkomponenten erstellen. Die Formularkomponenten basieren auf Kernkomponenten. Sie können diese einfach entsprechend den Anforderungen Ihrer Organisation anpassen.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

So erstellen Sie ein adaptives Formular auf einer Sites-Seite:

1. Öffnen Sie die AEM Sites-Seite im Bearbeitungsmodus.
1. Ziehen Sie die Komponente **[!UICONTROL Container für Adaptive Formulare]** vom Komponenten-Browser zur Sites-Seite hinzugefügt. Dadurch wird ein Bereich für das Formular auf der Seite geschaffen. Sie können den Layout-Modus verwenden, um die Größe des Container-Bereichs zu ändern.
1. Ziehen Sie Kernkomponenten des adaptiven Formulars per Drag &amp; Drop in den Container-Bereich, um das Formular zu erstellen.
1. Fügen Sie die Schaltfläche „Senden“ hinzu.

Legen Sie als Nächstes die [Sendeaktion](#configure-submit-action-for-form) und erweiterte Eigenschaften fest.

### Erstellen eines Formulars in einem Experience Fragment {#create-an-adaptive-form-in-experience-fragment}

Sie können die Reichweite Ihrer Formulare erweitern, indem Sie sie zu AEM Experience Fragments hinzufügen, was eine nahtlose Wiederverwendung über mehrere Seiten oder Sites hinweg ermöglicht. Sie können beispielsweise ein Newsletter-Registrierungsformular in ein Experience Fragment einfügen. Auf diese Weise können Sie das Fragment bequem über mehrere Seiten Ihrer Website hinweg wiederverwenden, sodass das Formular nicht wiederholt neu erstellt werden muss. Alle Aktualisierungen oder Änderungen, die im Experience Fragment am Newsletter-Registrierungsformular vorgenommen werden, werden automatisch auf alle Seiten übertragen, auf denen es verwendet wird. Dadurch wird der Prozess optimiert und ein nahtloses Benutzererlebnis sichergestellt, während die Verwaltung der Formulare Ihrer Website vereinfacht wird.

So erstellen Sie ein adaptives Formular in einem Experience Fragment:

1. Öffnen Sie ein Experience Fragment.
1. Ziehen Sie den **[!UICONTROL Container für adaptive Formulare]** vom Komponenten-Browser in das Experience Fragment.
1. Ziehen Sie Kernkomponenten des adaptiven Formulars per Drag &amp; Drop in den Container-Bereich im Experience Fragment, um das Formular zu erstellen.
1. Fügen Sie die Schaltfläche „Senden“ hinzu.

Legen Sie als Nächstes die [Sendeaktion](#configure-submit-action-for-form) und erweiterte Eigenschaften fest.

### Konvertieren eines adaptiven Formulars in einer AEM Sites-Seite in ein Experience Fragment {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

Sie können ein vorhandenes adaptives Formular in einem Sites-Seiten-Editor in ein Experience Fragment konvertieren, um es auf mehreren Seiten oder Sites wiederzuverwenden.

So konvertieren Sie ein adaptives Formular auf einer AEM Sites-Seite in ein Experience Fragment:

1. Öffnen Sie die AEM Sites-Seite mit dem adaptiven Formular (in der Komponente „Container für adaptive Formulare“) im Bearbeitungsmodus.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]** aus, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formularseiten hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Wählen Sie in der Menüleiste das Symbol ![In Experience Fragment-Variante konvertieren](/help/forms/using/assets/Smock_FilingCabinet_18_N.svg).
   ![Konvertieren von Formularen in Siteseiten in Experience Fragment](/help/forms/using/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   Es wird ein Dialogfeld zum Konvertieren des Containers für adaptive Formulare in ein neues Experience Fragment oder zum Hinzufügen zu einem vorhandenen Experience Fragment angezeigt.
1. Legen Sie im Dialogfeld „In Experience Fragment-Variante konvertieren“ Werte für die folgenden Optionen fest:

   * **Aktion:** Wählen Sie diese Option aus, um ein neues Experience Fragment zu erstellen oder zu einem vorhandenen Experience Fragment hinzuzufügen.
   * **Übergeordneter Pfad:** Geben Sie den Pfad des Ordners an, in dem das Experience Fragment gehostet werden soll. Die Option ist nur zum Erstellen eines neuen Experience Fragment verfügbar.
   * **Vorlage:** Geben Sie den Pfad der Experience Fragment-Vorlage an. Wenn Sie keine Experience Fragment-Vorlage haben, [erstellen Sie sie](/help/sites-developing/experience-fragments.md). Die Option ist nur zum Hinzufügen des adaptiven Formulars zu einem vorhandenen Experience Fragment verfügbar.
   * **Fragmenttitel:** Geben Sie den Titel des Experience Fragment an. Der Titel identifiziert ein Experience Fragment eindeutig.


## Konfigurieren der Sendeaktion für das Formular {#configure-submit-action-for-form}

Mit einer Übermittlungsaktion können Sie das Ziel der Daten auswählen, die über ein adaptives Formular erfasst werden. Eine Sendeaktion wird ausgelöst, wenn eine Benutzerin bzw. ein Benutzer in einem adaptiven Formular auf die Schaltfläche „Senden“ klickt. Adaptive Formulare enthalten einige vordefinierte Sendeaktionen. Sie können außerdem die standardmäßigen Sendeaktionen erweitern, um Ihre eigene benutzerdefinierte Sendeaktion zu erstellen. So konfigurieren Sie eine Sendeaktion für Ihr Formular:

1. Öffnen Sie den AEM-Seiteneditor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]** aus, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formularseiten hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/using/assets/configure-icon.svg). Das Dialogfeld zum Konfigurieren von Sendeaktionen der Container adaptiver Formulare wird geöffnet.
   ![Container für adaptive Formulare](/help/forms/using/assets/adaptive-forms-container.png)
1. Wählen Sie je nach Ihren Anforderungen eine Übermittlungsaktion aus und konfigurieren Sie sie. Detaillierte Informationen zu Übermittlungsaktionen finden Sie unter [Übermittlungsaktion für adaptive Formulare](configuring-submit-actions.md)


## Konfigurieren eines Schema- oder Formulardatenmodells für ein Formular {#configure-schema-or-data-model-for-form}

Sie können das Formulardatenmodell verwenden, um ein Formular mit einer Datenquelle zu verbinden und Daten basierend auf Benutzeraktionen zu senden und zu empfangen. Sie können auch ein Formular mit einem JSON-Schema verbinden, um die gesendeten Daten in einem vordefinierten Format zu empfangen.

Bevor Sie ein Formular mit einem Schema oder Formulardatenmodell verbinden

* [Erstellen Sie ein JSON-Schema und laden Sie es in Ihre Umgebung hoch](adaptive-form-json-schema-form-model.md)
* [Erstellen eines Formulardatenmodells](create-form-data-models.md)

So konfigurieren Sie ein JSON-Schema oder ein Formulardatenmodell für Ihr Formular:

1. Öffnen Sie den AEM-Seiteneditor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]** aus, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formularseiten hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/using/assets/configure-icon.svg). Das Dialogfeld zum Konfigurieren von Datenmodellen der Container adaptiver Formulare wird geöffnet.
   ![Formulardatenmodell Container für adaptive Formulare](/help/forms/using/assets/form-data-model-adaptive-forms-container.png)
1. Wählen Sie ein JSON-Schema oder ein Formulardatenmodell aus und konfigurieren Sie es entsprechend Ihren Anforderungen. Detaillierte Informationen zu Übermittlungsaktionen finden Sie unter [Übermittlungsaktion für adaptive Formulare](configuring-submit-actions.md).

   * Wenn Sie die Option **[!UICONTROL Formularmodell]** wählen, können Sie mit der Option **[!UICONTROL Formulardatenmodell auswählen]** ein vorkonfiguriertes Formulardatenmodell auswählen.
   * Wenn Sie die Option **[!UICONTROL Schema]** wählen, verwenden Sie die Option **[!UICONTROL Schema]**, um ein JSON-Schema für Ihr Formular auszuwählen.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Konfigurieren eines Vorbefüllungsdienstes für ein Formular {#configure-prefill-service-for-form}

Sie können den Vorbefüllungsdienst verwenden, um Felder eines adaptiven Formulars mit vorhandenen Daten automatisch auszufüllen. Wenn ein Benutzer ein Formular öffnet, werden die Werte für diese Felder vorbefüllt. Sie haben folgende Möglichkeiten:

* [Erstellen eines benutzerdefinierten Vorbefüllungsdienstes](prepopulate-adaptive-form-fields.md)
* [Verwenden des Vorbefüllungsdienstes für Formulardatenmodelle](#fdm-prefill-service)

### Verwenden des Vorbefüllungsdienstes für Formulardatenmodelle {#fdm-prefill-service}

Sie können den Vorbefüllungsdienst für Formulardatenmodelle verwenden, um Felder eines Formulars mit einem konfigurierten Formulardatenmodell im Voraus auszufüllen. Der Vorbefüllungsdienst für das Formulardatenmodell verwendet den [Get-Dienst des konfigurierten Formulardatenmodells](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) zum Abrufen von Daten. So verwenden Sie den Vorbefüllungsdienst für Formulardatenmodelle eines adaptiven Formulars:

1. Öffnen Sie den AEM-Seiteneditor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]** aus, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formularseiten hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/using/assets/configure-icon.svg). Das Dialogfeld zum Konfigurieren von Datenmodellen der Container adaptiver Formulare wird geöffnet.
   ![Vorabausfüllen des Dienstformulars für den Seiteneditor der AEM Sites](/help/forms/using/assets/prefill-service-fdm-aem-sites-page-editor.png)
1. Formulardatenmodell auswählen. Öffnen Sie die Registerkarte **[!UICONTROL Allgemein]**. Wählen Sie im Vorbefüllungsdienst die Option **[!UICONTROL Formularportal-Entwurf des Vorbefüllungsdienstes]**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Leitet die Benutzenden bei der Formularübermittlung an eine neue Benutzerin bzw. einen neuen Benutzer weiter oder zeigt eine Dankesnachricht an

Beim Senden eines Formulars können Sie die Benutzenden zu einer anderen Web-Seite oder Nachricht umleiten. So leiten Sie die Benutzenden um oder konfigurieren die Dankesnachricht:

1. Öffnen Sie den AEM-Seiteneditor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]** aus, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formularseiten hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/using/assets/configure-icon.svg). Das Dialogfeld zum Konfigurieren von Datenmodellen der Container adaptiver Formulare wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Übermittlung]**.

   * Um eine Umleitungs-URL zu konfigurieren, wählen Sie für die Senden-Option die Option „Zu URL umleiten“ aus und geben Sie eine absolute Adresse, eine Umleitungs-URL oder einen relativen Pfad einer AEM Sites-Seite an.

   * Um eine benutzerdefinierte Nachricht oder eine Dankesnachricht zu konfigurieren, wählen Sie für die Senden-Option die Option „Nachricht anzeigen“ und geben Sie im Feld „Nachrichteninhalt“ eine Nachricht ein. Es handelt sich um ein Rich-Text-Feld. Sie können die Vollbildoption verwenden, um alle verfügbaren Rich-Text-Elemente anzuzeigen.
