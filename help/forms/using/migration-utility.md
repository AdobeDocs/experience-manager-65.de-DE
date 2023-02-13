---
title: Migration der Assets und Dokumente von AEM Forms
seo-title: Migrate AEM Forms assets and documents
description: Mithilfe des Migrationsdienstprogramms können Sie Assets und Dokumente von AEM Forms bis Version 6.3 in AEM 6.4 Forms migrieren.
seo-description: The Migration utility allows you to Migrate AEM Forms assets and documents from AEM 6.3 Forms or prior versions to AEM 6.4 Forms.
uuid: a3fdf940-7fc2-441c-91c8-ad66ba47e5f2
content-type: reference
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-strategy: max-2018
discoiquuid: 39dfef85-d047-4b6d-a0f5-92bd77df103b
docset: aem65
role: Admin
exl-id: 0f9aab7d-8e41-449a-804b-7e1bfa90befd
source-git-commit: 9d142ce9e25e048512440310beb05d762468f6a2
workflow-type: ht
source-wordcount: '1743'
ht-degree: 100%

---

# Migration der Assets und Dokumente von AEM Forms{#migrate-aem-forms-assets-and-documents}

Das Migrationsdienstprogramm konvertiert die [Assets von adaptiven Formularen](../../forms/using/introduction-forms-authoring.md), [Cloud-Konfigurationen](/help/sites-developing/extending-cloud-config.md) und [Correspondence Management-Assets](/help/forms/using/cm-overview.md) von dem in früheren Versionen verwendeten Format in das in AEM 6.5 Forms verwendete Format. Wenn Sie das Migrationsdienstprogramm ausführen, werden folgende Elemente migriert:

* Benutzerdefiniert Komponenten für adaptive Formulare
* Adaptive Formulare und Correspondence Management-Vorlagen
* Cloud-Konfigurationen
* Assets für Correspondence Management und adaptive Formulare

>[!NOTE]
>
>Bei einem fehlgeschlagenen Upgrade können Sie für den Fall von Correspondence Management-Assets die Migration jedes Mal ausführen, wenn Sie die Assets importieren. Für die Correspondence Management-Migration muss das Forms-Kompatibilitätspaket installiert sein.

## Verfahren zur Migration {#approach-to-migration}

Sie können [ein Upgrade](../../forms/using/upgrade.md) auf die neueste Version von AEM Forms 6.5 von AEM Forms 6.4, 6.3 oder 6.2 durchführen oder eine Neuinstallation vornehmen. Je nachdem, ob Sie die vorherige Installation aktualisiert oder eine Neuinstallation durchgeführt haben, müssen Sie einen der folgenden Schritte ausführen:

**Im Falle eines direkten Upgrades**

Wenn Sie eine ersetzende Aktualisierung durchgeführt haben, verfügt die aktualisierte Instanz bereits über die Assets und Dokumente. Bevor Sie jedoch die Assets und Dokumente verwenden können, müssen Sie das [AEMFD-Kompatibilitätspaket](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) installieren (enthält das Correspondence-Management-Kompatibilitätspaket).

Dann müssen Sie die Assets und Dokumente aktualisieren, indem Sie das [Migrationsprogramm ausführen](#runningmigrationutility).

**Bei nicht ersetzender Installation**

Bevor Sie die Assets und Dokumente verwenden können, müssen Sie das [AEMFD-Kompatibilitätspaket](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) (einschließlich des Correspondence Management-Kompatibilitätspakets) installieren, wenn es sich um eine dezentrale (neue) Installation handelt.

Dann müssen Sie Ihr Asset-Paket (zip oder cmp) in das neue Setup importieren und dann die Assets und Dokumente aktualisieren, indem Sie das [Migrationsprogramm ausführen](#runningmigrationutility). Adobe empfiehlt, neue Assets auf der neuen Installation erst nach Ausführung des Migrationsprogramms zu erstellen.

Aufgrund der [Abwärtskompatibilität-bezogenen](/help/sites-deploying/backward-compatibility.md) Änderungen werden Speicherorte von einigen Ordnern im CRX-Repository geändert. Exportieren und importieren Sie Abhängigkeiten (benutzerdefinierte Bibliotheken und Assets) vom vorherigen Setup in eine neue Umgebung manuell.

## Vor dem Start der Migration lesen {#prerequisites}

Für Correspondence Management-Assets:

* Für die Assets, die von der vorherigen Plattform importiert werden, wird eine Eigenschaft hinzugefügt: **fd:version=1.0**.
* Seit AEM 6.1 Forms sind Kommentare nicht standardmäßig verfügbar. Die zuvor hinzugefügten Kommentare stehen in den Assets zur Verfügung, sind jedoch nicht automatisch auf der Oberfläche sichtbar. Sie müssen die Eigenschaft „extendedProperties“ in der AEM Forms-Benutzeroberfläche anpassen, um die Kommentare sichtbar zu machen.
* In einigen früheren Versionen, beispielsweise LiveCycle ES4, wurde Text mithilfe von Flex RichTextEditor bearbeitet. Seit AEM 6.1 Forms wird HTML-Editor verwendet. Dadurch können sich die Darstellung und das Erscheinungsbild der Schriftarten, Schriftgrößen und Schriftartränder von früheren Versionen in der Autorenbenutzeroberfläche unterscheiden. Die ausgegebenen Briefe sehen jedoch gleich aus.
* Listen in den Textmodulen wurden verbessert und werden jetzt anders dargestellt. Es gibt möglicherweise visuelle Unterschiede. Wir empfehlen, die Buchstaben an den Stellen darzustellen und anzuzeigen, wo Sie Listen in Textmodulen verwenden. 
* Da Bildinhaltmodule in DAM-Assets konvertiert werden und Layouts und Fragmente während der Migration zu Formularen hinzugefügt werden, wird die Eigenschaft „Aktualisiert von“ bei diesen Moduländerungen in „admin“ geändert.
* Der Versionsverlauf der Assets wird nicht migriert und steht nach der Migration nicht zur Verfügung. Der nachfolgende Versionsverlauf wird nach der Migration beibehalten.
* Der Status „Veröffentlichungsbereit“ wird seit AEM 6.1 Forms nicht mehr unterstützt, sodass alle Assets mit dem Status „Veröffentlichungsbereit“ den Status „Geändert“ erhalten.
* Da die Benutzeroberfläche auf AEM Forms 6.3 aktualisiert wird, sind die Schritte für die Anpassung ebenfalls unterschiedlich. Sie müssen die Anpassung erneut vornehmen, wenn Sie von einer Version vor 6.3 migrieren.
* Layout-Fragmente wurden von /content/apps/cm/layouts/fragmentlayouts/1001 in /content/apps/cm/modules/fragmentlayouts verschoben. Der Datenwörterbuchverweis in Assets zeigt Pfad des Datenwörterbuchs anstatt des Namens an.
* Alle Tabulatorabstände, die für die Ausrichtung von Textmodulen verwendet werden, müssen angepasst werden. Weitere Informationen finden Sie unter [Correspondence Management – verwenden von Tabulatorabständen zum Anordnen von Text](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html).
* Die Asset Composer-Konfigurationen ändern sich zu Correspondence Management-Konfigurationen.
* Assets werden in Ordner mit einem Namen wie „Existing Text“ oder „Existing List“ verschoben.

## Verwenden des Migrationsdienstprogramms  {#using-the-migration-utility}

### Ausführen des Migrationsdienstprogramms  {#runningmigrationutility}

Führen Sie die Migration aus, bevor Sie Änderungen an den Assets vornehmen oder Assets erstellen. Wir empfehlen, das Dienstprogramm erst dann auszuführen, wenn Änderungen an den Assets vorgenommen wurden oder Assets erstellt wurden. Stellen Sie sicher, dass die Benutzeroberfläche von Correspondence Management oder Adaptive Forms-Assets nicht geöffnet ist, während die Migration ausgeführt wird.

Wenn Sie das Migrationsdienstprogramm zum ersten Mal ausführen, wird ein Protokoll unter dem folgenden Pfad und mit dem folgenden Namen erstellt: `\[aem-installation-directory]\cq-quickstart\logs\aem-forms-migration.log`. Dieses Protokoll enthält aktualisierte Correspondence Management- und Adaptive Forms-Migrationsinformationen, beispielsweise zum Verschieben von Assets.

>[!NOTE]
>
>Stellen Sie vor dem Ausführen des Migrationsdienstprogramms sicher, dass Sie eine Sicherungskopie Ihres crx-Repositorys erstellt haben.

1. Melden Sie sich in einer Browsersitzung bei der AEM-Autoreninstanz als Administrator an.

1. Öffnen Sie die folgende URL im Browser:

   https://[*hostname*]:[*port*]/[*context_path*]/libs/fd/foundation/gui/content/migration.html

   Der Browser zeigt vier Optionen an:

   * AEM Forms-Assets-Migration
   * Migration von benutzerdefinierten adaptiven Formularkomponenten
   * Migration von adaptiven Formularvorlagen
   * Migration von AEM Forms-Cloud-Konfigurationen

1. Führen Sie die folgenden Schritte aus, um die Migration durchführen:

   * Um **Assets** zu migrieren, tippen Sie auf „AEM Forms – Asset-Migration“ und auf dem nächsten Bildschirm auf **Migration beginnen**. Die folgenden Elemente werden migriert:

      * Adaptive Formulare
      * Dokumentfragmente
      * Designs
      * Briefe
      * Datenwörterbücher

   >[!NOTE]
   >
   >Während der Asset-Migration treten möglicherweise Warnungen ähnlich der folgenden auf: „Konflikt aufgetreten bei …“. Solche Benachrichtigungen bedeuten, dass Regeln für einige Komponenten in adaptiven Formularen nicht migriert werden konnten. Beispiel: Wenn bei einer Komponente ein Ereignis auftritt, das sowohl Regeln als auch Skripte umfasst und wenn die Regeln nach einem Skript angewendet werden, wird keine der Regeln für die Komponente migriert. Allerdings können Sie [diese Regeln migrieren, indem Sie den Regeleditor für das Authoring von adaptiven Formularen öffnen](#migrate-rules).

   * Um benutzerdefinierte Komponenten für adaptive Formulare zu migrieren, tippen Sie auf **Migration benutzerdefinierter Komponenten für adaptive Formulare** und auf der Seite „Migration von benutzerdefinierten Komponenten“ auf **Migration beginnen**. Die folgenden Elemente werden migriert:

      * Benutzerdefinierte Komponenten, die für adaptive Formulare geschrieben wurden
      * Komponentenüberlagerungen, falls vorhanden.
   * Um Vorlagen für adaptive Formulare zu migrieren, tippen Sie auf **Migration von Vorlagen für adaptive Formulare** und auf der Seite „Migration von benutzerdefinierten Komponenten“ auf **Migration beginnen**. Die folgenden Elemente werden migriert:

      * Adaptive Formularvorlagen, die unter `/apps` oder `/conf` mit dem AEM-Vorlageneditor erstellt wurden.
   * Migrieren Sie die AEM Forms Cloud-Konfigurations-Services, um das neue kontextbezogene Cloud-Service-Paradigma zu nutzen, das die Benutzeroberfläche mit Touch-Funktion (unter `/conf`) umfasst. Wenn Sie Services der Cloud-Konfiguration von AEM Forms migrieren, werden die Cloud-Services in `/etc` nach `/conf` verschoben. Wenn Sie keine Anpassungen von Cloud-Services haben, die von den veralteten Pfaden (`/etc`) abhängen, wird empfohlen, dass Sie das Migrationsdienstprogramm direkt nach dem Upgrade auf 6.5 ausführen und für alle weiteren Arbeiten die Cloud-Konfigurations-Benutzeroberfläche mit Touch-Funktion verwenden. Wenn Sie über Anpassungen für die bereits vorhandenen Cloud-Services verfügen, setzen Sie die Verwendung der klassischen Benutzeroberfläche bei der Aktualisierung fort, bis die Anpassungen für die migrierten Pfade (`/conf`) abgeschlossen sind, und führen Sie erst dann das Migrationsdienstprogramm aus.

   Um **AEM Forms-Cloud-Dienste** zu migrieren, die Folgendes umfassen, tippen Sie auf „AEM Forms-Cloud-Konfigurationsmigration“ (die Cloud-Konfigurationsmigration ist unabhängig vom AEMFD-Kompatibilitätspaket) und dann auf der Seite „Konfigurationsmigration“ auf **Migration starten**:

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

   Im Browserfenster wird während der Migration Folgendes ausgeführt: 

   * Wenn die Assets aktualisiert sind: Assets wurden erfolgreich aktualisiert.
   * Nachdem die Migration abgeschlossen ist: Migration für Elemente wurde abgeschlossen.

   Wenn ausgeführt, geht das Migrationsdienstprogramm wie folgt vor: 

   * **Fügt den Assets die Tags hinzu**: Fügt das Tag „Correspondence Management: Migrierte Assets“/„Adaptive Formulare: Migrierte Assets“ zu den migrierten Assets hinzu, damit Benutzende die migrierten Assets ermitteln können. Wenn Sie das Migrationsdienstprogramm ausführen, werden alle im System vorhandenen Assets mit „Migriert“ markiert. 
   * **Erstellt Tags**: Die Kategorien und Unterkategorien, die im Vorgängersystem vorhanden sind, werden als Tags erstellt, und dann werden diese Tags den entsprechenden Correspondence Management-Assets in AEM zugeordnet. So werden beispielsweise eine Kategorie (Schadensmeldungen) sowie eine Unterkategorie (Schadensmeldungen) einer Briefvorlage als Tags generiert.










1. Fahren Sie nach der Ausführung des Migrationsdienstprogramms mit den [Systemverwaltungsaufgaben](#housekeepingtasks) fort.

#### Migrieren von Regeln mithilfe des Regeleditors {#migrate-rules}

Diese Komponenten können migriert werden, indem sie im Regeleditor im Editor für adaptive Formulare geöffnet werden.

* Um Regeln und Skripte (für die Aktualisierung von 6.3 nicht erforderlich) in benutzerdefinierten Komponenten zu migrieren, tippen Sie auf „Migration von benutzerdefinierten Adaptive Forms-Komponenten“ und auf dem nächsten Bildschirm auf „Migration beginnen“. Die folgenden Elemente werden migriert:

   * Regeln und Skripten, erstellt mithilfe des Regel-Editors (6.1 FP1 und höher)

   * Skripte, erstellt mithilfe der Skript-Registerkarte in der Benutzeroberfläche von Version 6.1 oder niedriger

* Um Vorlagen (für die Aktualisierung von 6.3 und 6.4 nicht erforderlich) zu migrieren, tippen Sie auf „Migration von Adaptive Forms-Vorlagen“ und auf dem nächsten Bildschirm auf „Migration beginnen“. Die folgenden Elemente werden migriert:

   * Alte Vorlagen – Vorlagen für adaptive Formulare, erstellt unter /apps mithilfe von AEM 6.1 Forms oder niedriger. Dazu gehören die Skripten, die in den Vorlagenkomponenten definiert wurden.

   * Neue Vorlagen – Vorlagen für adaptive Formulare, erstellt mithilfe des Vorlagen-Editors unter /conf. Das umfasst die Migration von Regeln und Skripten, die mithilfe des Regel-Editors erstellt wurden.

### Systemverwaltungsaufgaben nach Ausführung des Migrationsdienstprogramms  {#housekeepingtasks}

Nachdem Sie das Migrationsdienstprogramm ausgeführt haben, führen Sie folgende Systemverwaltungsaufgaben durch: 

1. Stellen Sie sicher, dass die XFA-Version 3.3 oder eine spätere Version von Layouts und Fragment-Layouts verwendet wird. Wenn Sie Layouts und Fragment-Layouts einer älteren Version benutzen, könnte es Probleme beim Rendern des Briefs geben. Um ein älteres XFA auf die neueste Version zu aktualisieren, führen Sie folgende Schritte aus:

   1. [Herunterladen von XFA- als ZIP-Datei](../../forms/using/import-export-forms-templates.md#p-import-and-export-assets-in-correspondence-management-p) aus der Forms-Benutzeroberfläche.
   1. Extrahieren Sie die Datei.
   1. Öffnen Sie die XFA-Datei im neuesten Designer und speichern Sie sie. Die Version des XFA wird auf die neueste Version aktualisiert. 
   1. Hochladen des XFA in der forms-Benutzeroberfläche.

1. Veröffentlichen Sie alle Assets, die im vorherigen System vor der Migration veröffentlicht wurden. Das Migrationsdienstprogramm aktualisiert die Assets nur im Autorenmodus. Um die Assets in der Veröffentlichungsinstanz (s) zu aktualisieren, müssen Sie die Assets veröffentlichen. 

1. In AEM Forms 6.4 werden einige Rechte der Forms-Benutzergruppen geändert. Wenn Sie möchten, dass Ihre Benutzer XDPs und adaptive Formulare hochladen können, die Skripte enthalten oder den Code-Editor verwenden, müssen Sie sie der Gruppe der Forms-Power-User hinzufügen. Ebenso können Vorlagen-Autoren den Code-Editor im Regel-Editor nicht mehr verwenden. Damit Benutzer den Code-Editor verwenden können, fügen Sie sie der Gruppe „af-template-script-writers“ hinzu. Anweisungen zum Hinzufügen von Benutzern zu Gruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).
