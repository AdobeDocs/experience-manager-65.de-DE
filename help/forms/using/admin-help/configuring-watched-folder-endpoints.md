---
title: Konfigurieren von Endpunkten des Typs „Überwachter Ordner“
description: Erfahren Sie, wie Sie Endpunkte des Typs „Überwachter Ordner“ konfigurieren können. Wenn ein Dokument im überwachten Ordner abgelegt wird, wird ein konfigurierter Dienstvorgang aufgerufen, der die Datei bearbeitet.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
exl-id: ec169a01-a113-47eb-8803-bd783ea2c943
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '7192'
ht-degree: 100%

---

# Konfigurieren von Endpunkten des Typs „Überwachter Ordner“ {#configuring-watched-folder-endpoints}

Admins können einen Netzwerkordner konfigurieren, der als *überwachter Ordner* bezeichnet wird, sodass ein konfigurierter Dienstvorgang zur Verarbeitung einer Datei aufgerufen wird, wenn jemand eine Datei (z. B. eine PDF-Datei) in diesem überwachten Ordner ablegt. Nachdem der Dienst den vorgesehenen Vorgang ausgeführt hat, wird die geänderte Datei in einem angegebenen Ausgabeordner gespeichert.

## Konfigurieren des Watched Folder-Dienstes {#configuring-the-watched-folder-service}

Bevor Sie einen überwachten Ordner als Endpunkt konfigurieren, konfigurieren Sie den Watched Folder-Dienst. Die Konfigurationsparameter des Watched Folder-Dienstes haben zwei Verwendungszwecke:

* Das Konfigurieren von Attributen, die für alle Endpunkte des Typs „Überwachter Ordner“ gültig sind.
* Das Bereitstellen von Standardwerten für alle Endpunkte des Typs „Überwachter Ordner“.

Im Anschluss an die Konfiguration des Watched Folder-Dienstes fügen Sie einen Endpunkt des Typs „Überwachter Ordner“ für den Zieldienst hinzu.  Beim Hinzufügen des Endpunktes legen Sie Werte fest, z. B. den Dienstnamen und den Vorgangsnamen, die aufgerufen werden sollen, wenn Dateien oder Ordner im Eingabeordner des konfigurierten Watched Folder-Dienstes abgelegt werden. Weitere Informationen zum Konfigurieren des Watched Folder-Dienstes finden Sie unter [Einstellungen des Watched Folder-Dienstes](/help/forms/using/admin-help/configure-service-settings.md#watched-folder-service-settings).

## Erstellen eines überwachten Ordners {#creating-a-watched-folder}

Es gibt zwei Möglichkeiten, einen überwachten Ordner zu erstellen:

* Geben Sie bei der Konfiguration der Einstellungen für einen Endpunkt des Typs „Überwachter Ordner“ den vollständigen Pfad zum übergeordneten Verzeichnis in das Feld „Pfad“ ein und hängen Sie den Namen des zu erstellenden überwachten Ordners an, wie in diesem Beispiel:
  `  C:\MyPDFs\MyWatchedFolder`Da der Ordner „MyWatchedFolder“ noch nicht vorhanden ist, versucht AEM Forms, ihn an diesem Speicherort zu erstellen.

* Erstellen Sie vor dem Konfigurieren eines Endpunktes des Typs „Überwachter Ordner“ einen Ordner im Dateisystem und geben Sie anschließend in das Feld „Pfad“ den vollständigen Pfad ein.

In einer Cluster-Umgebung muss der Ordner, der als überwachter Ordner verwendet wird, zugriffsbereit sein, Schreibzugriff bieten und im Dateisystem oder Netzwerk freigegeben sein. In diesem Szenario muss jede Anwendungs-Server-Instanz des Clusters Zugriff auf denselben freigegebenen Ordner haben.

Wird der Anwendungs-Server unter Windows als Dienst ausgeführt, muss er durch eine der folgenden Methoden mit dem entsprechenden Zugriff auf den freigegebenen Ordner gestartet werden:

* Konfigurieren Sie den **Parameter** „Log On As“ des Anwendungsserverdiensts so, dass er als spezifischer Benutzer mit geeignetem Zugriff auf den freigegebenen überwachten Ordner gestartet wird.
* Konfigurieren Sie die Option „Start as Local System“ des Anwendungsserverdiensts so, dass die Interaktion des Diensts mit dem Desktop zulässig ist. Diese Option erfordert, dass der freigegebene überwachte Ordner für alle zugänglich ist und Schreibzugriff bietet.

## Verketten überwachter Ordner {#chaining-together-watched-folders}

Überwachte Ordner können miteinander verkettet werden, sodass ein Ergebnisdokument eines überwachten Ordners zum Eingabedokument des nächsten überwachten Ordners wird. Jeder überwachte Ordner kann einen anderen Dienst aufrufen. Indem überwachte Ordner auf diese Weise konfiguriert werden, können mehrere Dienste aufgerufen werden. Zum Beispiel kann ein überwachter Ordner PDF-Dateien in Adobe PostScript® und ein anderer PostScript-Dateien in PDF/A konvertieren. Legen Sie dazu den *Ergebnisordner* des vom ersten Endpunkt definierten überwachten Ordners so fest, dass er auf den *Eingabeordner* des vom zweiten Endpunkt definierten überwachten Ordners verweist.

Die Ausgabe der ersten Konvertierung wird an „\Pfad\result“ übergeben. Als Eingabe der zweiten Konvertierung dient „\Pfad\result“, und die Ausgabe der zweiten Konvertierung wird in „\Pfad\result\result“ oder den Ordner übertragen, den Sie im Feld „Ergebnisordner“ für die zweite Konvertierung angegeben haben.

## Benutzerinteraktion mit überwachten Ordnern {#how-users-interact-with-watched-folders}

Bei Endpunkten des Typs „überwachter Ordner“ können Benutzende Eingabedateien oder Ordner von ihrem Desktop in einen überwachten Ordner kopieren oder ziehen. Die Dateien werden in der Reihenfolge ihres Eingangs verarbeitet.

Wenn bei Endpunkten des Typs „überwachter Ordner“ der Auftrag nur eine Eingabedatei erfordert, kann diese Datei in den Stammordner des überwachten Ordners kopiert werden.

Wenn der Auftrag mehrere Eingabedateien umfasst, müssen die Benutzenden einen Ordner außerhalb der Hierarchie des überwachten Ordners erstellen, der alle erforderlichen Dateien enthält. Dieser neue Ordner sollte die Eingabedateien enthalten (und optional eine DDX-Datei, falls sie vom Prozess benötigt wird). Nachdem der Auftragsordner erstellt wurde, kopieren sie ihn in den Eingabeordner des überwachten Ordners.

>[!NOTE]
>
>Stellen Sie sicher, dass der Anwendungs-Server Löschzugriff auf die Dateien im überwachten Ordner hat. Wenn AEM Forms die Dateien nicht aus dem Eingabeordner löschen kann, nachdem sie durchsucht wurden, wird der dazugehörige Prozess unendlich oft aufgerufen.

## Ausgabe des überwachten Ordners {#watched-folder-output}

Wenn die Eingabe ein Ordner ist und die Ausgabe mehrere Dateien umfasst, erstellt AEM Forms einen Ausgabeordner mit dem Namen des Eingabeordners und kopiert die Ausgabedateien in diesen Ordner. Besteht die Ausgabe aus einer Dokumentzuordnung mit einem Schlüssel-Wert-Paar, wie z. B. die Ausgabe eines Ausgabeprozesses, wird der Schlüssel als Ausgabedateiname verwendet.

Die Ausgabedateinamen, die aus einem Endpunktprozess resultieren, dürfen keine anderen Zeichen als Buchstaben, Zahlen und einen Punkt (.)  vor der Dateierweiterung enthalten. AEM Forms konvertiert andere Zeichen in Hexadezimalwerte.

Client-Anwendungen rufen die Zieldokumente aus dem Ergebnisordner des überwachten Ordners ab.  Prozessfehler werden im Fehlerordner des überwachten Ordners protokolliert.

## Funktionsweise von überwachten Ordnern {#how-watched-folder-works}

Das Modul „Überwachter Ordner“ enthält folgende Dienste:

* Watched Folder-Dienst 
* provider.file_scan_service
* provider.file_write_results_service

Zusätzlich zu diesen Diensten hängt der Watched Folder-Dienst auch von anderen Diensten ab, z. B. dem Scheduler-Dienst für das Planen der Aufträge und dem Job Manager-Dienst zur Unterstützung des asynchronen Aufrufs von Zieldiensten.

### Verarbeiten einer Aufrufanforderung durch den Watched Folder-Dienst {#how-watched-folder-processes-an-invocation-request}

Der Watched Folder-Dienst verarbeitet das Erstellen, Aktualisieren und Löschen der Endpunkte.  Nachdem die Admins die Endpunkte erstellt haben, wird deren Auslösung durch den Scheduler-Dienst basierend auf dem angegebenen Wiederholungsintervall oder Cron-Ausdruck geplant.

Dieses Diagramm zeigt, wie eine Aufrufanfrage von Prozessen für überwachte Ordner verarbeitet wird.

![en_watchedfolder](assets/en_watchedfolder.png)

Der Prozess des Aufrufens eines Dienstes mithilfe überwachter Ordner läuft folgendermaßen ab:

1. Eine Client-Anwendung legt Dateien oder Ordner im Eingabeordner des überwachten Ordners ab.
1. Wenn das Auftragssuchintervall abgelaufen ist, ruft der Scheduler-Dienst den „provider.file_scan_service“-Dienst auf, um die Dateien oder Ordner im Eingabeordner zu verarbeiten.
1. Der „provider.file_scan_service“-Dienst führt die folgenden Aufgaben aus:


   * Er durchsucht den Eingabeordner nach Dateien oder Ordnern, die dem Muster für einzuschließende Dateien entsprechen, und schließt Dateien oder Ordner aus, die dem Muster für auszuschließende Dateien entsprechen.  Die ältesten Dateien oder Ordner werden zuerst ausgewählt.  Dateien und Ordner, die älter als die Wartezeit sind, werden ebenfalls ausgewählt.  In einem Suchvorgang basiert die Anzahl der verarbeiteten Dateien bzw. Ordner auf der Batch-Größe.  Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](configuring-watched-folder-endpoints.md#about-file-patterns).  Informationen zum Einstellen der Stapelgröße finden Sie unter [Einstellungen des Watched Folder-Dienstes](/help/forms/using/admin-help/configure-service-settings.md#watched-folder-service-settings).
   * Der Dienst wählt die zu verarbeitenden Dateien oder Ordner aus.  Wenn die Dateien oder Ordner nicht vollständig heruntergeladen wurden, werden sie im nächsten Suchvorgang ausgewählt.  Um sicherzustellen, dass Ordner vollständig heruntergeladen werden, müssen Admins unter Verwendung des Musters für auszuschließende Dateien einen benannten Ordner erstellen.  Sobald der Ordner alle Dateien enthält, muss er in das Muster umbenannt werden, das im Muster für einzuschließende Dateien angegeben ist.  Dieser Schritt gewährleistet, dass der Ordner alle erforderlichen Dateien zum Aufrufen des Dienstes enthält.  Informationen dazu, wie Sie sicherstellen, dass Ordner vollständig heruntergeladen werden, finden Sie unter [Tipps und Tricks für überwachte Ordner](configuring-watched-folder-endpoints.md#tips-and-tricks-for-watched-folders).
   * Der Dienst verschiebt die Dateien oder Ordner in den Bereitstellungsordner, nachdem sie zur Verarbeitung ausgewählt wurden.
   * Der Dienst konvertiert die Dateien oder Ordner im Bereitstellungsordner basierend auf den Parameterzuordnungen für die Endpunkteingabe.  Beispiele für Zuordnungen von Eingabeparametern finden Sie unter [Tipps und Tricks für überwachte Ordner](configuring-watched-folder-endpoints.md#tips-and-tricks-for-watched-folders).


1. Der für den Endpunkt konfigurierte Zieldienst wird entweder synchron oder asynchron aufgerufen.  Der Zieldienst wird unter Verwendung des Benutzernamens und Kennworts aufgerufen, die für den Endpunkt konfiguriert sind.

   * Bei einem synchronen Aufruf wird der Zieldienst direkt aufgerufen, woraufhin die Antwort unmittelbar verarbeitet wird.
   * Bei einem asynchronen Aufruf wird der Zieldienst über den Job Manager-Dienst aufgerufen, der die Anforderung in einer Warteschlange ablegt. Der Job Manager-Dienst ruft wiederum den „provider.file_write_results_service“-Dienst auf, um die Ergebnisse zu verarbeiten.

1. Der „provider.file_write_results_service“-Dienst verarbeitet die Antwort oder das Fehlschlagen des Zieldienstaufrufs.  Bei erfolgreichem Abschluss wird die Ausgabe auf Grundlage der Endpunktkonfiguration im Ergebnisordner gespeichert.  Der „provider.file_write_results_service“-Dienst behält auch die Quelle bei, wenn der Endpunkt für die Beibehaltung der Ergebnisse nach einem erfolgreichen Abschluss konfiguriert ist.

   Wenn der Aufruf des Zieldienstes fehlschlägt, protokolliert der „provider.file_write_results_service“-Dienst den Grund in der Datei „failure.log“ und legt diese Datei im Fehlerordner ab. Der Fehlerordner wird auf Grundlage der für den Endpunkt angegebenen Konfigurationsparameter erstellt.  Wenn die Admins die Option „Bei Fehler beibehalten“ für die Endpunktkonfiguration festlegen, kopiert der „provider.file_write_results_service“-Dienst auch die Quelldateien in den Fehlerordner. Informationen zum Wiederherstellen von Dateien aus dem Fehlerordner finden Sie unter [Fehlerquellen und Wiederherstellung](configuring-watched-folder-endpoints.md#failure-points-and-recovery).


## Einstellungen für Endpunkte des Typs „Überwachter Ordner“ {#watched-folder-endpoint-settings}

Mithilfe der folgenden Einstellungen können Sie einen Endpunkt des Typs „überwachter Ordner“ konfigurieren.

**Name** (obligatorisch): Gibt den Endpunkt an. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird. Wenn Sie eine URL als Namen des Endpunktes eingeben, vergewissern Sie sich, dass sie den in RFC1738 angegebenen Syntaxregeln entspricht.

**Beschreibung**: Eine Beschreibung des Endpunkts. Der Name darf kein &lt;-Zeichen enthalten, weil dadurch die Anzeige des Namens in Workspace abgeschnitten wird.

**Pfad** (obligatorisch): Gibt den Speicherort des überwachten Ordners an. In einer Clusterumgebung muss diese Einstellung auf einen freigegebenen Netzwerkordner zeigen, auf den alle Computer im Cluster zugreifen können.

**Asynchron**: Bestimmt, ob ein asynchroner oder ein synchroner Aufruftyp verwendet wird. Der Standardwert ist „asynchron“. „Asynchron“ wird für langlebige Prozesse empfohlen, „synchron“ für transiente und kurzlebige Prozesse.

**Cron-Ausdruck**: Geben Sie einen Cron-Ausdruck ein, wenn der überwachte Ordner mithilfe eines Cron-Ausdrucks geplant werden muss. Wenn diese Einstellung konfiguriert ist, wird „Repeat Interval“ ignoriert.

**Wiederholungsintervall**: Das Intervall in Sekunden, in dem der überwachte Ordner auf Eingaben überprüft wird. Außer wenn die Einstellung „Einschränken“ aktiviert ist, muss das Abfrageintervall länger sein als die Verarbeitungsdauer für einen durchschnittlichen Auftrag. Andernfalls kann es zu einer Überlastung des Systems kommen. Der Standardwert ist 5. Weitere Informationen finden Sie in der Beschreibung für die Stapelgröße.

**Wiederholungsanzahl**: Anzahl, wie oft der überwachte Ordner oder das Verzeichnis überprüft wird. Der Wert „-1“ steht für eine uneingeschränkte („unendliche“) Überprüfung. Der Standardwert ist -1.

**Drosselung**: Wenn diese Option ausgewählt ist, wird die Anzahl der Aufträge für überwachte Ordner begrenzt, die AEM Forms zu einem bestimmten Zeitpunkt verarbeitet. Die maximale Anzahl von Aufträgen wird durch den Wert von „Stapelgröße“ bestimmt. (Siehe Informationen zu Einschränkungen.)

**Benutzername** (obligatorisch): Der Benutzername, der beim Aufrufen eines Ziel-Services aus dem überwachten Ordner verwendet wird. Der Standardwert ist „SuperAdmin“.

**Domain-Name** (obligatorisch): Die Domain der Benutzerin bzw. des Benutzers. Der Standardwert ist „DefaultDom“.

**Stapelgröße**: Die Anzahl der Dateien oder Ordner, die pro Überprüfung aufgenommen werden. Mit dieser Einstellung können Sie eine Überlastung des Systems verhindern, da das gleichzeitige Überprüfen zu vieler Dateien zu einem Absturz führen kann. Der Standardwert ist 2.

Die Einstellungen „Wiederholungsintervall“ und „Stapelgröße“ bestimmen, wie viele Dateien bei jeder Überprüfung vom Watched Folder-Dienst ausgewählt werden. Der überwachte Ordner verwendet einen Quartz-Threadpool für die Überprüfung des Eingabeordners. Der Threadpool wird mit anderen Diensten gemeinsam verwendet. Je kürzer das Überprüfungsintervall kurz ist, desto häufiger wird der Eingabeordner von den Threads überprüft. Falls häufig Dateien im überwachten Ordner abgelegt werden, sollten Sie ein kurzes Überprüfungsintervall wählen. Wenn Dateien nicht häufig abgelegt werden, sollten Sie ein größeres Überprüfungsintervall einrichten, damit die anderen Dienste die Threads verwenden können.

Falls eine große Anzahl von Dateien abgelegt wird, wählen Sie eine große Stapelgröße.  Wenn der vom Endpunkt des überwachten Ordners aufgerufene Dienst beispielsweise 700 Dateien pro Minute verarbeiten kann und die Benutzenden Dateien mit der gleichen Geschwindigkeit in den Eingabeordner ablegen, kann die Leistung des überwachten Ordners durch die Einstellung der Stapelgröße auf 350 und des Wiederholungsintervalls auf 30 Sekunden verbessert werden, ohne dass die Kosten für eine zu häufige Überprüfung des überwachten Ordners anfallen.

Wenn Dateien im überwachten Ordner abgelegt werden, werden die Dateien in der Eingabe aufgelistet, was die Leistung beeinträchtigen kann, wenn jede Sekunde eine Überprüfung stattfindet. Ein Verlängern des Überprüfungsintervalls kann die Leistung verbessern. Wenn das Volumen der abzulegenden Dateien gering ist, passen Sie die Batch-Größe und das Wiederholungsintervall entsprechend an. Wenn beispielsweise jede Sekunde 10 Dateien abgelegt werden, versuchen Sie, das Wiederholungsintervall auf 1 Sekunde und die Batch-Größe auf 10 festzulegen.

**Wartezeit**: Die Zeit in Millisekunden, die gewartet werden soll, bevor ein Ordner oder eine Datei nach der Erstellung überprüft wird. Wenn die Wartezeit beispielsweise 3.600.000 Millisekunden (eine Stunde) beträgt und die Datei vor einer Minute erstellt wurde, wird diese Datei frühestens in 59 Minuten abgerufen. Der Standardwert ist 0.

Diese Einstellung ist nützlich, um sicherzustellen, dass eine Datei oder ein Ordner vollständig in den Eingabeordner kopiert wird. Wenn Sie beispielsweise eine große Datei verarbeiten müssen und das Herunterladen der Datei 10 Minuten dauert, legen Sie die Wartezeit auf 10 x 60 x 1000 Millisekunden fest. Dies verhindert, dass der überwachte Ordner die Datei überprüft, wenn sie nicht 10 Minuten alt ist.

**Dateimuster ausschließen**: Eine durch Semikolon **;** getrennte Liste von Mustern, die ein überwachter Ordner verwendet, um zu bestimmen, welche Dateien und Ordner überprüft und aufgenommen werden sollen. Alle Dateien oder Ordner, die diesem Muster entsprechen, werden nicht zur Verarbeitung überprüft.

Diese Einstellung ist hilfreich, wenn die Eingabe aus einem Ordner mit mehreren Dateien besteht. Der Inhalt des Ordners kann in einen Ordner mit einem Namen kopiert werden, der vom überwachten Ordner aufgenommen wird. Dies verhindert, dass der überwachte Ordner einen Ordner zur Verarbeitung aufnimmt, bevor dieser vollständig in den Eingabeordner kopiert wurde.

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

Wenn der Pfad nicht absolut, sondern relativ ist, wird der Ordner im überwachten Ordner erstellt. Der Standardwert ist „result/%Y/%M/%D/“, d. h. der Ergebnisordner im überwachten Ordner. Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](configuring-watched-folder-endpoints.md#about-file-patterns).

>[!NOTE]
>
>Je kleiner die Größe des Ergebnisordners, desto höher die Watched Folder-Leistung. Wenn beispielsweise die geschätzte Belastung für den überwachten Ordner bei 1000 Dateien pro Stunde liegt, sollten Sie ein Muster wie `result/%Y%M%D%H` verwenden, sodass jede Stunde ein neuer Unterordner erstellt wird. Wenn die Belastung geringer ist (z. B. 1000 Dateien pro Tag), können Sie ein Muster wie das folgende verwenden: `result/%Y%M%D`.

**Aufbewahrungsordner**: Der Ort, an dem Dateien nach erfolgreichem Überprüfen und Aufnehmen gespeichert werden. Der Pfad kann absolut, relativ oder ein Nullverzeichnispfad sein. Sie können Dateimuster wie für den Ergebnisordner beschrieben verwenden.  Der Standardwert ist „preserve/%Y/%M/%D/“.

**Fehlerordner**: Der Ordner, in dem Dateien mit Fehlern gespeichert werden. Dieser Speicherort ist stets relativ zum überwachten Ordner. Sie können Dateimuster verwenden, wie für den Ergebnisordner beschrieben.

Schreibgeschützte Dateien werden nicht verarbeitet und im Fehlerordner gespeichert.

Der Standardwert ist „failure/%Y/%M/%D/“.

**Bei Fehler beibehalten**: Eingabedateien werden beibehalten, wenn der Vorgang für einen Dienst nicht ausgeführt werden kann. Der Standardwert lautet true.

**Doppelte Dateinamen überschreiben**: Wenn diese Option auf „True“ gesetzt ist, werden Dateien im Ergebnisordner und im Aufbewahrungsordner überschrieben. Bei Festlegung auf „False“ wird an die Namen von Dateien und Ordnern ein numerisches Indexsuffix angehängt. Der Standardwert ist „False“.

**Bereinigungszeit** (obligatorisch): Dateien und Ordner im Ergebnisordner werden bereinigt, wenn sie älter als dieser Wert sind. Dieser Wert wird in Tagen gemessen. Diese Einstellung trägt dazu bei, dass der Ergebnisordner nicht voll wird.

Ein Wert von „-1“ Tagen bedeutet, dass der Ergebnisordner nie gelöscht wird. Der Standardwert ist -1.

**Vorgangsname** (obligatorisch): Eine Liste von Vorgängen, die dem Endpunkt des überwachten Ordners zugewiesen werden können.

**Zuordnungen von Eingabeparametern**: Dient zur Konfiguration der Eingaben, die zur Verarbeitung des Services und Vorgangs erforderlich sind. Die verfügbaren Einstellungen hängen davon ab, welcher Dienst den Endpunkt „Überwachter Ordner“ verwendet. Es gibt zwei Eingabetypen:

**Literal**: Der überwachte Ordner verwendet den in das Feld eingegebenen Wert so, wie er angezeigt wird. Alle grundlegenden Java-Typen werden unterstützt. Wenn eine API beispielsweise Eingaben wie String, Long, Int oder Boolean verwendet, wird die Zeichenfolge in einen ordnungsgemäßen Typ konvertiert und der Dienst aufgerufen.

**Variable**: Der eingegebene Wert ist ein Dateimuster, das vom überwachten Ordner zum Auswählen der Eingabe verwendet wird. Beispielsweise können Benutzende beim Kennwortverschlüsselungsdienst, bei dem das Eingabedokument eine PDF-Datei sein muss, „*.pdf“ als Dateimuster verwenden. Der überwachte Ordner nimmt alle Dateien im überwachten Ordner auf, die diesem Muster entsprechen, und ruft für jede Datei den Dienst auf. Wenn eine Variable verwendet wird, werden alle Eingabedateien in Dokumente konvertiert. Nur APIs, die „Document“ als Eingabetyp verwenden, werden unterstützt. 

**Zuordnungen von Ausgabeparametern**: Dient zur Konfiguration der Ausgaben des Dienstes und des Vorgangs. Die verfügbaren Einstellungen hängen davon ab, welcher Dienst den Endpunkt „Überwachter Ordner“ verwendet.

Die Ausgabe des überwachten Ordners kann ein einzelnes Dokument, eine Liste von Dokumenten oder eine Zuordnung von Dokumenten sein. Diese Ausgabedokumente werden anschließend mithilfe des in der Ausgabeparameterzuordnung angegebenen Musters im Ergebnisordner gespeichert.

>[!NOTE]
>
>Das Angeben von Namen, die zu eindeutigen Ausgabedateinamen führen, verbessert die Leistung. Nehmen wir zum Beispiel den Fall, dass der Service ein Ausgabedokument zurückgibt und die Ausgabeparameter-Zuordnung es `%F.%E` (dem Dateinamen und der Erweiterung der Eingabedatei) zuordnet. In diesem Fall, wenn der Benutzer jede Minute Dateien mit demselben Namen ablegt und der Ergebnisordner auf `result/%Y/%M/%D` konfiguriert ist und die Einstellung „Doppelt vorhandene Dateinamen überschreiben“ deaktiviert ist, versucht der Watched Folder-Dienst die doppelten Dateinamen aufzulösen. Der Prozess des Auflösens von doppelten Dateinamen kann Auswirkungen auf die Leistung haben. In diesem Fall kann die Leistung verbessert werden, wenn die Ausgabeparameter-Zuordnung auf `%F_%h_%m_%s_%l` geändert wird, um dem Namen Stunden, Minuten, Sekunden und Millisekunden hinzuzufügen, oder wenn sichergestellt wird, dass abgelegte Dateien eindeutige Namen haben. 

## Informationen zu Dateimustern {#about-file-patterns}

Admins können den Dateityp angeben, von dem ein Dienst aufgerufen werden kann. Für jeden überwachten Ordner können mehrere Dateimuster angegeben werden. Ein Dateimuster kann eine der folgenden Dateieigenschaften sein:

* Dateien mit bestimmten Dateinamenerweiterungen, z. B. &amp;ast;.dat, &amp;ast;.xml, &amp;ast;.pdf
* Dateien mit bestimmten Namen, z. B. data.*
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

Wenn das Muster der Zuordnung von Ausgabeparametern mit „File.separator“ (dem Pfadtrennzeichen) endet, wird ein Ordner erstellt und der Inhalt in diesen Ordner kopiert. Endet das Muster nicht mit „File.separator“, wird der Inhalt (Ergebnisdatei oder -ordner) mit diesem Namen erstellt. Weitere Informationen zu Zuordnungen von Ausgabeparametern finden Sie unter [Tipps und Tricks für überwachte Ordner](configuring-watched-folder-endpoints.md#tips-and-tricks-for-watched-folders).

## Über die Drosselung {#about-throttling}

Wenn die Drosselung für einen Endpunkt des Typs „überwachter Ordner“ aktiviert ist, wird die Anzahl an Aufträgen für überwachte Ordner, die zu jeder Zeit verarbeitet werden können, begrenzt.  Die maximale Anzahl von Aufträgen wird durch den Wert für die Batch-Größe bestimmt, der auch im Endpunkt des überwachten Ordners konfigurierbar ist. In das Eingabeverzeichnis des überwachten Ordners eingehende Dokumente werden nicht mehr abgerufen, wenn der Grenzwert für die Drosselung erreicht wurde.  Die Dokumente bleiben ebenfalls im Eingabeverzeichnis, bis andere Aufträge für überwachte Ordner abgeschlossen wurden und ein erneuter Abrufversuch unternommen wird.  Im Falle der synchronen Verarbeitung werden alle in einem einzigen Abruf verarbeiteten Aufträge für die Berechnung des Grenzwertes für die Drosselung berücksichtigt, auch wenn die Aufträge nacheinander in einem einzigen Thread verarbeitet werden.

>[!NOTE]
>
>Die Drosselung wird bei einem Cluster nicht skaliert. Wenn die Drosselung aktiviert ist, verarbeitet der Cluster insgesamt zu keinem Zeitpunkt mehr als die Anzahl der Aufträge, die in der Batch-Größe angegeben sind. Diese Beschränkung ist Cluster-weit und nicht für jeden Knoten im Cluster spezifisch. Bei einer Batch-Größe von 2 könnte beispielsweise das Einschränkungslimit mit einem einzigen Knoten erreicht werden, der zwei Aufträge verarbeitet, und keine anderen Knoten würden den Eingabeordner abrufen, bis einer der Aufträge abgeschlossen ist.

### Wie die Drosselung funktioniert {#how-throttling-works}

Der Watched Folder-Dienst überprüft den Eingabeordner zum jeweiligen Wiederholungsintervall, nimmt die unter „Batch-Größe“ angegebene Anzahl von Dateien auf und ruft den Zieldienst für jede dieser Dateien auf. Wenn die Batch-Größe beispielsweise 4 beträgt, nimmt der Watched Folder-Dienst bei jeder Überprüfung vier Dateien auf, erstellt vier Aufrufanfragen und ruft den Zieldienst auf. Wenn der Dienst „Überwachter Ordner“ vor Abschluss dieser Anfragen erneut aufgerufen wird, werden unabhängig davon, ob die vorherigen vier Aufträge abgeschlossen sind, erneut vier Aufträge gestartet.

Die Drosselung verhindert, dass der Watched Folder-Dienst neue Aufträge aufruft, wenn die vorherigen Aufträge noch nicht abgeschlossen sind. Der Watched Folder-Dienst erkennt die in Bearbeitung befindlichen Aufträge und verarbeitet neue Aufträge auf Grundlage der Batch-Größe abzüglich der in Bearbeitung befindlichen Aufträge.  Wenn im zweiten Aufruf beispielsweise nur drei Aufträge abgeschlossen sind und ein Auftrag noch ausgeführt wird, ruft der Dienst für überwachte Ordner nur drei weitere Aufträge auf.

* Der Dienst für überwachte Ordner verlässt sich bei der Ermittlung der Anzahl der laufenden Aufträge auf die Anzahl der im Bereitstellungsordner vorhandenen Dateien. Verbleiben Dateien unverarbeitet im Bereitstellungsordner, werden keine weiteren Aufträge vom Dienst „Überwachter Ordner“ aufgerufen. Wenn die Batch-Größe beispielsweise 4 beträgt und drei Aufträge angehalten sind, ruft der Watched Folder-Dienst bei Folgeaufrufen nur einen weiteren Auftrag auf. Es gibt mehrere Szenarien, in denen Dateien im Bereitstellungsordner unverarbeitet bleiben können. Wenn Aufträge angehalten sind, können die dazugehörigen Prozesse von Admins auf der Seite zur Verwaltung des Arbeitsablaufs für Formulare beendet werden, sodass diese Dateien vom Watched Folder-Dienst aus dem Bereitstellungsordner verschoben werden.
* Wenn der Formular-Server heruntergefahren wird, bevor der Watched Folder-Dienst die Aufträge aufrufen kann, können die Admins die Dateien aus dem Bereitstellungsordner verschieben.  Weitere Informationen finden Sie unter [Fehlerquellen und Wiederherstellung](configuring-watched-folder-endpoints.md#failure-points-and-recovery).
* Wenn zwar der Formular-Server, nicht aber der Watched Folder-Dienst ausgeführt wird, während der Job Manager-Dienst zurückruft (wozu es kommt, wenn Dienste nicht in der richtigen Reihenfolge starten), dann können die Admins die Dateien aus dem Bereitstellungsordner verschieben. Weitere Informationen finden Sie unter [Fehlerquellen und Wiederherstellung](configuring-watched-folder-endpoints.md#failure-points-and-recovery).


## Leistung und Skalierbarkeit {#performance-and-scalability}

Der Watched Folder-Dienst kann insgesamt 100 Ordner auf einem einzelnen Knoten verarbeiten.  Die Leistung des Watched Folder-Dienstes ist von der Leistung des Formular-Servers abhängig. Bei asynchronem Aufruf ist die Leistung stärker von der Systemauslastung sowie von den Aufträgen abhängig, die sich in der Auftrags-Manager-Warteschlange befinden.

Die Leistung des Watched Folder-Dienstes kann durch das Hinzufügen von Knoten zum Cluster verbessert werden.  Watched Folder-Aufträge werden durch den Quartz Scheduler auf den Cluster-Knoten bzw. im Falle asynchroner Anforderungen vom Job Manager-Dienst verteilt. Alle Aufträge sind persistent in der Datenbank gespeichert.

Der Watched Folder-Dienst ist bei der Zeitplanung, Aufhebung von Zeitplanungen und der erneuten Zeitplanung der Aufträge vom Scheduler-Dienst abhängig. Es stehen noch andere Dienste zur Verfügung, wie z. B. Event Management-Dienst, User Manager-Dienst oder Email Provider-Dienst, die den Threadpool des Scheduler-Dienstes gemeinsam nutzen. Dies kann sich auf die Leistung des Watched Folder-Dienstes auswirken. Wenn alle Dienste beginnen, den Threadpool des Scheduler-Dienstes zu verwenden, wird eine Leistungsoptimierung erforderlich.

## Überwachte Ordner in einem Cluster {#watched-folders-in-a-cluster}

In einem Cluster ist der Watched Folder-Dienst beim Lastenausgleich und Failover vom Quartz Scheduler und vom Job Manager-Dienst abhängig. Weitere Informationen zum Quartz-Cluster-Verhalten finden Sie in der [Quartz-Dokumentation.](https://www.quartz-scheduler.org/documentation)

Der Watched Folder-Dienst führt bei jedem Abruf die folgenden drei Hauptaufgaben aus:

* Überprüfen des Ordners
* Aufrufen des Zieldienstes
* Verarbeiten der Ergebnisse

Das Lastenausgleich- und Failover-Verhalten ändert sich in Abhängigkeit davon, ob der überwachte Ordner für synchrone oder asynchrone Aufrufe konfiguriert ist.

### Synchroner überwachter Ordner in einem Cluster {#synchronous-watched-folder-in-a-cluster}

Bei synchronen Aufrufen entscheidet der Quartz-Lastenausgleich, welchem Knoten das Abrufereignis zugeteilt wird.  Der Knoten, dem das Abrufereignis zugeteilt wird, führt alle Aufgaben aus: Überprüfen des Ordners, Aufrufen des Zieldienstes und Verarbeiten der Ergebnisse.

![en_synchwatchedfoldercluster](assets/en_synchwatchedfoldercluster.png)

Wenn bei einem synchronen Aufruf ein Fehler bei einem Knoten auftritt, sendet der Quartz Scheduler neue Abrufereignisse an andere Knoten.  Die auf dem fehlerhaften Knoten gestarteten Aufrufe gehen verloren.  Weitere Informationen zum Wiederherstellen der dem fehlerhaften Auftrag zugeordneten Dateien finden Sie unter [Fehlerquellen und Wiederherstellung](configuring-watched-folder-endpoints.md#failure-points-and-recovery).


### Asynchroner überwachter Ordner in einem Cluster {#asynchronous-watched-folder-in-a-cluster}

Bei asynchronen Aufrufen entscheidet der Quartz-Lastenausgleich, welchem Knoten das Abrufereignis zugeteilt wird.  Der Knoten, dem das Abrufereignis zugeteilt wird, überprüft den Eingabeordner und ruft den Zieldienst auf, indem die Anforderung in die Warteschlange des Job Manager-Dienstes gestellt wird.  Der Lastenausgleich des Job Manager-Dienstes ist dagegen für die Entscheidung verantwortlich, von welchem Knoten die Aufrufanforderung verarbeitet wird.  Es ist möglich, dass eine Anforderung auf Knoten B verarbeitet wird, auch wenn die Aufrufanforderung von Knoten A erstellt wurde.  Natürlich kann es auch vorkommen, dass derselbe Knoten, von dem die Aufrufanforderung gestartet wurde, am Ende auch die Verarbeitung der Anforderung übernimmt.

![en_asynchwatchedfoldercluster](assets/en_asynchwatchedfoldercluster.png)

Wenn bei einem asynchronen Aufruf ein Fehler bei einem Knoten auftritt, sendet der Quartz Scheduler neue Abrufereignisse an andere Knoten.  Aufrufanfragen, die auf dem fehlerhaften Knoten erstellt wurden, befinden sich in der Warteschlange des Job Manager-Dienstes und werden zur Verarbeitung an andere Knoten gesendet.  Dateien, für die keine Aufrufanfragen erstellt wurden, bleiben im Bereitstellungsordner.  Weitere Informationen zum Wiederherstellen der dem fehlerhaften Auftrag zugeordneten Dateien finden Sie unter [Fehlerquellen und Wiederherstellung](configuring-watched-folder-endpoints.md#failure-points-and-recovery).


## Fehlerquellen und Wiederherstellung {#failure-points-and-recovery}

Bei jedem Abrufereignis sperrt der Dienst für überwachte Ordner den Eingabeordner, verschiebt die Dateien, die dem Muster für einzuschließende Dateien entsprechen, in den Bereitstellungsordner und entsperrt dann den Eingabeordner. Das Sperren ist erforderlich, damit zwei Threads nicht denselben Dateisatz abrufen und ihn zweimal verarbeiten. Die Wahrscheinlichkeit, dass es hierzu kommt, steigt mit einem kurzen Wiederholungsintervall und einer hohen Batch-Größe.  Nachdem die Dateien in den Bereitstellungsordner verschoben wurden, wird der Eingabeordner entsperrt, damit andere Threads den Ordner scannen können. Dieser Schritt bietet einen hohen Durchsatz, da andere Threads scannen können, während ein Thread die Dateien verarbeitet.

Nachdem die Dateien in den Bereitstellungsordner verschoben wurden, werden Aufrufanfragen für jede Datei erstellt, und der Zieldienst wird aufgerufen. Es kann vorkommen, dass der Dienst für überwachte Ordner die Dateien im Bereitstellungsordner nicht wiederherstellen kann:

* Wenn der Server heruntergefahren wird, bevor der Dienst für überwachte Ordner die Aufrufanfrage erstellen kann, bleiben die Dateien im Bereitstellungsordner und werden nicht wiederhergestellt.
* Wenn der Dienst für überwachte Ordner die Aufrufanfrage für jede der Dateien im Bereitstellungsordner erfolgreich erstellt hat und der Server abstürzt, gibt es je nach Aufruftyp zwei Verhaltensweisen:

**Synchron**: Wenn der Watched Folder-Dienst so konfiguriert ist, dass der Dienst synchron aufgerufen wird, bleiben alle Dateien des Bereitstellungsordners unverarbeitet im Bereitstellungsordner.

**Asynchron:** In diesem Fall ist der Watched Folder-Dienst vom Job Manager-Dienst abhängig. Wenn der Job Manager-Dienst den Dienst für überwachte Ordner zurückruft, werden die Dateien im Bereitstellungsordner basierend auf den Ergebnissen des Aufrufs in den Aufbewahrungs- oder Fehlerordner verschoben. Wenn der Job Manager-Dienst den Dienst für überwachte Ordner nicht zurückruft, bleiben die Dateien unverarbeitet im Bereitstellungsordner. Diese Situation tritt auf, falls der Dienst für überwachte Ordner nicht ausgeführt wird, wenn der Job Manager zurückruft.

### Wiederherstellen von nicht verarbeiteten Quelldateien im Bereitstellungsordner {#recovering-unprocessed-source-files-in-the-stage-folder}

Wenn der Dienst für überwachte Ordner die Quelldateien im Bereitstellungsordner nicht verarbeiten kann, können Sie die nicht verarbeiteten Dateien wiederherstellen.

1. Starten Sie den Anwendungs-Server oder Knoten neu.
1. (Optional) Beenden Sie den Watched Folder-Dienst, sodass keine neuen Eingabedateien verarbeitet werden. Wenn Sie diesen Schritt überspringen, ist es viel schwieriger zu bestimmen, welche Dateien im Bereitstellungsordner nicht verarbeitet wurden. Führen Sie eine der folgenden Aufgaben aus, um zu verhindern, dass der Dienst für überwachte Ordner neue Eingabedateien verarbeitet:

   * Ändern Sie in „Anwendungen und Dienste“ den Parameter „Muster für einzuschließende Dateien“ für den überwachten Ordner-Endpunkt in ein Muster, das keiner der neuen Eingabedateien entspricht (geben Sie beispielsweise `NOMATCH` ein).
   * Setzen Sie den Prozess aus, der neue Eingabedateien erstellt.

   Warten Sie, bis AEM Forms alle Dateien wiederherstellt und verarbeitet. Die meisten Dateien sollten wiederhergestellt und alle neuen Eingabedateien korrekt verarbeitet werden. Die Wartezeit bis zum Wiederherstellen und Verarbeiten der Dateien durch den überwachten Ordner hängt von der Dauer des aufzurufenden Vorgangs und der Anzahl der wiederherzustellenden Dateien ab.

1. Bestimmen Sie, welche Dateien nicht verarbeitet werden können. Wenn Sie eine angemessene Zeitdauer abgewartet und den vorherigen Schritt abgeschlossen haben, sich aber immer noch nicht verarbeitete Dateien im Bereitstellungsordner befinden, fahren Sie mit dem nächsten Schritt fort.

   >[!NOTE]
   >
   >Sie können den Datums- und Zeitstempel der Dateien im Bereitstellungsverzeichnis anzeigen. Je nach Anzahl der Dateien und der normalen Verarbeitungsdauer können Sie ermitteln, welche Dateien so alt sind, dass sie als blockiert betrachtet werden können.

1. Kopieren Sie die nicht verarbeiteten Dateien aus dem Bereitstellungsordner in den Eingabeordner.
1. Wenn der Dienst für überwachte Ordner in Schritt 2 an der Verarbeitung neuer Eingabedateien gehindert wurde, ändern Sie den Parameter „Muster für einzuschließende Dateien“ in den vorherigen Wert zurück oder aktivieren Sie den zuvor deaktivierten Prozess erneut.

## Hinweise zur Sicherheit von überwachten Ordnern {#security-considerations-for-watched-folders}

Jeder überwachte Ordner ist mit einem Benutzernamen und einem Kennwort konfiguriert. Diese Anmeldeinformationen werden beim Aufrufen der Dienste verwendet. Der Watched Folder-Dienst basiert auf der Tatsache, dass der freigegebene Ordner durch das zugrunde liegende Sicherheitsdateisystem geschützt ist, sodass nur die Person auf den freigegebenen Ordner zugreifen kann, die für den überwachten Ordner verantwortlich ist.

## Tipps und Tricks für überwachte Ordner {#tips-and-tricks-for-watched-folders}

Im Folgenden finden Sie einige Tipps und Tricks zum Konfigurieren des Endpunkts vom Typ „Überwachter Ordner“:

* Bei einem überwachten Ordner unter Windows, der Bilddateien verarbeitet, geben Sie Werte für die Optionen „Muster für einzuschließende Dateien“ bzw. „Muster für auszuschließende Dateien“ an, um zu verhindern, dass die automatisch von Windows erzeugte Datei „Thumbs.db“ vom überwachten Ordner abgerufen wird.
* Wenn ein Cron-Ausdruck angegeben ist, wird das Wiederholungsintervall ignoriert. Die Verwendung des Cron-Ausdrucks basiert auf dem Open-Source-Vorgangsplanungssystem Quartz, Version 1.4.0.
* Die Stapelgröße ist die Anzahl der Dateien und Ordner, die bei jeder Überprüfung des überwachten Ordners aufgenommen wird. Wenn die Stapelgröße auf „2“ festgelegt ist und zehn Dateien oder Ordner im überwachten Ordner abgelegt werden, werden bei jeder Überprüfung nur zwei aufgenommen. Bei der nächsten Überprüfung, die nach dem als Wiederholungsintervall angegebenen Zeitraum eintritt, werden die nächsten zwei Dateien aufgenommen.
* Admins können reguläre Ausdrücke mit der zusätzlichen Unterstützung durch Platzhaltermuster als Dateimuster angeben. Bei der Überwachung von Ordnern wird der reguläre Ausdruck geändert, um Platzhaltermuster wie „*.*“ und „*.pdf“ zu unterstützen. Diese Platzhaltermuster werden nicht von regulären Ausdrücken unterstützt.
* Der Watched Folder-Dienst überprüft den Eingabeordner auf Eingaben und erkennt nicht, ob die Quelldatei bzw. der Quellordner bereits vollständig in den Eingabeordner kopiert wurde, bevor mit der Verarbeitung der Datei oder des Ordners begonnen wird. Führen Sie die folgenden Schritte aus, um sicherzustellen, dass die Quelldatei bzw. der Quellordner vollständig in den Eingabeordner des überwachten Ordners kopiert wurde, bevor die Datei oder der Ordner aufgenommen wird:

   * Verwenden Sie „Wartezeit“. Dabei handelt es sich um den Zeitraum in Millisekunden, den der Watched Folder-Dienst ab dem Zeitpunkt der letzten Änderung wartet. Verwenden Sie diese Funktion, wenn Sie große Dateien verarbeiten müssen. Wenn das Herunterladen einer Datei beispielsweise 10 Minuten dauert, geben Sie die Wartezeit als 10 x 60 x 1000 Millisekunden an. Dies verhindert, dass der Dienst für überwachte Ordner die Datei aufnimmt, wenn sie nicht bereits 10 Minuten alt ist.
   * Verwenden Sie „Muster für auszuschließende Dateien“ und „Muster für einzuschließende Dateien“. Wenn zum Beispiel das Muster für auszuschließende Dateien `ex*` und das Muster für einzuschließende Dateien `in*` lautet, werden bei überwachten Ordnern die Dateien erfasst, die mit „in“ beginnen, aber nicht die, die mit „ex“ beginnen. Benennen Sie zum Kopieren großer Dateien oder Ordner zuerst die Datei bzw. den Ordner so um, dass der Name mit „ex“ beginnt. Benennen Sie die Datei bzw. den Ordner mit dem mit „ex“ beginnenden Namen nach vollständigem Abschluss des Kopiervorgangs in den überwachten Ordner wieder in „in*“ um.

* Verwenden Sie „Bereinigungszeit“, um den Ergebnisordner „sauber“ zu halten. Der Watched Folder-Dienst bereinigt alle Dateien, die älter als die unter „Bereinigungszeit“ angegebene Dauer sind. Diese Dauer wird in Tagen angegeben.
* Wenn ein Endpunkt vom Typ „Überwachter Ordner“ hinzugefügt wird, wird nach der Auswahl des Vorgangsnamens die Zuordnung der Eingabeparameter ausgefüllt. Für jede Eingabe des Vorgangs wird ein Feld für die Zuordnung von Eingabeparametern generiert. Im Folgenden finden Sie Beispiele für Zuordnungen von Eingabeparametern:

   * Für die Eingabe `com.adobe.idp.Document` gilt: Wenn der Eingabetyp des Dienstvorgangs `Document` ist, kann der Administrator den Zuordnungstyp als `Variable` angeben. Der Watched Folder-Dienst nimmt die Eingabe aus dem Eingabeordner des überwachten Ordners auf. Grundlage hierfür ist das im Eingabeparameter angegebene Dateimuster. Wenn der Administrator `*.pdf` als Parameter angibt, wird jede Datei mit der Erweiterung „.pdf“ aufgenommen, in `com.adobe.idp.Document` konvertiert und der Service aufgerufen.
   * Für die Eingabe in `java.util.Map`: Wenn der Service-Vorgang eine Eingabe vom Typ `Map` hat, kann der Administrator den Zuordnungstyp als `Variable` angeben und einen Zuordnungswert mit einem Muster wie `*.pdf` eingeben. Angenommen ein Dienst benötigt eine Zuordnung von zwei `com.adobe.idp.Document`-Objekten, die zwei Dateien im Eingabeordner repräsentieren, z. B „1.pdf“ und „2.pdf“. Der Watched Folder-Dienst erstellt eine Zuordnung mit dem Dateinamen als Schlüssel und dem Wert `com.adobe.idp.Document`.
   * Für die Eingabe in `java.util.List`: Wenn der Service-Vorgang eine Eingabe vom Typ „Liste“ hat, kann der Administrator den Zuordnungstyp als `Variable` angeben und einen Zuordnungswert mit einem Muster wie `*.pdf` eingeben. Wenn PDF-Dateien im Eingabeordner abgelegt werden, erstellt der Watched Folder-Dienst eine Liste der `com.adobe.idp.Document`-Objekte, die diese Dateien repräsentiert, und ruft den Zieldienst auf.
   * Für `java.lang.String` gilt: Der Administrator hat zwei Möglichkeiten. Zunächst kann der Administrator den Zuordnungstyp als `Literal` angeben und einen Zuordnungswert als Zeichenfolge eingeben, z. B. `hello.`. Der überwachte Ordner ruft den Service mit der Zeichenfolge `hello` auf. Zweitens kann der Administrator den Zuordnungstyp als `Variable` angeben und einen Zuordnungswert mit einem Muster wie `*.txt` eingeben. Im zweiten Fall werden Dateien mit der TXT-Endung als Dokument gelesen, das zwangsweise in eine Zeichenfolge umgewandelt ist, um den Dienst aufzurufen.
   * Der Administrator kann den Zuordnungstyp als `Literal` angeben und den Wert vorgeben. Der Watched Folder-Dienst ruft den Dienst mit dem angegebenen Wert auf.

* Der Watched Folder-Dienst ist für die Arbeit mit Dokumenten vorgesehen. Die unterstützten Ausgaben sind `com.adobe.idp.Document`, `org.w3c.Document`, `org.w3c.Node` sowie eine Liste und Zuordnung dieser Typen. Jeder andere Typ führt zu einer Fehlerausgabe im Fehlerordner.
* Wenn die Ergebnisse nicht im Ergebnisordner vorhanden sind, überprüfen Sie den Fehlerordner, um herauszufinden, ob ein Fehler aufgetreten ist.
* Der Dienst für überwachte Ordner funktioniert optimal im asynchronen Modus. In diesem Modus stellt der Watched Folder-Dienst die Aufrufanfrage in die Warteschlange und ruft zurück. Die Warteschlange wird dann asynchron verarbeitet. Wenn die Option „Asynchron“ nicht festgelegt ist, ruft der Watched Folder-Dienst den Zieldienst synchron auf und die Prozess-Engine wartet, bis der Dienst die Anfrage abgeschlossen und Ergebnisse erzeugt hat. Wenn der Zieldienst lange für die Verarbeitung der Anfrage braucht, kann es beim Watched Folder-Dienst zu Zeitüberschreitungsfehlern kommen.
* Beim Erstellen von überwachten Ordnern für Import- und Exportvorgänge ist eine Abstraktion von Dateinamenerweiterungen nicht zulässig. Wenn der Form Data Integration-Dienst bei Verwendung von überwachten Ordnern aufgerufen wird, passt der Ty der Dateinamenerweiterung für die Ausgabedatei möglicherweise nicht zum beabsichtigten Ausgabeformat für den Dokumentobjekttyp. Wenn beispielsweise die Eingabedatei für einen überwachten Ordner, von dem der Exportvorgang aufgerufen wird, ein XFA-Formular mit Daten ist, muss die Ausgabedatei eine XDP-Datendatei sein. Um eine Ausgabedatei mit der richtigen Dateinamenerweiterung zu erhalten, können Sie diese in den „Zuordnungen von Ausgabeparametern“ angeben. In diesem Beispiel können Sie „%F.xdp“ für die Ausgabeparameterzuordnung verwenden.
* Eingabedateien werden von einem überwachten Ordner möglicherweise verarbeitet, bevor sie vollständig in den Ordner kopiert wurden. Unter UNIX ist das Sperren von Dateien nicht wie unter Windows obligatorisch. Aus diesem Grund kann eine Datei, die in einen überwachten Ordner kopiert wird, von diesem überwachten Ordner in den Bereitstellungsordner verschoben werden, ohne den Abschluss des Kopiervorgangs abzuwarten. Bei diesem Verhalten wird nur ein Teil der Eingabedatei verarbeitet. Zurzeit gibt es zwei vorläufige Lösungen:

   * Vorläufige Lösung 1

      1. Geben Sie ein Muster für „Muster für auszuschließende Dateien“ an, beispielsweise „temp*.ps“.
      1. Kopieren Sie Dateien, deren Namen mit „temp“ beginnen (z. B. „temp1.ps“), in den überwachten Ordner.
      1. Nachdem die Datei vollständig in den überwachten Ordner kopiert wurde, benennen Sie die Datei so um, dass der Name dem für „Muster für einzuschließende Dateien“ angegebenen Muster entspricht. Die vollständige Datei wird dann vom überwachten Ordner in den Bereitstellungsordner verschoben.

   * Vorläufige Lösung 2

     Wenn die maximale Dauer für den Kopiervorgang der Dateien in einen überwachten Ordner bekannt ist, geben Sie diesen Zeitraum in Sekunden unter „Wartezeit“ an. Der überwachte Ordner lässt dann immer zuerst den angegebenen Zeitraum verstreichen, bevor die Datei in den Bereitstellungsordner verschoben wird.

     Dieses Problem tritt bei Dateien unter Windows nicht auf, weil unter Windows eine Datei während eines Schreibvorgangs durch einen Thread gesperrt wird. Es ist aber ein Problem für Ordner unter Windows. Für Ordner müssen Sie die unter „Problemumgehung 1“ aufgeführten Schritte befolgen.

* Wenn das Endpunktattribut „Preserve Folder Name“ (Ordnernamen bewahren) für den Watched Folder-Dienst auf einen leeren Ordnerpfad (null) festgelegt ist, wird das Testverzeichnis nicht wie erforderlich geleert. Der Ordner enthält dann immer noch die verarbeitete Datei sowie den temporären Ordner.

## Dienstspezifische Empfehlungen für überwachte Ordner {#service-specific-recommendations-for-watched-folders}

Für alle Dienste müssen die Stapelgröße und das Wiederholungsintervall des überwachten Ordners so angepasst werden, dass die Häufigkeit, mit der neue Dateien und Ordner vom Watched Folder-Dienst zur Verarbeitung aufgenommen werden, nicht die Rate der Aufträge übersteigt, die vom AEM-Formular-Server verarbeitet werden können. Die tatsächlich zu verwendenden Parameter können abweichen. Dies hängt davon ab, wie viele überwachte Ordner konfiguriert sind, welche Dienste überwachte Ordner verwenden und wie intensiv die Aufträge den Prozessor auslasten.

### Empfehlungen für den Generate PDF-Dienst {#generate-pdf-service-recommendations}

* Der Generate PDF-Dienst kann von folgenden Dateitypen jeweils nur eine Datei gleichzeitig konvertieren: Microsoft Word, Microsoft Excel, Microsoft PowerPoint, Microsoft Project, AutoCAD, Adobe Photoshop®, Adobe FrameMaker® und Adobe PageMaker®. Diese Aufträge auszuführen, dauert lange. Stellen Sie daher sicher, dass die Stapelgröße niedrig eingestellt ist. Erhöhen Sie außerdem das Wiederholungsintervall, wenn weitere Knoten im Cluster vorhanden sind.
* Für PostScript (PS), Encapsulated PostScript (EPS) und Bilddateitypen kann der Generate PDF-Dienst mehrere Dateien parallel verarbeiten. Optimieren Sie sorgfältig die Bean-Pool-Größe der Sitzung (von der die Anzahl der parallel ausgeführten Konvertierungen gesteuert wird) in Abhängigkeit von der Kapazität Ihres Servers sowie der Anzahl der im Cluster vorhandenen Knoten. Erhöhen Sie dann die Stapelgröße auf einen Wert, der der Bean-Pool-Größe der Sitzung für die Dateitypen entspricht, die konvertiert werden sollen. Die Abrufhäufigkeit sollte von der Anzahl der Knoten im Cluster bestimmt werden. Da diese Arten von Aufträgen vom Generate PDF-Dienst jedoch recht schnell verarbeitet werden, kann das Wiederholungsintervall mit einem niedrigen Wert wie 5 oder 10 konfiguriert werden.
* Auch wenn der Generate PDF-Dienst jeweils nur eine OpenOffice-Datei verarbeiten kann, wird die Konvertierung relativ schnell durchgeführt. Die oben erläuterte Logik für PS-, EPS- und Bildkonvertierungen gilt ebenfalls für OpenOffice-Konvertierungen.
* Halten Sie für eine gleichmäßige Lastverteilung im Cluster die Stapelgröße niedrig und erhöhen Sie das Wiederholungsintervall.

### Empfehlungen für den Dienst „Barcode-Formulare“ {#barcoded-forms-service-recommendations}

* Geben Sie zur Erzielung einer optimalen Leistung bei der Verarbeitung von Formularen mit Strichcode (kleine Dateien) als Stapelgröße `10` und als Wiederholungsintervall `2` ein.
* Befinden sich viele Dateien im Eingabeordner, kann es zu Fehlern mit ausgeblendeten Dateien namens „*thumbs.db*“ kommen. Es wird daher empfohlen, das „Muster für einzuschließende Dateien“ auf denselben Wert festzulegen wie den für die Eingabevariable festgelegten Wert (z. B. `*.tiff`). Auf diese Weise wird der Watched Folder-Dienst daran gehindert, die DB-Dateien zu verarbeiten.
* Eine Stapelgröße von `5` und ein Wiederholungsintervall von `2` sind normalerweise ausreichend, da der Barcoded Forms-Dienst für gewöhnlich ungefähr 0,5 Sekunden für die Verarbeitung eines Strichcodes benötigt.
* Der Watched Folder-Dienst wartet nicht darauf, dass die Prozess-Engine den Auftrag abschließt, bevor neue Dateien oder Ordner aufgenommen werden. Der überwachte Ordner wird weiterhin überprüft und der Zieldienst aufgerufen. Durch dieses Verhalten kann die Prozess-Engine überlastet werden, was zu Ressourcenproblemen und Zeitüberschreitungen führen kann. Stellen Sie sicher, dass Sie mithilfe des Wiederholungsintervalls und der Stapelgröße die Eingabe für den überwachten Ordner einschränken. Sie können das Wiederholungsintervall erhöhen und die Stapelgröße verringern, wenn mehr überwachte Ordner vorhanden sind, oder die Drosselung am Endpunkt aktivieren. Informationen zur Drosselung finden Sie unter [Informationen zur Drosselung](configuring-watched-folder-endpoints.md#about-throttling).
* Der Watched Folder-Service nimmt die Identität des im Benutzer- und Domain-Namen angegebenen Benutzers an. Der Watched Folder-Dienst ruft den Dienst als diese Person auf, wenn er direkt aufgerufen wird oder wenn der Prozess eine kurze Lebensdauer hat. Bei einem langlebigen Prozess wird dieser mit dem Systemkontext aufgerufen. Admins können Betriebssystemrichtlinien für den Watched Folder-Dienst festlegen, um zu bestimmen, wem der Zugriff gewährt oder verweigert werden soll.
* Organisieren Sie die Ergebnis-, Fehler- und Aufbewahrungsordner mithilfe von Dateimustern. (Siehe [Informationen zu Dateimustern](configuring-watched-folder-endpoints.md#about-file-patterns).)

* Der Watched Folder-Dienst verwendet zum Überprüfen der überwachten Ordner den Quartz Scheduler. Der Quartz Scheduler verfügt über einen Threadpool zum Überprüfen der Ordner. Wenn das Wiederholungsintervall für den überwachten Ordner sehr kurz (&lt; 5 Sekunden) und die Stapelgröße hoch ist (> 2), kann eine Wettlaufsituation auftreten. In diesem Fall wird eine Datei von zwei Quartz-Threads aufgenommen:

   * Einer der Threads findet die Datei erfolgreich und ruft den Zieldienst mit der Datei auf.
   * Der zweite Thread sieht zwar die Datei, schlägt aber bei der Überprüfung der Gültigkeit der Datei fehl (Lesen oder Schreiben der Datei), wodurch falsch positive Fehler erzeugt werden, die anzeigen, dass der Dateiinhalt nicht verarbeitet werden kann, weil die Datei schreibgeschützt ist. Hierzu kommt es nur, wenn das Wiederholungsintervall kurz und die Stapelgröße hoch ist.
