---
title: Migration zur Touch-Benutzeroberfläche
seo-title: Migration zur Touch-Benutzeroberfläche
description: Migration zur Touch-Benutzeroberfläche
seo-description: Migration zur Touch-Benutzeroberfläche
uuid: 47c43b56-532b-4ada-8503-04d66bab3564
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: introduction
discoiquuid: b315720f-e9b8-4063-99e2-1b9aa6bba460
docset: aem65
exl-id: 33dc1ee7-1e34-43d8-9265-c66535f5e002
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 14%

---

# Migration zur Touch-Benutzeroberfläche{#migration-to-the-touch-ui}

Ab Version 6.0 führte Adobe Experience Manager (AEM) eine neue Benutzeroberfläche ein, die als *Touch-optimierte Benutzeroberfläche* bezeichnet wird (auch *Touch-Benutzeroberfläche* genannt). Sie ist an die Adobe Marketing Cloud und die allgemeinen Richtlinien für die Benutzeroberfläche der Adobe angepasst. Dies ist inzwischen die Standard-Benutzeroberfläche in AEM mit der veralteten, Desktop-orientierten Benutzeroberfläche, die als *klassische Benutzeroberfläche* bezeichnet wird.

Wenn Sie AEM mit der klassischen Benutzeroberfläche verwendet haben, müssen Sie Maßnahmen ergreifen, um Ihre Instanz zu migrieren. Diese Seite soll als Sprungbrett dienen, indem Links zu einzelnen Ressourcen bereitgestellt werden.

>[!NOTE]
>
>Ein solches Migrationsprojekt kann erhebliche Auswirkungen auf Ihre Instanz haben. Empfohlene Richtlinien finden Sie unter [Verwalten von Projekten - Best Practices](/help/managing/best-practices.md) .

## Grundlagen {#the-basics}

Beachten Sie bei der Migration die folgenden (wichtigen) Unterschiede zwischen der klassischen und der Touch-Benutzeroberfläche:

<table>
 <tbody>
  <tr>
   <td>Klassische Benutzeroberfläche</td>
   <td>Touch-optimierte Benutzeroberfläche</td>
  </tr>
  <tr>
   <td>Wird im JCR-Repository als Knotenstruktur beschrieben. Jeder Knoten, der ein Element der Benutzeroberfläche darstellt, wird als <em>ExtJS-Widget</em> bezeichnet und clientseitig von <code>ExtJS</code> gerendert.</td>
   <td>Wird auch im JCR-Repository als Knotenstruktur beschrieben. In diesem Fall bezieht sich jedoch jeder Knoten auf einen Sling-Ressourcentyp (Sling-Komponente), der für das Rendering zuständig ist. Die Benutzeroberfläche wird daher (im Grunde) serverseitig gerendert.</td>
  </tr>
  <tr>
   <td><p><code>sling:resourceType</code></p>
    <ul>
     <li>nicht verwendet</li>
    </ul> </td>
   <td><code>sling:resourceType</code>
    <ul>
     <li>verwendet</li>
     <li>zum Beispiel<br /> <code>cq/gui/components/authoring/dialog</code><br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Dialogknoten:</p>
    <ul>
     <li>Name: <code>dialog</code></li>
     <li>jcr:primaryType: <code>cq:Dialog</code></li>
    </ul> </td>
   <td><p>Dialogknoten:</p>
    <ul>
     <li>Name: <code>cq:dialog</code></li>
     <li>jcr:primaryType: <code>nt:unstructured</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Javascript-Speicherort:</p>
    <ul>
     <li>Imperative Teile werden direkt über Listener eingebettet oder in Clientlibs verwaltet.</li>
    </ul> </td>
   <td><p>Javascript-Speicherort:</p>
    <ul>
     <li>Imperative Teile können nicht in die Dialogfelddefinition eingebettet werden. Aufgabentrennung.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Ereignisverarbeitung:</p>
    <ul>
     <li>Dialogfeld-Widgets verweisen direkt auf JavaScript-Code.</li>
    </ul> </td>
   <td><p>Ereignisverarbeitung:</p>
    <ul>
     <li>JavaScript beobachtet Dialogfeldereignisse.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Rendering durch den Client:
    <ul>
     <li>Der Client erstellt dynamisch die Komponenten der Benutzeroberfläche.</li>
     <li>Komponentendefinition für Client-Anforderungen (Pull) (als JSON) vom Server.</li>
    </ul> </td>
   <td>Vom Server durchgeführte Wiedergabe:
    <ul>
     <li>Der Client fordert Seiten zusammen mit der zugehörigen Benutzeroberfläche an.</li>
     <li>Der Server sendet (push) die Benutzeroberfläche als HTML-Dokumente. Verwenden von Coral-UI-Komponenten.<br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Das heißt, dass die Migration eines Abschnitts Ihrer Benutzeroberfläche von der klassischen Benutzeroberfläche zur Touch-Benutzeroberfläche bedeutet, dass ein *ExtJS-Widget* in eine *Sling-Komponente* übertragen wird. Um dies zu vereinfachen, basiert die Touch-Benutzeroberfläche auf dem Granite-UI-Framework, das bereits einige Sling-Komponenten für die Benutzeroberfläche bereitstellt (als Granite-UI-Komponenten bezeichnet).

Bevor Sie beginnen, überprüfen Sie den Status und die zugehörigen Empfehlungen:

* [Status der Funktionen der Touch-optimierten Benutzeroberfläche](/help/release-notes/touch-ui-features-status.md)
* [Empfehlungen für Kunden zur Benutzeroberfläche](/help/sites-deploying/ui-recommendations.md)

Die Grundlagen der Entwicklung der Touch-Benutzeroberfläche bieten eine solide Grundlage:

* [Konzepte der Touch-optimierten Benutzeroberfläche von AEM](/help/sites-developing/touch-ui-concepts.md)
* [Struktur der Touch-optimierten Benutzeroberfläche von AEM](/help/sites-developing/touch-ui-structure.md)

## Migrieren der Seitenbearbeitung {#migrating-page-authoring}

Dialoge sind bei der Migration Ihrer Komponenten ein wichtiger Faktor:

* [Entwickeln AEM Komponenten](/help/sites-developing/developing-components.md)  (mit der Touch-optimierten Benutzeroberfläche)
* [Migration von einer klassischen Komponente](/help/sites-developing/developing-components.md#migrating-from-a-classic-component)
* [AEM-Modernisierungs-Tools](/help/sites-developing/modernization-tools.md)  - Hilfe beim Konvertieren der Dialogfelder Ihrer Komponenten der klassischen Benutzeroberfläche in die Touch-Benutzeroberfläche

   * In der Touch-Benutzeroberfläche gibt es eine Kompatibilitätsebene, um ein Dialogfeld der klassischen Benutzeroberfläche in einem &quot;Touch-UI-Wrapper&quot;zu öffnen. Dies hat jedoch eingeschränkte Funktionalität und wird langfristig nicht empfohlen.

* [Anpassen von Dialogfeldern in der Touch-optimierten Benutzeroberfläche](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-customizing-dialog-fields-in-touch-ui.html)
* [Erstellen einer neuen Feld-Komponente in der Granite-Benutzeroberfläche](/help/sites-developing/granite-ui-component.md)
* [Anpassen der Seitenbearbeitung](/help/sites-developing/customizing-page-authoring-touch.md)  (mit der Touch-optimierten Benutzeroberfläche)

## Migrieren von Konsolen {#migrating-consoles}

Sie können die Konsolen auch anpassen:

* [Anpassen der Konsolen](/help/sites-developing/customizing-consoles-touch.md)  (für die Touch-optimierte Benutzeroberfläche)

## Verwandte Aspekte {#related-considerations}

Obwohl dies nicht direkt mit einer Migration auf die Touch-Benutzeroberfläche in Zusammenhang steht, sollten gleichzeitig auch verwandte Probleme in Betracht gezogen werden, da dies ebenfalls empfohlen wird:

* [Vorlagen](/help/sites-developing/templates.md)  -  [Bearbeitbare Vorlagen](/help/sites-developing/page-templates-editable.md)
* [Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html)
* [HTL](https://docs.adobe.com/content/help/de-DE/experience-manager-htl/using/overview.html)

>[!NOTE]
>
>Siehe auch [Entwicklung - Best Practices](/help/sites-developing/best-practices.md).

## Weitere Ressourcen {#further-resources}

Umfassende Informationen zur Entwicklung von AEM finden Sie in der Sammlung von Ressourcen unter:

* [Benutzerhandbuch für Entwickler](/help/sites-developing/home.md)
* [Dokumentation zur Granite-Benutzeroberfläche](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html)
* [Tutorials und Videos zu AEM 6.5 Sites](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/overview.html)
* [Erste Schritte bei der Entwicklung von AEM Sites – WKND-Tutorial](/help/sites-developing/getting-started.md)
* [AEM Gems](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-index.html)
* [AEM-Modernisierungs-Tools](https://opensource.adobe.com/aem-modernize-tools/)

>[!CAUTION]
>
>AEM Modernisierungs-Tools sind Community-Maßnahmen und werden von der Adobe nicht unterstützt oder garantiert.
