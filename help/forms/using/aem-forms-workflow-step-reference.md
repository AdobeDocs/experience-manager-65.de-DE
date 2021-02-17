---
title: Formularzentrierte Workflows in OSGi - Schritt-Referenz
seo-title: Formularzentrierte Workflows in OSGi - Schritt-Referenz
description: Der formularzentrierte Workflow in OSGi-Schritten ermöglicht das schnelle Erstellen adaptiver formularbasierter Workflows.
seo-description: Der formularzentrierte Workflow in OSGi-Schritten ermöglicht das schnelle Erstellen adaptiver formularbasierter Workflows.
uuid: 6f791c45-0e35-4c55-9106-5340caab94b7
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: f0a5588d-f210-4f04-bc35-b62834f90ab1
docset: aem65
translation-type: tm+mt
source-git-commit: a873cf3e7efd3bc9cd4744bf09078d9040efcdda
workflow-type: tm+mt
source-wordcount: '7109'
ht-degree: 51%

---


# Formularzentrierte Workflows in OSGi - Schritt-Referenz{#forms-centric-workflow-on-osgi-step-reference}

## Schritte für den Forms-Workflow {#forms-workflow-steps}

Schritte für den Forms-Workflow führen AEM Forms-spezifische Vorgänge in einem AEM-Workflow durch. Diese Schritte ermöglichen das schnelle Erstellen adaptiver formularzentrierter Workflows auf OSGi. Diese Workflows können für die Entwicklung grundlegender geschäftlicher Prozesse zur Überprüfung und Genehmigung Workflows, intern und quer durch die Firewall verwendet werden. Sie können die Forms-Workflow-Schritte außerdem verwenden, um Document Services zu starten, Adobe Sign-Signatur-Workflow zu integrieren und andere AEM Forms-Vorgänge auszuführen. Sie benötigen das [AEM Forms Add-On](https://www.adobe.com/go/learn_aemforms_documentation_63), um diese Schritte in einem Workflow zu verwenden.

## Schritt „Aufgaben zuweisen“ {#assign-task-step}

Der Schritt „Aufgaben zuweisen“ erstellt eine Aufgabe und weist sie einem Benutzer oder einer Gruppe zu. Zusammen mit der Zuweisung der Aufgabe gibt die Komponente außerdem das adaptive Formular oder die nicht interaktive PDF-Datei für die Aufgabe an. Das adaptive Formular ist erforderlich, damit die Benutzer Eingaben vornehmen können, und die nicht interaktive PDF-Datei oder ein schreibgeschütztes adaptives Formular wird in Workflows verwendet, die nur zur Prüfung dienen.

Sie können mit dieser Komponente auch das Verhalten der Aufgabe steuern. Beispielsweise das Erstellen eines automatischen Datensatzdokuments, die Zuweisung der Aufgabe zu einem bestimmten Benutzer oder einer Gruppe, das Angeben des Pfads der gesendeten Daten, das Angeben des Pfads der Daten, die im Voraus ausgefüllt werden sollen und das Angeben der Standardaktionen. Schritt „Aufgaben zuweisen“ hat folgende Eigenschaften:

* **Titel:** Bezeichnung der Aufgabe. Der Titel wird in der AEM Inbox angezeigt.
* **Beschreibung:** Erläuterung der Vorgänge, die in der Aufgabe ausgeführt werden. Diese Informationen sind für andere Prozessentwickler nützlich, wenn Sie in einer gemeinsamen Entwicklungsumgebung arbeiten.

* **Miniaturbildpfad:** Pfad des Aufgabenminiaturbilds. Wenn kein Pfad angegeben ist, wird für ein adaptives Formular das Standardminiaturbild angezeigt und für das Datensatzdokument wird ein Standardsymbol angezeigt.
* **Workflow-Phase:** Ein Workflow kann mehrere Phasen enthalten. Diese Phasen werden in der AEM Inbox angezeigt. Sie können diese Phasen in den Eigenschaften des Modells definieren (Sidekick > Seite> Seiteneigenschaften > Phasen).
* **Priorität:** Die ausgewählte Priorität wird in der AEM Inbox angezeigt. Die verfügbaren Optionen sind „Hoch“, „Mittel“ und „Niedrig“. Der Standardwert ist „Mittel“.
* **Fälligkeitsdatum:** Geben Sie die Anzahl der Tage oder Stunden an, nach denen die Aufgabe als „überfällig“ markiert wird. Wenn Sie **Aus** wählen, dann wird die Aufgabe nie als „überfällig“ markiert. Sie können auch einen Zeitüberschreitungs-Handler angeben, um bestimmte Aufgaben auszuführen, nachdem die Aufgabe überfällig ist.

* **Tage:** Die Anzahl der Tage, nach denen die Aufgabe abgeschlossen werden soll. Die Anzahl der Tage wird gezählt, nachdem die Aufgabe einem Benutzer zugewiesen wurde. Wenn eine Aufgabe nicht abgeschlossen wurde und die Anzahl der Tage im Feld „Tage“ überschreitet, wird bei Auswahl dieser Option nach den fälligen Tagen ein Zeitüberschreitungshandler ausgelöst.
* **Stunden:** Die Anzahl der Tage, innerhalb derer die Aufgabe abgeschlossen werden soll. Die Anzahl der Stunden wird gezählt, nachdem die Aufgabe einem Benutzer zugewiesen wurde. Wenn eine Aufgabe nicht abgeschlossen wurde und die Anzahl der Stunden im Feld „Stunden“ überschreitet, wird bei Auswahl dieser Option nach den fälligen Stunden ein Zeitüberschreitungshandler ausgelöst.
* **Zeitüberschreitung nach Fälligkeitsdatum:** Wählen Sie diese Option, um das Auswahlfeld „Zeitüberschreitungshandler“ zu aktivieren.
* **Zeitüberschreitungshandler:** Wählen Sie das Skript aus, das ausgeführt werden soll, wenn der Schritt „Aufgabe zuweisen“ das Fälligkeitsdatum überschreitet. Skripten, die im CRX-Repository unter [apps]/fd/Dashboard/scripts/timeoutHandler abgelegt werden, stehen zur Auswahl zur Verfügung. Der angegebene Pfad existiert nicht im CRX-Repository. Ein Administrator erstellt den Pfad, bevor er ihn verwendet.
* **Markieren Sie Aktion und Kommentar aus der letzten Aufgabe in „Aufgabendetails“:** Wählen Sie diese Option, um die letzte ausgeführte Aktion und den Kommentar, der im Abschnitt „Aufgabendetail“ einer Aufgabe erhalten wurde, anzuzeigen.
* **Typ:** Wählen Sie den Typ des Dokuments, das ausgefüllt werden soll, wenn der Workflow gestartet wird. Sie können ein adaptives Formular, ein schreibgeschütztes adaptives Formular, ein nicht interaktives PDF-Dokument, eine Interaktive Kommunikationsagent-Benutzeroberfläche oder ein interaktives Kanal für die interaktive Kommunikation auswählen.
* **Adaptives Formular verwenden:** Geben Sie die Methode zum Suchen des adaptiven Eingabefelds an. Diese Option ist verfügbar, wenn Sie in der Dropdown-Liste &quot;Typ&quot;die Option &quot;Adaptives Formular&quot;oder &quot;Schreibgeschütztes adaptives Formular&quot;auswählen. Sie können das adaptive Formular verwenden, das an den Workflow gesendet wird, in einem absoluten Pfad verfügbar ist oder in einem Pfad in einer Variablen verfügbar ist. Sie können eine Variable des Typs String verwenden, um den Pfad anzugeben.\
   Sie können mehrere adaptive Formulare mit einem Workflow verknüpfen. Daher können Sie mithilfe der verfügbaren Eingabemethoden ein adaptives Formular zur Laufzeit angeben.

* **Interaktive Kommunikation verwenden:** Geben Sie die Methode zum Auffinden der interaktiven Eingangskommunikation an. Sie können die interaktive Kommunikation verwenden, die an den Workflow gesendet wird, an einem absoluten Pfad verfügbar ist oder an einem Pfad in einer Variablen verfügbar ist. Sie können eine Variable des Typs String verwenden, um den Pfad anzugeben. Diese Option ist verfügbar, wenn Sie in der Dropdown-Liste &quot;Typ&quot;die Option &quot;Interaktive Kommunikationsagent-Benutzeroberfläche&quot;oder &quot;Interactive Communication Web Kanal-Dokument&quot;auswählen.

>[!NOTE]
>
>Für den Zugriff auf die Benutzeroberfläche von Interactive Communications Agent in AEM Posteingang müssen cm-agent-users und Gruppen von Workflow-Benutzern zugewiesen sein.

* **Adaptives Formular oder interaktiver Kommunikationspfad**: Geben Sie den Pfad des adaptiven Formulars oder der interaktiven Kommunikation an. Sie können das adaptive Formular oder die interaktive Kommunikation verwenden, die an den Workflow gesendet wird, an einem absoluten Pfad verfügbar ist, oder das adaptive Formular aus einem Pfad abrufen, der in einer Variablen des Datentyps Zeichenfolge gespeichert ist.
* **PDF-Eingabedatei auswählen mit:** Geben Sie den Pfad eines nicht interaktiven PDF-Dokuments an. Das Feld ist verfügbar, wenn Sie im Feld „Typ“ ein nicht interaktives PDF-Dokument auswählen. Sie können die PDF-Eingabedatei unter Verwendung des Pfads auswählen, der relativ zur Nutzlast ist, unter einem absoluten Pfad gespeichert wird oder eine Variable des Dokument-Datentyps verwendet. Beispiel: [Payload_Directory]/Workflow/PDF/credit-card.pdf. Der Pfad existiert nicht im CRX-Repository. Ein Administrator erstellt den Pfad, bevor er ihn verwendet. Sie benötigen ein Formular mit aktivierter Option „Datensatzdokument“ oder auf Vorlagen basierende adaptive Formulare, um die PDF-Pfad-Komponente zu verwenden.
* **Für abgeschlossene Aufgaben rendern Sie das adaptive Formular wie folgt**: Wenn eine Aufgabe als abgeschlossen markiert ist, können Sie das adaptive Formular als schreibgeschütztes adaptives Formular oder PDF-Dokument ausgeben. Sie benötigen ein Formular mit aktivierter Option „Datensatzdokument“ oder auf Vorlagen basierende adaptive Formulare zum Rendern des adaptiven Formulars als Datensatzdokument.
* **Vorausgefüllt:** Die folgenden Felder dienen als Eingaben in die Aufgabe:

   * **Wählen Sie die Eingabedatendatei mit:** Pfad der Eingabedatendatei (.json,). XML-, DOC- oder Formulardatenmodell). Sie können die Eingabedatendatei mit einem Pfad abrufen, der relativ zur Nutzlast ist, oder die Datei abrufen, die in einer Variablen des Dokument-, XML- oder JSON-Datentyps gespeichert ist. Beispielsweise enthält die Datei die Daten, die für das Formular über eine AEM Inbox-Anwendung gesendet werden. Ein Beispielpfad ist [Payload_Directory]/workflow/data.
   * **Wählen Sie die gewünschten Anlagen aus, indem Sie die** am Speicherort verfügbaren Anlagen an das mit der Aufgabe verknüpfte Formular anhängen. Der Pfad ist immer relativ zur Payload. Ein Beispielpfad ist [Payload_Directory]/attachments/
   * **JSON-Eingabedatei auswählen:** Wählen Sie eine JSON-Eingabedatei unter Verwendung eines Pfads aus, der relativ zur Nutzlast ist oder in einer Variablen des Datentyps Dokument, JSON oder Formulardatenmodell gespeichert ist. Diese Option ist verfügbar, wenn Sie in der Dropdown-Liste &quot;Typ&quot;die Option &quot;Interaktive Kommunikationsagent-Benutzeroberfläche&quot;oder &quot;Interactive Communication Web Kanal-Dokument&quot;auswählen.
   * **Wählen Sie einen benutzerdefinierten Vorfülldienst:** Wählen Sie den Vorfülldienst aus, um die Daten abzurufen, und füllen Sie das Dokument Interactive Communication Web Kanal oder die Agent-Benutzeroberfläche vorab aus.

   * **Verwenden Sie den oben ausgewählten interaktiven Kommunikationsdienst zum Vorausfüllen:** Verwenden Sie diese Option, um den in der Dropdown-Liste Interaktive Kommunikation verwenden definierten Dienst für interaktive Kommunikation zu verwenden.
   * **Zuordnung von Anforderungsattributen:** Verwenden Sie den Abschnitt &quot;Zuordnung von Anforderungsattributen&quot;, um den  [Namen und den Wert des Anforderungsattributs](../../forms/using/work-with-form-data-model.md#bindargument) zu definieren. Rufen Sie die Details aus der Datenquelle basierend auf dem in der Anforderung angegebenen Attributnamen und -wert ab. Sie können einen Wert für das Anforderungsattribut mit einem Literalwert oder einer Variablen des Datentyps String definieren.\
      Die Zuordnungsoptionen für den Vorfülldienst und das Anforderungsattribut sind nur verfügbar, wenn Sie in der Dropdown-Liste &quot;Typ&quot;die Option &quot;Interaktive Kommunikationsagent&quot;oder &quot;Interaktives Kommunikations-Web-Kanal&quot;auswählen.

* **Gesendete Informationen:** Die folgenden Felder dienen als Ausgabespeicherorte für die Aufgabe:

   * **Speichern Sie die Ausgabedatendatei mit:** Speichern Sie die Datendatei (.json,). XML-, DOC- oder Formulardatenmodell). Die Datendatei enthält Informationen, die über das zugeordnete Formular übermittelt werden. Sie können die Ausgabedatendatei unter Verwendung eines Pfads speichern, der relativ zur Nutzlast ist, oder sie in einer Variablen des Dokument-, XML- oder JSON-Datentyps speichern. Beispiel: [Payload_Directory]/Workflow/data, wobei data eine Datei ist.
   * **Anlagen speichern unter:** Speichern Sie die in einer Aufgabe bereitgestellten Formularanlagen. Sie können die Anlagen mit einem Pfad speichern, der relativ zur Nutzlast ist, oder sie in einer Variablen des Dokument-Datentyps speichern.
   * **Speichern Sie Dokument aus Datensatz mit:** Pfad, um ein Dokument aus Datensatzdatei zu speichern. Beispiel: [Payload_Directory]/DocumentofRecord/credit-card.pdf. Sie können das Dokument Datensatz unter Verwendung eines Pfads speichern, der relativ zur Nutzlast ist, oder es in einer Variablen des Dokument-Datentyps speichern. Wenn Sie die Option **Relativ zur Nutzlast** auswählen, wird das Dokument des Datensatzes nicht generiert, wenn das Pfadfeld leer bleibt. Diese Option ist nur verfügbar, wenn Sie in der Dropdown-Liste &quot;Typ&quot;die Option &quot;Adaptives Formular&quot;auswählen.

   * **Web-Kanal-Daten speichern unter:** Speichern Sie die Web-Kanal-Datendatei unter einem Pfad, der relativ zur Nutzlast ist, oder speichern Sie sie in einer Variablen des Datentyps Dokument, JSON oder Formulardatenmodell. Diese Option ist nur verfügbar, wenn Sie in der Dropdown-Liste &quot;Typ&quot;die Option &quot;Interaktive Kommunikationsagent&quot;auswählen.
   * **PDF-Dokument speichern unter:Das PDF-Dokument unter einem Pfad, der relativ zur Nutzlast ist,** speichern oder in einer Variablen des Dokument-Datentyps speichern. Diese Option ist nur verfügbar, wenn Sie in der Dropdown-Liste &quot;Typ&quot;die Option &quot;Interaktive Kommunikationsagent&quot;auswählen.
   * **Speichern Sie die Layoutvorlage mit:** Speichern Sie die Layoutvorlage unter einem Pfad, der relativ zur Nutzlast ist, oder speichern Sie sie in einer Variablen des Dokument-Datentyps. Die [Layoutvorlage](../../forms/using/layout-design-details.md) bezieht sich auf eine XDP-Datei, die Sie mit Forms Designer erstellen. Diese Option ist nur verfügbar, wenn Sie in der Dropdown-Liste &quot;Typ&quot;die Option &quot;Interaktive Kommunikationsagent&quot;auswählen.

* **&quot;Zuweisung&quot;> &quot;Zuweisungsoptionen&quot;:** Geben Sie an, wie die Aufgabe einem Benutzer zugewiesen werden soll. Sie können die Aufgabe dynamisch einem Benutzer oder einer Gruppe zuweisen, indem Sie das Skript „Teilnehmerauswahl“ verwenden oder die Aufgabe einem bestimmten AEM-Benutzer oder einer bestimmten Gruppe zuweisen.
* **Teilnehmerauswahl:** Die Option ist verfügbar, wenn die Option **Dynamically to a user or group (Dynamisch zu einem Benutzer oder einer Gruppe)** im Feld „Optionen zuweisen“ ausgewählt ist. Sie können ein ECMAScript oder einen Dienst verwenden, um einen Benutzer oder eine Gruppe dynamisch auszuwählen. Weitere Informationen finden Sie im Abschnitt [Dynamisches Zuweisen eines Workflows zu Benutzern](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) und [Erstellen eines benutzerdefinierten Schritts „Dynamischer Teilnehmer in Adobe Experience Manager“.](https://helpx.adobe.com/experience-manager/using/dynamic-steps.html)

* **Teilnehmer:** Das Feld ist verfügbar, wenn die Option **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]****im Feld „Teilnehmerauswahl“ ausgewählt ist.** In diesem Feld können Sie Benutzer oder Gruppen für die Option „RandomParticipantChooser“ auswählen.

* **Zuweisung:** Das Feld ist verfügbar, wenn  **[!UICONTROL com.adobe.fd.workspace.step.service.]** VariableParticipantChooseris im Feld  **&quot;** Teilnehmerauswahl&quot;ausgewählt ist. Mit dem Feld können Sie eine Variable des Datentyps String auswählen, um den Verantwortlichen zu definieren.

* **Argumente:** Das Feld ist verfügbar, wenn ein anderes als das Skript „RandomParticipantChoose“ im Feld „Teilnehmerauswahl“ ausgewählt wurde. In diesem Feld können Sie eine Liste mit durch Kommas getrennten Argumenten für das im Feld „Teilnehmerauswahl“ ausgewählte Skript angeben.

* **Benutzer oder Gruppe:** Die Aufgabe wurde dem ausgewählten Benutzer oder der Gruppe zugewiesen. Die Option ist verfügbar, wenn die Option **To a specific user or group (Zu einer bestimmten Benutzer bzw. einer bestimmten Gruppe)** im Feld „Optionen zuweisen“ ausgewählt ist. **** Das Feld listet alle Benutzer und Gruppen der Workflow-Benutzergruppe auf.\
   Das Dropdownmenü **Benutzer oder Gruppe** Liste die Benutzer und Gruppen, auf die der angemeldete Benutzer Zugriff hat. Die Anzeige des Benutzernamens hängt davon ab, ob Sie über Zugriffsberechtigungen für den Knoten **users** in crx-repository für diesen bestimmten Benutzer verfügen.

* **Bevollmächtigten per E-Mail benachrichtigen:** Wählen Sie diese Option, um E-Mail-Benachrichtigungen an den Bevollmächtigten zu senden. Diese Benachrichtigungen werden gesendet, wenn eine Aufgabe einem Benutzer zugewiesen wird. Aktivieren Sie die Benachrichtigungen von AEM Web Console, bevor Sie die Option verwenden. Für schrittweise Anweisungen siehe [Konfigurieren von E-Mail-Benachrichtigungen für den Schritt „Aufgabe zuweisen“](../../forms/using/aem-forms-workflow.md)

* **HTML-E-Mail-Vorlage**: Wählen Sie die E-Mail-Vorlage für die Benachrichtigungs-E-Mail. Um eine Vorlage zu bearbeiten, ändern Sie die Datei unter /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt im CRX-Repository.
* **Delegierung zulassen an:** AEM Inbox bietet dem angemeldeten Benutzer eine Option, den zugewiesenen Workflow an einen anderen Benutzer zu übertragen. Sie dürfen innerhalb derselben Gruppe oder an den Workflow-Benutzer einer anderen Gruppe delegieren. Wenn die Aufgabe einem einzelnen Benutzer zugewiesen ist und die Option **Delegierung an Mitglieder der Bevollmächtigten-Gruppe zulassen** aktiviert ist, kann die Aufgabe nicht an einen anderen Benutzer oder eine andere Gruppe übertragen werden.
* **Freigabeeinstellungen:** AEM InBox stehen Optionen zum Freigeben einer einzelnen oder aller Aufgaben im Posteingang für andere Benutzer zur Verfügung:
   * Wenn die Option **Den Verantwortlichen die explizite Freigabe im Posteingang zulassen** aktiviert ist, kann der Benutzer auf die Aufgabe klicken und sie für einen anderen AEM freigeben.
   * Wenn die Option **Den Verantwortlichen die Freigabe über den Posteingang gestatten** aktiviert ist und ein Benutzer seine Posteingangselemente freigibt oder anderen Benutzern den Zugriff auf seine Posteingangselemente erlaubt, werden nur Aufgaben mit der oben genannten Option für andere Benutzer freigegeben.

* **Aktionen > Standardaktionen:** Standardmäßig sind die Aktionen &quot;Senden&quot;, &quot;Speichern&quot;und &quot;Zurücksetzen&quot;verfügbar. Alle Standardaktionen sind standardmäßig aktiviert.
* **Route-Variable:** Name der Route-Variablen. Die Route-Variable erfasst benutzerdefinierte Aktionen, die ein Benutzer in der AEM Inbox auswählt.
* **Routen:** Eine Aufgabe kann auf verschiedene Routen verzweigen. Bei Auswahl in AEM Inbox gibt die Route einen Wert zurück, und der Workflow verzweigt basierend auf der ausgewählten Route. Sie können Routen entweder in einer Variablen des Datentyps String speichern oder **Literal** auswählen, um Routen manuell hinzuzufügen.

* **Titel**: Geben Sie den Titel für die Route an. Der Titel wird in der AEM Inbox angezeigt.
* **Korallen-Symbol:** Geben Sie das HTML-Attribut eines Korallensymbols an. Die Adobe CorelUI-Bibliothek bietet eine Vielzahl von Touch-First-Symbolen. Sie können ein Symbol für die Route auswählen und verwenden. Es wird zusammen mit dem Titel in AEM Inbox angezeigt. Wenn Sie die Routen in einer Variablen speichern, verwenden die Routen ein standardmäßiges &quot;Tags&quot;-Korallensymbol.
* **Bevollmächtigtem erlauben, Kommentare einzufügen**: Wählen Sie diese Option, um Kommentare für die Aufgabe zu aktivieren. Ein Beauftragter kann die Kommentare innerhalb der AEM Inbox zum Zeitpunkt des Aufgabenversands hinzufügen.
* **Kommentar in Variable speichern:** Speichern Sie den Kommentar in einer Variablen des Datentyps String. Diese Option wird nur angezeigt, wenn Sie das Kontrollkästchen **Dem Verantwortlichen das Hinzufügen eines Kommentars** aktivieren.

* **Bevollmächtigtem erlauben, Anlage(n) der Aufgabe hinzuzufügen**: Wählen Sie diese Option, um Anlagen für die Aufgabe zu aktivieren. Ein Beauftragter kann die Anlagen in der AEM Inbox zum Zeitpunkt der Aufgabensendung hinzufügen.
* **Speichern Sie Aufgaben-Anhänge mit**: Geben Sie den Speicherort des Anlagenordners an. Sie können Ausgabedateianlagen mit einem Pfad relativ zur Nutzlast oder in einer Variablen des Dokument-Datentyps speichern. Diese Option wird nur angezeigt, wenn Sie das Kontrollkästchen **Den Verantwortlichen das Hinzufügen von Anlagen zur Aufgabe** aktivieren und **Adaptives Formular**, **Schreibgeschütztes adaptives Formular** oder **Nicht interaktives PDF-Dokument** aus der Dropdownliste **Typ** auswählen Liste auf der Registerkarte **Formular/Dokument**.

>[!NOTE]
>
>Verwenden Sie während der Laufzeit die Registerkarte &quot;Anlagen&quot;in der Benutzeroberfläche des Agenten, um die Anlagen einer interaktiven Kommunikation zuzuordnen. Die verknüpften Anlagen werden nach dem Öffnen des Arbeitselements als Anlagen zur Aufgabe im Sidekick angezeigt.

* **Benutzerdefinierte Metadaten verwenden:** Wählen Sie diese Option, um das benutzerdefinierte Metadatenfeld zu aktivieren. Benutzerdefinierte Metadaten werden in E-Mail-Vorlagen verwendet.
* **Benutzerdefinierte Metadaten:** Wählen Sie benutzerdefinierte Metadaten für die E-Mail-Vorlagen. Die benutzerdefinierten Metadaten sind im CRX-Repository unter apps/fd/dashboard/scripts/metadataScripts verfügbar. Der angegebene Pfad existiert nicht im CRX-Repository. Ein Administrator erstellt den Pfad, bevor er ihn verwendet. Sie können auch einen Dienst für die benutzerdefinierten Metadaten verwenden. Sie können auch die WorkitemUserMetadataService-Schnittstelle erweitern, um benutzerdefinierte Metadaten bereitzustellen.
* **Daten aus vorherigen Schritten anzeigen**: Wählen Sie - falls verfügbar - diese Option aus, um den Bevollmächtigten das Anzeigen früherer Bevollmächtigter, bereits vorgenommener Aktionen, Kommentare zu dieser Aufgabe und des Nachweisdokuments über abgeschlossene Aufgaben zu ermöglichen.
* **Daten aus allen nachfolgenden Schritten einblenden:** Wählen Sie diese Option, um dem aktuellen Bearbeiter zu ermöglichen, die durchgeführte Aktion und Kommentare, die von nachfolgenden Beauftragten zur Aufgabe hinzugefügt wurden, anzuzeigen. Außerdem kann sich der aktuelle Bevollmächtigte ein Dokument als Nachweis über die abgeschlossenen Aufgaben anzeigen lassen - sofern verfügbar.
* **Sichtbarkeit des Datentyps:** Standardmäßig kann ein Bevollmächtigter ein Datensatzdokument, Bevollmächtigte, durchgeführte Aktionen und Kommentare anzeigen, die frühere und nachfolgende Bevollmächtigte hinzugefügt haben. Verwenden Sie die Option „Sichtbarkeit von Datentyp“, um den Typ der für die Bevollmächtigten sichtbaren Daten zu begrenzen.

## Schritt „E-Mail senden“{#send-email-step}

Verwenden Sie den E-Mail-Schritt, um eine E-Mail zu senden, z. B. eine E-Mail mit einem Dokument, einen Link eines adaptiven Formulars, einen Link einer interaktiven Kommunikation oder ein angehängtes PDF-Dokument. Der Schritt „E-Mail senden“ unterstützt [HTML-E-Mails](https://en.wikipedia.org/wiki/HTML_email). HTML-E-Mails sind responsive und passen sich an den E-Mail-Client und die Bildschirmgröße des Empfängers an. Sie können eine HTML-E-Mail-Vorlage verwenden, um das Erscheinungsbild, das Farbschema und Verhalten der E-Mail zu definieren.

Der E-Mail-Schritt verwendet den Day CQ Mail-Dienst Bevor Sie den E-Mail-Schritt verwenden, stellen Sie sicher, dass der [E-Mail-Dienst](../../forms/using/aem-forms-workflow.md) konfiguriert wurde. Der E-Mail-Schritt hat die folgenden Eigenschaften:

**Titel:** Der Titel des Schritts hilft beim Identifizieren des Schritts im Workflow-Editor.

**Beschreibung:** Erklärungen können für andere Entwickler nützlich sein, wenn Sie in einer gemeinsamen Entwicklungsumgebung arbeiten.

**E-Mail-Betreff:** Betreff kann aus Workflow-Metadaten abgerufen, manuell angegeben oder aus dem in einer Variablen gespeicherten Wert abgerufen werden. Wählen Sie eine der folgenden Optionen aus:

* **Literal -** Geben Sie ein Thema manuell an.
* **Abrufen von Workflow-Metadaten**  - Abrufen des Betreffs von einer Metadateneigenschaft.
* **Variable** : Rufen Sie den Betreff aus dem Wert ab, der in einer Variablen des Zeichenfolgen-Datentyps gespeichert ist.

**HTML-E-Mail-Vorlage**: HTML-Vorlage für die E-Mail. Sie können diese Variablen in einer E-Mail-Vorlage verwenden. Der E-Mail-Schritt extrahiert und zeigt alle Variablen an, die in einer Vorlage für Eingaben enthalten sind. 

**Metadaten für E-Mail-Vorlagen: Der** Wert der Variablen für E-Mail-Vorlagen kann ein vom Benutzer angegebener Wert, der Pfad eines Assets auf dem Autor oder dem Veröffentlichungsserver, Bild oder eine Eigenschaft für Workflow-Metadaten sein.

* **Literal:** Verwenden Sie die Option, wenn Sie den genauen, zu spezifizierenden Wert kennen. Beispiel: [example@example.com](mailto:example@example.com).

* **Workflow-Metadaten:** Verwenden Sie die Option, wenn der zu verwendende Wert in einer Workflow-Metadaten-Eigenschaft gespeichert wird. Nachdem Sie die Option ausgewählt haben, geben Sie den Namen der Metadateneigenschaft in das leere Textfeld unter der Option „Workflow-Metadaten“ ein. Zum Beispiel emailAddress.
* **Asset-URL:** Verwenden Sie die Option, um einen Weblink einer interaktiven Kommunikation mit der E-Mail einzubetten. Wählen Sie nach Auswahl der Option die einzubettende interaktive Kommunikation aus. Das Asset kann sich auf dem Autoren- oder dem Veröffentlichungsserver befinden.
* **Bild:** Verwenden Sie die Option, um ein Bild in die E-Mail einzubetten. Nachdem Sie die Option ausgewählt haben, suchen Sie nach dem entsprechenden Bild und wählen Sie es aus. Die Bildoption ist nur für die Bild-Tags (&lt;img src=&quot;*&quot;/>) verfügbar, die in der E-Mail-Vorlage verfügbar sind.

**E-Mail-Adresse des Absenders/Empfängers:** Wählen Sie die  **** Literaloption aus, um manuell eine E-Mail-Adresse anzugeben, oder wählen Sie die Option &quot; **Abruf aus Workflow-** Metadaten&quot;, um die E-Mail-Adresse aus einer Metadateneigenschaft abzurufen. Sie können auch eine Liste von Metadaten-Eigenschaften-Arrays für die Option **Aus Workflow-Metadaten abrufen** angeben. Wählen Sie die Option **Variable** aus, um die E-Mail-Adresse aus dem Wert abzurufen, der in einer Variablen des Zeichenfolgen-Datentyps gespeichert ist.

**Dateianlage:** Das am angegebenen Speicherort verfügbare Asset wird an die E-Mail angehängt. Der Pfad des Assets kann relativ zur Payload oder zum absoluten Pfad sein. Ein Beispielpfad ist [Payload_Directory]/attachments/.

Wählen Sie die Option **Variable**, um die in einer Variablen des Dokuments-, XML- oder JSON-Datentyps gespeicherte Dateianlage abzurufen.

**Dateiname:** Name der E-Mail-Anhangsdatei. Der E-Mail-Schritt ändert den ursprünglichen Dateinamen der Anlage in den angegebenen Dateinamen. Der Name kann manuell angegeben oder aus einer Workflow-Metadateneigenschaft oder einer Variablen abgerufen werden. Verwenden Sie die Option **Literal**, wenn Sie den genauen zu spezifizierenden Wert kennen. Verwenden Sie die Option **Variable**, um den Dateinamen aus dem Wert abzurufen, der in einer Variablen des Zeichenfolgen-Datentyps gespeichert ist. Verwenden Sie die Option **Von Workflow-Metadaten abrufen**, wenn der zu verwendende Wert in einer Workflow-Metadaten-Eigenschaft gespeichert wird.

## Schritt „Generieren von Datensatzdokument“{#generate-document-of-record-step}

Wenn ein Formular ausgefüllt oder eingereicht wird, können Sie das Formular in gedruckter Form oder als Dokument speichern. Dies wird als Datensatzdokument (DOR) bezeichnet. Sie können den Schritt „Generieren von Datensatzdokument“ verwenden, um eine schreibgeschützte oder interaktive PDF-Version eines adaptiven Formulars zu erstellen. Die PDF-Version enthält Informationen, die zusammen mit dem Layout des adaptiven Formulars in das Formular eingegeben werden.

Der Schritt „Nachweisdokument“ hat die folgenden Eigenschaften:

**Adaptives Formular** verwenden: Geben Sie die Methode zum Suchen des adaptiven Eingabefelds an. Sie können das adaptive Formular verwenden, das an den Workflow gesendet wird, in einem absoluten Pfad verfügbar ist oder in einem Pfad in einer Variablen verfügbar ist. Sie können eine Variable des Datentyps String verwenden, um den Pfad im Feld **Variable auswählen anzugeben, um** aufzulösen.\
Sie können mehrere adaptive Formulare mit einem Workflow verknüpfen. Daher können Sie mithilfe der verfügbaren Eingabemethoden ein adaptives Formular zur Laufzeit angeben.

**Adaptiver Formularpfad**: Geben Sie den Pfad des adaptiven Formulars an. Das Feld ist verfügbar, wenn Sie die Option **Verfügbar unter einem absoluten Pfad** im Feld **Adaptives Formular verwenden** auswählen.

**Wählen Sie Eingabedaten mit:** Pfad der Eingabedaten für das adaptive Formular. Sie können die Daten an einem Speicherort relativ zur Nutzlast speichern, einen absoluten Pfad der Daten angeben oder Daten abrufen, die in einer Variablen des Dokument-, JSON- oder XML-Datentyps gespeichert sind. Die Eingabedaten werden mit dem adaptiven Formular zusammengeführt, um ein Datensatzdokument zu erstellen.

**Wählen Sie den Pfad der Anlage &quot;Eingabe&quot;aus, indem Sie:** Pfad der Anlagen verwenden. Diese Anhänge sind im Datensatzdokument enthalten. Sie können die Anlagen an einem Speicherort relativ zur Nutzlast belassen, einen absoluten Pfad der Anlagen angeben oder Anlagen abrufen, die in einer Variablen des Dokument-Datentyps gespeichert sind.

Wenn Sie den Pfad eines Ordners angeben, z. B. Anlagen, werden alle Dateien, die direkt im Ordner verfügbar sind, an das Datensatzdokument angehängt. Wenn Dateien in den Ordnern verfügbar sind, die im angegebenen Pfad für den Anhang direkt verfügbar sind, werden die Dateien im Datensatzdokument als Anlagen aufgenommen. Wenn sich Ordner in direkt verfügbaren Ordnern befinden, werden diese übersprungen.

**Generiertes Dokument aus Datensatz speichern mit folgenden Optionen:** Geben Sie den Speicherort an, an dem ein Dokument Datensatzdatei gespeichert werden soll. Sie können den Payload-Ordner überschreiben, Dokument des Datensatzes an einem Speicherort im Payload-Ordner ablegen oder das Dokument des Datensatzes in einer Variablen des Dokument-Datentyps speichern.

**Gebietsschema**: Geben Sie die Sprache des Datensatzdokuments an. Wählen Sie **Literal** aus, um das Gebietsschema aus einer Dropdown-Liste auszuwählen, oder wählen Sie **Variable**, um das Gebietsschema aus dem Wert abzurufen, der in einer Variablen des Zeichenfolgendatentyps gespeichert ist. Sie müssen den Gebietsschema-Code definieren, während Sie den Wert für das Gebietsschema in einer Variablen speichern. Geben Sie beispielsweise **en_US** für Englisch und **fr_FR** für Französisch an.

## Schritt „Formulardatenmodelldienst aufrufen“{#invoke-form-data-model-service-step}

Sie können [AEM Forms-Datenintegration](../../forms/using/data-integration.md) verwenden, um unterschiedliche Datenquellen zu konfigurieren und Verbindungen zu ihnen herzustellen. Diese Datenquellen können eine Datenbank, ein Webdienst, ein REST-Dienst, ein OData-Dienst und eine CRM-Lösung sein. Mit AEM Forms-Datenintegration können Sie ein Formulardatenmodell erstellen, das verschiedene Dienste umfasst, um Vorgänge zum Datenabruf, Hinzufügen und Aktualisieren in der konfigurierten Datenbank durchzuführen. Sie können den **Schritt „Formulardatenmodelldienst aufrufen“** verwenden, um ein Formulardatenmodell (FDM) zu wählen und die Dienste des FDM abzurufen, zu aktualisieren oder Daten unterschiedlichen Datenquellen hinzuzufügen.

Um die Eingaben für Felder des Schritts zu erläutern, werden die folgende Datenbanktabelle und JSON-Datei als Beispiel verwendet:

**Beispiel: Tabelle „Kundendetails“**

<table>
 <tbody> 
  <tr> 
   <td>Property</td> 
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
* **Eingabe für Dienste > Geben Sie Eingabedaten mithilfe von Literal-, Variablen- oder Workflow-Metadaten und einer JSON-Datei** an: Ein Dienst kann mehrere Argumente haben. Wählen Sie die Option aus, um den Wert der Dienstargumente von einer Workflow-Metadateneigenschaft, einem JSON-Objekt, einer Variablen abzurufen oder den Wert direkt in das bereitgestellte Textfeld einzugeben:

   * **Literal:** Verwenden Sie die Option, wenn Sie den genauen zu spezifizierenden Wert kennen. Beispiel: srose@we.info.
   * **Variable:** Verwenden Sie die Option, um den in einer Variablen gespeicherten Wert abzurufen.
   * **Aus Workflow-Metadaten abrufen:** Verwenden Sie die Option, wenn der zu verwendende Wert in einer Workflow-Metadaten-Eigenschaft gespeichert wird. Zum Beispiel emailAddress.
   * **JSON Dot Notation:** Verwenden Sie die Option, wenn der zu verwendende Wert in einer JSON-Datei enthalten ist. Beispiel: Insurance.customerDetails.emailAddress. Die Option &quot;JSON-Punktnotation&quot;ist nur verfügbar, wenn die Option &quot;Eingabefelder aus Eingabe-JSON zuordnen&quot;ausgewählt ist.
   * **Zuordnen von Eingabefelder aus der Eingabe JSON:** Geben Sie den Pfad einer JSON-Datei an, um den Eingabewert einiger Service-Parameter aus der JSON-Datei abzurufen. Der Pfad der JSON-Datei kann relativ zur Nutzlast, zu einem absoluten Pfad, sein oder Sie können ein JSON-Eingabedatum mit einer JSON- oder dem Formulardatenmodelltyp auswählen.

* **Input for services > Provide input data using variable or a JSON file:** Wählen Sie die Option, um Werte für alle Argumente aus einer JSON-Datei abzurufen, die unter einem absoluten Pfad, einem Pfad relativ zur Payload oder in einer Variablen gespeichert wurde.
* **Wählen Sie Input JSON-Dokument mit**: Die JSON-Datei, die Werte für alle Dienstargumente enthält. Der Pfad der JSON-Datei kann **relativ zur Payload** oder einem **absoluten Pfad sein.** Sie können das JSON-Eingabedatenmodell auch mit einer Variablen des JSON- oder des Formulardatenmodells abrufen.

* **JSON Dot Notation:** Lassen Sie das Feld leer, um alle Objekte der angegebenen JSON-Datei als Eingabe für Service-Parameter zu verwenden. Um ein bestimmtes JSON-Objekt aus der angegebenen JSON-Datei als Eingabe für Service-Parameter zu lesen, geben Sie die Dot Notation für das JSON-Objekt an, z. B. wenn Sie ein JSON ähnlich wie am Anfang des Abschnitts aufgeführt haben, geben Sie insurance.customerDetails an, um alle Details eines Kunden als Eingabe für den Dienst anzugeben.
* **Output of service > Map and write output values to variable or metadata:** Select the option to save the output values as properties of the workflow instance metadata node in crx-repository. Geben Sie den Namen der Metadateneigenschaft an und wählen Sie das entsprechende Dienstausgabeattribut, das der Metadateneigenschaft zugeordnet werden soll, ordnen Sie z. B. die vom Output-Dienst zurückgegebene Telefonnummer mit der Eigenschaft phone_number den Workflow-Metadaten zu. Gleichermaßen können Sie die Ausgabe in einer Variablen des Typs &quot;Lang&quot;speichern. Wenn Sie eine Eigenschaft für das Ausgabeattribut **[!UICONTROL Dienst auswählen, das zugeordnet werden soll]**, werden für die Option **[!UICONTROL Ausgabe speichern unter]** nur Variablen gefüllt, die Daten der ausgewählten Eigenschaft speichern können.

* **Ausgabe des Dienstes > Ausgabe in Variable oder JSON-Datei speichern:** Wählen Sie die Option zum Speichern der Ausgabewerte in einer JSON-Datei unter einem absoluten Pfad, in einem Pfad relativ zur Payload oder in einer Variablen .
* **Speichern Sie Output JSON-Dokument mit den folgenden Optionen:** Speichern Sie die JSON-Ausgabedatei. Der Pfad der JSON-Ausgabedatei kann relativ zur Payload oder einem absoluten Pfad sein. Sie können die JSON-Ausgabedatei auch mit einer Variablen des JSON- oder Formulardatenmodells-Datentyps speichern.

## Schritt „Dokument signieren“{#sign-document-step}

Mit dem Schritt „Dokument signieren“ können Sie Adobe Sign zum Signieren von Dokumenten verwenden. Der Schritt „Dokument signieren“ hat folgende Eigenschaften:

* **Name der Vereinbarung:** Geben Sie den Titel der Vereinbarung an. Der Name der Vereinbarung wird Teil des Betreffs und des Nachrichtentextes der E-Mail, die an die Unterzeichner gesendet wird. Sie können den Namen entweder in einer Variablen des Datentyps String speichern oder **Literal** auswählen, um den Namen manuell hinzuzufügen.

* **Gebietsschema:** Geben Sie die Sprache für die E-Mail- und Bestätigungsoptionen an. Sie können das Gebietsschema entweder in einer Variablen des Datentyps String speichern oder **Literal** auswählen, um das Gebietsschema aus der Liste der verfügbaren Optionen auszuwählen. Sie müssen den Gebietsschema-Code definieren, während Sie den Wert für das Gebietsschema in einer Variablen speichern. Geben Sie beispielsweise **en_US** für Englisch und **fr_FR** für Französisch an.

* **Cloud-Konfiguration für Adobe Sign**: Wählen Sie eine Adobe Sign Cloud-Konfiguration. Wenn Sie Adobe Sign für AEM Forms nicht konfiguriert haben, lesen Sie den Abschnitt [Adobe Sign in AEM Forms integrieren](../../forms/using/adobe-sign-integration-adaptive-forms.md).

* **Wählen Sie das zu unterzeichnende Dokument aus:** Sie können ein Dokument an einem Speicherort im Verhältnis zur Nutzlast auswählen, Nutzlast als Dokument verwenden, einen absoluten Pfad des Dokuments angeben oder das Dokument abrufen, das in einer Variablen des Dokument-Datentyps gespeichert ist.
* **Tage bis Abgabetermin:** Ein Dokument wird als „fällig“ (Abgabetermin überschritten) gekennzeichnet, nachdem für die im Feld **Tage bis Abgabetermin** angegebene Anzahl von Tagen keine Aktivität für die Aufgabe ermittelt wurde. Die Anzahl der Tage wird gezählt, nachdem das Dokument einem Benutzer zur Unterzeichnung zugewiesen wurde.
* **Häufigkeit der E-Mail-Erinnerung:** Sie können eine Erinnerungs-E-Mail im täglichen oder wöchentlichen Intervall senden. Die Woche wird ab dem Tag gezählt, an dem das Dokument einem Benutzer zum Signieren zugewiesen wurde.
* **Signaturvorgang:** Sie können ein Dokument in einer sequenziellen oder parallelen Reihenfolge signieren. Bei sequenzieller Anordnung erhält jeder Unterzeichner das Formular in Folge. Nachdem der erste Unterzeichner das Dokument signiert hat, wird das Formular an den nächsten Unterzeichner gesendet und so weiter. Bei paralleler Anordnung können mehrere Unterzeichner ein Formular gleichzeitig signieren.
* **Umleitungs-URL:** Geben Sie eine Umleitungs-URL an. Nachdem das Dokument signiert wurde, können Sie den Empfänger an eine URL umleiten. Normalerweise enthält diese URL eine Dankesnachricht oder weitere Anweisungen.
* **Workflow-Phase:** Ein Workflow kann mehrere Phasen enthalten. Diese Phasen werden in der AEM Inbox angezeigt. Sie können diese Phasen in den Eigenschaften des Modells definieren (Sidekick > Seite> Seiteneigenschaften > Phasen).
* **Unterzeichner wählen:** Geben Sie die Methode zum Auswählen von Unterzeichnern für das Dokument an. Sie können den Workflow einem Benutzer oder einer Gruppe dynamisch zuweisen oder manuell Details einem Unterzeichner hinzufügen.
* **Skript oder Dienst zur Auswahl von Unterzeichnern:** Die Option ist nur verfügbar, wenn die Option „Dynamisch“ im Feld „Unterzeichner auswählen“ ausgewählt ist. Sie können ein ECMAScript oder einen Dienst angeben, um Unterzeichner und Überprüfungsoptionen für ein Dokument auszuwählen.
* **Unterzeichnerdetails:** Die Option ist nur verfügbar, wenn die Option „Manuell“ im Feld „Unterzeichner auswählen“ ausgewählt ist. Geben Sie die E-Mail-Adresse an und wählen Sie einen optionalen Bestätigungsmechanismus. Bevor Sie einen Zwei-Schritt-Bestätigungsmechanismus auswählen, vergewissern Sie sich, dass die entsprechende Verifizierungsoption für das konfigurierte Adobe Sign-Konto aktiviert ist. Sie können eine Variable des Datentyps String verwenden, um Werte für die Felder **[!UICONTROL E-Mail]**, **[!UICONTROL Ländercode]** und **[!UICONTROL Telefonnummer]** zu definieren. Die Felder **[!UICONTROL Ländercode]** und **[!UICONTROL Telefonnummer]** werden nur angezeigt, wenn Sie **[!UICONTROL Telefonbestätigung]** aus der Dropdown-Liste **[!UICONTROL 2-stufige Überprüfung]** auswählen.
* **Statusvariable:** Ein Adobe Sign-aktiviertes Dokument speichert den Signaturstatus des Dokuments in einer Variablen des Datentyps String. Geben Sie den Namen der Statusvariable (adobeSignStatus) an. Eine Statusvariable einer Instanz ist in CRXDE unter /etc/workflow/instances/&lt;server>/&lt;date-time>/&lt;instance of workflow model>/workItems/&lt;node>/metaData enthält den Status einer Variablen verfügbar.
* **Unterschriebenes Dokument mit den folgenden Optionen speichern:** Geben Sie den Speicherort an, an dem unterschriebene Dokumente aufbewahrt werden sollen. Sie können die Payload-Datei überschreiben, das signierte Dokument an einem Speicherort im Payload-Ordner ablegen oder das signierte Dokument in einer Variablen des Dokuments speichern.

## Schritt „Document Services“{#document-services-steps}

Bei AEM Document Services handelt es sich um einen Satz an OSGi-Diensten zum Erstellen, Zusammenstellen und Sichern von PDF-Dokumenten. AEM Forms stellt für jeden Dokument-Dienst einen AEM Workflow-Schritt bereit.

Ähnlich wie bei anderen AEM Forms-Arbeitsablaufschritten wie &quot;Aufgabe zuweisen&quot;, &quot;E-Mail senden&quot;und &quot;Dokument unterschreiben&quot;können Sie Variablen in allen AEM Dokument Services-Schritten verwenden. Weitere Informationen zum Erstellen und Verwalten von Variablen finden Sie unter [Variablen in AEM](../../forms/using/variable-in-aem-workflows.md).

### Schritt „Dokumentzeitstempel einfügen“{#apply-document-time-stamp-step}

Fügen Sie einen Zeitstempel in das Dokument ein. Sie geben Dokumentdetails wie den Pfad des Eingabedokuments, den Namen des Eingabedokuments und den Speicherort für die exportierten Daten an. Sie können die vorhandene Nutzdatendatei überschreiben, einen anderen Dateinamen wählen, um Daten in einer anderen Datei im Payload-Ordner zu speichern, einen absoluten Pfad zu den Daten bereitzustellen oder Daten in einer Variablen des Dokument-Datentyps zu speichern.

### Schritt „In Bild umwandeln“{#convert-to-image-step}

Konvertiert ein PDF-Dokument in eine Liste von Bildern. Unterstützte Bildformate sind JPEG, JPEG2000, PNG und TIFF. Die folgenden Informationen gelten für Konvertierungen in TIFF-Bilder:

* Eine mehrseitige TIFF-Datei wird generiert.
* Einige Anmerkungen sind nicht in TIFF-Bildern enthalten. Anmerkungen, die Acrobat zur Erstellung ihrer Darstellung benötigen, sind nicht enthalten.

### Schritt „Nach PDF/A konvertieren“  {#convert-to-pdf-a-step}

Konvertiert ein PDF-Dokument mit den verfügbaren Optionen in das PDF/A-Format. Die PDF/A-Version des Portable Document Format (PDF) ist auf die Archivierung und Langzeitarchivierung von Dokumenten spezialisiert. 

### Schritt „Konvertieren nach PS“{#convert-to-ps-step}

Konvertieren von PDF-Dokumenten in PostScript – Beim Konvertieren in PostScript können Sie für den Konvertierungsvorgang das Quelldokument und die PostScript-Ebene (2 oder 3) angeben. Das PDF-Dokument, das in eine PostScript-Datei konvertiert wird, muss nicht interaktiv sein.

### Schritt „PDF vom angegebenen Typ erstellen“  {#create-pdf-from-specified-type-step}

Generiert ein PDF-Dokument aus einer Eingabedatei. Das Dokument für die Eingabe kann relativ zur Nutzlast sein, einen absoluten Pfad haben, selbst Nutzlast sein oder in einer Variablen des Dokument-Datentyps gespeichert werden.

### Schritt „PDF aus URL/HTML/ZIP erstellen“{#create-pdf-from-url-html-zip-step}

Erstellt ein PDF-Dokument anhand der bereitgestellten URL-, HTML- und ZIP-Datei.

### Schritt „Daten exportieren“  {#export-data-step}

Exportiert Daten aus einem PDF-Formular oder aus einer XDP-Datei Sie müssen den Dateipfad des Eingabedokuments und das Exportdatenformat eingeben. Die Optionen für das Exportdatenformat sind Auto, XDP und XmlData.

### Schritt „PDF in den angegebenen Format exportieren“  {#export-pdf-to-specified-type-step}

Konvertiert ein PDF-Dokument in ein ausgewähltes Format.

### Schritt „Nicht interaktive PDF-Dateien generieren“  {#generatenoninteractive}

Generieren Sie eine nicht interaktive PDF-Datei. Es bietet verschiedene Anpassungsoptionen.

>[!NOTE]
>
>Sie können Variablen verwenden, um die Vorlagendatei für Eingabedateien anzugeben. Speichern Sie den Pfad der Vorlagendatei in einer Variablen des Datentyps String.

### Schritt „Daten importieren“{#import-data-step}

Führt Formulardaten in einem PDF-Formular zusammen. Sie können Formulardaten in ein PDF-Formular importieren.

### Schritt „DDX aufrufen“  {#invokeddx}

Führt die DDX-Datei in der angegebenen Zuordnung von Eingabedokumenten aus und gibt die veränderten PDF-Dokumente zurück.

>[!NOTE]
>
>Sie können Variablen verwenden, um die DDX-Datei für Eingabe-Dokumente anzugeben. Speichern Sie die DDX-Datei in einer Variablen des Dokument- oder XML-Datentyps.

### Schritt „PDF optimieren“{#optimize-pdf-step}

Optimiert PDF-Dateien durch Reduzierung ihrer Größe. Das Ergebnis dieser Konvertierung sind PDF-Dateien, die kleiner als ihre Originalversionen sein können. Bei diesem Vorgang werden außerdem PDF-Dokumente in die in den Optimierungsparametern angegebene PDF-Version konvertiert.

Die Optimierungseinstellungen geben an, wie Dateien optimiert werden. Hier sind Beispieleinstellungen:

* Zielgruppe PDF-Version
* Objekte wie JavaScript-Aktionen und eingebettete Seitenminiaturen verwerfen
* Verwerfen von Benutzerdaten wie Kommentaren und Dateianlagen
* Ungültige oder nicht verwendete Einstellungen verwerfen
* Komprimieren unkomprimierter Daten oder Verwenden effizienterer Komprimierungsalgorithmen
* Entfernen von eingebetteten Schriftarten
* Festlegen von Transparenzwerten

### Schritt „PDF-Formular ausgeben“  {#renderpdf}

Rendert ein Formular, das in Form Designer (XDP) erstellt wurde, in ein PDF-Formular.

>[!NOTE]
>
>Sie können Variablen verwenden, um die Vorlagendatei für Eingabedateien anzugeben. Speichern Sie den Pfad der Vorlagendatei in einer Variablen des Datentyps String.

### Schritt „Dokument absichern“{#secure-document-step}

Verschlüsseln, signieren und zertifizieren Sie ein Dokument. AEM Forms unterstützt sowohl die kennwortbasierte als auch die zertifikatsbasierte Verschlüsselung. Sie können auch zwischen verschiedenen Algorithmen zum Signieren von Dokumenten wählen. Zum Beispiel SHA-256 und SH-512. Sie können den Workflow-Schritt zum Reader Extending von PDF-Dokumenten verwenden. Der Workflow-Schritt bietet Optionen zum Aktivieren von Barcode-Dekodierung, digitalen Signaturen, Importieren und Exportieren von PDF-Daten und anderen Optionen.

### Schritt „An Drucker senden“{#send-to-printer-step}

Senden Sie ein Dokument direkt an einen Drucker. Der Dienst unterstützt die folgenden Druckerzugriffsmechanismen:

* **Drucker mit direktem Zugriff**: Ein Drucker, der auf demselben Computer installiert ist, wird als Drucker mit direktem Zugriff und der Computer als Druckerhost bezeichnet. Dieser Druckertyp kann ein lokaler Drucker sein, der direkt an den Computer angeschlossen ist.
* **Drucker mit indirektem Zugriff**: Der Drucker, der auf einem Druckserver installiert ist, steht für den Zugriff von anderen Computern zur Verfügung. Es stehen Technologien wie das Common UNIX® Printing System (CUPS) und das LDP-Protokoll (Line Printer Daemon) zur Verfügung, um eine Verbindung zu einem Netzwerkdrucker herzustellen. Um auf einen Drucker mit indirektem Zugriff zuzugreifen, geben Sie die IP- oder Hostnamen des Druckservers an. Bei Verwendung dieses Mechanismus können Sie ein Dokument an einen LPD-URI senden, wenn im Netzwerk ein LP-Daemon ausgeführt wird. Mit dem Mechanismus können Sie das Dokument zu jedem Drucker weiterleiten, der mit dem Netzwerk verbunden ist, in dem ein LP-Daemon ausgeführt wird.

### Druckten Ausgabeschritt {#generatePrintedOutput} generieren

Der Schritt generiert eine PCL-, PostScript-, ZPL-, IPL-, TPCL- oder DPL-Ausgabe, sofern ein Formularentwurf und eine Datendatei vorhanden sind. Die Datendatei wird mit dem Formularentwurf zusammengeführt und für den Druck formatiert. Die durch diesen Schritt generierte Ausgabe kann direkt an einen Drucker gesendet oder als Datei gespeichert werden. Es wird empfohlen, diesen Schritt zu verwenden, wenn Sie Formularentwürfe oder Daten aus einer Anwendung verwenden möchten. Wenn sich Ihre Formularentwürfe oder Formularentwürfe im Netzwerk, im lokalen Dateisystem oder im HTTP-Speicherort befinden, verwenden Sie den Vorgang generatePrintedOutput.

Beispiel: Ihre Anwendung erfordert, dass Sie einen Formularentwurf mit einer Datendatei zusammenführen. Die Daten beinhalten Hunderte von Datensätzen. Außerdem muss die Ausgabe an einen Drucker gesendet werden, der ZPL unterstützt. Der Formularentwurf und Ihre Eingabedaten befinden sich in einer Anwendung. Verwenden Sie den generatePrintedOutput-Vorgang, um einzelne Datensätze mit einem Formularentwurf zusammenführen und die Ausgabe an einen Drucker zu senden, der ZPL unterstützt.

Der Schritt &quot;Drucken generieren&quot;verfügt über die folgenden Eigenschaften:

**Eingabeeigenschaften**

* **[!UICONTROL Wählen Sie die Vorlagendatei mit]**: Geben Sie den Pfad der Vorlagendatei an. Sie können die Vorlagendatei unter Verwendung des Pfades auswählen, der relativ zur Nutzlast ist, unter einem absoluten Pfad gespeichert wird oder eine Variable des Dokument-Datentyps verwendet. Beispiel: [Payload_Directory]/Workflow/data.xml. Wenn der Pfad nicht im CRX-Repository vorhanden ist, kann ein Administrator den Pfad erstellen, bevor er verwendet wird. Darüber hinaus können Sie Payload auch als Eingabedatendatei akzeptieren.

* **[!UICONTROL Wählen Sie das Dokument data mit]**: Geben Sie den Pfad einer Eingabedatendatei an. Sie können die Eingabedatendatei unter Verwendung des Pfades auswählen, der relativ zur Nutzlast ist, unter einem absoluten Pfad gespeichert wird oder eine Variable des Dokument-Datentyps verwendet. Beispiel: [Payload_Directory]/Workflow/data.xml. Wenn der Pfad nicht im CRX-Repository vorhanden ist, kann ein Administrator den Pfad erstellen, bevor er verwendet wird.

* **[!UICONTROL Druckerformat]**: Ein Wert im Druckformat, der die Seitenbeschreibungssprache angibt, die verwendet werden soll, wenn keine XDC-Datei bereitgestellt wird, um den Ausgabestream zu generieren. Wenn Sie einen Literalwert angeben, wählen Sie einen der folgenden Werte:

   * **[!UICONTROL Benutzerspezifische PCL]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei für PCL anzugeben.
   * **[!UICONTROL Benutzerdefiniertes PostScript]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei für PostScript anzugeben.
   * **[!UICONTROL Benutzerspezifische ZPL]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei für ZPL anzugeben.
   * **[!UICONTROL Generisches Farb-PCL (5c)]**: Verwenden Sie eine generische Farbe PCL (5c).
   * **[!UICONTROL Generisches PostScript Level3]**: Verwenden Sie generische PostScript Level 3.
   * **[!UICONTROL ZPL 300 DPI]**: Verwenden Sie ZPL 300 DPI. Die Datei zpl300.xdc wird verwendet.
   * **[!UICONTROL ZPL 600 DPI]**: Verwenden Sie ZPL 600 DPI. Die Datei zpl600.xdc wird verwendet.
   * **[!UICONTROL Benutzerdefiniertes IPL]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei für IPL anzugeben.
   * **[!UICONTROL IPL 300 DPI]**: Verwenden Sie IPL 300 DPI. Die Datei ipl300.xdc wird verwendet.
   * **[!UICONTROL IPL 400 DPI]**: Verwenden Sie IPL 400 DPI. Die Datei ipl400.xdc wird verwendet.
   * **[!UICONTROL Benutzerspezifische TPCL]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei für TPCL anzugeben.
   * **[!UICONTROL TPCL 305 DPI]**: Verwenden Sie TPCL 300 DPI. Die Datei tpcl305.xdc wird verwendet.
   * **[!UICONTROL PCL 600 DPI]**: Verwenden Sie TPCL 600 DPI. Die Datei tpcl600.xdc wird verwendet.
   * **[!UICONTROL Benutzerdefinierte DPL]**: Verwenden Sie die Option, um eine benutzerdefinierte XDC-Datei DPL anzugeben.
   * **[!UICONTROL DPL300DPI]**: Verwenden Sie DPL 300 DPI. Die Datei dpl300.xdc wird verwendet.
   * **[!UICONTROL DPL406DPI]**: Verwenden Sie DPL 400 DPI. Die Datei dpl406.xdc wird verwendet.
   * **[!UICONTROL DPL600DPI]**: Verwenden Sie DPL 600 DPI. Die Datei dpl600.xdc wird verwendet.

**Ausgabeeigenschaften**

* **[!UICONTROL Output Dokument speichern unter]**: Geben Sie den Speicherort für die Ausgabedatei an. Sie können die Ausgabedatei an einem Speicherort speichern, der relativ zur Nutzlast ist, in einer Variablen oder einen absoluten Speicherort zum Speichern der Ausgabedatei angeben. Wenn der Pfad nicht im CRX-Repository vorhanden ist, kann ein Administrator den Pfad erstellen, bevor er verwendet wird.

**Erweiterte Eigenschaften**

* **[!UICONTROL Wählen Sie den Speicherort des Stammordners für Inhalte aus]**: Der Inhaltsstamm ist ein Zeichenfolgenwert, der den URI, den absoluten Verweis oder den Speicherort im Repository angibt, an dem die vom Formularentwurf verwendeten relativen Elemente abgerufen werden. Beispiel: Wenn der Formularentwurf relativ auf ein Bild verweist, z. B. ../myImage.gif, muss sich myImage.gif unter repository:// befinden. Der Standardwert ist repository://, der auf die Stammebene des Repositorys verweist.

   Wenn Sie ein Asset aus Ihrer Anwendung auswählen, muss der Inhaltsstamm-URI-Pfad die richtige Struktur aufweisen. Wenn beispielsweise ein Formular aus einer Anwendung namens SampleApp unter SampleApp/1.0/forms/Test.xdp gespeichert wird, muss der Inhaltsstamm-URI als repository://administrator@password/Applications/SampleApp/1.0/forms/ oder repository:/Applications/SampleApp/1.0/forms/ (wenn die Berechtigung null ist) angegeben werden. Wenn der Inhaltsstamm-URI auf diese Weise angegeben wird, werden die Pfade aller referenzierten Elemente im Formular für diesen URI aufgelöst.

* **[!UICONTROL Wählen Sie die XCI-Datei mit]**: XCI-Dateien werden verwendet, um Schriftarten und andere Eigenschaften zu beschreiben, die für Formularelemente verwendet werden. Sie können eine XCI-Datei relativ zur Nutzlast an einem absoluten Pfad oder mithilfe einer Variablen des Dokument-Datentyps belassen.

* **[!UICONTROL Gebietsschema]**: Gibt die Sprache an, in der das PDF-Dokument generiert wird. Wenn Sie einen Literalwert angeben, wählen Sie eine Sprache aus der Liste oder einen der folgenden Werte:
   * **So verwenden Sie den Serverstandard**: (Standard) Verwenden Sie die auf dem AEM Forms-Server konfigurierte Spracheinstellung. Die Spracheinstellung wird mithilfe von Administration Console konfiguriert. (Weitere Informationen finden Sie in der [Designer-Hilfe](http://www.adobe.com/go/learn_aemforms_designer_65_de).)

   * **So verwenden Sie einen benutzerspezifischen Wert**: Geben Sie den Gebietsschema-Code in das Feld &quot;Literal&quot;ein oder wählen Sie eine Zeichenfolgenvariable mit dem Gebietsschema-Code. Eine vollständige Liste der unterstützten Gebietsschemas finden Sie unter http://java.sun.com/j2se/1.5.0/docs/guide/intl/locale.doc.html.

* **[!UICONTROL Kopien]**: Ein ganzzahliger Wert, der die Anzahl der Exemplare angibt, die für die Ausgabe generiert werden sollen. Der Standardwert ist 1. 

* **[!UICONTROL Duplexdruck]**: Ein Seitenumbruchwert, der angibt, ob der zweiseitige oder einseitige Druck verwendet werden soll. Drucker, die PostScript und PCL unterstützen, verwenden diesen Wert. Wenn Sie einen Literalwert angeben, wählen Sie einen der folgenden Werte:
   * **[!UICONTROL Duplex, lange Kante]**: Verwenden Sie den zweiseitigen Druck und den zweiseitigen Druck unter Verwendung von Seitenumbrüchen.
   * **[!UICONTROL Duplex Kurze Kante]**: Verwenden Sie den zweiseitigen Druck und den zweiseitigen Druck mithilfe der kurzen Seitenumbrüche.
   * **[!UICONTROL Simplex]**: Verwenden Sie den einseitigen Druck.