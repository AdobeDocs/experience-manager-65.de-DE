---
title: Fehlerbehebung bei Installationsproblemen mit AEM
description: In diesem Artikel werden einige der Installationsprobleme behandelt, auf die Sie möglicherweise bei AEM stoßen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
exl-id: 55576729-be9c-412e-92ac-4be90650c6fa
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1227'
ht-degree: 90%

---

# Fehlerbehebung bei Installationsproblemen mit AEM{#troubleshooting}

Dieser Abschnitt enthält detaillierte Informationen zu den verfügbaren Protokollen, die Ihnen bei der Fehlerbehebung helfen, sowie Informationen zu einigen Problemen, auf die Sie bei AEM stoßen könnten.

## Fehlerbehebung bei der Autorenleistung {#troubleshoot-author-performance}

Das Analysieren der langsamen Leistung einer Authoring-Instanz kann sehr komplex werden. Als ersten Schritt muss ermittelt werden, auf welchem Niveau des technologischen Stacks die Leistung abnimmt.

Die folgende Entscheidungsstruktur bietet eine Anleitung zum Eingrenzen des Engpasses.

![chlimage_1-75](assets/chlimage_1-75.png)

## Grundlegende Optimierung {#basic-optimization}

![chlimage_1-76](assets/chlimage_1-76.png)

## Konfigurieren von Protokolldateien und Prüfprotokollen {#configuring-log-files-and-audit-logs}

AEM zeichnet detaillierte Protokolle auf, die Sie konfigurieren können, um Installationsprobleme möglicherweise zu beheben. Weitere Informationen finden Sie im Abschnitt [Arbeiten mit Prüfdatensätzen und Protokolldateien](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files).

## Verwenden der Option „verbose“ (ausführlich) {#using-the-verbose-option}

Wenn Sie AEM WCM starten, können Sie die Option „-v“ für „verbose“ zur Befehlszeile hinzufügen. Beispiel: java -jar cq-wcm-quickstart-&lt;Version>.jar -v.

Die Option „verbose“ zeigt einen Teil der Ausgabe des Schnellstartprotokolls in der Konsole an und kann somit für die Fehlerbehebung verwendet werden.

## Häufige Installationsprobleme {#common-installation-issues}

Im folgenden Abschnitt werden einige Installationsprobleme und deren Lösungen beschrieben.

### Ein Doppelklick auf die JAR-Datei für den Schnellstart hat keine Auswirkung oder öffnet die JAR-Datei mit einem anderen Programm (z. B. dem Archiv-Manager) {#double-clicking-the-quickstart-jar-does-not-have-any-effect-or-opens-the-jar-file-with-another-program-for-example-archive-manager}

Dieses Problem weist in der Regel darauf hin, dass ein Problem mit der Konfiguration der Desktop-Umgebung Ihres Betriebssystems im Hinblick auf das Öffnen von Dateien mit der Erweiterung „.jar“ vorliegt. Es kann auch darauf hinweisen, dass Java™ nicht installiert ist oder dass Sie eine nicht unterstützte Version von Java™ verwenden.

Da JAR-Dateien das allgegenwärtige ZIP-Format verwenden, können einige Archivierungsprogramme den Desktop automatisch so konfigurieren, dass JAR-Dateien als Archivdateien geöffnet werden.

Gehen Sie zur Fehlerbehebung wie folgt vor:

* Vergewissern Sie sich, dass Sie mindestens Java™ Version 1.6 installiert haben.
* Probieren Sie ein Kontextmenü (in der Regel Rechtsklick) für den AEM WCM-Schnellstart aus und wählen Sie „Öffnen mit…“
* Überprüfen Sie, ob Java™ oder Sun Java™ aufgelistet ist, und versuchen Sie, AEM WCM damit auszuführen. Wenn mehrere Java™-Versionen installiert sind, wählen Sie die unterstützte Version aus.

  Wenn dieser Schritt erfolgreich ist und Ihr Betriebssystem eine Option anbietet, das ausgewählte Programm immer zum Ausführen der .jar-Dateien zu verwenden, aktivieren Sie sie. Doppelklicken sollte von nun an funktionieren.

* Manchmal hilft eine Neuinstallation der unterstützten Java™-Version dabei, die korrekte Zuordnung wiederherzustellen.
* Sie können CRX immer mit der Befehlszeile oder Start-/Stopp-Skripten ausführen, wie zuvor in diesem Dokument beschrieben.

### Meine über CRX ausgeführte Anwendung erzeugt Fehler wegen unzureichendem Arbeitsspeicher {#my-application-running-on-crx-throws-out-of-memory-errors}

>[!NOTE]
>
>Siehe auch [Analysieren von Speicherproblemen](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17482.html?lang=de).


CRX selbst benötigt nur wenig Speicherplatz. Wenn die in CRX ausgeführte Anwendung größere Mengen Arbeitsspeicher benötigt oder Vorgänge anfordert, die viel Arbeitsspeicher belegen, etwa große Transaktionen, muss die JVM-Instanz, in der CRX ausgeführt wird, mit den entsprechenden Speichereinstellungen gestartet werden.

Verwenden Sie Java™-Befehlsoptionen, um die Speichereinstellungen der JVM zu definieren (z. B. „java -Xmx512m -jar crx*.jar“, um die Heap-Größe auf 512 MB festzulegen).

Geben Sie die Speichereinstellungsoption beim Starten von AEM WCM über die Befehlszeile an. Die Start-/Stopp-Skripte für AEM WCM oder benutzerdefinierten Skripte zur Verwaltung des Starts von AEM WCM können ebenfalls geändert werden, um die erforderlichen Speichereinstellungen zu definieren.

Wenn Sie Ihre Heap-Größe bereits auf 512 MB definiert haben, können Sie das Speicherproblem weiter analysieren, indem Sie einen Heap-Dump erstellen.

Verwenden Sie den folgenden Befehl, um automatisch ein Heap-Abbild zu erstellen, wenn nicht genügend Arbeitsspeicher verfügbar ist:

java -Xmx256m -XX:+HeapDumpOnOutOfMemoryError -jar &amp;ast;.jar

Diese Methode generiert eine Heap-Dump-Datei (**java_…hprof**) immer dann, wenn dem Prozess der Speicher ausgeht. Der Prozess kann nach der Erstellung des Heap-Dumps fortgesetzt werden.

Häufig sind drei Heap-Dump-Dateien erforderlich, die über einen bestimmten Zeitraum erfasst wurden, um das Problem zu analysieren:

* Vor dem Auftreten eines Fehlers
* Fehler 1
* Fehler 2
* *Idealerweise wäre es auch gut, Informationen nach der Auflösung des Ereignisses zu sammeln*

Diese können verglichen werden, um Änderungen zu sehen und zu sehen, wie Objekte Speicher verwenden.

>[!NOTE]
>
>Wenn Sie diese Informationen regelmäßig erfassen oder Erfahrung mit dem Lesen von Heap-Dumps haben, kann eine Heap-Dump-Datei ausreichen, um das Problem zu analysieren.

### Der AEM-Begrüßungsbildschirm wird nach einem Doppelklick auf den AEM-Schnellstart nicht im Browser angezeigt {#the-aem-welcome-screen-does-not-display-in-the-browser-after-double-clicking-aem-quickstart}

In bestimmten Situationen werden die AEM WCM-Begrüßungsbildschirme nicht automatisch angezeigt, obwohl das Repository selbst fehlerfrei läuft. Dieses Problem kann von der Einrichtung des Betriebssystems, der Browser-Konfiguration oder ähnlichen Faktoren abhängen.

Ein häufiges Symptom ist, dass im AEM WCM-Schnellstartfenster die Meldung „AEM WCM starting up, waiting for server startup...“ angezeigt wird. Sollte diese Meldung über einen relativ langen Zeitraum bestehen bleiben, geben Sie die AEM WCM-URL manuell in das Browser-Fenster ein und verwenden Sie den Standardport 4502 oder den Port, über den die Instanz läuft: http://localhost:4502/.

Es ist auch möglich, den Grund dafür, dass der Browser nicht startet, in Protokollen zu finden.

Manchmal wird die Meldung „AEM WCM wird über http://localhost:port/ ausgeführt.“ im AEM WCM-Schnellstartfenster angezeigt und der Browser startet nicht automatisch. Klicken Sie in diesem Fall auf die URL im AEM WCM-Schnellstartfenster (es handelt sich um einen Hyperlink) oder geben Sie die URL manuell im Browser ein.

Sollte das Problem durch keinen der Vorschläge gelöst werden können, überprüfen Sie die Protokolle, um herauszufinden, was passiert ist.

### Die Website wird nicht geladen oder schlägt mit Java 11™ gelegentlich fehl {#the-website-does-not-load-or-fails-intermittently-with-java11}

Es gibt ein bekanntes Problem bei der Ausführung von AEM 6.5 auf Java™ 11, bei dem die Website möglicherweise nicht geladen wird oder zeitweise fehlschlägt.

Tritt dieses Problem auf, führen Sie folgende Schritte aus:

1. Öffnen Sie die `sling.properties`-Datei unter dem Ordner `crx-quickstart/conf/`.
1. Suchen Sie die folgende Zeile:

   `org.osgi.framework.bootdelegation=sun.,com.sun.`

1. Ersetzen Sie sie durch die Folgende:

   `org.osgi.framework.bootdelegation=sun.,com.sun.,jdk.internal.reflect,jdk.internal.reflect.*`

1. Starten Sie die Instanz neu.

## Fehlerbehebung bei Installationen mit einem Anwendungs-Server {#troubleshooting-installations-with-an-application-server}

### Meldung „Seite nicht gefunden“ wird angezeigt, wenn eine Geometrixx Outdoors-Seite angefordert wird {#page-not-found-returned-when-requesting-a-geometrixx-outdoor-page}

**Gilt für WebLogic 10.3.5 und JBoss® 5.1**

Wenn eine englische Seite „geometrixx-outdoors/en“ einen 404-Fehler (Seite nicht gefunden) zurückgibt, sollten Sie sich noch einmal vergewissern, dass Sie die zusätzliche „sling“-Eigenschaft in der Datei „sling.properties“ festgelegt haben, die für diese speziellen Anwendungs-Server erforderlich ist.

Weitere Informationen finden Sie unter *Bereitstellen der AEM-Web-Anwendung*.

### Die Größe der Antwortkopfzeile kann größer als 4 KB sein. {#response-header-size-can-be-greater-than-kb}

502-Fehler können darauf hinweisen, dass der Webserver die Größe der AEM HTTP-Antwortkopfzeile nicht verarbeiten kann. AEM kann HTTP-Antwortkopfzeilen generieren, die Cookies mit einer Größe von mehr als 4 KB beinhalten. Achten Sie darauf, dass Ihr Servlet-Container so konfiguriert ist, dass die maximale Größe der Antwortkopfzeile größer als 4 KB sein darf.

Bei Tomcat 7.0 beispielsweise steuert das Attribut „maxHttpHeaderSize“ des [HTTP Connectors](https://tomcat.apache.org/tomcat-7.0-doc/config/http.html) Größenbegrenzungen für Kopfzeilen.

## Deinstallation von Adobe Experience Manager {#uninstalling-adobe-experience-manager}

Da AEM nur in ein einziges Verzeichnis installiert wird, ist kein Deinstallationsprogramm erforderlich. Für eine Deinstallation kann es ausreichen, das gesamte Verzeichnis zu löschen, wobei die Art der Deinstallation von AEM davon abhängt, was Sie bezwecken möchten und welche Art persistenten Speicher Sie verwenden.

Wenn persistenter Speicher in das Installationsverzeichnis eingebettet ist, z. B. in der standardmäßigen TarPM-Installation, werden beim Löschen von Ordnern auch Daten entfernt.

>[!NOTE]
>
>Adobe empfiehlt, das Repository zu sichern, bevor Sie AEM löschen. Wenn Sie das gesamte Installationsverzeichnis „&lt;cq-installation-directory>“ löschen, wird dabei auch das Repository gelöscht. Sichern Sie die Repository-Daten vor dem Löschen, indem Sie den Ordner „&lt;cq-installation-directory>/crx-quickstart/repository“ an einen anderen Speicherort verschieben oder kopieren, bevor Sie die anderen Ordner löschen.

Wenn Ihre AEM-Installation externen Speicher verwendet, z. B. einen Datenbank-Server, werden beim Entfernen des Ordners zwar nicht automatisch die Daten entfernt, aber die Speicherkonfiguration, wodurch die Wiederherstellung der JCR-Inhalte schwierig wird.

### JSP-Dateien werden unter JBoss® nicht kompiliert {#jsp-files-are-not-compiled-on-jboss}

Wenn Sie JSP-Dateien auf JBoss® installieren oder auf Experience Manager aktualisieren und die entsprechenden Servlets nicht kompiliert sind, stellen Sie sicher, dass der JBoss®-JSP-Compiler korrekt konfiguriert ist. Weitere Informationen finden Sie im 
Artikel [JSP-Kompilierungsprobleme in JBoss®](https://helpx.adobe.com/de/experience-manager/kb/jsps-dont-compile-jboss.html).
