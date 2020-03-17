---
title: Bekannte Probleme
description: Versionshinweise zu bekannten Problemen mit Adobe Experience Manager 6.5
uuid: 8fbdb167-833a-4179-aad1-0a26a4e5b3a7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: d11fc727-f23a-4cde-9fa6-97e2c81b4ad0
docset: aem65
translation-type: tm+mt
source-git-commit: 86dbd52d44a78401aa50cce299850469c51b691c

---


# Bekannte Probleme {#known-issues}

Nachfolgend sind bekannte Probleme in Version 6.5 von Adobe Experience Manager aufgeführt, die im April 2019 veröffentlicht wurde.

Um weitere Informationen zu bekannten Problemen zu erhalten, wenden Sie sich an den [Support](https://helpx.adobe.com/support/experience-manager.html).

## Plattform {#platform}

* Es wird ein Problem gemeldet, bei dem CRX-Quickstart und sein Inhalt gelöscht werden.

   Stellen Sie bei jeder dieser Aktionen sicher, dass die Eigenschaft &quot;*htmllibmanager.fileSystemOutputCacheLocation*&quot;nie eine leere Zeichenfolge ist:

   1. Aufruf von &quot;*/libs/granite/ui/content/dumplibs.rebuild.html?invalidate=true*&quot;.
   2. Aktualisieren auf AEM 6.5.
   3. Ausführung der &quot;Migration von verzögertem Inhalt&quot;auf AEM 6.5.
   Es steht ein Artikel der [Wissensdatenbank](https://helpx.adobe.com/experience-manager/kb/avoid-crx-quickstart-deletion-in-aem-6-5.html) mit weiteren Details und der Problemumgehung zur Verfügung.

* Wenn Sie JDK 11 mit der AEM 6.5-Instanz verwenden, werden einige der Seiten nach der Bereitstellung einiger Pakete möglicherweise als leer angezeigt. Die folgende Fehlermeldung wird in der Protokolldatei angezeigt:

   ```
   *ERROR* [OsgiInstallerImpl] org.apache.sling.scripting.sightly bundle org.apache.sling.scripting.sightly:1.1.2.1_4_0 (558)[org.apache.sling.scripting.sightly.impl.engine.extension.use.JavaUseProvider(3345)] : Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl)
   java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl
   ```

So beheben Sie diesen Fehler:

1. Halten Sie die AEM-Instanz an. Gehen Sie zur `<aem_server_path_on_server>crx-quickstart\conf` Datei und öffnen Sie sie `sling.properties` . Adobe empfiehlt eine Sicherung dieser Datei.

2. Suchen nach `org.osgi.framework.bootdelegation=`. Hinzufügen `jdk.internal.reflect,jdk.internal.reflect.*` Eigenschaften, um das Ergebnis anzuzeigen:

   ```
   org.osgi.framework.bootdelegation=sun.*,com.sun.*,jdk.internal.reflect,jdk.internal.reflect.*
   ```

3. Speichern Sie die Datei und starten Sie die AEM-Instanz neu.

## Assets {#assets}

* **Suchen:** Die Suche führt nicht zu Rückgaben, wenn die Suchzeichenfolge Leerzeichen am Anfang enthält ([OAK-4786](https://issues.apache.org/jira/browse/OAK-4786))
* **Ordner-Metadatenschema**: Nach Hinzufügen einer Auswahlschaltfläche entsprechen das ID-Feld und das Wertfeld nicht den Erwartungen und die Löschfunktion kann nicht verwendet werden (CQ-4261144)
* Beim Umbenennen eines Assets ist es nicht möglich, ein Leerzeichen im Asset-Namen zu verwenden (CQ-4266403)

## Formulare {#forms}

* Wenn AEM Forms unter einem Linux-Betriebssystem installiert ist, funktioniert die digitale Signatur nicht beim Modul für die Hardwaresicherheit (CQ-4266721)
* (Nur AEM Forms auf WebSphere) Die Option **Forms-Workflow**> **Aufgabensuche** gibt kein Ergebnis zurück, wenn Sie nach einem **Administrator** anhand des **Anwendernamens** suchen (CQ-4266457)

* AEM Forms kann keine .tif- und .tiff-Dateien mit JPEG-Komprimierung in PDF-Dokumente konvertieren (CQ-4265972)
* Die Optionen **AEM Forms-Asset-Scanner** und **Letter in interaktive Kommunikation – Migration** funktionieren nicht auf der Seite **AEM Forms-Migration** (CQ-4266572)

* (Nur JBoss 7) Wenn Sie ein Upgrade von einer früheren Version auf AEM 6.5 Forms durchführen und in der vorherigen Version Prozesse (.lca) vorhanden waren, die eine Kopie des standardmäßigen Sende- oder Standard-Renderprozesses erstellt und verwendet haben, können HTML5-Formulare, die solche Prozesse (.lca) verwenden, die erforderlichen Aktionen nicht ausführen. (CQ-4243928)
* Wenn in einem adaptiven Formular ein Formulardatenmodell-Service vom Regel-Editor aufgerufen wird, um die Werte der Bildauswahlkomponente dynamisch zu aktualisieren, werden die Werte der Bildauswahlkomponente nicht aktualisiert (CQ-4254754)
* AEM Forms Designer installer requires the 32-bit version of [Visual C++ redistributable runtime package 2012](https://support.microsoft.com/en-in/help/2977003/the-latest-supported-visual-c-downloads) and [Visual C++ redistributable runtime packages 2013](https://support.microsoft.com/en-in/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package). Stellen Sie sicher, dass die oben genannten Redistributable Runtime Packages vor Installationsbeginn installiert sind (CQ-4265668)

* Wenn ein adaptives Formular so konfiguriert ist, dass die Werte einer Komponente dynamisch aktualisiert werden, und auf die Veröffentlichungsinstanz, die das Formular hostet, über den Dispatcher zugegriffen wird, kann die Funktion zum dynamischen Aktualisieren von Feldwerten nicht mehr verwendet werden. Um das Problem zu lösen, öffnen Sie CRXDE in der Veröffentlichungsinstanz, navigieren Sie zu /libs/fd/af/runtime/clientlibs/guideChartReducer und erstellen Sie die unten aufgeführte Eigenschaft.

   * Name: allowProxy
   * Type: Boolean
   * Value: True
   * Protected: False
   * Mandatory: False
   * Multiple: False
   * Auto Created: False

Durch diese Eigenschaft können Client-Bibliotheken unter dem Laufzeitordner auf Proxys zugreifen (CQ-4268679)

