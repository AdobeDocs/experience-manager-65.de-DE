---
title: Rendering von adaptiven Vorlagen
description: Rendering von adaptiven Vorlagen
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: 58cac3b1-b7cd-44b2-b89b-f5ee8811c198
source-git-commit: 260f71acd330167572d817fdf145a018b09cbc65
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 12%

---

# Rendering von adaptiven Vorlagen{#adaptive-template-rendering}

Das Rendering adaptiver Vorlagen bietet eine Möglichkeit, eine Seite mit Varianten zu verwalten. Diese Funktion, die ursprünglich zur Bereitstellung verschiedener HTML-Ausgaben für Mobilgeräte (z. B. Feature Phone oder Smart Phone) nützlich war, ist nützlich, wenn Erlebnisse für verschiedene Geräte bereitgestellt werden müssen, für die eine andere Markup- oder HTML-Ausgabe erforderlich ist.

## Übersicht {#overview}

Vorlagen basieren auf einem responsiven Raster. Die auf diesen Vorlagen erstellten Seiten sind vollständig responsiv und passen sich automatisch an den Viewport des Client-Geräts an. Über die Emulator-Symbolleiste im Seiten-Editor können Autoren Layouts für bestimmte Geräte festlegen.

Es ist auch möglich, Vorlagen zur Unterstützung des adaptiven Renderings einzurichten. Wenn Gerätegruppen ordnungsgemäß konfiguriert sind, wird die Seite mit einem anderen Selektor in der URL gerendert, wenn ein Gerät im Emulatormodus ausgewählt wird. Mithilfe eines Selektors kann ein bestimmtes Seiten-Rendering direkt über die URL aufgerufen werden.

Denken Sie beim Einrichten Ihrer Gerätegruppen daran:

* Jedes Gerät muss mindestens einer Gerätegruppe angehören.
* Ein Gerät kann mehreren Gerätegruppen angehören.
* Da Geräte mehreren Gerätegruppen angehören können, können Selektoren kombiniert werden.
* Die Kombination von Selektoren wird von oben nach unten ausgewertet, da sie im Repository beibehalten werden.

>[!NOTE]
>
>Die Gerätegruppe &quot;Responsive Geräte&quot;verfügt nie über einen Selektor, da Geräte, die responsives Design unterstützen, vermutlich kein adaptives Layout benötigen

## Konfiguration {#configuration}

Adaptive Rendering-Selektoren können für bestehende Gerätegruppen oder für [Gruppen, die Sie selbst erstellt haben.](/help/sites-developing/mobile.md#device-groups)

In diesem Beispiel werden Sie die vorhandene Gerätegruppe konfigurieren **Smartphones** , um eine Auswahl für adaptives Rendering als Teil der **Erlebnisseite** -Vorlage in We.Retail.

1. Bearbeiten Sie die Gerätegruppe, für die ein adaptiver Selektor benötigt wird, unter `http://localhost:4502/miscadmin#/etc/mobile/groups`.

   Aktivieren Sie die Option **Emulator deaktivieren** und speichern Sie diese Einstellung.

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. Der Selektor steht für die **BlackBerry®** und **iPhone 4** hat die Gerätegruppe **Smartphone** wird in den folgenden Schritten zu den Vorlagen und Seitenstrukturen hinzugefügt.

   ![chlimage_1-158](assets/chlimage_1-158.png)

1. Lassen Sie mithilfe von CRXDE Lite zu, dass die Gerätegruppe in Ihrer Vorlage verwendet wird, indem Sie sie zur String-Eigenschaft mit mehreren Werten hinzufügen `cq:deviceGroups` in der Struktur Ihrer Vorlage.

   `/conf/<your-site>/settings/wcm/templates/<your-template>/structure/jcr:content`

   Wenn Sie beispielsweise die Gerätegruppe Smartphone hinzufügen möchten:

   `/conf/we-retail/settings/wcm/templates/experience-page/structure/jcr:content`

   ![chlimage_1-159](assets/chlimage_1-159.png)

1. Lassen Sie mithilfe von CRXDE Lite zu, dass die Gerätegruppe auf Ihrer Site verwendet wird, indem Sie sie zur String-Eigenschaft mit mehreren Werten hinzufügen `cq:deviceGroups` auf der Struktur Ihrer Site.

   `/content/<your-site>/jcr:content`

   Wenn Sie beispielsweise die Variable **Smartphone** Gerätegruppe:

   `/content/we-retail/jcr:content`

   ![chlimage_1-160](assets/chlimage_1-160.png)

Jetzt bei Verwendung der [Emulator](/help/sites-authoring/responsive-layout.md#layout-definitions-device-emulation-and-breakpoints) im Seiteneditor (z. B. wann [Layout ändern](/help/sites-authoring/responsive-layout.md)) und Sie ein Gerät der konfigurierten Gerätegruppe auswählen, wird die Seite mit einem Selektor als Teil der URL gerendert.

In diesem Beispiel wird beim Bearbeiten einer Seite basierend auf der Variablen **Erlebnisseite** und bei Auswahl von iPhone 4 im Emulator wird die Seite gerendert, einschließlich des Selektors als `arctic-surfing-in-lofoten.smart.html` anstelle von `arctic-surfing-in-lofoten.html`

Die Seite lässt sich auch direkt über diesen Selektor auswählen.

![chlimage_1-161](assets/chlimage_1-161.png)
