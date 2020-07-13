---
title: '"Gefällt mir"-Essentials'
seo-title: '"Gefällt mir"-Essentials'
description: Übersicht über Link-Komponenten
seo-description: Übersicht über Link-Komponenten
uuid: 89f16859-c901-4090-8e16-363b95c508de
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f176c42b-b16b-42c9-af22-4b6421de5a90
pagetitle: Liking Essentials
translation-type: tm+mt
source-git-commit: c897f034edbdbeee74869165ed384c3408a857e0
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 2%

---


# &quot;Gefällt mir&quot;-Essentials {#liking-essentials}

Die &quot;Gefällt mir&quot;-Komponente, eine [tally](tally.md) -Unterklasse, ist ein nützliches Werkzeug, mit dem Mitglieder eine positive Meinung zu einem bestimmten Inhalt äußern können, indem sie einfach das Herzsymbol auswählen.

Das Platzieren mehrerer Instanzen einer &quot;Gefällt mir&quot;-Komponente auf derselben Seite ist zulässig. Jede Instanz muss mit einer eindeutigen `tally name` Eigenschaft konfiguriert werden.

Anonyme Veröffentlichung von &quot;Gefällt mir&quot;-Klicks wird nicht unterstützt. Site-Besucher müssen sich registrieren und sich anmelden, um an &quot;Gefällt mir&quot;teilzunehmen. Der angemeldete Besucher (Member) kann jederzeit ein- und ausgeschaltet werden.

## Grundlagen für clientseitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/tally/components/hbs/liken</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließbar</strong></a></td>
   <td>Ja - Eigenschaften können im <i>Designmodus bearbeitet </i>werden</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td> cq.social.hbs.liking</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td><p> /libs/social/tally/components/hbs/liking/liking.hbs<br /> /libs/social/tally/components/hbs/liking/activity-icon.hbs<br /> /libs/social/tally/components/hbs/liking/activity-title.hbs</p> </td>
  </tr>
  <tr>
   <td><strong>CSS</strong></td>
   <td> /libs/social/tally/components/hbs/liking/clientlibs/likingcomponent.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td><p>Siehe <a href="liking.md">Verwenden von "Gefällt mir"</a></p> </td>
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Tally-APIs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Tal-Endpunkte](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Zugreifen auf gepostete Abstimmungen {#accessing-posted-voting-ugc}

UGC sollte mithilfe einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Speichers](working-with-srp.md) für UGC Programmierungszugriff auf UGC, unabhängig von der gewählten Datenspeicherung (wie ASRP, MSRP oder JSRP).

**Speicherort und Format des UGC im Repository können ohne Warnung** geändert werden.

Siehe:

* [Übersicht über](srp.md) den Datenspeicherung Resource Provider - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP Dienstprogrammmethoden und Beispiele.
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) - Codierungsrichtlinien.
* [SocialUtils Refactoring](socialutils.md) - Zuordnen von nicht mehr unterstützten Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.

