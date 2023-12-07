---
title: Sicherungsstrategien für überwachte Ordner
description: In diesem Dokument wird beschrieben, wie überwachte Ordner von verschiedenen Sicherungs- und Wiederherstellungsszenarien betroffen sind, welche Einschränkungen und Ergebnisse in diesen Szenarien bestehen und wie Datenverlust minimiert werden kann.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 0d36160a-29fa-4cc4-a0ff-fc681d3e040e
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 20%

---

# Sicherungsstrategien für überwachte Ordner {#backup-strategies-for-watched-folders}

In diesem Inhalt wird beschrieben, wie überwachte Ordner von verschiedenen Sicherungs- und Wiederherstellungsszenarien betroffen sind, welche Einschränkungen und Ergebnisse bei diesen Szenarien bestehen und wie Datenverlust minimiert werden kann.

*Überwachter Ordner* ist eine dateisystembasierte Anwendung, die konfigurierte Dienstvorgänge aufruft, die die Datei in einem der folgenden Ordner in der Hierarchie des überwachten Ordners bearbeiten:

* Eingabe
* Staging
* Ausgabe
* Fehler
* Preserve

Ein Benutzer oder eine Client-Anwendung legt die Datei oder den Ordner zuerst im Eingabeordner ab. Der Dienstvorgang verschiebt die Datei dann zur Verarbeitung in den Ordner &quot;Stage&quot;. Nachdem der Dienst den angegebenen Vorgang ausgeführt hat, wird die geänderte Datei im Ordner &quot;Output&quot;gespeichert. Erfolgreich verarbeitete Quelldateien werden in den Ordner &quot;Preserve&quot;verschoben und fehlgeschlagene Verarbeitungsdateien werden in den Ordner &quot;Failure&quot;verschoben. Wenn das Attribut `Preserve On Failure` für den überwachten Ordner aktiviert ist, werden fehlerhaft verarbeitete Quelldateien in den Aufbewahrungsordner verschoben. (Siehe [Konfigurieren von Endpunkten des Typs &quot;überwachter Ordner&quot;](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#configuring-watched-folder-endpoints).

Sie können überwachte Ordner sichern, indem Sie das Dateisystem sichern.

>[!NOTE]
>
>Diese Sicherung ist unabhängig vom Sicherungs- und Wiederherstellungsprozess für Datenbank- oder Dokumentenspeicher.

## Funktionsweise überwachter Ordner {#how-watched-folders-work}

In diesem Inhalt wird der Prozess zur Verarbeitung von Dateien für überwachte Ordner beschrieben. Es ist wichtig, diesen Prozess zu verstehen, bevor ein Konjunkturprogramm entwickelt wird. In diesem Beispiel ist das Attribut `Preserve On Failure` für den überwachten Ordner aktiviert. Die Dateien werden in der Reihenfolge ihres Eingangs verarbeitet.

In der folgenden Tabelle wird die Dateibearbeitung von fünf Beispieldateien (Datei1, Datei2, Datei3, Datei4, Datei5) während des gesamten Prozesses beschrieben. In der Tabelle stellt die X-Achse die Zeit dar, z. B. Zeit 1 oder T1, und die Y-Achse stellt Ordner innerhalb der Hierarchie des überwachten Ordners dar, z. B. Eingabe.

<table>
 <thead>
  <tr>
   <th><p>Ordner</p></th>
   <th><p>T1</p></th>
   <th><p>T2</p></th>
   <th><p>T3</p></th>
   <th><p>T4</p></th>
   <th><p>T5</p></th>
   <th><p>T6</p></th>
   <th><p>T7</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Eingabe</p></td>
   <td><p>Datei1, Datei2, Datei3, Datei4</p></td>
   <td><p>Datei2, Datei3, Datei4</p></td>
   <td><p>Datei3, Datei4</p></td>
   <td><p>Datei4</p></td>
   <td><p>leer</p></td>
   <td><p>Datei5</p></td>
   <td><p>leer</p></td>
  </tr>
  <tr>
   <td><p>Staging</p></td>
   <td><p>leer</p></td>
   <td><p>Datei1</p></td>
   <td><p>Datei2</p></td>
   <td><p>Datei3</p></td>
   <td><p>Datei4</p></td>
   <td><p>leer</p></td>
   <td><p>Datei5</p></td>
  </tr>
  <tr>
   <td><p>Ausgabe</p></td>
   <td><p>leer</p></td>
   <td><p>leer</p></td>
   <td><p>file1_out</p></td>
   <td><p>file1_out, file2_out</p></td>
   <td><p>file1_out, file2_out</p></td>
   <td><p>file1_out, file2_out, file4_out</p></td>
   <td><p>file1_out, file2_out, file4_out</p></td>
  </tr>
  <tr>
   <td><p>Fehler</p></td>
   <td><p>leer</p></td>
   <td><p>leer</p></td>
   <td><p>leer</p></td>
   <td><p>leer</p></td>
   <td><p>file3_fail, file3 </p></td>
   <td><p>file3_fail, file3 </p></td>
   <td><p>file3_fail, file3 </p></td>
  </tr>
  <tr>
   <td><p>Preserve</p></td>
   <td><p>leer</p></td>
   <td><p>leer</p></td>
   <td><p>Datei1 </p></td>
   <td><p>Datei1, Datei2 </p></td>
   <td><p>Datei1, Datei2 </p></td>
   <td><p>Datei1, Datei2, Datei4 </p></td>
   <td><p>Datei1, Datei2, Datei4 </p></td>
  </tr>
 </tbody>
</table>

Im folgenden Text wird die Dateibearbeitung für jedes Mal beschrieben:

**T1:** Die vier Beispieldateien werden im Eingabeordner abgelegt.

**T2:** Der Dienstvorgang verschiebt Datei1 in den Ordner „Stage“ zur Bearbeitung.

**T3**: Der Dienstvorgang verschiebt Datei2 in den Bereitstellungsordner zur Bearbeitung. Die Ergebnisse von Datei1 werden in den Ordner &quot;Output&quot;verschoben und Datei1 in den Ordner &quot;Preserve&quot;.

**T4:** Der Dienstvorgang verschiebt Datei3 in den Ordner „Stage“ zur Bearbeitung. Die Ergebnisse für Datei2 werden in den Ordner „Output“ verschoben, und Datei2 wird in den Ordner „Preserve“ verschoben.

**T5:** Der Dienstvorgang verschiebt Datei4 in den Ordner „Stage“ zur Bearbeitung. Die Bearbeitung von Datei3 schlägt fehl, und der Dienstvorgang platziert sie im Ordner „Failure“.

**T6:** Der Dienstvorgang platziert Datei5 im Ordner „Input“. Die Ergebnisse für Datei4 werden in den Ordner „Output“ verschoben, und Datei4 wird in den Ordner „Preserve“ verschoben.

**T7:** Der Dienstvorgang verschiebt Datei5 in den Ordner „Stage“ zur Bearbeitung.

## Überwachte Ordner sichern {#backing-up-watched-folders}

Es wird empfohlen, das gesamte Dateisystem für überwachte Ordner in einem anderen Dateisystem zu sichern.

## Überwachte Ordner wiederherstellen {#restoring-watched-folders}

In diesem Abschnitt wird beschrieben, wie Sie überwachte Ordner wiederherstellen. Überwachte Ordner rufen häufig Prozesse mit kurzer Lebensdauer auf, die innerhalb einer Minute abgeschlossen werden. In solchen Fällen verhindert das Wiederherstellen des überwachten Ordners mit einer stündlichen Sicherung keinen Datenverlust.

Wenn beispielsweise eine Sicherung zum Zeitpunkt T1 erfolgt und der Server bei T7 fehlschlägt, werden Datei1, Datei2, Datei3 und Datei4 bereits bearbeitet. Das Wiederherstellen des überwachten Ordners mit einer Sicherung, die auf T1 durchgeführt wird, verhindert keinen Datenverlust.

Wenn eine neuere Sicherung durchgeführt wurde, können Sie die Dateien wiederherstellen. Beachten Sie beim Wiederherstellen der Dateien, in welchem Hierarchieordner sich die aktuelle Datei befindet:

**Staging:** Dateien in diesem Ordner werden nach der Wiederherstellung des überwachten Ordners erneut verarbeitet.

**Input:** Dateien in diesem Ordner werden nach der Wiederherstellung des überwachten Ordners erneut verarbeitet.

**Ergebnis:** Dateien in diesem Ordner werden nicht verarbeitet.

**Ausgabe:** Dateien in diesem Ordner werden nicht verarbeitet.

**Preserve:** Dateien in diesem Ordner werden nicht verarbeitet.

## Strategien zur Minimierung von Datenverlust {#strategies-to-minimize-data-loss}

Die folgenden Strategien können den Datenverlust von Ausgabe- und Eingabeordnern beim Wiederherstellen eines überwachten Ordners minimieren:

* Sichern Sie die Ausgabe- und Fehlerordner häufig, z. B. stündlich, um den Verlust von Ergebnis- und Fehlerdateien zu vermeiden.
* Sichern Sie die Eingabedateien in einem anderen Ordner als dem überwachten Ordner. Dadurch wird die Dateiverfügbarkeit nach der Wiederherstellung sichergestellt, falls Sie die Dateien weder im Ordner &quot;Output&quot;noch im Ordner &quot;Failure&quot;finden können. Stellen Sie sicher, dass Ihr Dateibenennungsschema einheitlich ist.

  Wenn Sie die Ausgabe beispielsweise mit `%F.`*extension* speichern, hat die Ausgabedatei denselben Namen wie die Eingabedatei. Auf diese Weise können Sie feststellen, welche Eingabedateien bearbeitet werden und welche erneut übermittelt werden müssen. Wenn nur die Datei &quot;file1_out&quot;im Ergebnisordner und nicht die Dateien &quot;datei2_out&quot;, &quot;file3_out&quot;und &quot;file4_out&quot;angezeigt werden, müssen Sie die Dateien &quot;datei2&quot;, &quot;file3&quot;und &quot;file4&quot;erneut senden.

* Wenn die verfügbare Sicherung des überwachten Ordners älter ist als die für die Verarbeitung des Auftrags benötigte Zeit, sollten Sie zulassen, dass das System einen überwachten Ordner erstellt und die Dateien automatisch im Eingabeordner ablegt.
* Wenn die neueste verfügbare Sicherung nicht neu genug ist, die Sicherungsdauer kürzer ist als die für die Verarbeitung der Dateien benötigte Zeit und der überwachte Ordner wiederhergestellt wird, wurde die Datei in einer der folgenden Phasen bearbeitet:

   * **Phase 1:** Im Eingabeordner
   * **Phase 2:** Kopiert in den Ordner &quot;Stage&quot;, aber der Prozess wurde noch nicht aufgerufen
   * **Phase 3:** Kopiert in den Ordner &quot;Stage&quot;und der Prozess wird aufgerufen
   * **Phase 4:** Laufende Bearbeitung
   * **Stufe 5:** Ergebnisse

  Wenn sich Dateien in Phase 1 befinden, werden sie bearbeitet. Wenn sich Dateien in Phase 2 oder 3 befinden, platzieren Sie sie im Eingabeordner, damit die Bearbeitung erneut durchgeführt werden kann.

  >[!NOTE]
  >
  >Wenn die Verarbeitung einer Datei mehrmals erfolgt, wird ein Datenverlust verhindert, Ergebnisse können jedoch dupliziert werden.

## Zusammenfassung {#conclusion}

Aufgrund der dynamischen und sich ständig ändernden Natur eines überwachten Ordners sollten überwachte Ordner mit Dateien wiederhergestellt werden, die innerhalb eines Tages gesichert werden. Eine Best Practice wäre, die Ergebnisse zu sichern, den Eingabeordner auf einem Server zu speichern und Eingabedateien zu verfolgen, damit Sie den Auftrag bei einem Fehler erneut übermitteln können.
