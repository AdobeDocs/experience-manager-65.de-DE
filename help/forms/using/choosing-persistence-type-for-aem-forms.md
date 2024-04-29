---
title: Wählen eines Persistenztyps für eine AEM Forms-Installation
description: Wählen Sie einen Persistenztyp mit Bedacht aus. Er hilft Ihnen beim Aufbau einer effizienten und skalierbaren AEM Forms-Umgebung.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
role: Admin
exl-id: 621fe107-f4ac-42b1-8c7b-8abbcaac7380
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '372'
ht-degree: 100%

---

# Wählen eines Persistenztyps für eine AEM Forms-Installation {#choosing-a-persistence-type-for-an-aem-forms-installation}

Wählen Sie einen Persistenztyp mit Bedacht aus. Er hilft Ihnen beim Aufbau einer effizienten und skalierbaren AEM Forms-Umgebung.

Persistenz ist die Methode zum Speichern von Inhalten auf den physischen Speichern. Sie definiert die tatsächliche Datenstruktur und den Speichermechanismus für die Daten. MicroKernels fungieren als Persistenz-Manager in AEM Forms. AEM Forms unterstützt Persistenz (MicroKernels) vom Typ TarMK, MongoMK und RDBMK. Sie können je nach Zweck und Bereitstellungstyp (Einzel-Server, Farm oder Cluster) einer AEM Forms-Instanz einen Persistenztyp für AEM Forms auswählen.

>[!NOTE]
>
>LiveCycle ES4 SP1 verwendet TarPM-Persistenz zum Speichern von Inhalten.

In der folgenden Tabelle werden alle unterstützten Persistenztypen zusammen mit verschiedenen Parametern aufgeführt, um Ihnen die Auswahl eines Persistenztyps für Ihre Umgebung zu erleichtern:

<table>
 <tbody>
  <tr>
   <th><strong>Installationstyp/Kosten</strong></th>
   <th><strong>TarMK</strong></th>
   <th><strong>MongoMK</strong></th>
   <th><strong>RDBMK</strong></th>
  </tr>
  <tr>
   <th><strong>Eigenständige Einrichtung</strong></th>
   <td>Unterstützt<br /> </td>
   <td>Unterstützt</td>
   <td>Unterstützt </td>
  </tr>
  <tr>
   <th><strong>Cluster-Einrichtung</strong></th>
   <td>Nicht unterstützt</td>
   <td>Unterstützt</td>
   <td>Unterstützt </td>
  </tr>
  <tr>
   <th><strong>Lizenzkosten</strong></th>
   <td>Im Lieferumfang von AEM enthalten </td>
   <td>Separate Lizenz erforderlich</td>
   <td>Separate Lizenz erforderlich</td>
  </tr>
 </tbody>
</table>

TarMK ist auf Leistung ausgelegt, während MongoMK und RDBMK auf Skalierbarkeit ausgelegt sind. Adobe empfiehlt TarMK als Standardpersistenztechnologie für alle AEM Forms-Bereitstellungsszenarien für die Autoren- und Veröffentlichungsinstanz, außer in Fällen, die im Abschnitt [Mongo auswählt oder ein relationale Datenbank-Microkernel über TarMK](#p-choosing-mongo-or-a-relational-database-microkernel-over-tarmk-p) erläutert werden.

Die Liste der unterstützten Mikro-Kernels finden Sie in den Artikeln [ Technische Anforderungen für AEM Forms auf OSGi](/help/sites-deploying/technical-requirements.md) oder [Von AEM Forms auf JEE unterstützte Plattformkombinationen](/help/forms/using/aem-forms-jee-supported-platforms.md).

## Auswählen von Mongo oder eines relationalen Datenbank-Mikro-Kernels anstelle von TarMK {#choosing-mongo-or-a-relational-database-microkernel-over-tarmk}

Eine skalierbare (Cluster-) AEM Forms-Umgebung ist ein Satz von zwei oder mehr horizontal konfigurierten, aktiven Autoreninstanzen. Sie können mehr als eine Autoreninstanz ausführen, wenn ein einzelner Server, der alle gleichzeitigen Autorenaktivitäten unterstützt, nicht mehr tragbar ist.

Für eine skalierbare (Cluster-) AEM Forms auf JEE-Umgebung werden nur die Persistenztypen MongoMK und RDBMK unterstützt. Die Anzahl der Server oder die Größe der skalierbaren Umgebung variiert je nach Installation. Eine Liste mit Überlegungen und Beispielen finden Sie in den Artikeln [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md) und oder [ Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md). Sie können sich auch an den AEM Forms-Support wenden, um detaillierte Informationen zur Kapazitätsplanung für AEM Forms mit RDBMK und TarMK zu erhalten.
