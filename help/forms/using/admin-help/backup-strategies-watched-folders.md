---
title: Sicherungsstrategien für überwachte Ordner
description: In diesem Dokument werden überwachte Ordner unter dem Aspekt der Sicherung und Wiederherstellung beschrieben, wobei die Einschränkungen und Ergebnisse verschiedener Sicherungsszenarien erläutert und Vorschläge zur Minimierung möglicher Datenverluste gemacht werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 0d36160a-29fa-4cc4-a0ff-fc681d3e040e
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '1080'
ht-degree: 100%

---

# Sicherungsstrategien für überwachte Ordner {#backup-strategies-for-watched-folders}

In diesem Abschnitt werden überwachte Ordner unter dem Aspekt der Sicherung und Wiederherstellung beschrieben, wobei die Einschränkungen und Ergebnisse verschiedener Sicherungsszenarien erläutert und Vorschläge zur Minimierung möglicher Datenverluste gemacht werden.

*Überwachter Ordner* ist eine dateisystembasierte Anwendung, die konfigurierte Dienstvorgänge aufruft, die die Datei in einem der folgenden Ordner in der Hierarchie überwachter Ordner bearbeiten:

* Eingabe
* Staging
* Ausgabe
* Fehler
* Preserve

Eine Person oder eine Client-Anwendung legt zuerst Dateien oder Ordner im Eingabeordner ab. Im Rahmen des Dienstvorgangs wird die Datei dann zur Verarbeitung in den Bereitstellungsordner verschoben. Nachdem der Dienst den vorgesehenen Vorgang ausgeführt hat, wird die geänderte Datei im Ausgabeordner gespeichert. Erfolgreich verarbeitete Quelldateien werden in den Aufbewahrungsordner, nicht verarbeitete Dateien in den Fehlerordner verschoben. Wenn das Attribut `Preserve On Failure` für den überwachten Ordner aktiviert ist, werden fehlerhaft verarbeitete Quelldateien in den Aufbewahrungsordner verschoben. (Siehe [Konfigurieren von Endpunkten des Typs „Überwachter Ordner“](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#configuring-watched-folder-endpoints).)

Sie können überwachte Ordner sichern, indem Sie das Dateisystem sichern.

>[!NOTE]
>
>Diese Sicherung ist unabhängig vom Sicherungs- und Wiederherstellungsprozess für Datenbank- oder Dokumentenspeicher.

## Funktionsweise überwachter Ordner {#how-watched-folders-work}

In diesem Inhalt wird der Prozess zur Verarbeitung von Dateien für überwachte Ordner beschrieben. Sie müssen mit diesem Prozess vertraut sein, bevor Sie einen Wiederherstellungsplan entwickeln. In diesem Beispiel ist das Attribut `Preserve On Failure` für den überwachten Ordner aktiviert. Die Dateien werden in der Reihenfolge ihres Eingangs verarbeitet.

In der folgenden Tabelle wird die Dateibearbeitung von fünf Beispieldateien (Datei1, Datei2, Datei3, Datei4, Datei5) während des gesamten Prozesses beschrieben. In der Tabelle werden auf der X-Achse die Zeit (z. B. Zeit 1 oder T1) und auf der Y-Achse die Ordner in der Hierarchie öffentlicher Ordner abgebildet, z. B. „Eingabe“.

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
   <td><p>Datei1_out</p></td>
   <td><p>Datei1_out, Datei2_out</p></td>
   <td><p>Datei1_out, Datei2_out</p></td>
   <td><p>Datei1_out, Datei2_out, Datei4_out</p></td>
   <td><p>Datei1_out, Datei2_out, Datei4_out</p></td>
  </tr>
  <tr>
   <td><p>Fehler</p></td>
   <td><p>leer</p></td>
   <td><p>leer</p></td>
   <td><p>leer</p></td>
   <td><p>leer</p></td>
   <td><p>Datei3_fail, Datei3 </p></td>
   <td><p>Datei3_fail, Datei3 </p></td>
   <td><p>Datei3_fail, Datei3 </p></td>
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

Im Folgenden wird die Dateiverarbeitung am jeweiligen Zeitpunkt beschrieben:

**T1:** Die vier Beispieldateien werden im Eingabeordner abgelegt.

**T2:** Der Dienstvorgang verschiebt Datei1 in den Ordner „Stage“ zur Bearbeitung.

**T3**: Der Dienstvorgang verschiebt Datei2 in den Bereitstellungsordner zur Bearbeitung. Die Ergebnisse für Datei1 werden in den Ausgabeordner verschoben, und Datei1 wird in den Aufbewahrungsordner verschoben.

**T4:** Der Dienstvorgang verschiebt Datei3 in den Ordner „Stage“ zur Bearbeitung. Die Ergebnisse für Datei2 werden in den Ordner „Output“ verschoben, und Datei2 wird in den Ordner „Preserve“ verschoben.

**T5:** Der Dienstvorgang verschiebt Datei4 in den Ordner „Stage“ zur Bearbeitung. Die Bearbeitung von Datei3 schlägt fehl, und der Dienstvorgang platziert sie im Ordner „Failure“.

**T6:** Der Dienstvorgang platziert Datei5 im Ordner „Input“. Die Ergebnisse für Datei4 werden in den Ordner „Output“ verschoben, und Datei4 wird in den Ordner „Preserve“ verschoben.

**T7:** Der Dienstvorgang verschiebt Datei5 in den Ordner „Stage“ zur Bearbeitung.

## Sichern überwachter Ordner {#backing-up-watched-folders}

Es wird empfohlen, das gesamte Dateisystem der überwachten Ordner in einem anderen Dateisystem zu sichern.

## Wiederherstellen überwachter Ordner {#restoring-watched-folders}

In diesem Abschnitt wird beschrieben, wie Sie überwachte Ordner wiederherstellen. Überwachte Ordner rufen häufig kurzfristige Prozesse auf, die binnen einer Minute abgeschlossen sind. Wenn in solchen Fällen der überwachte Ordner mit einem stündlich durchgeführten Backup wiederhergestellt wird, kann der Datenverlust nicht verhindert werden.

Wenn beispielsweise ein Backup bei Zeitpunkt T1 erfolgt und der Server bei T7 ausfällt, wurden Datei1, Datei2, Datei3 und Datei4 bereits verarbeitet. Das Wiederherstellen des überwachten Ordners mit einem bei T1 erfolgten Backup verhindert keinen Datenverlust.

Wenn ein späteres Backup erfolgte, können Sie die Dateien wiederherstellen. Beachten Sie beim Wiederherstellen der Dateien die Hierarchie überwachter Ordner, in der sich die aktuelle Datei befindet:

**Bereitstellung:** Dateien in diesem Ordner werden nach der Wiederherstellung des überwachten Ordners erneut verarbeitet.

**Input:** Dateien in diesem Ordner werden nach der Wiederherstellung des überwachten Ordners erneut verarbeitet.

**Ergebnis:** Dateien in diesem Ordner werden nicht verarbeitet.

**Ausgabe:** Dateien in diesem Ordner werden nicht verarbeitet.

**Preserve:** Dateien in diesem Ordner werden nicht verarbeitet.

## Strategien zur Minimierung von Datenverlusten {#strategies-to-minimize-data-loss}

Mithilfe der folgenden Strategien kann der Datenverlust bei Aus- und Eingabeordnern bei der Wiederherstellung eines überwachten Ordners minimiert werden:

* Sichern Sie Ausgabe- und Fehlerordner regelmäßig, z. B. stündlich, um den Verlust von Ergebnis- und Fehlerdateien zu vermeiden.
* Sichern Sie die Eingabedateien in einem anderen Ordner als dem überwachten Ordner. Dies gewährleistet die Verfügbarkeit der Dateien nach einer Wiederherstellung, sollten Sie die Dateien weder im Ausgabe- noch im Fehlerordner finden. Vergewissern Sie sich, dass das Dateibenennungsschema einheitlich ist.

  Wenn Sie die Ausgabe beispielsweise mit `%F.`*extension* speichern, hat die Ausgabedatei denselben Namen wie die Eingabedatei. Auf diese Weise können Sie leichter bestimmen, welche Eingabedateien verarbeitet wurden und welche erneut zur Verarbeitung übergeben werden müssen. Wenn im Ergebnisordner nur die Datei Datei1_out angezeigt wird, aber weder Datei2_out noch Datei3_out noch Datei4_out, bedeutet dies, dass Sie die Dateien Datei2, Datei3 und Datei4 erneut zur Verarbeitung übergeben müssen.

* Ist die verfügbare Sicherung des überwachten Ordners älter als der Zeitraum, der zur Verarbeitung des Auftrags erforderlich ist, ist es besser, das System einen neuen überwachten Ordner erstellen und dann die Dateien automatisch im Eingabeordner ablegen zu lassen.
* Wenn die letzte verfügbare Sicherung nicht neu genug ist, die Sicherungsdauer kürzer als die für die Verarbeitung der Dateien benötigte Zeit ist und der überwachte Ordner wiederhergestellt wurde, wurde die Datei in einer der folgenden Phasen verarbeitet:

   * **Phase 1:** Im Eingabeordner
   * **Phase 2:** Kopiert in den Bereitstellungsordner, aber der Prozess wurde noch nicht aufgerufen.
   * **Phase 3:** Kopiert in den Bereitstellungsordner und der Prozess wurde aufgerufen.
   * **Phase 4:** Verarbeitung ist im Gang.
   * **Phase 5:** Ergebnisse wurden zurückgegeben.

  Sind Dateien in Phase 1, werden sie verarbeitet. Sind Dateien in Phase 2 oder 3, legen Sie sie im Eingabeordner ab, damit die Verarbeitung erneut erfolgt.

  >[!NOTE]
  >
  >Wenn die Verarbeitung einer Datei mehr als einmal erfolgt, wird ein Datenverlust verhindert, doch Ergebnisse werden ggf. dupliziert.

## Zusammenfassung {#conclusion}

Aufgrund der Dynamik und konstanten Änderung überwachter Ordner muss deren Wiederherstellung mithilfe von Dateien erfolgen, die innerhalb eines Tages gesichert wurden. Eine Best Practice besteht darin, die Ergebnisse zu sichern, den Eingabeordner auf einem Server zu speichern und die Eingabedateien zu erfassen, damit im Falle eines Ausfalls der Auftrag erneut zur Verarbeitung übergeben werden kann.
