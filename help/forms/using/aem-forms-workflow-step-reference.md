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
source-git-commit: d9608d584e822accc0c198fcf1d1b706d065938e
workflow-type: tm+mt
source-wordcount: '7466'
ht-degree: 65%

---

# Formularzentrierte Workflows in OSGi - Schritt-Referenz {#forms-centric-workflow-on-osgi-step-reference}

Mit Workflow-Modelle können Sie eine Business-Logik in einen automatisierten, sich wiederholenden Prozess umwandeln. Anhand eines Modells können Sie eine Reihe von Schritten definieren und ausführen. Sie können auch Modelleigenschaften definieren, um beispielsweise festzulegen, ob es sich um einen Übergangs-Workflow oder einen Workflow mit mehreren Ressourcen handelt. Sie können [verschiedene AEM-Workflow-Schritte in ein Modell aufnehmen, um die Business-Logik zu erzielen](/help/sites-developing/workflows-models.md#extending-aem).

## Schritte für den Forms-Workflow {#forms-workflow-steps}

Schritte für den Forms-Workflow führen AEM Forms-spezifische Vorgänge in einem AEM-Workflow durch. Diese Schritte ermöglichen das schnelle Erstellen adaptiver formularzentrierter Workflows auf OSGi. Diese Workflows können zur Entwicklung grundlegender Prüfungs- und Genehmigungs-Workflows, interner und branchenübergreifender Geschäftsprozesse verwendet werden. Sie können die Forms-Workflow-Schritte außerdem verwenden, um Document Services zu starten, Adobe Sign-Signatur-Workflow zu integrieren und andere AEM Forms-Vorgänge auszuführen. Sie benötigen das [AEM Forms Add-On](https://www.adobe.com/go/learn_aemforms_documentation_63), um diese Schritte in einem Workflow zu verwenden.

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
* **Typ:** Wählen Sie den Typ des Dokuments, das ausgefüllt werden soll, wenn der Workflow gestartet wird. Sie können ein adaptives Formular, ein schreibgeschütztes adaptives Formular, ein nicht interaktives PDF-Dokument, die Benutzeroberfläche für interaktive Kommunikationsagenten oder ein Webkanaldokument für interaktive Kommunikation auswählen.
* **Adaptives Formular verwenden:** Geben Sie die Methode an, um das adaptive Formular für die Eingabe zu suchen. Diese Option ist verfügbar, wenn Sie aus der Dropdownliste Typ die Option Adaptives Formular oder Schreibgeschütztes adaptives Formular auswählen. Sie können das adaptive Formular verwenden, das an den Workflow gesendet wurde, das in einem absoluten Pfad verfügbar ist oder in einem Pfad in einer Variablen verfügbar ist. Sie können eine Variable des Typs „Zeichenfolge“ verwenden, um den Pfad anzugeben.\
   Sie können mehrere adaptive Formulare mit einem Workflow verknüpfen. Daher können Sie mithilfe der verfügbaren Eingabemethoden ein adaptives Formular zur Laufzeit angeben.

* **Interaktive Kommunikation verwenden:** Geben Sie die Methode an, nach der die interaktive Eingabekommunikation lokalisiert werden soll. Sie können die interaktive Kommunikation verwenden, die an den Workflow gesendet wurde, in einem absoluten Pfad verfügbar ist oder in einem Pfad in einer Variablen verfügbar ist. Sie können eine Variable des Typs „Zeichenfolge“ verwenden, um den Pfad anzugeben. Diese Option ist verfügbar, wenn Sie die Benutzeroberfläche des interaktiven Kommunikationsagenten oder das Webkanaldokument der interaktiven Kommunikation aus der Dropdownliste Typ auswählen.

>[!NOTE]
>
>Sie müssen über Gruppenzuweisungen für cm-agent-users und workflow-users verfügen, um in AEM Posteingang auf die Benutzeroberfläche von Interactive Communications Agent zuzugreifen.

* **Adaptives Formular oder Pfad zur interaktiven Kommunikation**: Geben Sie den Pfad des adaptiven Formulars oder der interaktiven Kommunikation an. Sie können das adaptive Formular oder die interaktive Kommunikation verwenden, die an den Workflow gesendet werden, der in einem absoluten Pfad verfügbar ist, oder das adaptive Formular aus einem Pfad abrufen, der in einer Variablen des Datentyps Zeichenfolge gespeichert ist.
* **Wählen Sie die Eingabe-PDF mit:** Geben Sie den Pfad eines nicht interaktiven PDF-Dokuments an. Das Feld ist verfügbar, wenn Sie im Feld „Typ“ ein nicht interaktives PDF-Dokument auswählen. Sie können die PDF-Eingabedatei unter Verwendung des Pfads auswählen, der relativ zur Payload ist, unter einem absoluten Pfad gespeichert wird oder eine Variable des Datentyps „Dokument“ verwendet. Beispiel: [Payload_Directory]/Workflow/PDF/credit-card.pdf. Der Pfad existiert nicht im CRX-Repository. Ein Administrator erstellt den Pfad, bevor er ihn verwendet. Sie benötigen ein Formular mit aktivierter Option „Datensatzdokument“ oder auf Vorlagen basierende adaptive Formulare, um die PDF-Pfad-Komponente zu verwenden.
* **Für abgeschlossene Aufgaben rendern Sie das adaptive Formular wie folgt**: Wenn eine Aufgabe als abgeschlossen markiert ist, können Sie das adaptive Formular als schreibgeschütztes adaptives Formular oder PDF-Dokument ausgeben. Sie benötigen ein Formular mit aktivierter Option „Datensatzdokument“ oder auf Vorlagen basierende adaptive Formulare zum Rendern des adaptiven Formulars als Datensatzdokument.
* **Vorausgefüllt:** Die folgenden Felder dienen als Eingaben für die Aufgabe:

   * **[!UICONTROL Eingabedatendatei auswählen mit]**: Pfad der Eingabedatendatei (.json, .xml, .doc oder Formulardatenmodell). Sie können die Eingabedatendatei mit einem Pfad abrufen, der relativ zur Payload ist, oder die Datei abrufen, die in einer Variablen des Datentyps Dokument, XML oder JSON gespeichert ist. Beispielsweise enthält die Datei die Daten, die über eine AEM-Posteingangsanwendung für das Formular übermittelt werden. Ein Beispielpfad ist [Payload_Directory]/workflow/data.

   * **Wählen Sie Eingabeanhänge mit:** Die am Speicherort verfügbaren Anlagen werden an das Formular angehängt, das mit der Aufgabe verknüpft ist. Der Pfad kann relativ zur Payload sein oder die Anlagen abrufen, die in einer Variablen des Typs ArrayList of Document gespeichert sind. Ein Beispielpfad ist [Payload_Directory]/attachments/. Sie können Anlagen angeben, die relativ zur Payload platziert werden, oder eine Dokumenttyp-Variable („Array-Liste“ > „Dokument“) verwenden, um einen Eingabeanhang für das adaptive Formular anzugeben..

      * **Eingabe-JSON auswählen:** Wählen Sie eine JSON-Eingabedatei anhand eines Pfads aus, der relativ zur Payload ist oder in einer Variablen des Datentyps &quot;Dokument&quot;, &quot;JSON&quot;oder &quot;Formulardatenmodell&quot;gespeichert ist. Diese Option ist verfügbar, wenn Sie die Benutzeroberfläche des interaktiven Kommunikationsagenten oder das Webkanaldokument der interaktiven Kommunikation aus der Dropdownliste Typ auswählen.
      * **Wählen Sie einen benutzerdefinierten Vorbefüllungs-Dienst aus:** Wählen Sie den Vorbefüllungs-Dienst aus, um die Daten abzurufen und das Webkanaldokument zur interaktiven Kommunikation oder die Benutzeroberfläche für Agenten vorab auszufüllen.
      * **Verwenden Sie den Vorbefüllungs-Dienst der oben ausgewählten interaktiven Kommunikation:** Verwenden Sie diese Option, um den Vorbefüllungs-Dienst der interaktiven Kommunikation zu verwenden, der in der Dropdown-Liste Interaktive Kommunikation verwenden definiert ist.
      * **Anforderungsattributzuordnung:** Verwenden Sie den Abschnitt Anforderungsattribut-Zuordnung , um die [Name und Wert des Anforderungsattributs](../../forms/using/work-with-form-data-model.md#bindargument). Rufen Sie die Details aus der Datenquelle basierend auf dem in der Anforderung angegebenen Attributnamen und -wert ab. Sie können einen Wert für das Anforderungsattribut mit einem Literalwert oder einer Variablen des Datentyps „Zeichenfolge“ definieren.\
         Die Zuordnungsoptionen für Vorbefüllungs- und Anforderungsattribute sind nur verfügbar, wenn Sie in der Dropdownliste Typ die Option Interaktive Kommunikationsagent oder Webkanaldokument für interaktive Kommunikation auswählen.

* **Gesendete Informationen:** Die folgenden Felder dienen als Ausgabespeicherorte für die Aufgabe:

   * **Speichern Sie die Ausgabedatendatei mit:** Speichern Sie die Datendatei (.json,). XML, .doc oder Formulardatenmodell). Die Datendatei enthält Informationen, die über das zugeordnete Formular übermittelt werden. Sie können die Ausgabedatendatei unter Verwendung eines Pfads speichern, der relativ zur Payload ist, oder sie in einer Variablen des Datentyps „Dokument“, XML oder JSON speichern. Zum Beispiel [Payload_Directory]/Workflow/data, wobei „data“ für eine Datei steht.
   * **Speichern von Anlagen mit:** Speichern Sie die in einer Aufgabe bereitgestellten Formularanhänge. Sie können die Anlagen mit einem Pfad speichern, der relativ zur Payload ist, oder sie in einer Variablen des Arrays des Dokumentdatentyps speichern.
   * **Speichern Sie das Datensatzdokument mit:** Pfad zum Speichern einer Datensatzdokumentdatei. Beispielsweise [Payload_Directory]/DocumentofRecord/credit-card.pdf. Sie können das Datensatzdokument unter Verwendung eines Pfads speichern, der relativ zur Payload ist, oder es in einer Variablen des Datentyps „Dokument“ speichern. Wenn Sie die Option **Relativ zur Payload** auswählen, wird das Datensatzdokument nicht generiert, wenn das Feld „Pfad“ leer bleibt. Diese Option ist nur verfügbar, wenn Sie Adaptives Formular aus der Dropdownliste Typ auswählen.

   * **Speichern Sie Webkanaldaten mithilfe von:** Speichern Sie die Webkanal-Datendatei mit einem Pfad, der relativ zur Payload ist, oder speichern Sie sie in einer Variablen des Datentyps &quot;Dokument&quot;, &quot;JSON&quot;oder &quot;Formulardatenmodell&quot;. Diese Option ist nur verfügbar, wenn Sie in der Dropdown-Liste Typ die Option Interaktive Kommunikationsagent-Benutzeroberfläche auswählen.
   * **Speichern Sie das PDF-Dokument mit:** Speichern Sie das PDF-Dokument mit einem Pfad, der relativ zur Payload ist, oder speichern Sie es in einer Variablen des Dokumentdatentyps. Diese Option ist nur verfügbar, wenn Sie in der Dropdown-Liste Typ die Option Interaktive Kommunikationsagent-Benutzeroberfläche auswählen.
   * **Speichern Sie die Layout-Vorlage mit:** Speichern Sie die Layout-Vorlage mit einem Pfad, der relativ zur Payload ist, oder speichern Sie sie in einer Variablen des Dokumentdatentyps. Die [Layoutvorlage](../../forms/using/layout-design-details.md) bezieht sich auf eine XDP-Datei, die Sie mit Forms Designer erstellen. Diese Option ist nur verfügbar, wenn Sie in der Dropdown-Liste Typ die Option Interaktive Kommunikationsagent-Benutzeroberfläche auswählen.

* **Zuweisung > Optionen zuweisen:** Geben Sie die Methode an, um die Aufgabe einem Benutzer zuzuweisen. Sie können die Aufgabe dynamisch einem Benutzer oder einer Gruppe zuweisen, indem Sie das Skript „Teilnehmerauswahl“ verwenden oder die Aufgabe einem bestimmten AEM-Benutzer oder einer bestimmten Gruppe zuweisen.
* **Teilnehmerauswahl:** Die Option ist verfügbar, wenn die Option **Dynamically to a user or group (Dynamisch zu einem Benutzer oder einer Gruppe)** im Feld „Optionen zuweisen“ ausgewählt ist. Sie können ein ECMAScript oder einen Service verwenden, um einen Benutzer oder eine Gruppe dynamisch auszuwählen. Weitere Informationen finden Sie im Abschnitt [Dynamisches Zuweisen eines Workflows zu Benutzern](https://helpx.adobe.com/de/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) und [Erstellen eines benutzerdefinierten Schritts „Dynamischer Teilnehmer in Adobe Experience Manager“.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en&amp;CID=RedirectAEMCommunityKautuk)

* **Teilnehmer:** Das Feld ist verfügbar, wenn die Option **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]****im Feld „Teilnehmerauswahl“ ausgewählt ist.** In diesem Feld können Sie Benutzer oder Gruppen für die Option „RandomParticipantChooser“ auswählen.

* **Bevollmächtigter:** Das Feld ist verfügbar, wenn die Variable **[!UICONTROL com.adobe.fd.workspace.step.service.VariableParticipantChooser]** wird im **Teilnehmerauswahl** -Feld. Mit dem Feld können Sie eine Variable des Datentyps „Zeichenfolge“ auswählen, um den Verantwortlichen zu definieren.

* **Argumente:** Das Feld ist verfügbar, wenn ein anderes als das Skript „RandomParticipantChoose“ im Feld „Teilnehmerauswahl“ ausgewählt wurde. In diesem Feld können Sie eine Liste mit durch Kommas getrennten Argumenten für das im Feld „Teilnehmerauswahl“ ausgewählte Skript angeben.

* **Benutzer oder Gruppe:** Die Aufgabe wurde dem ausgewählten Benutzer oder der Gruppe zugewiesen. Die Option ist verfügbar, wenn die Option **Zu einem bestimmten Benutzer bzw. einer bestimmten Gruppe** im Feld **Optionen zuweisen** ausgewählt ist. Das Feld listet alle Benutzer und Gruppen der Workflow-Benutzergruppe auf.\
   Das Dropdownmenü **Benutzer oder Gruppe** führt die Benutzer und Gruppen auf, auf die der angemeldete Benutzer Zugriff hat. Die Anzeige des Benutzernamens hängt davon ab, ob Sie über Zugriffsberechtigungen für den Knoten **users** im CRX-Repository für diesen bestimmten Benutzer verfügen.

* **[!UICONTROL E-Mail-Benachrichtigung senden]**: Wählen Sie diese Option aus, um E-Mail-Benachrichtigungen an den Verantwortlichen zu senden. Diese Benachrichtigungen werden gesendet, wenn eine Aufgabe einem Benutzer oder einer Gruppe zugewiesen wird. Mit der Option **[!UICONTROL Empfänger-E-Mail-Adresse]** können Sie den Mechanismus zum Abrufen der E-Mail-Adresse angeben.

* **[!UICONTROL Empfänger-E-Mail-Adresse]**: Sie können die E-Mail-Adresse in einer Variablen speichern, mit einem Literal eine permanente E-Mail-Adresse angeben oder die Standard-E-Mail-Adresse des Verantwortlichen verwenden, die in seinem Profil angegeben ist. Sie können das Literal oder eine Variable verwenden, um die E-Mail-Adresse einer Gruppe anzugeben. Die Option „Variable“ ist beim dynamischen Abrufen und Verwenden einer E-Mail-Adresse hilfreich. Die Option **[!UICONTROL Standardmäßige E-Mail-Adresse des Verantwortlichen verwenden]** gilt nur für einen einzelnen Verantwortlichen. In diesem Fall wird die E-Mail-Adresse verwendet, die im Benutzerprofil des Verantwortlichen gespeichert ist.

* **HTML-E-Mail-Vorlage**: Wählen Sie die E-Mail-Vorlage für die Benachrichtigungs-E-Mail. Um eine Vorlage zu bearbeiten, ändern Sie die Datei unter /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt im CRX-Repository.
* **Delegierung zulassen an:** AEM Inbox bietet dem angemeldeten Benutzer eine Option, den zugewiesenen Workflow an einen anderen Benutzer zu übertragen. Sie dürfen innerhalb derselben Gruppe oder an den Workflow-Benutzer einer anderen Gruppe delegieren. Wenn die Aufgabe einem einzelnen Benutzer zugewiesen ist und die Option **Delegierung an Mitglieder der Gruppe an Verantwortlichen zulassen** aktiviert ist, kann die Aufgabe nicht an einen anderen Benutzer oder eine andere Gruppe übertragen werden.
* **Freigabeeinstellungen:** AEM Posteingang bietet Optionen zum Freigeben einer einzelnen oder aller Aufgaben im Posteingang für andere Benutzer:
   * Wenn die **Bevollmächtigten explizit im Posteingang freigeben** ausgewählt ist, kann der Benutzer auf die Aufgabe klicken und sie für einen anderen AEM Benutzer freigeben.
   * Wenn die **Bevollmächtigten über die Freigabe im Posteingang zulassen** aktiviert ist und ein Benutzer seine Posteingangselemente weitergibt oder anderen Benutzern den Zugriff auf seine Posteingangselemente ermöglicht, werden nur Aufgaben, für die die oben genannte Option aktiviert ist, für andere Benutzer freigegeben.

* **Aktionen > Standardaktionen:** Standardmäßig sind die Aktionen &quot;Senden&quot;, &quot;Speichern&quot;und &quot;Zurücksetzen&quot;verfügbar. Alle Standardaktionen sind standardmäßig aktiviert.
* **Route-Variable:** Name der Route-Variablen. Die Route-Variable erfasst benutzerdefinierte Aktionen, die ein Benutzer im AEM-Posteingang auswählt.
* **Routen:** Eine Aufgabe kann auf verschiedene Routen verzweigen. Bei Auswahl im AEM-Posteingang gibt die Route einen Wert zurück, und der Workflow verzweigt basierend auf der ausgewählten Route. Sie können Routen entweder in einer Variablen des Arrays des Datentyps „Zeichenfolge“ speichern oder **Literal** auswählen, um Routen manuell hinzuzufügen.

* **Routentitel**: Geben Sie den Titel für die an. Er wird im AEM-Posteingang angezeigt.
* **Korallensymbol**: Geben Sie das HTML-Attribut eines Korallensymbols an. Die Adobe CoralUI-Bibliothek bietet eine Vielzahl von Touch-First-Symbolen. Sie können ein Symbol für die Route auswählen und verwenden. Es wird zusammen mit dem Titel im AEM-Posteingang angezeigt. Wenn Sie die Routen in einer Variablen speichern, verwenden die Routen ein standardmäßiges „Tags“-Korallensymbol.
* **Zulassen, dass Verantwortlicher Kommentare hinzufügt**: Wählen Sie diese Option, um Kommentare für die Aufgabe zu aktivieren. Ein Verantwortlicher kann die Kommentare innerhalb des AEM-Posteingangs zum Zeitpunkt der Aufgabenübermittlung hinzufügen.
* **Kommentar in Variable speichern:** Speichern Sie den Kommentar in einer Variablen des Datentyps String . Diese Option wird nur angezeigt, wenn Sie das Kontrollkästchen **Zulassen, dass Verantwortlicher Kommentare hinzufügt** aktivieren.

* **Bevollmächtigtem erlauben, Anlage(n) der Aufgabe hinzuzufügen**: Wählen Sie diese Option, um Anlagen für die Aufgabe zu aktivieren. Ein Verantwortlicher kann die Anhänge im AEM-Posteingang zum Zeitpunkt der Aufgabenübermittlung hinzufügen.
* **Aufgabenanhänge speichern mit**: Geben Sie den Speicherort des Anhangsordners an. Sie können Ausgabeaufgabenanhänge mit einem Pfad relativ zur Payload oder in einer Variablen des Arrays des Datentyps „Dokument“ speichern. Diese Option wird nur angezeigt, wenn Sie **Bevollmächtigten erlauben, Anlagen zur Aufgabe hinzuzufügen** Kontrollkästchen und wählen Sie **Adaptives Formular**, **Schreibgeschütztes adaptives Formular** oder **Nicht interaktives PDF-Dokument** von **Typ** Dropdown-Liste im **Formular/Dokument** Registerkarte.

>[!NOTE]
>
>Verwenden Sie während der Laufzeit die Registerkarte Anlagen in der Benutzeroberfläche für Agenten , um die Anlagen einer interaktiven Kommunikation zuzuordnen. Die zugehörigen Anlagen werden nach dem Öffnen des Arbeitselements in einem Complete -Status als Aufgabenanlagen im Sidekick angezeigt.

* **Benutzerdefinierte Metadaten verwenden:** Wählen Sie diese Option, um das benutzerdefinierte Metadatenfeld zu aktivieren. Benutzerdefinierte Metadaten werden in E-Mail-Vorlagen verwendet.
* **Benutzerdefinierte Metadaten:** Wählen Sie benutzerdefinierte Metadaten für die E-Mail-Vorlagen. Die benutzerdefinierten Metadaten sind im CRX-Repository unter apps/fd/dashboard/scripts/metadataScripts verfügbar. Der angegebene Pfad existiert nicht im CRX-Repository. Ein Administrator erstellt den Pfad, bevor er ihn verwendet. Sie können auch einen Service für die benutzerdefinierten Metadaten verwenden. Sie können auch die WorkitemUserMetadataService-Schnittstelle erweitern, um benutzerdefinierte Metadaten bereitzustellen.
* **Daten aus vorherigen Schritten anzeigen**: Wählen Sie - falls verfügbar - diese Option aus, um den Bevollmächtigten das Anzeigen früherer Bevollmächtigter, bereits vorgenommener Aktionen, Kommentare zu dieser Aufgabe und des Nachweisdokuments über abgeschlossene Aufgaben zu ermöglichen.
* **Daten aus allen nachfolgenden Schritten einblenden:** Wählen Sie diese Option, um dem aktuellen Bearbeiter zu ermöglichen, die durchgeführte Aktion und Kommentare, die von nachfolgenden Beauftragten zur Aufgabe hinzugefügt wurden, anzuzeigen. Außerdem kann sich der aktuelle Bevollmächtigte ein Dokument als Nachweis über die abgeschlossenen Aufgaben anzeigen lassen - sofern verfügbar.
* **Sichtbarkeit des Datentyps:** Standardmäßig kann ein Bevollmächtigter ein Datensatzdokument, Bevollmächtigte, durchgeführte Aktionen und Kommentare anzeigen, die frühere und nachfolgende Bevollmächtigte hinzugefügt haben. Verwenden Sie die Option „Sichtbarkeit des Datentyps“, um den Typ der für die Verantwortlichen sichtbaren Daten zu begrenzen.

>[!NOTE]
>
>Die Optionen zum Speichern des Schritts &quot;Aufgabe zuweisen&quot;als Entwurf und zum Abrufen des Verlaufs des Schritts &quot;Aufgabe zuweisen&quot;sind deaktiviert, wenn Sie eine [!DNL Adobe Experience Manager] Workflow-Modell für die externe Datenspeicherung. Außerdem ist die Option zum Speichern im Posteingang deaktiviert.

## Schritt „E-Mail senden“ {#send-email-step}

Verwenden Sie den E-Mail-Schritt, um eine E-Mail zu senden, z. B. eine E-Mail mit einem Dokument, einen Link eines adaptiven Formulars, einen Link einer interaktiven Kommunikation oder ein angehängtes PDF-Dokument. Der Schritt „E-Mail senden“ unterstützt [HTML-E-Mails](https://de.wikipedia.org/wiki/HTML_email). HTML-E-Mails sind responsive und passen sich an den E-Mail-Client und die Bildschirmgröße des Empfängers an. Sie können eine HTML-E-Mail-Vorlage verwenden, um das Erscheinungsbild, das Farbschema und Verhalten der E-Mail zu definieren.

Beim E-Mail-Schritt wird der Day CQ Mail Service zum Senden von E-Mails verwenden. Bevor Sie den E-Mail-Schritt verwenden, stellen Sie sicher, dass der [E-Mail-Dienst](../../forms/using/aem-forms-workflow.md) konfiguriert wurde. Der E-Mail-Schritt hat folgende Eigenschaften:

**Titel:** Der Titel des Schritts hilft beim Identifizieren des Schritts im Workflow-Editor.

**Beschreibung:** Erklärungen können für andere Entwickler nützlich sein, wenn Sie in einer gemeinsamen Entwicklungsumgebung arbeiten.

**E-Mail-Betreff:** Betreff kann aus Workflow-Metadaten abgerufen, manuell angegeben oder aus dem in einer Variablen gespeicherten Wert abgerufen werden. Zur Auswahl stehen:

* **Literal** – Geben Sie ein Thema manuell an.
* **Aus Workflow-Metadaten abrufen** – Sie können den Betreff von einer Metadateneigenschaft abrufen.
* **Variable** – Sie können den Betreff aus dem Wert abrufen, der in einer Variablen des Datentyps „Zeichenfolge“ gespeichert ist.

**HTML-E-Mail-Vorlage**: HTML-Vorlage für die E-Mail. Sie können Variablen in einer E-Mail-Vorlage spezifizieren. Der E-Mail-Schritt extrahiert und zeigt alle Variablen an, die in einer Vorlage für Eingaben enthalten sind.

**E-Mail-Vorlagenmetadaten:** Der Wert der E-Mail-Vorlagenvariablen kann ein vom Benutzer angegebener Wert, der Pfad eines Assets auf dem Autor- oder Veröffentlichungsserver, Bild oder eine Workflow-Metadateneigenschaft sein.

* **Literal:** Verwenden Sie die Option, wenn Sie den genauen Wert kennen, der angegeben werden soll. Beispiel: [beispiel@beispiel.com](mailto:example@example.com).

* **Workflow-Metadaten:** Verwenden Sie die Option, wenn der zu verwendende Wert in einer Workflow-Metadaten-Eigenschaft gespeichert wird. Nachdem Sie die Option ausgewählt haben, geben Sie den Namen der Metadateneigenschaft in das leere Textfeld unter der Option „Workflow-Metadaten“ ein. Beispiel: e-mailAdresse.
* **Asset-URL:** Verwenden Sie die Option, um einen Web-Link einer interaktiven Kommunikation in die E-Mail einzubetten. Nachdem Sie die Option ausgewählt haben, durchsuchen Sie die einzubettende interaktive Kommunikation und wählen Sie sie aus. Das Asset kann sich auf dem Autoren- oder dem Veröffentlichungsserver befinden.
* **Bild:** Verwenden Sie die Option, um ein Bild in die E-Mail einzubetten. Nachdem Sie die Option ausgewählt haben, suchen Sie nach dem entsprechenden Bild und wählen Sie es aus. Die Bildoption ist nur für die Bild-Tags (&lt;img src=&quot;&lt;span id=&quot; translate=&quot;no&quot; />&quot;/>) verfügbar, die in der E-Mail-Vorlage verfügbar sind.&#42;

**E-Mail-Adresse des Absenders/Empfängers:** Wählen Sie die **Literal** Option zur manuellen Angabe einer E-Mail-Adresse oder zur Auswahl der **Aus Workflow-Metadaten abrufen** -Option zum Abrufen der E-Mail-Adresse aus einer Metadateneigenschaft. Sie können auch eine Liste von Metadateneigenschaften-Arrays für die Option **Aus Workflow-Metadaten abrufen** angeben. Wählen Sie die Option **Variable** aus, um die E-Mail-Adresse aus dem Wert abzurufen, der in einer Variablen des Datentyps „Zeichenfolge“ gespeichert ist.

**Dateianhang:** Das am angegebenen Speicherort verfügbare Asset wird an die E-Mail angehängt. Der Pfad des Assets kann relativ zur Payload oder zum absoluten Pfad sein. Ein Beispielpfad ist [Payload_Directory]/attachments/.

Wählen Sie die Option **Variable**, um den in einer Variablen des Dateityps „Dokument“, XML oder JSON gespeicherte Dateianhang abzurufen.

**Dateiname:** Name der E-Mail-Anhangsdatei. Der E-Mail-Schritt ändert den Originaldateinamen des Anhangs in den angegebenen Dateinamen. Der Name kann manuell angegeben oder aus einer Workflow-Metadateneigenschaft oder einer Variable abgerufen werden. Verwenden Sie die Option **Literal**, wenn Sie den genauen zu spezifizierenden Wert kennen. Verwenden Sie die Option **Variable**, um den Dateinamen aus dem Wert abzurufen, der in einer Variablen des Datentyps „Zeichenfolge“ gespeichert ist. Verwenden Sie die Option **Aus Workflow-Metadaten abrufen**, wenn der zu verwendende Wert in einer Workflow-Metadateneigenschaft gespeichert wird.

## Schritt „Datensatzdokument generieren“ {#generate-document-of-record-step}

Wenn ein Formular ausgefüllt oder übermittelt wird, können Sie das Formular drucken oder als Dokument speichern. Dies wird als Datensatzdokument (DOR) bezeichnet. Sie können den Schritt „Generieren von Datensatzdokument“ verwenden, um eine schreibgeschützte oder interaktive PDF-Version eines adaptiven Formulars zu erstellen. Die PDF-Version enthält Informationen, die zusammen mit dem Layout des adaptiven Formulars in das Formular eingegeben werden.

Der Schritt „Datensatzdokument generieren“ hat folgende Eigenschaften:

**Adaptives Formular verwenden**: Geben Sie die Methode an, um das adaptive Formular für die Eingabe zu suchen. Sie können das adaptive Formular verwenden, das an den Workflow gesendet wurde, das in einem absoluten Pfad verfügbar ist oder in einem Pfad in einer Variablen verfügbar ist. Sie können eine Variable des Datentyps „Zeichenfolge“ verwenden, um den Pfad im Feld **Variable zur Auflösung auswählen** anzugeben.\
Sie können mehrere adaptive Formulare mit einem Workflow verknüpfen. Daher können Sie mithilfe der verfügbaren Eingabemethoden ein adaptives Formular zur Laufzeit angeben.

**Adaptiver Formularpfad**: Geben Sie den Pfad des adaptiven Formulars an. Das Feld ist verfügbar, wenn Sie die Option **Unter einem absoluten Pfad verfügbar** im Feld **Adaptives Formular verwenden** auswählen.

**Wählen Sie Eingabedaten mithilfe von aus:** Pfad der Eingabedaten für das adaptive Formular. Sie können die Daten an einem Speicherort relativ zur Payload speichern, einen absoluten Pfad der Daten angeben oder Daten abrufen, die in einer Variablen des Datentyps „Dokument“, JSON oder XML gespeichert sind. Die Eingabedaten werden mit dem adaptiven Formular zusammengeführt, um ein Datensatzdokument zu erstellen.

**Wählen Sie den Pfad für den Eingabeanhang mit:** Pfad der Anlagen. Diese Anhänge sind im Datensatzdokument enthalten. Sie können die Anhänge an einem Speicherort relativ zur Payload speichern, einen absoluten Pfad der Anhänge angeben oder Anhänge abrufen, die in einer Variablen des Datentyps „Dokument“ gespeichert sind.

Wenn Sie den Pfad eines Ordners angeben, z. B. Anhänge, werden alle Dateien, die direkt im Ordner verfügbar sind, an das Datensatzdokument angehängt. Wenn Dateien in den Ordnern verfügbar sind, die im angegebenen Pfad für den Anhang direkt verfügbar sind, werden die Dateien im Datensatzdokument als Anhänge aufgenommen. Wenn sich Ordner in direkt verfügbaren Ordnern befinden, werden diese übersprungen.

**Generiertes Datensatzdokument mit den folgenden Optionen speichern:** Geben Sie den Speicherort an, unter dem ein Datensatzdokument gespeichert werden soll. Sie können den Payload-Ordner überschreiben, das Datensatzdokument an einem Speicherort im Payload-Ordner ablegen oder das Datensatzdokument in einer Variablen des Dokumentdatentyps speichern.

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
   * **Variable:** Verwenden Sie die -Option, um den in einer Variablen gespeicherten Wert abzurufen.
   * **Aus Workflow-Metadaten abrufen:** Verwenden Sie die Option, wenn der zu verwendende Wert in einer Workflow-Metadaten-Eigenschaft gespeichert wird. Beispiel: e-mailAddress.
   * **[!UICONTROL Relativ zur Nutzlast]**: Verwenden Sie die Option zum Abrufen des Dateianhangs, der in einem Pfad relativ zur Payload gespeichert ist. Wählen Sie die Option aus und geben Sie entweder den Ordnernamen an, der den Dateianhang enthält, oder geben Sie den Dateinamen für den Anhang im Textfeld an.

      Wenn beispielsweise der Ordner „Relativ zur Nutzlast“ im CRX-Repository einen Dateianhang am Speicherort `attachment\attachment-folder` enthält, geben Sie `attachment\attachment-folder` im Textfeld an, nachdem Sie die Option **[!UICONTROL Relativ zur Nutzlast]** ausgewählt haben.
   * **JSON Dot Notation:** Verwenden Sie die Option, wenn der zu verwendende Wert in einer JSON-Datei enthalten ist. Beispiel: Insurance.customerDetails.emailAddress. Die Option JSON Dot Notation ist nur verfügbar, wenn die Option Eingabefelder aus Eingabe-JSON zuordnen ausgewählt ist.
   * **Zuordnen von Eingabefelder aus der Eingabe JSON:** Geben Sie den Pfad einer JSON-Datei an, um den Eingabewert einiger Service-Parameter aus der JSON-Datei abzurufen. Der Pfad der JSON-Datei kann relativ zur Payload bzw. zu einem absoluten Pfad sein oder Sie können ein JSON-Eingabedokument mit einer Variable vom Typ JSON oder Formulardatenmodell auswählen.

* **Eingabe für Dienste > Geben Sie Eingabedaten mithilfe einer Variablen oder einer JSON-Datei an:** Wählen Sie die Option aus, um Werte für alle Argumente aus einer JSON-Datei abzurufen, die in einem absoluten Pfad, in einem Pfad relativ zur Payload oder in einer Variablen gespeichert ist.
* **Auswahl des Eingabe-JSON-Dokuments mit**: Die JSON-Datei, die Werte für alle Dienstargumente enthält. Der Pfad der JSON-Datei kann **relativ zur Payload** oder einem **absoluten Pfad** sein. Sie können das JSON-Eingabedokument auch mit einer Variablen vom Typ „JSON“ oder „Formulardatenmodell“ abrufen.

* **JSON Dot Notation:** Lassen Sie das Feld leer, um alle Objekte der angegebenen JSON-Datei als Eingabe für Service-Parameter zu verwenden. Um ein bestimmtes JSON-Objekt aus der angegebenen JSON-Datei als Eingabe für Service-Argumente zu lesen, geben Sie die Dot Notation für das JSON-Objekt an, z. B. wenn Sie eine JSON ähnlich wie am Anfang des Abschnitts aufgeführt haben, geben Sie „insurance.customerDetails“ an, um alle Details eines Kunden als Eingabe für den Service anzugeben.
* **Ausgabe des Dienstes > Zuordnen und Schreiben von Ausgabewerten zu Variablen oder Metadaten:** Wählen Sie die Option zum Speichern der Ausgabewerte als Eigenschaften des Metadatenknotens der Workflow-Instanz im crx-Repository aus. Geben Sie den Namen der Metadateneigenschaft an und wählen Sie das entsprechende Service-Ausgabeattribut, das der Metadateneigenschaft zugeordnet werden soll, ordnen Sie z. B. die vom Ausgabe-Service zurückgegebene Telefonnummer der Eigenschaft „phone_number“ der Workflow-Metadaten zu. Auf ähnliche Weise können Sie die Ausgabe in einer Variablen des Datentyps Long speichern. Wenn Sie eine Eigenschaft für die **[!UICONTROL Dienstausgabeattribut, das zugeordnet werden soll]** -Option, werden nur Variablen, die Daten der ausgewählten Eigenschaft speichern können, für die **[!UICONTROL Speichern Sie die Ausgabe in]** -Option.

* **Ausgabe des Dienstes > Ausgabe in Variable oder JSON-Datei speichern:** Wählen Sie die Option aus, um die Ausgabewerte in einer JSON-Datei unter einem absoluten Pfad, in einem Pfad relativ zur Payload oder in einer Variablen zu speichern.
* **Speichern Sie das JSON-Ausgabedokument mit den folgenden Optionen:** Speichern Sie die JSON-Ausgabedatei. Der Pfad der JSON-Ausgabedatei kann relativ zur Payload oder einem absoluten Pfad sein. Sie können die JSON-Ausgabedatei auch mit einer Variablen vom Typ „JSON“ oder „Formulardatenmodell“ speichern.

## Schritt „Dokument signieren“ {#sign-document-step}

Mit dem Schritt „Dokument signieren“ können Sie Adobe Sign zum Signieren von Dokumenten verwenden. Der Schritt „Dokument signieren“ hat folgende Eigenschaften:

* **Name der Vereinbarung:** Geben Sie den Titel der Vereinbarung an. Der Name der Vereinbarung wird Teil des Betreffs und des Textkörpers der E-Mail, die an die Unterzeichner gesendet wird. Sie können den Namen entweder in einer Variablen des Datentyps „Zeichenfolge“ speichern oder **Literal** auswählen, um den Namen manuell hinzuzufügen.

* **Gebietsschema:** Geben Sie die Sprache für die E-Mail- und Bestätigungsoptionen an. Sie können das Gebietsschema entweder in einer Variablen des Datentyps „Zeichenfolge“ speichern oder **Literal** auswählen, um das Gebietsschema aus der Liste der verfügbaren Optionen auszuwählen. Sie müssen den Gebietsschema-Code definieren, während Sie den Wert für das Gebietsschema in einer Variablen speichern. Geben Sie beispielsweise **en_US** für Englisch und **fr_FR** für Französisch an.

* **Cloud-Konfiguration für Adobe Sign**: Wählen Sie eine Adobe Sign Cloud-Konfiguration. Wenn Sie Adobe Sign für AEM Forms nicht konfiguriert haben, lesen Sie den Abschnitt [Adobe Sign in AEM Forms integrieren](../../forms/using/adobe-sign-integration-adaptive-forms.md).

* **Wählen Sie Dokument aus, das signiert werden soll:** Sie können ein Dokument an einem Speicherort auswählen, der relativ zur Payload ist, die Payload als Dokument verwenden, einen absoluten Pfad des Dokuments angeben oder das Dokument abrufen, das in einer Variablen des Dokumentdatentyps gespeichert ist.
* **Tage bis Abgabetermin:** Ein Dokument wird als „fällig“ (Abgabetermin überschritten) gekennzeichnet, nachdem für die im Feld **Tage bis Abgabetermin** angegebene Anzahl von Tagen keine Aktivität für die Aufgabe ermittelt wurde. Die Anzahl der Tage wird gezählt, nachdem das Dokument einem Benutzer zur Unterzeichnung zugewiesen wurde.
* **Häufigkeit der E-Mail-Erinnerung:** Sie können eine Erinnerungs-E-Mail im täglichen oder wöchentlichen Intervall senden. Die Woche wird ab dem Tag gezählt, an dem das Dokument einem Benutzer zum Signieren zugewiesen wurde.
* **Signaturvorgang:** Sie können ein Dokument in einer sequenziellen oder parallelen Reihenfolge signieren. Bei sequenzieller Reihenfolge erhält jeweils nur ein Unterzeichner das Formular zur Unterzeichnung. Nachdem der erste Unterzeichner das Dokument signiert hat, wird das Formular an den nächsten Unterzeichner gesendet und so weiter. Bei paralleler Reihenfolge können mehrere Unterzeichner ein Formular gleichzeitig signieren.
* **Umleitungs-URL:** Geben Sie eine Umleitungs-URL an. Nachdem das Dokument signiert wurde, können Sie den Verantwortlichen an eine URL umleiten. Normalerweise enthält diese URL eine Dankesnachricht oder weitere Anweisungen.
* **Workflow-Phase:** Ein Workflow kann mehrere Phasen enthalten. Diese werden im AEM-Posteingang angezeigt. Sie können diese Schritte in den Eigenschaften des Modells definieren (Sidekick > Seite > Seiteneigenschaften > Schritte).
* **Unterzeichner wählen:** Geben Sie die Methode zum Auswählen von Unterzeichnern für das Dokument an. Sie können den Workflow einem Benutzer oder einer Gruppe dynamisch zuweisen oder manuell Details zu einem Unterzeichner hinzufügen.
* **Skript oder Dienst zur Auswahl von Unterzeichnern:** Die Option ist nur verfügbar, wenn die Option „Dynamisch“ im Feld „Unterzeichner auswählen“ ausgewählt ist. Sie können ein ECMAScript oder einen Service angeben, um Unterzeichner und Verifizierungsoptionen für ein Dokument auszuwählen.
* **Unterzeichnerdetails:** Die Option ist nur verfügbar, wenn die Option „Manuell“ im Feld „Unterzeichner auswählen“ ausgewählt ist. Geben Sie die E-Mail-Adresse an und wählen Sie einen optionalen Verifizierungsmechanismus aus. Bevor Sie einen Zwei-Schritt-Bestätigungsmechanismus auswählen, vergewissern Sie sich, dass die entsprechende Verifizierungsoption für das konfigurierte Adobe Sign-Konto aktiviert ist. Sie können eine Variable des Datentyps String verwenden, um Werte für **[!UICONTROL Email]**, **[!UICONTROL Ländercode]** und **[!UICONTROL Telefonnummer]** -Felder. Die **[!UICONTROL Ländercode]** und **[!UICONTROL Telefonnummer]** Felder werden nur angezeigt, wenn Sie **[!UICONTROL Telefonüberprüfung]** von **[!UICONTROL zweistufige Überprüfung]** Dropdown-Liste.
* **Statusvariable:** Ein für Adobe Sign aktiviertes Dokument speichert den Signaturstatus des Dokuments in einer Variablen des Datentyps String . Geben Sie den Namen der Statusvariable (adobeSignStatus) an. Eine Statusvariable einer Instanz ist in CRXDE unter /etc/workflow/instances/ verfügbar.&lt;server>/&lt;date-time>/&lt;instance of=&quot;&quot; workflow=&quot;&quot; model=&quot;&quot;>/workItems/&lt;node>/metaData enthält den Status einer Variablen.
* **Speichern Sie das signierte Dokument mit den folgenden Optionen:** Geben Sie den Speicherort für signierte Dokumente an. Sie können die Payload-Datei überschreiben, das signierte Dokument an einem Speicherort im Payload-Ordner ablegen oder das signierte Dokument in einer Variablen des Dokumenttyps speichern.

## Schritt „Document Services“ {#document-services-steps}

Bei AEM Document Services handelt es sich um einen Satz an OSGi-Diensten zum Erstellen, Zusammenstellen und Sichern von PDF-Dokumenten. AEM Forms bietet für jeden Dokumentendienst einen separaten AEM Workflow-Schritt.

Ähnlich wie bei anderen AEM Forms-Workflow-Schritten wie &quot;Aufgabe zuweisen&quot;, &quot;E-Mail senden&quot;und &quot;Dokument unterschreiben&quot;können Sie Variablen in allen Schritten AEM Document Services verwenden. Weitere Informationen zum Erstellen und Verwalten von Variablen finden Sie unter [Variablen in AEM Workflows](../../forms/using/variable-in-aem-workflows.md).

### Schritt „Dokumentzeitstempel einfügen“ {#apply-document-time-stamp-step}

Fügen Sie einen Zeitstempel in das Dokument ein. Sie geben Dokumentdetails wie den Pfad des Eingabedokuments, den Namen des Eingabedokuments und den Speicherort für die exportierten Daten an. Sie können die vorhandene Payload-Datei überschreiben, einen anderen Dateinamen auswählen, um Daten in einer anderen Datei im Payload-Ordner zu speichern, einen absoluten Pfad zu den Daten angeben oder Daten in einer Variablen des Dokumentdatentyps speichern.

### Schritt „In Bild umwandeln“ {#convert-to-image-step}

Konvertiert ein PDF-Dokument in eine Bildliste. Unterstützte Bildformate sind JPEG, JPEG2000, PNG und TIFF. Die folgenden Informationen gelten für Konvertierungen in TIFF-Bilder:

* Eine mehrseitige TIFF-Datei wird generiert.
* Einige Anmerkungen sind nicht in TIFF-Bildern enthalten. Anmerkungen, die Acrobat zur Erstellung ihrer Darstellung benötigen, sind nicht enthalten.

### Schritt „Nach PDF/A konvertieren“ {#convert-to-pdf-a-step}

Konvertiert ein PDF-Dokument mit den verfügbaren Optionen in das PDF/A-Format. Die PDF/A-Version des Portable Document Format (PDF) ist auf die Archivierung und Langzeitarchivierung von Dokumenten spezialisiert. 

### Schritt „Konvertieren nach PS“ {#convert-to-ps-step}

Konvertieren von PDF-Dokumenten in PostScript – Beim Konvertieren in PostScript können Sie für den Konvertierungsvorgang das Quelldokument und die PostScript-Ebene (2 oder 3) angeben. Das PDF-Dokument, das in eine PostScript-Datei konvertiert wird, muss nicht interaktiv sein.

### Schritt „PDF vom angegebenen Typ erstellen“ {#create-pdf-from-specified-type-step}

Generiert ein PDF-Dokument aus einer Eingabedatei. Das Eingabedokument kann relativ zur Payload sein, einen absoluten Pfad haben, selbst Nutzlast sein oder in einer Variablen des Dokumentdatentyps gespeichert sein.

### Schritt „PDF aus URL/HTML/ZIP erstellen“ {#create-pdf-from-url-html-zip-step}

Erstellt ein PDF-Dokument anhand der bereitgestellten URL-, HTML- und ZIP-Datei.

### Schritt „Daten exportieren“ {#export-data-step}

Exportiert Daten aus einem PDF-Formular oder aus einer XDP-Datei Sie müssen den Dateipfad des Eingabedokuments und das Exportdatenformat eingeben. Die Optionen für das Exportdatenformat sind Auto, XDP und XmlData.

### Schritt „PDF in den angegebenen Format exportieren“ {#export-pdf-to-specified-type-step}

Konvertiert ein PDF-Dokument in ein ausgewähltes Format.

### Schritt „Nicht interaktive PDF-Dateien generieren“ {#generatenoninteractive}

Generieren Sie eine nicht interaktive PDF-Datei. Es bietet verschiedene Anpassungsoptionen.

>[!NOTE]
>
>Sie können Variablen verwenden, um die Vorlagendatei für Eingabedokumente anzugeben. Speichern Sie den Pfad der Vorlagendatei in einer Variablen des Datentyps String .

### Schritt „Daten importieren“ {#import-data-step}

Führt Formulardaten in einem PDF-Formular zusammen. Sie können Formulardaten in ein PDF-Formular importieren.

### Schritt „DDX aufrufen“ {#invokeddx}

Führt die DDX-Datei in der angegebenen Zuordnung von Eingabedokumenten aus und gibt die veränderten PDF-Dokumente zurück.

>[!NOTE]
>
>Sie können Variablen verwenden, um die DDX-Datei für Eingabedokumente anzugeben. Speichern Sie die DDX-Datei in einer Variablen des Datentyps &quot;Document&quot;oder &quot;XML&quot;.

### Schritt „PDF optimieren“ {#optimize-pdf-step}

Optimiert PDF-Dateien durch Reduzierung ihrer Größe. Das Ergebnis dieser Konvertierung sind PDF-Dateien, die kleiner als ihre Originalversionen sein können. Bei diesem Vorgang werden außerdem PDF-Dokumente in die in den Optimierungsparametern angegebene PDF-Version konvertiert.

In den Optimierungseinstellungen wird festgelegt, wie Dateien optimiert werden. Im Folgenden finden Sie Beispieleinstellungen:

* Target PDF-Version
* Verwerfen von Objekten wie JavaScript-Aktionen und eingebetteten Seitenminiaturen
* Verwerfen von Benutzerdaten wie Kommentaren und Dateianlagen
* Verwerfen ungültiger oder nicht verwendeter Einstellungen
* Komprimieren unkomprimierter Daten oder Verwenden effizienterer Komprimierungsalgorithmen
* Entfernen eingebetteter Schriftarten
* Transparenzwerte festlegen

### Schritt „PDF-Formular ausgeben“ {#renderpdf}

Rendert ein Formular, das in Form Designer (XDP) erstellt wurde, in ein PDF-Formular.

>[!NOTE]
>
>Sie können Variablen verwenden, um die Vorlagendatei für Eingabedokumente anzugeben. Speichern Sie den Pfad der Vorlagendatei in einer Variablen des Datentyps String .

### Schritt „Dokument absichern“ {#secure-document-step}

Verschlüsseln, signieren und zertifizieren Sie ein Dokument. AEM Forms unterstützt sowohl die kennwortbasierte als auch die zertifikatsbasierte Verschlüsselung. Sie können auch zwischen verschiedenen Algorithmen zum Signieren von Dokumenten wählen. Zum Beispiel SHA-256 und SH-512. Sie können den Workflow-Schritt zum Reader Extending von PDF-Dokumenten verwenden. Der Workflow-Schritt bietet Optionen zum Aktivieren von Barcode-Dekodierung, digitalen Signaturen, Importieren und Exportieren von PDF-Daten und anderen Optionen.

### Schritt „An Drucker senden“ {#send-to-printer-step}

Senden Sie ein Dokument direkt an einen Drucker. Der Dienst unterstützt die folgenden Druckerzugriffsmechanismen:

* **Drucker mit direktem Zugriff**: Ein Drucker, der auf demselben Computer installiert ist, wird als Drucker mit direktem Zugriff und der Computer als Druckerhost bezeichnet. Dieser Druckertyp kann ein lokaler Drucker sein, der direkt an den Computer angeschlossen ist.
* **Drucker mit indirektem Zugriff**: Der Drucker, der auf einem Druckserver installiert ist, steht für den Zugriff von anderen Computern zur Verfügung. Es stehen Technologien wie das Common UNIX® Printing System (CUPS) und das LDP-Protokoll (Line Printer Daemon) zur Verfügung, um eine Verbindung zu einem Netzwerkdrucker herzustellen. Um auf einen Drucker mit indirektem Zugriff zuzugreifen, geben Sie die IP-Adresse oder den Hostnamen des Druckservers an. Bei Verwendung dieses Mechanismus können Sie ein Dokument an einen LPD-URI senden, wenn im Netzwerk ein LP-Daemon ausgeführt wird. Mit dem Mechanismus können Sie das Dokument zu jedem Drucker weiterleiten, der mit dem Netzwerk verbunden ist, in dem ein LP-Daemon ausgeführt wird.

### Druckten Ausgabeschritt generieren {#generatePrintedOutput}

Der Schritt generiert eine PCL-, PostScript-, ZPL-, IPL-, TPCL- oder DPL-Ausgabe mit einem Formularentwurf und einer Datendatei. Die Datendatei wird mit dem Formularentwurf zusammengeführt und für den Druck formatiert. Die durch diesen Schritt generierte Ausgabe kann direkt an einen Drucker gesendet oder als Datei gespeichert werden. Es wird empfohlen, diesen Schritt zu verwenden, wenn Sie Formularentwürfe oder Daten aus einer Anwendung verwenden möchten. Wenn sich Ihre Formularentwürfe oder Formularentwürfe im Netzwerk, im lokalen Dateisystem oder im HTTP-Speicherort befinden, verwenden Sie den generatePrintedOutput-Vorgang.

Beispiel: Ihre Anwendung erfordert, dass Sie einen Formularentwurf mit einer Datendatei zusammenführen. Die Daten beinhalten Hunderte von Datensätzen. Außerdem muss die Ausgabe an einen Drucker gesendet werden, der ZPL unterstützt. Der Formularentwurf und Ihre Eingabedaten befinden sich in einer Anwendung. Verwenden Sie den generatePrintedOutput-Vorgang, um einzelne Datensätze mit einem Formularentwurf zusammenführen und die Ausgabe an einen Drucker zu senden, der ZPL unterstützt.

Der Schritt &quot;Printed Output generieren&quot;verfügt über die folgenden Eigenschaften:

**Eingabeeigenschaften**

* **[!UICONTROL Wählen Sie die Vorlagendatei mithilfe von]**: Geben Sie den Pfad der Vorlagendatei an. Sie können die Vorlagendatei anhand des Pfads auswählen, der relativ zur Payload ist, in einem absoluten Pfad gespeichert ist oder eine Variable des Dokumentdatentyps verwendet. Beispiel: [Payload_Directory]/Workflow/data.xml Wenn der Pfad nicht im CRX-Repository vorhanden ist, kann ein Administrator den Pfad erstellen, bevor er ihn verwendet. Darüber hinaus können Sie Payload als Eingabedatendatei akzeptieren.

* **[!UICONTROL Wählen Sie das Datendokument mithilfe von]**: Geben Sie den Pfad einer Eingabedatendatei an. Sie können die Eingabedatendatei anhand des Pfads auswählen, der relativ zur Payload ist, in einem absoluten Pfad gespeichert ist, oder mithilfe einer Variablen des Dokumentdatentyps. Beispiel: [Payload_Directory]/Workflow/data.xml Wenn der Pfad nicht im CRX-Repository vorhanden ist, kann ein Administrator den Pfad erstellen, bevor er ihn verwendet.

* **[!UICONTROL Druckerformat]**: Ein Print Format -Wert, der die Sprache der Seitenbeschreibung angibt, die verwendet werden soll, wenn keine XDC-Datei bereitgestellt wird, um den Ausgabestream zu generieren. Wenn Sie einen Literalwert angeben, wählen Sie einen der folgenden Werte:

   * **[!UICONTROL Benutzerdefinierte PCL]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei für PCL anzugeben.
   * **[!UICONTROL Benutzerdefiniertes PostScript]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei für PostScript anzugeben.
   * **[!UICONTROL Custom ZPL]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Dateidatei für ZPL anzugeben.
   * **[!UICONTROL Generic Color PCL (5c)]**: Verwenden Sie eine generische Farb-PCL (5c).
   * **[!UICONTROL Generisches PostScript Level3]**: Verwenden Sie generisches PostScript Level 3.
   * **[!UICONTROL ZPL 300 DPI]**: Verwenden Sie ZPL mit 300 DPI. Die Datei zpl300.xdc wird verwendet.
   * **[!UICONTROL ZPL 600 DPI]**: Verwenden Sie ZPL 600 DPI. Die Datei zpl600.xdc wird verwendet.
   * **[!UICONTROL Benutzerdefiniertes IPL]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei für IPL anzugeben.
   * **[!UICONTROL IPL 300 DPI]**: Verwenden Sie IPL 300 DPI. Die Datei ipl300.xdc wird verwendet.
   * **[!UICONTROL IPL 400 DPI]**: Verwenden Sie IPL 400 DPI. Die Datei ipl400.xdc wird verwendet.
   * **[!UICONTROL Benutzerdefiniertes TPCL]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei für TPCL anzugeben.
   * **[!UICONTROL TPCL 305 DPI]**: Verwenden Sie TPCL 300 DPI. Die Datei tpcl305.xdc wird verwendet.
   * **[!UICONTROL PCL 600 DPI]**: Verwenden Sie TPCL 600 DPI. Die Datei tpcl600.xdc wird verwendet.
   * **[!UICONTROL Custom DPL]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei DPL anzugeben.
   * **[!UICONTROL DPL300DPI]**: Verwenden Sie DPL mit 300 DPI. Die Datei dpl300.xdc wird verwendet.
   * **[!UICONTROL DPL406DPI]**: Verwenden Sie DPL 400 DPI. Die Datei dpl406.xdc wird verwendet.
   * **[!UICONTROL DPL600DPI]**: Verwenden Sie DPL 600 DPI. Die Datei dpl600.xdc wird verwendet.

**Ausgabeeigenschaften**

* **[!UICONTROL Ausgabedokument mithilfe von speichern]**: Geben Sie den Speicherort für die Ausgabedatei an. Sie können die Ausgabedatei an einem Speicherort speichern, der relativ zur Payload ist, in einer Variablen, oder einen absoluten Speicherort für die Ausgabedatei angeben. Wenn der Pfad nicht im CRX-Repository vorhanden ist, kann ein Administrator den Pfad erstellen, bevor er ihn verwendet.

**Erweiterte Eigenschaften**

* **[!UICONTROL Wählen Sie den Speicherort des Inhaltsstamms mit]**: Der Inhaltsstamm ist ein string -Wert, der den URI, den absoluten Verweis oder den Speicherort im Repository angibt, um relative Assets abzurufen, die vom Formularentwurf verwendet werden. Beispiel: Wenn der Formularentwurf relativ auf ein Bild verweist, z. B. ../myImage.gif, muss sich myImage.gif unter repository:// befinden. Der Standardwert ist repository://, der auf die Stammebene des Repositorys verweist.

   Wenn Sie ein Asset aus Ihrer Anwendung auswählen, muss der Inhaltsstamm-URI-Pfad die richtige Struktur aufweisen. Wenn beispielsweise ein Formular aus einer Anwendung namens SampleApp unter SampleApp/1.0/forms/Test.xdp gespeichert wird, muss der Inhaltsstamm-URI als repository://administrator@password/Applications/SampleApp/1.0/forms/ oder repository:/Applications/SampleApp/1.0/forms/ (wenn die Berechtigung null ist) angegeben werden. Wenn der Inhaltsstamm-URI auf diese Weise angegeben wird, werden die Pfade aller referenzierten Elemente im Formular für diesen URI aufgelöst.

* **[!UICONTROL XCI-Datei mit]**: XCI-Dateien werden verwendet, um Schriftarten und andere Eigenschaften zu beschreiben, die für Formularelemente verwendet werden. Sie können eine XCI-Datei relativ zur Payload an einem absoluten Pfad oder mithilfe einer Variablen des Dokumentdatentyps belassen.

* **[!UICONTROL Gebietsschema]**: Gibt die Sprache an, die zum Generieren des PDF-Dokuments verwendet wird. Wenn Sie einen Literalwert angeben, wählen Sie eine Sprache aus der Liste oder einen der folgenden Werte:
   * **So verwenden Sie den Server-Standard**: (Standard) Verwenden Sie die auf dem AEM Forms-Server konfigurierte Einstellung &quot;Locale&quot;. Die Einstellung &quot;Gebietsschema&quot;wird mithilfe der Administration Console konfiguriert. (Weitere Informationen finden Sie in der [Designer-Hilfe](http://www.adobe.com/go/learn_aemforms_designer_65).)

   * **So verwenden Sie benutzerdefinierten Wert**: Geben Sie den Gebietsschema-Code in das Feld &quot;Literal&quot;ein oder wählen Sie eine string -Variable aus, die den Gebietsschema-Code enthält. Eine vollständige Liste der unterstützten Gebietsschemas finden Sie unter http://java.sun.com/j2se/1.5.0/docs/guide/intl/locale.doc.html.

* **[!UICONTROL Kopien]**: Ein integer -Wert, der die Anzahl der Exemplare angibt, die für die Ausgabe generiert werden sollen. Der Standardwert ist 1.

* **[!UICONTROL Duplex Printing]**: Ein Paginierungswert, der angibt, ob zweiseitiger oder einseitiger Druck verwendet werden soll. Drucker, die PostScript und PCL unterstützen, verwenden diesen Wert. Wenn Sie einen Literalwert bereitstellen, wählen Sie einen der folgenden Werte:
   * **[!UICONTROL Duplex Long Edge]**: Zweiseitiger Druck wird verwendet und der Seitenumbruch erfolgt an langen Kanten.
   * **[!UICONTROL Duplex Short Edge]**: Zweiseitiger Druck und Druck mit Kurzwahlpaginierung.
   * **[!UICONTROL Simplex]**: Einseitiger Druck wird verwendet.
