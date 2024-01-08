---
title: Testen von Kernkomponenten in We.Retail
description: Erfahren Sie, wie Sie mit We.Retail Kernkomponenten in Adobe Experience Manager ausprobieren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: b5f2be67-c93c-4dbc-acc0-3edd8f1a282f
source-git-commit: 3bcdbfc17efe1f4c6069fd97fd6a16ec41d0579e
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 28%

---

# Testen von Kernkomponenten in We.Retail{#trying-out-core-components-in-we-retail}

Die Kernkomponenten sind moderne, flexible Komponenten mit einfacher Erweiterbarkeit und einfacher Integration in Ihre Projekte. Die Kernkomponenten basieren auf verschiedenen grundlegenden Designprinzipien, wie HTL, Benutzerfreundlichkeit standardmäßig, Konfigurierbarkeit, Versionierung und Erweiterbarkeit. We.Retail basiert auf Kernkomponenten.

## Probieren Sie es aus {#trying-it-out}

1. Starten Sie Adobe Experience Manager (AEM) mit dem Beispielinhalt &quot;We.Retail&quot;und öffnen Sie die [Komponentenkonsole](/help/sites-authoring/default-components-console.md).

   **Globale Navigation > Tools > Komponenten**

1. Wenn Sie die Leiste in der Komponentenkonsole öffnen, können Sie nach einer bestimmten Komponentengruppe filtern. Die Kernkomponenten finden Sie unter

   * `.core-wcm`: Die standardmäßigen Kernkomponenten
   * `.core-wcm-form`: Die Kernkomponenten für die Formularübermittlung

   Choose `.core-wcm`.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. Alle Kernkomponenten haben den Namen **v1**, was zeigt, dass dies die erste Version dieser Kernkomponente ist. Es werden in Zukunft reguläre Versionen veröffentlicht, die versionskompatibel mit AEM sind und ein einfaches Upgrade ermöglichen, sodass Sie die neuesten Funktionen nutzen können.
1. Klicks **Text (v1)**.

   Hier können Sie sehen, dass der **Ressourcentyp** der Komponente `/apps/core/wcm/components/text/v1/text` lautet. Kernkomponenten befinden sich unter `/apps/core/wcm/components` und werden pro Komponente versioniert.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Klicken Sie auf **Dokumentation** Registerkarte, um die Entwicklerdokumentation für die Komponente anzuzeigen.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Kehren Sie zur Komponentenkonsole zurück. Nach Gruppe filtern **We.Retail** und wählen Sie die **Text** -Komponente.
1. Hier können Sie sehen, dass der **Ressourcentyp** auf eine Komponente verweist, wie unter `/apps/weretail` erwartet, aber der **Ressourcen-Supertyp** zurück auf die Kernkomponente `/apps/core/wcm/components/text/v1/text` verweist.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Klicken Sie auf **Live-Nutzung** Registerkarte, um zu sehen, auf welchen Seiten diese Komponente verwendet wird. Klicken Sie auf die erste **Dankeseite**, um die Seite zu bearbeiten.

   ![chlimage_1-166](assets/chlimage_1-166.png)

1. Wählen Sie auf der Dankeseite die Textkomponente aus und klicken Sie im Bearbeitungsmenü der Komponente auf das Symbol Vererbung abbrechen .

   [We.Retail verfügt über eine globalisierte Site-Struktur](/help/sites-developing/we-retail-globalized-site-structure.md) wo Inhalte von Sprach-Mastern an gesendet werden [Live Copies über einen Mechanismus namens Vererbung](/help/sites-administering/msm.md). Aus diesem Grund muss die Vererbung abgebrochen werden, damit ein Benutzer Text manuell bearbeiten kann.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Bestätigen Sie den Abbruch, indem Sie auf **Ja** klicken.

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. Nachdem die Vererbung abgebrochen und Sie die Textkomponenten ausgewählt haben, stehen viele weitere Optionen zur Verfügung. Klicken Sie auf **Bearbeiten**.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. Sie können nun sehen, welche Bearbeitungsmöglichkeiten für die Textkomponente zur Verfügung stehen.

   ![chlimage_1-170](assets/chlimage_1-170.png)

1. Aus dem **Seiteninformationen** Menü auswählen **Vorlage bearbeiten**.
1. Klicken Sie im Vorlagen-Editor der Seite auf die Schaltfläche **Politik** Symbol der Textkomponente im **Layout-Container** der Seite.

   ![chlimage_1-171](assets/chlimage_1-171.png)

1. Die Kernkomponenten ermöglichen es einem Vorlagenautor, zu konfigurieren, welche Eigenschaften den Seitenautoren zur Verfügung stehen. Dazu gehören Funktionen wie zulässige Einfügequellen, Formatierungsoptionen und verfügbare Absatzstile.

   Solche Dialogfelder sind für viele Kernkomponenten verfügbar und arbeiten Hand in Hand mit dem Vorlageneditor. Nach der Aktivierung sind sie für den Autor über die Komponenten-Editoren verfügbar.

   ![chlimage_1-172](assets/chlimage_1-172.png)

## Weiterführende Informationen {#further-information}

Weitere Informationen zu den Kernkomponenten finden Sie im Authoring-Dokument . [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) für einen Überblick über die Funktionen der Kernkomponenten und das Entwicklerdokument [Entwickeln von Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html?lang=de) für einen technischen Überblick.

Sie können sich darüber hinaus eingehender mit [bearbeitbaren Vorlagen](/help/sites-developing/we-retail-editable-templates.md) befassen. Umfassende Informationen zu bearbeitbaren Vorlagen finden Sie im Dokument [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md) für Autoren oder im Dokument [Bearbeitbare Seitenvorlagen](/help/sites-developing/page-templates-editable.md) für Entwickler.
