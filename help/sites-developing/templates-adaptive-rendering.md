---
title: Rendern von adaptiven Vorlagen
description: Erfahren Sie mehr über das Rendern von adaptiven Vorlagen in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: 58cac3b1-b7cd-44b2-b89b-f5ee8811c198
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 100%

---

# Rendering von adaptiven Vorlagen{#adaptive-template-rendering}

Das Rendern von adaptiven Vorlagen bietet eine Möglichkeit, eine Seite mit Varianten zu verwalten. Diese Funktion half ursprünglich bei der Bereitstellung verschiedener HTML-Ausgaben für Mobilgeräte (z. B. Feature Phones im Gegensatz zu Smartphones). Jetzt ist sie nützlich, wenn Erlebnisse für verschiedene Geräte bereitgestellt werden müssen, für die eine andere Markup- oder HTML-Ausgabe erforderlich ist.

## Übersicht {#overview}

Vorlagen werden auf einem responsiven Raster aufgebaut. Seiten, die basierend auf diesen Vorlagen erstellt wurden, sind vollständig responsiv und passen sich automatisch an das Ansichtsfenster des Client-Geräts an. Über die Emulator-Symbolleiste im Seiten-Editor können Autoren Layouts für bestimmte Geräte festlegen.

Es ist auch möglich, Vorlagen zum Unterstützen des adaptiven Renderns einzurichten. Wenn Gerätegruppen ordnungsgemäß konfiguriert sind, wird die Seite mit einem anderen Selektor in der URL gerendert, wenn ein Gerät im Emulatormodus ausgewählt wird. Mit einem Selektor kann ein bestimmtes Seiten-Rendering direkt über die URL aufgerufen werden.

Beachten Sie beim Einrichten Ihrer Gerätegruppen Folgendes:

* Jedes Gerät muss mindestens einer Gerätegruppe angehören.
* Ein Gerät kann mehreren Gerätegruppen angehören.
* Da Geräte mehreren Gerätegruppen angehören können, können Selektoren kombiniert werden.
* Die Kombination von Selektoren wird von oben nach unten ausgewertet, während sie im Repository beibehalten werden.

>[!NOTE]
>
>Die Gerätegruppe „Responsive Geräte“ verfügt nie über einen Selektor, da davon ausgegangen wird, dass Geräte, die responsive Designs unterstützen, kein adaptives Layout benötigen.

## Konfiguration {#configuration}

Selektoren für das adaptive Rendern können für bereits vorhandene Gerätegruppen konfiguriert werden oder für [Gruppen, die Sie selbst erstellt haben](/help/sites-developing/mobile.md#device-groups).

In diesem Beispiel konfigurieren Sie die bereits vorhandene Gerätegruppe **Smartphones**, sodass sie als Teil der Vorlage **Erlebnisseite** in We.Retail einen Selektor für das adaptive Rendern aufweist.

1. Bearbeiten Sie die Gerätegruppe, für die ein adaptiver Selektor benötigt wird, unter `http://localhost:4502/miscadmin#/etc/mobile/groups`.

   Aktivieren Sie die Option **Emulator deaktivieren** und speichern Sie diese Einstellung.

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. Der Selektor steht für **BlackBerry®** und **iPhone 4** zur Verfügung, sofern in den folgenden Schritten die Gerätegruppe **Smartphone** zur Vorlage und zu den Seitenstrukturen hinzugefügt wird.

   ![chlimage_1-158](assets/chlimage_1-158.png)

1. Lassen Sie über CRXDE Lite zu, dass die Gerätegruppe in der Vorlage genutzt wird, indem Sie sie zur mehrwertigen Zeichenfolgen-Eigenschaft `cq:deviceGroups` in der Struktur der Vorlage hinzufügen.

   `/conf/<your-site>/settings/wcm/templates/<your-template>/structure/jcr:content`

   Beispiel: Sie möchten die Smartphone-Gerätegruppe hinzufügen:

   `/conf/we-retail/settings/wcm/templates/experience-page/structure/jcr:content`

   ![chlimage_1-159](assets/chlimage_1-159.png)

1. Lassen Sie über CRXDE Lite zu, dass die Gerätegruppe auf Ihrer Website genutzt wird, indem Sie sie zur mehrwertigen Zeichenfolgen-Eigenschaft `cq:deviceGroups` in der Struktur der Website hinzufügen.

   `/content/<your-site>/jcr:content`

   Beispiel: Sie möchten die Gerätegruppe **Smartphone** zulassen:

   `/content/we-retail/jcr:content`

   ![chlimage_1-160](assets/chlimage_1-160.png)

Wenn Sie jetzt den [Emulator](/help/sites-authoring/responsive-layout.md#layout-definitions-device-emulation-and-breakpoints) im Seiten-Editor verwenden (z. B. beim [Bearbeiten des Layouts](/help/sites-authoring/responsive-layout.md)) und ein Gerät der konfigurierten Gerätegruppe auswählen, wird die Seite mit einem Selektor als Teil der URL gerendert.

Wenn Sie im vorliegenden Beispiel eine Seite bearbeiten, die auf der Vorlage **Erlebnisseite** basiert, und im Emulator „iPhone 4“ auswählen, wird die Seite so gerendert, dass der Selektor als `arctic-surfing-in-lofoten.smart.html` und nicht als `arctic-surfing-in-lofoten.html` enthalten ist.

Die Seite lässt sich auch direkt über diesen Selektor auswählen.

![chlimage_1-161](assets/chlimage_1-161.png)
