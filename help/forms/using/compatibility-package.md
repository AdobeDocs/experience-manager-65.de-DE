---
title: Kompatibilitätspaket
seo-title: Compatibility Package
description: Durch die Installation des Kompatibilitätspakets auf AEM Forms 6.5 können Sie die Correspondence Management-Assets aus AEM Forms 6.4 und früheren Versionen sowie veraltete Vorlagen und Seiten für adaptive Formulare verwenden
seo-description: Installing the Compatibility package on AEM Forms 6.4 lets you use the Correspondence Management assets from AEM Forms 6.4 and deprecated adaptive forms templates and pages
uuid: b49633d6-2cb3-422c-a314-25f3b8a37b7f
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 73e8ccc6-f857-493e-b6e3-878f93e2a356
docset: aem65
role: Admin
exl-id: bb16017c-a1bf-40d8-a78d-827c05b7ee2e
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 58%

---

# Kompatibilitätspaket{#compatibility-package}

## Übersicht {#overview}

Interaktive Kommunikation ist der standardmäßige und empfohlene Ansatz zum Erstellen von Kundenkommunikation in AEM Forms 6.5. Um Briefe in AEM Forms 6.5 weiterhin verwenden zu können, müssen Sie das neueste [AEMFD-Kompatibilitätspaket](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) installieren.

Mit dem AEMFD-Kompatibilitätspaket können Sie auch [Verwenden Sie die folgenden Assets aus AEM Forms 6.4, 6.3 und 6.2 auf AEM Forms 6.5:](../../forms/using/compatibility-package.md#add-support-for-aem-forms-and-assets-in-aem-forms)

* Dokumentfragmente
* Briefe
* Datenwörterbücher
* Veraltete Vorlagen und Seiten für adaptive Formulare

Weitere Informationen finden Sie unter [Durch Installation des Kompatibilitätspakets mit AEM Forms 6.5 kompatible Assets](../../forms/using/compatibility-package.md#assetsmadecompatible).

## Hinzufügen von Unterstützung für Assets von AEM Forms 6.4, 6.3 und 6.2 in AEM Forms 6.5 {#add-support-for-aem-forms-and-assets-in-aem-forms}

Gehen Sie nach der Aktualisierung wie folgt vor, um das AEM-Kompatibilitätspaket zu installieren und Ihre Assets mit Version 6.5 kompatibel zu machen:

Stellen Sie sicher, dass das [AEM-Kompatibilitätspaket](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) vorinstalliert ist.

1. Installieren Sie das neueste 6.5-[Kompatibilitätspaket](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html).

   Weitere Informationen zum Hochladen und Installieren des Pakets finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).

1. Nachdem die Protokolle stabilisiert wurden, starten Sie den Server neu.
1. Verwenden Sie das Migrationsdienstprogramm, um Ihre Assets mit Version 6.5 kompatibel zu machen.

   Weitere Informationen finden Sie unter [Migrationsdienstprogramm](../../forms/using/migration-utility.md).

## Durch Installation des Kompatibilitätspakets mit AEM Forms 6.5 kompatible Assets {#assetsmadecompatible}

Durch Installation des Kompatibilitätspakets können Sie die folgenden Assets und Vorlagen mit AEM Forms 6.5 kompatibel machen:

* Correspondence Management-Assets aus AEM 6.4 und früher:

   * [Briefe](../../forms/using/create-letter.md)
   * [Datenwörterbücher](/help/forms/using/data-dictionary.md)
   * Dokumentfragmente

* Veraltete Vorlagen für adaptive Formulare:

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrollmentTemplate
   * /libs/fd/af/templates/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* Veraltete Seiten für adaptive Formulare:

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedenrollment
