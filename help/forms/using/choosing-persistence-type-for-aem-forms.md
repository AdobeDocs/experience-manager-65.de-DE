---
title: Wählen eines Persistenztyps für eine AEM Forms-Installation
seo-title: Wählen eines Persistenztyps für eine AEM Forms-Installation
description: Wählen Sie einen Persistenztyp mit Bedacht aus. Diese Funktion ermöglicht Ihnen, eine leistungsstarke und skalierbare AEM Forms-Umgebung zu erstellen.
seo-description: Wählen Sie einen Persistenztyp mit Bedacht aus. Diese Funktion ermöglicht Ihnen, eine leistungsstarke und skalierbare AEM Forms-Umgebung zu erstellen.
uuid: 1c692502-5039-4757-9358-1772772b3904
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: a972fb35-38a7-4b83-99bd-6a6dddf8043b
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 100%

---


# Wählen eines Persistenztyps für eine AEM Forms-Installation {#choosing-a-persistence-type-for-an-aem-forms-installation}

Wählen Sie einen Persistenztyp mit Bedacht aus. Diese Funktion ermöglicht Ihnen, eine leistungsstarke und skalierbare AEM Forms-Umgebung zu erstellen.

Persistenz bezeichnet die Methode, Inhalte physisch zu speichern. Es definiert die tatsächliche Datenstruktur- und Speichermethode für die Daten. MicroKernels dienen als Persistenzmanager in AEM Forms. AEM Forms unterstützt die Persistenztypen (MicroKernals) TarMK, MongoMK und RDBMK. Sie können je nach Zweck und Veröffentlichungstyp (Einzelserver oder Cluster) einer AEM Forms-Instanz einen Persistenztyp für AEM auswählen.

>[!NOTE]
>
>LiveCycle ES4 SP1 verwendet TarPM-Persistenz zum Speichern von Inhalten.

In der folgenden Tabelle werden alle unterstützten Persistenztypen zusammen mit verschiedenen Parametern aufgeführt, um einen Persistenztyp für Ihre Umgebung auszuwählen:

<table>
 <tbody>
  <tr>
   <th><strong>Installations/Kosten</strong></th>
   <th><strong>TarMK</strong></th>
   <th><strong>MongoMk</strong></th>
   <th><strong>RDBMK</strong></th>
  </tr>
  <tr>
   <th><strong>Eigenständige Einrichtung</strong></th>
   <td>Unterstützt<br /> </td>
   <td>Unterstützt</td>
   <td>Unterstützt</td>
  </tr>
  <tr>
   <th><strong>Cluster-Einrichtung</strong></th>
   <td>Nicht unterstützt</td>
   <td>Unterstützt</td>
   <td>Unterstützt</td>
  </tr>
  <tr>
   <th><strong>Lizenzkosten</strong></th>
   <td>Im Lieferumfang von AEM enthalten </td>
   <td>Separate Lizenz erforderlich</td>
   <td>Separate Lizenz erforderlich</td>
  </tr>
 </tbody>
</table>

TarMK ist auf Leistung ausgerichtet, während bei MongoMK und RDBMK die Skalierbarkeit im Vordergrund steht. Adobe empfiehlt TarMK als Standardpersistenztechnologie für alle AEM Forms-Bereitstellungsszenarien für die Autoren- und Veröffentlichungsinstanz, außer in Fällen, die im Abschnitt [ Mongo auswählt oder ein relationale Datenbank-Microkernel über TarMK](#p-choosing-mongo-or-a-relational-database-microkernel-over-tarmk-p) erläutert werden.

Die Liste der unterstützten Microkernel finden Sie in den Artikeln [Technische Anforderungen für AEM Forms on OSGi](/help/sites-deploying/technical-requirements.md) oder [Unterstützte Plattformkombinationen für AEM Forms on JEE](/help/forms/using/aem-forms-jee-supported-platforms.md).

## Wählen eines Microkernel des Typs Mongo oder relationale Datenbank über TarMK {#choosing-mongo-or-a-relational-database-microkernel-over-tarmk}

Eine skalierbare (geclusterte) AEM Forms-Umgebung besteht aus einem Satz von zwei oder mehr horizontal konfigurierten aktiven Autoreninstanzen. Sie können mehr als eine Autoreninstanz ausführen, wenn ein einzelner Server zur Unterstützung aller gleichzeitigen Authoring-Aktivitäten nicht mehr ausreicht.

Für eine skalierbare (geclusterte) AEM Forms on JEE-Umgebung werden ausschließlich die Persistenztypen MongoMK und RDBMK unterstützt. Die Anzahl der Server oder die Größe der skalierbaren Umgebung variiert je nach Installation. Eine Liste von Überlegungen und Beispielen finden Sie in den Artikeln [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md) oder [Architektur- und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md). Ausführlichere Informationen zur Kapazitätsplanung für AEM Forms in Verbindung mit RDBMK und TarMK erhalten Sie auch, indem Sie sich an den AEM Forms-Support wenden.
