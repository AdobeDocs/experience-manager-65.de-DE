---
title: Steuern des Zugriffs auf richtliniengeschützte Dokumente
description: Erfahren Sie, wie Sie den Zugriff auf Ihre richtliniengeschützten Dokumente anzeigen, verwalten und steuern können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: 0eb6e769-97c1-41ee-8d12-91bece984947
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '2167'
ht-degree: 100%

---

# Steuern des Zugriffs auf richtliniengeschützte Dokumente {#controlling-access-to-policy-protected-documents}

Sie können steuern, wie Empfängerinnen und Empfänger Ihre richtliniengeschützten Dokumente nutzen, und zwar unabhängig vom Ausmaß ihrer Verteilung.

Auf der Seite „Dokumente“ können Sie die folgenden Aufgaben ausführen:

* Suchen und Anzeigen der Details richtliniengeschützter Dokumente. Angezeigt werden der Name des Dokuments, des Herausgebers und der Richtlinie sowie das Datum der Aktivierung der Richtlinie. Wird die Richtlinie, die ein Dokument schützt, gelöscht, wird unter dem Richtliniennamen auch die ID der gelöschten Richtlinie angezeigt. Benutzerinnen und Benutzer können ihre eigenen richtliniengeschützten Dokumente anzeigen und verwalten. Admins können alle richtliniengeschützten Dokumente anzeigen und verwalten.
* Ändern der Details der Richtlinie, die für ein Dokument gilt. Benutzerinnen und Benutzer können ihre eigenen Richtlinien bearbeiten. Admins können freigegebene und persönliche Richtlinien bearbeiten. Richtliniensatzkoordinatorinnen und -koordinatoren können freigegebene Richtlinien in Richtliniensätzen bearbeiten, für die sie Berechtigungen haben. Auf der Seite „Dokumentdetails“ können Sie direkt auf die Richtlinie zugreifen, die einem Dokument zugeordnet ist.
* Den Zugriff auf ein richtliniengeschütztes PDF-Dokument sperren und reaktivieren. Admins können den Zugriff auf Dokumente sperren und reaktivieren. Richtliniensatzkoordinatorinnen und -koordinatoren (mit der Berechtigung zum Verwalten von Dokumenten) können den Zugriff auf richtliniengeschützte Dokumente, die freigegebene Richtlinien in ihren Richtliniensätzen verwenden, sperren und reaktivieren. Benutzerinnen und Benutzer können den Zugriff auf ihre richtliniengeschützten Dokumente sperren, wenn sie die Richtlinie erstellt haben, die das Dokument schützt, oder wenn die Richtlinie eine freigegebene Richtlinie ist, die diesen Vorgang zulässt.
* Die für ein Dokument geltende Richtlinie wechseln. Benutzerinnen und Benutzer, die Richtlinien auf Dokumente anwenden, können die Richtlinie wechseln, wenn sie die Richtlinie erstellt haben, oder wenn die Richtlinie eine freigegebene Richtlinie ist, die diesen Vorgang zulässt. Richtliniensatzkoordinatorinnen und -koordinatoren können Richtlinien in ihren Richtliniensätzen wechseln. Admins können für alle Dokumente geltende Richtlinien wechseln.

Wenn ein Dokument durch eine Richtlinie geschützt ist und Sie Zugriffsberechtigungen sperren oder die geltende Richtlinie wechseln, werden die Änderungen wie folgt wirksam:

* Ist das Dokument online, werden Änderungen sofort übernommen, es sei denn, die Benutzerin bzw. der Benutzer hat das Dokument geöffnet. In diesem Fall muss die Person das Dokument schließen, damit die Änderungen in Kraft treten.
* Wenn eine Empfängerin oder ein Empfänger das Dokument offline verwendet (z. B. auf einem Laptop), werden die Änderungen übernommen, sobald die Empfängerin bzw. der Empfänger das nächste Mal mit der Dokumentensicherheit synchronisiert wird, indem die Person ein richtliniengeschütztes Dokument online öffnet.

## Anzeigen von Informationen zu einem Dokument {#view-information-about-a-document}

Für jedes Dokument auf der Seite „Dokumente“ werden der Name des Dokuments, des Herausgebers und der Richtlinie sowie das Datum angezeigt, an dem das Dokument geschützt wurde. Wurde die Richtlinie, die ein Dokument geschützt hat, gelöscht, wird unter „Richtlinienname“ auch die ID der gelöschten Richtlinie angezeigt.

Auf der (weiter unten beschriebenen) Seite „Dokumentdetails“ können Sie weitere Details zu einem bestimmten Dokument anzeigen:

>[!NOTE]
>
>Klicken Sie auf der Seite „Dokumentdetails“ auf den Link „Richtlinienname“, um auf Richtlinien zuzugreifen, die in Microsoft Outlook automatisch für Empfängerinnen und Empfänger eines Dokuments generiert werden, das an eine E-Mail-Nachricht angehängt wird. Diese Richtlinien werden nicht auf der Seite „Richtlinien“ angezeigt.

**Dokumentname:** Der Name des ausgewählten Dokuments.

**Dokument-ID:** Eine eindeutige Kennung, die Document Security zuweist, wenn eine Richtlinie auf das Dokument angewendet wird. Document Security nutzt diese Nummer zum Nachverfolgen des Dokuments.

**Dokumentstatus:** Status des Dokuments (z. B. aktiv oder gesperrt).

**Vermarkter:** Name des Benutzers, der die Richtlinie an das Dokument angehängt hat.

**Richtlinienname:** Der Name der Richtlinie, die dem Schutz des Dokuments dient. Sie können zum Öffnen der Richtlinie auf ihren Namen klicken. Klicken Sie auf diesen Link, um auf Richtlinien zuzugreifen, die Acrobat für Empfängerinnen und Empfänger eines Dokuments generiert, das in Outlook an eine E-Mail-Nachricht angehängt ist. Diese Richtlinien werden nicht auf der Seite „Richtlinien“ angezeigt.

**Richtlinientyp:** Der Richtlinientyp, der auf das Dokument angewendet wurde.

**Veröffentlichungsdatum:** Das Datum, an dem die Richtlinie auf das Dokument angewendet wurde.

**Zugehörige Iterationen:** Wenn das Dokument verwandte Iterationen hat, erscheint dieses Element auch in der Liste. Klicken Sie auf den Link, um die Liste der verwandten Iterationen für das Dokument anzuzeigen.

Benutzerinnen und Benutzer können Informationen zu ihren geschützten Dokumenten anzeigen. Admins können Informationen zu Dokumenten anzeigen, die beliebige Benutzerinnen oder Benutzer mit einer Richtlinie geschützt haben. Richtliniensatzkoordinatorinnen und -koordinatoren können Informationen zu Dokumenten anzeigen, die von Richtlinien in ihren Richtliniensätzen geschützt werden.

1. Klicken Sie auf der Dokumentensicherheits-Seite auf „Dokumente“.
1. Klicken Sie in der Dokumentliste auf das gewünschte Dokument. Die Seite „Dokumentdetails“ mit detaillierten Informationen zum Dokument wird geöffnet. Diese Seite bietet auch Optionen zum Sperren des Dokumentzugriffs, Wechseln der Richtlinie und Anzeigen dokumentbezogener Ereignisse.

## Anzeigen von verwandten Iterationen eines Dokuments {#view-related-iterations-for-a-document}

Wenn das Tracking verwandter Iterationen aktiviert ist, können Sie die von verschiedenen Benutzenden gespeicherten Versionen eines Dokuments nachverfolgen. Diese Funktion wird nur von bestimmten Anwendungen wie PTC Pro/ENGINEER Wildfire unterstützt.

Diese Funktion ist nützlich, wenn mehrere Benutzerinnen und Benutzer zusammenarbeiten und verschiedene Versionen desselben Dokuments speichern. Die Dokumentensicherheit kann die verschiedenen Iterationen nachverfolgen, weshalb Sie Dokumentinformationen für die verschiedenen Versionen anzeigen können.

Ist diese Funktion aktiviert, können Sie auf der Seite „Dokumente“ die verwandten Iterationen eines Dokuments anzeigen.

1. Rufen Sie die Seite „Dokumentdetails“ für ein Dokument auf. (Siehe [Anzeigen von Informationen zu einem Dokument](controlling-access-policy-protected-documents.md#view-information-about-a-document).)
1. Klicken Sie auf „Verwandte Iterationen anzeigen“. Diese Option ist nur verfügbar, wenn die Funktion aktiviert ist. Die Liste der verwandten Iterationen wird angezeigt. Für jede Iteration werden die folgenden Informationen angezeigt:

   * **Iteration:** Der Dateiname. Er kann vom ursprünglichen Dateinamen abweichen und an seinem Ende ist eine Versionsnummer angefügt.
   * **Herausgeber:** Der Herausgeber des ursprünglichen Dokuments.
   * **Erstellt von:** Der Benutzer, der die Iteration gespeichert hat.
   * **Erstellungsdatum:** Datum und Uhrzeit der Speicherung der Iteration.
   * **Richtlinie:** Die Richtlinie, welche die Iteration schützt. Verschiedene Iterationen können durch unterschiedliche Richtlinien geschützt werden.

1. Um die Seite „Dokumentdetails“ für die jeweilige Iteration anzuzeigen, klicken Sie auf den Dateinamen einer Iteration.

## Sperren und Reaktivieren des Zugriffs auf Dokumente {#revoking-and-reinstating-access-to-documents}

Sie können den Zugriff auf richtliniengeschützte Dokumente sperren und reaktivieren:

**Benutzer:** Können den Zugriff auf Dokumente, die sie schützen, über eigene persönliche Richtlinien oder über freigegebene Richtlinien sperren oder reaktivieren, bei denen die Sperrfunktion für den Benutzer aktiviert ist, der die Richtlinie anwendet. Benutzer, die den Zugriff auf ein Dokument nicht sperren oder eine Richtlinie nicht wechseln können, müssen sich an einen Administrator wenden.

**Administratoren:** Können Zugriffsberechtigungen für sämtliche richtliniengeschützten Dokumente sperren oder reaktivieren, auch für diejenigen, die durch persönliche oder freigegebene Richtlinien geschützt sind. Wenn ein Administrator den Zugriff auf ein Dokument sperrt, das durch eine freigegebene Richtlinie geschützt ist, kann nur der Administrator die Zugriffsberechtigungen für dieses Dokument reaktivieren.

**Richtliniensatz-Koordinatoren:** Können Zugriffsberechtigungen für Dokumente sperren oder reaktivieren, die von Richtlinien in ihren Richtliniensätzen geschützt werden.

Wenn Sie Dokumentzugriffsberechtigungen sperren oder reaktivieren, werden die Änderungen abhängig vom Status des Dokuments zu einem bestimmten Zeitpunkt wie folgt wirksam:

* Wenn das Dokument online und geschlossen ist, wird die Änderung wirksam, wenn sich die Empfängerin bzw. der Empfänger das nächste Mal mit der Dokumentensicherheit durch Öffnen eines richtliniengeschützten Dokuments synchronisiert.
* Wenn das Dokument online und geöffnet ist, wird die Änderung beim Schließen des Dokuments durch die Empfängerin bzw. den Empfänger wirksam.
* Wenn das Dokument offline ist (beispielsweise auf einem Laptop ohne Internet-Verbindung verwendet wird), wird die Änderung übernommen, sobald die Empfängerin oder der Empfänger das Dokument mit der Dokumentensicherheit synchronisiert.

**Sperren des Zugriffs auf ein richtliniengeschütztes Dokument**

1. Klicken Sie auf der Dokumentensicherheits-Seite auf „Dokumente“.
1. Aktivieren Sie das Kontrollkästchen neben dem gewünschten Dokument und klicken Sie auf „Sperren“. Sie können mehrere Dokumente gleichzeitig sperren.
1. Wählen Sie eine Nachricht aus, die allen Benutzenden, die versuchen, das Dokument zu öffnen, nach seiner Sperrung angezeigt werden soll:

   * **Allgemeine Nachrich:** Gibt den Benutzer an, der das Dokument gesperrt hat.
   * **Dokument beendet:** Gibt den Benutzer an, der das Dokument beendet hat.
   * **Dokument überarbeitet**: Gibt die Person an, die das Dokument überarbeitet hat.

1. (Optional) Wenn eine neuere Version des Dokuments verfügbar ist, geben Sie die URL ein und klicken Sie auf „Testen“, um die URL zu überprüfen.
1. Klicken Sie auf „OK“ und anschließend nochmals auf „OK“, um die Seite „Dokumente“ erneut aufzurufen.

**Reaktivieren der Dokumentzugriffsberechtigungen**

1. Klicken Sie auf der Dokumentensicherheits-Seite auf „Dokumente“.
1. Klicken Sie in der Dokumentliste auf das gewünschte Dokument.
1. Klicken Sie auf „Sperre aufheben“ und dann auf „OK“.

## Wechseln einer für ein Dokument geltende Richtlinie {#switch-a-policy-that-is-applied-to-a-document}

Benutzende, Richtliniensatzkoordinatorinnen und -koordinatoren sowie Admins können die für ein richtliniengeschütztes Dokument geltende Richtlinie wechseln (auf ein Dokument kann immer nur eine Richtlinie angewendet werden). Benutzende können Richtlinien wechseln, die für ihre eigenen richtliniengeschützten Dokumente gelten, wenn sie die Richtlinie erstellt haben oder die Richtlinie eine freigegebene Richtlinie ist, die diesen Vorgang zulässt. Andernfalls müssen Admins oder Richtliniensatzkoordinatorinnen bzw -koordinatoren die Richtlinie wechseln. Admins können Richtlinien für richtliniengeschützte Dokumente aller Benutzenden wechseln. Richtliniensatzkoordinatorinnen und -koordinatoren können Richtlinien in ihren Richtliniensätzen wechseln.

Wenn Sie eine Richtlinie wechseln, wird die neue Richtlinie wie folgt aktiviert:

* Wenn das Dokument online und geschlossen ist, wird die Änderung wirksam, wenn sich die Empfängerin bzw. der Empfänger das nächste Mal mit der Dokumentensicherheit durch Öffnen eines richtliniengeschützten Dokuments synchronisiert.
* Wenn das Dokument online und geöffnet ist, wird die Änderung beim Schließen des Dokuments durch die Benutzerin bzw. den Benutzer wirksam.
* Wenn das Dokument offline ist (d. h. ohne aktive Internet- oder Netzwerkverbindung beispielsweise auf einem Laptop verwendet wird), wird die Änderung übernommen, wenn die Empfängerin bzw. der Empfänger das nächste Mal mit der Dokumentensicherheit synchronisiert wird, indem die Person ein richtliniengeschütztes Dokument online öffnet.

>[!NOTE]
>
>Wenn Sie den anonymen Zugriff auf ein richtliniengeschütztes Dokument zulassen möchten, für das dieser Zugriff momentan nicht möglich ist, müssen Sie die vorhandene Richtlinie aus der Client-Anwendung entfernen und anschließend eine Richtlinie anwenden, die den anonymen Zugriff zulässt. Wenn Sie die Richtlinie wechseln, müssen die Benutzenden sich dennoch anmelden, um auf das Dokument zuzugreifen.

1. Klicken Sie auf der Dokumentensicherheits-Seite auf „Dokumente“.
1. Klicken Sie in der Dokumentliste auf das gewünschte Dokument.
1. Klicken Sie auf „Richtlinie wechseln“. Eine Liste mit bis zu 100 Richtlinien wird angezeigt.
1. Wird die gewünschte Richtlinie nicht angezeigt, wählen Sie in der Liste „Suchen“ entweder „Richtlinienname“ oder „Richtlinien-ID“ aus, geben den Namen oder die ID ein und klicken auf „Suchen“.
1. Klicken Sie auf eine neue Richtlinie in der Liste.
1. Klicken Sie auf „Richtlinie wechseln“ und anschließend auf „OK“, um zur Seite „Dokumente“ zurückzukehren. 

## Suche nach Dokumenten {#search-for-a-document}

Auf der Seite „Dokumente“ können Sie Dokumente über eine Kombination aus Datumsbereichsangaben und den in der Liste angegebenen Suchkriterien suchen. Zu diesen Kriterien zählen „Dokumentname“, „Richtlinienname“ und „Alle Dokumente“.

Einige zusätzliche Suchoptionen stehen nur Admins zur Verfügung:

**Dokument-ID:** Eindeutige ID-Nummer, die Document Security dem Dokument zuweist, wenn die Richtlinie angewendet wird.

**Dokumentname:** Name des Dokuments.

**Vermarktername:** Name des Benutzers, der die Richtlinie an das Dokument angehängt hat. Sie können den Benutzer aus allen Domains oder aus einer angegebenen Domain auswählen.

**Richtlinien-ID:** ID-Nummer der Richtlinie, die dem Dokument beigefügt ist.

**Richtlinienname:** Name der Richtlinie, die dem Dokument beigefügt ist.

**Alle Dokumente:** Alle Dokumente, die von Administratoren und Benutzern geschützt sind. Die Suchoption „Alle Dokumente“ kann sehr viele Dokumente zurückgeben.

1. Klicken Sie auf der Dokumentensicherheits-Seite auf „Dokumente“.
1. Wählen Sie in der Liste „Suchen“ die gewünschten Suchkriterien aus.

   Sie können als Kriterien „Dokument-ID“, „Dokumentname“, „Name des Herausgebers“, „Richtlinien-ID“, „Richtlinienname“ oder „Alle Dokumente“ angeben.

   Wenn Sie den Namen des Herausgebers angeben, klicken Sie auf das Adressbuchsymbol, und geben Sie die Domain an, in der Sie nach dem Benutzer suchen möchten. Klicken Sie auf „OK“, um zur Dokumentsuchseite zurückzukehren.

1. (Optional) Wählen Sie in der Liste „Datum“ eine Datumsbereichsoption aus. Wenn Sie „Eigene Daten“ auswählen, geben Sie das Datum im Format TT.MM.JJJJ in die angezeigten Felder ein oder verwenden Sie die Datumsauswahl, um den Datumsbereich anzugeben:

   * Klicken Sie auf den Kalender, um die Datumsauswahl zu öffnen.
   * Bestimmen Sie mithilfe der Pfeilschaltflächen ein Jahr und einen Monat.
   * Klicken Sie auf dem Kalender auf einen Monatstag.
   * Klicken Sie auf „OK“, um die Datumsauswahl zu schließen.

1. Klicken Sie auf „Suchen“.

## Sortieren der Dokumentenliste {#sort-the-document-list}

So können die Liste der Dokumente nach Spaltenüberschrift sortieren. Ein Dreieckssymbol neben der Spaltenüberschrift gibt an, nach welcher Spalte gegenwärtig sortiert wird. Ein nach oben zeigendes Dreieck gibt eine aufsteigende Reihenfolge an, ein nach unten zeigendes Dreieck gibt eine absteigende Reihenfolge an.

1. Klicken Sie auf der Dokumentensicherheits-Seite auf „Dokumente“.
1. Klicken Sie auf die gewünschte Spaltenüberschrift.
1. Um die Sortierreihenfolge zu ändern, klicken Sie nochmals auf die Spaltenüberschrift.

## Hinzufügen von Titelseiten zu Dokumenten, die durch Richtlinien geschützt sind {#add-cover-page-to-policy-protected-documents}

Beim Öffnen eines durch Dokumentensicherheit geschützten Dokuments wird bei den meisten PDF-Viewern, die nicht von Adobe sind, entweder die erste Seite als leere Seite angezeigt oder die Anwendung bricht ab, ohne das Dokument zu öffnen.

Sie können die Unterstüzung für Seite 0 (Wrapper-Dokument) verwenden, damit Nicht-Adobe-PDF-Viewer ein geschütztes Dokument öffnen und eine Titelseite im Dokument anzeigen können.

>[!NOTE]
>
>Beim Anzeigen derartiger Dokumente (mit Seite 0) in Adobe Reader/Acrobat oder Mobile Reader wird das geschützte Dokument standardmäßig geöffnet.

**Hinzufügen von Titelseiten zu Dokumenten, die durch Richtlinien geschützt sind**

Verwenden Sie die folgenden Vorgänge in Workbench:

**Schützen
Dokument mit Deckblatt:** Sichert ein PDF-Dokument mit der angegebenen Richtlinie und fügt dem Dokument ein Deckblatt hinzu

**Geschütztes Dokument extrahieren:** Extrahiert das richtliniengeschützte PDF-Dokument aus dem PDF-Dokument mit Deckblatt

Verwenden Sie die folgende Document Security-APIs:

**protectDocumentWithCoverPage:** Sichert ein bestimmtes PDF mit der angegebenen Richtlinie und gibt ein Dokument mit einem Deckblatt und dem geschützten Dokument als Anhang zurück
`//Create a ServiceClientFactory instance ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); //Create a RightsManagementClient object RightsManagementClient rightsClient = new RightsManagementClient(factory); //Reference a PDF document to which a policy is applied FileInputStream fileInputStream = new FileInputStream("C:\\testFile.pdf"); Document inPDF = new Document(fileInputStream); //Reference a Cover Page document FileInputStream coverPageInputStream = new FileInputStream("C:\\CoverPage.pdf"); Document inCoverDoc = new Document(coverPageInputStream); //Create a Document Manager object DocumentManager documentManager = rightsClient.getDocumentManager(); //Apply a policy to the PDF document RMSecureDocumentResult rmSecureDocument = documentManager.protectDocumentWithCoverPage( inPDF, "ProtectedPDF.pdf", "PolicySetName", "PolicyName", null, null, inCoverDoc, true); //Retrieve the policy-protected PDF document Document protectPDF = rmSecureDocument.getProtectedDoc(); //Save the policy-protected PDF document File myFile = new File("C:\\PolicyProtectedDoc.pdf"); protectPDF.copyToFile(myFile);` **extractProtectedDocument:** Extrahiert das geschützte Dokument, das eine Anlage im Dokument mit Deckblatt ist. Das Dokument mit der Titelseite kann mithilfe der Methode „protectDocumentWithCoverPage“ erstellt werden
`//Create a ServiceClientFactory instance ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); //Create a RightsManagementClient object RightsManagementClient rightsClient = new RightsManagementClient(factory); //Reference a protected PDF document with a Cover Page FileInputStream fileInputStream = new FileInputStream("C:\\policyProtectedDocWithCoverPage.pdf"); Document inPDF = new Document(fileInputStream); //Create a Document Manager object DocumentManager documentManager = rightsClient.getDocumentManager(); //Apply a policy to the PDF document Document extractedDoc = documentManager.extractProtectedDocument(inPDF); //Save the policy-protected PDF document File myFile = new File("C:\\PolicyProtectedDoc.pdf"); extractedDoc.copyToFile(myFile);`
