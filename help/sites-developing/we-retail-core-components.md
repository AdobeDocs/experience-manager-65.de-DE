---
title: Testen von Kernkomponenten in We.Retail
seo-title: Trying out Core Components in We.Retail
description: Testen von Kernkomponenten in We.Retail
seo-description: null
uuid: 8d1cea0b-99d9-49b2-b275-41f14864b1ff
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: af3cd818-61cf-4da1-bfb5-87540911ddd5
exl-id: b5f2be67-c93c-4dbc-acc0-3edd8f1a282f
source-git-commit: b886844dc80482ae4aae5fc7ce09e466efecc3bd
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 100%

---

# Testen von Kernkomponenten in We.Retail{#trying-out-core-components-in-we-retail}

Die Kernkomponenten sind moderne, flexible Komponenten, die sich problemlos erweitern und in Ihre Projekte integrieren lassen. Sie basieren auf mehreren wichtigen Designprinzipien wie HTL, unmittelbarer Nutzbarkeit, Konfigurierbarkeit, Versionierung und Erweiterbarkeit. We.Retail baut auf Kernkomponenten auf.

## Testen {#trying-it-out}

1. Starten Sie AEM mit den We.Retail-Beispielinhalten und öffnen Sie die [Komponentenkonsole](/help/sites-authoring/default-components-console.md).

   **Globale Navigation > Tools > Komponenten**

1. Wenn Sie die Leiste in der Komponentenkonsole öffnen, können Sie nach einer bestimmten Komponentengruppe filtern. Die Kernkomponenten befinden sich an den folgenden Stellen:

   * `.core-wcm`: Die standardmäßigen Kernkomponenten
   * `.core-wcm-form`: Die Kernkomponenten für die Formularübermittlung

   Choose `.core-wcm`.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. Beachten Sie, dass alle Kernkomponenten mit **v1** benannt sind, was bedeutet, dass dies die erste Version dieser Kernkomponente ist. Künftig werden regelmäßig Versionen veröffentlicht, die mit AEM kompatibel sind und ein einfaches Upgrade ermöglichen, sodass Sie die neuesten Funktionen nutzen können.
1. Klicken Sie auf **Text (v1)**.

   Hier können Sie sehen, dass der **Ressourcentyp** der Komponente `/apps/core/wcm/components/text/v1/text` lautet. Kernkomponenten befinden sich unter `/apps/core/wcm/components` und werden pro Komponente versioniert.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Klicken Sie auf die Registerkarte **Dokumentation**, um die Entwicklerdokumentation für die Komponente anzuzeigen.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Wechseln Sie zur Komponentenkonsole zurück. Filtern Sie nach der Gruppe **We.Retail** und wählen Sie die **Textkomponente** aus.
1. Hier können Sie sehen, dass der **Ressourcentyp** auf eine Komponente verweist, wie unter `/apps/weretail` erwartet, aber der **Ressourcen-Supertyp** zurück auf die Kernkomponente `/apps/core/wcm/components/text/v1/text` verweist.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Klicken Sie auf die Registerkarte **Live-Nutzung**, um anzuzeigen, auf welchen Seiten diese Komponente aktuell verwendet wird. Klicken Sie auf die erste **Dankeseite**, um die Seite zu bearbeiten.

   ![chlimage_1-166](assets/chlimage_1-166.png)

1. Wählen Sie auf der Dankeseite die Textkomponente aus und klicken Sie im Bearbeitungsmenü der Komponente auf das Symbol zum Aufheben der Vererbung.

   [We.Retail weist eine globalisierte Site-Struktur auf](/help/sites-developing/we-retail-globalized-site-structure.md), in der Inhalte von Sprach-Mastern per Push ](/help/sites-administering/msm.md)durch einen Mechanismus, der als Vererbung bezeichnet wird, an Live Copies übertragen werden[. Aus diesem Grund muss die Vererbung abgebrochen werden, damit Benutzer den Text manuell bearbeiten können.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Bestätigen Sie den Abbruch, indem Sie auf **Ja** klicken.

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. Wenn die Vererbung abgebrochen ist und Sie die Textkomponenten auswählen, stehen Ihnen viele weitere Optionen zur Verfügung. Klicken Sie auf **Bearbeiten**.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. Sie können nun sehen, welche Bearbeitungsmöglichkeiten für die Textkomponente zur Verfügung stehen.

   ![chlimage_1-170](assets/chlimage_1-170.png)

1. Wählen Sie aus dem Menü **Seiteninformationen** die Option **Vorlage bearbeiten** aus.
1. Klicken Sie im Vorlagen-Editor der Seite auf das **Richtlinien**-Symbol der Textkomponente im **Layout-Container** der Seite.

   ![chlimage_1-171](assets/chlimage_1-171.png)

1. Die Kernkomponenten ermöglichen es Vorlagenautoren zu konfigurieren, welche Eigenschaften für Seitenautoren zur Verfügung stehen. Dazu zählen Funktionen wie zulässige Einfügequellen, Formatierungsoptionen und verfügbare Absatzformate.

   Derartige Designdialogfelder sind für viele Kernkomponenten verfügbar und sind eng mit dem Vorlagen-Editor verzahnt. Sobald diese aktiviert sind, stehen sie den Autoren über die Komponenten-Editoren zur Verfügung.

   ![chlimage_1-172](assets/chlimage_1-172.png)

## Weiterführende Informationen {#further-information}

Weitere Informationen zu den Kernkomponenten finden Sie im Dokument [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) für Autoren. Dies enthält einen Überblick über die Kernkomponenten. Im Dokument [Entwickeln von Kernkomponenten](https://helpx.adobe.com/de/experience-manager/core-components/using/developing.html) für Entwickler finden Sie einen technischen Überblick.

Sie können sich darüber hinaus eingehender mit [bearbeitbaren Vorlagen](/help/sites-developing/we-retail-editable-templates.md) befassen. Umfassende Informationen zu bearbeitbaren Vorlagen finden Sie im Dokument [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md) für Autoren oder im Dokument [Bearbeitbare Seitenvorlagen](/help/sites-developing/page-templates-editable.md) für Entwickler.
