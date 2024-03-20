---
title: Migration der Assets und Dokumente von AEM Forms
description: Mit dem Migrationsdienstprogramm können Sie Adobe Experience Manager (AEM) Forms-Assets und -Dokumente aus AEM 6.3 Forms oder früheren Versionen in AEM 6.4 Forms migrieren.
content-type: reference
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-strategy: max-2018
docset: aem65
role: Admin
exl-id: 0f9aab7d-8e41-449a-804b-7e1bfa90befd
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1736'
ht-degree: 89%

---

# Migration der Assets und Dokumente von AEM Forms{#migrate-aem-forms-assets-and-documents}

Das Migrationsdienstprogramm konvertiert die [Assets von adaptiven Formularen](../../forms/using/introduction-forms-authoring.md), [Cloud-Konfigurationen](/help/sites-developing/extending-cloud-config.md) und [Correspondence Management-Assets](/help/forms/using/cm-overview.md) von dem in früheren Versionen verwendeten Format in das in Adobe Experience Manager (AEM) 6.5 Forms verwendete Format. Wenn Sie das Migrationsdienstprogramm ausführen, werden folgende Elemente migriert:

* Benutzerdefinierte Komponenten für adaptive Formulare
* Adaptive Formulare und Correspondence Management-Vorlagen
* Cloud-Konfigurationen
* Assets für Correspondence Management und adaptive Formulare

>[!NOTE]
>
>Bei einer nicht ersetzenden Aktualisierung für Correspondence Management-Assets können Sie die Migration jedes Mal ausführen, wenn Sie die Assets importieren. Für die Correspondence Management-Migration muss das Forms-Kompatibilitätspaket installiert worden sein.

## Migrationsansatz {#approach-to-migration}

Sie können ein [Upgrade](../../forms/using/upgrade.md) auf die neueste Version von AEM Forms 6.5 von AEM Forms 6.4, 6.3 oder 6.2 oder eine Neuinstallation durchführen. Je nachdem, ob Sie die vorherige Installation aktualisiert oder eine Neuinstallation durchgeführt haben, müssen Sie einen der folgenden Schritte ausführen:

**Wenn eine ersetzende Aktualisierung erfolgt**

Wenn Sie ein ersetzendes Upgrade durchgeführt haben, verfügt die aktualisierte Instanz bereits über die Assets und Dokumente. Bevor Sie die Assets und Dokumente verwenden können, müssen Sie jedoch das [AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) installieren (enthält das Correspondence-Management-Kompatibilitätspaket).

Dann müssen Sie die Assets und Dokumente aktualisieren, indem Sie das [Migrationsprogramm ausführen](#runningmigrationutility).

**Bei einer nicht ersetzenden Installation**

Wenn es sich um eine nicht ersetzende (neue) Installation handelt, bevor Sie die Assets und Dokumente verwenden können, müssen Sie das [AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) (einschließlich des Correspondence Management-Kompatibilitätspakets) installieren.

Dann müssen Sie Ihr Asset-Paket (zip oder cmp) in das neue Setup importieren und anschließend die Assets und Dokumente aktualisieren, indem Sie das [Migrationsdienstprogramm ausführen](#runningmigrationutility). Adobe empfiehlt, erst nach Ausführung des Migrationsdienstprogramms neue Assets im neuen Setup zu erstellen.

Aufgrund von Änderungen [im Zusammenhang mit der Abwärtskompatibilität](/help/sites-deploying/backward-compatibility.md) haben sich die Speicherorte einiger Ordner im CRX-Repository geändert. Sie müssen Abhängigkeiten (benutzerdefinierte Bibliotheken und Assets) manuell vom vorherigen Setup in eine neue Umgebung exportieren und importieren.

## Vor dem Start der Migration {#prerequisites}

Für Correspondence Management-Assets:

* Für die Assets, die von der vorherigen Plattform importiert werden, wird eine Eigenschaft hinzugefügt: **fd:version=1.0**.
* Seit AEM 6.1 Forms sind Kommentare nicht standardmäßig verfügbar. Die zuvor hinzugefügten Kommentare stehen in den Assets zur Verfügung, sind jedoch nicht automatisch auf der Oberfläche sichtbar. Sie müssen die Eigenschaft „extendedProperties“ in der AEM Forms-Benutzeroberfläche anpassen, um die Kommentare sichtbar zu machen.
* In einigen früheren Versionen wie LiveCycle ES4 wurde Text mit dem Flex RichTextEditor bearbeitet, aber seit AEM 6.1 Forms wird der HTML-Editor verwendet. Dadurch können sich das Rendern und das Erscheinungsbild der Schriftarten, Schriftgrößen und Schriftartränder von früheren Versionen in der Autorenbenutzeroberfläche unterscheiden. Die gerenderten Briefe sehen jedoch gleich aus.
* Listen in Textmodulen wurden verbessert und werden jetzt anders gerendert. Es kann visuelle Unterschiede geben. Adobe empfiehlt, dass Sie die Buchstaben rendern und sie betrachten, wo Sie Listen in Textmodulen verwenden.
* Da Bildinhaltsmodule in DAM-Assets konvertiert und Layouts und Fragmente während der Migration zu Formularen hinzugefügt werden, wird die Eigenschaft „Aktualisiert von“ bei diesen Moduländerungen in „admin“ geändert.
* Der Versionsverlauf der Assets wird nicht migriert und steht nach der Migration nicht zur Verfügung. Der nachfolgende Versionsverlauf wird nach der Migration beibehalten.
* Der Status „Veröffentlichungsbereit“ wird seit AEM 6.1 Forms nicht mehr unterstützt, sodass alle Assets mit dem Status „Veröffentlichungsbereit“ den Status „Geändert“ erhalten.
* Da die Benutzeroberfläche auf AEM Forms 6.3 aktualisiert wird, sind die Schritte für die Anpassung ebenfalls unterschiedlich. Wiederholen Sie die Anpassung, wenn Sie von einer älteren Version als 6.3 migrieren.
* Layout-Fragmente werden von `/content/apps/cm/layouts/fragmentlayouts/1001` nach `/content/apps/cm/modules/fragmentlayouts` verschoben. Der Datenwörterbuchverweis in Assets zeigt Pfad des Datenwörterbuchs anstatt dessen Namens an.
* Alle Tabulatorzeichen, die für die Ausrichtung in Textmodulen verwendet werden, müssen angepasst werden. Weitere Informationen finden Sie unter [Correspondence Management: Anordnen von Text mit Tabulatorabständen](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html).
* Die Asset Composer-Konfigurationen ändern sich zu Correspondence Management-Konfigurationen.
* Assets werden in Ordner mit einem Namen wie „Existing Text“ oder „Existing List“ verschoben.

## Verwenden des Migrationsdienstprogramms {#using-the-migration-utility}

### Ausführen des Migrationsdienstprogramms {#runningmigrationutility}

Führen Sie das Migrationsdienstprogramm aus, bevor Sie Änderungen an den Assets vornehmen oder Assets erstellen. Adobe empfiehlt, das Dienstprogramm erst dann auszuführen, wenn Änderungen an den Assets vorgenommen oder Assets erstellt wurden. Stellen Sie sicher, dass die Benutzeroberfläche von Correspondence Management oder Adaptive Forms-Assets nicht geöffnet ist, während die Migration ausgeführt wird.

Wenn Sie das Migrationsdienstprogramm zum ersten Mal ausführen, wird ein Protokoll unter dem folgenden Pfad und mit dem folgenden Namen erstellt: `\[aem-installation-directory]\cq-quickstart\logs\aem-forms-migration.log`. Dieses Protokoll wird fortlaufend mit Informationen zu Correspondence Management und adaptiven Formularen aktualisiert, beispielsweise zum Verschieben von Assets.

>[!NOTE]
>
>Stellen Sie vor dem Ausführen des Migrationsdienstprogramms sicher, dass Sie ein Backup Ihres CRX-Repositorys erstellt haben.

1. Melden Sie sich in einer Browser-Sitzung bei der AEM-Autoreninstanz als Admin an.

1. Öffnen Sie die folgende URL im Browser:

   https://[*hostname*]:[*port*]/[*context_path*]/libs/fd/foundation/gui/content/migration.html

   Der Browser zeigt vier Optionen an:

   * AEM Forms-Assets-Migration
   * Migration von benutzerdefinierten adaptiven Formularkomponenten
   * Migration von adaptiven Formularvorlagen
   * Migration von AEM Forms-Cloud-Konfigurationen

1. Führen Sie die folgenden Schritte aus, um die Migration durchführen:

   * Migrieren **Assets**, wählen Sie AEM Forms Assets Migration und klicken Sie im nächsten Bildschirm auf **Migration starten**. Die folgenden Elemente werden migriert:

      * Adaptive Formulare
      * Dokumentfragmente
      * Designs
      * Briefe
      * Datenwörterbücher

   >[!NOTE]
   >
   >Während der Asset-Migration treten möglicherweise Warnungen ähnlich der folgenden auf: „Konflikt aufgetreten bei …“. Solche Benachrichtigungen bedeuten, dass Regeln für einige Komponenten in adaptiven Formularen nicht migriert werden konnten. Beispiel: Wenn bei einer Komponente ein Ereignis auftritt, das sowohl Regeln als auch Skripte umfasst und wenn die Regeln nach einem Skript angewendet werden, wird keine der Regeln für die Komponente migriert. Allerdings können Sie [diese Regeln migrieren, indem Sie den Regeleditor für das Authoring von adaptiven Formularen öffnen](#migrate-rules).

   * Um benutzerdefinierte Komponenten des adaptiven Formulars zu migrieren, wählen Sie **Migration benutzerdefinierter Forms-Komponenten** und wählen Sie auf der Seite &quot;Migration benutzerdefinierter Komponenten&quot;die Option **Migration starten**. Die folgenden Elemente werden migriert:

      * benutzerdefinierte Komponenten für adaptive Formulare
      * Komponentenüberlagerungen, falls vorhanden

   * Um adaptive Formularvorlagen zu migrieren, wählen Sie **Adaptive Forms-Vorlagenmigration** und wählen Sie auf der Seite &quot;Migration benutzerdefinierter Komponenten&quot;die Option **Migration starten**. Die folgenden Elemente werden migriert:

      * Adaptive Formularvorlagen, die unter `/apps` oder `/conf` mit dem AEM-Vorlageneditor erstellt wurden.

   * Migrieren Sie die Cloud-Konfigurations-Services von AEM Forms, um das neue kontextbezogene Cloud-Service-Paradigma zu nutzen, das die Touch-optimierte Benutzeroberfläche (unter `/conf`) umfasst. Wenn Sie Services der Cloud-Konfiguration von AEM Forms migrieren, werden die Cloud-Services in `/etc` nach `/conf` verschoben. Wenn keine Cloud-Service-Anpassungen vorliegen, die von den veralteten Pfaden (`/etc`) abhängen, empfiehlt Adobe, das Migrationsdienstprogramm direkt nach dem Upgrade auf 6.5 auszuführen und für alle weiteren Arbeiten die Touch-optimierte Cloud-Konfigurationsbenutzeroberfläche zu verwenden. Wenn Sie über Anpassungen für die bereits vorhandenen Cloud-Services verfügen, setzen Sie die Verwendung der klassischen Benutzeroberfläche bei der Aktualisierung so lange fort, bis die Anpassungen für die migrierten Pfade (`/conf`) abgeschlossen sind, und führen Sie erst dann das Migrationsdienstprogramm aus.

   Migrieren **AEM Forms Cloud Services**, die Folgendes enthalten, wählen Sie AEM Forms Cloud-Konfigurationsmigration (die Cloud-Konfigurationsmigration ist unabhängig vom AEMFD-Kompatibilitätspaket). Wählen Sie die Migration zu AEM Forms Cloud-Konfigurationen und dann auf der Seite &quot;Konfigurationsmigration&quot;die Option **Migration starten**:

   * Cloud-Services für das Formulardatenmodell

      * Quellpfad: `/etc/cloudservices/fdm`
      * Zielpfad: `/conf/global/settings/cloudconfigs/fdm`

   * reCAPTCHA

      * Quellpfad: `/etc/cloudservices/recaptcha`
      * Zielpfad: `/conf/global/settings/cloudconfigs/recaptcha`

   * Adobe Sign

      * Quellpfad: `/etc/cloudservices/echosign`
      * Zielpfad: `/conf/global/settings/cloudconfigs/echosign`

   * Cloud-Services für Typekit

      * Quellpfad: `/etc/cloudservices/typekit`
      * Zielpfad: `/conf/global/settings/cloudconfigs/typekit`

   Im Browser-Fenster wird während der Migration Folgendes angezeigt:

   * Wenn die Assets aktualisiert werden: Assets werden erfolgreich aktualisiert.
   * Wenn die Migration abgeschlossen ist: Die Migration für Assets wurde abgeschlossen.

   Wenn das Migrationsdienstprogramm ausgeführt wird, tut es Folgendes:

   * **Fügt den Assets die Tags hinzu**: Fügt das Tag „Correspondence Management: Migrierte Assets“/„Adaptive Formulare: Migrierte Assets“ zu den migrierten Assets hinzu, damit Benutzende die migrierten Assets ermitteln können. Wenn Sie das Migrationsdienstprogramm ausführen, werden alle im System vorhandenen Assets mit „Migriert“ markiert. 
   * **Erstellt Tags**: Die Kategorien und Unterkategorien, die im Vorgängersystem vorhanden sind, werden als Tags erstellt, und dann werden diese Tags den entsprechenden Correspondence Management-Assets in AEM zugeordnet. Beispielsweise werden eine Kategorie (Schadensmeldungen) und eine Unterkategorie (Schadensmeldungen) einer Briefvorlage als Tags generiert.

1. Fahren Sie nach der Ausführung des Migrationsdienstprogramms mit den [Systemverwaltungsaufgaben](#housekeepingtasks) fort.

#### Migrieren von Regeln mithilfe des Regeleditors {#migrate-rules}

Diese Komponenten können migriert werden, indem sie im Regeleditor im Editor für adaptive Formulare geöffnet werden.

* Um Regeln und Skripte (die bei einer Aktualisierung von 6.3 nicht erforderlich sind) in benutzerdefinierten Komponenten zu migrieren, wählen Sie Adaptive Forms Custom Components Migration (Adaptive-Komponentenmigration) und klicken Sie im nächsten Bildschirm auf &quot;Migration starten&quot;. Die folgenden Elemente werden migriert:

   * Regeln und Skripten, erstellt mithilfe des Regel-Editors (6.1 FP1 und höher)

   * Skripte, erstellt mithilfe der Skript-Registerkarte in der Benutzeroberfläche von Version 6.1 oder niedriger

* Um Vorlagen zu migrieren (bei einer Aktualisierung von 6.3 und 6.4 nicht erforderlich), wählen Sie Adaptive Forms-Vorlagenmigration und wählen Sie im nächsten Bildschirm die Option Migration starten aus. Die folgenden Elemente werden migriert:

   * Alte Vorlagen – Vorlagen für adaptive Formulare, erstellt unter /apps mithilfe von AEM 6.1 Forms oder niedriger. Dazu gehören die Skripten, die in den Vorlagenkomponenten definiert wurden.

   * Neue Vorlagen: Vorlagen für adaptive Formulare, die mithilfe des Vorlageneditors unter `/conf` erstellt werden. Das umfasst die Migration von Regeln und Skripten, die mithilfe des Regeleditors erstellt wurden.

### Systemverwaltungsaufgaben nach Ausführung des Migrationsdienstprogramms {#housekeepingtasks}

Nachdem Sie das Migrationsdienstprogramm ausgeführt haben, führen Sie folgende Systemverwaltungsaufgaben durch:

1. Stellen Sie sicher, dass XFA-Version 3.3 oder eine spätere Version von Layouts und Fragment-Layouts verwendet wird. Wenn Sie Layouts und Fragment-Layouts einer älteren Version benutzen, könnte es Probleme beim Rendern des Briefs geben. Um älteres XFA auf die neueste Version zu aktualisieren, führen Sie folgende Schritte aus:

   1. [Herunterladen von XFA- als ZIP-Datei](../../forms/using/import-export-forms-templates.md#p-import-and-export-assets-in-correspondence-management-p) aus der Forms-Benutzeroberfläche.
   1. Extrahieren Sie die Datei.
   1. Öffnen Sie die XFA-Datei im neuesten Designer und speichern Sie sie. Die Version der XFA wird auf die neueste Version aktualisiert.
   1. Laden Sie die XFA in der Forms-Benutzeroberfläche hoch.

1. Veröffentlichen Sie alle Assets, die im vorherigen System vor der Migration veröffentlicht wurden. Das Migrationsdienstprogramm aktualisiert die Assets nur in der Autoreninstanz. Um die Assets in den Veröffentlichungsinstanzen zu aktualisieren, müssen Sie die Assets veröffentlichen.

1. In AEM Forms 6.4 und 6.5 haben sich einige Rechte der Forms-Benutzergruppen geändert. Wenn Sie möchten, dass Ihre Benutzenden XDPs und adaptive Forms mit Skripten hochladen oder einen Code-Editor verwenden können, müssen Sie diese zur Gruppe „forms-power-users“ hinzufügen. Ebenso können Vorlagenautorinnen und -autoren den Code-Editor im Regeleditor nicht mehr verwenden. Damit Benutzende den Code-Editor verwenden können, fügen Sie sie der Gruppe „af-template-script-writers“ hinzu. Anweisungen zum Hinzufügen von Benutzenden zu Gruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).
