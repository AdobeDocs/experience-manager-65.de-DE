---
title: Konfigurieren von Geschäftskalendern
description: Geschäftskalender definieren Geschäftstage und geschäftsfreie Tage für Ihre Organisation. Erfahren Sie, wie Sie die Geschäftskalender konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 4282718a-41f1-411a-9cd7-8c470005107d
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: ht
source-wordcount: '1889'
ht-degree: 100%

---

# Konfigurieren von Geschäftskalendern {#configuring-business-calendars}

*Geschäftskalender* definieren Geschäftstage und geschäftsfreie Tage (z. B. gesetzliche Feiertage, Wochenenden und Betriebsferien) für Ihre Organisation. Bei Verwendung von Geschäftskalendern überspringt AEM Forms geschäftsfreie Tage bei der Durchführung bestimmter Datumsberechnungen. In Workbench können Sie festlegen, ob Geschäftskalender für Ereignisse, die Benutzenden zugeordnet sind (wie Aufgabenerinnerungen, Termine und Eskalationen) oder für Aktionen, die Benutzenden nicht zugeordnet sind (wie z. B. Timer-Ereignisse und der Wait-Dienst), verwendet werden sollen.

Beispielsweise ist eine Aufgabenerinnerung so konfiguriert, dass sie drei Werktage nach der Zuweisung der Aufgabe an eine Benutzerin bzw. einen Benutzer erfolgt. Die Aufgabe wird am Donnerstag zugewiesen. Die folgenden drei Tage sind jedoch keine Geschäftstage, da der Freitag ein Nationalfeiertag ist und die nächsten zwei Tage Wochenendtage sind. Die Erinnerung wird daher am Mittwoch der nächsten Woche versandt.

>[!NOTE]
>
>Bei der Berechnung von Daten und Uhrzeiten mithilfe von Geschäftskalendern verwendet AEM Forms das Datum und die Uhrzeit des Servers, auf dem es ausgeführt wird, und passt nicht den Unterschied zwischen Zeitzonen an. Wenn beispielsweise eine Aufgabenerinnerung um 10:00 Uhr auf einem Server geplant ist, der in London läuft, sich die Person, die die Erinnerung erhält, jedoch in New York City befindet, erhält die Person die Erinnerung um 5:00 Uhr Ortszeit.

## Verwenden des Standardgeschäftskalenders {#using-the-default-business-calendar}

AEM Forms bietet einen Standardgeschäftskalender (namens *Integrierter Kalender*), in dem Samstage und Sonntage als geschäftsfreie Tage festgelegt sind. Wenn alle Benutzenden in Ihrer Organisation dieselben geschäftsfreien Tage haben, können Sie den Standardgeschäftskalender entsprechend Ihrer Organisation aktualisieren. Wenn Sie nur den Standardgeschäftskalender verwenden, müssen Sie keine Geschäftskalender in der Benutzerverwaltung aktivieren oder Zuordnungen bereitstellen. Wenn keine anderen Geschäftskalender definiert sind, verwendet AEM Forms den Standardgeschäftskalender.

## Einrichten mehrerer Geschäftskalender {#setting-up-multiple-business-calendars}

Wenn einige Personen in Ihrer Organisation unterschiedliche geschäftsfreie Tage haben, können Sie mehrere Geschäftskalender definieren und Zuordnungen konfigurieren, die die Auflösung eines Geschäftskalenders für eine Person zur Laufzeit ermöglichen.

### Definieren mehrerer Geschäftskalender {#define-multiple-business-calendars}

1. Entscheiden Sie, wie Sie den entsprechenden Geschäftskalender mit einer Person verknüpfen. Es gibt zwei Möglichkeiten, einen Geschäftskalender mit einer Benutzerin bzw. einem Benutzer zu verknüpfen:

   **Gruppenmitgliedschaft**: Ein Geschäftskalender kann Benutzenden auf Basis ihrer Gruppenmitgliedschaft zugewiesen werden. In diesem Fall verwenden alle Benutzenden der Gruppe denselben Geschäftskalender.

   Ist eine Person Mitglied in zwei verschiedenen Gruppen, die unterschiedlichen Geschäftskalendern zugeordnet sind, verwendet AEM Forms den ersten in den Suchergebnissen gefundenen Kalender. In diesem Fall sollten Sie die Verwendung von Geschäftskalenderschlüsseln erwägen, um Benutzende mit Geschäftskalendern zu verknüpfen.

   **Geschäftskalenderschlüssel**: Einem Benutzer kann ein Geschäftskalender auf Basis eines Geschäftskalenderschlüssels zugewiesen werden, wobei es sich um eine Einstellung handelt, die in User Management festgelegt wird. Anschließend ordnen Sie den Geschäftskalenderschlüssel einem Geschäftskalender im Forms-Workflow zu.

    Die Methode zum Zuweisen von Geschäftskalenderschlüsseln zu Benutzern ist davon abhängig, ob eine Unternehmens-, eine lokale oder eine Hybrid-Domain verwendet wird. Detaillierte Informationen zum Einrichten von Domains finden Sie unter [Hinzufügen von Domains](/help/forms/using/admin-help/adding-domains.md#adding-domains). 

    Wenn Sie eine lokale oder Hybrid-Domain verwenden, werden Informationen zu Benutzern nur in der User Management-Datenbank gespeichert. Um den Geschäftskalenderschlüssel für diese Benutzenden festzulegen, geben Sie beim Hinzufügen oder Bearbeiten einer Person in der Benutzerverwaltung im Feld „Geschäftskalenderschlüssel“ eine Zeichenfolge ein. (Siehe [Hinzufügen und Konfigurieren von Benutzenden](/help/forms/using/admin-help/adding-configuring-users.md#adding-and-configuring-users).) Anschließend ordnen Sie die Geschäftskalenderschlüssel (die Zeichenfolgen) den Geschäftskalendern im Forms-Workflow zu. (Siehe [Zuordnen von Benutzenden und Gruppen zu einem Geschäftskalender](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar).)

    Wenn Sie eine Unternehmens-Domain verwenden, befinden sich Informationen zu Benutzern in einem Speichersystem von Drittanbietern wie etwa einem LDAP-Ordner, der von User Management mit der User Management-Datenbank synchronisiert wird. Dies ermöglicht Ihnen die Zuordnung eines Geschäftskalenderschlüssels zu einem Feld im LDAP-Ordner. Wenn beispielsweise jeder Benutzerdatensatz in Ihrem Ordner ein Feld „Land“ enthält und Sie Geschäftskalender auf Grundlage des Landes zuweisen möchten, in dem sich die Person befindet, geben Sie den Feldnamen von „Land“ im Feld „Geschäftskalenderschlüssel“ an, wenn Sie die Benutzereinstellungen für den Ordner angeben. (Siehe [Konfigurieren von Verzeichnissen](/help/forms/using/admin-help/configuring-directories.md#configuring-directories).) Anschließend können Sie die Geschäftskalenderschlüssel (die für das Feld „Land“ im LDAP-Verzeichnis definierten Werte) zu Geschäftskalendern im Forms-Workflow zuordnen. (Siehe [Zuordnen von Benutzenden und Gruppen zu einem Geschäftskalender](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar).)

1. Definieren Sie im Forms-Workflow einen Kalender für jede Gruppe von Benutzenden, die dieselben geschäftsfreien Tage haben. (Siehe [Erstellen oder Aktualisieren eines Geschäftskalenders](configuring-business-calendars.md#create-or-update-a-business-calendar).)
1. Ordnen Sie im Forms-Workflow die Geschäftskalenderschlüssel oder Gruppenmitgliedschaften für jeden Kalender zu. (Siehe [Zuordnen von Benutzenden und Gruppen zu einem Geschäftskalender](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar).)
1. In Workbench wählt die zuständige Person für die Prozessentwicklung, ob sie Geschäftskalender für Erinnerungen, Fristen und Eskalationen verwenden möchte. (Siehe [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63_de).)

   Wenn die für die Prozessentwicklung zuständige Person Geschäftskalender verwendet, wählt AEM Forms den entsprechenden Geschäftskalender dynamisch anhand der Benutzerverwaltungseinstellung und der in der Administrationskonsole definierten Geschäftskalenderzuordnungen aus. Falls keine Zuordnungen vorhanden sind, wird der Standardkalender verwendet.

   Wenn die für die Prozessentwicklung zuständige Person keine Geschäftskalender verwendet, wird bei der Datumsberechnung für das Ereignis jeder Tag als Geschäftstag behandelt. Ein Aufgabentermin kann beispielsweise so konfiguriert sein, dass er drei Tage nach der Zuweisung der Aufgabe an eine Person fällig wird. Die Aufgabe wird am Donnerstag zugewiesen. Der Aufgabentermin wird trotz des Wochenendes am Sonntag fällig.

## Erstellen oder Aktualisieren eines Geschäftskalenders {#create-or-update-a-business-calendar}

Wenn in Ihrer Organisation verschiedene Benutzergruppen mit unterschiedlichen geschäftsfreien Tagen vorhanden sind, können Sie mehrere Geschäftskalender definieren. Sie können auch an vorhandenen Kalendern Änderungen vornehmen, einschließlich des von AEM Forms bereitgestellten integrierten Standardkalenders.

>[!NOTE]
>
>Wenn Sie keinen Geschäftskalender erstellen, wird der Standardkalender verwendet.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Formular-Workflow“ > „Geschäftskalender“.
1. Um einen neuen Geschäftskalender hinzuzufügen, klicken Sie auf ![bus_cal_plus](assets/bus_cal_plus.png). In der Dropdown-Liste wird der Text „*Neuer Kalender*“ angezeigt. Markieren Sie den Text und geben Sie einen anderen Namen für Ihren Kalender ein.

   Wählen Sie zum Bearbeiten eines vorhandenen Geschäftskalenders diesen aus der Dropdown-Liste aus.

1. Wählen Sie unter „Geschäftsfreier Standardtag“ alle geschäftsfreien Wochentage aus, wie z. B. Wochenenden.
1. [Optional] Wählen Sie „Geschäftszeiten verwenden“ und geben Sie die Anfangs- und Endzeiten für die Geschäftstage an.

   Wenn Sie diese Option wählen, wird ein Ereignis, das vor dem angegebenen Zeitraum eintritt, an den Anfang des Zeitraums verschoben, und ein Ereignis, das nach dem Zeitraum eintritt, wird an die Anfangszeit des nächsten Geschäftstages verschoben.

   Nehmen wir zum Beispiel an, dass einer Person an einem Dienstag um 2:00 Uhr morgens eine Aufgabe zugewiesen wird und die Erinnerung für diese Aufgabe auf zwei Arbeitstage eingestellt ist. Ohne Geschäftszeiten erfolgt die Erinnerung am Donnerstag um 2:00 Uhr morgens. Sind die Geschäftszeiten auf 8:00 Uhr bis 17:00 Uhr festgelegt, wird die Erinnerung auf Donnerstag 8:00 Uhr verlegt. Ohne Geschäftszeiten würde eine Erinnerung, wenn das Erinnerungsereignis am Dienstag um 18:00 Uhr erstellt wurde, am Donnerstag nach Feierabend erfolgen. Sind die Geschäftszeiten auf 8:00 Uhr bis 17:00 Uhr festgelegt, erfolgt die Erinnerung am Freitag um 8:00 Uhr morgens.

1. Doppelklicken Sie im Kalender auf der linken Seite auf alle weiteren geschäftsfreien Tage, wie z. B. Feiertage. Tage, die in der Vergangenheit liegen, können nicht ausgewählt werden. Die von Ihnen ausgewählten geschäftsfreien Tage werden in einer Liste auf der rechten Seite angezeigt, wobei das Datum zweimal pro Zeile angezeigt wird. Wählen Sie das linke Datum aus, um einen Namen oder eine Beschreibung für den geschäftsfreien Tag einzugeben.

   Um einen arbeitsfreien Tag aus der Liste zu entfernen, klicken Sie auf ![Bus_cal_trash](assets/bus_cal_trash.png) neben dem Tag.

1. [Optional] Wenn dieser Kalender der Standardkalender sein soll, wählen Sie „Standardkalender“. Der Standardkalender wird verwendet, wenn keine anderen Kalenderzuordnungen für Benutzenden zugeordnete Ereignisse vorhanden sind oder wenn kein Geschäftskalender für das Timer-Ereignis oder den Wait-Dienst festgelegt ist. Der Standardkalender kann nicht gelöscht werden.
1. Wenn die Definition der geschäftsfreien Tage fertig gestellt ist, wählen Sie „Kalender aktiviert“, um den Kalender zu aktivieren, und klicken dann auf „Speichern“.

   Wenn Sie einen vorhandenen Kalender aktualisieren, wird die neue Version sofort gültig und wird für alle Geschäftskalenderberechnungen verwendet, einschließlich Aufgaben, die bereits ausgeführt werden.

   >[!NOTE]
   >
   >Wenn Sie den Kalender nicht aktivieren, wird der Standardkalender verwendet.

## Zuordnen von Benutzenden und Gruppen zu einem Geschäftskalender {#mapping-users-and-groups-to-a-business-calendar}

Es gibt zwei Methoden, um einer Benutzerin oder einem Benutzer einen Geschäftskalender zuzuordnen. Sie können Geschäftskalender Benutzenden auf Grundlage eines Geschäftskalenderschlüssels zuweisen oder auf Basis der Ordnergruppe, der die jeweilige Person angehört. Die von AEM Forms zu verwendende Methode wird auf der Registerkarte „Zuordnung“ festgelegt, wo auch die Geschäftskalenderschlüssel und Gruppen den Geschäftskalendern zugeordnet werden. Detaillierte Informationen zum Verknüpfen von Geschäftskalendern mit Benutzenden finden Sie unter [Einrichten mehrerer Geschäftskalender](configuring-business-calendars.md#setting-up-multiple-business-calendars).

### Zuordnen von Geschäftskalendern zu Benutzenden auf der Grundlage von Geschäftskalenderschlüsseln {#associate-business-calendars-with-users-based-on-business-calendar-keys}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Geschäftskalender“, und klicken Sie dann auf die Registerkarte „Zuordnung“.
1. Wählen Sie in der Liste „Das System verwendet“ den Eintrag „User Manager-Geschäftskalenderschlüssel-Auflösung“ aus.
1. Wählen Sie „User Manager-Geschäftskalenderschlüssel anzeigen“ aus. Eine Liste mit einem Satz eindeutiger Geschäftskalenderschlüssel, die in der Benutzerverwaltung definiert wurden, wird angezeigt.

   Bei lokalen und Hybrid-Domains zeigt die Liste die Werte an, die in User Management in das Feld „Geschäftskalenderschlüssel“ eingegeben wurden. Bei Unternehmens-Domains (LDAP) zeigt die Liste den eindeutigen Satz an, der von dem LDAP-Feld zurückgegeben wird (z. B. „country“), das in den LDAP-Domain-Einstellungen konfiguriert wurde.

   Wenn die Admins der Benutzerverwaltung keine Geschäftskalenderschlüssel definiert haben, ist die Liste leer.

1. Wählen Sie für jedes Element in der Liste der Benutzerverwaltungs-Geschäftskalenderschlüssel einen Kalender aus.
1. Klicken Sie auf Speichern.

### Zuordnen von Geschäftskalendern zu Benutzenden und Gruppen auf der Grundlage von Verzeichnisdienstgruppen {#associate-business-calendars-with-users-and-groups-based-on-directory-service-groups}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Geschäftskalender“, und klicken Sie dann auf die Registerkarte „Zuordnung“.
1. Wählen Sie in der Liste „Das System verwendet“ den Eintrag „vom Verzeichnis-Server definierte Gruppen“ aus.
1. Wählen Sie auf der Registerkarte „Zuordnung“ die Option „Verzeichnisdienstgruppen anzeigen“ aus. Eine Liste mit den Gruppen, die in der Benutzerverwaltung definiert wurden, wird angezeigt. (Siehe [Ordnereinstellungen](/help/forms/using/admin-help/configuring-directories.md#directory-settings).)

   >[!NOTE]
   >
   >Wenn Sie in Workbench einen Benutzerdienst für die Verwendung von Geschäftskalendern konfiguriert haben und der Dienst einer Gruppe zugewiesen ist, verwendet AEM Forms die hier angegebenen Gruppenzuordnungen, um den Kalender für die Gruppe aufzulösen. AEM Forms verwendet immer Gruppenzuordnungen für die Auflösung des Kalenders für Gruppen, selbst wenn Sie Geschäftskalenderschlüssel für die Auflösung des Kalenders für Benutzende verwenden. Wenn keine Gruppenzuordnung gefunden wird, wird der Standardgeschäftskalender verwendet.

1. Wählen Sie für jedes Element in der Liste „Verzeichnisdienstgruppe“ einen Kalender aus.
1. Klicken Sie auf Speichern.

## Exportieren und Importieren von Geschäftskalendern {#exporting-and-importing-business-calendars}

AEM Forms ermöglicht Ihnen das Exportieren und Importieren Ihrer Geschäftskalender als XML-Dateien. Mithilfe dieser Funktion können Sie Kalender aus einem Testsystem in ein Produktionssystem verschieben.

>[!NOTE]
>
>Diese Funktion exportiert und importiert alle definierten Geschäftskalender, einschließlich des von AEM Forms bereitgestellten Standardgeschäftskalenders. Ein importierter Geschäftskalender mit demselben Namen wie ein bereits vorhandener Kalender überschreibt den vorhandenen Kalender.

### Exportieren von Geschäftskalendern {#export-business-calendars}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Formular-Workflow“ > „Geschäftskalender“. 
1. Klicken Sie auf „Exportieren“ und speichern Sie die XML-Datei.

### Importieren von Geschäftskalendern {#import-business-calendars}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Formular-Workflow“ > „Geschäftskalender“. 
1. Wählen Sie Importieren.
1. Wählen Sie die XML-Datei aus, die die exportierten Geschäftskalender enthält, und klicken Sie auf „Öffnen“.

## Löschen eines Geschäftskalenders {#delete-a-business-calendar}

Alle Geschäftskalender, die in Ihrer Organisation nicht mehr benötigt werden, können entfernt werden. Wenn Sie einen Geschäftskalender löschen, der noch Benutzenden oder Gruppen zugeordnet ist, wird der Standardkalender verwendet.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Formular-Workflow“ > „Geschäftskalender“.
1. Wählen Sie den Kalender aus.
1. Klicken Sie auf Löschen.
