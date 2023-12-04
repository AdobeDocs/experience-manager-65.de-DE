---
title: Migration der Assets und Dokumente von AEM Forms
description: Mit dem Migrationsdienstprogramm können Sie Adobe Experience Manager (AEM)-Assets und -Dokumente aus AEM 6.3 Forms oder früheren Versionen in AEM 6.4 Forms migrieren.
content-type: reference
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-strategy: max-2018
docset: aem65
role: Admin
exl-id: 0f9aab7d-8e41-449a-804b-7e1bfa90befd
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '1736'
ht-degree: 36%

---

# Migration der Assets und Dokumente von AEM Forms{#migrate-aem-forms-assets-and-documents}

Das Migrationsdienstprogramm konvertiert die [Adaptive Forms-Assets](../../forms/using/introduction-forms-authoring.md), [Cloud-Konfigurationen](/help/sites-developing/extending-cloud-config.md), und [Correspondence Management-Assets](/help/forms/using/cm-overview.md) von dem Format, das in früheren Versionen verwendet wurde, bis zum Format, das in Adobe Experience Manager (AEM) 6.5 Forms verwendet wird. Wenn Sie das Migrationsdienstprogramm ausführen, werden die folgenden Elemente migriert:

* Benutzerdefinierte Komponenten für adaptive Formulare
* Adaptive Formulare und Correspondence Management-Vorlagen
* Cloud-Konfigurationen
* Assets für Correspondence Management und adaptive Formulare

>[!NOTE]
>
>Bei einer nicht ersetzenden Aktualisierung für Correspondence Management-Assets können Sie die Migration jedes Mal ausführen, wenn Sie die Assets importieren. Für die Correspondence Management-Migration muss das Forms-Kompatibilitätspaket installiert sein.

## Migrationsansatz {#approach-to-migration}

Sie können [Upgrade](../../forms/using/upgrade.md) auf die neueste Version von AEM Forms 6.5 von AEM Forms 6.4, 6.3 oder 6.2 oder eine Neuinstallation. Je nachdem, ob Sie Ihre vorherige Installation aktualisiert oder eine Neuinstallation durchgeführt haben, müssen Sie einen der folgenden Schritte ausführen:

**Wenn eine ersetzende Aktualisierung erfolgt**

Wenn Sie eine ersetzende Aktualisierung durchgeführt haben, verfügt die aktualisierte Instanz bereits über die Assets und Dokumente. Bevor Sie die Assets und Dokumente verwenden können, müssen Sie jedoch die [AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) (enthält das Correspondence Management-Kompatibilitätspaket)

Anschließend müssen Sie die Assets und Dokumente durch [Ausführen des Migrationsdienstprogramms](#runningmigrationutility).

**Bei einer nicht ersetzenden Installation**

Wenn es sich um eine nicht ersetzende (neue) Installation handelt, müssen Sie die [AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) (enthält das Correspondence Management-Kompatibilitätspaket).

Anschließend müssen Sie Ihr Asset-Paket (zip oder cmp) in das neue Setup importieren und dann die Assets und Dokumente aktualisieren, indem Sie [Ausführen des Migrationsdienstprogramms](#runningmigrationutility). Adobe empfiehlt die Erstellung von Assets in der neuen Einrichtung erst nach Ausführung des Migrationsdienstprogramms.

Aufgrund von [Abwärtskompatibilität](/help/sites-deploying/backward-compatibility.md) geändert wurde, werden die Speicherorte einiger Ordner im CRX-Repository geändert. Exportieren und importieren Sie Abhängigkeiten (benutzerdefinierte Bibliotheken und Assets) manuell von der vorherigen Einrichtung in eine neue Umgebung.

## Bevor Sie mit der Migration fortfahren {#prerequisites}

Für Correspondence Management-Assets:

* Für die Assets, die von der vorherigen Plattform importiert werden, wird eine Eigenschaft hinzugefügt: **fd:version=1.0**.
* Seit AEM 6.1 Forms sind Kommentare nicht standardmäßig verfügbar. Die zuvor hinzugefügten Kommentare stehen in den Assets zur Verfügung, sind jedoch nicht automatisch auf der Oberfläche sichtbar. Passen Sie die Eigenschaft &quot;extendedProperties&quot;in der Benutzeroberfläche von AEM Forms an, damit die Kommentare sichtbar werden.
* In einigen früheren Versionen wie LiveCycle ES4 wurde Text mit dem Flex RichTextEditor bearbeitet, aber seit AEM 6.1 Forms wird der HTML-Editor verwendet. Aufgrund dieser Darstellung und des Erscheinungsbilds der Schriftarten, Schriftgrößen und Schriftränder kann sich von den vorherigen Versionen in der Author-Benutzeroberfläche unterscheiden. Die Buchstaben sehen jedoch beim Rendern gleich aus.
* Listen in Textmodulen wurden verbessert und werden jetzt anders dargestellt. Es kann visuelle Unterschiede geben. Adobe empfiehlt, dass Sie die Buchstaben rendern und sehen, wo Sie Listen in Textmodulen verwenden.
* Da Bildinhaltsmodule in DAM-Assets konvertiert werden und Layouts und Fragmente während der Migration zu Formularen hinzugefügt werden, wird die Eigenschaft &quot;Aktualisiert von&quot;für diese Module in &quot;admin&quot;geändert.
* Der Versionsverlauf der Assets wird nicht migriert und steht nach der Migration nicht zur Verfügung. Der nachfolgende Versionsverlauf nach der Migration wird beibehalten.
* Der Status „Veröffentlichungsbereit“ wird seit AEM 6.1 Forms nicht mehr unterstützt, sodass alle Assets mit dem Status „Veröffentlichungsbereit“ den Status „Geändert“ erhalten.
* Da die Benutzeroberfläche auf AEM Forms 6.3 aktualisiert wird, sind die Schritte für die Anpassung ebenfalls unterschiedlich. Wiederholen Sie die Anpassung, wenn Sie von einer Version vor 6.3 migrieren.
* Layout-Fragmente verschieben sich von `/content/apps/cm/layouts/fragmentlayouts/1001` nach `/content/apps/cm/modules/fragmentlayouts`. Die Datenwörterbuchreferenz in Assets zeigt den Pfad des Datenwörterbuchs anstelle des Namens an.
* Alle Tabulatorzeichen, die für die Ausrichtung in Textmodulen verwendet werden, müssen angepasst werden. Weitere Informationen finden Sie unter [Correspondence Management - Anordnen von Text mit Tabulatorabständen](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html).
* Die Asset Composer-Konfigurationen ändern sich zu Correspondence Management-Konfigurationen.
* Assets werden in Ordner mit einem Namen wie „Existing Text“ oder „Existing List“ verschoben.

## Verwenden des Migrationsdienstprogramms {#using-the-migration-utility}

### Ausführen des Migrationsdienstprogramms {#runningmigrationutility}

Führen Sie das Migrationsdienstprogramm aus, bevor Sie die Assets ändern oder Assets erstellen. Adobe empfiehlt, das Dienstprogramm nicht auszuführen, nachdem Sie Änderungen vorgenommen oder Assets erstellt haben. Stellen Sie sicher, dass die Benutzeroberfläche von Correspondence Management oder Adaptive Forms-Assets nicht geöffnet ist, während die Migration ausgeführt wird.

Wenn Sie das Migrationsdienstprogramm zum ersten Mal ausführen, wird ein Protokoll unter dem folgenden Pfad und mit dem folgenden Namen erstellt: `\[aem-installation-directory]\cq-quickstart\logs\aem-forms-migration.log`. Dieses Protokoll wird weiterhin mit Correspondence Management- und Adaptive Forms-Migrationsinformationen aktualisiert, z. B. zum Verschieben von Assets.

>[!NOTE]
>
>Bevor Sie das Migrationsdienstprogramm ausführen, stellen Sie sicher, dass Sie eine Sicherung Ihres CRX-Repositorys durchgeführt haben.

1. Melden Sie sich in einer Browsersitzung bei Ihrer AEM-Autoreninstanz als Administrator an.

1. Öffnen Sie die folgende URL im Browser:

   https://[*hostname*]:[*port*]/[*context_path*]/libs/fd/foundation/gui/content/migration.html

   Der Browser zeigt vier Optionen an:

   * AEM Forms-Assets-Migration
   * Migration von benutzerdefinierten adaptiven Formularkomponenten
   * Migration von adaptiven Formularvorlagen
   * Migration von AEM Forms-Cloud-Konfigurationen

1. Führen Sie die folgenden Schritte aus, um die Migration durchzuführen:

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

      * Benutzerdefinierte Komponenten, die für Adaptive Forms geschrieben wurden
      * Komponentenüberlagerungen, falls vorhanden.

   * Um adaptive Formularvorlagen zu migrieren, wählen Sie **Adaptive Forms-Vorlagenmigration** und wählen Sie auf der Seite &quot;Migration benutzerdefinierter Komponenten&quot;die Option **Migration starten**. Die folgenden Elemente werden migriert:

      * Adaptive Formularvorlagen, die unter `/apps` oder `/conf` mit dem AEM-Vorlageneditor erstellt wurden.

   * Migrieren Sie AEM Forms Cloud Configuration Services, um das neue kontextabhängige Cloud Service-Paradigma zu verwenden, das die Touch-optimierte Benutzeroberfläche enthält (unter `/conf`). Wenn Sie Services der Cloud-Konfiguration von AEM Forms migrieren, werden die Cloud-Services in `/etc` nach `/conf` verschoben. Wenn Sie über keine Cloud Services-Anpassungen verfügen, die von den veralteten Pfaden (`/etc`), empfiehlt Adobe, das Migrationsdienstprogramm nach der Aktualisierung auf 6.5 auszuführen. Verwenden Sie die Touch-optimierte Cloud-Konfiguration für alle weiteren Arbeiten. Wenn Sie über Anpassungen für die bereits vorhandenen Cloud-Services verfügen, setzen Sie die Verwendung der klassischen Benutzeroberfläche bei der Aktualisierung fort, bis die Anpassungen für die migrierten Pfade (`/conf`) abgeschlossen sind, und führen Sie erst dann das Migrationsdienstprogramm aus.

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

   Im Browserfenster wird während der Migration Folgendes ausgeführt: 

   * Wenn die Assets aktualisiert werden: Assets wurden erfolgreich aktualisiert.
   * Wenn die Migration abgeschlossen ist: Die Migration für Assets wurde abgeschlossen.

   Wenn das Migrationsdienstprogramm ausgeführt wird, führt es Folgendes aus:

   * **Fügt den Assets die Tags hinzu**: Fügt das Tag „Correspondence Management: Migrierte Assets“/„Adaptive Formulare: Migrierte Assets“ zu den migrierten Assets hinzu, damit Benutzende die migrierten Assets ermitteln können. Wenn Sie das Migrationsdienstprogramm ausführen, werden alle im System vorhandenen Assets mit „Migriert“ markiert. 
   * **Erstellt Tags**: Die Kategorien und Unterkategorien, die im Vorgängersystem vorhanden sind, werden als Tags erstellt, und dann werden diese Tags den entsprechenden Correspondence Management-Assets in AEM zugeordnet. Beispielsweise werden eine Kategorie (Schadensmeldungen) und eine Unterkategorie (Schadensmeldungen) einer Briefvorlage als Tags generiert.

1. Fahren Sie nach der Ausführung des Migrationsdienstprogramms mit den [Systemverwaltungsaufgaben](#housekeepingtasks) fort.

#### Migrieren von Regeln mithilfe des Regeleditors {#migrate-rules}

Diese Komponenten können migriert werden, indem sie im Regeleditor im adaptiven Forms-Editor geöffnet werden.

* Um Regeln und Skripte (die bei einer Aktualisierung von 6.3 nicht erforderlich sind) in benutzerdefinierten Komponenten zu migrieren, wählen Sie Adaptive Forms Custom Components Migration (Adaptive-Komponentenmigration) und klicken Sie im nächsten Bildschirm auf &quot;Migration starten&quot;. Die folgenden Elemente werden migriert:

   * Regeln und Skripten, erstellt mithilfe des Regel-Editors (6.1 FP1 und höher)

   * Skripte, erstellt mithilfe der Skript-Registerkarte in der Benutzeroberfläche von Version 6.1 oder niedriger

* Um Vorlagen zu migrieren (bei einer Aktualisierung von 6.3 und 6.4 nicht erforderlich), wählen Sie Adaptive Forms-Vorlagenmigration und wählen Sie im nächsten Bildschirm die Option Migration starten aus. Die folgenden Elemente werden migriert:

   * Alte Vorlagen – Vorlagen für adaptive Formulare, erstellt unter /apps mithilfe von AEM 6.1 Forms oder niedriger. Dazu gehören die Skripten, die in den Vorlagenkomponenten definiert wurden.

   * Neue Vorlagen - Vorlagen für adaptive Formulare, die mithilfe des Vorlageneditors unter `/conf`. Das umfasst die Migration von Regeln und Skripten, die mithilfe des Regel-Editors erstellt wurden.

### Systemverwaltungsaufgaben nach Ausführung des Migrationsdienstprogramms {#housekeepingtasks}

Nachdem Sie das Migrationsdienstprogramm ausgeführt haben, führen Sie die folgenden Systemverwaltungsaufgaben durch:

1. Stellen Sie sicher, dass die XFA-Version der Layouts und Fragmentlayouts 3.3 oder höher ist. Wenn Sie Layouts und Fragment-Layouts einer älteren Version benutzen, könnte es Probleme beim Rendern des Briefs geben. Führen Sie die folgenden Schritte aus, um eine Version eines älteren XFA auf die neueste Version zu aktualisieren:

   1. [Herunterladen von XFA- als ZIP-Datei](../../forms/using/import-export-forms-templates.md#p-import-and-export-assets-in-correspondence-management-p) aus der Forms-Benutzeroberfläche.
   1. Extrahieren Sie die Datei.
   1. Öffnen Sie die XFA-Datei im neuesten Designer und speichern Sie sie. Die Version des XFA wird auf die neueste Version aktualisiert.
   1. Laden Sie die XFA in die Forms-Benutzeroberfläche hoch.

1. Veröffentlichen Sie alle Assets, die vor der Migration im vorherigen System veröffentlicht wurden. Das Migrationsdienstprogramm aktualisiert die Assets nur auf der Autoreninstanz. Um die Assets auf den Veröffentlichungsinstanzen zu aktualisieren, müssen Sie die Assets veröffentlichen.

1. In AEM Forms 6.4 werden einige Rechte der Forms-Benutzergruppen geändert. Wenn Sie möchten, dass Ihre Benutzer XDPs und adaptive Forms mit Skripten hochladen oder einen Code-Editor verwenden können, müssen Sie diese zur Gruppe der Formular-Hauptbenutzer hinzufügen. Ebenso können Vorlagenautoren den Code-Editor im Regeleditor nicht mehr verwenden. Damit Benutzer einen Code-Editor verwenden können, fügen Sie ihn zur Gruppe af-template-script-writers hinzu. Anweisungen zum Hinzufügen von Benutzern zu Gruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).
