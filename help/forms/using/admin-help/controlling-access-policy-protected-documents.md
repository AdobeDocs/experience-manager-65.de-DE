---
title: Steuern des Zugriffs auf richtliniengeschützte Dokumente
seo-title: Steuern des Zugriffs auf richtliniengeschützte Dokumente
description: Erfahren Sie, wie Sie den Zugriff auf ihre richtliniengeschützten Dokumente anzeigen, verwalten und steuern können.
seo-description: Erfahren Sie, wie Sie den Zugriff auf ihre richtliniengeschützten Dokumente anzeigen, verwalten und steuern können.
uuid: 2d9f95e9-e4ee-47e2-988e-a191d1d1d264
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: f34058c3-384a-4b73-a386-5bc9125acbf8
feature: Document Security
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2190'
ht-degree: 85%

---


# Steuern des Zugriffs auf richtliniengeschützte Dokumente {#controlling-access-to-policy-protected-documents}

Sie können steuern, wie Empfänger Ihre richtliniengeschützten Dokumente nutzen, und zwar unabhängig vom Ausmaß ihrer Verteilung.

Auf der Seite „Dokumente“ können Sie die folgenden Aufgaben ausführen:

* Suchen und Anzeigen der Details richtliniengeschützter Dokumente. Angezeigt werden der Name des Dokuments, des Herausgebers und der Richtlinie sowie das Datum der Aktivierung der Richtlinie. Wird die Richtlinie, die ein Dokument schützt, gelöscht, wird unter dem Richtliniennamen auch die ID der gelöschten Richtlinie angezeigt. Benutzer können ihre eigenen richtliniengeschützten Dokumente anzeigen und verwalten. Administratoren können alle richtliniengeschützten Dokumente anzeigen und verwalten.
* Ändern der Details der Richtlinie, die für ein Dokument gilt. Benutzer können ihre eigenen Richtlinien bearbeiten. Administratoren können freigegebene und persönliche Richtlinien bearbeiten. Richtliniensatzkoordinatoren können freigegebene Richtlinien in Richtliniensätzen bearbeiten, für die sie Berechtigungen haben. Auf der Seite „Dokumentdetails“ können Sie direkt auf die Richtlinie zugreifen, die einem Dokument zugeordnet ist.
* Den Zugriff auf ein richtliniengeschütztes PDF-Dokument sperren und reaktivieren. Administratoren können den Zugriff auf Dokumente sperren und reaktivieren. Richtliniensatzkoordinatoren (mit der Berechtigung zum Verwalten von Dokumenten) können den Zugriff auf richtliniengeschützte Dokumente, die freigegebene Richtlinien in ihren Richtliniensätzen verwenden, sperren und reaktivieren. Benutzer können den Zugriff auf ihre richtliniengeschützten Dokumente sperren, wenn sie die Richtlinie erstellt haben, die das Dokument schützt, oder die Richtlinie eine freigegebene Richtlinie ist, die diesen Vorgang zulässt.
* Die für ein Dokument geltende Richtlinie wechseln. Benutzer, die Richtlinien auf Dokumente anwenden, können die Richtlinie wechseln, wenn sie die Richtlinie erstellt haben, die das Dokument schützt, oder die Richtlinie eine freigegebene Richtlinie ist, die diesen Vorgang zulässt. Richtliniensatzkoordinatoren können Richtlinien in ihren Richtliniensätzen wechseln. Administratoren können für alle Dokumente geltende Richtlinien wechseln.

Wenn ein Dokument durch eine Richtlinie geschützt ist und Sie Zugriffsberechtigungen sperren oder die geltende Richtlinie wechseln, werden die Änderungen wie folgt wirksam:

* Ist das Dokument online, werden Änderungen sofort übernommen, es sei denn, der Benutzer hat das Dokument geöffnet. In diesem Fall muss der Benutzer das Dokument schließen, damit die Änderungen in Kraft treten.
* Wenn ein Empfänger das Dokument offline verwendet (z. B. auf einem Laptop), werden die Änderungen bei der nächsten Synchronisierung mit Document Security durch Öffnen eines beliebigen richtliniengeschützten Dokuments wirksam.

## Informationen zu einem Dokument anzeigen {#view-information-about-a-document}

Für jedes Dokument auf der Seite „Dokumente“ werden der Name des Dokuments, des Herausgebers und der Richtlinie sowie das Datum angezeigt, an dem das Dokument geschützt wurde. Wurde die Richtlinie, die ein Dokument geschützt hat, gelöscht, wird unter „Richtlinienname“ auch die ID der gelöschten Richtlinie angezeigt.

Auf der (weiter unten beschriebenen) Seite „Dokumentdetails“ können Sie weitere Details zu einem bestimmten Dokument anzeigen.

>[!NOTE]
>
>Sie müssen auf der Seite „Dokumentdetails“ auf den Link „Richtlinienname“ klicken, um auf Richtlinien zuzugreifen, die in Microsoft Outlook automatisch für Empfänger eines Dokuments generiert wurden, das an eine E-Mail-Nachricht angehängt wurde. Diese Richtlinien werden nicht auf der Seite „Richtlinien“ angezeigt.

**Name des Dokuments:** Der Name des ausgewählten Dokuments.

**Dokument-ID:** Eine eindeutige ID, die von Dokument Security zugewiesen wird, wenn eine Richtlinie auf das Dokument angewendet wird. Document Security nutzt diese Nummer zum Nachverfolgen des Dokuments.

**Dokument-Status:** Status des Dokuments (z. B. aktiv oder gesperrt)

**Herausgeber:** Name des Benutzers, der die Richtlinie an das Dokument angehängt hat.

**Richtlinienname:** Der Name der Richtlinie, die zum Schutz des Dokuments verwendet wird. Sie können zum Öffnen der Richtlinie auf den Namen klicken. Über diesen Hyperlink können Sie auf Richtlinien zugreifen, die Acrobat für Empfänger eines Dokuments generiert, das in Outlook an eine E-Mail-Nachricht angehängt ist. Diese Richtlinien werden nicht auf der Seite „Richtlinien“ angezeigt.

**Richtlinientyp:** Der Richtlinientyp, der auf das Dokument angewendet wurde.

**Veröffentlichungsdatum:** Das Datum, an dem die Richtlinie auf das Dokument angewendet wurde.

**Verwandte Iterationen:** Wenn das Dokument verwandte Iterationen aufweist, wird dieses Element auch in der Liste angezeigt. Klicken Sie auf den Hyperlink, um die Liste der verwandten Iterationen für das Dokument anzuzeigen.

Benutzer können Informationen zu ihren geschützten Dokumenten anzeigen. Administratoren können Informationen zu Dokumenten anzeigen, die beliebige Benutzer mit einer Richtlinie geschützt haben. Richtliniensatzkoordinatoren können Informationen zu Dokumenten anzeigen, die von Richtlinien in ihren Richtliniensätzen geschützt werden.

1. Klicken Sie auf der Document Security-Seite auf „Dokumente“.
1. Klicken Sie in der Dokumentliste auf das gewünschte Dokument. Die Seite „Dokumentdetails“ wird mit detaillierten Informationen zum Dokument angezeigt. Diese Seite bietet auch Optionen zum Sperren des Dokumentzugriffs, Wechseln der Richtlinie und Anzeigen dokumentbezogener Ereignisse.

## Verwandte Iterationen eines Dokuments anzeigen  {#view-related-iterations-for-a-document}

Wenn das Nachverfolgen verwandter Iterationen aktiviert ist, können Sie von verschiedenen Benutzern gespeicherte Versionen eines Dokuments nachverfolgen. Diese Funktion wird nur von bestimmten Anwendungen wie PTC Pro/ENGINEER Wildfire unterstützt.

Diese Funktion ist nützlich, wenn mehrere Benutzer zusammenarbeiten und verschiedene Versionen desselben Dokuments speichern. Document Security kann die verschiedenen Iterationen nachverfolgen, weshalb Sie Dokumentinformationen für die verschiedenen Versionen anzeigen können.

Ist diese Funktion aktiviert, können Sie auf der Seite „Dokumente“ die verwandten Iterationen eines Dokuments anzeigen.

1. Rufen Sie die Seite „Dokumentdetails“ für ein Dokument auf. (Siehe [Informationen zu einem Dokument anzeigen](controlling-access-policy-protected-documents.md#view-information-about-a-document).)
1. Klicken Sie auf „Verwandte Iterationen anzeigen“. Diese Option ist nur verfügbar, wenn die Funktion aktiviert ist. Die Liste verwandter Iterationen wird angezeigt. Für jede Iteration werden die folgenden Informationen angezeigt:

   * **Iteration:** Der Dateiname. Er kann vom ursprünglichen Dateinamen abweichen und an seinem Ende ist eine Versionsnummer angefügt.
   * **Herausgeber:** Der Herausgeber des ursprünglichen Dokuments.
   * **Erstellt von:** Der Benutzer, der die Iteration gespeichert hat.
   * **Erstellungsdatum:** Datum und Uhrzeit der Speicherung der Iteration.
   * **Richtlinie:** Die Richtlinie, welche die Iteration schützt. Verschiedene Iterationen können durch unterschiedliche Richtlinien geschützt werden.

1. Um die Seite „Dokumentdetails“ für die jeweilige Iteration anzuzeigen, klicken Sie auf den Dateinamen einer Iteration.

## Zugriff auf Dokumente sperren und reaktivieren  {#revoking-and-reinstating-access-to-documents}

Sie können den Zugriff auf richtliniengeschützte Dokumente sperren und reaktivieren:

**Benutzer:** Kann den Zugriff auf Dokumente, die sie schützen, mit ihren eigenen persönlichen Richtlinien oder freigegebenen Richtlinien sperren oder reaktivieren, für die die Sperrfunktion für den Benutzer aktiviert ist, der die Richtlinie anwendet. Benutzer, die den Zugriff auf ein Dokument nicht sperren oder eine Richtlinie nicht wechseln können, müssen sich an einen Administrator wenden.

**Administratoren:** Können Zugriffsberechtigungen auf richtliniengeschützte Dokument sperren oder reaktivieren, einschließlich solcher, die durch persönliche oder freigegebene Richtlinien geschützt sind. Wenn ein Administrator den Zugriff auf ein Dokument sperrt, das durch eine freigegebene Richtlinie geschützt ist, kann nur der Administrator die Zugriffsberechtigungen für dieses Dokument reaktivieren.

**Richtliniensatzkoordinatoren:** Können Zugriffsberechtigungen für Dokumente, die von Richtlinien in ihren Richtliniensätzen geschützt werden, widerrufen oder reaktivieren.

Wenn Sie Dokumentzugriffsberechtigungen sperren oder reaktivieren, werden die Änderungen abhängig vom Status des Dokuments wirksam.

* Wenn das Dokument online und geschlossen ist, wird die Änderung wirksam, wenn sich der Empfänger das nächste Mal mit Document Security durch Öffnen eines richtliniengeschützten Dokuments synchronisiert.
* Wenn das Dokument online und geöffnet ist, wird die Änderung beim Schließen des Dokuments durch den Empfänger wirksam.
* Wenn das Dokument offline ist (ohne Internetverbindung beispielsweise auf einem Laptop verwendet wird), wird die Änderung übernommen, sobald der Empfänger das Dokument mit Document Security synchronisiert.

**Zugriff auf ein richtliniengeschütztes Dokument sperren**

1. Klicken Sie auf der Document Security-Seite auf „Dokumente“.
1. Aktivieren Sie das Kontrollkästchen neben dem gewünschten Dokument und klicken Sie auf „Sperren“. Sie können mehrere Dokumente gleichzeitig sperren.
1. Wählen Sie eine Nachricht aus, die Benutzern, die versuchen, das Dokument zu öffnen, nach seiner Sperrung angezeigt werden soll:

   * **Allgemeine Nachrich:** Gibt den Benutzer an, der das Dokument gesperrt hat.
   * **Dokument beendet:** Gibt den Benutzer an, der das Dokument beendet hat.
   * **Dokument überarbeitet**: Gibt den Benutzer an, der das Dokument überarbeitet hat.

1. (Optional) Wenn eine neuere Version des Dokuments verfügbar ist, geben Sie die URL ein und klicken Sie auf „Testen“, um die URL zu überprüfen.
1. Klicken Sie auf „OK“ und anschließend nochmals auf „OK“, um die Seite „Dokumente“ erneut aufzurufen.

**Dokumentzugriffsberechtigungen reaktivieren**

1. Klicken Sie auf der Document Security-Seite auf „Dokumente“.
1. Klicken Sie in der Dokumentliste auf das gewünschte Dokument.
1. Klicken Sie auf „Sperre aufheben“ und dann auf „OK“.

## Eine für ein Dokument geltende Richtlinie wechseln  {#switch-a-policy-that-is-applied-to-a-document}

Benutzer, Richtliniensatzkoordinatoren und Administratoren können die für ein richtliniengeschütztes Dokument geltende Richtlinie wechseln (auf ein Dokument kann immer nur eine Richtlinie angewendet werden). Benutzer können Richtlinien wechseln, die für ihre eigenen richtliniengeschützten Dokumente gelten, wenn sie die Richtlinie erstellt haben oder die Richtlinie eine freigegebene Richtlinie ist, die diesen Vorgang zulässt. Andernfalls muss der Administrator oder Richtliniensatzkoordinator die Richtlinie wechseln. Administratoren können Richtlinien für richtliniengeschützte Dokumente aller Benutzer wechseln. Richtliniensatzkoordinatoren können Richtlinien in ihren Richtliniensätzen wechseln.

Wenn Sie eine Richtlinie wechseln, wird die neue Richtlinie wie folgt aktiviert:

* Wenn das Dokument online und geschlossen ist, wird die Änderung wirksam, wenn sich der Empfänger das nächste Mal mit Document Security durch Öffnen eines richtliniengeschützten Dokuments synchronisiert.
* Wenn das Dokument online und geöffnet ist, wird die Änderung beim Schließen des Dokuments durch den Benutzer wirksam.
* Wenn das Dokument offline ist (ohne aktive Internet- oder Netzwerkverbindung beispielsweise auf einem Laptop verwendet wird), wird die Änderung übernommen, wenn der Empfänger sich mit Document Security synchronisiert, indem er ein richtliniengeschütztes Dokument online öffnet.

>[!NOTE]
>
>Wenn Sie den anonymen Zugriff auf ein richtliniengeschütztes Dokument zulassen möchten, für das dieser Zugriff momentan nicht möglich ist, müssen Sie die vorhandene Richtlinie aus der Clientanwendung entfernen und anschließend eine Richtlinie anwenden, die den anonymen Zugriff zulässt. Wenn Sie die Richtlinie wechseln, müssen die Benutzer sich dennoch anmelden, um auf das Dokument zuzugreifen.

1. Klicken Sie auf der Document Security-Seite auf „Dokumente“.
1. Klicken Sie in der Dokumentliste auf das gewünschte Dokument.
1. Klicken Sie auf „Richtlinie wechseln“. Eine Liste mit bis zu 100 Richtlinien wird angezeigt.
1. Wird die gewünschte Richtlinie nicht angezeigt, wählen Sie in der Liste „Suchen“ entweder „Richtlinienname“ oder „Richtlinien-ID“ aus, geben den Namen oder die ID ein und klicken auf „Suchen“.
1. Klicken Sie auf eine neue Richtlinie in der Liste.
1. Klicken Sie auf „Richtlinie wechseln“ und anschließend auf „OK“, um zur Seite „Dokumente“ zurückzukehren.

## Nach einem Dokument suchen  {#search-for-a-document}

Auf der Seite „Dokumente“ können Sie Dokumente über eine Kombination aus Datumsbereichsangaben und den in der Liste angegebenen Suchkriterien suchen. Zu diesen Kriterien zählen „Dokumentname“, „Richtlinienname“ und „Alle Dokumente“.

Einige zusätzliche Suchoptionen stehen nur Administratoren zur Verfügung:

**Dokument-ID:** Eindeutige ID-Nummer, die Dokument Security dem Dokument zuweist, wenn die Richtlinie angewendet wird.

**Name des Dokuments:** Name des Dokuments.

**Name des Herausgebers:** Name des Benutzers, der die Richtlinie an das Dokument angehängt hat. Sie können den Benutzer aus allen Domänen oder aus einer angegebenen Domäne auswählen.

**Richtlinie-ID:** ID-Nummer der Richtlinie, die an das Dokument angehängt ist.

**Richtlinienname:** Name der Richtlinie, die an das Dokument angehängt wird.

**Alle Dokumente:** Alle Dokumente, die von Administratoren und Benutzern geschützt werden. Die Suchoption „Alle Dokumente“ kann sehr viele Dokumente zurückgeben.

1. Klicken Sie auf der Document Security-Seite auf „Dokumente“.
1. Wählen Sie in der Liste „Suchen“ die gewünschten Suchkriterien aus.

   Sie können als Kriterien „Dokument-ID“, „Dokumentname“, „Name des Herausgebers“, „Richtlinien-ID“, „Richtlinienname“ oder „Alle Dokumente“ angeben.

   Wenn Sie den Namen des Herausgebers angeben, klicken Sie auf das Adressbuchsymbol, und geben Sie die Domäne an, in der Sie nach dem Benutzer suchen möchten. Klicken Sie auf „OK“, um zur Dokumentsuchseite zurückzukehren.

1. (Optional) Wählen Sie in der Liste „Datum“ eine Datumsbereichsoption aus. Wenn Sie „Eigene Daten“ auswählen, geben Sie das Datum im Format TTMMJJJJ in die angezeigten Felder ein oder verwenden Sie die Datumsauswahl, um den Datumsbereich anzugeben:

   * Klicken Sie auf den Kalender, um die Datumsauswahl zu öffnen.
   * Bestimmen Sie über die Pfeilschaltflächen ein Jahr und einen Monat.
   * Klicken Sie auf dem Kalender auf einen Monatstag.
   * Klicken Sie auf „OK“, um die Datumsauswahl zu schließen.

1. Klicken Sie auf „Suchen“.

## Dokumentenliste sortieren  {#sort-the-document-list}

So können die Liste der Dokumente nach Spaltenüberschrift sortieren. Ein Dreieckssymbol neben der Spaltenüberschrift gibt an, nach welcher Spalte gegenwärtig sortiert wird. Ein nach oben zeigendes Dreieck gibt eine aufsteigende Reihenfolge an. Ein nach unten zeigendes Dreieck gibt eine absteigende Reihenfolge an.

1. Klicken Sie auf der Document Security-Seite auf „Dokumente“.
1. Klicken Sie auf die gewünschte Spaltenüberschrift.
1. Um die Sortierreihenfolge zu ändern, klicken Sie nochmals auf die Spaltenüberschrift.

## Hinzufügen von Titelseiten, die durch Richtlinien geschützt sind  {#add-cover-page-to-policy-protected-documents}

Beim Öffnen eines durch Document Security geschützten Dokuments wird bei den meisten Nicht PDF Viewern von Adobe entweder die erste Seite als leere Seite angezeigt oder die Anwendung bricht ab, ohne das Dokument zu öffnen.

Sie können die Seite 0-Support (Wrapper-Dokument) verwenden, damit Nicht-Adobe-PDF Viewer ein geschütztes Dokument öffnen und eine Titelseite im Dokument anzeigen können.

>[!NOTE]
>
>Beim Anzeigen derartiger Dokumente (mit Seite 0) in Adobe Reader/Acrobat oder Mobile Reader wird das geschützte Dokument standardmäßig geöffnet.

**Hinzufügen von Titelseiten, die durch Richtlinien geschützt sind**

Verwenden Sie die folgenden Vorgänge in Workbench:

**Protect-Dokument mit Titelseite:** Sichert ein PDF-Dokument mit der angegebenen Richtlinie und fügt dem Dokument eine Titelseite hinzu

**Geschütztes Dokument extrahieren:** Extrahiert das richtliniengeschützte PDF-Dokument aus dem PDF-Dokument mit Titelseite

Verwenden Sie die folgende Document Security-APIs:

**protectDocumentWithCoverPage:** Sichert eine bestimmte PDF-Datei mit der angegebenen Richtlinie und gibt ein Dokument mit einer Titelseite und dem geschützten Dokument als Anhang 
`//Create a ServiceClientFactory instance ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); //Create a RightsManagementClient object RightsManagementClient rightsClient = new RightsManagementClient(factory); //Reference a PDF document to which a policy is applied FileInputStream fileInputStream = new FileInputStream("C:\\testFile.pdf"); Document inPDF = new Document(fileInputStream); //Reference a Cover Page document FileInputStream coverPageInputStream = new FileInputStream("C:\\CoverPage.pdf"); Document inCoverDoc = new Document(coverPageInputStream); //Create a Document Manager object DocumentManager documentManager = rightsClient.getDocumentManager(); //Apply a policy to the PDF document RMSecureDocumentResult rmSecureDocument = documentManager.protectDocumentWithCoverPage( inPDF, "ProtectedPDF.pdf", "PolicySetName", "PolicyName", null, null, inCoverDoc, true); //Retrieve the policy-protected PDF document Document protectPDF = rmSecureDocument.getProtectedDoc(); //Save the policy-protected PDF document File myFile = new File("C:\\PolicyProtectedDoc.pdf"); protectPDF.copyToFile(myFile);` **extractProtectedDocument zurück:** Extrahiert das geschützte Dokument, das eine Anlage im Dokument mit Titelseite ist. Das Dokument mit der Titelseite kann mithilfe der Methode „protectDocumentWithCoverPage“ erstellt werden
`//Create a ServiceClientFactory instance ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); //Create a RightsManagementClient object RightsManagementClient rightsClient = new RightsManagementClient(factory); //Reference a protected PDF document with a Cover Page FileInputStream fileInputStream = new FileInputStream("C:\\policyProtectedDocWithCoverPage.pdf"); Document inPDF = new Document(fileInputStream); //Create a Document Manager object DocumentManager documentManager = rightsClient.getDocumentManager(); //Apply a policy to the PDF document Document extractedDoc = documentManager.extractProtectedDocument(inPDF); //Save the policy-protected PDF document File myFile = new File("C:\\PolicyProtectedDoc.pdf"); extractedDoc.copyToFile(myFile);`