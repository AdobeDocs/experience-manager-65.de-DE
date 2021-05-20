---
title: Sicherungsstrategien für überwachte Ordner
seo-title: Sicherungsstrategien für überwachte Ordner
description: In diesem Dokument werden überwachte Ordner unter dem Aspekt der Sicherung und Wiederherstellung beschrieben, wobei die Einschränkungen und Ergebnisse verschiedener Sicherungsszenarien erläutert und Vorschläge zur Minimierung möglicher Datenverluste unterbreitet werden.
seo-description: In diesem Dokument werden überwachte Ordner unter dem Aspekt der Sicherung und Wiederherstellung beschrieben, wobei die Einschränkungen und Ergebnisse verschiedener Sicherungsszenarien erläutert und Vorschläge zur Minimierung möglicher Datenverluste unterbreitet werden.
uuid: c61997b8-6c36-4bd9-90e5-411841a6c176
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 6f775933-e989-4456-ad01-9bdf5dee3dad
exl-id: 0d36160a-29fa-4cc4-a0ff-fc681d3e040e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 95%

---

# Sicherungsstrategien für überwachte Ordner {#backup-strategies-for-watched-folders}

In diesem Abschnitt werden überwachte Ordner unter dem Aspekt der Sicherung und Wiederherstellung beschrieben, wobei die Einschränkungen und Ergebnisse verschiedener Sicherungsszenarien erläutert und Vorschläge zur Minimierung möglicher Datenverluste unterbreitet werden.

*Watched Folder* ist eine dateisystembasierte Anwendung zum Aufrufen konfigurierter Dienstvorgänge, über welche die Datei in einem der folgenden Ordner in der Hierarchie überwachter Ordner verarbeitet wird:

* Eingabe
* Staging
* Ausgabe
* Failure
* Preserve

Ein Benutzer oder eine Clientanwendung legt zuerst Dateien oder Ordner im Eingabeordner ab. Im Rahmen des Dienstvorgangs wird die Datei dann zur Verarbeitung in den Ordner „Stage“ verschoben. Nachdem der Dienst den vorgesehenen Vorgang ausgeführt hat, wird die geänderte Datei im Ordner „Output“ gespeichert. Erfolgreich verarbeitete Quelldateien werden in den Ordner „Preserve“, nicht verarbeitete Dateien in den Ordner „Failure“ verschoben. Wenn das Attribut `Preserve On Failure` für den überwachten Ordner aktiviert ist, werden fehlgeschlagene verarbeitete Quelldateien in den Ordner &quot;Preserve&quot;verschoben. (Siehe [Endpunkte für überwachte Ordner konfigurieren](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#configuring-watched-folder-endpoints).)

Überwachte Ordner können durch Sichern des Dateisystems gesichert werden.

>[!NOTE]
>
>Diese Sicherung ist unabhängig vom Sicherungs- und Wiederherstellungsprozess für Datenbank oder Dokumentenspeicher.

## Funktionsweise überwachter Ordner {#how-watched-folders-work}

In diesem Abschnitt wird der Dateiverarbeitungsprozess für überwachte Ordner beschrieben. Sie müssen mit diesem Prozess vertraut sein, bevor Sie einen Wiederherstellungsplan entwickeln. In diesem Beispiel ist das Attribut `Preserve On Failure` für den überwachten Ordner aktiviert. Die Dateien werden in der Reihenfolge ihres Eingangs verarbeitet.

In der folgenden Tabelle wird die Dateiverarbeitung von fünf Beispieldateien (Datei1, Datei2, Datei3, Datei4, Datei5) im gesamten Prozess beschrieben. In der Tabelle werden auf der X-Achse die Zeit (z. B. Zeit 1 oder Z1) und auf der Y-Achse die Ordner in der Hierarchie öffentlicher Ordner abgebildet, z. B. „Eingabe“.

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
   <td><p>Fehlgeschlagen</p></td>
   <td><p>leer</p></td>
   <td><p>leer</p></td>
   <td><p>leer</p></td>
   <td><p>leer</p></td>
   <td><p>Datei3_Fehler, Datei3 </p></td>
   <td><p>Datei3_Fehler, Datei3 </p></td>
   <td><p>Datei3_Fehler, Datei3 </p></td>
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

Der folgende Text beschreibt die Dateiverarbeitung am jeweiligen Zeitpunkt:

**T1:** Die vier Beispieldateien werden im Ordner „Input“ abgelegt.

**T2:** Der Dienstvorgang verschiebt Datei1 in den Ordner „Stage“ zur Bearbeitung.

**T3:** Der Dienstvorgang verschiebt Datei2 in den Ordner „Stage“ zur Bearbeitung. Die Ergebnisse für Datei1 werden in den Ordner „Output“ verschoben, und Datei1 wird in den Ordner „Preserve“ verschoben.

**T4:** Der Dienstvorgang verschiebt Datei3 in den Ordner „Stage“ zur Bearbeitung. Die Ergebnisse für Datei2 werden in den Ordner „Output“ verschoben, und Datei2 wird in den Ordner „Preserve“ verschoben.

**T5:** Der Dienstvorgang verschiebt Datei4 in den Ordner „Stage“ zur Bearbeitung. Die Bearbeitung von Datei3 schlägt fehl, und der Dienstvorgang platziert sie im Ordner „Failure“.

**T6:** Der Dienstvorgang platziert Datei5 im Ordner „Input“. Die Ergebnisse für Datei4 werden in den Ordner „Output“ verschoben, und Datei4 wird in den Ordner „Preserve“ verschoben.

**T7:** Der Dienstvorgang verschiebt Datei5 in den Ordner „Stage“ zur Bearbeitung.

## Überwachte Ordner sichern {#backing-up-watched-folders}

Es wird empfohlen, das gesamte Überwachter Ordner-Dateisystem in einem anderen Dateisystem zu sichern.

## Überwachte Ordner wiederherstellen  {#restoring-watched-folders}

In diesem Kapitel wird die Wiederherstellung überwachter Ordner beschrieben. Überwachte Ordner rufen häufig kurzfristige Prozesse auf, die binnen einer Minute abgeschlossen sind. In diesen Fällen werden Datenverluste nicht verhindert, wenn der überwachte Ordner mittels einer stündlich erstellten Sicherung wiederhergestellt wird.

Wenn beispielsweise eine Sicherung bei Zeitpunkt Z1 erfolgt und der Server bei Z7 ausfällt, wurden Datei1, Datei2, Datei3 und Datei4 bereits verarbeitet. Das Wiederherstellen des überwachten Ordners mit einer bei T1 erfolgten Sicherung verhindert keinen Datenverlust.

Wenn eine spätere Sicherung erfolgte, können Sie die Dateien wiederherstellen. Beachten Sie beim Wiederherstellen der Dateien die Hierarchie überwachter Ordner, in der sich die aktuelle Datei befindet:

**Stage:** Dateien in diesem Ordner werden nach der Wiederherstellung des überwachten Ordners erneut verarbeitet.

**Input:** Dateien in diesem Ordner werden nach der Wiederherstellung des überwachten Ordners erneut verarbeitet.

**Result:** Dateien in diesem Ordner werden nicht verarbeitet.

**Output:** Dateien in diesem Ordner werden nicht verarbeitet.

**Preserve:** Dateien in diesem Ordner werden nicht verarbeitet.

## Strategien zur Minimierung von Datenverlusten  {#strategies-to-minimize-data-loss}

Über die folgenden Vorgehensweisen kann der Datenverlust bei Ein- und Ausgabeordnern bei der Wiederherstellung eines überwachten Ordners minimiert werden:

* Sichern Sie Ein- und Ausgabeordner regelmäßig, z. B. stündlich, um den Verlust von Ergebnis- und Fehlerdateien zu vermeiden.
* Sichern Sie die Eingabedateien in einem anderen Ordner als dem überwachten Ordner. Dies gewährleistet die Verfügbarkeit der Dateien nach der Wiederherstellung, sollten Sie die Dateien weder im Ordner „Output“ noch im Ordner „Failure“ finden. Vergewissern Sie sich, dass das Dateibenennungsschema einheitlich ist.

   Wenn Sie beispielsweise die Ausgabe mit `%F.`*extension* speichern, hat die Ausgabedatei denselben Namen wie die Eingabedatei. Auf diese Weise können Sie leichter bestimmen, welche Eingabedateien verarbeitet wurden und welche erneut zur Verarbeitung übergeben werden müssen. Wenn im Ordner „Result“ nur die Datei Datei1_out angezeigt wird, aber weder Datei2_out noch Datei3_out noch Datei4_out, bedeutet dies, dass die Dateien Datei2, Datei3 und Datei4 erneut zur Verarbeitung übergeben werden müssen.

* Ist die verfügbare Sicherung des überwachten Ordners älter als der Zeitraum, der zur Verarbeitung des Auftrags erforderlich ist, ist es besser, das System automatisch einen neuen überwachten Ordner erstellen zu lassen und dann die Dateien im Ordner „Input“ abzulegen.
* Wenn die letzte verfügbare Sicherung nicht neu genug ist, die Sicherungsdauer kürzer als die für die Verarbeitung der Dateien benötigte Zeit ist und der überwachte Ordner wiederhergestellt wurde, wurde die Datei in einer folgenden Phasen verarbeitet:

   * **Phase 1:** Im Ordner „Input“
   * **Phase 2:** Kopiert in den Ordner „Stage“, aber der Prozess wurde noch nicht aufgerufen
   * **Phase 3:** Kopiert in den Ordner „Stage“, und der Prozess wurde aufgerufen
   * **Phase 4:** Verarbeitung ist im Gang
   * **Phase 5:** Ergebnisse wurden zurückgegeben.

   Sind Dateien in Phase 1, werden sie verarbeitet. Sind Dateien in Phase 2 oder 3, legen Sie sie im Eingabeordner ab, damit die Verarbeitung erneut erfolgt.

   >[!NOTE]
   >
   >Wenn die Verarbeitung einer Datei mehr als einmal erfolgt, wird ein Datenverlust verhindert, doch Ergebnisse werden ggf. dupliziert.

## Zusammenfassung {#conclusion}

Aufgrund der Dynamik und konstanten Änderung überwachter Ordner muss deren Wiederherstellung mithilfe von Dateien erfolgen, die binnen eines Tages gesichert wurden. Eine bewährte Methode besteht darin, die Ergebnisse zu sichern, den Eingabeordner auf einem Server zu speichern und die Eingabedateien zu erfassen, damit im Falle eines Ausfalls der Auftrag erneut zur Verarbeitung übergeben werden kann.
