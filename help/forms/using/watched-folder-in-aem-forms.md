---
title: Überwachter Ordner in AEM Forms
description: Ein Administrator kann einen Ordner überwachen lassen und einen Workflow-, Dienst- oder Skriptvorgang starten, wenn eine Datei im überwachten Ordner abgelegt wird.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: fbf5c7c3-cb01-4fda-8e5d-11d56792d4bf
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '7146'
ht-degree: 57%

---

# Überwachter Ordner in AEM Forms{#watched-folder-in-aem-forms}

Ein Administrator kann einen Netzwerkordner konfigurieren, der als überwachter Ordner bezeichnet wird, sodass ein vorkonfigurierter Workflow-, Dienst- oder Skriptvorgang zur Verarbeitung der Datei aufgerufen wird, wenn ein Benutzer eine Datei (z. B. eine PDF-Datei) in diesem überwachten Ordner ablegt. Nachdem der Dienst den vorgesehenen Vorgang ausgeführt hat, wird die Ergebnisdatei in einem angegebenen Ausgabeordner gespeichert. Weitere Informationen zu Workflows, Diensten und Skripten finden Sie unter [Verschiedene Methoden zur Verarbeitung von Dateien](#variousmethodsforprocessingfiles).

## Überwachten Ordner erstellen {#create-a-watched-folder}

Sie können eine der folgenden Methoden verwenden, um einen überwachten Ordner im Dateisystem zu erstellen:

* Geben Sie bei der Konfiguration der Eigenschaften für einen Konfigurationsknoten des Typs „Überwachter Ordner“ den vollständigen Pfad zum übergeordneten Ordner in die Eigenschaft „folderPath“ ein und hängen Sie den Namen des zu erstellenden überwachten Ordners an wie in diesem Beispiel: `C:/MyPDFs/MyWatchedFolder`
Der Ordner `MyWatchedFolder` existiert nicht. AEM Forms versucht, den Ordner unter dem angegebenen Pfad zu erstellen.

* Erstellen Sie vor dem Konfigurieren eines Endpunkts des Typs „Überwachter Ordner“ einen Ordner im Dateisystem und geben Sie anschließend den vollständigen Pfad in die Eigenschaft „folderPath“ ein. Detaillierte Informationen zur Eigenschaft &quot;folderPath&quot;finden Sie unter [Eigenschaften für überwachte Ordner](#watchedfolderproperties).

>[!NOTE]
>
>In einer Clusterumgebung muss der Ordner, der als überwachter Ordner verwendet wird, zugriffsbereit sein, Schreibzugriff bieten und im Dateisystem oder Netzwerk freigegeben sein. Jede Anwendungsserverinstanz des Clusters muss Zugriff auf denselben freigegebenen Ordner haben. Erstellen Sie unter Windows auf allen Servern ein zugeordnetes Netzlaufwerk und geben Sie den Pfad des zugeordneten Netzlaufwerks in der Eigenschaft folderPath an.

## Konfigurationsknoten für überwachten Ordner erstellen {#create-watched-folder-configuration-node}

Um einen überwachten Ordner zu konfigurieren, erstellen Sie einen Konfigurationsknoten des Typs „Überwachter Ordner“. Führen Sie die folgenden Schritte aus, um den Konfigurationsknoten zu erstellen: 

1. Melden Sie sich als Administrator bei CRX-DE an und navigieren Sie zum Ordner „/etc/fd/watchfolder/config“. 

1. Erstellen Sie einen Knoten des Typs `nt:unstructured`. Beispiel: watchedfolder

   >[!NOTE]
   >
   >Der Knotenname des überwachten Ordners darf keine Leerzeichen und Sonderzeichen enthalten.

1. Fügen Sie dem Knoten folgende Eigenschaften hinzu:

   * `folderPath`
   * `inputProcessorType`
   * `inputProcessorId`
   * `outputFilePattern`

   Eine vollständige Liste der unterstützten Eigenschaften finden Sie unter [Eigenschaften für überwachte Ordner](#watchedfolderproperties).

1. Klicken Sie auf **Alle speichern**. Der Knoten wird erstellt und die Eigenschaften werden gespeichert. Die Ordner `input`, `result`, `failure`, `preserve` und `stage` werden unter dem in der Eigenschaft `folderPath` angegebenen Pfad erstellt.

   Der Überprüfungsauftrag beginnt mit der regelmäßigen Überprüfung des überwachten Ordners im definierten Zeitintervall.

## Eigenschaften für überwachte Ordner {#watchedfolderproperties}

Sie können die folgenden Eigenschaften für einen überwachten Ordner konfigurieren.

* **folderPath (Zeichenfolge)**: Der Pfad des Ordners, der regelmäßig mit dem angegebenen Zeitintervall überprüft werden soll. In einer Clusterumgebung muss sich der Ordner an einem freigegebenen Speicherort befinden und alle Server müssen uneingeschränkten Zugriff auf diesen Server haben. Dies ist eine obligatorische Eigenschaft.
* **inputProcessorType (Zeichenfolge)**: Der Typ des zu startenden Prozesses. Zur Auswahl stehen Workflow, Skript oder Dienst. Dies ist eine obligatorische Eigenschaft.
* **inputProcessorId (Zeichenfolge)**: Das Verhalten der Eigenschaft „inputProcessorId“ wird durch den für die Eigenschaft „inputProcessorType“ angegebenen Wert gesteuert. Dies ist eine obligatorische Eigenschaft. In der folgenden Liste werden alle möglichen Werte der Eigenschaft &quot;inputProcessorType&quot;und die entsprechenden Anforderungen für die Eigenschaft &quot;inputProcessorType&quot;aufgeführt:

   * Für einen Workflow geben Sie das Workflow-Modell an, das ausgeführt werden soll. Beispiel: /etc/workflow/models/&lt;workflow_name>/jcr:content/model
   * Für ein Skript geben Sie den JCR-Pfad des auszuführenden Skripts an. Beispiel: /etc/fd/watchfolder/test/testScript.ecma
   * Für einen Dienst geben Sie den Filter an, der zum Suchen nach einem OSGi-Dienst verwendet werden soll. Der Dienst ist als Implementierung der com.adobe.aemfd.watchfolder.service.api.ContentProcessor-Schnittstelle registriert.

* **runModes (Zeichenfolge)**: Eine kommagetrennte Liste der zulässigen Ausführungsmodi für die Ausführung des Workflows. Beispiele:

   * author

   * publish

   * Autor,Veröffentlichen

   * publish, author

>[!NOTE]
>
>Ist auf dem Server, der den überwachten Ordner hostet, keiner der angegebenen Ausführungsmodi verfügbar, wird der überwachte Ordner immer aktiviert, egal, welche Ausführmodi auf dem Server laufen.

* **outputFilePattern (Zeichenfolge)**: Das Muster der Ausgabedatei. Sie können ein Ordner- oder Dateimuster angeben. Wenn Sie ein Ordnermuster angeben, erhalten die Ausgabedateien Namen gemäß den Angaben in den Workflows. Wenn Sie ein Dateimuster angeben, erhalten die Ausgabedateien Namen gemäß den Angaben im Dateimuster. [In Datei- und Ordnermustern können Sie außerdem eine Ordnerstruktur für die Ausgabedateien angeben. ](../../forms/using/watched-folder-in-aem-forms.md#p-file-and-folder-patterns-p) Dies ist eine obligatorische Eigenschaft.

* **stageFileExpirationDuration (Long, Standard -1)**: Die Anzahl der Sekunden, die gewartet werden soll, bevor eine Eingabedatei/ein Ordner, die/der bereits zur Verarbeitung abgerufen wurde, als Zeitüberschreitung erkannt und als Fehler gekennzeichnet wurde. Dieser Ablaufmechanismus wird nur aktiviert, wenn der Wert für diese Eigenschaft eine positive Zahl ist.

>[!NOTE]
>
>Selbst wenn eine Eingabe mithilfe dieses Mechanismus als zeitlich begrenzt markiert wird, kann sie möglicherweise immer noch im Hintergrund verarbeitet werden, sie braucht nur mehr Zeit als erwartet. Wenn die Eingabeinhalte verbraucht wurden, bevor der Timeout-Mechanismus eintrat, kann die Verarbeitung sogar zu einem späteren Zeitpunkt abgeschlossen werden und die Ausgabe wird in den Ergebnisordner abgelegt. Wenn die Inhalte nicht vor der Zeitüberschreitung genutzt wurden, ist es sehr wahrscheinlich, dass die Verarbeitung später beim Versuch, die Inhalte zu nutzen, fehlerhaft wird und dieser Fehler auch im Fehlerordner für dieselbe Eingabe protokolliert wird. Wenn die Verarbeitung für die Eingabe dagegen aufgrund eines zeitweisen Auftrags-/Workflow-Fehlers nie aktiviert wurde (dies ist das Szenario, auf das der Ablaufmechanismus abzielt), tritt keiner dieser beiden Fälle auf. Daher sollten Sie bei Einträgen im Fehlerordner, die als Fehler wegen einer Zeitüberschreitung gemeldet wurden (suchen Sie im Fehlerprotokoll nach Meldungen der Art „Datei nach erheblicher Zeit nicht verarbeitet, wird als Fehler markiert!“), den Ergebnisordner (und auch den Fehlerordner selbst auf einen anderen Eintrag für dieselbe Eingabe) prüfen, ob die zuvor beschriebenen Fälle tatsächlich eingetreten sind.

* **deleteExpiredStageFileOnlyWhenThrottled (Boolean, Standard true):** Ob die Zeitüberschreitungsfunktion nur aktiviert werden soll, wenn der überwachte Ordner gedrosselt wird. Der Mechanismus ist für gedrosselte überwachte Ordner relevanter, da eine kleine Anzahl von Dateien, die noch nicht verarbeitet sind (aufgrund zeitweiliger Auftrags-/Workflow-Fehler), die Verarbeitung für den gesamten Batch blockieren kann, wenn die Drosselung aktiviert ist. Wenn diese Eigenschaft als &quot;true&quot;beibehalten wird (Standardeinstellung), wird der Ablaufmechanismus nicht für überwachte Ordner aktiviert, die nicht gedrosselt werden. Wenn die Eigenschaft als „false“ beibehalten wird, tritt die Zeitüberschreitung immer ein, wenn die stageFileExpirationDuration-Eigenschaft eine positive Zahl ist.

* **pollInterval (Lang)**: Das Intervall in Sekunden, in dem der überwachte Ordner auf Eingaben überprüft wird. Außer wenn die Einstellung „Einschränken“ aktiviert ist, muss das Abfrageintervall länger sein als die Verarbeitungsdauer für einen durchschnittlichen Auftrag. Andernfalls kann es zu einer Überlastung des Systems kommen. Der Standardwert ist 5. Weitere Informationen finden Sie in der Beschreibung für die Stapelgröße . Der Wert des pollInterval muss größer oder gleich 1 sein.
* **excludeFilePattern (Zeichenfolge)**: Eine durch Semikolon (;) getrennte Liste von Mustern, mit deren Hilfe in einem überwachten Ordner ermittelt wird, welche Dateien und Ordner überprüft und aufgenommen werden sollen. Alle Dateien oder Ordner, die diesem Muster entsprechen, werden nicht für die Verarbeitung überprüft. Diese Einstellung ist nützlich, wenn die Eingabe ein Ordner mit mehreren Dateien ist. Der Inhalt des Ordners kann in einen Ordner mit einem Namen kopiert werden, der vom überwachten Ordner aufgenommen wird. Dies verhindert, dass der überwachte Ordner einen Ordner für die Verarbeitung aufnimmt, bevor dieser vollständig in den Eingabeordner kopiert ist. Der Standardwert ist Null.
Sie können [Dateimuster](../../forms/using/watched-folder-in-aem-forms.md#p-file-and-folder-patterns-p) verwenden, um Folgendes auszuschließen:

   * Dateien mit bestimmten Dateinamenerweiterungen, z. B. &#42;.dat, &#42;.xml, .pdf, &#42;.&#42;
   * Dateien mit bestimmten Namen; durch „data&#42;“ würden beispielsweise Dateien und Ordner mit den Namen „data1“, „data2“ usw. ausgeschlossen.
   * Dateien mit zusammengesetzten Ausdrücken in Name und Erweiterung, wie in den folgenden Beispielen:

      * Data[0-9][0-9][0-9].[dD][aA]&#39;port&#39;
      * &#42;.[dD][Aa]&#39;port&#39;
      * &#42;.[Xx][Mm][Ll]

Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](../../forms/using/watched-folder-in-aem-forms.md#p-file-and-folder-patterns-p).

* **includeFilePattern (Zeichenfolge)**: Eine durch Semikolon (;) getrennte Liste von Mustern, mit deren Hilfe in einem überwachten Ordner ermittelt wird, welche Dateien und Ordner überprüft und aufgenommen werden sollen. Wenn zum Beispiel für IncludeFilePattern „input&#42;“ festgelegt wird, werden alle Dateien und Ordner aufgenommen, die „input&#42;“ enthalten Hierzu gehören auch Dateien und Ordner namens „input1“, „input2“ usw. Der Standardwert ist &#42; und bezieht sich auf alle Dateien und Ordner. Sie können Dateimuster verwenden, um Folgendes einzuschließen:

   * Dateien mit bestimmten Dateinamenerweiterungen, z. B. &#42;.dat, &#42;.xml, .pdf, &#42;.&#42;
   * Dateien mit bestimmten Namen, z. B. data.&#42; Hierzu gehören auch Dateien und Ordner namens data1, data2 usw.

* Dateien mit zusammengesetzten Ausdrücken in Name und Erweiterung, wie in den folgenden Beispielen:

   * Data[0-9][0-9][0-9].[dD][aA]&#39;port&#39;

      * &#42;.[dD][Aa]&#39;port&#39;
      * &#42;.[Xx][Mm][Ll]

Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](../../forms/using/watched-folder-in-aem-forms.md#p-file-and-folder-patterns-p)

* **waitTime (Long)**: Die Zeit in Millisekunden, die gewartet wird, bevor ein Ordner oder eine Datei nach der Erstellung überprüft wird. Wenn die Wartezeit beispielsweise 3.600.000 Millisekunden (eine Stunde) beträgt und die Datei vor einer Minute erstellt wurde, wird diese Datei abgerufen, nachdem 59 oder mehr Minuten vergangen sind. Der Standardwert ist 0. Diese Einstellung ist nützlich, um sicherzustellen, dass eine Datei oder ein Ordner vollständig in den Eingabeordner kopiert wurde. Wenn Sie beispielsweise eine große Datei verarbeiten müssen und das Herunterladen der Datei 10 Minuten dauert, legen Sie die Wartezeit auf 10&#42;60 &#42;1000 Millisekunden fest. Dies verhindert, dass der überwachte Ordner die Datei überprüft, wenn sie nicht zehn Minuten alt ist.
* **purgeDuration (Lang)**: Dateien und Ordner im Ergebnisordner werden bereinigt, wenn sie älter als dieser Wert sind. Dieser Wert wird in Tagen gemessen. Diese Einstellung hilft sicherzustellen, dass der Ergebnisordner nicht voll wird. Ein Wert von -1 Tagen bedeutet, dass der Ergebnisordner nie gelöscht wird. Der Standardwert ist -1.
* **resultFolderName (Zeichenfolge)**: Der Ordner, in dem die Ergebnisse gespeichert werden. Wenn die Ergebnisse nicht in diesem Ordner angezeigt werden, überprüfen Sie den Fehlerordner. Schreibgeschützte Dateien werden nicht verarbeitet und im Fehlerordner gespeichert. Dieser Wert kann ein absoluter oder relativer Pfad mit den folgenden Dateimustern sein:

   * %F = Dateinamenpräfix
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
   * %P = Prozess- oder Auftrags-ID

  Wenn es beispielsweise am 17. Juli 2009 20 Uhr ist und Sie C:/Test/WF0/failure/%Y/%M/%D/%H/ angeben, ist der Ergebnisordner C:/Test/WF0/failure/2009/07/17/20.

  Wenn der Pfad nicht absolut, sondern relativ ist, wird der Ordner im überwachten Ordner erstellt. Der Standardwert ist „result/%Y/%M/%D/“, d. h. der Ergebnisordner im überwachten Ordner. Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](../../forms/using/watched-folder-in-aem-forms.md#p-file-and-folder-patterns-p).

>[!NOTE]
>
>Je kleiner die Größe der Ergebnisordner ist, desto besser ist die Leistung des überwachten Ordners. Wenn beispielsweise die geschätzte Auslastung für den überwachten Ordner bei 1000 Dateien pro Stunde liegt, sollten Sie ein Muster wie „result/%Y%M%D%H“ verwenden, sodass jede Stunde ein neuer Unterordner erstellt wird. Wenn die Belastung geringer ist (z. B. 1000 Dateien pro Tag), können Sie ein Muster wie &quot;result/%Y%M%D&quot;verwenden.

* **failureFolderName (Zeichenfolge)**: Der Ordner, in dem Dateien mit Fehlern gespeichert werden. Dieser Speicherort ist stets relativ zum überwachten Ordner. Sie können Dateimuster verwenden, wie für &quot;Ergebnisordner&quot;beschrieben. Schreibgeschützte Dateien werden nicht verarbeitet und im Fehlerordner gespeichert. Der Standardwert ist failure/%Y/%M/%D/.
* **preserveFolderName (Zeichenfolge):** Der Speicherort, an dem Dateien nach erfolgreicher Verarbeitung gespeichert werden. Der Pfad kann ein absoluter, relativer oder Null-Ordnerpfad sein. Sie können Dateimuster verwenden, wie für &quot;Ergebnisordner&quot;beschrieben. Der Standardwert ist preserve/%Y/%M/%D/.
* **batchSize (Lang)**: Die Anzahl der Dateien oder Ordner, die pro Überprüfung aufgenommen werden. Verwenden Sie , um eine Überlastung des Systems zu verhindern. Das gleichzeitige Überprüfen zu vieler Dateien kann zu einem Absturz führen. Der Standardwert ist 2.

  Die Einstellungen für Abrufintervall und Stapelgröße bestimmen, wie viele Dateien bei jeder Überprüfung vom Watched Folder-Dienst ausgewählt werden. Der Watched Folder-Dienst verwendet einen Quartz-Thread-Pool, um den Eingabeordner zu überprüfen. Der Thread-Pool wird für andere Dienste freigegeben. Wenn das Überprüfungsintervall gering ist, wird der Eingabeordner häufig von den Threads überprüft. Falls häufig Dateien im überwachten Ordner abgelegt werden, sollten Sie ein kurzes Überprüfungsintervall wählen. Wenn Dateien selten abgelegt werden, verwenden Sie ein größeres Überprüfungsintervall, damit die anderen Dienste die Threads verwenden können.

  Wenn eine große Anzahl von Dateien abgelegt wird, machen Sie die Stapelgröße groß. Wenn beispielsweise der vom Endpunkt des Typs „Überwachter Ordner“ gestartete Dienst 700 Dateien pro Minute verarbeiten kann und die Benutzer Dateien mit derselben Rate im Eingabeordner ablegen, verbessert das Festlegen der Stapelgröße auf 350 und des Abrufintervalls auf 30 Sekunden die Leistung des Überwachter Ordner-Dienstes, ohne dass der überwachte Ordner allzu häufig überprüft werden muss.

   Wenn Dateien im überwachten Ordner abgelegt werden, werden die Dateien in der Eingabe aufgelistet. Dadurch kann die Leistung reduziert werden, wenn jede Sekunde eine Überprüfung stattfindet. Eine Erhöhung des Überprüfungsintervalls kann die Leistung verbessern. Wenn das Volumen der abgelegten Dateien gering ist, passen Sie die Stapelgröße und das Abrufintervall entsprechend an. Wenn beispielsweise jede Sekunde 10 Dateien abgelegt werden, versuchen Sie, das pollInterval auf 1 Sekunde und die Stapelgröße auf 10 festzulegen.

* **throttleOn (Boolescher Wert)**: Wenn diese Option ausgewählt ist, wird die Anzahl der Aufträge für den überwachten Ordner begrenzt, die AEM Forms zu jeder Zeit verarbeiten kann. Die maximale Anzahl von Aufträgen wird durch den Wert von „Stapelgröße“ bestimmt. Der Standardwert ist „true“. (Siehe [Über Einschränkungen](../../forms/using/watched-folder-in-aem-forms.md#p-about-throttling-p).

* **overwriteDuplicateFilename (Boolescher Wert)**: Bei Festlegung auf „True“ werden Dateien im Ergebnisordner und im Aufbewahrungsordner überschrieben. Bei Festlegung auf &quot;False&quot;werden Dateien und Ordner mit dem Suffix &quot;Numerischer Index&quot;für den Namen verwendet. Der Standardwert ist False.
* **preserveOnFailure (Boolescher Wert)**: Bewahrt die Eingabedateien auf, wenn es zu einem Fehler bei der Ausführung des Vorgangs für einen Dienst kommt. Der Standardwert lautet true.
* **inputFilePattern (Zeichenfolge)**: Geben Sie das Muster der Eingabedateien für einen überwachten Ordner an. Erzeugt eine Zulässigkeitsliste der für die Dateien.
* **asynch (Boolescher Wert)**: Bestimmt, ob ein asynchroner oder ein synchroner Aufruftyp verwendet wird. Der Standardwert ist „true“ (asynchron). Da die Verarbeitung von Dateien sehr ressourcenintensiv ist, sollten Sie den Wert „true“ für das Flag „asynch“ beibehalten, um eine Überlastung des Haupt-Threads des Überprüfungsauftrags zu vermeiden. In einer Clusterumgebung muss der Wert „true“ für das Flag unter allen Umständen beibehalten werden, um den Lastenausgleich für die Dateiverarbeitung zwischen den verfügbaren Servern zu ermöglichen. Wird für das Flag der Wert „false“ festgelegt, versucht der Überprüfungsauftrag, die einzelnen Dateien bzw. Ordner der höchsten Ebene nacheinander innerhalb seines eigenen Threads zu verarbeiten. Setzen Sie das Flag nicht ohne einen bestimmten Grund auf &quot;false&quot;, z. B. für die Workflow-basierte Verarbeitung bei einem Setup mit einem einzelnen Server.

>[!NOTE]
>
>Die Workflows sind standardmäßig asynchron. Selbst wenn Sie den Wert auf false setzen, werden die Workflows im asynchronen Modus gestartet.

* **enabled (Boolescher Wert)**: Deaktiviert und aktiviert die Überprüfung des überwachten Ordners. Legen Sie für „enabled“ den Wert „true“ fest, um die Überprüfung des überwachten Ordners zu starten. Der Standardwert lautet true.
* **payloadMapperFilter:** Wenn ein Ordner als überwachter Ordner konfiguriert ist, wird im überwachten Ordner eine Ordnerstruktur erstellt. Die Struktur verfügt über Ordner, in denen Eingaben bereitgestellt, Ausgaben (Ergebnisse) empfangen, Daten für Fehler gespeichert, Daten für langlebige Prozesse beibehalten und Daten für verschiedene Phasen gespeichert werden. Die Ordnerstruktur eines überwachten Ordners kann als Nutzlast von Forms-orientierten Workflows dienen. Mit einem Payload-Mapper können Sie die Struktur einer Payload definieren, die einen überwachten Ordner für Eingabe, Ausgabe und Verarbeitung verwendet. Wenn Sie beispielsweise den standardmäßigen Zuordner verwenden, ordnet er den Inhalt des überwachten Ordners dem Ordner [payload]\input und [payload]\output zu. Es sind zwei vordefinierte Payload-Mapper-Implementierungen verfügbar. Wenn Sie [eine benutzerdefinierte Implementierung](../../forms/using/watched-folder-in-aem-forms.md#creating-a-custom-payload-mapper-filter)verwenden Sie eine der nativen Implementierungen:

   * **Standard-Mapper**: Verwenden Sie den Standard-Payload-Mapper, um den Eingabe- und Ausgabe-Inhalt der überwachten Ordner in separaten Eingabe- und Ausgabeordnern in der Payload zu belassen. Verwenden Sie im Payload-Pfad eines Workflows außerdem die Pfade [payload]/input/ und [payload]/output, um Inhalte abzurufen und zu speichern.

   * **Einfacher dateibasierter Payload-Mapper:** Verwenden Sie den einfachen dateibasierten Payload-Mapper, um Eingabe- und Ausgabe-Inhalte direkt im Nutzdatenordner zu beizubehalten. Es wird keine zusätzliche Hierarchie erstellt, wie z. B. ein Standard-Mapper.

### Benutzerdefinierte Konfigurationsparameter {#custom-configuration-parameters}

Sie können außer den oben aufgeführten Konfigurationseigenschaften für überwachte Ordner ach benutzerdefinierte Konfigurationsparameter angeben. Die benutzerdefinierten Parameter werden an den Dateiverarbeitungscode übergeben. Dies ermöglicht es, das Verhalten des Codes gemäß dem Wert des Parameters zu ändern. So legen Sie einen Parameter fest:

1. Melden Sie sich bei CRXDE-Lite an und navigieren Sie zum Konfigurationsknoten für den überwachten Ordner.
1. Fügen Sie einen Eigenschaftsparameter hinzu.&lt;property_name>“ zum Konfigurationsknoten für den überwachten Ordner hinzu. Es können nur Eigenschaften der Typen Boolescher Wert, Datum, Dezimalzahl, Double, Lang und Zeichenfolge verwendet werden. Sie können Eigenschaften mit einzelnen und mit mehreren Werten angeben.

>[!NOTE]
>
>Wenn der Datentyp der Eigenschaft Double lautet, geben Sie einen Dezimalpunkt im Wert dieser Eigenschaften an. Für alle Eigenschaften, deren Datentyp Double lautet und bei deren Wert kein Dezimalpunkt angegeben ist, wird der Typ in Long umgewandelt.

Diese Eigenschaften werden als unveränderliche Zuordnung des Typs „Map&lt;String, Object>“ an den Verarbeitungscode übergeben. Dieser Code kann ein ECMAScript, ein Workflow oder ein Dienst sein. Die für die Eigenschaften angegebenen Werte stehen als Schlüssel-Wert-Paare in der Zuordnung zur Verfügung. Der Schlüssel ist der Name der Eigenschaft, der Wert ihr Wert. Weitere Informationen zu benutzerdefinierten Konfigurationsparametern finden Sie in der folgenden Abbildung:

![Beispiel: Konfigurationsknoten für überwachten Ordner mit obligatorischen Eigenschaften, einige optionalen Eigenschaften und einigen Konfigurationsparametern](assets/custom-configuration-parameters.png)

Beispiel: Konfigurationsknoten für überwachten Ordner mit obligatorischen Eigenschaften, einigen optionalen Eigenschaften und einigen Konfigurationsparametern.

#### Stummschaltbare Variablen für Workflows {#mutable-variables-for-workflows}

Sie können veränderliche Variablen für Workflow-basierte Dateiverarbeitungsmethoden erstellen. Diese Variablen dienen als Container für die zwischen den Schritten eines Workflows übertragenen Daten. So erstellen Sie solche Variablen:

1. Melden Sie sich bei CRXDE-Lite an und navigieren Sie zum Konfigurationsknoten für den überwachten Ordner.

1. Fügen Sie die Eigenschaft workflow.var hinzu.&lt;variable_name> in den Konfigurationsknoten für den überwachten Ordner.

   Es können nur Eigenschaften der Typen Boolescher Wert, Datum, Dezimalzahl, Double, Lang und Zeichenfolge verwendet werden. Eigenschaften mit mehreren Werten werden ebenfalls unterstützt. Bei Eigenschaften mit mehreren Werten ist der für den Workflow-Schritt verfügbare Wert ein Array des angegebenen Typs.

   >[!NOTE]
   >
   >Wenn der Datentyp der Eigenschaft Double lautet, geben Sie einen Dezimalpunkt im Wert dieser Eigenschaften an. Für alle Eigenschaften, deren Datentyp Double lautet und bei deren Wert kein Dezimalpunkt angegeben ist, wird der Typ in Long umgewandelt.

>[!NOTE]
>
>In der JCR-Spezifikation ist ein Standardwert für die Eigenschaften erforderlich. Die Standardwerte stehen zur Verarbeitung durch die Schritte des Workflows zur Verfügung. Geben Sie also die richtigen Standardwerte an.

![custom-configuration-parameters2](assets/custom-configuration-parameters2.png)

## Verschiedene Methoden zur Verarbeitung von Dateien {#variousmethodsforprocessingfiles}

Sie können einen Workflow, einen Dienst oder ein Skript starten, um die in einem überwachten Ordner abgelegten Dokumente zu verarbeiten.

### Verarbeiten von Dateien in einem überwachten Ordner mithilfe eines Dienstes   {#using-a-service-to-process-files-of-a-watched-folder-nbsp}

Ein Dienst ist eine benutzerdefinierte Implementierung der `com.adobe.aemfd.watchfolder.service.api.ContentProcessor`-Schnittstelle. Sie wird in OSGi mit einigen benutzerdefinierten Eigenschaften registriert. Die benutzerdefinierten Eigenschaften der Implementierung machen sie eindeutig und erleichtern die Identifizierung der Implementierung.

#### Benutzerdefinierte Implementierung der ContentProcessor-Schnittstelle {#custom-implementation-of-the-contentprocessor-interface}

Die benutzerdefinierte Implementierung übernimmt einen Verarbeitungskontext (ein Objekt des Typs „com.adobe.aemfd.watchfolder.service.api.ProcessorContext“), liest die Eingabedokumente und -konfigurationsparameter aus dem Kontext, verarbeitet die Eingaben und fügt die Ausgaben wieder in den Kontext ein. ProcessorContext verfügt über die folgenden APIs:

* **getWatchFolderId**: Gibt die ID des überwachten Ordners zurück.
* **getInputMap**: Gibt eine Zuordnung des Typs „Map“ zurück. Die Schlüssel der Zuordnung sind der Dateiname der Eingabedatei und ein Dokumentobjekt mit dem Inhalt der Datei. Verwenden Sie die getinputMap-API, um die Eingabedateien zu lesen.
* **getConfigParameters**: Gibt eine unveränderliche Zuordnung des Typs „Map“ zurück. Die Zuordnung enthält die Konfigurationsparameter eines überwachten Ordners.

* **setResult**: Die ContentProcessor-Implementierung verwendet diese API zum Schreiben des Ausgabedokuments in den Ergebnisordner. Sie können den Namen für die Ausgabedatei an die setResult-API übergeben. Die API kann die bereitgestellte Datei je nach dem angegebenen Ausgabeordner/Dateimuster verwenden oder ignorieren. Wenn Sie ein Ordnermuster angeben, erhalten die Ausgabedateien Namen gemäß den Angaben in den Workflows. Wenn Sie ein Dateimuster angeben, erhalten die Ausgabedateien Namen gemäß den Angaben im Dateimuster.

Beispielsweise ist der folgende Code eine benutzerdefinierte Implementierung der ContentProcessor-Schnittstelle mit der benutzerdefinierten Eigenschaft &quot;foo=bar&quot;.

```java
@Component(metatype = true, immediate = true, label = "WF Test Service", description = "WF Test Service")
@Service(value = {OutputWriter.class, ContentProcessor.class})
@Property(name = "foo", value = "bar")
public class OutputWriter implements ContentProcessor {
```

while [Konfigurieren eines überwachten Ordners](../../forms/using/watched-folder-in-aem-forms.md#p-create-watched-folder-configuration-node-p)Wenn Sie die Eigenschaft &quot;inputProcessorId&quot;als (foo=bar) und die Eigenschaft &quot;inputProcessorType&quot;als Dienst angeben, wird der oben genannte Dienst (benutzerdefinierte Implementierung) zur Verarbeitung der Eingabedateien des überwachten Ordners verwendet.

Auch das folgenden Beispiel zeigt eine benutzerdefinierte Implementierung der ContentProcessor-Schnittstelle. In diesem Beispiel übernimmt der Dienst Eingabedateien, kopiert sie an einen temporären Speicherort und gibt ein Dokumentobjekt mit dem Inhalt der Datei zurück. Der Inhalt des Dokumentobjekts wird im Ergebnisordner gespeichert. Der physische Pfad des Ergebnisordners wird im [Konfigurationsknoten für überwachten Ordner](../../forms/using/watched-folder-in-aem-forms.md#p-create-watched-folder-configuration-node-p).

```java
@Component(immediate = true)
@Service(value = ContentProcessor.class)
@Property(name = "serviceSelector", value = "testProcessor1")
public class TestContentProcessor1 implements ContentProcessor {
    @Override
    public void processInputs(ProcessorContext context) throws Exception {
        Map.Entry<String, Document> e = context.getInputMap().entrySet().iterator().next();
        File f = new File((String) context.getConfigParameters().get("tempDir"),
                context.getConfigParameters().get("outPrefix") + e.getKey());
        e.getValue().copyToFile(f);
        context.setResult(f.getName(), new Document(f, true));
    }
}
```

### Verwenden von Skripten zur Verarbeitung von Dateien in einem überwachten Ordner {#using-scripts-to-process-files-of-a-watched-folder}

Skripts sind der ECMAScript-kompatible benutzerdefinierter Code, der in die im überwachten Ordner abgelegten Prozessdokumente geschrieben wird. Jedes Skript wird als ein JCR-Knoten dargestellt. Das Skript weist neben den standardmäßigen ECMAScript-Variablen (log, sling und weitere) eine processorContext-Variable auf. Die Variable gehört zum Typ „processorContext“. ProcessorContext verfügt über die folgenden APIs:

* **getWatchFolderId**: Gibt die ID des überwachten Ordners zurück.
* **getInputMap**: Gibt eine Zuordnung des Typs „Map“ zurück. Die Schlüssel der Zuordnung sind der Dateiname der Eingabedatei und ein Dokumentobjekt mit dem Inhalt der Datei. Verwenden Sie die getinputMap-API, um die Eingabedateien zu lesen.
* **getConfigParameters**: Gibt eine unveränderliche Zuordnung des Typs „Map“ zurück. Die Zuordnung enthält die Konfigurationsparameter eines überwachten Ordners.
* **setResult**: Die ContentProcessor-Implementierung verwendet diese API zum Schreiben des Ausgabedokuments in den Ergebnisordner. Sie können den Namen für die Ausgabedatei an die setResult-API übergeben. Die API kann die bereitgestellte Datei je nach dem angegebenen Ausgabeordner/Dateimuster verwenden oder ignorieren. Wenn Sie ein Ordnermuster angeben, erhalten die Ausgabedateien Namen gemäß den Angaben in den Workflows. Wenn Sie ein Dateimuster angeben, erhalten die Ausgabedateien Namen gemäß den Angaben im Dateimuster.

Der folgende Code ist ein Beispiel für ECMAScript. Er übernimmt Eingabedateien, kopiert sie an einen temporären Speicherort und gibt ein Dokumentobjekt mit dem Inhalt der Datei zurück. Der Inhalt des Dokumentobjekts wird im Ergebnisordner gespeichert. Der physische Pfad des Ergebnisordners wird im [Konfigurationsknoten für überwachten Ordner](../../forms/using/watched-folder-in-aem-forms.md#p-create-watched-folder-configuration-node-p).

>[!NOTE]
>
>Der Ausgabeordner und das Dateinamenpräfix werden anhand der Konfigurationsparameter für den überwachten Ordner bestimmt.

```java
var inputMap = processorContext.getInputMap();
var params = processorContext.getConfigParameters();
var entry = inputMap.entrySet().iterator().next();
var tempFile = new Packages.java.io.File(params.get("tempDir"), params.get("outPrefix") + entry.getKey());
entry.getValue().copyToFile(tempFile);
processorContext.setResult(tempFile.getName(), new Packages.com.adobe.aemfd.docmanager.Document(tempFile, true));
```

#### Speicherort von Skripten und Sicherheitsüberlegungen {#location-of-scripts-and-security-considerations}

Standardmäßig wird ein Container-Ordner (/etc/fd/watchfolder/scripts) bereitgestellt, in dem Kunden ihre Skripte platzieren können. Der vom watch-folder-Framework verwendete standardmäßige service-user verfügt über die erforderlichen Berechtigungen zum Lesen von Skripten von diesem Speicherort aus.

Wenn Sie Ihre Skripte an einem benutzerdefinierten Speicherort ablegen möchten, verfügt der standardmäßige service-user eventuell nicht über Leserechte für den benutzerdefinierten Speicherort. Führen Sie in einem solchen Fall die folgenden Schritte durch, um die benötigten Berechtigungen für den benutzerdefinierten Speicherort bereitzustellen:

1. Erstellen Sie einen Systembenutzer programmgesteuert oder über die Konsole https://&#39;[server]:[port]&#39;/crx/explorer. Sie können auch einen vorhandenen Systembenutzer verwenden. Es ist wichtig, hier mit Systembenutzern anstelle von normalen Benutzern zu arbeiten.
1. Gewähren Sie dem neu erstellten oder vorhandenen Systembenutzer Leseberechtigungen für den benutzerdefinierten Speicherort, an dem die Skripte gespeichert werden. Sie können über mehrere benutzerdefinierte Orte verfügen. Sie müssen ihm für alle benutzerdefinierten Speicherorte mindestens Leserechte gewähren.
1. Suchen Sie in der Felix-Konfigurationskonsole (/system/console/configMgr) die Dienstbenutzerzuordnung für die watch-folders. Diese Zuordnung sieht wie &quot;Mapping: adobe-aemds-core-watch-folder=...&quot;aus.
1. Klicken Sie auf die Zuordnung. Ändern Sie für den Eintrag &#39;adobe-aemds-core-watch-folder:scripts=fd-service&#39; die Angabe „fd-service“ in die ID des benutzerdefinierten Systembenutzers. Klicken Sie auf Speichern.

Jetzt können Sie den konfigurierten benutzerdefinierten Speicherort verwenden, um die Skripte zu speichern.

### Verarbeiten von Dateien in einem überwachten Ordner mithilfe eines Workflows {#using-a-workflow-to-process-files-of-a-watched-folder}

Mithilfe von Workflows können Sie Aktivitäten in Experience Manager automatisieren. Workflows bestehen aus einer Reihe von Schritten, die in einer bestimmten Reihenfolge ausgeführt werden. Bei jedem Schritt wird eine bestimmte Aktivität ausgeführt, etwa eine Seite aktiviert oder eine E-Mail verschickt. Workflows können mit Assets im Repository, mit Benutzerkonten und mit Experience Manager-Diensten interagieren. Daher können Workflows komplizierte Aufgaben koordinieren.

* Beachten Sie vor der Erstellung eines Workflows die folgenden Punkte:
* Die Ausgabe eines Schritts muss für alle nachfolgenden Schritte verfügbar sein.
In jedem Schritt muss es möglich sein, die in vorhergehenden Schritten generierten bestehenden Ausgabedaten zu aktualisieren oder zu löschen.
* Die veränderlichen Variablen werden für die Weiterleitung der benutzerdefinierten dynamischen Daten zwischen den Schritten verwendet.

Führen Sie für die Verarbeitung von Dateien mithilfe von Workflows die folgenden Schritte aus:

1. Erstellen Sie eine Implementierung der `com.adobe.aemfd.watchfolder.workflow.api.WorkflowContextProcessor`-Schnittstelle. Dies ist der für einen Dienst erstellten Implementierung ähnlich.

   >[!NOTE]
   >
   >Sie können die vollständige Implementierung in ECMAScript erstellen.

1. Suchen Sie in einem Schritt des Workflows den OSGi-Dienst des Typs com.adobe.aemfd.watchfolder.workflow.api.WorkflowContextService und rufen Sie die Methode execute() des Dienstes mit den folgenden Argumenten auf.

   * Ihre benutzerdefinierte Implementierung der WorkflowContextProcessor-Schnittstelle
   * workItem
   * workflowSession
   * Metadaten

Wenn Sie den Workflow mithilfe von Java implementieren, stellt die AEM-Workflow-Engine Werte für die Variablen „workItem“, „workflowSession“ und „metadata“ bereit. Diese Variablen werden als Argumente an die execute() -Methode Ihrer benutzerdefinierten WorkflowProcess -Implementierung übergeben.

Wenn Sie den Workflow mithilfe von ECMAScript implementieren, stellt die AEM-Workflow-Engine Werte für die Variablen „graniteWorkItem“, „graniteWorkflowSession“ und „metadata“ bereit. Diese Variablen werden als Argumente an die Methode WorkflowContextService.execute() übergeben.

Das Argument für „processWorkflowContext()“ ist ein Objekt des Typs „com.adobe.aemfd.watchfolder.workflow.api.WorkflowContext“. Die WorkflowContext-Schnittstelle verfügt über die folgenden APIs, um die oben erwähnten Workflow-spezifischen Überlegungen zu erleichtern:

* getWorkItem: Gibt den Wert der Variablen „WorkItem“ zurück. Die Variable wird an die Methode „WorkflowContextService.execute()“ übergeben.
* getWorkflowSession: Gibt den Wert der Variablen „WorkflowSession“ zurück. Die Variable wird an die Methode „WorkflowContextService.execute()“ übergeben.
* getMetadata: Gibt den Wert der Variablen „metadata“ zurück. Die Variable wird an die Methode „WorkflowContextService.execute()“ übergeben.
* getCommittedVariables: Gibt eine schreibgeschützte Objektzuordnung mit den in vorhergehenden Schritten festgelegten Variablen zurück. Wurde eine Variable nicht in einem der vorhergehenden Schritte geändert, wird der bei der Konfiguration des überwachten Ordners angegebene Standardwert zurückgegeben.
* getCommittedResults: Gibt eine schreibgeschützte Dokumentzuordnung zurück. Die Zuordnung stellt die in den vorhergehenden Schritten generierten Ausgabedateien dar.
* setVariable: Die Implementierung von „WorkflowContextProcessor“ nutzt diese Variable zur Steuerung der Variablen für die benutzerdefinierten dynamischen Daten, die zwischen den Schritten übertragen werden. Name und Typ der Variablen stimmen mit den bei der [Konfiguration des überwachten Ordners](../../forms/using/watched-folder-in-aem-forms.md#p-configure-the-watched-folder-p) angegebenen Namen der Variablen überein. Um den Wert einer Variablen zu ändern, rufen Sie die setVariable-API mit einem Wert ungleich Null auf. Um eine Variable zu entfernen, rufen Sie setVariable() mit einem Nullwert auf.

Die folgenden ProcessorContext-APIs sind ebenfalls verfügbar:

* getWatchFolderId: Gibt die ID des überwachten Ordners zurück.
* getInputMap: Gibt eine Zuordnung des Typs „Map&lt;String, Dokument>“ zurück. Die Schlüssel der Zuordnung sind der Dateiname der Eingabedatei und ein Dokumentobjekt mit dem Inhalt der Datei. Verwenden Sie die getinputMap-API, um die Eingabedateien zu lesen.
* getConfigParameters: Gibt eine unveränderliche Zuordnung des Typs „Map&lt;String, Objekt>“ zurück. Die Zuordnung enthält die Konfigurationsparameter eines überwachten Ordners.
* setResult: Die ContentProcessor-Implementierung verwendet diese API zum Schreiben des Ausgabedokuments in den Ergebnisordner. Sie können den Namen für die Ausgabedatei an die setResult-API übergeben. Die API kann die bereitgestellte Datei je nach dem angegebenen Ausgabeordner/Dateimuster verwenden oder ignorieren. Wenn Sie ein Ordnermuster angeben, erhalten die Ausgabedateien Namen gemäß den Angaben in den Workflows. Wenn Sie ein Dateimuster angeben, erhalten die Ausgabedateien Namen gemäß den Angaben im Dateimuster

Überlegungen zur setResult-API bei Verwendung in Workflows:

* Um ein neues Ausgabedokument als weiteren Beitrag zum Gesamtergebnis des Workflows hinzuzufügen, rufen Sie die setResult-API mit einem Dateinamen auf, der von keinem der vorhergehende Schritte als Name der Ausgabedatei verwendet wurde.
* Um die von einem vorhergegangenen Schritt generierte Ausgabe zu aktualisieren, rufen Sie die setResult-API mit einem Dateinamen auf, der bereits von einem vorhergehenden Schritt verwendet wurde.
* Um eine von einem vorhergegangenen Schritt generierte Ausgabe zu löschen, rufen Sie „setResult“ mit einem bereits von einem vorhergehenden Schritt verwendeten Dateinamen und Null als Inhalt auf.

>[!NOTE]
>
>Ein Aufruf der setResult-API mit einem Null-Inhalt würde in jedem anderen Szenario zu einem Fehler führen.

Das folgende Beispiel zeigt eine Implementierung als Workflow-Schritt. In diesem Beispiel verwendet das ECMAScript die Variable stepCount, um zu verfolgen, wie oft ein Schritt in der aktuellen Instanz des Workflows aufgerufen wird.
Der Name des Ausgabeordners ist eine Kombination aus der Nummer des aktuellen Schritts, dem Originaldateinamen und dem im Parameter „outPrefix“ angegebenen Präfix.

Das ECMAScript ruft einen Verweis des Workflow-Kontext-Dienstes ab und erstellt eine Implementierung der WorkflowContextProcessor-Schnittstelle. Die WorkflowContextProcessor-Implementierung übernimmt Eingabedateien, kopiert sie an einen temporären Speicherort und gibt ein Dokument zurück, das die kopierte Datei repräsentiert. Basierend auf dem Wert der Booleschen Variablen „purgePrevious“ wird beim aktuellen Schritt die Ausgabe aus dessen zuletzt vorhergegangener Ausführung innerhalb der aktuellen Instanz des Workflows gelöscht. Zuletzt wird die Methode „wfSvc.execute“ aufgerufen, um die Implementierung von „WorkflowContextProcessor“ auszuführen. Der Inhalt des Ausgabedokuments wird im Ergebnisordner unter dem physischen Pfad gespeichert, der im Konfigurationsknoten für den überwachten Ordner angegeben ist.

```javascript
log.error("Watch-folder workflow script called for step: " + graniteWorkItem.getNode().getTitle());
var wfSvc = sling.getService(Packages.com.adobe.aemfd.watchfolder.workflow.api.WorkflowContextService);
// Custom WorkflowContextProcessor implementation which defines the processWorkflowContext() method purely in JS
var impl = { processWorkflowContext: function (wfContext) {
    var wfId = wfContext.getWatchFolderId();
    var inputMap = wfContext.getInputMap();
    var paramMap = wfContext.getConfigParameters();
    var preResults = wfContext.getCommittedResults();
    var preVars = wfContext.getCommittedVariables();
    log.info("WF ID: " + wfId); // workflowId of type String
    log.info("Inputs: " + inputMap); // Input map of type Map<String, Document>
    log.info("Params: " + paramMap); // Config params of type Map<String, Object>
    log.info("Old results: " + preResults);
    log.info("Old variables: " + preVars);
    var currStepNumber = new Packages.java.lang.Long(new Packages.java.lang.Long(preVars.get("stepCount")).longValue() + 1);
    log.info("Current step number: " + currStepNumber);
    wfContext.setVariable("stepCount", currStepNumber);
    var entry = inputMap.entrySet().iterator().next();
    var tempFile = new Packages.java.io.File(paramMap.get("tempDir"), paramMap.get("outPrefix") + "STEP-" + currStepNumber + "-" + entry.getKey());
    entry.getValue().copyToFile(tempFile);
    var fName = tempFile.getName();
    var outDoc = new Packages.com.adobe.aemfd.docmanager.Document(tempFile, true);
    wfContext.setResult(tempFile.getName(), outDoc);
    var prevStepOutName = paramMap.get("outPrefix") + "STEP-" + (currStepNumber - 1) + "-" + entry.getKey();
    if (preResults.containsKey(prevStepOutName) && paramMap.get("purgePrevious").booleanValue()) {
        log.info("Purging previous step output " + prevStepOutName);
        wfContext.setResult(prevStepOutName, null);
    }
} }
wfSvc.execute(impl, graniteWorkItem, graniteWorkflowSession, metaData);
log.info("Exiting workflow script!")
```

### Erstellen eines Payload Mapper-Filters, um die Struktur eines überwachten Ordners der Payload eines Workflows zuzuordnen {#create-payload-mapper-filter-to-map-structure-of-a-watched-folder-to-the-payload-of-a-workflow}

Wenn Sie einen überwachten Ordner erstellen, wird eine Ordnerstruktur innerhalb des überwachten Ordners erstellt. Die Ordnerstruktur enthält Ordner für Phasen, Ergebnisse, Aufbewahrung, Eingabe und Fehler. Die Ordnerstruktur kann als Eingabe-Payload für den Workflow dienen und die Ausgabe von einem Workflow akzeptieren. Sie kann gegebenenfalls auch Fehlerquellen auflisten.

Wenn sich die Struktur einer Payload von der Struktur des überwachten Ordners unterscheidet, können Sie benutzerdefinierte Skripte schreiben, um die Struktur des überwachten Ordners der Payload zuzuordnen. Ein solches Skript wird als Payload-Mapper-Filter bezeichnet. Standardmäßig bietet AEM Forms einen Payload-Mapper-Filter, um die Struktur des überwachten Ordners einer Payload zuzuordnen.

#### Erstellen eines benutzerdefinierten Payload Mapper-Filters {#creating-a-custom-payload-mapper-filter}

1. Herunterladen [Adobe Client SDK](https://repo1.maven.org/maven2/com/adobe/aemfd/aemfd-client-sdk/).
1. Richten Sie das Client-SDK im Build-Pfad des maven-basierten Projekts ein. Um zu beginnen, können Sie das folgende Maven-basierte Projekt in der IDE Ihrer Wahl herunterladen und öffnen.
1. Bearbeiten Sie den im Beispielpaket verfügbaren Payload-Mapper-Filtercode entsprechend Ihren Anforderungen.
1. Verwenden Sie Maven, um ein Bundle des benutzerdefinierten Payload Mapper-Filters zu erstellen.
1. Verwendung [AEM Bundles Console](https://localhost:4502/system/console/bundles) um das Bundle zu installieren.

   Jetzt wird der benutzerdefinierte Payload Mapper-Filter in AEM Benutzeroberfläche für überwachte Ordner aufgeführt. Sie können es mit Ihrem Workflow verwenden.

   Der folgende Beispielcode implementiert einen einfachen dateibasierten Mapper für die Dateien, die relativ zu einer Payload gespeichert werden. Sie können ihn verwenden, um zu beginnen.

   ```java
   package com.adobe.aemfd.watchfolder.workflow;
   import com.adobe.aemfd.docmanager.Document;
   import com.adobe.aemfd.watchfolder.workflow.api.payload.PayloadMapper;
   import com.adobe.aemfd.watchfolder.workflow.api.payload.WorkflowExecutionContext;
   import com.adobe.aemfd.watchfolder.workflow.api.payload.WorkflowInitializationContext;
   import com.adobe.aemfd.watchfolder.workflow.api.payload.WorkflowVariable;
   import com.adobe.granite.workflow.exec.Workflow;
   import org.apache.felix.scr.annotations.Component;
   import org.apache.felix.scr.annotations.Service;
   import org.apache.sling.api.resource.ResourceResolver;
   import javax.jcr.Binary;
   import javax.jcr.Node;
   import java.util.Collection;
   import java.util.HashMap;
   import java.util.Map;
   @Component(immediate = true)
   @Service(value = PayloadMapper.class)
   public class SimpleFileBasedPayloadMapper implements PayloadMapper {
   @Override
   public Node createPayload(WorkflowInitializationContext wfInitCtxt, Node stagingFolder, String uniquePayloadName,
   Map<String, Binary> inputs, Collection<WorkflowVariable> variableDefs) throws Exception {
   Node dirNode = stagingFolder.addNode(uniquePayloadName, "sling:Folder");
   for (Map.Entry<String, Binary> bins: inputs.entrySet()) {
   Node fileNode = dirNode.addNode(bins.getKey(), "nt:file");
   Node resNode = fileNode.addNode ("jcr:content", "nt:resource");
   resNode.setProperty("jcr:data", bins.getValue());
   }
   return dirNode;
   }
   @Override
   public Map<String, Document> getInputs(WorkflowInitializationContext wfInitCtxt, WorkflowExecutionContext wfExecCtxt,
   Node payload, ResourceResolver resourceResolver) throws Exception {
   return null; //To change body of implemented methods use File | Settings | File Templates.
   }
   @Override
   public void setOutput(WorkflowInitializationContext wfInitCtxt, WorkflowExecutionContext wfExecCtxt, Node payload,
   String fileName, Binary contents, int outputMode) throws Exception {
   //To change body of implemented methods use File | Settings | File Templates.
   }
   @Override
   public Map<String, Document> getIntermediateOutputs(WorkflowInitializationContext wfInitCtxt,
   WorkflowExecutionContext wfExecCtxt, Node payload,
   ResourceResolver resourceResolver) throws Exception {
   return null; //To change body of implemented methods use File | Settings | File Templates.
   }
   @Override
   public Map<String, Document> getFinalOutputs(WorkflowInitializationContext wfInitCtxt, Workflow workflow, Node payload,
   ResourceResolver resourceResolver) throws Exception {
   Map<String, Object> params = wfInitCtxt.getConfigParameters();
   Map<String, Document> result = new HashMap<String, Document>();
   for (Map.Entry<String, Object> me: params.entrySet()) {
   String key = me.getKey();
   if (key.startsWith("pm.outfile.")) {
   String fName = (String) me.getValue();
   Document d = new Document(payload.getPath() + "/" + fName, resourceResolver);
   result.put(fName, d);
   }
   }
   return result;
   }
   @Override
   public void setVariable(WorkflowInitializationContext wfInitCtxt, WorkflowExecutionContext wfExecCtxt, Node payload,
   WorkflowVariable variable) throws Exception {
   //To change body of implemented methods use File | Settings | File Templates.
   }
   @Override
   public Map<String, Object> getVariables(WorkflowInitializationContext wfInitCtxt, WorkflowExecutionContext wfExecCtxt,
   Node payload) throws Exception {
   return null; //To change body of implemented methods use File | Settings | File Templates.
   }
   }
   ```

## Interaktion von Benutzern mit einem überwachten Ordner {#how-users-interact-with-a-watched-folder}

Bei Endpunkten des Typs „überwachter Ordner“ können Benutzer Vorgänge zur Verarbeitung von Dateien starten, indem sie Dateien oder Ordner vom Desktop in einen überwachten Ordner kopieren oder ziehen. Die Dateien werden in der Reihenfolge ihres Eingangs verarbeitet.

Wenn bei Endpunkten des Typs &quot;Überwachter Ordner&quot;für einen Auftrag nur eine Eingabedatei erforderlich ist, kann der Benutzer diese Datei in den Stammordner des überwachten Ordners kopieren.

Wenn der Auftrag mehrere Eingabedateien umfasst, muss der Benutzer einen Ordner außerhalb der Hierarchie des überwachten Ordners erstellen, der alle erforderlichen Dateien enthält. Dieser neue Ordner sollte die Eingabedateien enthalten (und optional eine DDX-Datei, falls vom Prozess benötigt). Nachdem der Auftragsordner erstellt wurde, kopiert er ihn in den Eingabeordner des überwachten Ordners.

>[!NOTE]
>
>Stellen Sie sicher, dass der Anwendungsserver Löschzugriff auf die Dateien im überwachten Ordner hat. Wenn AEM Forms die Dateien nicht aus dem Eingabeordner löschen kann, nachdem sie durchsucht wurden, wird der zugehörige Prozess auf unbestimmte Zeit gestartet.

## Weitere Informationen zu überwachten Ordnern {#additional-information-about-the-watched-folders}

### Über Einschränkungen {#about-throttling}

Wenn Einschränkungen für einen Endpunkt des Typs „überwachter Ordner“ aktiviert sind, wird die Anzahl der Aufträge für den überwachten Ordner, die zu jeder Zeit verarbeitet werden können, begrenzt. Die maximale Anzahl von Aufträgen wird durch den Wert für die Stapelgröße bestimmt, der auch im Endpunkt des überwachten Ordners konfigurierbar ist. In den Eingabeordner des überwachten Ordners eingehende Dokumente werden nicht mehr abgefragt, wenn der Grenzwert für „Einschränken“ erreicht ist. Die Dokumente bleiben im Eingabeordner, bis andere Aufträge für den überwachten Ordern abgeschlossen sind und ein erneuter Abfrageversuch unternommen wird. Bei der synchronen Verarbeitung werden alle in einer einzigen Abfrage verarbeiteten Aufträge für die Drosselung berücksichtigt, auch wenn die Aufträge nacheinander in einem einzigen Thread verarbeitet werden.

>[!NOTE]
>
>Die Drosselung wird bei einem Cluster nicht skaliert. Wenn die Drosselung aktiviert ist, verarbeitet der Cluster insgesamt zu keinem Zeitpunkt mehr als die Anzahl der Aufträge, die in der Stapelgröße angegeben sind. Diese Beschränkung ist clusterweit und nicht für jeden Knoten im Cluster spezifisch. Bei einer Stapelgröße von 2 könnte beispielsweise die Beschränkung für die Einschränkungen bei der Drosselung mit einem einzelnen Knoten erreicht werden, der zwei Aufträge verarbeitet, und keine anderen Knoten würden den Eingabeordner abrufen, bis einer der Aufträge abgeschlossen ist.

#### Funktionsweise von Einschränkungen {#how-throttling-works}

Der Eingabeordner des überwachten Ordners wird jeweils nach Ablauf des pollInterval überprüft, die in „Stapelgröße“ angegebene Anzahl von Dateien wird aufgenommen und der Zieldienst für jede dieser Dateien wird aufgerufen. Wenn die Stapelgröße beispielsweise 4 beträgt, nimmt der Dienst für überwachte Ordner bei jeder Überprüfung vier Dateien auf, erstellt vier Aufrufanforderungen und ruft den Zieldienst auf. Wenn der Watched Folder-Dienst vor Abschluss dieser Anforderungen erneut aufgerufen wird, werden unabhängig davon, ob die vorherigen vier Aufträge abgeschlossen sind, erneut vier Aufträge gestartet.

&quot;Einschränken&quot;verhindert, dass der Watched Folder-Dienst neue Aufträge aufruft, wenn die vorherigen Aufträge noch nicht abgeschlossen sind. Der Dienst für überwachte Ordner erkennt in der Bearbeitung befindliche Aufträge und verarbeitet neue Aufträge auf Grundlage der Stapelgröße abzüglich der in Bearbeitung befindlichen Aufträge. Wenn im zweiten Aufruf beispielsweise nur drei Aufträge abgeschlossen sind und ein Auftrag noch ausgeführt wird, ruft der Watched Folder-Dienst nur drei weitere Aufträge auf.

* Der Watched Folder-Dienst verlässt sich bei der Ermittlung der Anzahl der laufenden Aufträge auf die Anzahl der im Bereitstellungsordner vorhandenen Dateien. Verbleiben Dateien unverarbeitet im Bereitstellungsordner, werden keine weiteren Aufträge vom Dienst für überwachte Ordner aufgerufen. Wenn die Stapelgröße beispielsweise 4 beträgt und drei Aufträge angehalten sind, ruft der Dienst für überwachte Ordner bei Folgeaufrufen nur einen weiteren Auftrag auf. Es gibt mehrere Szenarien, in denen Dateien unverarbeitet im Bereitstellungsordner bleiben können. Wenn Aufträge angehalten werden, kann der Administrator den Prozess auf der Verwaltungsseite für Process Management beenden, sodass die Dateien vom Watched Folder-Dienst aus dem Bereitstellungsordner verschoben werden.
* Wenn der AEM Forms-Server heruntergefahren wird, bevor der Dienst für überwachte Ordner die Aufträge aufruft, kann der Administrator die Dateien aus dem Bereitstellungsordner verschieben. Weitere Informationen finden Sie unter [Fehlerquellen und Wiederherstellung](../../forms/using/watched-folder-in-aem-forms.md#p-failure-points-and-recoveryfailure-points-and-recovery-p).
* Wenn zwar der AEM Forms-Server, nicht aber der Dienst für überwachte Ordner ausgeführt wird, während der Job Manager-Dienst zurückruft (wozu es kommt, wenn Dienste nicht in der richtigen Reihenfolge starten), dann kann der Administrator die Dateien aus dem Bereitstellungsordner verschieben. Weitere Informationen finden Sie unter [Fehlerquellen und Wiederherstellung](../../forms/using/watched-folder-in-aem-forms.md#p-failure-points-and-recoveryfailure-points-and-recovery-p).

### Fehlerquellen und WiederherstellungFehlerquellen und Wiederherstellung {#failure-points-and-recoveryfailure-points-and-recovery}

Bei jedem Abrufereignis sperrt der Watched Folder-Dienst den Eingabeordner, verschiebt die Dateien, die dem Muster der einzuschließenden Dateien entsprechen, in den Bereitstellungsordner und entsperrt dann den Eingabeordner. Das Sperren ist erforderlich, damit zwei Threads nicht denselben Dateisatz abrufen und ihn zweimal verarbeiten. Die Wahrscheinlichkeit, dass es hierzu kommt, steigen mit einem kurzen pollInterval und einer hohen Stapelgröße. Nachdem die Dateien in den Bereitstellungsordner verschoben wurden, wird der Eingabeordner entsperrt, damit andere Threads den Ordner überprüfen können. Dieser Schritt bietet einen hohen Durchsatz, da andere Threads überprüfen können, während ein Thread die Dateien verarbeitet.

Nachdem die Dateien in den Bereitstellungsordner verschoben wurden, werden Aufrufanforderungen für jede Datei erstellt und der Zieldienst wird aufgerufen. Es kann vorkommen, dass der Watched Folder-Dienst die Dateien im Bereitstellungsordner nicht wiederherstellen kann:

* Wenn der Server heruntergefahren wird, bevor der Watched Folder-Dienst die Aufrufanforderung erstellen kann, bleiben die Dateien im Bereitstellungsordner im Bereitstellungsordner und werden nicht wiederhergestellt.

* Wenn der Watched Folder-Dienst die Aufrufanforderung für jede der Dateien im Bereitstellungsordner erfolgreich erstellt hat und der Server abstürzt, gibt es je nach Aufruftyp zwei Verhaltensweisen:

   * **Synchron**: Wenn der Watched Folder-Dienst so konfiguriert ist, dass der Dienst synchron aufgerufen wird, bleiben alle Dateien im Bereitstellungsordner unverarbeitet im Bereitstellungsordner.
   * **Asynchron:** In diesem Fall ist der Dienst für überwachte Ordner vom Job Manager-Dienst abhängig. Wenn der Job Manager-Dienst den überwachten Ordner zurückruft, werden die Dateien im Bereitstellungsordner basierend auf den Ergebnissen des Aufrufs in den Ordner &quot;Preserve&quot;oder &quot;Failure&quot;verschoben. Wenn der Job Manager-Dienst den überwachten Ordner nicht zurückruft, bleiben die Dateien unverarbeitet im Bereitstellungsordner. Diese Situation tritt auf, wenn der Watched Folder-Dienst nicht ausgeführt wird, wenn der Job Manager zurückruft.

#### Nicht verarbeitete Quelldateien im Bereitstellungsordner wiederherstellen {#recover-unprocessed-source-files-in-the-stage-folder}

Wenn der Watched Folder-Dienst die Quelldateien im Bereitstellungsordner nicht verarbeiten kann, können Sie die nicht verarbeiteten Dateien wiederherstellen.

1. Starten Sie den Anwendungsserver oder Knoten neu.

1. Beenden Sie den Watched Folder-Dienst von der Verarbeitung neuer Eingabedateien. Wenn Sie diesen Schritt überspringen, ist es viel schwieriger zu bestimmen, welche Dateien nicht im Bereitstellungsordner verarbeitet werden. Führen Sie eine der folgenden Aufgaben aus, um zu verhindern, dass der Watched Folder-Dienst neue Eingabedateien verarbeitet:

   * Ändern Sie die Eigenschaft includeFilePattern für den überwachten Ordner in eine Angabe, die keiner der neuen Eingabedateien entspricht (z. B. NOMATCH).
   * Setzen Sie den Prozess aus, der neue Eingabedateien erstellt.

   Warten Sie, bis AEM Forms alle Dateien wiederherstellt und verarbeitet. Die meisten Dateien sollten abgerufen und alle neuen Eingabedateien korrekt verarbeitet werden. Die Wartezeit bis zum Wiederherstellen und Verarbeiten der Dateien durch den überwachten Ordner hängt von der Dauer des aufzurufenden Vorgangs und der Anzahl der wiederherzustellenden Dateien ab.

1. Bestimmen Sie, welche Dateien nicht verarbeitet werden können. Wenn Sie eine angemessene Zeitdauer abgewartet und den vorherigen Schritt abgeschlossen haben und noch nicht verarbeitete Dateien im Bereitstellungsordner verbleiben, fahren Sie mit dem nächsten Schritt fort.

   >[!NOTE]
   >
   >Sie können den Datums- und Zeitstempel der Dateien im Bereitstellungsverzeichnis anzeigen. Je nach Anzahl der Dateien und der normalen Verarbeitungszeit können Sie bestimmen, welche Dateien alt genug sind, um als blockiert betrachtet zu werden.

1. Kopieren Sie die nicht verarbeiteten Dateien aus dem Bereitstellungsordner in den Eingabeordner.

1. Wenn Sie in Schritt 2 verhindert haben, dass der Watched Folder-Dienst neue Eingabedateien verarbeitet, ändern Sie das Muster für einzuschließende Dateien in den vorherigen Wert oder aktivieren Sie den von Ihnen deaktivierten Prozess erneut.

### Überwachte Ordner verketten {#chain-watched-folders-together}

Überwachte Ordner können miteinander verkettet werden, sodass ein Ergebnisdokument eines überwachten Ordners zum Eingabedokument des nächsten überwachten Ordners wird. Jeder überwachte Ordner kann einen anderen Dienst aufrufen. Indem überwachte Ordner auf diese Weise konfiguriert werden, können mehrere Dienste aufgerufen werden. Beispiel: Ein überwachter Ordner kann PDF-Dateien in Adobe PostScript® und ein anderer PostScript-Dateien in PDF/A konvertieren. Legen Sie dazu den Ergebnisordner des vom ersten Endpunkt definierten überwachten Ordners so fest, dass er auf den Eingabeordner des vom zweiten Endpunkt definierten überwachten Ordners verweist.

Die Ausgabe der ersten Konvertierung wird an „\Pfad\result“ übergeben. Als Eingabe der zweiten Konvertierung dient „\Pfad\result“, und die Ausgabe der zweiten Konvertierung wird in „\Pfad\result\result“ oder den Ordner übertragen, den Sie im Feld „Ergebnisordner“ für die zweite Konvertierung angegeben haben.

### Datei- und Ordnermuster {#file-and-folder-patterns}

Administratoren können den Dateityp angeben, der einen Dienst aufrufen kann. Für jeden überwachten Ordner können mehrere Dateimuster angegeben werden. Ein Dateimuster kann eine der folgenden Dateieigenschaften sein:

* Dateien mit bestimmten Dateinamenerweiterungen, z. B. &#42;.dat, &#42;.xml, .pdf, &#42;.&#42;
* Dateien mit bestimmten Namen, z. B. data.&#42;
* Dateien mit zusammengesetzten Ausdrücken in Name und Erweiterung, wie in den folgenden Beispielen:

   * Data[0-9][0-9][0-9].[dD][aA]&#39;port&#39;
   * &#42;.[dD][Aa]&#39;port&#39;
   * &#42;.[Xx][Mm][Ll]

* Der Administrator kann das Dateimuster des Ausgabeordners definieren, in dem die Ergebnisse gespeichert werden sollen. Für die Ausgabeordner (Ergebnis, Beibehaltung und Fehler) kann der Administrator eines der folgenden Dateimuster angeben:
* %Y = Jahr (vollständig)
* %y = Jahr (letzte zwei Stellen)
* %M = Monat,
* %D = Tag des Monats,
* %d = Tag des Jahres,
* %h = Stunde,
* %m = Minute,
* %s = Sekunde,
* %R = Zufallszahl zwischen 0 und 9
* %J = Auftragsname

Der Pfad zum Ergebnisordner kann beispielsweise C:\Adobe\Adobe LiveCycle ES4\BarcodedForms\%y\%m\%d lauten.

Zuordnungen von Ausgabeparametern können auch zusätzliche Muster angeben, z. B.:

* %F = Quelldateiname
* %E = Quelldateinamenerweiterung

Wenn das Zuordnungsmuster der Ausgabeparameter mit &quot;File.separator&quot;(dem Pfadtrennzeichen) endet, wird ein Ordner erstellt und der Inhalt in diesen Ordner kopiert. Endet das Muster nicht mit „File.separator“, wird der Inhalt (Ergebnisdatei oder -ordner) mit diesem Namen erstellt.

## Verwenden von PDF Generatoren mit einem überwachten Ordner {#using-pdf-generator-with-a-watched-folder}

Sie können einen überwachten Ordner so konfigurieren, dass ein Workflow, ein Dienst oder ein Skript zur Verarbeitung der Eingabedokumente gestartet wird. Im folgenden Abschnitt wird ein überwachter Ordner für den Aufruf eines ECMAScripts konfiguriert. Das ECMAScript konvertiert Microsoft Word-Dokumente (.docx) in PDF-Dokumente mit PDF Generator.

Führen Sie die folgenden Schritte aus, um einen überwachten Ordner mit PDF Generator zu konfigurieren:

1. [ECMAScript erstellen](../../forms/using/watched-folder-in-aem-forms.md#p-create-an-ecmascript-p)
1. [Workflow erstellen](../../forms/using/watched-folder-in-aem-forms.md#p-create-a-workflow-p)
1. [Überwachten Ordner konfigurieren](../../forms/using/watched-folder-in-aem-forms.md#p-configure-the-watched-folder-p)

### Erstellen eines ECMAScript {#create-an-ecmascript}

Das ECMAScript konvertiert Microsoft Word-Dokumente (.docx) mit der createPDF-API des PDF Generators in PDF-Dokumente. Führen Sie die folgenden Schritte aus, um das Skript zu erstellen:

1. Öffnen Sie CRXDE Lite in einem Browserfenster. Die URL lautet https://&#39;[server]:[port]&#39;/crx/de.

1. Navigieren Sie zu „/etc/workflow/scripts“ und erstellen Sie einen Ordner namens „PDFG“. 

1. Erstellen Sie im Ordner „PDFG“ eine Datei mit dem Namen „pdfg-openOffice-sample.ecma“ und fügen Sie ihr den folgenden Code hinzu:

   ```javascript
   var wfSvc = sling.getService(Packages.com.adobe.aemfd.watchfolder.workflow.api.WorkflowContextService);
   // Custom ContentProcessor implementation which defines the processInputs() method purely in JS
   var impl = { processWorkflowContext: function (wrkfContext) {
   
     //  var logger = Packages.org.slf4j.LoggerFactory.getLogger("cmb-mergeandprint-sample.ecma");
                   var inputMap=wrkfContext.getInputMap();
   
                   var distiller = sling.getService(com.adobe.pdfg.service.api.DistillerService);
                   var generatePDF = sling.getService(com.adobe.pdfg.service.api.GeneratePDFService);
                   var pdfgConfig = sling.getService(com.adobe.pdfg.service.api.PDFGConfigService);
       var result = new Packages.java.util.HashMap();
       var entry = inputMap.entrySet().iterator().next();
       var pdfgOut = generatePDF.createPDF(entry.getValue(), ".docx", "Standard OpenOffice", "Standard", "No Security", null, null);
                   var convertedDoc = pdfgOut.get("ConvertedDoc");
   //   logger.info("SuccessFully saved the document to Ouput Node");
       wrkfContext.setResult(entry.getKey().substring(0, entry.getKey().lastIndexOf('.'))+".pdf",convertedDoc); // Ownership flag set to true for auto temp-file deletion.
   
   } }
   
   wfSvc.execute(impl, graniteWorkItem, graniteWorkflowSession, metaData);
   ```

1. Speichern und schließen Sie die Datei.

### Workflow erstellen {#create-a-workflow}

1. Öffnen Sie die AEM Workflow-Benutzeroberfläche in einem Browser-Fenster.
   <https://[servername>]:&#39;port&#39;/workflow

1. Klicken Sie in der Modellansicht auf **Neu**. Geben Sie im Dialogfeld Neuer Workflow **Titel** und klicken Sie auf **OK**.

   ![create-a-workflow-pdf](assets/create-a-workflow-pdf.png)

1. Wählen Sie den neu erstellten Workflow aus und klicken Sie auf **Bearbeiten**. Der Workflow wird in einem neuen Fenster geöffnet.

1. Löschen Sie den standardmäßigen Workflow-Schritt. Ziehen Sie den Prozessschritt aus dem Sidekick in den Workflow.

   ![create-a-workflow-pdf2](assets/create-a-workflow-pdf2.png)

1. Klicken Sie mit der rechten Maustaste auf den Prozessschritt und wählen Sie **Bearbeiten**. Das Fenster Schritt-Eigenschaften wird angezeigt.

1. Wählen Sie auf der Registerkarte „Prozess“ das ECMAScript aus. Zum Beispiel das Skript „pdfg-openOffice-sample.ecma“, das in [Erstellen eines ECMAScripts](#p-create-an-ecmascript-p) erstellt wurde. Aktivieren Sie die Option **Handler-Modus** und klicken Sie auf **OK**.

   ![create-a-workflow3-pdf](assets/create-a-workflow3-pdf.png)

### Konfigurieren des überwachten Ordners {#configure-the-watched-folder}

1. Öffnen Sie CRXDE Lite in einem Browserfenster. https://&#39;[server]:[port]&#39;/crx/de/

1. Navigieren Sie zum Ordner „/etc/fd/watchfolder/config/“ und erstellen Sie einen Knoten des Typs „nt:unstructured“.

   ![configure-the-watched-folder-pdf](assets/configure-the-watched-folder-pdf.png)

1. Fügen Sie dem Knoten folgende Eigenschaften hinzu:

   * folderPath (Zeichenfolge): Der Pfad des Ordners, der regelmäßig mit dem angegebenen Zeitintervall überprüft werden soll. Der Ordner muss sich an einem freigegebenen Speicherort befinden und alle Server müssen uneingeschränkten Zugriff auf diesen Server haben.
inputProcessorType (Zeichenfolge): Der Typ des zu startenden Prozesses. Geben Sie für dieses Tutorial „Workflow“ an.

   * inputProcessorId (Zeichenfolge): Das Verhalten der Eigenschaft „inputProcessorId“ wird durch den für die Eigenschaft „inputProcessorType“ angegebenen Wert gesteuert. In diesem Beispiel hat die Eigenschaft „inputProcessorType“ den Wert „workflow“. Geben Sie daher für die Eigenschaft &quot;inputProcessorId&quot;den folgenden Pfad des PDFG-Workflows an: /etc/workflow/models/pdfg/jcr:content/model

   * outputFilePattern (Zeichenfolge): Das Muster der Ausgabedatei. Sie können ein Ordner- oder Dateimuster angeben. Wenn Sie ein Ordnermuster angeben, erhalten die Ausgabedateien Namen gemäß den Angaben in den Workflows. Wenn Sie ein Dateimuster angeben, erhalten die Ausgabedateien Namen gemäß den Angaben im Dateimuster.

   Für überwachte Ordner werden außer den oben genannten obligatorischen Eigenschaften einige optionale Eigenschaften unterstützt. Eine vollständige Liste und Beschreibung der optionalen Eigenschaften finden Sie unter [Eigenschaften für überwachte Ordner](#watchedfolderproperties).

## Bekannte Probleme {#watched-folder-known-issues}

Beim Starten von AEM 6.5 Forms auf JEE werden Dateien verarbeitet, bevor JBoss vollständig gestartet wird, wodurch Dateien nicht verarbeitet werden können. Um dies zu vermeiden, löschen Sie vor dem Starten von JBoss alle überwachten Ordner.
