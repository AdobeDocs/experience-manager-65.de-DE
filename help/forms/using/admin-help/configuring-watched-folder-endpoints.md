---
title: Konfigurieren von Endpunkten für überwachte Ordner
description: Erfahren Sie, wie Sie Endpunkte für überwachte Ordner konfigurieren. Wenn ein Dokument in einem überwachten Ordner abgelegt wird, wird ein konfigurierter Dienstvorgang aufgerufen und die Datei bearbeitet.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
exl-id: ec169a01-a113-47eb-8803-bd783ea2c943
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '7192'
ht-degree: 41%

---

# Konfigurieren von Endpunkten für überwachte Ordner {#configuring-watched-folder-endpoints}

Ein Administrator kann einen Netzwerkordner konfigurieren, der als *Überwachter Ordner*, sodass beim Platzieren einer Datei (z. B. einer PDF-Datei) im überwachten Ordner ein konfigurierter Dienstvorgang aufgerufen und die Datei bearbeitet wird. Nachdem der Dienst den vorgesehenen Vorgang ausgeführt hat, wird die geänderte Datei in einem angegebenen Ausgabeordner gespeichert.

## Konfigurieren des Watched Folder-Dienstes {#configuring-the-watched-folder-service}

Bevor Sie einen Endpunkt des Typs &quot;überwachter Ordner&quot;konfigurieren, konfigurieren Sie den Dienst für überwachte Ordner . Die Konfigurationsparameter des Watched Folder-Dienstes haben zwei Zwecke:

* So konfigurieren Sie Attribute, die für alle Endpunkte überwachter Ordner gelten
* So stellen Sie Standardwerte für alle Endpunkte des überwachten Ordners bereit

Nach dem Konfigurieren des Watched Folder-Dienstes fügen Sie einen Endpunkt des Typs &quot;Überwachter Ordner&quot;für den Zieldienst hinzu. Beim Hinzufügen des Endpunkts legen Sie Werte wie den Dienstnamen und den Vorgangsnamen fest, die aufgerufen werden, wenn Dateien oder Ordner im Eingabeordner des konfigurierten Watched Folder-Dienstes abgelegt werden. Weitere Informationen zum Konfigurieren des Watched Folder-Dienstes finden Sie unter [Einstellungen des Watched Folder-Dienstes](/help/forms/using/admin-help/configure-service-settings.md#watched-folder-service-settings).

## Überwachten Ordner erstellen {#creating-a-watched-folder}

Sie können einen überwachten Ordner auf zwei Arten erstellen:

* Geben Sie beim Konfigurieren der Einstellungen für einen Endpunkt des Typs &quot;überwachter Ordner&quot;den vollständigen Pfad zum übergeordneten Ordner in das Feld &quot;Pfad&quot;ein und hängen Sie den Namen des zu erstellenden überwachten Ordners an, wie in diesem Beispiel gezeigt:
  `  C:\MyPDFs\MyWatchedFolder`Da der Ordner „MyWatchedFolder“ noch nicht vorhanden ist, versucht AEM Forms, ihn an diesem Speicherort zu erstellen.

* Erstellen Sie einen Ordner im Dateisystem, bevor Sie einen Endpunkt des Typs &quot;überwachter Ordner&quot;konfigurieren, und geben Sie dann den vollständigen Pfad in das Feld &quot;Pfad&quot;ein.

In einer Clusterumgebung muss der Ordner, der als überwachter Ordner verwendet wird, zugänglich, schreibbar und im Dateisystem oder Netzwerk freigegeben sein. In diesem Szenario muss jede Anwendungsserverinstanz des Clusters Zugriff auf denselben freigegebenen Ordner haben.

Wenn der Anwendungsserver unter Windows als Dienst ausgeführt wird, muss er auf eine der folgenden Arten mit dem entsprechenden Zugriff auf den freigegebenen Ordner gestartet werden:

* Konfigurieren Sie den **Parameter** „Log On As“ des Anwendungsserverdiensts so, dass er als spezifischer Benutzer mit geeignetem Zugriff auf den freigegebenen überwachten Ordner gestartet wird.
* Konfigurieren Sie die Option „Start as Local System“ des Anwendungsserverdiensts so, dass die Interaktion des Diensts mit dem Desktop zulässig ist. Für diese Option muss der freigegebene überwachte Ordner für alle zugänglich und schreibbar sein.

## Überwachte Ordner verketten {#chaining-together-watched-folders}

Überwachte Ordner können miteinander verkettet werden, sodass ein Ergebnisdokument eines überwachten Ordners das Eingabedokument des nächsten überwachten Ordners ist. Jeder überwachte Ordner kann einen anderen Dienst aufrufen. Durch die Konfiguration überwachter Ordner auf diese Weise können mehrere Dienste aufgerufen werden. Beispielsweise könnte ein überwachter Ordner PDF-Dateien in Adobe PostScript® und ein anderer PostScript-Dateien in das PDF/A-Format konvertieren. Legen Sie dazu einfach die *result* Ordner des überwachten Ordners, der vom ersten Endpunkt definiert wird und auf den *input* Ordner des überwachten Ordners, der durch Ihren zweiten Endpunkt definiert wird.

Die Ausgabe der ersten Konvertierung wird an „\Pfad\result“ übergeben. Als Eingabe der zweiten Konvertierung dient „\Pfad\result“, und die Ausgabe der zweiten Konvertierung wird in „\Pfad\result\result“ oder den Ordner übertragen, den Sie im Feld „Ergebnisordner“ für die zweite Konvertierung angegeben haben.

## Interaktion der Benutzer mit überwachten Ordnern {#how-users-interact-with-watched-folders}

Bei Endpunkten des Typs &quot;überwachter Ordner&quot;können Benutzer durch Kopieren oder Ziehen von Eingabedateien oder Ordnern von ihren Desktops in einen überwachten Ordner aufrufen. Die Dateien werden in der Reihenfolge ihres Eingangs verarbeitet.

Wenn bei Endpunkten des Typs &quot;überwachter Ordner&quot;für den Auftrag nur eine Eingabedatei erforderlich ist, kann der Benutzer diese Datei in den Stammordner des überwachten Ordners kopieren.

Wenn der Auftrag mehr als eine Eingabedatei enthält, muss der Benutzer einen Ordner außerhalb der Hierarchie des überwachten Ordners erstellen, der alle erforderlichen Dateien enthält. Dieser neue Ordner sollte die Eingabedateien enthalten (und optional eine DDX-Datei, falls vom Prozess benötigt). Nachdem der Auftragsordner erstellt wurde, kopiert er ihn in den Eingabeordner des überwachten Ordners.

>[!NOTE]
>
>Stellen Sie sicher, dass der Anwendungsserver Löschzugriff auf die Dateien im überwachten Ordner hat. Wenn AEM Formulare die Dateien nicht aus dem Eingabeordner löschen können, nachdem sie durchsucht wurden, wird der zugehörige Prozess auf unbestimmte Zeit aufgerufen.

## Ausgabe des überwachten Ordners {#watched-folder-output}

Wenn die Eingabe ein Ordner ist und die Ausgabe aus mehreren Dateien besteht, erstellt AEM Formulare einen Ausgabeordner mit demselben Namen wie der Eingabeordner und kopiert die Ausgabedateien in diesen Ordner. Wenn die Ausgabe aus einer Dokumentzuordnung besteht, die ein Schlüssel-Wert-Paar enthält, z. B. die Ausgabe aus einem Output-Prozess, wird der Schlüssel als Name der Ausgabedatei verwendet.

Die Ausgabedateinamen, die aus einem Endpunktprozess resultieren, dürfen keine anderen Zeichen als Buchstaben, Zahlen und einen Punkt (.) enthalten vor der Dateierweiterung. AEM Formulare konvertiert andere Zeichen in Hexadezimalwerte.

Client-Anwendungen rufen die Ergebnisdokumente aus dem Ergebnisordner des überwachten Ordners ab. Prozessfehler werden im Fehlerordner des überwachten Ordners protokolliert.

## Funktionsweise von überwachten Ordnern {#how-watched-folder-works}

Das Watched Folder-Modul enthält die folgenden Dienste:

* Watched Folder-Dienst
* provider.file_scan_service
* provider.file_write_results_service

Zusätzlich zu den oben aufgeführten Diensten ist der Watched Folder-Dienst auch von anderen Diensten abhängig, einschließlich des Scheduler-Dienstes für die Planung der Aufträge und des Job Manager-Dienstes, um den asynchronen Aufruf von Zieldiensten zu unterstützen.

### Verarbeitung einer Aufrufanforderung durch den überwachten Ordner {#how-watched-folder-processes-an-invocation-request}

Der Watched Folder-Dienst verarbeitet die Erstellung, Aktualisierung und Löschung von Endpunkten. Nachdem der Administrator die Endpunkte erstellt hat, werden sie vom Scheduler-Dienst basierend auf dem angegebenen Wiederholungsintervall oder Cron-Ausdruck ausgelöst.

Dieses Diagramm zeigt, wie eine Aufrufanforderung von einem überwachten Ordner verarbeitet wird.

![en_watchedfolder](assets/en_watchedfolder.png)

Der Prozess zum Aufrufen eines Dienstes mithilfe überwachter Ordner sieht wie folgt aus:

1. Eine Client-Anwendung legt Dateien oder Ordner im Eingabeordner des überwachten Ordners ab.
1. Wenn das Überprüfungsintervall für Aufträge auftritt, ruft der Scheduler-Dienst den &quot;provider.file_scan_service&quot;-Dienst auf, um die Dateien oder Ordner im Eingabeordner zu verarbeiten.
1. Der &quot;provider.file_scan_service&quot;-Dienst führt die folgenden Aufgaben aus:


   * Scannt den Eingabeordner nach Dateien oder Ordnern, die dem Muster für einzuschließende Dateien entsprechen, und schließt Dateien oder Ordner für das angegebene Muster für auszuschließende Dateien aus. Die ältesten Dateien oder Ordner werden zuerst abgerufen. Dateien und Ordner, die älter als die Wartezeit sind, werden ebenfalls abgerufen. Bei einer Überprüfung basiert die Anzahl der verarbeiteten Dateien oder Ordner auf der Batch-Größe. Weitere Informationen zu Dateimustern finden Sie unter [Über Dateimuster](configuring-watched-folder-endpoints.md#about-file-patterns). Informationen zum Festlegen der Batch-Größe finden Sie unter [Einstellungen des Watched Folder-Dienstes](/help/forms/using/admin-help/configure-service-settings.md#watched-folder-service-settings).
   * Ruft die Dateien oder Ordner zur Verarbeitung ab. Wenn die Dateien oder Ordner nicht vollständig heruntergeladen wurden, werden sie bei der nächsten Prüfung aufgenommen. Um sicherzustellen, dass Ordner vollständig heruntergeladen werden, sollten Administratoren einen Ordner mit einem Namen erstellen, indem sie das Muster für auszuschließende Dateien verwenden. Nachdem der Ordner alle Dateien enthält, muss er in das Muster umbenannt werden, das im Muster für einzuschließende Dateien angegeben ist. Dieser Schritt stellt sicher, dass der Ordner über alle zum Aufrufen des Dienstes erforderlichen Dateien verfügt. Weitere Informationen zum Sicherstellen, dass Ordner vollständig heruntergeladen werden, finden Sie unter [Tipps und Tricks für überwachte Ordner](configuring-watched-folder-endpoints.md#tips-and-tricks-for-watched-folders).
   * Verschiebt die Dateien oder Ordner in den Bereitstellungsordner, nachdem sie zur Verarbeitung ausgewählt wurden.
   * Konvertiert die Dateien oder Ordner im Bereitstellungsordner basierend auf den Zuordnungen der Endpunkteingabeparameter in die entsprechende Eingabe. Beispiele für Zuordnungen von Eingabeparametern finden Sie unter [Tipps und Tricks für überwachte Ordner](configuring-watched-folder-endpoints.md#tips-and-tricks-for-watched-folders).


1. Der für den Endpunkt konfigurierte Zieldienst wird entweder synchron oder asynchron aufgerufen. Der Zieldienst wird mit dem für den Endpunkt konfigurierten Benutzernamen und Kennwort aufgerufen.

   * Synchrone Aufrufe rufen den Zieldienst direkt und verarbeiten die Antwort sofort.
   * Bei asynchronem Aufruf wird der Zieldienst über den Job Manager-Dienst aufgerufen, der die Anforderung in eine Warteschlange stellt. Der Job Manager-Dienst ruft wiederum den &quot;provider.file_write_results_service&quot;-Dienst auf, um die Ergebnisse zu verarbeiten.

1. Der &quot;provider.file_write_results_service&quot;-Dienst verarbeitet die Antwort oder den Fehler des Zieldienstaufrufs. Bei erfolgreicher Ausführung wird die Ausgabe basierend auf der Endpunktkonfiguration im Ergebnisordner gespeichert. Der &quot;provider.file_write_results_service&quot;-Dienst behält auch die Quelle bei, wenn der Endpunkt so konfiguriert ist, dass die Ergebnisse nach erfolgreichem Abschluss beibehalten werden.

   Wenn der Aufruf des Zieldienstes zu einem Fehler führt, protokolliert der &quot;provider.file_write_results_service&quot;-Dienst den Grund für den Fehler in einer &quot;failure.log&quot;-Datei und legt diese Datei im Fehlerordner ab. Der Fehlerordner wird anhand der für den Endpunkt angegebenen Konfigurationsparameter erstellt. Wenn der Administrator die Option Bei Fehler beibehalten für die Endpunktkonfiguration festlegt, kopiert der &quot;provider.file_write_results_service&quot;-Dienst auch die Quelldateien in den Fehlerordner. Informationen zum Wiederherstellen von Dateien aus dem Fehlerordner finden Sie unter [Fehlerquellen und Wiederherstellung](configuring-watched-folder-endpoints.md#failure-points-and-recovery).


## Einstellungen für Endpunkte des Typs „Überwachter Ordner“ {#watched-folder-endpoint-settings}

Verwenden Sie die folgenden Einstellungen, um einen Endpunkt des Typs &quot;überwachter Ordner&quot;zu konfigurieren.

**Name** (obligatorisch): Gibt den Endpunkt an. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird. Wenn Sie eine URL als Namen des Endpunkts eingeben, stellen Sie sicher, dass sie den in RFC1738 angegebenen Syntaxregeln entspricht.

**Beschreibung**: Eine Beschreibung des Endpunkts. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird.

**Pfad** (obligatorisch): Gibt den Speicherort des überwachten Ordners an. In einer Clusterumgebung muss diese Einstellung auf einen freigegebenen Netzwerkordner zeigen, auf den alle Computer im Cluster zugreifen können.

**Asynchron**: Bestimmt, ob ein asynchroner oder ein synchroner Aufruftyp verwendet wird. Der Standardwert ist „asynchron“. Asynchron wird für langlebige Prozesse empfohlen, während synchron für transiente oder kurzlebige Prozesse empfohlen wird.

**Cron-Ausdruck**: Geben Sie einen Cron-Ausdruck ein, wenn der überwachte Ordner mithilfe eines Cron-Ausdrucks geplant werden muss. Wenn diese Einstellung konfiguriert ist, wird „Repeat Interval“ ignoriert.

**Wiederholungsintervall**: Das Intervall in Sekunden, in dem der überwachte Ordner auf Eingaben überprüft wird. Sofern die Einstellung &quot;Einschränken&quot;nicht aktiviert ist, sollte &quot;Wiederholungsintervall&quot;länger sein als die Verarbeitungsdauer für einen durchschnittlichen Auftrag. Andernfalls kann das System überlastet sein. Der Standardwert ist 5. Weitere Informationen finden Sie in der Beschreibung für die Stapelgröße .

**Wiederholungsanzahl**: Anzahl, wie oft der überwachte Ordner oder das Verzeichnis überprüft wird. Der Wert &quot;-1&quot;bedeutet uneingeschränktes Überprüfen. Der Standardwert ist -1.

**Drosselung**: Wenn diese Option ausgewählt ist, wird die Anzahl der Aufträge für überwachte Ordner begrenzt, die AEM Forms zu einem bestimmten Zeitpunkt verarbeitet. Die maximale Anzahl von Aufträgen wird durch den Wert von „Stapelgröße“ bestimmt. (Siehe Informationen zu Einschränkungen.)

**Benutzername** (obligatorisch): Der Benutzername, der beim Aufrufen eines Ziel-Services aus dem überwachten Ordner verwendet wird. Der Standardwert ist „SuperAdmin“.

**Domänenname:** (Erforderlich) Die Domäne des Benutzers. Der Standardwert ist „DefaultDom“.

**Stapelgröße**: Die Anzahl der Dateien oder Ordner, die pro Überprüfung aufgenommen werden. Mit dieser Einstellung können Sie eine Überlastung des Systems verhindern, da das gleichzeitige Überprüfen zu vieler Dateien zu einem Absturz führen kann. Der Standardwert ist 2.

Die Einstellungen „Wiederholungsintervall“ und „Stapelgröße“ bestimmen, wie viele Dateien bei jeder Überprüfung vom Watched Folder-Dienst ausgewählt werden. Der überwachte Ordner verwendet einen Quartz-Threadpool für die Überprüfung des Eingabeordners. Der Threadpool wird mit anderen Diensten gemeinsam verwendet. Wenn das Überprüfungsintervall gering ist, wird der Eingabeordner häufig von den Threads überprüft. Wenn Dateien häufig im überwachten Ordner abgelegt werden, sollten Sie das Überprüfungsintervall klein halten. Wenn Dateien nicht häufig abgelegt werden, sollten Sie ein größeres Überprüfungsintervall verwenden, damit die anderen Dienste die Threads verwenden können.

Falls eine große Anzahl von Dateien abgelegt wird, wählen Sie eine große Stapelgröße.  Wenn der vom Endpunkt des überwachten Ordners aufgerufene Dienst beispielsweise 700 Dateien pro Minute verarbeiten kann und die Benutzenden Dateien mit der gleichen Geschwindigkeit in den Eingabeordner ablegen, kann die Leistung des überwachten Ordners durch die Einstellung der Stapelgröße auf 350 und des Wiederholungsintervalls auf 30 Sekunden verbessert werden, ohne dass die Kosten für eine zu häufige Überprüfung des überwachten Ordners anfallen.

Wenn Dateien im überwachten Ordner abgelegt werden, werden die Dateien in der Eingabe aufgelistet, was die Leistung beeinträchtigen kann, wenn jede Sekunde eine Überprüfung stattfindet. Ein Verlängern des Überprüfungsintervalls kann die Leistung verbessern. Wenn das Volumen der abzulegenden Dateien gering ist, passen Sie die Batch-Größe und das Wiederholungsintervall entsprechend an. Wenn beispielsweise jede Sekunde 10 Dateien abgelegt werden, versuchen Sie, das Wiederholungsintervall auf 1 Sekunde und die Batch-Größe auf 10 festzulegen.

**Wartezeit**: Die Zeit in Millisekunden, die gewartet werden soll, bevor ein Ordner oder eine Datei nach der Erstellung überprüft wird. Wenn die Wartezeit beispielsweise 3.600.000 Millisekunden (eine Stunde) beträgt und die Datei vor einer Minute erstellt wurde, wird diese Datei erst nach Ablauf von mindestens 59 Minuten abgerufen. Der Standardwert ist 0.

Diese Einstellung ist nützlich, um sicherzustellen, dass eine Datei oder ein Ordner vollständig in den Eingabeordner kopiert wurde. Wenn Sie beispielsweise eine große Datei verarbeiten müssen und das Herunterladen der Datei 10 Minuten dauert, legen Sie die Wartezeit auf 10 x 60 x 1000 Millisekunden fest. Dies verhindert, dass der überwachte Ordner die Datei überprüft, wenn sie nicht 10 Minuten alt ist.

**Dateimuster ausschließen**: Eine durch Semikolon **;** getrennte Liste von Mustern, die ein überwachter Ordner verwendet, um zu bestimmen, welche Dateien und Ordner überprüft und aufgenommen werden sollen. Dateien oder Ordner mit diesem Muster werden nicht zur Verarbeitung überprüft.

Diese Einstellung ist hilfreich, wenn die Eingabe aus einem Ordner mit mehreren Dateien besteht. Der Inhalt des Ordners kann in einen Ordner mit einem Namen kopiert werden, der vom überwachten Ordner aufgenommen wird. Dadurch wird verhindert, dass der überwachte Ordner einen Ordner zur Verarbeitung aufnimmt, bevor der Ordner vollständig in den Eingabeordner kopiert wird.

Sie können Dateimuster verwenden, um Folgendes auszuschließen:

* Dateien mit bestimmten Dateinamenerweiterungen, z. B. *.dat, *.xml, *.pdf.
* Dateien mit bestimmten Namen, z. B. data.„*“ würde Dateien und Ordner mit den Namen *data1*, *data2* usw. ausschließen.
* Dateien mit zusammengesetzten Ausdrücken in Name und Erweiterung, wie in den folgenden Beispielen:

   * Data[0-9][0-9][0-9].[dD][aA]&#39;port&#39;
   * &amp;ast;.[dD][Aa]&#39;port&#39;
   * &amp;ast;.[Xx][Mm][Ll]

Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](configuring-watched-folder-endpoints.md#about-file-patterns).

**Dateimuster einbeziehen** (obligatorisch): Eine durch Semikolon **;** getrennte Liste von Mustern, die ein überwachter Ordner verwendet, um zu bestimmen, welche Ordner und Dateien überprüft und aufgenommen werden sollen. Wenn als Muster für einzuschließende Dateien beispielsweise „input*“ eingegeben wird, werden alle Dateien und Ordner aufgenommen, die „input*“ im Namen enthalten. Hierzu gehören auch Dateien und Ordner namens „input1“, „input2“ usw.

Der Standardwert ist „*“, wodurch alle Dateien und Ordner verwendet werden.

Sie können Dateimuster verwenden, um Folgendes einzuschließen:

* Dateien mit bestimmten Dateinamenerweiterungen, z. B. *.dat, *.xml, *.pdf.
* Dateien mit bestimmten Namen, z. B. data.„*“ würde Dateien und Ordner mit den Namen *data1*, *data2* usw. einschließen.
* Dateien mit zusammengesetzten Ausdrücken in Name und Erweiterung, wie in den folgenden Beispielen:

   * Data[0-9][0-9][0-9].[dD][aA]&#39;port&#39;
   * &amp;ast;.[dD][Aa]&#39;port&#39;
   * &amp;ast;.[Xx][Mm][Ll]

Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](configuring-watched-folder-endpoints.md#about-file-patterns).


**Ergebnisordner**: Der Ordner, in dem die gespeicherten Ergebnisse abgelegt werden. Wenn die Ergebnisse nicht in diesem Ordner angezeigt werden, überprüfen Sie den Fehlerordner. Schreibgeschützte Dateien werden nicht verarbeitet und im Fehlerordner gespeichert. Dieser Wert kann ein absoluter oder relativer Pfad mit folgenden Dateimustern sein:

* %F = Dateinamenspräfix
* %E = Dateinamenerweiterung
* %Y = Jahr (vollständig)
* %y = Jahr (letzte zwei Stellen)
* %M = Monat
* %D = Tag des Monats
* %d = Tag des Jahres
* %H = Stunde (24-Stunden-Format)
* %h = Stunde (12-Stunden-Format)
* %m = Minute
* %s = Sekunde
* %l = Millisekunde
* %R = Zufallszahl (zwischen 0 und 9)
* %P = Prozess- oder Vorgangs-ID

Wenn es zum Beispiel 20 Uhr am 17. Juli 2009 ist und Sie `C:/Test/WF0/failure/%Y/%M/%D/%H/` angeben, lautet der Ergebnisordner `C:/Test/WF0/failure/2009/07/17/20`.

Wenn der Pfad nicht absolut, sondern relativ ist, wird der Ordner im überwachten Ordner erstellt. Der Standardwert ist result/%Y/%M/%D/, der Ergebnisordner im überwachten Ordner. Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](configuring-watched-folder-endpoints.md#about-file-patterns).

>[!NOTE]
>
>Je kleiner die Größe des Ergebnisordners, desto höher die Watched Folder-Leistung. Wenn beispielsweise die geschätzte Belastung für den überwachten Ordner bei 1000 Dateien pro Stunde liegt, sollten Sie ein Muster wie `result/%Y%M%D%H` verwenden, sodass jede Stunde ein neuer Unterordner erstellt wird. Wenn die Belastung geringer ist (z. B. 1000 Dateien pro Tag), können Sie ein Muster wie das folgende verwenden: `result/%Y%M%D`.

**Aufbewahrungsordner**: Der Ort, an dem Dateien nach erfolgreichem Überprüfen und Aufnehmen gespeichert werden. Der Pfad kann absolut, relativ oder ein Nullverzeichnispfad sein. Sie können Dateimuster wie für den Ergebnisordner beschrieben verwenden.  Der Standardwert ist „preserve/%Y/%M/%D/“.

**Fehlerordner**: Der Ordner, in dem Dateien mit Fehlern gespeichert werden. Dieser Speicherort ist stets relativ zum überwachten Ordner. Sie können Dateimuster verwenden, wie für &quot;Ergebnisordner&quot;beschrieben.

Schreibgeschützte Dateien werden nicht verarbeitet und im Fehlerordner gespeichert.

Der Standardwert ist „failure/%Y/%M/%D/“.

**Bei Fehler beibehalten:** Bewahren Sie Eingabedateien auf, wenn der Vorgang für einen Dienst nicht ausgeführt werden kann. Der Standardwert lautet true.

**Doppelte Dateinamen überschreiben**: Wenn diese Option auf „True“ gesetzt ist, werden Dateien im Ergebnisordner und im Aufbewahrungsordner überschrieben. Bei Festlegung auf „False“ wird an die Namen von Dateien und Ordnern ein numerisches Indexsuffix angehängt. Der Standardwert ist „False“.

**Bereinigungszeit** (obligatorisch): Dateien und Ordner im Ergebnisordner werden bereinigt, wenn sie älter als dieser Wert sind. Dieser Wert wird in Tagen gemessen. Diese Einstellung hilft sicherzustellen, dass der Ergebnisordner nicht voll wird.

Ein Wert von „-1“ Tagen bedeutet, dass der Ergebnisordner nie gelöscht wird. Der Standardwert ist -1.

**Vorgangsname** (obligatorisch): Eine Liste von Vorgängen, die dem Endpunkt des überwachten Ordners zugewiesen werden können.

**Zuordnungen von Eingabeparametern**: Dient zur Konfiguration der Eingaben, die zur Verarbeitung des Services und Vorgangs erforderlich sind. Die verfügbaren Einstellungen hängen davon ab, welcher Dienst den Endpunkt des überwachten Ordners verwendet. Im Folgenden finden Sie zwei Arten von Eingaben:

**Literal**: Der überwachte Ordner verwendet den in das Feld eingegebenen Wert so, wie er angezeigt wird. Alle grundlegenden Java-Typen werden unterstützt. Wenn eine API beispielsweise Eingaben wie String, Long, Int oder Boolean verwendet, wird die Zeichenfolge in einen ordnungsgemäßen Typ konvertiert und der Dienst aufgerufen.

**Variable**: Der eingegebene Wert ist ein Dateimuster, das vom überwachten Ordner zum Auswählen der Eingabe verwendet wird. Wenn beispielsweise der Dienst für das verschlüsselte Kennwort vorhanden ist, bei dem das Eingabedokument eine PDF-Datei sein muss, kann der Benutzer &amp;ast;.pdf als Dateimuster verwenden. Der überwachte Ordner nimmt alle Dateien im überwachten Ordner auf, die diesem Muster entsprechen, und ruft den Dienst für jede Datei auf. Wenn eine Variable verwendet wird, werden alle Eingabedateien in Dokumente konvertiert. Es werden nur APIs unterstützt, die Document als Eingabetyp verwenden.

**Zuordnungen von Ausgabeparametern**: Dient zur Konfiguration der Ausgaben des Dienstes und des Vorgangs. Die verfügbaren Einstellungen hängen davon ab, welcher Dienst den Endpunkt des überwachten Ordners verwendet.

Die Watched Folder-Ausgabe kann ein einzelnes Dokument, eine Liste von Dokumenten oder eine Zuordnung von Dokumenten sein. Diese Ausgabedokumente werden dann im Ergebnisordner gespeichert, wobei das in der Ausgabeparameterzuordnung angegebene Muster verwendet wird.

>[!NOTE]
>
>Die Angabe von Namen, die zu eindeutigen Ausgabedateinamen führen, verbessert die Leistung. Nehmen wir zum Beispiel den Fall, dass der Service ein Ausgabedokument zurückgibt und die Ausgabeparameter-Zuordnung es `%F.%E` (dem Dateinamen und der Erweiterung der Eingabedatei) zuordnet. In diesem Fall, wenn der Benutzer jede Minute Dateien mit demselben Namen ablegt und der Ergebnisordner auf `result/%Y/%M/%D` konfiguriert ist und die Einstellung „Doppelt vorhandene Dateinamen überschreiben“ deaktiviert ist, versucht der Watched Folder-Dienst die doppelten Dateinamen aufzulösen. Der Prozess des Auflösens von doppelten Dateinamen kann Auswirkungen auf die Leistung haben. In diesem Fall kann die Leistung verbessert werden, wenn die Ausgabeparameter-Zuordnung auf `%F_%h_%m_%s_%l` geändert wird, um dem Namen Stunden, Minuten, Sekunden und Millisekunden hinzuzufügen, oder wenn sichergestellt wird, dass abgelegte Dateien eindeutige Namen haben. 

## Über Dateimuster {#about-file-patterns}

Admins können den Dateityp angeben, von dem ein Dienst aufgerufen werden kann. Für jeden überwachten Ordner können mehrere Dateimuster festgelegt werden. Ein Dateimuster kann eine der folgenden Dateieigenschaften sein:

* Dateien mit bestimmten Dateinamenerweiterungen. Beispiel: &amp;ast;.dat, &amp;ast;.xml, &amp;ast;.pdf
* Dateien mit bestimmten Namen. Zum Beispiel Daten.*
* Dateien mit zusammengesetzten Ausdrücken in Name und Erweiterung, wie in den folgenden Beispielen:

   * Data[0-9][0-9][0-9].[dD][aA]&#39;port&#39;
   * &amp;ast;.[dD][Aa]&#39;port&#39;
   * &amp;ast;.[Xx][Mm][Ll]

Admins können das Dateimuster des Ausgabeordners definieren, in dem die Ergebnisse gespeichert werden sollen. Für die Ausgabeordner (Ergebnis, Beibehaltung und Fehler) können Admins eines der folgenden Dateimuster angeben:

* %Y = Jahr (vollständig)
* %y = Jahr (letzte zwei Stellen)
* %M = Monat
* %D = Tag des Monats
* %d = Tag des Jahres
* %h = Stunde
* %m = Minute
* %s = Sekunde
* %R = Zufallszahl zwischen 0 und 9
* %J = Auftragsname

Der Pfad zum Ergebnisordner kann beispielsweise `C:\Adobe\Adobe_Experience_Manager_forms\BarcodedForms\%y\%m\%d` lauten.

Über Zuordnungen von Ausgabeparametern können außerdem zusätzliche Muster angegeben werden, wie z. B.:

* %F = Quelldateiname
* %E = Quelldateinamenerweiterung

Wenn das Zuordnungsmuster der Ausgabeparameter mit &quot;File.separator&quot;(dem Pfadtrennzeichen) endet, wird ein Ordner erstellt und der Inhalt in diesen Ordner kopiert. Endet das Muster nicht mit „File.separator“, wird der Inhalt (Ergebnisdatei oder -ordner) mit diesem Namen erstellt. Weitere Informationen zu Zuordnungen von Ausgabeparametern finden Sie unter [Tipps und Tricks für überwachte Ordner](configuring-watched-folder-endpoints.md#tips-and-tricks-for-watched-folders).

## Über Einschränkungen {#about-throttling}

Wenn &quot;Einschränken&quot;für einen Endpunkt des Typs &quot;überwachter Ordner&quot;aktiviert ist, wird die Anzahl der Aufträge für überwachte Ordner begrenzt, die zu jeder Zeit verarbeitet werden können. Die maximale Anzahl von Aufträgen wird durch den Wert für die Batch-Größe bestimmt, der auch im Endpunkt des überwachten Ordners konfigurierbar ist. Eingehende Dokumente im Eingabeordner des überwachten Ordners werden nicht abgerufen, wenn die Beschränkung für die Einschränkungen erreicht wurde. Die Dokumente bleiben auch im Eingabeordner, bis andere Aufträge für überwachte Ordner abgeschlossen und ein weiterer Abrufversuch unternommen wurde. Bei synchroner Verarbeitung werden alle in einer einzigen Abfrage verarbeiteten Aufträge für die Drosselung berücksichtigt, auch wenn die Aufträge nacheinander in einem einzigen Thread verarbeitet werden.

>[!NOTE]
>
>Die Drosselung wird bei einem Cluster nicht skaliert. Wenn die Drosselung aktiviert ist, verarbeitet der Cluster insgesamt zu keinem Zeitpunkt mehr als die Anzahl der Aufträge, die in der Batch-Größe angegeben sind. Diese Beschränkung ist Cluster-weit und nicht für jeden Knoten im Cluster spezifisch. Bei einer Batch-Größe von 2 könnte beispielsweise das Einschränkungslimit mit einem einzigen Knoten erreicht werden, der zwei Aufträge verarbeitet, und keine anderen Knoten würden den Eingabeordner abrufen, bis einer der Aufträge abgeschlossen ist.

### Wie die Drosselung funktioniert {#how-throttling-works}

Der Watched Folder-Dienst überprüft den Eingabeordner bei jedem Wiederholungsintervall, nimmt die in der Stapelgröße angegebene Anzahl von Dateien auf und ruft den Zieldienst für jede dieser Dateien auf. Wenn die Stapelgröße beispielsweise 4 beträgt, nimmt der Watched Folder-Dienst bei jeder Überprüfung vier Dateien auf, erstellt vier Aufrufanforderungen und ruft den Zieldienst auf. Wenn der Watched Folder-Dienst vor Abschluss dieser Anforderungen erneut aufgerufen wird, werden unabhängig davon, ob die vorherigen vier Aufträge abgeschlossen sind, erneut vier Aufträge gestartet.

Die Drosselung verhindert, dass der Dienst für überwachte Ordner neue Aufträge aufruft, wenn die vorherigen Aufträge noch nicht abgeschlossen sind. Der Watched Folder-Dienst erkennt laufende Aufträge und verarbeitet neue Aufträge basierend auf der Batch-Größe abzüglich der laufenden Aufträge. Wenn im zweiten Aufruf beispielsweise nur drei Aufträge abgeschlossen sind und ein Auftrag noch ausgeführt wird, ruft der Dienst für überwachte Ordner nur drei weitere Aufträge auf.

* Der Dienst für überwachte Ordner verlässt sich bei der Ermittlung der Anzahl der laufenden Aufträge auf die Anzahl der im Bereitstellungsordner vorhandenen Dateien. Wenn Dateien im Bereitstellungsordner nicht verarbeitet werden, ruft der Watched Folder-Dienst keine weiteren Aufträge auf. Wenn die Stapelgröße beispielsweise 4 beträgt und drei Aufträge angehalten sind, ruft der Watched Folder-Dienst in nachfolgenden Aufrufen nur einen Auftrag auf. Es gibt mehrere Szenarien, in denen Dateien im Bereitstellungsordner unverarbeitet bleiben können. Wenn Aufträge angehalten werden, kann der Administrator den Prozess auf der Verwaltungsseite des Arbeitsablaufs für Formulare beenden, sodass der Watched Folder-Dienst die Dateien aus dem Bereitstellungsordner verschiebt.
* Wenn der Forms-Server heruntergefahren wird, bevor der Watched Folder-Dienst die Aufträge aufrufen kann, kann der Administrator die Dateien aus dem Bereitstellungsordner verschieben. Weitere Informationen finden Sie unter [Fehlerquellen und Wiederherstellung](configuring-watched-folder-endpoints.md#failure-points-and-recovery).
* Wenn der Forms-Server ausgeführt wird, der Watched Folder-Dienst jedoch nicht ausgeführt wird, wenn der Job Manager-Dienst zurückruft (wozu es kommt, wenn Dienste nicht in der richtigen Reihenfolge starten), kann der Administrator die Dateien aus dem Bereitstellungsordner verschieben. Weitere Informationen finden Sie unter [Fehlerquellen und Wiederherstellung](configuring-watched-folder-endpoints.md#failure-points-and-recovery).


## Leistung und Skalierbarkeit {#performance-and-scalability}

Der Watched Folder-Dienst kann insgesamt 100 Ordner auf einem einzelnen Knoten bereitstellen. Die Leistung des Watched Folder-Dienstes hängt von der Leistung des Forms-Servers ab. Bei asynchronem Aufruf hängt die Leistung stärker von der Systemlast und den Aufträgen ab, die sich in der Warteschlange &quot;Job Manager&quot;befinden.

Die Leistung des Watched Folder-Dienstes kann durch Hinzufügen von Knoten zum Cluster verbessert werden. Watched Folder-Aufträge werden durch den Quartz Scheduler auf den Clusterknoten und, falls asynchron, durch den Job Manager-Dienst verteilt. Alle Aufträge werden in der Datenbank beibehalten.

Der Watched Folder-Dienst ist für die Planung, Aufhebung der Zeitplanung und Umplanung der Aufträge vom Scheduler-Dienst abhängig. Andere Dienste wie der Event Management-Dienst, der User Manager-Dienst und der Email Provider-Dienst sind verfügbar, die den Thread-Pool des Scheduler-Dienstes gemeinsam nutzen. Dies kann sich auf die Leistung des überwachten Ordners auswirken. Die Thread-Optimierung des Thread-Pools des Scheduler-Dienstes ist erforderlich, wenn alle Dienste damit beginnen, ihn zu verwenden.

## Überwachte Ordner in einem Cluster {#watched-folders-in-a-cluster}

In einem Cluster ist der Watched Folder-Dienst für Lastenausgleich und Failover vom Quartz Scheduler und vom Job Manager-Dienst abhängig. Weitere Informationen zum Quartz-Clusterverhalten finden Sie unter [Quartz-Dokumentation](https://www.quartz-scheduler.org/documentation).

Der Watched Folder-Dienst führt bei jeder Abfrage die folgenden drei Hauptaufgaben aus:

* Überprüfen des Ordners
* Aufrufen des Zieldienstes
* Ergebnisse verarbeiten

Das Lastenausgleich- und Failover-Verhalten ändert sich je nachdem, ob der überwachte Ordner für den synchronen oder asynchronen Aufruf konfiguriert ist.

### Synchroner überwachter Ordner in einem Cluster {#synchronous-watched-folder-in-a-cluster}

Bei synchronen Aufrufen entscheidet der Quartz-Lastenausgleich, welcher Knoten das Abrufereignis erhält. Der Knoten, der das Abrufereignis erhält, führt alle Aufgaben aus: Überprüfen des Ordners, Aufrufen des Zieldienstes und Verarbeiten der Ergebnisse.

![en_synchwatchedfoldercluster](assets/en_synchwatchedfoldercluster.png)

Bei synchronen Aufrufen sendet der Quartz Scheduler neue Abrufereignisse an andere Knoten, wenn ein Knoten fehlschlägt. Aufrufe, die auf dem fehlerhaften Knoten gestartet wurden, gehen verloren. Weitere Informationen zum Wiederherstellen der mit dem fehlgeschlagenen Auftrag verknüpften Dateien finden Sie unter [Fehlerquellen und Wiederherstellung](configuring-watched-folder-endpoints.md#failure-points-and-recovery).


### Asynchroner überwachter Ordner in einem Cluster {#asynchronous-watched-folder-in-a-cluster}

Bei asynchronen Aufrufen entscheidet der Quartz-Lastenausgleich, welcher Knoten das Abrufereignis erhält. Der Knoten, der das Abrufereignis erhält, überprüft den Eingabeordner und ruft den Zieldienst auf, indem die Anforderung in die Warteschlange des Job Manager-Dienstes gestellt wird. Der Lastenausgleich des Job Manager-Dienstes ist wiederum dafür verantwortlich, zu entscheiden, welcher Knoten die Aufrufanforderung verarbeitet. Obwohl Knoten A die Aufrufanforderung erstellt hat, verarbeitet Knoten B die Anfrage letztendlich. Oder der Knoten, der die Aufrufanforderung gestartet hat, führt möglicherweise auch zur Verarbeitung der Anfrage.

![en_asynchwatchedfoldercluster](assets/en_asynchwatchedfoldercluster.png)

Wenn bei asynchronen Aufrufen ein Fehler bei einem Knoten auftritt, sendet der Quartz Scheduler neue Abrufereignisse an andere Knoten. Aufrufanforderungen, die auf dem fehlerhaften Knoten erstellt wurden, befinden sich in der Warteschlange des Job Manager-Dienstes und werden zur Verarbeitung an andere Knoten gesendet. Dateien, für die keine Aufrufanforderungen erstellt werden, verbleiben im Bereitstellungsordner. Weitere Informationen zum Wiederherstellen der mit dem fehlgeschlagenen Auftrag verknüpften Dateien finden Sie unter [Fehlerquellen und Wiederherstellung](configuring-watched-folder-endpoints.md#failure-points-and-recovery).


## Fehlerquellen und Wiederherstellung {#failure-points-and-recovery}

Bei jedem Abrufereignis sperrt der Dienst für überwachte Ordner den Eingabeordner, verschiebt die Dateien, die dem Muster für einzuschließende Dateien entsprechen, in den Bereitstellungsordner und entsperrt dann den Eingabeordner. Das Sperren ist erforderlich, damit zwei Threads nicht denselben Dateisatz abrufen und ihn zweimal verarbeiten. Die Wahrscheinlichkeit, dass dies geschieht, steigt mit einem kleinen Wiederholungsintervall und einer großen Stapelgröße. Nachdem die Dateien in den Bereitstellungsordner verschoben wurden, wird der Eingabeordner entsperrt, damit andere Threads den Ordner scannen können. Dieser Schritt bietet einen hohen Durchsatz, da andere Threads scannen können, während ein Thread die Dateien verarbeitet.

Nachdem die Dateien in den Bereitstellungsordner verschoben wurden, werden Aufrufanfragen für jede Datei erstellt, und der Zieldienst wird aufgerufen. Es kann vorkommen, dass der Dienst für überwachte Ordner die Dateien im Bereitstellungsordner nicht wiederherstellen kann:

* Wenn der Server heruntergefahren wird, bevor der Dienst für überwachte Ordner die Aufrufanfrage erstellen kann, bleiben die Dateien im Bereitstellungsordner und werden nicht wiederhergestellt.
* Wenn der Dienst für überwachte Ordner die Aufrufanfrage für jede der Dateien im Bereitstellungsordner erfolgreich erstellt hat und der Server abstürzt, gibt es je nach Aufruftyp zwei Verhaltensweisen:

**Synchron:** Wenn der Watched Folder-Dienst so konfiguriert ist, dass der Dienst synchron aufgerufen wird, bleiben alle Dateien im Bereitstellungsordner unverarbeitet im Bereitstellungsordner.

**Asynchron:** In diesem Fall ist der Watched Folder-Dienst vom Job Manager-Dienst abhängig. Wenn der Job Manager-Dienst den Dienst für überwachte Ordner zurückruft, werden die Dateien im Bereitstellungsordner basierend auf den Ergebnissen des Aufrufs in den Aufbewahrungs- oder Fehlerordner verschoben. Wenn der Job Manager-Dienst den Dienst für überwachte Ordner nicht zurückruft, bleiben die Dateien unverarbeitet im Bereitstellungsordner. Diese Situation tritt auf, falls der Dienst für überwachte Ordner nicht ausgeführt wird, wenn der Job Manager zurückruft.

### Nicht verarbeitete Quelldateien im Bereitstellungsordner wiederherstellen {#recovering-unprocessed-source-files-in-the-stage-folder}

Wenn der Dienst für überwachte Ordner die Quelldateien im Bereitstellungsordner nicht verarbeiten kann, können Sie die nicht verarbeiteten Dateien wiederherstellen.

1. Starten Sie den Anwendungs-Server oder Knoten neu.
1. (Optional) Beenden Sie den Watched Folder-Dienst daran, neue Eingabedateien zu verarbeiten. Wenn Sie diesen Schritt überspringen, ist es viel schwieriger zu bestimmen, welche Dateien im Bereitstellungsordner nicht verarbeitet wurden. Führen Sie eine der folgenden Aufgaben aus, um zu verhindern, dass der Dienst für überwachte Ordner neue Eingabedateien verarbeitet:

   * Ändern Sie in „Anwendungen und Dienste“ den Parameter „Muster für einzuschließende Dateien“ für den überwachten Ordner-Endpunkt in ein Muster, das keiner der neuen Eingabedateien entspricht (geben Sie beispielsweise `NOMATCH` ein).
   * Setzen Sie den Prozess aus, der neue Eingabedateien erstellt.

   Warten Sie, bis AEM Formulare alle Dateien wiederherstellt und verarbeitet. Die meisten Dateien sollten wiederhergestellt und alle neuen Eingabedateien korrekt verarbeitet werden. Die Wartezeit bis zum Wiederherstellen und Verarbeiten der Dateien durch den überwachten Ordner hängt von der Dauer des aufzurufenden Vorgangs und der Anzahl der wiederherzustellenden Dateien ab.

1. Bestimmen Sie, welche Dateien nicht verarbeitet werden können. Wenn Sie eine angemessene Zeitdauer abgewartet und den vorherigen Schritt abgeschlossen haben, sich aber immer noch nicht verarbeitete Dateien im Bereitstellungsordner befinden, fahren Sie mit dem nächsten Schritt fort.

   >[!NOTE]
   >
   >Sie können den Datums- und Zeitstempel der Dateien im Bereitstellungsverzeichnis anzeigen. Je nach Anzahl der Dateien und der normalen Verarbeitungsdauer können Sie ermitteln, welche Dateien so alt sind, dass sie als blockiert betrachtet werden können.

1. Kopieren Sie die nicht verarbeiteten Dateien aus dem Bereitstellungsordner in den Eingabeordner.
1. Wenn der Dienst für überwachte Ordner in Schritt 2 an der Verarbeitung neuer Eingabedateien gehindert wurde, ändern Sie den Parameter „Muster für einzuschließende Dateien“ in den vorherigen Wert zurück oder aktivieren Sie den zuvor deaktivierten Prozess erneut.

## Sicherheitsüberlegungen für überwachte Ordner {#security-considerations-for-watched-folders}

Jeder überwachte Ordner ist mit einem Benutzernamen und Kennwort konfiguriert. Diese Anmeldeinformationen werden beim Aufrufen der Dienste verwendet. Der Watched Folder-Dienst basiert auf der Tatsache, dass der freigegebene Ordner mit dem zugrunde liegenden Sicherheitsdateisystem geschützt ist, sodass nur der Eigentümer des überwachten Ordners auf den freigegebenen Ordner zugreifen kann.

## Tipps und Tricks für überwachte Ordner {#tips-and-tricks-for-watched-folders}

Im Folgenden finden Sie einige Tipps und Tricks zum Konfigurieren des Endpunkts des Typs &quot;überwachter Ordner&quot;:

* Wenn Sie unter Windows einen überwachten Ordner haben, der Bilddateien verarbeitet, geben Sie Werte für die Option &quot;Muster für einzuschließende Dateien&quot;oder &quot;Muster für auszuschließende Dateien&quot;an, um zu verhindern, dass die automatisch generierte Windows-Datei &quot;Thumbs.db&quot;vom überwachten Ordner abgerufen wird.
* Wenn ein Cron-Ausdruck angegeben ist, wird das Wiederholungsintervall ignoriert. Die Verwendung von Cron-Ausdrücken basiert auf dem Open-Source-Auftragsplanungssystem Quartz, Version 1.4.0.
* Die Stapelgröße ist die Anzahl der Dateien oder Ordner, die bei jeder Überprüfung des überwachten Ordners aufgenommen werden. Wenn die Stapelgröße auf zwei festgelegt ist und zehn Dateien oder Ordner im Eingabeordner des überwachten Ordners abgelegt werden, werden bei jeder Überprüfung nur zwei aufgenommen. Bei der nächsten Überprüfung, die nach der im Wiederholungsintervall festgelegten Zeit erfolgt, werden die nächsten beiden Dateien aufgenommen.
* Für Dateimuster können Administratoren reguläre Ausdrücke mit zusätzlicher Unterstützung für Platzhaltermuster angeben, um Dateimuster anzugeben. Bei der Überwachung von Ordnern wird der reguläre Ausdruck geändert, um Platzhaltermuster wie „*.*“ und „*.pdf“ zu unterstützen. Diese Platzhaltermuster werden von regulären Ausdrücken nicht unterstützt.
* Der Watched Folder-Dienst überprüft den Eingabeordner auf die Eingabe und weiß nicht, ob die Quelldatei oder der Quellordner vollständig in den Eingabeordner kopiert wurde, bevor die Verarbeitung der Datei oder des Ordners gestartet wird. Führen Sie die folgenden Aufgaben aus, um sicherzustellen, dass die Quelldatei oder der Ordner vollständig in den Eingabeordner des überwachten Ordners kopiert wird, bevor die Datei oder der Ordner aufgenommen wird:

   * Verwenden Sie die Wartezeit (in Millisekunden), die der Watched Folder-Dienst ab der letzten Änderung wartet. Verwenden Sie diese Funktion, wenn Sie große Dateien verarbeiten müssen. Wenn das Herunterladen einer Datei beispielsweise 10 Minuten dauert, geben Sie die Wartezeit als 10 x 60 x 1000 Millisekunden an. Dies verhindert, dass der Watched Folder-Dienst die Datei aufnimmt, wenn sie nicht älter als 10 Minuten ist.
   * Verwenden Sie das Muster für auszuschließende Dateien und das Muster für einzuschließende Dateien. Wenn zum Beispiel das Muster für auszuschließende Dateien `ex*` und das Muster für einzuschließende Dateien `in*` lautet, werden bei überwachten Ordnern die Dateien erfasst, die mit „in“ beginnen, aber nicht die, die mit „ex“ beginnen. Benennen Sie zum Kopieren großer Dateien oder Ordner zuerst die Datei bzw. den Ordner so um, dass der Name mit „ex“ beginnt. Benennen Sie die Datei bzw. den Ordner mit dem mit „ex“ beginnenden Namen nach vollständigem Abschluss des Kopiervorgangs in den überwachten Ordner wieder in „in*“ um.

* Verwenden Sie die Bereinigungsdauer, um den Ergebnisordner sauber zu halten. Der Watched Folder-Dienst bereinigt alle Dateien, die älter als die in der Bereinigungsdauer angegebene Dauer sind. Die Dauer wird in Tagen angegeben.
* Beim Hinzufügen eines Endpunkts des Typs &quot;Überwachter Ordner&quot;wird nach Auswahl des Vorgangsnamens die Zuordnung der Eingabeparameter ausgefüllt. Für jede Eingabe des Vorgangs wird ein Feld für die Zuordnung von Eingabeparametern generiert. Im Folgenden finden Sie Beispiele für Zuordnungen von Eingabeparametern:

   * Für die Eingabe `com.adobe.idp.Document` gilt: Wenn der Eingabetyp des Dienstvorgangs `Document` ist, kann der Administrator den Zuordnungstyp als `Variable` angeben. Der Watched Folder-Dienst nimmt die Eingabe aus dem Eingabeordner des überwachten Ordners basierend auf dem für den Eingabeparameter angegebenen Dateimuster auf. Wenn der Administrator `*.pdf` als Parameter angibt, wird jede Datei mit der Erweiterung „.pdf“ aufgenommen, in `com.adobe.idp.Document` konvertiert und der Service aufgerufen.
   * Für die Eingabe in `java.util.Map`: Wenn der Service-Vorgang eine Eingabe vom Typ `Map` hat, kann der Administrator den Zuordnungstyp als `Variable` angeben und einen Zuordnungswert mit einem Muster wie `*.pdf` eingeben. Angenommen ein Dienst benötigt eine Zuordnung von zwei `com.adobe.idp.Document`-Objekten, die zwei Dateien im Eingabeordner repräsentieren, z. B „1.pdf“ und „2.pdf“. Der Watched Folder-Dienst erstellt eine Zuordnung mit dem Dateinamen als Schlüssel und dem Wert `com.adobe.idp.Document`.
   * Für die Eingabe in `java.util.List`: Wenn der Service-Vorgang eine Eingabe vom Typ „Liste“ hat, kann der Administrator den Zuordnungstyp als `Variable` angeben und einen Zuordnungswert mit einem Muster wie `*.pdf` eingeben. Wenn PDF-Dateien im Eingabeordner abgelegt werden, erstellt der Watched Folder-Dienst eine Liste der `com.adobe.idp.Document`-Objekte, die diese Dateien repräsentiert, und ruft den Zieldienst auf.
   * Für `java.lang.String` gilt: Der Administrator hat zwei Möglichkeiten. Zunächst kann der Administrator den Zuordnungstyp als `Literal` angeben und einen Zuordnungswert als Zeichenfolge eingeben, z. B. `hello.`. Der überwachte Ordner ruft den Service mit der Zeichenfolge `hello` auf. Zweitens kann der Administrator den Zuordnungstyp als `Variable` angeben und einen Zuordnungswert mit einem Muster wie `*.txt` eingeben. Im zweiten Fall werden Dateien mit der TXT-Endung als Dokument gelesen, das zwangsweise in eine Zeichenfolge umgewandelt ist, um den Dienst aufzurufen.
   * Der Administrator kann den Zuordnungstyp als `Literal` angeben und den Wert vorgeben. Der Watched Folder-Dienst ruft den Dienst mit dem angegebenen Wert auf.

* Der Watched Folder-Dienst ist für die Arbeit mit Dokumenten vorgesehen. Die unterstützten Ausgaben sind `com.adobe.idp.Document`, `org.w3c.Document`, `org.w3c.Node`und eine Liste und Zuordnung dieser Typen. Jeder andere Typ führt zu einer Fehlerausgabe im Fehlerordner.
* Wenn sich die Ergebnisse nicht im Ergebnisordner befinden, überprüfen Sie den Fehlerordner, um festzustellen, ob ein Fehler aufgetreten ist.
* Der Watched Folder-Dienst funktioniert am besten, wenn er im asynchronen Modus verwendet wird. In diesem Modus platziert der Watched Folder-Dienst die Aufrufanforderung in die Warteschlange und ruft zurück. Die Warteschlange wird dann asynchron verarbeitet. Wenn die Option &quot;Asynchron&quot;nicht festgelegt ist, ruft der Watched Folder-Dienst den Zieldienst synchron auf und die Prozess-Engine wartet, bis der Dienst mit der Anforderung fertig ist und Ergebnisse generiert werden. Wenn die Verarbeitung der Anforderung durch den Zieldienst lange dauert, kann es beim Watched Folder-Dienst zu Zeitüberschreitungsfehlern kommen.
* Die Erstellung von überwachten Ordnern für Import- und Exportvorgänge ermöglicht keine Abstraktion von Dateinamenerweiterungen. Beim Aufrufen des Form Data Integration-Dienstes mit überwachten Ordnern stimmt der Dateinamenerweiterungstyp für die Ausgabedatei möglicherweise nicht mit dem beabsichtigten Ausgabeformat für den Dokumentobjekttyp überein. Wenn die Eingabedatei für einen überwachten Ordner, der den Exportvorgang aufruft, beispielsweise ein XFA-Formular ist, das Daten enthält, sollte die Ausgabe eine XDP-Datendatei sein. Um eine Ausgabedatei mit der richtigen Dateinamenerweiterung zu erhalten, können Sie sie in der Zuordnung der Ausgabeparameter angeben. In diesem Beispiel können Sie %F.xdp für die Zuordnung von Ausgabeparametern verwenden.
* Der Watched Folder-Dienst kann Eingabedateien verarbeiten, bevor sie vollständig in den Ordner kopiert werden. Das Sperren von Dateien ist unter UNIX nicht erforderlich, da es sich unter Windows befindet. Aus diesem Grund kann der Watched Folder-Dienst die Datei beim Kopieren einer Datei in einen überwachten Ordner in die Staging-Umgebung verschieben, ohne auf den Abschluss der Dateikopie zu warten. Durch dieses Verhalten wird nur ein Teil der Eingabedatei verarbeitet. Derzeit gibt es zwei Problemumgehungen:

   * Problemumgehung 1

      1. Geben Sie ein Muster für „Muster für auszuschließende Dateien“ an, beispielsweise „temp*.ps“.
      1. Kopieren Sie Dateien, deren Namen mit „temp“ beginnen (z. B. „temp1.ps“), in den überwachten Ordner.
      1. Nachdem die Datei vollständig in den überwachten Ordner kopiert wurde, benennen Sie die Datei so um, dass der Name dem für „Muster für einzuschließende Dateien“ angegebenen Muster entspricht. Der Watched Folder-Dienst verschiebt dann die abgeschlossene Datei in die Bühne.

   * Problemumgehung 2

     Wenn Sie wissen, wie lange es maximal dauert, Ihre Dateien in einen überwachten Ordner zu kopieren, geben Sie die Zeit in Sekunden für die Wartezeit an. Der Watched Folder-Dienst wartet dann die angegebene Zeitdauer, bevor die Datei in die Staging-Umgebung verschoben wird.

     Dies ist kein Problem für Dateien unter Windows, da Windows eine Datei sperrt, wenn ein Thread schreibt. Dies ist jedoch ein Problem für Ordner unter Windows. Für Ordner müssen Sie die Schritte unter Problemumgehung 1 ausführen.

* Wenn das Endpunktattribut &quot;Ordnername beibehalten&quot;für den überwachten Ordner auf einen Nullverzeichnispfad festgelegt ist, wird der Staging-Ordner nicht wie gewünscht bereinigt. Der Ordner enthält weiterhin die verarbeitete Datei und den temporären Ordner.

## Dienstspezifische Empfehlungen für überwachte Ordner {#service-specific-recommendations-for-watched-folders}

Bei allen Diensten sollten Sie die Stapelgröße und das Wiederholungsintervall des überwachten Ordners so anpassen, dass die Rate, mit der der Watched Folder-Dienst neue Dateien und Ordner zur Verarbeitung aufnimmt, nicht die Verarbeitungsrate für Aufträge überschreitet, die vom AEM Forms-Server verarbeitet werden können. Die tatsächlichen Parameter, die verwendet werden sollen, variieren je nachdem, wie viele überwachte Ordner konfiguriert sind, welche Dienste überwachte Ordner verwenden und wie intensiv die Aufträge auf dem Prozessor sind.

### Empfehlungen für den Generate PDF-Dienst {#generate-pdf-service-recommendations}

* Der Generate PDF-Dienst kann für die folgenden Dateitypen jeweils nur eine Datei konvertieren: Microsoft Word, Microsoft Excel, Microsoft PowerPoint, Microsoft Project, AutoCAD, Adobe Photoshop®, Adobe FrameMaker® und Adobe PageMaker®. Hierbei handelt es sich um Aufträge mit langer Laufzeit. Achten Sie daher darauf, die Batch-Größe auf eine niedrige Einstellung festzulegen. Erhöhen Sie außerdem das Wiederholungsintervall, wenn sich im Cluster weitere Knoten befinden.
* Für PostScript (PS), Encapsulated PostScript (EPS) und Bilddateitypen kann der Generate PDF-Dienst mehrere-Dateien parallel verarbeiten. Sie sollten die Poolgröße des Sitzungsangebots (die die Anzahl der parallel durchgeführten Konvertierungen steuert) abhängig von der Kapazität Ihres Servers und der Anzahl der Knoten im Cluster sorgfältig anpassen. Erhöhen Sie dann die Batch-Größe auf eine Zahl, die der Session Beans-Poolgröße für die Dateitypen entspricht, die Sie konvertieren möchten. Die Abrufhäufigkeit sollte von der Anzahl der Knoten im Cluster bestimmt werden. Da der Generate PDF-Dienst diese Arten von Aufträgen jedoch ziemlich schnell verarbeitet, können Sie das Wiederholungsintervall auf einen niedrigen Wert wie 5 oder 10 konfigurieren.
* Obwohl der Generate PDF-Dienst nur eine OpenOffice-Datei gleichzeitig konvertieren kann, ist die Konvertierung ziemlich schnell. Die obige Logik für PS-, EPS- und Bildkonvertierungen gilt auch für OpenOffice-Konvertierungen.
* Um eine gleichmäßige Lastverteilung im Cluster zu aktivieren, halten Sie die Stapelgröße niedrig und erhöhen Sie das Wiederholungsintervall.

### Empfehlungen für Barcoded Forms-Dienst {#barcoded-forms-service-recommendations}

* Geben Sie zur Erzielung einer optimalen Leistung bei der Verarbeitung von Formularen mit Strichcode (kleine Dateien) als Stapelgröße `10` und als Wiederholungsintervall `2` ein.
* Befinden sich viele Dateien im Eingabeordner, kann es zu Fehlern mit ausgeblendeten Dateien namens „*thumbs.db*“ kommen. Es wird daher empfohlen, das „Muster für einzuschließende Dateien“ auf denselben Wert festzulegen wie den für die Eingabevariable festgelegten Wert (z. B. `*.tiff`). Auf diese Weise wird der Watched Folder-Dienst daran gehindert, die DB-Dateien zu verarbeiten.
* Eine Stapelgröße von `5` und ein Wiederholungsintervall von `2` sind normalerweise ausreichend, da der Barcoded Forms-Dienst für gewöhnlich ungefähr 0,5 Sekunden für die Verarbeitung eines Strichcodes benötigt.
* Der Watched Folder-Dienst wartet nicht, bis die Prozess-Engine den Auftrag abgeschlossen hat, bevor neue Dateien oder Ordner aufgenommen werden. Der überwachte Ordner wird weiterhin überprüft und der Zieldienst aufgerufen. Dieses Verhalten kann die Engine überlasten und zu Ressourcenproblemen und Zeitüberschreitungen führen. Stellen Sie sicher, dass Sie das Wiederholungsintervall und die Stapelgröße verwenden, um die Watched Folder-Eingabe zu beschränken. Sie können das Wiederholungsintervall erhöhen und die Stapelgröße verringern, wenn mehr überwachte Ordner vorhanden sind, oder die Drosselung am Endpunkt aktivieren. Informationen zur Einschränkungen finden Sie unter [Über Einschränkungen](configuring-watched-folder-endpoints.md#about-throttling).
* Der Watched Folder-Service nimmt die Identität des im Benutzer- und Domain-Namen angegebenen Benutzers an. Der Watched Folder-Dienst ruft den Dienst als dieser Benutzer auf, wenn er direkt aufgerufen wird oder wenn der Prozess kurzlebig ist. Bei einem langlebigen Prozess wird der Prozess mit dem Systemkontext aufgerufen. Administratoren können Betriebssystemrichtlinien für den überwachten Ordner festlegen, um zu bestimmen, welchem Benutzer der Zugriff gestattet oder verweigert werden soll.
* Verwenden Sie Dateimuster, um Ergebnis-, Fehler- und Aufbewahrungsordner zu organisieren. (Siehe [Über Dateimuster](configuring-watched-folder-endpoints.md#about-file-patterns).

* Der Watched Folder-Dienst verlässt sich beim Überprüfen der überwachten Ordner auf den Quartz Scheduler. Der Quartz Scheduler verfügt über einen Thread-Pool, um sie zu überprüfen. Wenn das Wiederholungsintervall für den überwachten Ordner sehr niedrig (&lt; 5 Sekunden) ist und die Stapelgröße hoch (> 2) ist, kann es zu einer Race-Bedingung kommen. Wenn diese Bedingung eintritt, wird eine Datei von zwei Quartz-Threads abgerufen:

   * Einer der Threads findet die Datei erfolgreich und ruft den Zieldienst mit der Datei auf.
   * Der zweite Thread sieht die Datei, schlägt jedoch fehl, wenn versucht wird herauszufinden, ob die Datei gültig ist (Lese- oder Schreibdatei), was zu falschen Fehlern führt, die darauf hinweisen, dass die Datei nicht verarbeitet werden kann, da sie schreibgeschützt ist. Dies geschieht nur mit einem niedrigen Wiederholungsintervall und einer hohen Stapelgröße.
