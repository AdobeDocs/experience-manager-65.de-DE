---
title: Essentials zur Abstimmung
seo-title: Essentials zur Abstimmung
description: Übersicht über die Abstimmungskomponente
seo-description: Übersicht über die Abstimmungskomponente
uuid: ed0a771d-1c14-4fbf-ab6a-a028e5ee2e2a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 1a947a06-6a5c-4be9-b2fa-e5fa809ff3b8
translation-type: tm+mt
source-git-commit: 0b25d956c19c5fc5d79f87b292a0c61a23e5d66a

---


# Essentials zur Abstimmung {#voting-essentials}

Die stimmberechtigte Komponente, eine [tally](tally.md) -Unterklasse, ist ein nützliches Werkzeug, mit dem Mitglieder einen bestimmten Inhalt bewerten können, indem sie einfach Pfeiltasten nach oben oder unten wählen, um ihre Meinung zu äußern.

Die Platzierung mehrerer Instanzen einer stimmberechtigten Komponente auf derselben Seite ist zulässig. Jede Instanz muss mit einer eindeutigen `tally name` Eigenschaft konfiguriert werden.

Anonyme Entsendung einer Stimme wird nicht unterstützt. Site-Besucher müssen sich nur einmal registrieren und sich anmelden, um an der Abstimmung teilzunehmen. Der unterzeichnete Besucher (Mitglied) kann ihre Stimme jederzeit ändern.

## Grundlagen für clientseitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/tally/components/hbs/stimmberechtigt</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließbar</strong></a></td>
   <td>Ja - Eigenschaften können im <i>Designmodus bearbeitet </i>werden</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td> cq.social.hbs.stimmte</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td><p> /libs/social/tally/components/hbs/voting/voting.hbs<br /> /libs/social/tally/components/hbs/voting/activity-title.hbs</p> </td>
  </tr>
  <tr>
   <td><strong>CSS</strong></td>
   <td> /libs/social/tally/components/hbs/voting/clientlibs/votingcomponent.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td><p>Siehe, <a href="voting.md">Abstimmungen</a></p> </td>
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

* [Übersicht über](srp.md) den Datenspeicherung Resource Provider - Einführung und Übersicht über die Repository-Nutzung
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) - Richtlinien für die Kodierung
* [SocialUtils Refactoring](socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden

