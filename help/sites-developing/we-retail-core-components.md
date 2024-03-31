---
title: Testen von Kernkomponenten in We.Retail
description: Erfahren Sie, wie Sie mit We.Retail Kernkomponenten in Adobe Experience Manager testen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: b5f2be67-c93c-4dbc-acc0-3edd8f1a282f
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 100%

---

# Testen von Kernkomponenten in We.Retail{#trying-out-core-components-in-we-retail}

Die Kernkomponenten sind moderne, flexible Komponenten, die sich problemlos erweitern und in Ihre Projekte integrieren lassen. Sie basieren auf mehreren wichtigen Design-Prinzipien wie HTL, unmittelbarer Nutzbarkeit, Konfigurierbarkeit, Versionierung und Erweiterbarkeit. We.Retail baut auf Kernkomponenten auf.

## Probieren Sie es aus {#trying-it-out}

1. Starten Sie Adobe Experience Manager (AEM) mit den We.Retail-Beispielinhalten und öffnen Sie die [Komponentenkonsole](/help/sites-authoring/default-components-console.md):

   **Globale Navigation > Tools > Komponenten**

1. Wenn Sie die Leiste in der Komponentenkonsole öffnen, können Sie nach einer bestimmten Komponentengruppe filtern. Die Kernkomponenten befinden sich unter:

   * `.core-wcm`: Die standardmäßigen Kernkomponenten
   * `.core-wcm-form`: Die Kernkomponenten für die Formularübermittlung

   Choose `.core-wcm`.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. Alle Kernkomponenten sind mit **v1** benannt. Das bedeutet, dass dies die erste Version dieser Kernkomponente ist. Künftig werden regelmäßig Versionen veröffentlicht, die mit AEM kompatibel sind und ein einfaches Upgrade ermöglichen, sodass Sie die neuesten Funktionen nutzen können.
1. Klicken Sie auf **Text (v1)**.

   Hier können Sie sehen, dass der **Ressourcentyp** der Komponente `/apps/core/wcm/components/text/v1/text` lautet. Kernkomponenten befinden sich unter `/apps/core/wcm/components` und werden pro Komponente versioniert.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Klicken Sie auf die Registerkarte **Dokumentation**, um die Entwicklerdokumentation für die Komponente anzuzeigen.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Kehren Sie zur Komponentenkonsole zurück. Filtern Sie nach der Gruppe **We.Retail** und wählen Sie die **Textkomponente** aus.
1. Hier können Sie sehen, dass der **Ressourcentyp** auf eine Komponente verweist, wie unter `/apps/weretail` erwartet, aber der **Ressourcen-Supertyp** zurück auf die Kernkomponente `/apps/core/wcm/components/text/v1/text` verweist.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Klicken Sie auf die Registerkarte **Live-Nutzung**, um anzuzeigen, auf welchen Seiten diese Komponente verwendet wird. Klicken Sie auf die erste **Dankeseite**, um die Seite zu bearbeiten.

   ![chlimage_1-166](assets/chlimage_1-166.png)

1. Wählen Sie auf der Dankesseite die Textkomponente aus und klicken Sie im Bearbeitungsmenü der Komponente auf das Symbol „Vererbung abbrechen“.

   [We.Retail weist eine globalisierte Site-Struktur auf](/help/sites-developing/we-retail-globalized-site-structure.md), in der Inhalte von Sprachmustervorlagen per Push [durch einen Mechanismus, der als Vererbung bezeichnet wird, an Live Copies übertragen werden](/help/sites-administering/msm.md). Aus diesem Grund muss die Vererbung abgebrochen werden, damit Benutzende den Text manuell bearbeiten können.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Bestätigen Sie den Abbruch, indem Sie auf **Ja** klicken.

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. Wenn die Vererbung abgebrochen ist und Sie die Textkomponenten auswählen, stehen Ihnen viele weitere Optionen zur Verfügung. Klicken Sie auf **Bearbeiten**.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. Sie können nun sehen, welche Bearbeitungsmöglichkeiten für die Textkomponente zur Verfügung stehen.

   ![chlimage_1-170](assets/chlimage_1-170.png)

1. Wählen Sie aus dem Menü **Seiteninformationen** die Option **Vorlage bearbeiten** aus.
1. Klicken Sie im Vorlageneditor der Seite auf das **Richtlinien**-Symbol der Textkomponente im **Layout-Container** der Seite.

   ![chlimage_1-171](assets/chlimage_1-171.png)

1. Kernkomponenten ermöglichen es Vorlagenautorinnen und -autoren zu konfigurieren, welche Eigenschaften für Seitenautorinnen und -autoren zur Verfügung stehen. Dazu zählen Funktionen wie zulässige Einfügequellen, Formatierungsoptionen und verfügbare Absatzformate.

   Derartige Design-Dialogfelder sind für viele Kernkomponenten verfügbar und eng mit dem Vorlageneditor verzahnt. Sobald diese aktiviert sind, stehen sie den Autorinnen und Autoren über die Komponenteneditoren zur Verfügung.

   ![chlimage_1-172](assets/chlimage_1-172.png)

## Weiterführende Informationen {#further-information}

Weitere Informationen zu den Kernkomponenten finden Sie im Dokument [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) für Autorinnen und Autoren. Dies enthält einen Überblick über die Kernkomponenten. Im Dokument [Entwickeln von Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html?lang=de) für Entwicklerinnen und Entwickler finden Sie einen technischen Überblick.

Sie können sich darüber hinaus eingehender mit [bearbeitbaren Vorlagen](/help/sites-developing/we-retail-editable-templates.md) befassen. Umfassende Informationen zu bearbeitbaren Vorlagen finden Sie im Dokument [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md) für Autoren oder im Dokument [Bearbeitbare Seitenvorlagen](/help/sites-developing/page-templates-editable.md) für Entwickler.
