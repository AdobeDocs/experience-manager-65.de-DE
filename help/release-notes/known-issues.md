---
title: Bekannte Probleme
description: Spezifische Versionshinweise zu bekannten Problemen mit Adobe Experience Manager 6.5
exl-id: 736037cf-af8c-4ce2-969e-c100a939a038
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 46%

---

# Bekannte Probleme {#known-issues}

Nachfolgend sind bekannte Probleme in Version 6.5 von Adobe Experience Manager aufgeführt, die im April 2019 veröffentlicht wurde.

Um weitere Informationen zu bekannten Problemen zu erhalten, wenden Sie sich an den [Support](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de).

## Plattform {#platform}

* Es wird ein Problem gemeldet, bei dem CRX-Quickstart und sein Inhalt gelöscht werden.

   Stellen Sie bei jeder dieser Aktionen sicher, dass die Eigenschaft `htmllibmanager.fileSystemOutputCacheLocation` keine leere Zeichenfolge ist:

   1. Bei einem Aufruf von `/libs/granite/ui/content/dumplibs.rebuild.html?invalidate=true`.
   2. Aktualisieren auf AEM 6.5.
   3. &quot;Lazy Content Migration&quot;auf AEM 6.5 ausführen.

   Ein Artikel [Knowledge Base](https://helpx.adobe.com/experience-manager/kb/avoid-crx-quickstart-deletion-in-aem-6-5.html) mit weiteren Details und der Problemumgehung ist verfügbar.

* Wenn Sie JDK 11 mit AEM 6.5-Instanz verwenden, werden einige der Seiten nach der Bereitstellung einiger Pakete möglicherweise als leer angezeigt. Die folgende Fehlermeldung wird in der Protokolldatei angezeigt:

   ```java
   *ERROR* [OsgiInstallerImpl] org.apache.sling.scripting.sightly bundle org.apache.sling.scripting.sightly:1.1.2.1_4_0 (558)[org.apache.sling.scripting.sightly.impl.engine.extension.use.JavaUseProvider(3345)] : Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl)
   java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl
   ```

So beheben Sie diesen Fehler:

1. Halten Sie die AEM-Instanz an. Gehen Sie zu `<aem_server_path_on_server>crx-quickstart\conf` und öffnen Sie die Datei `sling.properties` . Adobe empfiehlt, eine Sicherungskopie dieser Datei zu erstellen.

1. Suchen Sie nach `org.osgi.framework.bootdelegation=`. Fügen Sie die Eigenschaften `jdk.internal.reflect,jdk.internal.reflect.*` hinzu, um das Ergebnis anzuzeigen.

```java
org.osgi.framework.bootdelegation=sun.*,com.sun.*,jdk.internal.reflect,jdk.internal.reflect.*
```

1. Speichern Sie die Datei und starten Sie die AEM-Instanz neu.

## Assets {#assets}

* **Suche:** Die Suche führt nicht zu Rückgaben, wenn die Suchzeichenfolge führende Leerzeichen enthält ([OAK-4786](https://issues.apache.org/jira/browse/OAK-4786))
* **Ordner-Metadatenschema**: Nach Hinzufügen einer Auswahlschaltfläche entsprechen das ID-Feld und das Wertfeld nicht den Erwartungen und die Löschfunktion kann nicht verwendet werden (CQ-4261144)
* Beim Umbenennen eines Assets ist es nicht möglich, ein Leerzeichen im Asset-Namen zu verwenden (CQ-4266403)

## Formulare {#forms}

* Wenn AEM Forms auf dem Linux-Betriebssystem installiert ist, funktioniert Digital Signature mit Hardware Security Module nicht. (CQ-4266721)
* (Nur AEM Forms auf WebSphere) Die Option **Forms-Workflow**> **Aufgabensuche** gibt kein Ergebnis zurück, wenn Sie nach einem **Administrator** anhand des **Anwendernamens** suchen (CQ-4266457)

* AEM Forms kann TIF- und TIFF-Dateien mit JPEG-Komprimierung nicht in PDF-Dokumente konvertieren. (CQ-4265972)
* Die Optionen **AEM Forms-Asset-Scanner** und **Letter in interaktive Kommunikation – Migration** funktionieren nicht auf der Seite **AEM Forms-Migration** (CQ-4266572)

* (Nur JBoss 7) Wenn Sie von einer früheren Version auf AEM 6.5 Forms aktualisieren und die vorherige Version über Prozesse (.lca) verfügte, die eine Kopie des standardmäßigen Sende- oder Renderprozesses erstellt und verwendet haben, kann HTML5 Forms mit solchen Prozessen (.lca) die erforderlichen Aktionen nicht durchführen. (CQ-4243928)
* Wenn in einem adaptiven Formular ein Formulardatenmodell-Service vom Regel-Editor aufgerufen wird, um die Werte der Bildauswahlkomponente dynamisch zu aktualisieren, werden die Werte der Bildauswahlkomponente nicht aktualisiert (CQ-4254754)
* Für das AEM Forms Designer-Installationsprogramm ist die 32-Bit-Version von [Visual C++ Redistributable Runtime Package 2012](https://support.microsoft.com/de-de/help/2977003/the-latest-supported-visual-c-downloads) und [Visual C++ Redistributable Runtime Packages 2013](https://support.microsoft.com/de-de/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package) erforderlich. Stellen Sie sicher, dass die oben genannten Redistributable Runtime Packages vor Installationsbeginn installiert sind (CQ-4265668)

* PDF Generator unterstützt keine Authentifizierung mit Smart Card.  Wenn ein Administrator die Gruppenrichtlinie `Interactive Logon: Require Smart card` auf einem Windows-Server aktiviert, werden alle vorhandenen PDF Generator-Benutzer invalidiert.

* Wenn ein adaptives Formular so konfiguriert ist, dass die Werte einer Komponente dynamisch aktualisiert werden, und auf die Veröffentlichungsinstanz, die das Formular hostet, über den Dispatcher zugegriffen wird, kann die Funktion zum dynamischen Aktualisieren von Feldwerten nicht mehr verwendet werden. Um das Problem zu beheben, öffnen Sie CRXDE in der Veröffentlichungsinstanz, navigieren Sie zu `/libs/fd/af/runtime/clientlibs/guideChartReducer` und erstellen Sie die Eigenschaft, die unten aufgeführt ist.

   * Name: allowProxy
   * Typ: Boolesch
   * Value: True
   * Protected: False
   * Mandatory: False
   * Multiple: False
   * Automatisch erstellt: False

   Durch diese Eigenschaft können Client-Bibliotheken unter dem Laufzeitordner auf Proxys zugreifen (CQ-4268679)

* Wenn AEM Forms gestartet wird, wird die `SAX Security Manager could not be setup`-Warnung angezeigt.
* Wenn Sie ein mit AEM Forms Document Security geschütztes PDF auf einem Apple iOS oder iPadOS öffnen, auf dem Adobe Acrobat Reader Version 20.10.00 ausgeführt wird.
