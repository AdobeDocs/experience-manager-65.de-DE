---
title: Migration der Assets und Dokumente von AEM Forms
seo-title: Migration der Assets und Dokumente von AEM Forms
description: Mithilfe des Migrationsdienstprogramms können Sie Assets und Dokumente von AEM Forms bis Version 6.3 in AEM 6.4 Forms migrieren.
seo-description: Mithilfe des Migrationsdienstprogramms können Sie Assets und Dokumente von AEM Forms bis Version 6.3 in AEM 6.4 Forms migrieren.
uuid: a3fdf940-7fc2-441c-91c8-ad66ba47e5f2
content-type: reference
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-strategy: max-2018
discoiquuid: 39dfef85-d047-4b6d-a0f5-92bd77df103b
docset: aem65
translation-type: tm+mt
source-git-commit: 3226edb575de3d9f8bff53f5ca81e2957f37c544

---


# Migration der Assets und Dokumente von AEM Forms{#migrate-aem-forms-assets-and-documents}

The Migration utility converts the [Adaptive Forms assets](../../forms/using/introduction-forms-authoring.md), [cloud configrurations](/help/sites-developing/extending-cloud-config.md), and [Correspondence Management assets](/help/forms/using/cm-overview.md) from the format used in the earlier versions to the format used in AEM 6.5 Forms. Wenn Sie das Migrationsdienstprogramm ausführen, werden folgende Elemente migriert:

* Benutzerdefiniert Komponenten für adaptive Formulare
* Adaptive Formulare und Correspondence Management-Vorlagen
* Cloud-Konfigurationen
* Assets für Correspondence Management und adaptive Formulare

>[!NOTE]
>
>Bei einem fehlgeschlagenen Upgrade können Sie für den Fall von Correspondence Management-Assets die Migration jedes Mal ausführen, wenn Sie die Assets importieren. Für die Correspondence Management-Migration muss das Forms-Kompatibilitätspaket installiert sein.

## Verfahren zur Migration {#approach-to-migration}

You can [upgrade](../../forms/using/upgrade.md) to the latest version of AEM Forms 6.5 from AEM Forms 6.4, 6.3, or 6.2 or perform a fresh installation. Je nachdem, ob Sie die vorherige Installation aktualisiert oder eine Neuinstallation durchgeführt haben, müssen Sie einen der folgenden Schritte ausführen:

**Im Falle eines direkten Upgrades**

Wenn Sie eine ersetzende Aktualisierung durchgeführt haben, verfügt die aktualisierte Instanz bereits über die Assets und Dokumente. Bevor Sie jedoch die Assets und Dokumente verwenden können, müssen Sie das [AEMFD-Kompatibilitätspaket ](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) installieren (enthält das Correspondence-Management-Kompatibilitätspaket).

Dann müssen Sie die Assets und Dokumente aktualisieren, indem Sie das [Migrationsprogramm ausführen](#runningmigrationutility).

**Bei nicht ersetzender Installation**

If it is an out of place (fresh) installation, before you can use the assets and documents, you will need to install [AEMFD Compatibility package](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) (includes the Correspondence Management Compatibility package).

Then you need to import your asset package (zip or cmp) on the new setup and then update the assets and documents by [running the Migration utility](#runningmigrationutility). Adobe empfiehlt, neue Assets erst nach dem Ausführen des Migrationsdienstprogramms zu erstellen.

Aufgrund der [Abwärtskompatibilität-bezogenen](/help/sites-deploying/backward-compatibility.md) Änderungen werden Speicherorte von einigen Ordnern im CRX-Repository geändert. Exportieren und importieren Sie Abhängigkeiten (benutzerdefinierte Bibliotheken und Assets) vom vorherigen Setup in eine neue Umgebung manuell.

## Read before you proceed with the migration {#prerequisites}

Für Correspondence Management-Assets:

* For the assets that are imported from the previous platform, a property gets added: **fd:version=1.0**.
* Seit AEM 6.1 Forms sind Kommentare nicht standardmäßig verfügbar. Die Kommentare, die zuvor hinzugefügt wurden, stehen in den Assets zur Verfügung, sind jedoch nicht automatisch auf der Oberfläche sichtbar. Sie müssen die Eigenschaft „extendedProperties“ in der AEM Forms-Benutzeroberfläche anpassen, um die Kommentare sichtbar zu machen.
* In einigen früheren Versionen, beispielsweise LiveCycle ES4, wurde Text mithilfe von Flex RichTextEditor bearbeitet. Seit AEM 6.1 Forms wird HTML-Editor verwendet. Dadurch können sich die Darstellung und das Erscheinungsbild der Schriftarten, Schriftgrößen und Schriftartränder von früheren Versionen in der Autorenbenutzeroberfläche unterscheiden. Die ausgegebenen Briefe sehen jedoch gleich aus.
* Listen in den Textmodulen wurden verbessert und werden jetzt anders dargestellt. Es gibt möglicherweise visuelle Unterschiede. Wir empfehlen, die Buchstaben an den Stellen darzustellen und anzuzeigen, wo Sie Listen in Textmodulen verwenden. 
* Da Bildinhaltmodule in DAM-Assets konvertiert werden und Layouts und Fragmente während der Migration zu Formularen hinzugefügt werden, wird die Eigenschaft „Aktualisiert von“ bei diesen Moduländerungen in „admin“ geändert.
* Der Versionsverlauf der Assets wird nicht migriert und steht nach der Migration nicht zur Verfügung. Der nachfolgende Versionsverlauf wird nach der Migration beibehalten.
* Der Status „Veröffentlichungsbereit“ wird seit AEM 6.1 Forms nicht mehr unterstützt, sodass alle Assets mit dem Status „Veröffentlichungsbereit“ den Status „Geändert“ erhalten.
* Da die Benutzeroberfläche auf AEM Forms 6.3 aktualisiert wird, sind die Schritte für die Anpassung ebenfalls unterschiedlich. Sie müssen die Anpassung erneut vornehmen, wenn Sie von einer Version vor 6.3 migrieren.
* Layout-Fragmente wurden von /content/apps/cm/layouts/fragmentlayouts/1001 in /content/apps/cm/modules/fragmentlayouts verschoben. Datenwörterbuchverweis in Assets zeigt den Pfad des Datenwörterbuchs anstelle des Namens an.
* Alle Tabulatorabstände, die für die Ausrichtung von Textmodulen verwendet werden, müssen angepasst werden. Weitere Informationen finden Sie unter [Correspondence Management – verwenden von Tabulatorabständen zum Anordnen von Text](https://helpx.adobe.com/aem-forms/kb/cm-tab-spacing-limitations.html).
* Asset Composer-Konfigurationen ändern sich in Correspondence Management-Konfigurationen.
* Assets werden in Ordner mit einem Namen wie „Existing Text“ oder „Existing List“ verschoben.

## Verwenden des Migrationsdienstprogramms{#using-the-migration-utility} 

### Ausführen des Migrationsdienstprogramms{#runningmigrationutility} 

Führen Sie die Migration aus, bevor Sie Änderungen an den Assets vornehmen oder Assets erstellen. Wir empfehlen, das Dienstprogramm erst dann auszuführen, wenn Änderungen an den Assets vorgenommen wurden oder Assets erstellt wurden. Stellen Sie sicher, dass die Benutzeroberfläche von Correspondence Management oder adaptiven Formularen Assets nicht geöffnet ist, während der Migrationsprozess ausgeführt wird.

Wenn Sie das Migrationsdienstprogramm zum ersten Mal ausführen, wird ein Protokoll unter dem folgenden Pfad und mit dem folgenden Namen erstellt: \[aem-installation-directory]\cq-quickstart\logs\aem-forms-migration.log. Dieses Protokoll enthält aktualisierte Correspondence Management- und Adaptive Forms-Migrationsinformationen, beispielsweise zum Verschieben von Assets.

>[!NOTE]
>
>Stellen Sie vor dem Ausführen des Migrationsdienstprogramms sicher, dass Sie eine Sicherungskopie Ihres crx-Repositorys erstellt haben.

1. Melden Sie sich in einer Browsersitzung bei der AEM-Autoreninstanz als Administrator an.

1. Öffnen Sie die folgende URL im Browser:

   https://[*hostname*]:[*port*]/[*context_path*]/libs/fd/foundation/gui/content/migration.html

   Der Browser zeigt vier Optionen an:

   * AEM Forms-Asset-Migration
   * Migration von benutzerdefinierten Adaptive Forms-Komponenten
   * Migration von Adaptive Forms-Vorlagen
   * AEM Forms Cloud-Konfigurationensmigration

1. Führen Sie die folgenden Schritte aus, um die Migration durchführen:

   * Um **Assets** zu migrieren, tippen Sie auf „AEM Forms – Asset-Migration“ und auf dem nächsten Bildschirm auf **Migration beginnen**. Die folgenden Elemente werden migriert:

      * Adaptive Formulare
      * Dokumentfragmente
      * Designs
      * Briefe
      * Datenwörterbücher
   >[!NOTE]
   >
   >Während der Asset-Migration treten möglicherweise Warnungen ähnlich der folgenden auf: „Konflikt aufgetreten bei …“. Solche Meldungen weisen darauf hin, dass Regeln für einige Komponenten in adaptiven Formularen nicht migriert werden konnten. Beispiel: Wenn bei einer Komponente ein Ereignis auftritt, das sowohl Regeln als auch Skripten umfasst und wenn die Regeln nach einem Skript angewendet werden, wird keine der Regeln für die Komponente migriert. Allerdings können diese Regeln migriert werden, indem der Regeleditor für das Authoring von adaptiven Formularen geöffnet wird.
   >
   >
   >Diese Komponenten können migriert werden, indem sie im Regel-Editor im Editor für adaptive Formulare geöffnet werden.
   >
   >
   >
   >    * Um Regeln und Skripten (die bei einer Aktualisierung von 6.3 nicht erforderlich sind) in benutzerdefinierten Komponenten zu migrieren, tippen Sie auf Migration zu benutzerdefinierten adaptiven Formularen und dann im nächsten Bildschirm auf Migration starten. Die folgenden Elemente werden migriert:    >
      >
      >
      >        

      * Regeln und Skripten, erstellt mithilfe des Regel-Editors (6.1 FP1 und höher)
      >        * Skripte, erstellt mithilfe der Skript-Registerkarte in der Benutzeroberfläche von Version 6.1 oder niedriger
   >
   >
   >    * Um Vorlagen zu migrieren (bei einer Aktualisierung von 6.3 und 6.4 nicht erforderlich), tippen Sie auf Migration zu adaptiven Formularen und dann im nächsten Bildschirm auf Migration starten. Die folgenden Elemente werden migriert:
      >
      >
      >
      >        


      * Alte Vorlagen - die Vorlagen für adaptive Formulare, die unter /apps mit AEM 6.1 Forms oder früher erstellt wurden. Dazu gehören die Skripten, die in den Vorlagenkomponenten definiert wurden.
      >        * Neue Vorlagen - Vorlagen für adaptive Formulare, die mit dem Vorlageneditor unter /conf erstellt wurden. Das umfasst die Migration von Regeln und Skripten, die mithilfe des Regel-Editors erstellt wurden.


   * To migrate adaptive form custom components, tap **Adaptive Forms Custom Components Migration** and in the Custom Components Migration page, tap **Start Migration**. Die folgenden Elemente werden migriert:

      * Benutzerdefinierte Komponenten, die für adaptive Formulare geschrieben wurden
      * Komponentenüberlagerungen, falls vorhanden.
   * To migrate adaptive form templates, tap **Adaptive Forms Template Migration** and in the Custom Components Migration page, tap **Start Migration**. Die folgenden Elemente werden migriert:

      * Die adaptiven Formularvorlagen, die unter /Apps oder /Conf mit dem AEM-Vorlageneditor erstellt wurden.
   * Migrieren Sie die AEM Forms Cloud-Konfigurationsdienste, um das neue kontextbezogene Cloud-Dienst-Paradigma zu nutzen, das die Benutzeroberfläche mit Touch-Funktion (unter/conf) umfasst. Wenn Sie AEM Forms Cloud-Konfigurationsdienste migrieren, werden die Cloud-Dienste in /etc nach /conf verschoben. Wenn Sie keine Anpassungen an Cloud-Services vornehmen, die von den alten Pfaden (/etc) abhängen, sollten Sie das Migrationsdienstprogramm unmittelbar nach der Aktualisierung auf 6.5 ausführen und die Touch-Cloud-Konfigurationsoberfläche für weitere Arbeiten verwenden. Wenn Sie über Anpassungen für die bereits vorhandene Cloud-Dienste verfügen, setzen Sie die klassische Benutzeroberfläche bei der Aktualisierung fort, bis die Anpassungen für die migrierten Pfaden (/conf) abgeschlossen sind, und führen Sie das Migrationshilfsprogramm aus.
   To migrate **AEM Forms cloud services**, which include the following, tap AEM Forms Cloud Configuration Migration (cloud config migration is independent of AEMFD Compatibility package), tap AEM Forms Cloud Configurations Migration and then on the Configuration Migration page, tap **Start Migration**:

   * Cloud-Dienste für Formulardatenmodell

      * Quellpfad: /etc/cloudservices/fdm
      * Zielpfad: /conf/global/settings/cloudconfigs/fdm
   * Recaptcha

      * Quellpfad: /etc/cloudservices/recaptcha
      * Zielpfad: /conf/global/settings/cloudconfigs/recaptcha
   * Adobe Sign

      * Quellpfad: /etc/cloudservices/echosign
      * Zielpfad: /conf/global/settings/cloudconfigs/echosign
   * Cloud-Dienste für Typekit

      * Quellpfad: /etc/cloudservices/typekit
      * Zielpfad: /conf/global/settings/cloudconfigs/typekit
   Im Browserfenster wird während der Migration Folgendes ausgeführt: 

   * Wenn die Assets aktualisiert sind: Assets wurden erfolgreich aktualisiert.
   * Nachdem die Migration abgeschlossen ist: Migration für Elemente wurde abgeschlossen.
   Wenn ausgeführt, geht das Migrationsdienstprogramm wie folgt vor: 

   * **Fügt den Elementen die Tags hinzu**: Fügt das Tag „Correspondence Management: Migrierte Assets“ / „Adaptive Forms : Migrierte Assets“. den migrierten Assets hinzu, damit Benutzer migrierte Inhalte ermitteln können. Wenn Sie das Migrationsdienstprogramm ausführen, werden alle vorhandenen Assets im System als migriert markiert.
   * **Erstellt Tags**: Die Kategorien und Unterkategorien, die im Vorgängersystem vorhanden sind, werden als Tags erstellt, und dann werden diese Tags den entsprechenden Correspondence Management-Assets in AEM zugeordnet. So werden beispielsweise eine Kategorie (Schadensmeldungen) sowie eine Unterkategorie (Schadensmeldungen) einer Briefvorlage als Tags generiert.

















1. Nach der Ausführung des Migrationsdienstprogramms fahren Sie mit den [Systemverwaltungsaufgaben](#housekeepingtasks) fort.

### Systemverwaltungsaufgaben nach Ausführung des Migrationsdienstprogramms  {#housekeepingtasks}

Nachdem Sie das Migrationsdienstprogramm ausgeführt haben, führen Sie folgende Systemverwaltungsaufgaben durch:[](../../forms/using/import-export-forms-templates.md) 

1. Stellen Sie sicher, dass die XFA-Version von Layouts und Fragmentlayouts 3.3 oder höher ist. Wenn Sie Layouts und Fragmentlayouts einer älteren Version verwenden, kann es zu Problemen beim Rendern des Briefs kommen. Um ein älteres XFA auf die neueste Version zu aktualisieren, führen Sie folgende Schritte aus:

   1. [Herunterladen von XFA- als ZIP-Datei](../../forms/using/import-export-forms-templates.md#p-import-and-export-assets-in-correspondence-management-p) aus der Forms-Benutzeroberfläche.
   1. Extrahieren Sie die Datei. 
   1. Öffnen Sie die XFA-Datei im neuesten Designer und speichern Sie sie. Die Version des XFA wird auf die neueste Version aktualisiert. 
   1. Hochladen des XFA in der forms-Benutzeroberfläche.

1. Veröffentlichen Sie alle Assets, die im vorherigen System vor der Migration veröffentlicht wurden. Das Migrationsdienstprogramm aktualisiert die Assets nur im Autorenmodus . Um die Assets in der Veröffentlichungsinstanz (s) zu aktualisieren, müssen Sie die Assets veröffentlichen. 
1. In AEM Forms 6.4 und 6.5 werden einige Rechte der Benutzergruppen für Formulare geändert. Wenn Sie möchten, dass Ihre Benutzer XDPs und adaptive Formulare hochladen können, die Skripte enthalten oder den Code-Editor verwenden, müssen Sie sie der Gruppe der Forms-Power-User hinzufügen. Ebenso können Vorlagen-Autoren den Code-Editor im Regel-Editor nicht mehr verwenden. Damit Benutzer den Code-Editor verwenden können, fügen Sie sie der Gruppe „af-template-script-writers“ hinzu. For instructions on adding users to groups, see [Managing Users and User Groups](/help/communities/users.md).

