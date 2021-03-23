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
translation-type: tm+mt
source-git-commit: 7035c19a109ff67655ee0419aa37d1723e2189cc
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 14%

---


# Migration zur Touch-Benutzeroberfläche{#migration-to-the-touch-ui}

Ab Version 6.0 hat Adobe Experience Manager (AEM) eine neue Benutzeroberfläche eingeführt, die als *touchfähige Benutzeroberfläche* bezeichnet wird (auch bekannt als *Touch-Benutzeroberfläche*). Es ist an die Adobe Marketing Cloud und die allgemeinen Richtlinien der Benutzeroberfläche der Adobe angepasst. Dies ist die Standardbenutzeroberfläche in AEM mit der alten, Desktop-orientierten Oberfläche, die als *klassische Benutzeroberfläche* bezeichnet wird.

Wenn Sie AEM mit der klassischen Benutzeroberfläche verwendet haben, müssen Sie Maßnahmen ergreifen, um Ihre Instanz zu migrieren. Diese Seite soll als Sprungbrett dienen, indem Links zu einzelnen Ressourcen bereitgestellt werden.

>[!NOTE]
>
>Ein solches Migrationsprojekt kann erhebliche Auswirkungen auf Ihre Instanz haben. Empfohlene Richtlinien finden Sie unter [Verwalten von Projekten - Best Practices](/help/managing/best-practices.md).

## Grundlagen {#the-basics}

Beachten Sie beim Migrieren die folgenden (wichtigen) Unterschiede zwischen der klassischen und der Touch-Benutzeroberfläche:

<table>
 <tbody>
  <tr>
   <td>Klassische Benutzeroberfläche</td>
   <td>Touch-optimierte Benutzeroberfläche</td>
  </tr>
  <tr>
   <td>Wird im JCR-Repository als Knotenstruktur beschrieben. Jeder Knoten, der ein Element der Benutzeroberfläche darstellt, wird als <em>ExtJS-Widget</em> bezeichnet und clientseitig von <code>ExtJS</code> gerendert.</td>
   <td>Wird auch im JCR-Repository als Knotenstruktur beschrieben. In diesem Fall bezieht sich jedoch jeder Knoten auf einen Sling-Ressourcentyp (Sling-Komponente), der für das Rendering zuständig ist. Die Benutzeroberfläche wird also (im Grunde) serverseitig gerendert.</td>
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
   <td><p>JavaScript-Speicherort:</p>
    <ul>
     <li>Imperative Teile werden direkt mit Listenern eingebettet oder in clientlibs verwaltet.</li>
    </ul> </td>
   <td><p>JavaScript-Speicherort:</p>
    <ul>
     <li>Imperative Teile können nicht in die Dialogdefinition eingebettet werden. Trennung der Zuständigkeiten.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Umgang mit Ereignissen:</p>
    <ul>
     <li>Dialog-Widgets verweisen direkt auf JavaScript-Code.</li>
    </ul> </td>
   <td><p>Umgang mit Ereignissen:</p>
    <ul>
     <li>JavaScript überwacht Dialogfelder.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Vom Client durchgeführte Wiedergabe:
    <ul>
     <li>Client erstellt die Komponenten der Benutzeroberfläche dynamisch.</li>
     <li>Client-Anforderungen (Pull) Komponentendefinition (als JSON) vom Server.</li>
    </ul> </td>
   <td>Vom Server ausgeführte Wiedergabe:
    <ul>
     <li>Der Client fordert Seiten zusammen mit der entsprechenden Benutzeroberfläche an.</li>
     <li>Der Server sendet (push) die Benutzeroberfläche als HTML-Dokumente; Verwenden von Coral UI-Komponenten.<br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Mit anderen Worten bedeutet die Migration eines Abschnitts Ihrer Benutzeroberfläche von der klassischen Benutzeroberfläche zur Touch-Benutzeroberfläche, dass ein *ExtJS-Widget* in eine *Sling-Komponente* portiert wird. Um dies zu erleichtern, basiert die Touch-Benutzeroberfläche auf dem Granite UI-Framework, das bereits einige Sling-Komponenten für die Benutzeroberfläche bereitstellt (als Granite UI-Komponenten bezeichnet).

Prüfen Sie vor dem Beginn den Status und die entsprechenden Empfehlungen:

* [Status der Touch-UI-Funktionen](/help/release-notes/touch-ui-features-status.md)
* [Empfehlungen für Kunden zur Benutzeroberfläche](/help/sites-deploying/ui-recommendations.md)

Die Grundlagen für die Entwicklung der Touch-Benutzeroberfläche bieten eine solide Grundlage:

* [Konzepte der Touch-optimierten Benutzeroberfläche von AEM](/help/sites-developing/touch-ui-concepts.md)
* [Struktur der Touch-optimierten Benutzeroberfläche von AEM](/help/sites-developing/touch-ui-structure.md)

## Migrieren von Seiten-Authoring {#migrating-page-authoring}

Dialoge sind ein wichtiger Faktor bei der Migration Ihrer Komponenten:

* [Entwickeln AEM Komponenten](/help/sites-developing/developing-components.md)  (mit der touchfähigen Benutzeroberfläche)
* [Migration von einer klassischen Komponente](/help/sites-developing/developing-components.md#migrating-from-a-classic-component)
* [AEM Modernisierungstools](/help/sites-developing/modernization-tools.md)  - Unterstützung beim Konvertieren der Dialoge Ihrer klassischen UI-Komponenten in die Touch-Benutzeroberfläche

   * Es gibt eine Kompatibilitätsebene in der Touch-Benutzeroberfläche, um ein klassisches UI-Dialogfeld in einem &quot;Touch-UI-Wrapper&quot; zu öffnen, aber dies hat eingeschränkte Funktionalität und wird langfristig nicht empfohlen.

* [Anpassen von Dialogfeldern in der Touch-Benutzeroberfläche](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-customizing-dialog-fields-in-touch-ui.html)
* [Erstellen einer neuen Feld-Komponente in der Granite-Benutzeroberfläche](/help/sites-developing/granite-ui-component.md)
* [Anpassen der Seitenbearbeitung](/help/sites-developing/customizing-page-authoring-touch.md)  (mit der touchfähigen Benutzeroberfläche)

## Migrieren von Konsolen {#migrating-consoles}

Sie können die Konsolen auch anpassen:

* [Anpassen der Konsolen](/help/sites-developing/customizing-consoles-touch.md)  (für die touchfähige Benutzeroberfläche)

## Verwandte Aspekte {#related-considerations}

Es gibt zwar nicht direkt mit einer Migration auf die Touch-Benutzeroberfläche zu tun, aber es lohnt sich, gleichzeitig einige Probleme zu prüfen, da diese ebenfalls empfohlen werden:

* [Vorlagen](/help/sites-developing/templates.md)  -  [bearbeitbare Vorlagen](/help/sites-developing/page-templates-editable.md)
* [Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html)
* [HTL](https://docs.adobe.com/content/help/de-DE/experience-manager-htl/using/overview.html)

>[!NOTE]
>
>Siehe auch [Entwicklung - Best Practices](/help/sites-developing/best-practices.md).

## Weitere Ressourcen {#further-resources}

Ausführliche Informationen über die Entwicklung AEM sind der Sammlung der Mittel zu entnehmen unter:

* [Benutzerhandbuch für Entwickler](/help/sites-developing/home.md)
* [Dokumentation zur Granite-Benutzeroberfläche](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html)
* [AEM 6.5 Tutorials und Videos](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/overview.html)
* [Erste Schritte bei der Entwicklung von AEM Sites – WKND-Tutorial](/help/sites-developing/getting-started.md)
* [AEM Gems](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-index.html)
* [AEM-Modernisierungs-Tools](https://opensource.adobe.com/aem-modernize-tools/)

>[!CAUTION]
>
>AEM Moderationstools sind eine Community-Anstrengung und werden von der Adobe nicht unterstützt oder garantiert.

