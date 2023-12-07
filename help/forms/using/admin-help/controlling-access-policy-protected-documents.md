---
title: Steuern des Zugriffs auf richtliniengeschützte Dokumente
description: Erfahren Sie, wie Sie den Zugriff auf richtliniengeschützte Dokumente anzeigen, verwalten und steuern können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: 0eb6e769-97c1-41ee-8d12-91bece984947
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '2167'
ht-degree: 23%

---

# Steuern des Zugriffs auf richtliniengeschützte Dokumente {#controlling-access-to-policy-protected-documents}

Sie können steuern, wie Empfänger Ihre richtliniengeschützten Dokumente verwenden, unabhängig davon, wie weit Sie sie verteilen.

Auf der Seite &quot;Dokumente&quot;haben Sie folgende Möglichkeiten:

* Suchen Sie nach den Details richtliniengeschützter Dokumente und zeigen Sie diese an. Sie können Informationen zum Dokumentnamen, zum Veröffentlichungsnamen, zum Richtliniennamen und zum Datum der Anwendung der Richtlinie anzeigen. Wenn die Richtlinie, die ein Dokument geschützt hat, gelöscht wird, wird auch die ID der gelöschten Richtlinie unter dem Richtliniennamen angezeigt. Benutzer können ihre eigenen richtliniengeschützten Dokumente anzeigen und verwalten. Administratoren können alle richtliniengeschützten Dokumente anzeigen und verwalten.
* Ändern Sie die Details der Richtlinie, die auf ein Dokument angewendet wird. Benutzer können ihre eigenen Richtlinien bearbeiten, Administratoren können freigegebene und persönliche Richtlinien bearbeiten und Richtliniensatzkoordinatoren können freigegebene Richtlinien in den Richtliniensätzen bearbeiten, für die sie Berechtigungen haben. Sie können direkt auf der Seite &quot;Dokumentdetails&quot;auf die mit einem Dokument verknüpfte Richtlinie zugreifen.
* Sperren und reaktivieren Sie den Zugriff auf ein richtliniengeschütztes Dokument. Administratoren können den Zugriff auf alle Dokumente sperren und reaktivieren. Richtliniensatzkoordinatoren (die berechtigt sind, Dokumente zu verwalten) können den Zugriff auf richtliniengeschützte Dokumente, die freigegebene Richtlinien verwenden, aus ihren Richtliniensätzen sperren und reaktivieren. Benutzer können den Zugriff auf ihre richtliniengeschützten Dokumente sperren, wenn sie die Richtlinie erstellt haben, die das Dokument schützt, oder wenn die Richtlinie eine freigegebene Richtlinie ist, die diese Funktion zulässt.
* Wechseln Sie die Richtlinie, die auf ein Dokument angewendet wird. Benutzer, die Richtlinien auf Dokumente anwenden, können eine Richtlinie wechseln, wenn sie sie erstellt haben oder wenn es sich um eine freigegebene Richtlinie handelt, die diese Funktion ermöglicht. Richtliniensatzkoordinatoren können Richtlinien aus ihren Richtliniensätzen wechseln. Administratoren können Richtlinien wechseln, die auf jedes Dokument angewendet werden.

Wenn ein Dokument durch eine Richtlinie geschützt ist und Sie Zugriffsberechtigungen sperren oder die angewendete Richtlinie wechseln, werden die Änderungen wie folgt wirksam:

* Wenn das Dokument online ist, werden Änderungen sofort angewendet, es sei denn, der Benutzer hat das Dokument geöffnet. In diesem Fall muss der Benutzer das Dokument schließen, damit die Änderungen wirksam werden.
* Wenn ein Empfänger das Dokument offline verwendet (z. B. auf einem Laptop), werden die Änderungen bei der nächsten Synchronisierung mit Document Security durch Öffnen eines beliebigen richtliniengeschützten Dokuments wirksam.

## Informationen zu einem Dokument anzeigen {#view-information-about-a-document}

Für jedes Dokument, das auf der Seite &quot;Dokumente&quot;aufgeführt ist, können Sie den Dokumentnamen, den Namen des Herausgebers, den Richtliniennamen und das Datum sehen, an dem das Dokument geschützt wurde. Wenn die Richtlinie, die ein Dokument geschützt hat, gelöscht wurde, wird die Richtlinien-ID unter &quot;Richtlinienname&quot;aufgeführt.

Sie können auch weitere Details zu einem bestimmten Dokument auf der Seite &quot;Dokumentdetails&quot;anzeigen, die nachfolgend beschrieben werden:

>[!NOTE]
>
>Verwenden Sie den Link Richtlinienname auf der Seite &quot;Dokumentdetails&quot;, um auf Richtlinien zuzugreifen, die in Microsoft Outlook automatisch für Empfänger eines Dokuments generiert werden, das an eine E-Mail-Nachricht angehängt ist. Diese Richtlinien werden nicht auf der Seite &quot;Richtlinien&quot;angezeigt.

**Dokumentname:** Der Name des ausgewählten Dokuments.

**Dokument-ID:** Eine eindeutige Kennung, die Document Security zuweist, wenn eine Richtlinie auf das Dokument angewendet wird. Document Security nutzt diese Nummer zum Nachverfolgen des Dokuments.

**Dokumentstatus:** Status des Dokuments (z. B. aktiv oder gesperrt).

**Vermarkter:** Name des Benutzers, der die Richtlinie an das Dokument angehängt hat.

**Richtlinienname:** Der Name der Richtlinie, die dem Schutz des Dokuments dient. Sie können auf den Namen klicken, um die Richtlinie zu öffnen. Verwenden Sie diesen Link, um auf Richtlinien zuzugreifen, die Acrobat für Empfänger eines Dokuments generiert, das an eine E-Mail-Nachricht in Outlook angehängt ist. Diese Richtlinien werden nicht auf der Seite Richtlinien angezeigt.

**Richtlinientyp:** Der Richtlinientyp, der auf das Dokument angewendet wurde.

**Veröffentlichungsdatum:** Das Datum, an dem die Richtlinie auf das Dokument angewendet wurde.

**Zugehörige Iterationen:** Wenn das Dokument verwandte Iterationen hat, erscheint dieses Element auch in der Liste. Klicken Sie auf den Link, um die Liste der zugehörigen Iterationen für das Dokument anzuzeigen.

Benutzer können Informationen zu ihren geschützten Dokumenten anzeigen. Administratoren können Informationen zu Dokumenten anzeigen, die alle Benutzer durch eine Richtlinie geschützt haben. Richtliniensatzkoordinatoren können Informationen zu Dokumenten anzeigen, die durch Richtlinien in ihren Richtliniensätzen geschützt sind.

1. Klicken Sie auf der Document Security-Seite auf Dokumente.
1. Klicken Sie in der Dokumentliste auf das entsprechende Dokument. Die Seite &quot;Dokumentdetails&quot;mit detaillierten Informationen zum Dokument wird geöffnet. Auf dieser Seite finden Sie außerdem Optionen zum Sperren des Dokumentzugriffs, Wechseln der Richtlinie und Anzeigen von Ereignissen, die mit diesem Dokument in Verbindung stehen.

## Zugehörige Iterationen für ein Dokument anzeigen {#view-related-iterations-for-a-document}

Wenn die Verfolgung verwandter Iterationen aktiviert ist, können Sie Versionen eines Dokuments verfolgen, die von verschiedenen Benutzern gespeichert wurden. Diese Funktion wird nur von bestimmten Anwendungen wie PTC Pro/ENGINEER Wildfire unterstützt.

Diese Funktion ist nützlich, wenn mehrere Benutzer zusammenarbeiten und verschiedene Versionen desselben Dokuments speichern. Document Security kann die verschiedenen Iterationen verfolgen. Daher können Sie Dokumentinformationen für die verschiedenen Versionen einfach anzeigen.

Wenn diese Funktion aktiviert ist, können Sie die zugehörigen Iterationen eines Dokuments auf der Seite Dokumente anzeigen.

1. Zeigen Sie die Dokumentdetailseite für ein Dokument an. (Siehe [Informationen zu einem Dokument anzeigen](controlling-access-policy-protected-documents.md#view-information-about-a-document).
1. Klicken Sie auf Verwandte Iterationen anzeigen . Die Option ist nur verfügbar, wenn die Funktion aktiviert ist. Die Liste der zugehörigen Iterationen wird angezeigt. Für jede Iteration können Sie die folgenden Informationen anzeigen:

   * **Iteration:** Der Dateiname. Er kann vom ursprünglichen Dateinamen abweichen und an seinem Ende ist eine Versionsnummer angefügt.
   * **Herausgeber:** Der Herausgeber des ursprünglichen Dokuments.
   * **Erstellt von:** Der Benutzer, der die Iteration gespeichert hat.
   * **Erstellungsdatum:** Datum und Uhrzeit der Speicherung der Iteration.
   * **Richtlinie:** Die Richtlinie, welche die Iteration schützt. Verschiedene Iterationen können durch verschiedene Richtlinien geschützt werden.

1. Um die Seite &quot;Dokumentdetails&quot;für diese Iteration anzuzeigen, klicken Sie auf den Dateinamen einer Iteration.

## Zugriff auf Dokumente sperren und reaktivieren {#revoking-and-reinstating-access-to-documents}

Sie können den Zugriff auf richtliniengeschützte Dokumente sperren und reaktivieren:

**Benutzer:** Können den Zugriff auf Dokumente, die sie schützen, über eigene persönliche Richtlinien oder über freigegebene Richtlinien sperren oder reaktivieren, bei denen die Sperrfunktion für den Benutzer aktiviert ist, der die Richtlinie anwendet. Benutzer, die den Zugriff auf ein Dokument nicht sperren oder eine Richtlinie nicht wechseln können, müssen sich an einen Administrator wenden.

**Administratoren:** Können Zugriffsberechtigungen für sämtliche richtliniengeschützten Dokumente sperren oder reaktivieren, auch für diejenigen, die durch persönliche oder freigegebene Richtlinien geschützt sind. Wenn ein Administrator den Zugriff auf ein Dokument sperrt, das durch eine freigegebene Richtlinie geschützt ist, kann nur der Administrator die Zugriffsberechtigungen für dieses Dokument reaktivieren.

**Richtliniensatz-Koordinatoren:** Können Zugriffsberechtigungen für Dokumente sperren oder reaktivieren, die von Richtlinien in ihren Richtliniensätzen geschützt werden.

Wenn Sie Dokumentzugriffsberechtigungen sperren oder reaktivieren, wird die Änderung zu diesen Zeiten wirksam:

* Wenn das Dokument online und geschlossen ist, wird die Änderung wirksam, wenn sich der Empfänger das nächste Mal mit Document Security durch Öffnen eines richtliniengeschützten Dokuments synchronisiert.
* Wenn das Dokument online und geöffnet ist, wird die Änderung beim Schließen des Dokuments durch den Empfänger wirksam.
* Wenn das Dokument offline ist (ohne Internetverbindung verwendet wird, z. B. auf einem Laptop), wird die Änderung bei der nächsten Synchronisierung des Empfängers mit Document Security wirksam.

**Zugriff auf ein richtliniengeschütztes Dokument sperren**

1. Klicken Sie auf der Document Security-Seite auf Dokumente.
1. Aktivieren Sie das Kontrollkästchen neben dem entsprechenden Dokument und klicken Sie auf &quot;Sperren&quot;. Sie können den Zugriff auf mehrere Dokumente gleichzeitig sperren.
1. Wählen Sie eine Nachricht aus, die Benutzern angezeigt werden soll, die versuchen, das Dokument zu öffnen, nachdem es widerrufen wurde:

   * **Allgemeine Nachrich:** Gibt den Benutzer an, der das Dokument gesperrt hat.
   * **Dokument beendet:** Gibt den Benutzer an, der das Dokument beendet hat.
   * **Dokument überarbeitet**: Gibt an, dass der Autor das Dokument überarbeitet hat

1. (Optional) Wenn eine neuere Version des Dokuments verfügbar ist, geben Sie die URL ein und klicken Sie auf Testen , um die URL zu überprüfen.
1. Klicken Sie auf OK und dann erneut auf OK , um zur Seite &quot;Dokumente&quot;zurückzukehren.

**Dokumentzugriffsberechtigungen reaktivieren**

1. Klicken Sie auf der Document Security-Seite auf Dokumente.
1. Klicken Sie in der Dokumentliste auf das entsprechende Dokument.
1. Klicken Sie auf Aufhebung der Sperrung und dann auf OK.

## Auf ein Dokument angewendete Richtlinie wechseln {#switch-a-policy-that-is-applied-to-a-document}

Benutzer, Richtliniensatzkoordinatoren und Administratoren können die Richtlinie wechseln, die auf ein richtliniengeschütztes Dokument angewendet wird (Sie können nur eine Richtlinie auf ein Dokument anwenden). Benutzer können Richtlinien wechseln, die auf ihre eigenen richtliniengeschützten Dokumente angewendet werden, wenn sie die Richtlinie erstellt haben oder wenn die Richtlinie eine freigegebene Richtlinie ist, für die diese Funktion aktiviert ist. Andernfalls muss der Administrator oder Richtliniensatzkoordinator die Richtlinie wechseln. Administratoren können Richtlinien für die richtliniengeschützten Dokumente eines Benutzers wechseln. Richtliniensatzkoordinatoren können Richtlinien aus ihren Richtliniensätzen wechseln.

Wenn Sie eine Richtlinie wechseln, wird die neue Richtlinie wie folgt durchgesetzt:

* Wenn das Dokument online und geschlossen ist, wird die Änderung wirksam, wenn sich der Empfänger das nächste Mal mit Document Security synchronisiert, indem ein richtliniengeschütztes Dokument online geöffnet wird.
* Wenn das Dokument online und geöffnet ist, wird die Änderung beim Schließen des Dokuments durch den Benutzer wirksam.
* Wenn das Dokument offline ist (ohne aktive Internet- oder Netzwerkverbindung wie auf einem Laptop verwendet wird), wird die Änderung angewendet, wenn der Benutzer das nächste Mal eine Synchronisierung mit Document Security durchführt, indem er ein richtliniengeschütztes Dokument online öffnet.

>[!NOTE]
>
>Um den anonymen Zugriff auf ein richtliniengeschütztes Dokument zuzulassen, für das dieser Zugriff derzeit nicht möglich ist, entfernen Sie die vorhandene Richtlinie in der Clientanwendung und wenden Sie dann eine Richtlinie an, die den anonymen Zugriff zulässt. Wenn Sie die Richtlinie wechseln, müssen sich die Benutzer dennoch anmelden, um auf das Dokument zuzugreifen.

1. Klicken Sie auf der Document Security-Seite auf Dokumente.
1. Klicken Sie in der Dokumentliste auf das entsprechende Dokument.
1. Klicken Sie auf Richtlinie wechseln . Eine Liste mit bis zu 100 Richtlinien wird angezeigt.
1. Wenn die gewünschte Richtlinie nicht angezeigt wird, wählen Sie in der Liste &quot;Suchen&quot;den Eintrag &quot;Richtlinienname&quot;oder &quot;Richtlinien-ID&quot;aus, geben Sie den Namen oder die ID ein und klicken Sie auf &quot;Suchen&quot;.
1. Klicken Sie auf eine neue Richtlinie in der Liste.
1. Klicken Sie auf Richtlinie wechseln und dann auf OK , um zur Seite Dokumente zurückzukehren.

## Nach Dokumenten suchen {#search-for-a-document}

Sie können auf der Seite &quot;Dokumente&quot;nach Dokumenten suchen, indem Sie eine Kombination aus Datumsbereichskriterien und den in der Liste verfügbaren Suchkriterien verwenden. Zu diesen Kriterien gehören der Dokumentname, der Richtlinienname oder alle Dokumente.

Einige zusätzliche Suchoptionen stehen nur Administratoren zur Verfügung:

**Dokument-ID:** Eindeutige ID-Nummer, die Document Security dem Dokument zuweist, wenn die Richtlinie angewendet wird.

**Dokumentname:** Name des Dokuments.

**Vermarktername:** Name des Benutzers, der die Richtlinie an das Dokument angehängt hat. Sie können den Benutzer aus allen Domains oder aus einer angegebenen Domain auswählen.

**Richtlinien-ID:** ID-Nummer der Richtlinie, die dem Dokument beigefügt ist.

**Richtlinienname:** Name der Richtlinie, die dem Dokument beigefügt ist.

**Alle Dokumente:** Alle Dokumente, die von Administratoren und Benutzern geschützt sind. Die Verwendung der Option &quot;Alle Dokumente&quot;zur Suche kann zu einer langen Liste von Dokumenten führen.

1. Klicken Sie auf der Document Security-Seite auf Dokumente.
1. Wählen Sie in der Liste &quot;Suchen&quot;die gewünschten Suchkriterien aus.

   Sie können die Kriterien als Dokument-ID, Dokumentname, Herausgebername, Richtlinien-ID, Richtlinienname oder alle Dokumente angeben.

   Wenn Sie den Namen des Herausgebers angeben, klicken Sie auf das Adressbuchsymbol, und geben Sie die Domain an, in der Sie nach dem Benutzer suchen möchten. Klicken Sie auf „OK“, um zur Dokumentsuchseite zurückzukehren.

1. (Optional) Wählen Sie in der Liste &quot;Datum&quot;eine Datumsbereichsoption aus. Wenn Sie &quot;Benutzerdefinierte Datumswerte&quot;auswählen, geben Sie das Datum im Format JJJJ/MM/TT in die angezeigten Felder ein oder geben Sie mit der Datumsauswahl den Datumsbereich an:

   * Klicken Sie auf den Kalender , um die Datumsauswahl zu öffnen.
   * Verwenden Sie die Pfeile, um ein Jahr und einen Monat zu finden.
   * Klicken Sie auf einen Tag des Monats im Kalender.
   * Klicken Sie auf OK , um die Datumsauswahl zu schließen.

1. Klicken Sie auf „Suchen“.

## Dokumentenliste sortieren {#sort-the-document-list}

Sie können die Liste der Dokumente nach Spaltenüberschrift sortieren. Dreieckssymbole neben der Spaltenüberschrift geben an, welche Spalte derzeit zum Sortieren verwendet wird. Ein nach oben zeigendes Dreieck gibt eine aufsteigende Reihenfolge an, während ein nach unten zeigendes Dreieck eine absteigende Reihenfolge angibt.

1. Klicken Sie auf der Document Security-Seite auf Dokumente.
1. Klicken Sie auf die entsprechende Spaltenüberschrift.
1. Um die Sortierreihenfolge zu ändern, klicken Sie erneut auf die Spalte.

## Titelseite zu richtliniengeschützten Dokumenten hinzufügen {#add-cover-page-to-policy-protected-documents}

Wenn es die meisten Nicht-Adobe PDF-Viewer gibt, wird beim Öffnen eines durch Document Security geschützten Dokuments entweder die erste Seite als leere Seite angezeigt oder die Anwendung wird abgebrochen, ohne das Dokument zu öffnen.

Sie können die Unterstützung für Seite 0 (Wrapper Document) verwenden, damit Nicht-Adobe PDF-Viewer ein geschütztes Dokument öffnen und eine Titelseite im Dokument anzeigen können.

>[!NOTE]
>
>Bei der Anzeige solcher Dokumente (die Seite 0 enthalten) in Adobe Reader/Acrobat oder Mobile Reader wird das geschützte Dokument standardmäßig geöffnet.

**Hinzufügen einer Titelseite zu einem richtliniengeschützten Dokument**

Verwenden Sie die folgenden Prozesse in Workbench:

**Schützen
Dokument mit Deckblatt:** Sichert ein PDF-Dokument mit der angegebenen Richtlinie und fügt dem Dokument ein Deckblatt hinzu

**Geschütztes Dokument extrahieren:** Extrahiert das richtliniengeschützte PDF-Dokument aus dem PDF-Dokument mit Deckblatt

Verwenden Sie die folgende Document Security-APIs:

**protectDocumentWithCoverPage:** Sichert ein bestimmtes PDF mit der angegebenen Richtlinie und gibt ein Dokument mit einem Deckblatt und dem geschützten Dokument als Anhang zurück
`//Create a ServiceClientFactory instance ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); //Create a RightsManagementClient object RightsManagementClient rightsClient = new RightsManagementClient(factory); //Reference a PDF document to which a policy is applied FileInputStream fileInputStream = new FileInputStream("C:\\testFile.pdf"); Document inPDF = new Document(fileInputStream); //Reference a Cover Page document FileInputStream coverPageInputStream = new FileInputStream("C:\\CoverPage.pdf"); Document inCoverDoc = new Document(coverPageInputStream); //Create a Document Manager object DocumentManager documentManager = rightsClient.getDocumentManager(); //Apply a policy to the PDF document RMSecureDocumentResult rmSecureDocument = documentManager.protectDocumentWithCoverPage( inPDF, "ProtectedPDF.pdf", "PolicySetName", "PolicyName", null, null, inCoverDoc, true); //Retrieve the policy-protected PDF document Document protectPDF = rmSecureDocument.getProtectedDoc(); //Save the policy-protected PDF document File myFile = new File("C:\\PolicyProtectedDoc.pdf"); protectPDF.copyToFile(myFile);` **extractProtectedDocument:** Extrahiert das geschützte Dokument, das eine Anlage im Dokument mit Deckblatt ist. Das Dokument mit der Titelseite kann mithilfe der Methode „protectDocumentWithCoverPage“ erstellt werden
`//Create a ServiceClientFactory instance ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); //Create a RightsManagementClient object RightsManagementClient rightsClient = new RightsManagementClient(factory); //Reference a protected PDF document with a Cover Page FileInputStream fileInputStream = new FileInputStream("C:\\policyProtectedDocWithCoverPage.pdf"); Document inPDF = new Document(fileInputStream); //Create a Document Manager object DocumentManager documentManager = rightsClient.getDocumentManager(); //Apply a policy to the PDF document Document extractedDoc = documentManager.extractProtectedDocument(inPDF); //Save the policy-protected PDF document File myFile = new File("C:\\PolicyProtectedDoc.pdf"); extractedDoc.copyToFile(myFile);`
