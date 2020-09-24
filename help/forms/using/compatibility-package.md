---
title: Kompatibilitätspaket
seo-title: Kompatibilitätspaket
description: Durch die Installation des Kompatibilitätspakets auf AEM Forms 6.5 können Sie die Correspondence Management-Assets von AEM Forms 6.4 und früheren Versionen sowie nicht mehr unterstützte Vorlagen und Seiten für adaptive Formulare verwenden
seo-description: Die Installation des Kompatibilitätspakets auf AEM Forms 6.4 ermöglicht es Ihnen, die Correspondence Management-Assets aus AEM Forms 6.4 sowie veraltete Vorlagen und Seiten für adaptive Formulare zu verwenden.
uuid: b49633d6-2cb3-422c-a314-25f3b8a37b7f
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 73e8ccc6-f857-493e-b6e3-878f93e2a356
docset: aem65
translation-type: tm+mt
source-git-commit: a929252a13f66da8ac3e52aea0655b12bdd1425f
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 64%

---


# Kompatibilitätspaket{#compatibility-package}

## Überblick {#overview}

Interactive communication is the default and recommended approach to create customer communications in AEM Forms 6.5. To continue using letters in AEM Forms 6.5, you need to install the latest [AEMFD Compatibility package](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html).

The AEMFD Compatibility package also allows you to [use the following assets from AEM Forms 6.4, 6.3 and 6.2 on AEM Forms 6.5:](../../forms/using/compatibility-package.md#add-support-for-aem-forms-and-assets-in-aem-forms)

* Dokumentfragmente
* Briefe
* Datenwörterbücher
* Veraltete Vorlagen und Seiten für adaptive Formulare

For more information, see [Assets made compatible with AEM Forms 6.5 by installing the Compatibility package](../../forms/using/compatibility-package.md#assetsmadecompatible).

## Add support for AEM Forms 6.4, 6.3 and 6.2 assets in AEM Forms 6.5 {#add-support-for-aem-forms-and-assets-in-aem-forms}

Gehen Sie nach der Aktualisierung wie folgt vor, um das AEM-Kompatibilitätspaket zu installieren und Ihre Assets mit Version 6.5 kompatibel zu machen:

Ensure that you have [AEM Compatibility package](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) pre-installed.

1. Install the latest 6.5 [Compatibility package](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html).

   Weitere Informationen zum Hochladen und Installieren des Pakets finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).

1. Nachdem die Protokolle stabilisiert sind, starten Sie den Server neu.
1. Verwenden Sie das Migrationsdienstprogramm, um Ihre Assets mit Version 6.5 kompatibel zu machen.

   For more information, see [migration utility](../../forms/using/migration-utility.md).

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

* Veraltete Seiten für adaptive Formulare

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedenrollment

