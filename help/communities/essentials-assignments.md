---
title: Zuweisungsgrundlagen
seo-title: Zuweisungsgrundlagen
description: Übersicht über Zuweisungsfunktionen für Aktivierungs-Communities
seo-description: Übersicht über Zuweisungsfunktionen für Aktivierungs-Communities
uuid: e49fce26-1091-4f37-93e8-c4ec85371811
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 6bac681e-59e1-4786-9c50-6679c936cfd1
docset: aem65
exl-id: 75cef5da-4f93-4721-99c0-ad44c8ab76d4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 14%

---

# Zuweisungsgrundlagen {#assignments-essentials}

Lesen Sie weiter, um mehr über die wesentlichen Informationen für die Arbeit mit der Zuweisungsfunktion von [Aktivierungs-Community](/help/communities/overview.md#enablement-community)-Sites zu erfahren.

Die Zuweisungsfunktion ist die Möglichkeit, Aktivierungsressourcen und Lernpfade Mitgliedern von Aktivierungsgemeinschaften zuzuweisen.

## Grundlagen für Client-seitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/enable/components/hbs/myassigned</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.myassigned<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learning.path</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/enablement/components/hbs/myassigned/myassigned.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/enablement/components/hbs/myassigned/clientlibs/myassigned.css</td>
  </tr>
  <tr>
   <td><strong> properties</strong></td>
   <td>Siehe <a href="/help/communities/assignments.md">Zuweisungsfunktion</a></td>
  </tr>
 </tbody>
</table>

### Abschluss und Erfolgsstatus {#completion-and-success-status}

Abschluss und Erfolgsstatus werden in Berichten und Statusbannern für Zuweisungen verwendet.

Abschlussstatus:

* Nicht zugewiesen
* Nicht gestartet (neu)
* Wird ausgeführt
* Fertig stellen

Erfolgsstatus:

* Unknown
* Bestanden
* Fehler

Die einzigen möglichen Kombinationen aus Abschluss und Erfolgsstatus sind:

| **Abschluss** | **Success** |
|---|---|
| Nicht gestartet | unbekannt |
| Wird ausgeführt | unbekannt |
| Fertig stellen | Bestanden |
| Fertig stellen | Fehler |

## Grundlagen für serverseitige {#essentials-for-server-side}

### Zuweisungsfunktion {#assignments-function}

Eine Community-Site-Struktur, die die [Zuweisungsfunktion](/help/communities/functions.md#assignments-function) enthält, enthält eine konfigurierte ` [assignments](/help/communities/assignments.md)`-Komponente.

### Referenz-APIs {#reference-apis}

* [Aktivierungs-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [Reporting-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [Reporting-Analytics-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)
