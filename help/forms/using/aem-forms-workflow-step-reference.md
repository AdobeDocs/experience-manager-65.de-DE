---
title: Formularzentrierte Workflows in OSGi - Schritt-Referenz
seo-title: Forms-centric workflow on OSGi - Step Reference
description: Der formularzentrierte Workflow in OSGi-Schritten ermöglicht das schnelle Erstellen adaptiver formularbasierter Workflows.
seo-description: Forms-centric workflow on OSGi steps allow you rapidly build adaptive forms based workflows.
uuid: 6f791c45-0e35-4c55-9106-5340caab94b7
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: f0a5588d-f210-4f04-bc35-b62834f90ab1
docset: aem65
exl-id: 470fcfda-dfde-437c-b539-d5af1e13a7d6
source-git-commit: de7b1d2d0f3863f9554b346204c18cc57d4bf814
workflow-type: tm+mt
source-wordcount: '7575'
ht-degree: 98%

---

# Formularzentrierte Workflows in OSGi - Schritt-Referenz {#forms-centric-workflow-on-osgi-step-reference}

Mit Workflow-Modelle können Sie eine Business-Logik in einen automatisierten, sich wiederholenden Prozess umwandeln. Anhand eines Modells können Sie eine Reihe von Schritten definieren und ausführen. Sie können auch Modelleigenschaften definieren, um beispielsweise festzulegen, ob es sich um einen Übergangs-Workflow oder einen Workflow mit mehreren Ressourcen handelt. Sie können [verschiedene AEM-Workflow-Schritte in ein Modell aufnehmen, um die Business-Logik zu erzielen](/help/sites-developing/workflows-models.md#extending-aem).

## Schritte für den Forms-Workflow {#forms-workflow-steps}

Schritte für den Forms-Workflow führen AEM Forms-spezifische Vorgänge in einem AEM-Workflow durch. Diese Schritte ermöglichen das schnelle Erstellen adaptiver formularzentrierter Workflows auf OSGi. Diese Workflows können für die Entwicklung grundlegender Überprüfungs- und Genehmigungs-Workflows sowie interner und firmenübergreifender Geschäftsprozesse verwendet werden. Sie können die Forms-Workflow-Schritte außerdem verwenden, um Document Services zu starten, Adobe Sign-Signatur-Workflow zu integrieren und andere AEM Forms-Vorgänge auszuführen. Sie benötigen das [AEM Forms Add-On](https://www.adobe.com/go/learn_aemforms_documentation_63_de), um diese Schritte in einem Workflow zu verwenden.

Durch Forms-zentrierte Workflow-Schritte werden AEM Forms-spezifische Vorgänge in einem AEM-Workflow ausgeführt. Mit diesen Schritten können Sie schnell einen auf adaptiven Formularen basierenden Forms-zentrierten Workflow auf OSGi erstellen. Diese Workflows können für die Entwicklung grundlegender Überprüfungs- und Genehmigungs-Workflows, interner und „Across-the-Firewall“-Geschäftsprozesse verwendet werden.

>[!NOTE]
>
>Wenn das Workflow-Modell für einen externen Speicher markiert ist, können Sie für alle Schritte des Forms-Workflows nur die Variablenoption zum Speichern oder Abrufen von Datendateien und Anlagen auswählen.

## Schritt „Aufgabe zuweisen“ {#assign-task-step}

Der Schritt „Aufgaben zuweisen“ erstellt eine Aufgabe und weist sie einem Benutzer oder einer Gruppe zu. Zusammen mit der Zuweisung der Aufgabe gibt die Komponente außerdem das adaptive Formular oder die nicht interaktive PDF-Datei für die Aufgabe an. Das adaptive Formular ist erforderlich, damit die Benutzer Eingaben vornehmen können, und die nicht interaktive PDF-Datei oder ein schreibgeschütztes adaptives Formular wird in Workflows verwendet, die nur zur Prüfung dienen.

Sie können mit dieser Komponente auch das Verhalten der Aufgabe steuern. Beispielsweise das Erstellen eines automatischen Datensatzdokuments, die Zuweisung der Aufgabe zu einem bestimmten Benutzer oder einer Gruppe, das Angeben des Pfads der gesendeten Daten, das Angeben des Pfads der Daten, die im Voraus ausgefüllt werden sollen und das Angeben der Standardaktionen. Der Schritt „Aufgabe zuweisen“ hat folgende Eigenschaften:

* **Titel:** Bezeichnung der Aufgabe. Der Titel wird im AEM-Posteingang angezeigt.
* **Beschreibung:** Erläuterung der Vorgänge, die in der Aufgabe ausgeführt werden. Diese Informationen sind für andere Prozessentwickler nützlich, wenn Sie in einer gemeinsamen Entwicklungsumgebung arbeiten.

* **Miniaturbildpfad:** Pfad des Aufgabenminiaturbilds. Wenn kein Pfad angegeben ist, wird für ein adaptives Formular das Standardminiaturbild angezeigt und für das Datensatzdokument wird ein Standardsymbol angezeigt.
* **Workflow-Phase:** Ein Workflow kann mehrere Phasen enthalten. Diese werden im AEM-Posteingang angezeigt. Sie können diese Schritte in den Eigenschaften des Modells definieren (Sidekick > Seite > Seiteneigenschaften > Schritte).
* **Priorität:** Die ausgewählte Priorität wird in der AEM Inbox angezeigt. Die verfügbaren Optionen sind „Hoch“, „Mittel“ und „Niedrig“. Der Standardwert ist „Mittel“.
* **Fälligkeitsdatum:** Geben Sie die Anzahl der Tage oder Stunden an, nach denen die Aufgabe als „überfällig“ markiert wird. Wenn Sie **Aus** wählen, dann wird die Aufgabe nie als „überfällig“ markiert. Sie können auch einen Zeitüberschreitungs-Handler angeben, um bestimmte Aufgaben auszuführen, nachdem die Aufgabe überfällig ist.

* **Tage:** Die Anzahl der Tage, nach denen die Aufgabe abgeschlossen werden soll. Die Anzahl der Tage wird gezählt, nachdem die Aufgabe einem Benutzer zugewiesen wurde. Wenn eine Aufgabe nicht abgeschlossen wurde und die Anzahl der Tage im Feld „Tage“ überschreitet, wird bei Auswahl dieser Option nach den fälligen Tagen ein Zeitüberschreitungshandler ausgelöst.
* **Stunden:** Die Anzahl der Tage, innerhalb derer die Aufgabe abgeschlossen werden soll. Die Anzahl der Stunden wird gezählt, nachdem die Aufgabe einem Benutzer zugewiesen wurde. Wenn eine Aufgabe nicht abgeschlossen und die Anzahl der Stunden im Feld „Stunden“ überschritten wurde, wird bei Auswahl dieser Option nach der entsprechenden Stundenanzahl ein Zeitüberschreitungshandler ausgelöst.
* **Zeitüberschreitung nach Fälligkeitsdatum:** Wählen Sie diese Option, um das Auswahlfeld „Zeitüberschreitungshandler“ zu aktivieren.
* **Zeitüberschreitungshandler:** Wählen Sie das Skript aus, das ausgeführt werden soll, wenn der Schritt „Aufgabe zuweisen“ das Fälligkeitsdatum überschreitet. Skripte, die im CRX-Repository unter [apps]/fd/dashboard/scripts/timeoutHandler abgelegt werden, stehen zur Auswahl. Der angegebene Pfad existiert nicht im CRX-Repository. Ein Administrator erstellt den Pfad, bevor er ihn verwendet.
* **Markieren Sie Aktion und Kommentar aus der letzten Aufgabe in „Aufgabendetails“:** Wählen Sie diese Option, um die letzte ausgeführte Aktion und den Kommentar, der im Abschnitt „Aufgabendetail“ einer Aufgabe erhalten wurde, anzuzeigen.
* **Typ:** Wählen Sie den Typ des Dokuments, das ausgefüllt werden soll, wenn der Workflow gestartet wird. Sie können ein adaptives Formular, ein schreibgeschütztes adaptives Formular, ein nicht interaktives PDF-Dokument, die Agenten-Benutzeroberfläche für interaktive Kommunikation oder ein Dokument für interaktive Kommunikation über einen Web-Kanal auswählen.
* **Adaptives Formular verwenden**: Geben Sie die Methode zum Suchen des adaptiven Eingabeformulars an. Diese Option ist verfügbar, wenn Sie in der Dropdownliste „Typ“ die Option „Adaptives Formular“ oder „Schreibgeschütztes adaptives Formular“ auswählen. Sie können das adaptive Formular verwenden, das an den Workflow übermittelt wurde, in einem absoluten Pfad verfügbar ist oder in einem Pfad in einer Variablen verfügbar ist. Sie können eine Variable des Typs „Zeichenfolge“ verwenden, um den Pfad anzugeben.\
   Sie können mehrere adaptive Formulare mit einem Workflow verknüpfen. Daher können Sie ein adaptives Formular zur Laufzeit mithilfe der verfügbaren Eingabemethoden angeben.

* **Interaktive Kommunikation verwenden**: Geben Sie die Methode an, nach der die interaktive Eingabekommunikation lokalisiert werden soll. Sie können die interaktive Kommunikation verwenden, das an den Workflow übermittelt wurde, in einem absoluten Pfad verfügbar ist oder in einem Pfad in einer Variablen verfügbar ist. Sie können eine Variable des Typs „Zeichenfolge“ verwenden, um den Pfad anzugeben. Diese Option ist verfügbar, wenn Sie die Agenten-Benutzeroberfläche für interaktive Kommunikation oder das Dokument für interaktive Kommunikation über einen Web-Kanal in der Dropdown-Liste „Typ“ auswählen.

>[!NOTE]
>
>Sie müssen über Gruppenzuweisungen für cm-agent-users und workflow-users verfügen, um im AEM-Posteingang auf die Agenten-Benutzeroberfläche für interaktive Kommunikation zugreifen zu können.

* **Adaptives Formular oder Pfad zur interaktiven Kommunikation**: Geben Sie den Pfad des adaptiven Formulars oder der interaktiven Kommunikation an. Sie können das adaptive Formular oder die interaktive Kommunikation verwenden, das/die an den Workflow übermittelt wird und unter einem absoluten Pfad verfügbar ist, oder das adaptive Formular von einem Pfad abrufen, der in einer Variablen vom Datentyp „String“ gespeichert ist.
* **PDF-Eingabedatei auswählen mit**: Geben Sie den Pfad eines nicht interaktiven PDF-Dokuments an. Das Feld ist verfügbar, wenn Sie im Feld „Typ“ ein nicht interaktives PDF-Dokument auswählen. Sie können die PDF-Eingabedatei unter Verwendung des Pfads auswählen, der relativ zur Payload ist, unter einem absoluten Pfad gespeichert wird oder eine Variable des Datentyps „Dokument“ verwendet. Beispiel: [Payload_Directory]/Workflow/PDF/credit-card.pdf. Der Pfad existiert nicht im CRX-Repository. Ein Administrator erstellt den Pfad, bevor er ihn verwendet. Sie benötigen ein Formular mit aktivierter Option „Datensatzdokument“ oder auf Vorlagen basierende adaptive Formulare, um die PDF-Pfad-Komponente zu verwenden.
* **Für abgeschlossene Aufgaben rendern Sie das adaptive Formular wie folgt**: Wenn eine Aufgabe als abgeschlossen markiert ist, können Sie das adaptive Formular als schreibgeschütztes adaptives Formular oder PDF-Dokument ausgeben. Sie benötigen ein Formular mit aktivierter Option „Datensatzdokument“ oder auf Vorlagen basierende adaptive Formulare zum Rendern des adaptiven Formulars als Datensatzdokument.
* **Vorbefüllt:**: Die nachfolgend aufgeführte Felder dienen als Eingaben für die Aufgabe:

   * **[!UICONTROL Eingabedatendatei auswählen mit]**: Pfad der Eingabedatendatei (.json, .xml, .doc oder Formulardatenmodell). Sie können die Eingabedatendatei mit einem Pfad abrufen, der relativ zur Payload ist, oder die Datei abrufen, die in einer Variablen des Datentyps Dokument, XML oder JSON gespeichert ist. Beispielsweise enthält die Datei die Daten, die über eine AEM-Posteingangsanwendung für das Formular übermittelt werden. Ein Beispielpfad ist [Payload_Directory]/workflow/data.

   * **Eingabeanlagen auswählen mit:** Anlagen, die am Speicherort verfügbar sind, werden an das Formular angehängt, das mit der Aufgabe verknüpft ist. Der Pfad kann relativ zur Payload sein oder die Anlagen abrufen, die in einer Variablen des Typs ArrayList of Document gespeichert sind. Ein Beispielpfad ist [Payload_Directory]/attachments/. Sie können Anlagen angeben, die relativ zur Payload platziert werden, oder eine Dokumenttyp-Variable („Array-Liste“ > „Dokument“) verwenden, um einen Eingabeanhang für das adaptive Formular anzugeben..

      * **Wählen von JSON als Eingabe:** Wählen Sie als Eingabe eine JSON-Datei anhand eines Pfads aus, der relativ zur Payload ist oder in einer Variablen des Datentyps Dokument, JSON oder Formulardatenmodel gespeichert ist. Diese Option ist verfügbar, wenn Sie die Benutzeroberfläche des interaktiven Kommunikationsagenten oder das Dokument der interaktiven Kommunikation für den Web-Kanal aus der Dropdown-Liste „Typ“ auswählen.
      * **Wählen eines benutzerdefinierten Vorbefüllungs-Services:** Wählen Sie den Vorbefüllungs-Service aus, um die Daten abzurufen und das Dokument der interaktiven Kommunikation für den Web-Kanal oder die Benutzeroberfläche des Agenten vorab auszufüllen.
      * **Verwenden des Vorbefüllungs-Services der oben ausgewählten interaktiven Kommunikation:** Verwenden Sie diese Option, um den Vorbefüllungs-Service der interaktiven Kommunikation zu verwenden, der in der Dropdown-Liste „Interaktive Kommunikation verwenden“ definiert ist.
      * **Zuordnung von Anfrage-Attributen**: Verwenden Sie den Abschnitt „Attribut-Zuordnung anfordern“, um [Namen und Wert des Anfrage-Attributs](../../forms/using/work-with-form-data-model.md#bindargument) zu definieren. Rufen Sie die Details aus der Datenquelle basierend auf dem in der Anforderung angegebenen Attributnamen und -wert ab. Sie können einen Wert für das Anforderungsattribut mit einem Literalwert oder einer Variablen des Datentyps „Zeichenfolge“ definieren.\
         Die Zuordnungsoptionen für Vorbefüllungs-Services und Anfrage-Attribute sind nur verfügbar, wenn Sie in der Dropdown-Liste „Typ“ die Option „Benutzeroberfläche des interaktive Kommunikationsagenten“ oder „Dokument der interaktiven Kommunikation für den Web-Kanal“ auswählen.

* **Gesendete Informationen:** Die folgenden Felder dienen als Ausgabespeicherorte für die Aufgabe:

   * **Ausgabedatendatei speichern mit:**: Datendatei (.json, .xml, .doc oder Formulardatenmodell) speichern. Die Datendatei enthält Informationen, die über das zugeordnete Formular übermittelt werden. Sie können die Ausgabedatendatei unter Verwendung eines Pfads speichern, der relativ zur Payload ist, oder sie in einer Variablen des Datentyps „Dokument“, XML oder JSON speichern. Zum Beispiel [Payload_Directory]/Workflow/data, wobei „data“ für eine Datei steht.
   * **Anlagen speichern mit:** Formularanlagen in einer Aufgabe speichern. Sie können die Anlagen unter Verwendung eines Pfads speichern, der relativ zur Payload ist, oder sie in einer Variablen der Array-Liste vom Datentyp Dokument speichern.
   * **Datensatzdokument speichern mit:** Pfad zum Speichern einer Datensatzdokumentdatei. Beispielsweise [Payload_Directory]/DocumentofRecord/credit-card.pdf. Sie können das Datensatzdokument unter Verwendung eines Pfads speichern, der relativ zur Payload ist, oder es in einer Variablen des Datentyps „Dokument“ speichern. Wenn Sie die Option **Relativ zur Payload** auswählen, wird das Datensatzdokument nicht generiert, wenn das Feld „Pfad“ leer bleibt. Diese Option ist nur verfügbar, wenn Sie in der Dropdown-Liste „Typ“ die Option „Adaptives Formular“ auswählen.

   * **Web-Kanaldaten speichern mit:** Web-Kanal-Datendatei unter Verwendung eines Pfads speichern, der relativ zur Payload ist, oder in einer Variablen des Datentyps Dokument, JSON oder Formulardatenmodell speichern. Diese Option ist nur verfügbar, wenn Sie in der Dropdown-Liste „Typ“ die Option „Benutzeroberfläche des interaktiven Kommunikationsagenten“ auswählen.
   * **PDF-Dokument speichern mit:** PDF-Dokument unter Verwendung eines Pfads speichern, der relativ zur Payload ist, oder in einer Variablen von Datentyp Dokument speichern. Diese Option ist nur verfügbar, wenn Sie in der Dropdown-Liste „Typ“ die Option „Benutzeroberfläche des interaktiven Kommunikationsagenten“ auswählen.
   * **Layout-Vorlage speichern mit:** Layout-Vorlage unter Verwendung eines Pfads speichern, der relativ zur Payload ist, oder in einer Variablen vom Datentyp Dokument speichern. Die [Layout-Vorlage](../../forms/using/layout-design-details.md) verweist auf eine XDP-Datei, die Sie mit Forms Designer erstellen. Diese Option ist nur verfügbar, wenn Sie in der Dropdown-Liste „Typ“ die Option „Benutzeroberfläche des interaktiven Kommunikationsagenten“ auswählen.

* **Beauftragter > Optionen zuweisen:** Geben Sie die Methode an, mit der die Aufgabe einem Benutzer zugewiesen werden soll. Sie können die Aufgabe dynamisch einem Benutzer oder einer Gruppe zuweisen, indem Sie das Skript „Teilnehmerauswahl“ verwenden oder die Aufgabe einem bestimmten AEM-Benutzer oder einer bestimmten Gruppe zuweisen.
* **Teilnehmerauswahl:** Die Option ist verfügbar, wenn die Option **Dynamically to a user or group (Dynamisch zu einem Benutzer oder einer Gruppe)** im Feld „Optionen zuweisen“ ausgewählt ist. Sie können ein ECMAScript oder einen Service verwenden, um einen Benutzer oder eine Gruppe dynamisch auszuwählen. Weitere Informationen finden Sie im Abschnitt [Dynamisches Zuweisen eines Workflows zu Benutzern](https://helpx.adobe.com/de/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) und [Erstellen eines benutzerdefinierten Schritts „Dynamischer Teilnehmer in Adobe Experience Manager“.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de&amp;CID=RedirectAEMCommunityKautuk)

* **Teilnehmer:** Das Feld ist verfügbar, wenn die Option **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** im Feld **Teilnehmerauswahl** ausgewählt ist. In diesem Feld können Sie Benutzer oder Gruppen für die Option „RandomParticipantChooser“ auswählen.

* **Beauftragter**: Das Feld ist verfügbar, wenn die Option **[!UICONTROL com.adobe.fd.workspace.step.service.VariableParticipantChooser]** im Feld **Teilnehmerauswahl** ausgewählt ist. Mit dem Feld können Sie eine Variable des Datentyps „Zeichenfolge“ auswählen, um den Verantwortlichen zu definieren.

* **Argumente:** Das Feld ist verfügbar, wenn ein anderes als das Skript „RandomParticipantChoose“ im Feld „Teilnehmerauswahl“ ausgewählt wurde. In diesem Feld können Sie eine Liste mit durch Kommas getrennten Argumenten für das im Feld „Teilnehmerauswahl“ ausgewählte Skript angeben.

* **Benutzer oder Gruppe:** Die Aufgabe wurde dem ausgewählten Benutzer oder der Gruppe zugewiesen. Die Option ist verfügbar, wenn die Option **Zu einem bestimmten Benutzer bzw. einer bestimmten Gruppe** im Feld **Optionen zuweisen** ausgewählt ist. Das Feld listet alle Benutzer und Gruppen der Workflow-Benutzergruppe auf.\
   Das Dropdownmenü **Benutzer oder Gruppe** führt die Benutzer und Gruppen auf, auf die der angemeldete Benutzer Zugriff hat. Die Anzeige des Benutzernamens hängt davon ab, ob Sie über Zugriffsberechtigungen für den Knoten **users** im CRX-Repository für diesen bestimmten Benutzer verfügen.

* **[!UICONTROL E-Mail-Benachrichtigung senden]**: Wählen Sie diese Option aus, um E-Mail-Benachrichtigungen an den Verantwortlichen zu senden. Diese Benachrichtigungen werden gesendet, wenn eine Aufgabe einem Benutzer oder einer Gruppe zugewiesen wird. Mit der Option **[!UICONTROL Empfänger-E-Mail-Adresse]** können Sie den Mechanismus zum Abrufen der E-Mail-Adresse angeben.

* **[!UICONTROL Empfänger-E-Mail-Adresse]**: Sie können die E-Mail-Adresse in einer Variablen speichern, mit einem Literal eine permanente E-Mail-Adresse angeben oder die Standard-E-Mail-Adresse des Verantwortlichen verwenden, die in seinem Profil angegeben ist. Sie können das Literal oder eine Variable verwenden, um die E-Mail-Adresse einer Gruppe anzugeben. Die Option „Variable“ ist beim dynamischen Abrufen und Verwenden einer E-Mail-Adresse hilfreich. Die Option **[!UICONTROL Standardmäßige E-Mail-Adresse des Verantwortlichen verwenden]** gilt nur für einen einzelnen Verantwortlichen. In diesem Fall wird die E-Mail-Adresse verwendet, die im Benutzerprofil des Verantwortlichen gespeichert ist.

* **HTML-E-Mail-Vorlage**: Wählen Sie die E-Mail-Vorlage für die Benachrichtigungs-E-Mail. Um eine Vorlage zu bearbeiten, ändern Sie die Datei unter /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt im CRX-Repository.
* **Delegierung zulassen an:** AEM Inbox bietet dem angemeldeten Benutzer eine Option, den zugewiesenen Workflow an einen anderen Benutzer zu übertragen. Sie dürfen innerhalb derselben Gruppe oder an den Workflow-Benutzer einer anderen Gruppe delegieren. Wenn die Aufgabe einem einzelnen Benutzer zugewiesen ist und die Option **Delegierung an Mitglieder der Gruppe an Verantwortlichen zulassen** aktiviert ist, kann die Aufgabe nicht an einen anderen Benutzer oder eine andere Gruppe übertragen werden.
* **Freigabeeinstellungen**: Der AEM-Posteingang bietet Optionen zum Freigeben einer einzelnen oder aller Aufgaben im Posteingang für andere Benutzer:
   * Wenn die Option **Bevollmächtigtem erlauben, explizit im Posteingang freizugeben** ausgewählt ist, kann der Benutzer auf die Aufgabe klicken und sie für einen anderen AEM-Benutzer freigeben.
   * Wenn die Option **Bevollmächtigtem erlauben, explizit im Posteingang freizugeben** ausgewählt ist und ein Benutzer seine Posteingangselemente freigibt oder anderen Benutzern den Zugriff auf seine Posteingangselemente erlaubt, werden nur Aufgaben mit der zuvor erwähnten aktivierten Option für andere Benutzer freigegeben.

* **Aktionen > Standardaktionen**: Standardmäßig sind die Aktionen „Übermitteln“, „Speichern“ und „Zurücksetzen“ verfügbar. Alle Standardaktionen sind standardmäßig aktiviert.
* **Route-Variable:** Name der Route-Variablen. Die Route-Variable erfasst benutzerdefinierte Aktionen, die ein Benutzer im AEM-Posteingang auswählt.
* **Routen:** Eine Aufgabe kann auf verschiedene Routen verzweigen. Bei Auswahl im AEM-Posteingang gibt die Route einen Wert zurück, und der Workflow verzweigt basierend auf der ausgewählten Route. Sie können Routen entweder in einer Variablen des Arrays des Datentyps „Zeichenfolge“ speichern oder **Literal** auswählen, um Routen manuell hinzuzufügen.

* **Routentitel**: Geben Sie den Titel für die an. Er wird im AEM-Posteingang angezeigt.
* **Korallensymbol**: Geben Sie das HTML-Attribut eines Korallensymbols an. Die Adobe CoralUI-Bibliothek bietet eine Vielzahl von Touch-First-Symbolen. Sie können ein Symbol für die Route auswählen und verwenden. Es wird zusammen mit dem Titel im AEM-Posteingang angezeigt. Wenn Sie die Routen in einer Variablen speichern, verwenden die Routen ein standardmäßiges „Tags“-Korallensymbol.
* **Zulassen, dass Verantwortlicher Kommentare hinzufügt**: Wählen Sie diese Option, um Kommentare für die Aufgabe zu aktivieren. Ein Verantwortlicher kann die Kommentare innerhalb des AEM-Posteingangs zum Zeitpunkt der Aufgabenübermittlung hinzufügen.
* **Kommentar in Variable speichern**: Speichern des Kommentars in einer Variablen des Datentyps „String“. Diese Option wird nur angezeigt, wenn Sie das Kontrollkästchen **Zulassen, dass Verantwortlicher Kommentare hinzufügt** aktivieren.

* **Bevollmächtigtem erlauben, Anlage(n) der Aufgabe hinzuzufügen**: Wählen Sie diese Option, um Anlagen für die Aufgabe zu aktivieren. Ein Verantwortlicher kann die Anhänge im AEM-Posteingang zum Zeitpunkt der Aufgabenübermittlung hinzufügen.
* **Aufgabenanhänge speichern mit**: Geben Sie den Speicherort des Anhangsordners an. Sie können Ausgabeaufgabenanhänge mit einem Pfad relativ zur Payload oder in einer Variablen des Arrays des Datentyps „Dokument“ speichern. Diese Option wird nur angezeigt, wenn Sie das Kontrollkästchen **Bevollmächtigtem erlauben, Anhänge zur Aufgabe hinzuzufügen** aktivieren und **Adaptives Formular**, **Schreibgeschütztes adaptives Formular** oder **Nicht interaktives PDF-Dokument** aus der Dropdown-Liste **Typ** auf der Registerkarte **Formular/Dokument** auswählen.

>[!NOTE]
>
>Verwenden Sie zur Laufzeit die Registerkarte „Anlagen“ in der Agenten-Benutzeroberfläche, um die Anlagen mit einer interaktiven Kommunikation zu verknüpfen. Die zugehörigen Anlagen werden nach dem Öffnen des Arbeitselements in einem Status „Abgeschlossen“ als Aufgabenanlagen im Sidekick angezeigt.

* **Benutzerdefinierte Metadaten verwenden:** Wählen Sie diese Option, um das benutzerdefinierte Metadatenfeld zu aktivieren. Benutzerdefinierte Metadaten werden in E-Mail-Vorlagen verwendet.
* **Benutzerdefinierte Metadaten:** Wählen Sie benutzerdefinierte Metadaten für die E-Mail-Vorlagen. Die benutzerdefinierten Metadaten sind im CRX-Repository unter apps/fd/dashboard/scripts/metadataScripts verfügbar. Der angegebene Pfad existiert nicht im CRX-Repository. Ein Administrator erstellt den Pfad, bevor er ihn verwendet. Sie können auch einen Service für die benutzerdefinierten Metadaten verwenden. Sie können auch die Schnittstelle WorkitemUserMetadataService erweitern, um benutzerdefinierte Metadaten bereitzustellen.
* **Daten aus vorherigen Schritten anzeigen**: Wählen Sie - falls verfügbar - diese Option aus, um den Bevollmächtigten das Anzeigen früherer Bevollmächtigter, bereits vorgenommener Aktionen, Kommentare zu dieser Aufgabe und des Nachweisdokuments über abgeschlossene Aufgaben zu ermöglichen.
* **Daten aus allen nachfolgenden Schritten einblenden:** Wählen Sie diese Option, um dem aktuellen Bearbeiter zu ermöglichen, die durchgeführte Aktion und Kommentare, die von nachfolgenden Beauftragten zur Aufgabe hinzugefügt wurden, anzuzeigen. Außerdem kann sich der aktuelle Bevollmächtigte ein Dokument als Nachweis über die abgeschlossenen Aufgaben anzeigen lassen - sofern verfügbar.
* **Sichtbarkeit des Datentyps:** Standardmäßig kann ein Bevollmächtigter ein Datensatzdokument, Bevollmächtigte, durchgeführte Aktionen und Kommentare anzeigen, die frühere und nachfolgende Bevollmächtigte hinzugefügt haben. Verwenden Sie die Option „Sichtbarkeit des Datentyps“, um den Typ der für die Verantwortlichen sichtbaren Daten zu begrenzen.

>[!NOTE]
>
>Die Optionen zum Speichern des Schritts &quot;Aufgabe zuweisen&quot;als Entwurf und zum Abrufen des Verlaufs des Schritts &quot;Aufgabe zuweisen&quot;sind deaktiviert, wenn Sie eine [!DNL Adobe Experience Manager] Workflow-Modell für die externe Datenspeicherung. Außerdem ist die Option zum Speichern im Posteingang deaktiviert.

## Schritt „E-Mail senden“ {#send-email-step}

Verwenden Sie den E-Mail-Schritt, um eine E-Mail zu senden, z. B. eine E-Mail mit einem Dokument, einen Link eines adaptiven Formulars, einen Link einer interaktiven Kommunikation oder ein angehängtes PDF-Dokument. Der Schritt „E-Mail senden“ unterstützt [HTML-E-Mails](https://en.wikipedia.org/wiki/HTML_email). HTML-E-Mails sind responsive und passen sich an den E-Mail-Client und die Bildschirmgröße des Empfängers an. Sie können eine HTML-E-Mail-Vorlage verwenden, um das Erscheinungsbild, das Farbschema und Verhalten der E-Mail zu definieren.

Beim E-Mail-Schritt wird der Day CQ Mail Service zum Senden von E-Mails verwenden. Bevor Sie den E-Mail-Schritt verwenden, stellen Sie sicher, dass der [E-Mail-Dienst](../../forms/using/aem-forms-workflow.md) konfiguriert wurde. Der E-Mail-Schritt hat folgende Eigenschaften:

**Titel:** Der Titel des Schritts hilft beim Identifizieren des Schritts im Workflow-Editor.

**Beschreibung:** Erklärungen können für andere Entwickler nützlich sein, wenn Sie in einer gemeinsamen Entwicklungsumgebung arbeiten.

**E-Mail-Betreff**: Der Betreff kann aus Workflow-Metadaten abgerufen, manuell angegeben oder aus dem in einer Variablen gespeicherten Wert abgerufen werden. Zur Auswahl stehen:

* **Literal** – Geben Sie ein Thema manuell an.
* **Aus Workflow-Metadaten abrufen** – Sie können den Betreff von einer Metadateneigenschaft abrufen.
* **Variable** – Sie können den Betreff aus dem Wert abrufen, der in einer Variablen des Datentyps „Zeichenfolge“ gespeichert ist.

**HTML-E-Mail-Vorlage**: HTML-Vorlage für die E-Mail. Sie können Variablen in einer E-Mail-Vorlage spezifizieren. Der E-Mail-Schritt extrahiert und zeigt alle Variablen an, die in einer Vorlage für Eingaben enthalten sind.

**E-Mail-Vorlagen-Metadaten**: Der Wert der E-Mail-Vorlagenvariablen kann ein benutzerspezifizierter Wert, der Pfad eines Assets auf dem Autoren- oder Veröffentlichungs-Server, ein Bild oder eine Workflow-Metadateneigenschaft sein.

* **Literal:** Verwenden Sie die Option, wenn Sie den genauen Wert kennen, der angegeben werden soll. Beispiel: [beispiel@beispiel.com](mailto:example@example.com).

* **Workflow-Metadaten:** Verwenden Sie die Option, wenn der zu verwendende Wert in einer Workflow-Metadaten-Eigenschaft gespeichert wird. Nachdem Sie die Option ausgewählt haben, geben Sie den Namen der Metadateneigenschaft in das leere Textfeld unter der Option „Workflow-Metadaten“ ein. Beispiel: e-mailAdresse.
* **Asset-URL**: Verwenden Sie diese Option zum Einbetten eines Weblinks einer interaktiven Kommunikation in die E-Mail. Nachdem Sie die Option ausgewählt haben, suchen Sie nach der interaktiven Kommunikation, die eingebettet werden soll. Das Asset kann sich auf dem Autoren- oder dem Veröffentlichungsserver befinden.
* **Bild:** Verwenden Sie die Option, um ein Bild in die E-Mail einzubetten. Nachdem Sie die Option ausgewählt haben, suchen Sie nach dem entsprechenden Bild und wählen Sie es aus. Die Bildoption ist nur für die Bild-Tags (&lt;img src=&quot;&lt;span id=&quot; translate=&quot;no&quot; />&quot;/>) verfügbar, die in der E-Mail-Vorlage verfügbar sind.&#42;

**E-Mail-Adresse des Absenders/Empfängers:** Wählen Sie die Option **Literal**, um eine E-Mail-Adresse manuell anzugeben, oder wählen Sie die Option **Aus Workflow-Metadaten abrufen**, um die E-Mail-Adresse aus einer Metadaten-Eigenschaft abzurufen. Sie können auch eine Liste von Metadateneigenschaften-Arrays für die Option **Aus Workflow-Metadaten abrufen** angeben. Wählen Sie die Option **Variable** aus, um die E-Mail-Adresse aus dem Wert abzurufen, der in einer Variablen des Datentyps „Zeichenfolge“ gespeichert ist.

**Dateianhang**: Das am angegebenen Speicherort verfügbare Asset wird an die E-Mail angehängt. Der Pfad des Assets kann relativ zur Payload oder zum absoluten Pfad sein. Ein Beispielpfad ist [Payload_Directory]/attachments/.

Wählen Sie die Option **Variable**, um den in einer Variablen des Dateityps „Dokument“, XML oder JSON gespeicherte Dateianhang abzurufen.

**Dateiname:** Name der E-Mail-Anhangsdatei. Der E-Mail-Schritt ändert den Originaldateinamen des Anhangs in den angegebenen Dateinamen. Der Name kann manuell angegeben oder aus einer Workflow-Metadateneigenschaft oder einer Variable abgerufen werden. Verwenden Sie die Option **Literal**, wenn Sie den genauen zu spezifizierenden Wert kennen. Verwenden Sie die Option **Variable**, um den Dateinamen aus dem Wert abzurufen, der in einer Variablen des Datentyps „Zeichenfolge“ gespeichert ist. Verwenden Sie die Option **Aus Workflow-Metadaten abrufen**, wenn der zu verwendende Wert in einer Workflow-Metadateneigenschaft gespeichert wird.

## Schritt „Datensatzdokument generieren“ {#generate-document-of-record-step}

Wenn ein Formular ausgefüllt oder übermittelt wird, können Sie das Formular drucken oder als Dokument speichern. Dies wird als Datensatzdokument (DOR) bezeichnet. Sie können den Schritt „Generieren von Datensatzdokument“ verwenden, um eine schreibgeschützte oder interaktive PDF-Version eines adaptiven Formulars zu erstellen. Die PDF-Version enthält Informationen, die zusammen mit dem Layout des adaptiven Formulars in das Formular eingegeben werden.

Der Schritt „Datensatzdokument generieren“ hat folgende Eigenschaften:

**Adaptives Formular verwenden**: Geben Sie die Methode zum Suchen des adaptiven Eingabeformulars an. Sie können das adaptive Formular verwenden, das an den Workflow übermittelt wurde, in einem absoluten Pfad verfügbar ist oder in einem Pfad in einer Variablen verfügbar ist. Sie können eine Variable des Datentyps „Zeichenfolge“ verwenden, um den Pfad im Feld **Variable zur Auflösung auswählen** anzugeben.\
Sie können mehrere adaptive Formulare mit einem Workflow verknüpfen. Daher können Sie ein adaptives Formular zur Laufzeit mithilfe der verfügbaren Eingabemethoden angeben.

**Adaptiver Formularpfad**: Geben Sie den Pfad des adaptiven Formulars an. Das Feld ist verfügbar, wenn Sie die Option **Unter einem absoluten Pfad verfügbar** im Feld **Adaptives Formular verwenden** auswählen.

**Eingabedaten auswählen mit**: Pfad der Eingabedaten für das adaptive Formular. Sie können die Daten an einem Speicherort relativ zur Payload speichern, einen absoluten Pfad der Daten angeben oder Daten abrufen, die in einer Variablen des Datentyps „Dokument“, JSON oder XML gespeichert sind. Die Eingabedaten werden mit dem adaptiven Formular zusammengeführt, um ein Datensatzdokument zu erstellen.

**Pfad für Eingabeanhang auswählen mit**: Pfad der Anhänge. Diese Anhänge sind im Datensatzdokument enthalten. Sie können die Anhänge an einem Speicherort relativ zur Payload speichern, einen absoluten Pfad der Anhänge angeben oder Anhänge abrufen, die in einer Variablen des Datentyps „Dokument“ gespeichert sind.

Wenn Sie den Pfad eines Ordners angeben, z. B. Anhänge, werden alle Dateien, die direkt im Ordner verfügbar sind, an das Datensatzdokument angehängt. Wenn Dateien in den Ordnern verfügbar sind, die im angegebenen Pfad für den Anhang direkt verfügbar sind, werden die Dateien im Datensatzdokument als Anhänge aufgenommen. Wenn sich Ordner in direkt verfügbaren Ordnern befinden, werden diese übersprungen.

**Generiertes Datensatzdokument mithilfe nachstehender Optionen speichern**: Geben Sie den Speicherort für ein Datensatzdokument an. Sie können den Payload-Ordner überschreiben, das Datensatzdokument an einem Speicherort im Payload-Verzeichnis ablegen oder es in einer Variablen des Datentyps „Document“ speichern.

**Gebietsschema**: Geben Sie die Sprache des Datensatzdokuments an. Wählen Sie **Literal** aus, um das Gebietsschema aus einer Dropdown-Liste auszuwählen, oder wählen Sie **Variable**, um das Gebietsschema aus dem Wert abzurufen, der in einer Variablen des Datentyps „Zeichenfolge“ gespeichert ist. Sie müssen den Gebietsschema-Code definieren, während Sie den Wert für das Gebietsschema in einer Variablen speichern. Geben Sie beispielsweise **en_US** für Englisch und **fr_FR** für Französisch an.

## Schritt „Formulardatenmodell-Service aufrufen“ {#invoke-form-data-model-service-step}

Sie können [AEM Forms-Datenintegration](../../forms/using/data-integration.md) verwenden, um unterschiedliche Datenquellen zu konfigurieren und Verbindungen zu ihnen herzustellen. Diese Datenquellen können eine Datenbank, ein Webdienst, ein REST-Dienst, ein OData-Dienst und eine CRM-Lösung sein. Mit AEM Forms-Datenintegration können Sie ein Formulardatenmodell erstellen, das verschiedene Dienste umfasst, um Vorgänge zum Datenabruf, Hinzufügen und Aktualisieren in der konfigurierten Datenbank durchzuführen. Sie können den **Schritt „Formulardatenmodelldienst aufrufen“** verwenden, um ein Formulardatenmodell (FDM) zu wählen und die Dienste des FDM abzurufen, zu aktualisieren oder Daten unterschiedlichen Datenquellen hinzuzufügen.

Um die Eingaben für Felder des Schritts zu erläutern, werden die folgende Datenbanktabelle und JSON-Datei als Beispiel verwendet:

**Beispiel: Tabelle „Kundendetails“**

<table>
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Wert<br /> </td> 
  </tr> 
  <tr> 
   <td>Vorname<br /> </td> 
   <td>Sarah<br /> </td> 
  </tr> 
  <tr> 
   <td>Nachname</td> 
   <td>Rose</td> 
  </tr> 
  <tr> 
   <td>Kunden-ID</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>E-Mail-Adresse<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**JSON-Beispieldatei**

```json
  { 
    customer: { 
     firstName: "Sarah", 
     lastName:"Rose", 
     customerId: "1", 
     emailAddress:"srose@we.info" 
   }, 
    insurance: {
     customerId: "1", 
    policyType: "Premium,
    policyNumber: "Premium-521499",
    customerDetails: { 
     firstName: "Sarah",
     lastName: "Rose",
     customerId: "1",
     emailAddress: "srose@we.info" 
    }
   }
  }
```

Der Schritt „Formulardatenmodelldienst aufrufen“ enthält die folgenden Felder, um Formulardatenmodellvorgänge zu vereinfachen:

* **Titel:** Bezeichnung des Schrittes. Dies erleichtert die Identifizierung dieses Schritts im Workflow-Editor.
* **Beschreibung:** Erklärungen können für andere Entwickler nützlich sein, wenn Sie in einer gemeinsamen Entwicklungsumgebung arbeiten.

* **Pfad für Formulardatenmodell**: Wählen Sie ein Formulardatenmodell auf dem Server aus.

* **Dienst**: Liste der Dienste, die das ausgewählte Formulardatenmodell bereitstellt.
* **Eingabe für Services > Bereitstellung von Eingabedaten mit Literal, Variable oder Workflow-Metadaten und einer JSON-Datei**: Ein Service kann mehrere Argumente aufweisen. Wählen Sie die Option zum Abrufen des Werts der Service-Parameter aus einer Workflow-Metadateneigenschaft, einem JSON-Objekt oder einer Variable aus oder geben Sie den Wert direkt in das bereitgestellte Textfeld ein:

   * **Literal:** Verwenden Sie die Option, wenn Sie den genauen Wert kennen, der angegeben werden soll. Beispiel: srose@we.info.
   * **Variable**: Verwenden Sie diese Option, um den in einer Variablen gespeicherten Wert abzurufen.
   * **Aus Workflow-Metadaten abrufen:** Verwenden Sie die Option, wenn der zu verwendende Wert in einer Workflow-Metadaten-Eigenschaft gespeichert wird. Beispiel: e-mailAddress.
   * **[!UICONTROL Relativ zur Nutzlast]**: Verwenden Sie die Option zum Abrufen des Dateianhangs, der in einem Pfad relativ zur Payload gespeichert ist. Wählen Sie die Option aus und geben Sie entweder den Ordnernamen an, der den Dateianhang enthält, oder geben Sie den Dateinamen für den Anhang im Textfeld an.

      Wenn beispielsweise der Ordner „Relativ zur Nutzlast“ im CRX-Repository einen Dateianhang am Speicherort `attachment\attachment-folder` enthält, geben Sie `attachment\attachment-folder` im Textfeld an, nachdem Sie die Option **[!UICONTROL Relativ zur Nutzlast]** ausgewählt haben.
   * **JSON Dot Notation:** Verwenden Sie die Option, wenn der zu verwendende Wert in einer JSON-Datei enthalten ist. Beispiel: Insurance.customerDetails.emailAddress. Die Option „JSON Dot Notation“ ist nur verfügbar, wenn Zuordnungseingabefelder zur Eingabe von JSON-Optionen ausgewählt sind.
   * **Zuordnen von Eingabefelder aus der Eingabe JSON:** Geben Sie den Pfad einer JSON-Datei an, um den Eingabewert einiger Service-Parameter aus der JSON-Datei abzurufen. Der Pfad der JSON-Datei kann relativ zur Payload bzw. zu einem absoluten Pfad sein oder Sie können ein JSON-Eingabedokument mit einer Variable vom Typ JSON oder Formulardatenmodell auswählen.

* **Eingabe für Services > Eingabedaten mithilfe einer Variablen oder einer JSON-Datei bereitstellen**: Wählen Sie diese Option, um Werte für alle Argumente aus einer JSON-Datei abzurufen, die unter einem absoluten Pfad, einem Pfad relativ zur Payload oder in einer Variablen gespeichert wurde.
* **Auswahl des Eingabe-JSON-Dokuments mit**: Die JSON-Datei, die Werte für alle Dienstargumente enthält. Der Pfad der JSON-Datei kann **relativ zur Payload** oder einem **absoluten Pfad** sein. Sie können das JSON-Eingabedokument auch mit einer Variablen vom Typ „JSON“ oder „Formulardatenmodell“ abrufen.

* **JSON Dot Notation:** Lassen Sie das Feld leer, um alle Objekte der angegebenen JSON-Datei als Eingabe für Service-Parameter zu verwenden. Um ein bestimmtes JSON-Objekt aus der angegebenen JSON-Datei als Eingabe für Service-Argumente zu lesen, geben Sie die Dot Notation für das JSON-Objekt an, z. B. wenn Sie eine JSON ähnlich wie am Anfang des Abschnitts aufgeführt haben, geben Sie „insurance.customerDetails“ an, um alle Details eines Kunden als Eingabe für den Service anzugeben.
* **Ausgabe des Service > Ausgabewerte zu Variablen oder Metadaten zuordnen und schreiben**: Wählen Sie diese Option, um die Ausgabewerte als Eigenschaften des Metadatenknotens der Workflow-Instanz im CRX-Repository zu speichern. Geben Sie den Namen der Metadateneigenschaft an und wählen Sie das entsprechende Service-Ausgabeattribut, das der Metadateneigenschaft zugeordnet werden soll, ordnen Sie z. B. die vom Ausgabe-Service zurückgegebene Telefonnummer der Eigenschaft „phone_number“ der Workflow-Metadaten zu. Auf ähnliche Weise können Sie die Ausgabe in einer Variablen des Datentyps „Long“ speichern. Wenn Sie eine Eigenschaft für die Option **[!UICONTROL Ausgabeattribut des Services, das abgebildet werden soll]** auswählen, werden für die Option **[!UICONTROL Speichern der Ausgabe in]** nur Variablen ausgefüllt, die Daten der ausgewählten Eigenschaft speichern können.

* **Ausgabe des Services > Ausgabe in Variable oder JSON-Datei speichern**: Wählen Sie diese Option, um die Ausgabewerte in einer JSON-Datei unter einem absoluten Pfad, einem Pfad relativ zur Payload oder in einer Variablen zu speichern.
* **Ausgabe-JSON-Dokument mithilfe folgender Optionen speichern**: Speichern der JSON-Ausgabedatei. Der Pfad der JSON-Ausgabedatei kann relativ zur Payload oder einem absoluten Pfad sein. Sie können die JSON-Ausgabedatei auch mit einer Variablen vom Typ „JSON“ oder „Formulardatenmodell“ speichern.

## Schritt „Dokument signieren“ {#sign-document-step}

Mit dem Schritt „Dokument signieren“ können Sie Adobe Sign zum Signieren von Dokumenten verwenden. Der Schritt „Dokument signieren“ hat folgende Eigenschaften:

* **Name der Vereinbarung:** Geben Sie den Titel der Vereinbarung an. Der Name der Vereinbarung wird Teil des Betreffs und des Textkörpers der E-Mail, die an die Unterzeichner gesendet wird. Sie können den Namen entweder in einer Variablen des Datentyps „Zeichenfolge“ speichern oder **Literal** auswählen, um den Namen manuell hinzuzufügen.

* **Gebietsschema:** Geben Sie die Sprache für die E-Mail- und Bestätigungsoptionen an. Sie können das Gebietsschema entweder in einer Variablen des Datentyps „Zeichenfolge“ speichern oder **Literal** auswählen, um das Gebietsschema aus der Liste der verfügbaren Optionen auszuwählen. Sie müssen den Gebietsschema-Code definieren, während Sie den Wert für das Gebietsschema in einer Variablen speichern. Geben Sie beispielsweise **en_US** für Englisch und **fr_FR** für Französisch an.

* **Cloud-Konfiguration für Adobe Sign**: Wählen Sie eine Adobe Sign Cloud-Konfiguration. Wenn Sie Adobe Sign für AEM Forms nicht konfiguriert haben, lesen Sie den Abschnitt [Adobe Sign in AEM Forms integrieren](../../forms/using/adobe-sign-integration-adaptive-forms.md).

* **Zu signierendes Dokument auswählen mit**: Sie können ein Dokument an einem Speicherort relativ zur Payload auswählen, Payload als das Dokument verwenden, einen absoluten Pfad für das Dokument angeben oder das Dokument abrufen, das in einer Variablen des Datentyps „Document“ gespeichert ist.


* **Wählen Sie den Pfad für die Eingabeanlage mit:** Pfad der Anlagen. Diese Anlagen sind im Signaturdokument enthalten. Sie können die Anhänge an einem Speicherort relativ zur Payload speichern, einen absoluten Pfad der Anhänge angeben oder Anhänge abrufen, die in einer Variablen des Datentyps „Dokument“ gespeichert sind.


   Wenn Sie den Pfad eines Ordners angeben, z. B. Anlagen, werden alle direkt im Ordner verfügbaren Dateien an das Signaturdokument angehängt. Wenn Dateien in den Ordnern verfügbar sind, die direkt im angegebenen Anlagenpfad verfügbar sind, werden die Dateien in &quot;Signing Document&quot;als Anhänge aufgenommen. Wenn sich Ordner in direkt verfügbaren Ordnern befinden, werden diese übersprungen.

* **Tage bis Abgabetermin:** Ein Dokument wird als „fällig“ (Abgabetermin überschritten) gekennzeichnet, nachdem für die im Feld **Tage bis Abgabetermin** angegebene Anzahl von Tagen keine Aktivität für die Aufgabe ermittelt wurde. Die Anzahl der Tage wird gezählt, nachdem das Dokument einem Benutzer zur Unterzeichnung zugewiesen wurde.
* **Häufigkeit der E-Mail-Erinnerung:** Sie können eine Erinnerungs-E-Mail im täglichen oder wöchentlichen Intervall senden. Die Woche wird ab dem Tag gezählt, an dem das Dokument einem Benutzer zum Signieren zugewiesen wurde.
* **Signaturvorgang:** Sie können ein Dokument in einer sequenziellen oder parallelen Reihenfolge signieren. Bei sequenzieller Reihenfolge erhält jeweils nur ein Unterzeichner das Formular zur Unterzeichnung. Nachdem der erste Unterzeichner das Dokument signiert hat, wird das Formular an den nächsten Unterzeichner gesendet und so weiter. Bei paralleler Reihenfolge können mehrere Unterzeichner ein Formular gleichzeitig signieren.
* **Umleitungs-URL:** Geben Sie eine Umleitungs-URL an. Nachdem das Dokument signiert wurde, können Sie den Verantwortlichen an eine URL umleiten. Normalerweise enthält diese URL eine Dankesnachricht oder weitere Anweisungen.
* **Workflow-Phase:** Ein Workflow kann mehrere Phasen enthalten. Diese werden im AEM-Posteingang angezeigt. Sie können diese Schritte in den Eigenschaften des Modells definieren (Sidekick > Seite > Seiteneigenschaften > Schritte).
* **Unterzeichner wählen:** Geben Sie die Methode zum Auswählen von Unterzeichnern für das Dokument an. Sie können den Workflow einem Benutzer oder einer Gruppe dynamisch zuweisen oder manuell Details zu einem Unterzeichner hinzufügen.
* **Skript oder Dienst zur Auswahl von Unterzeichnern:** Die Option ist nur verfügbar, wenn die Option „Dynamisch“ im Feld „Unterzeichner auswählen“ ausgewählt ist. Sie können ein ECMAScript oder einen Service angeben, um Unterzeichner und Verifizierungsoptionen für ein Dokument auszuwählen.
* **Unterzeichnerdetails:** Die Option ist nur verfügbar, wenn die Option „Manuell“ im Feld „Unterzeichner auswählen“ ausgewählt ist. Geben Sie die E-Mail-Adresse an und wählen Sie einen optionalen Verifizierungsmechanismus aus. Bevor Sie einen Zwei-Schritt-Bestätigungsmechanismus auswählen, vergewissern Sie sich, dass die entsprechende Verifizierungsoption für das konfigurierte Adobe Sign-Konto aktiviert ist. Sie können eine Variable vom Datentyp „String“ verwenden, um Werte für die Felder **[!UICONTROL E-Mail]**, **[!UICONTROL Länder-Code]** und **[!UICONTROL Telefonnummer]** zu definieren. Die Felder **[!UICONTROL Länder-Code]** und **[!UICONTROL Telefonnummer]** werden nur angezeigt, wenn Sie **[!UICONTROL Telefonüberprüfung]** aus der Dropdown-Liste **[!UICONTROL Zweistufenüberprüfung]** auswählen.
* **Statusvariable**: Ein Dokument, für das Adobe Sign aktiviert ist, speichert den Signierstatus des Dokuments in einer Variablen vom Datentyp „String“. Geben Sie den Namen der Statusvariable (adobeSignStatus) an. Eine Statusvariable einer Instanz ist in CRXDE unter /etc/workflow/instances/&lt;Server>/&lt;Datum/Uhrzeit>/&lt;Instanz des Workflow-Modells>/workItems/&lt;Knoten>/metaData verfügbar und enthält den Status einer Variablen.
* **Signiertes Dokument mit folgenden Optionen speichern**: Geben Sie den Speicherort für signierte Dokumente an. Sie können den Payload-Ordner überschreiben, das Datensatzdokument an einem Speicherort im Payload-Verzeichnis ablegen oder es in einer Variablen des Datentyps „Document“ speichern.

## Schritt „Document Services“ {#document-services-steps}

Bei AEM Document Services handelt es sich um einen Satz an OSGi-Diensten zum Erstellen, Zusammenstellen und Sichern von PDF-Dokumenten. AEM Forms stellt für jeden Dokumenten-Service einen separaten AEM-Workflow-Schritt bereit.

Ähnlich wie bei anderen AEM Forms-Workflow-Schritten wie „Aufgabe zuweisen“, „E-Mail senden“ und „Dokument unterschreiben“ können Sie Variablen in allen Schritten von AEM Document Services verwenden. Informationen zum Erstellen und Verwalten von Variablen finden Sie unter [Variablen in AEM-Workflows](../../forms/using/variable-in-aem-workflows.md).

### Schritt „Dokumentzeitstempel einfügen“ {#apply-document-time-stamp-step}

Fügen Sie einen Zeitstempel in das Dokument ein. Sie geben Dokumentdetails wie den Pfad des Eingabedokuments, den Namen des Eingabedokuments und den Speicherort für die exportierten Daten an. Sie können die vorhandene Payload-Datei überschreiben, einen anderen Dateinamen auswählen, um Daten in einer anderen Datei im Payload-Ordner zu speichern, einen absoluten Pfad zu den Daten angeben oder Daten in einer Variablen des Datentyps „Document“ speichern.

### Schritt „In Bild umwandeln“ {#convert-to-image-step}

Konvertiert ein PDF-Dokument in eine Bilderliste. Unterstützte Bildformate sind JPEG, JPEG2000, PNG und TIFF. Die folgenden Informationen gelten für Konvertierungen in TIFF-Bilder:

* Eine mehrseitige TIFF-Datei wird generiert.
* Einige Anmerkungen sind nicht in TIFF-Bildern enthalten. Anmerkungen, die Acrobat zur Erstellung ihrer Darstellung benötigen, sind nicht enthalten.

### Schritt „Nach PDF/A konvertieren“ {#convert-to-pdf-a-step}

Konvertiert ein PDF-Dokument mit den verfügbaren Optionen in das PDF/A-Format. Die PDF/A-Version des Portable Document Format (PDF) ist auf die Archivierung und Langzeitarchivierung von Dokumenten spezialisiert. 

### Schritt „Konvertieren nach PS“ {#convert-to-ps-step}

Konvertieren von PDF-Dokumenten in PostScript – Beim Konvertieren in PostScript können Sie für den Konvertierungsvorgang das Quelldokument und die PostScript-Ebene (2 oder 3) angeben. Das PDF-Dokument, das in eine PostScript-Datei konvertiert wird, muss nicht interaktiv sein.

### Schritt „PDF vom angegebenen Typ erstellen“ {#create-pdf-from-specified-type-step}

Generiert ein PDF-Dokument aus einer Eingabedatei. Das Eingabedokument kann relativ zur Payload sein, einen absoluten Pfad haben, selbst Payload sein oder in einer Variablen des Datentyps „Document“ gespeichert sein.

### Schritt „PDF aus URL/HTML/ZIP erstellen“ {#create-pdf-from-url-html-zip-step}

Erstellt ein PDF-Dokument anhand der bereitgestellten URL-, HTML- und ZIP-Datei.

### Schritt „Daten exportieren“ {#export-data-step}

Exportiert Daten aus einem PDF-Formular oder aus einer XDP-Datei Sie müssen den Dateipfad des Eingabedokuments und das Exportdatenformat eingeben. Die Optionen für das Exportdatenformat sind Auto, XDP und XmlData.

### Schritt „PDF in den angegebenen Format exportieren“ {#export-pdf-to-specified-type-step}

Konvertiert ein PDF-Dokument in ein ausgewähltes Format.

### Schritt „Nicht interaktive PDF-Dateien generieren“ {#generatenoninteractive}

Generieren Sie eine nicht interaktive PDF-Datei. Es sind verschiedene Anpassungsoptionen verfügbar. 

>[!NOTE]
>
>Sie können Variablen verwenden, um die Vorlagendatei für Eingabedokumente anzugeben. Speichern Sie den Pfad der Vorlagendatei in einer Variablen des Datentyps „String“.

### Schritt „Daten importieren“ {#import-data-step}

Führt Formulardaten in einem PDF-Formular zusammen. Sie können Formulardaten in ein PDF-Formular importieren.

### Schritt „DDX aufrufen“ {#invokeddx}

Führt die DDX-Datei in der angegebenen Zuordnung von Eingabedokumenten aus und gibt die veränderten PDF-Dokumente zurück.

>[!NOTE]
>
>Sie können Variablen verwenden, um die DDX-Datei für Eingabedokumente anzugeben. Speichern Sie die DDX-Datei in einer Variablen des Datentyps „Document“ oder „XML“.

### Schritt „PDF optimieren“ {#optimize-pdf-step}

Optimiert PDF-Dateien durch Reduzierung ihrer Größe. Als Ergebnis dieser Konvertierung erhalten Sie PDF-Dateien, die eventuell kleiner sind als die Originalversionen. Bei diesem Vorgang werden außerdem PDF-Dokumente in die in den Optimierungsparametern angegebene PDF-Version konvertiert.

In den Optimierungseinstellungen wird festgelegt, wie Dateien optimiert werden. Im Folgenden finden Sie Beispieleinstellungen:

* PDF-Zielversion
* Verwerfen von Objekten wie JavaScript-Aktionen und eingebetteten Seitenminiaturansichten
* Verwerfen von Benutzerdaten wie Kommentaren und Dateianlagen
* Verwerfen ungültiger oder nicht verwendeter Einstellungen
* Komprimieren unkomprimierter Daten oder Verwenden effizienterer Komprimierungsalgorithmen
* Entfernen eingebetteter Schriftarten
* Festlegen von Transparenzwerten

### Schritt „PDF-Formular ausgeben“ {#renderpdf}

Rendert ein Formular, das in Form Designer (XDP) erstellt wurde, in ein PDF-Formular.

>[!NOTE]
>
>Sie können Variablen verwenden, um die Vorlagendatei für Eingabedokumente anzugeben. Speichern Sie den Pfad der Vorlagendatei in einer Variablen des Datentyps „String“.

### Schritt „Dokument absichern“ {#secure-document-step}

Verschlüsseln, signieren und zertifizieren Sie ein Dokument. AEM Forms unterstützt sowohl die kennwortbasierte als auch die zertifikatsbasierte Verschlüsselung. Sie können auch zwischen verschiedenen Algorithmen zum Signieren von Dokumenten wählen. Zum Beispiel SHA-256 und SH-512. Sie können den Workflow-Schritt zum Reader Extending von PDF-Dokumenten verwenden. Der Workflow-Schritt bietet Optionen zum Aktivieren von Barcode-Dekodierung, digitalen Signaturen, Importieren und Exportieren von PDF-Daten und anderen Optionen.

### Schritt „An Drucker senden“ {#send-to-printer-step}

Senden Sie ein Dokument direkt an einen Drucker. Der Dienst unterstützt die folgenden Druckerzugriffsmechanismen:

* **Drucker mit direktem Zugriff**: Ein Drucker, der auf demselben Computer installiert ist, wird als Drucker mit direktem Zugriff und der Computer als Druckerhost bezeichnet. Dieser Druckertyp kann ein lokaler Drucker sein, der direkt an den Computer angeschlossen ist.
* **Drucker mit indirektem Zugriff**: Der Drucker, der auf einem Druckserver installiert ist, steht für den Zugriff von anderen Computern zur Verfügung. Es stehen Technologien wie das Common UNIX® Printing System (CUPS) und das LPD-Protokoll (Line Printer Daemon) zur Verfügung, um eine Verbindung zu einem Netzwerkdrucker herzustellen. Um auf einen Drucker mit indirektem Zugriff zuzugreifen, geben Sie die IP oder den Hostnamen des Druck-Servers an. Bei Verwendung dieses Mechanismus können Sie ein Dokument an einen LPD-URI senden, wenn im Netzwerk ein LP-Daemon ausgeführt wird. Mit dem Mechanismus können Sie das Dokument zu jedem Drucker weiterleiten, der mit dem Netzwerk verbunden ist, in dem ein LP-Daemon ausgeführt wird.

### Generieren des Schritts für die gedruckte Ausgabe {#generatePrintedOutput}

Dieser Schritt generiert eine PCL-, PostScript-, ZPL-, IPL-, TPCL- oder DPL-Ausgabe aus einem Formularentwurf und einer Datendatei. Die Datendatei wird mit dem Formularentwurf zusammengeführt und für den Druck formatiert. Die von diesem Schritt generierte Ausgabe kann direkt an einen Drucker gesendet oder als Datei gespeichert werden. Es wird empfohlen, diesen Schritt zu verwenden, wenn Sie Formularentwürfe oder Daten aus einem Programm verwenden möchten. Wenn sich Ihre Formularentwürfe oder Daten im Netzwerk, einem lokalen Dateisystem oder einem HTTP-Speicherort befinden, verwenden Sie den Vorgang generatePrintedOutput.

Beispiel: Ihre Anwendung erfordert, dass Sie einen Formularentwurf mit einer Datendatei zusammenführen. Die Daten beinhalten Hunderte von Datensätzen. Außerdem muss die Ausgabe an einen Drucker gesendet werden, der ZPL unterstützt. Der Formularentwurf und Ihre Eingabedaten befinden sich in einer Anwendung. Verwenden Sie den generatePrintedOutput-Vorgang, um einzelne Datensätze mit einem Formularentwurf zusammenführen und die Ausgabe an einen Drucker zu senden, der ZPL unterstützt.

Der Schritt „Gedruckte Ausgabe generieren“ hat die folgenden Eigenschaften:

**Eingabeeigenschaften**

* **[!UICONTROL Vorlagendatei auswählen mit]**: Geben Sie den Pfad der Vorlagendatei an. Sie können die Vorlagendatei auswählen, indem Sie den Pfad relativ zur Nutzlast, einen absoluten Pfad oder eine Variable vom Datentyp „Document“ verwenden. Beispiel: [Payload_Directory]/Workflow/data.xml. Wenn der Pfad nicht im CRX-Repository vorhanden ist, kann ein Administrator den Pfad erstellen, bevor er ihn verwendet. Darüber hinaus können Sie auch Payload als Eingabedatendatei akzeptieren.

* **[!UICONTROL Datendokument auswählen mit]**: Geben Sie den Pfad einer Eingabedatendatei an. Sie können die Eingabedatendatei auswählen, indem Sie den Pfad relativ zum Payload, einen absoluten Pfad oder eine Variable vom Datentyp „Document“ verwenden. Beispiel: [Payload_Directory]/Workflow/data.xml. Wenn der Pfad nicht im CRX-Repository vorhanden ist, kann ein Administrator den Pfad erstellen, bevor er ihn verwendet.

* **[!UICONTROL Druckerformat]**: Ein Druckformatwert, der beim Fehlen einer XDC-Datei die zu verwendende Sprache der Seitenbeschreibung angibt, um den Ausgabe-Stream zu generieren. Wenn Sie einen Literalwert angeben, wählen Sie einen der folgenden Werte:

   * **[!UICONTROL Benutzerdefinierte PCL]**: Verwenden Sie diese Option, um eine benutzerdefinierte XDC-Datei für PCL anzugeben.
   * **[!UICONTROL Benutzerdefiniertes PostScript]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei für PostScript anzugeben.
   * **[!UICONTROL Benutzerdefiniertes ZPL]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Dateidatei für ZPL anzugeben.
   * **[!UICONTROL Generische Farb-PCL (5c)]**: Verwenden Sie eine generische Farb-PCL (5c).
   * **[!UICONTROL Generisches PostScript Level3]**: Verwenden Sie generisches PostScript der Ebene 3.
   * **[!UICONTROL ZPL 300 DPI]**: Verwenden Sie ZPL mit 300 DPI. Die Datei zpl300.xdc wird verwendet.
   * **[!UICONTROL ZPL 600 DPI]**: Verwenden Sie ZPL mit 600 DPI. Die Datei zpl600.xdc wird verwendet.
   * **[!UICONTROL Benutzerdefiniertes IPL]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei für IPL anzugeben.
   * **[!UICONTROL IPL 300 DPI]**: Verwenden Sie IPL mit 300 DPI. Die Datei ipl300.xdc wird verwendet.
   * **[!UICONTROL IPL 400 DPI]**: Verwenden Sie IPL mit 400 DPI. Die Datei ipl400.xdc wird verwendet.
   * **[!UICONTROL Benutzerdefiniertes TPCL]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei für TPCL anzugeben.
   * **[!UICONTROL TPCL 305 DPI]**: Verwenden Sie TPCL mit 300 DPI. Die Datei tpcl305.xdc wird verwendet.
   * **[!UICONTROL PCL 600 DPI]**: Verwenden Sie TPCL mit 600 DPI. Die Datei tpcl600.xdc wird verwendet.
   * **[!UICONTROL Benutzerdefiniertes DPL]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei für DPL anzugeben.
   * **[!UICONTROL DPL300DPI]**: Verwenden Sie DPL mit 300 DPI. Die Datei dpl300.xdc wird verwendet.
   * **[!UICONTROL DPL406DPI]**: Verwenden Sie DPL mit 400 DPI. Die Datei dpl406.xdc wird verwendet.
   * **[!UICONTROL DPL600DPI]**: Verwenden Sie DPL mit 600 DPI. Die Datei dpl600.xdc wird verwendet.

**Ausgabeeigenschaften**

* **[!UICONTROL Ausgabedokument speichern mit]**: Geben Sie den Speicherort für die Ausgabedatei an. Sie können die Ausgabedatei an einem Speicherort speichern, der relativ zur Payload ist, in einer Variablen oder einen absoluten Speicherort für die Ausgabedatei angeben. Wenn der Pfad nicht im CRX-Repository vorhanden ist, kann ein Administrator den Pfad erstellen, bevor er ihn verwendet.

**Erweiterte Eigenschaften**

* **[!UICONTROL Speicherort des Inhaltsstamms auswählen mit]**: Der Inhaltsstamm ist ein Zeichenfolgenwert, der den URI, den absoluten Verweis oder den Speicherort im Repository angibt, um relative Elemente abzurufen, die vom Formularentwurf verwendet werden. Beispiel: Wenn der Formularentwurf relativ auf ein Bild verweist, z. B. ../myImage.gif, muss sich myImage.gif unter repository:// befinden. Der Standardwert ist repository://, der auf die Stammebene des Repositorys verweist.

   Wenn Sie ein Asset aus Ihrer Anwendung auswählen, muss der Inhaltsstamm-URI-Pfad die richtige Struktur aufweisen. Wenn beispielsweise ein Formular aus einer Anwendung namens SampleApp unter SampleApp/1.0/forms/Test.xdp gespeichert wird, muss der Inhaltsstamm-URI als repository://administrator@password/Applications/SampleApp/1.0/forms/ oder repository:/Applications/SampleApp/1.0/forms/ (wenn die Berechtigung null ist) angegeben werden. Wenn der Inhaltsstamm-URI auf diese Weise angegeben wird, werden die Pfade aller referenzierten Elemente im Formular für diesen URI aufgelöst.

* **[!UICONTROL XCI-Datei auswählen mit]**: XCI-Dateien werden verwendet, um Schriftarten und andere Eigenschaften zu beschreiben, die für Formularentwurfselemente verwendet werden. Sie können eine XCI-Datei relativ zur Payload, in einem absoluten Pfad oder mithilfe einer Variablen des Datentyps „Document“ beibehalten.

* **[!UICONTROL Gebietsschema]**: Legt die Sprache fest, die zum Generieren des PDF-Dokuments verwendet wird. Wenn Sie einen Literalwert angeben, wählen Sie eine Sprache aus der Liste oder einen der folgenden Werte:
   * **So verwenden Sie den Server-Standard**: 
(Standard) Verwenden Sie die Einstellung „Gebietsschema“, die auf dem AEM Forms-Server konfiguriert ist. Die Einstellung „Gebietsschema“ wird mit der Administration Console konfiguriert. (Weitere Informationen finden Sie in der [Designer-Hilfe](http://www.adobe.com/go/learn_aemforms_designer_65_de).)

   * **So verwenden Sie einen benutzerdefinierten Wert**: 
Geben Sie den Gebietsschema-Code in das Feld „Literal“ ein oder wählen Sie eine Zeichenfolgenvariable aus, die den Gebietsschema-Code enthält. Eine vollständige Liste der unterstützten Gebietsschemas finden Sie unter http://java.sun.com/j2se/1.5.0/docs/guide/intl/locale.doc.html.

* **[!UICONTROL Kopien]**: Ein ganzzahliger Wert, der die Anzahl der Kopien angibt, die für die Ausgabe generiert werden. Der Standardwert ist 1.

* **[!UICONTROL Duplexdruck]**: Ein Paginierungswert, der angibt, ob zweiseitiger oder einseitiger Druck verwendet werden soll. Drucker, die PostScript und PCL unterstützen, verwenden diesen Wert. Wenn Sie einen Literalwert angeben, wählen Sie einen der folgenden Werte aus:
   * **[!UICONTROL Duplex, lange Kante]**: Verwenden Sie den zweiseitiger Druck und die Paginierung erfolgt an langen Kanten.
   * **[!UICONTROL Duplex, kurze Kante]**: Verwenden Sie den zweiseitigen Druck mit Paginierung an kurzen Kanten.
   * **[!UICONTROL Simplex]**: Verwenden Sie den einseitigen Druck.
