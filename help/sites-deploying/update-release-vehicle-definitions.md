---
title: Definitionen des Releasebilds aktualisieren
seo-title: Definitionen des Releasebilds aktualisieren
description: Dieser Artikel beschreibt die verschiedenen AEM-Versionen, einschließlich Vollversionen, Feature Packs und Service Packs.
seo-description: Dieser Artikel beschreibt die verschiedenen AEM-Versionen, einschließlich Vollversionen, Feature Packs und Service Packs.
uuid: 388fb6f5-0249-41e2-a460-1bb4cd0f8494
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 32695db5-d62d-4959-8a24-3d56b4a19904
translation-type: tm+mt
source-git-commit: b827c8acb1db158060d209c819fc72ffbfeca65f

---


# Definitionen für AEM Update Release Release Vehicle{#update-release-vehicle-definitions}

Dieses Dokument enthält Einzelheiten zu den verschiedenen Versionen von Adobe Experience Manager (AEM), einschließlich Vollversionen, Feature Packs und Services Packs, die Adobe für Kunden bereitstellt.

>[!Note]
>
>Versionsplan für AEM-Updateversionen finden Sie im Fahrplan für [AEM-Updateversionen](https://helpx.adobe.com/experience-manager/update-releases-roadmap.html)

## Vollversion {#full-release}

<table>
 <tbody>
  <tr>
   <td><strong>Definition</strong></td>
   <td>
    <ul>
     <li>Geplante Veröffentlichung</li>
     <li>Unterstützt Aktualisierungspfade für bestimmte Versionen, die in den Versionshinweisen definiert sind</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Benennung </strong></td>
   <td>
    <ul>
     <li>Die Versionsnummern für größere Releases steigen nach der Formel X+1.Y.Z. </li>
     <li>Versionsnummern für kleinere Releases steigen je nach Formel X.Y+1.Z</li>
    </ul> <p>Dabei ist X die primäre Versionsnummer, Y die sekundäre Versionsnummer und Z die Patch-Nummer.</p> </td>
  </tr>
  <tr>
   <td><strong>Lieferumfang </strong></td>
   <td>
    <ul>
     <li>Neue Funktionen</li>
     <li>Verbesserungen</li>
     <li>Fehlerbehebungen</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Dokumentation</strong></td>
   <td>
    <ul>
     <li>Versionshinweise finden Sie im Dokumentationsportal</li>
     <li>Dokumentation zu Funktionen, Verbesserungen und Fehlerbehebungen finden Sie im Dokumentationsportal</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Veröffentlichungsintervall </strong></td>
   <td>Jährlich</td>
  </tr>
  <tr>
   <td><strong>Verfügbarkeit und Installation </strong></td>
   <td>
    <ul>
     <li>Lieferbar als eigenständiges Produktinstallationsprogramm</li>
     <li>Verfügbar auf der Lizenzierungs-Website und auf der Website für Managed Services</li>
     <li>Eventuelle Migration zum Inhaltsrepository</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Teststufe </strong></td>
   <td>Vollständige Validierung durch Qualitätssicherung</td>
  </tr>
 </tbody>
</table>

## Service Pack {#service-pack}

<table>
 <tbody>
  <tr>
   <td><strong>Definition</strong></td>
   <td>
    <ul>
     <li>Geplante Veröffentlichung</li>
     <li>Derzeit kann kein Rollback durchgeführt werden</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Benennung </strong></td>
   <td>
    <ul>
     <li>Patch-Versionsnummer ist eine einstellige Zahl</li>
     <li>Erhöhen Sie nach der Installation die Zahl des installierten Patch für die Versionsnummer, basierend auf der Formel X.Y.Z.SPx.</li>
     <li>Dabei ist X die primäre Versionsnummer, Y die sekundäre Versionsnummer und Z die Patch-Nummer. x ist die Service-Pack-Nummer.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Lieferumfang </strong></td>
   <td>
    <ul>
     <li>Neue Funktionen</li>
     <li>Verbesserungen</li>
     <li>Fehlerbehebungen</li>
     <li>Häufig verwendete Funktionspakete (falls vorhanden)</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Dokumentation</strong></td>
   <td>
    <ul>
     <li>Versionshinweise im Dokumentationsportal</li>
     <li>Dokumentation zu Funktionen, Verbesserungen, Fehlerbehebungen im Dokumentationsportal</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Veröffentlichungsintervall </strong></td>
   <td>Vierteljährlich</td>
  </tr>
  <tr>
   <td><strong>Verfügbarkeit und Installation </strong></td>
   <td>
    <ul>
     <li>Wird als Paket bereitgestellt</li>
     <li>Steht über Package Share zur Verfügung</li>
     <li>Vorhandene funktionale Installation erforderlich</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Teststufe </strong></td>
   <td>
    <ul>
     <li>Alle für die Qualitätssicherung validierten Fehlerbehebungen</li>
     <li>Gesamte Paketsicherheit mit Automatisierungsläufen</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Cumulative Fix Pack  {#cumulative-fix-pack-aem}

<table>
 <tbody>
  <tr>
   <td><strong>Definition</strong></td>
   <td>
    <ul>
     <li>Einzelauslieferungsmodell von Korrekturen</li>
     <li>Aggregator-Inhaltspaket mit Inhaltspaket einzelner Komponenten</li>
     <li>CFPs sind ein Rollover von Hotfixes, und es gibt keine Verbesserungen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Benennung </strong></td>
   <td><p>X.Y.Z.CFPx</p> <p>Dabei ist X die primäre Versionsnummer, Y die sekundäre Versionsnummer und Z die Patch-Nummer. x ist die Nummer des Cumulative Service Packs.</p> </td>
  </tr>
  <tr>
   <td><strong>Lieferumfang </strong></td>
   <td><p>CFP ist ein kumulatives Fixpack, das Korrekturen aller Komponenten bis zu einem bestimmten Datum enthält. Wenn ein Kunde z. B. CFP3 anwendet, gilt CFP3 = CFP1 + CFP2.</p> </td>
  </tr>
  <tr>
   <td><strong>Dokumentation</strong></td>
   <td>Versionshinweise im Dokumentationsportal</td>
  </tr>
  <tr>
   <td><strong>Veröffentlichungsintervall </strong></td>
   <td>Quaterly</td>
  </tr>
  <tr>
   <td><strong>Verfügbarkeit und Installation </strong></td>
   <td>
    <ul>
     <li>Wird als Paket bereitgestellt</li>
     <li>Steht über Package Share zur Verfügung</li>
     <li>Abhängig vom neuesten Service Pack veröffentlicht</li>
     <li>Die CFP ist selbstständig. Kunden müssen sich nicht über die Suche nach/das Auflösen von Abhängigkeiten den Kopf zerbrechen. CFPs sollten nach dem zuletzt veröffentlichten Service Pack installiert werden.</li>
     <li>CFPs können als ein Paket installiert werden und verbessern so das Kundenerlebnis.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Teststufe </strong></td>
   <td>Auf Integration validierte Qualitätssicherung und Regressionstests</td>
  </tr>
 </tbody>
</table>

## Cumulative Oak Fix Pack {#oak-cumulative-fix-pack}

<table>
 <tbody>
  <tr>
   <td><strong>Definition</strong></td>
   <td>
    <ul>
     <li>Ähnlich wie eine Standard-CFP, enthält jedoch nur Korrekturen zu Eichen</li>
     <li>COFP ist selbstständig (keine Abhängigkeiten). Kunden müssen sich nicht über die Suche nach/das Auflösen von Abhängigkeiten den Kopf zerbrechen. [1]</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Benennung </strong></td>
   <td>oak &lt;version&gt;</td>
  </tr>
  <tr>
   <td><strong>Lieferumfang </strong></td>
   <td>COFP ist ein kumulatives Fix Pack mit Fehlerbehebungen aller Oak Komponenten für eine bestimmte 1.x Version. Wenn der Kunde z. B. COHF 1.x.3 anwendet, gilt: COHF 1.x.3. = COHF 1.x.1 + COHF 1.x.2.</td>
  </tr>
  <tr>
   <td><strong>Dokumentation</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Veröffentlichungsintervall </strong></td>
   <td><p>Erforderlich</p> </td>
  </tr>
  <tr>
   <td><strong>Verfügbarkeit und Installation </strong></td>
   <td>
    <ul>
     <li>Der COFP-Installationsprozess wurde vereinfacht, um die Kundenerfahrung zu verbessern. (Kunden können ein einziges Paket für alle Komponenten installieren.)</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Teststufe </strong></td>
   <td><p>Qualitätssicherung validiert</p> </td>
  </tr>
 </tbody>
</table>

## Hotfix {#hot-fix}

<table>
 <tbody>
  <tr>
   <td><strong>Definition</strong></td>
   <td><p>Paket, das eine oder mehrere Dateien enthält, die zur Behebung eines Produktfehlers erstellt wurden, der wesentliche Dienste erheblich beeinträchtigt oder den Geschäftsbetrieb erheblich beeinträchtigt. </p> </td>
  </tr>
  <tr>
   <td><strong>Benennung </strong></td>
   <td>cq-&lt;Release-Version&gt;-hotfix-&lt;Hotfix-ID&gt;-&lt;Hotfix-Version&gt;</td>
  </tr>
  <tr>
   <td><strong>Lieferumfang </strong></td>
   <td>Beinhaltet Korrekturen für ein bestimmtes Problem</td>
  </tr>
  <tr>
   <td><strong>Dokumentation</strong></td>
   <td>Versionshinweise zu den öffentlichen Hotfixes sind nur nach Kundenanfragen über das AEM-Support-Portal verfügbar.</td>
  </tr>
  <tr>
   <td><strong>Veröffentlichungsintervall </strong></td>
   <td>Erforderlich</td>
  </tr>
  <tr>
   <td><strong>Verfügbarkeit und Installation </strong></td>
   <td>
    <ul>
     <li>Wird als Paket bereitgestellt</li>
     <li>Steht über Package Share zur Verfügung</li>
     <li>Abhängig vom neuesten Service Pack veröffentlicht</li>
     <li>Die meisten Hotfixes sind eigenständig, sofern nicht anders angegeben. Sie können in beliebiger Reihenfolge installiert werden. Sie können über die Registerkarte „Package Share Details“ des Elements „Abhängigkeiten“ verifiziert werden.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Teststufe </strong></td>
   <td>
    <ul>
     <li>Validiert durch die Kundenunterstützung</li>
     <li>Für AEM-Hotfixes gilt nicht die gleiche Qualitätssicherung wie für Service Packs oder Produktversionen. Daher sollten sie zuerst in einer Staging-Umgebung im Zuge des Qualitätsbereitstellungsprozesses geprüft werden.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Überlagerung {#overlay}

<table>
 <tbody>
  <tr>
   <td><strong>Definition</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Benennung </strong></td>
   <td>overlay-&lt;Ticket-ID&gt;</td>
  </tr>
  <tr>
   <td><strong>Lieferumfang </strong></td>
   <td>Fehlerbehebung für eine JS- oder JSP-Datei</td>
  </tr>
  <tr>
   <td><strong>Dokumentation</strong></td>
   <td>Keine</td>
  </tr>
  <tr>
   <td><strong>Veröffentlichungsintervall </strong></td>
   <td>Erforderlich</td>
  </tr>
  <tr>
   <td><strong>Verfügbarkeit und Installation </strong></td>
   <td>
    <ul>
     <li>Als Paket von der AEM-Kundenunterstützung bereitgestellt</li>
     <li>Nicht unbedingt in Service Packs oder Vollversionen enthalten</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Teststufe </strong></td>
   <td>Validiert durch die Kundenunterstützung</td>
  </tr>
 </tbody>
</table>

## Feature Pack {#feature-pack}

<table>
 <tbody>
  <tr>
   <td><strong>Definition</strong></td>
   <td>
    <ul>
     <li>Feature Packs sind Zusatzfunktionalitäten und werden über Service Packs bereitgestellt. Wenn eine AEM-Version ihr letztes Service Pack veröffentlicht hat, stellt Adobe in Zukunft kein Feature Pack dafür bereit.</li>
     <li>Die FPs enthalten Produktverbesserungen, die für eine spätere Produktversion geplant sind, aber aufgrund der Entscheidung des Produktmanagements von Adobe frühzeitig bereitgestellt werden.</li>
     <li>Features werden immer mit der nächsten Hauptversion zusammengeführt und dann in die vom Kunden benötigte AEM-Version zurückportiert.</li>
     <li>Feature Packs mit Funktionen von allgemeinem Interesse und GA Feature Packs werden mit dem nächsten Service Pack zusammengeführt</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Benennung </strong></td>
   <td>cq-&lt;Release-Version&gt;-featurepack-&lt;Featurepack-ID&gt;-&lt;Featurepack-Version&gt;</td>
  </tr>
  <tr>
   <td><strong>Lieferumfang </strong></td>
   <td>
    <ul>
     <li>Neue Funktionen</li>
     <li>Verbesserungen</li>
     <li>Fehlerkorrekturen (inkrementelle Produktaktualisierungen)</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Dokumentation</strong></td>
   <td>Die Dokumentation ist unter helpx.adobe.com verfügbar.</td>
  </tr>
  <tr>
   <td><strong>Veröffentlichungsintervall </strong></td>
   <td>Abhängig vom Produktbereich</td>
  </tr>
  <tr>
   <td><strong>Verfügbarkeit und Installation </strong></td>
   <td>
    <ul>
     <li>Wird über Service Packs bereitgestellt</li>
     <li>Steht über Package Share zur Verfügung. Kunden akzeptieren die Geschäftsbedingungen von Adobe über Package Share.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Teststufe </strong></td>
   <td>General Availability-Feature Packs werden durch die Qualitätssicherung validiert.</td>
  </tr>
 </tbody>
</table>

* [1]: OAK-Korrekturen werden nicht als einzelne Hotfixes bereitgestellt. Sie sind jedoch im Lieferumfang des nachfolgenden Cumulative Oak Hot Fix enthalten. Bei Bedarf kann ein Diagnose-Build zusätzlich zum aktuellen COFP bereitgestellt werden. Eine Vorbedingung hierfür ist, dass der Kunde das aktuelle COFP ausgeführt hat. Diagnose-Builds bieten nur die Qualitätssicherungsstufe eines Hotfixes. Sie bieten nicht dieselbe Qualitätssicherungsstufe wie ein Cumulative Fix Pack, ein Service Pack oder eine Produktversion. Die endgültige Fehlerbehebung wird mit der nächsten GFP geliefert.

