---
title: Konfigurieren von Geschäftskalendern
seo-title: Konfigurieren von Geschäftskalendern
description: Geschäftskalender definieren Geschäftstage und geschäftsfreie Tage für Ihre Organisation. Erfahren Sie, wie Sie die Geschäftskalender konfigurieren.
seo-description: Geschäftskalender definieren Geschäftstage und geschäftsfreie Tage für Ihre Organisation. Erfahren Sie, wie Sie die Geschäftskalender konfigurieren.
uuid: 0ba610b8-72a8-480c-8783-70d98cbe890a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 7a85e13d-4800-47c4-812a-5c6e2355298a
exl-id: 4282718a-41f1-411a-9cd7-8c470005107d
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1928'
ht-degree: 93%

---

# Konfigurieren von Geschäftskalendern {#configuring-business-calendars}

*Geschäftskalender* definieren Geschäftstage und geschäftsfreie Tage (z. B. gesetzliche Feiertage, Wochenenden und Betriebsferien) für Ihre Organisation. Bei Verwendung von Geschäftskalendern lässt AEM Forms geschäftsfreie Tage aus, wenn bestimmte Datumsberechnungen angestellt werden. In Workbench können Sie festlegen, ob Geschäftskalender für Benutzern zugeordnete Ereignisse wie z. B. Aufgabenerinnerungen, Termine und Eskalationen oder für nicht Benutzern zugeordnete Aktionen wie Timer-Ereignisse oder den Wait-Dienst verwendet werden sollen.

Eine Aufgabenerinnerung kann beispielsweise so konfiguriert sein, dass sie drei Geschäftstage nach der Zuweisung der Aufgabe zu einem Benutzer angezeigt wird. Die Aufgabe wird am Donnerstag zugewiesen. Die folgenden drei Tage sind nun aber keine Geschäftstage, weil der Freitag ein Feiertag und die nächsten zwei Tage Wochenendtage sind. Aus diesem Grund wird die Erinnerung am Mittwoch der nächsten Woche gesendet.

>[!NOTE]
>
>Beim Berechnen von Daten und Uhrzeiten unter Verwendung von Geschäftskalendern verwendet AEM Forms das Datum und die Uhrzeit des Servers, auf dem es ausgeführt wird, und führt keine Anpassung aufgrund von Zeitzonendifferenzen durch. Wird beispielsweise die Anzeige einer Aufgabenerinnerung für 10:00 Uhr vormittags auf einem Server geplant, der in London ausgeführt wird, während sich der Benutzer, der die Erinnerung erhält, aber in New York City befindet, erhält dieser die Erinnerung um 5:00 Uhr morgens Ortszeit.

## Standardgeschäftskalender verwenden {#using-the-default-business-calendar}

AEM Forms bietet einen Standardgeschäftskalender (namens *Integrierter Kalender*), in dem Samstage und Sonntage als geschäftsfreie Tage festgelegt sind. Wenn für alle Benutzer in Ihrer Organisation dieselben geschäftsfreien Tage gelten, können Sie den Standardgeschäftskalender dementsprechend aktualisieren. Wird nur der Standardgeschäftskalender verwendet, müssen in User Management keine Geschäftskalender aktiviert oder Zuordnungen bereitgestellt werden. Sind keine anderen Geschäftskalender definiert, verwendet AEM Forms den Standardgeschäftskalender.

## Mehrere Geschäftskalender einrichten  {#setting-up-multiple-business-calendars}

Wenn für einige der Benutzer in Ihrer Organisation abweichende geschäftsfreie Tage gelten, können Sie mehrere Geschäftskalender definieren und Zuordnungen konfigurieren, die die Auflösung eines Geschäftskalenders für einen Benutzer zur Laufzeit erlauben.

### Mehrere Geschäftskalender definieren  {#define-multiple-business-calendars}

1. Entscheiden Sie, wie Benutzern geeignete Geschäftskalender zugewiesen werden sollen. Es gibt zwei Methoden, um einem Benutzer einen Geschäftskalender zuzuordnen.

   **Gruppenmitgliedschaft:** Sie können einem Benutzer einen Geschäftskalender auf Grundlage der Gruppenmitgliedschaft des Benutzers zuweisen. In diesem Fall verwenden alle Benutzer der Gruppe denselben Geschäftskalender.

   Ist ein Benutzer Mitglied in zwei verschiedenen Gruppen, die unterschiedlichen Geschäftskalendern zugeordnet sind, verwendet AEM Forms den ersten in den Suchergebnissen gefundenen Kalender. In diesem Fall sollten Sie in Betracht ziehen, Benutzer anhand von Geschäftskalenderschlüsseln den Geschäftskalendern zuzuordnen.

   **Geschäftskalenderschlüssel:** Sie können einem Benutzer einen Geschäftskalender auf der Grundlage eines Geschäftskalenderschlüssels zuweisen, was einer in User Management festgelegten Einstellung entspricht. Anschließend ordnen Sie den Geschäftskalenderschlüssel einem Geschäftskalender im Arbeitsablauf für Formulare zu. 

    Die Methode zum Zuweisen von Geschäftskalenderschlüsseln zu Benutzern ist davon abhängig, ob eine Unternehmens-, eine lokale oder eine Hybriddomäne verwendet wird. Detaillierte Informationen zum Einrichten von Domänen finden Sie unter [Domänen hinzufügen](/help/forms/using/admin-help/adding-domains.md#adding-domains). 

    Wenn Sie eine lokale oder Hybriddomäne verwenden, werden Informationen zu Benutzern nur in der User Management-Datenbank gespeichert. Geben Sie zur Festlegung des Geschäftskalenderschlüssels für diese Benutzer eine Zeichenfolge in das Feld „Geschäftskalenderschlüssel“ ein, wenn Sie einen Benutzer in User Management hinzufügen oder bearbeiten. (Siehe [Benutzer hinzufügen und konfigurieren](/help/forms/using/admin-help/adding-configuring-users.md#adding-and-configuring-users).) Anschließend ordnen Sie die Geschäftskalenderschlüssel (die Zeichenfolgen) den Geschäftskalendern im Arbeitsablauf für Formulare zu. (Siehe [Benutzer und Gruppen einem Geschäftskalender zuordnen](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar).) 

    Wenn Sie eine Unternehmensdomäne verwenden, befinden sich Informationen zu Benutzern in einem Speichersystem von Drittanbietern wie etwa einem LDAP-Ordner, der von User Management mit der User Management-Datenbank synchronisiert wird. Dies ermöglicht Ihnen die Zuordnung eines Geschäftskalenderschlüssels zu einem Feld im LDAP-Ordner. Wenn beispielsweise jeder Benutzerdatensatz in Ihrem Ordner ein Feld „country“ enthält und Sie Geschäftskalender auf Grundlage des Landes zuweisen möchten, in dem sich der Benutzer befindet, geben Sie den Feldnamen „country“ im Feld „Geschäftskalenderschlüssel“ an, wenn Sie die Benutzereinstellungen für den Ordner angeben. (Siehe [Ordner konfigurieren](/help/forms/using/admin-help/configuring-directories.md#configuring-directories).) Anschließend können Sie die Geschäftskalenderschlüssel (die für das Feld „country“ im LDAP-Ordner definierten Werte) Geschäftskalendern im Arbeitsablauf für Formulare zuordnen. (Siehe [Benutzer und Gruppen einem Geschäftskalender zuordnen](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar).)

1. Definieren Sie im Arbeitsablauf für Formulare einen Kalender für jeden Satz von Benutzern, für die dieselben geschäftsfreien Tage gelten. (Siehe [Einen Geschäftskalender erstellen oder aktualisieren](configuring-business-calendars.md#create-or-update-a-business-calendar).)
1. Ordnen Sie im Arbeitsablauf für Formulare die Geschäftskalenderschlüssel oder Gruppenmitgliedschaften für jeden Kalender zu. (Siehe [Benutzer und Gruppen einem Geschäftskalender zuordnen](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar).)
1. Der Prozessentwickler wählt in Workbench aus, ob Geschäftskalender für Erinnerungen, Termine und Eskalationen verwendet werden. (Siehe [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63).)

   Wenn der Prozessentwickler Geschäftskalender verwendet, wählt AEM Forms den geeigneten Geschäftskalender dynamisch auf Grundlage der User Management-Einstellung und der in Administration Console definierten Geschäftskalenderzuordnungen aus. Sind keine Zuordnungen vorhanden, wird der Standardkalender verwendet.

   Wenn der Prozessentwickler keine Geschäftskalender verwendet, werden alle geschäftsfreien Tage bei der Datumsberechnung für das Ereignis als Geschäftstage behandelt. Ein Aufgabentermin kann beispielsweise so konfiguriert sein, dass er drei Tage nach der Zuweisung der Aufgabe zu einem Benutzer fällig wird. Die Aufgabe wird am Donnerstag zugewiesen. Der Aufgabentermin wird trotz des Wochenendes am Sonntag fällig.

## Einen Geschäftskalender erstellen oder aktualisieren  {#create-or-update-a-business-calendar}

Wenn in Ihrer Organisation verschiedene Benutzergruppen mit unterschiedlichen geschäftsfreien Tagen vorhanden sind, können Sie mehrere Geschäftskalender definieren. Sie können auch an vorhandenen Kalendern Änderungen vornehmen, einschließlich des von AEM Forms bereitgestellten integrierten Standardkalenders.

>[!NOTE]
>
>Wenn Sie keinen Geschäftskalender erstellen, wird der Standardkalender verwendet.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Geschäftskalender“.
1. Um einen neuen Geschäftskalender hinzuzufügen, klicken Sie auf ![bus_cal_plus](assets/bus_cal_plus.png). In der Dropdown-Liste wird der Text „*Neuer Kalender*“ angezeigt. Markieren Sie den Text und geben Sie einen anderen Namen für Ihren Kalender ein.

   Wählen Sie zum Bearbeiten eines vorhandenen Geschäftskalenders diesen aus der Dropdown-Liste aus.

1. Wählen Sie unter „Geschäftsfreier Standardtag“ alle geschäftsfreien Wochentage aus, wie z. B. Wochenenden.
1. [] Optional: Wählen Sie Geschäftszeiten verwenden aus und geben Sie die Start- und Endzeiten für die Geschäftstage an.

   Wenn Sie diese Option wählen, wird ein Ereignis, das vor dem angegebenen Zeitraum eintritt, an den Anfang des Zeitraums verschoben, und ein Ereignis, das nach dem Zeitraum eintritt, wird an die Anfangszeit des nächsten Geschäftstages verschoben.

   Nehmen Sie beispielsweise eine Situation an, in der einem Benutzer eine Aufgabe um 2:00 Uhr morgens an einem Dienstag zugewiesen wird. Die Erinnerung für diese Aufgabe wird dabei auf zwei Geschäftstage festgelegt. Ohne Geschäftszeiten wird die Erinnerung am Donnerstag um 2:00 Uhr morgens ausgeführt. Sind die Geschäftszeiten auf 8:00 Uhr bis 17:00 Uhr festgelegt, wird die Erinnerung auf Donnerstag 8:00 Uhr Morgens verlegt. Ohne Geschäftszeiten erfolgt eine Erinnerung, wenn das Erinnerungsereignis am Dienstag um 6:00 Uhr morgens erstellt wurde, nach der Geschäftszeit am Donnerstag. Sind die Geschäftszeiten auf 8:00 Uhr bis 17:00 Uhr festgelegt, wird die Erinnerung am Freitag um 8:00 Uhr Morgens ausgeführt.

1. Doppelklicken Sie im Kalender auf der linken Seite auf alle weiteren geschäftsfreien Tage, wie z. B. Feiertage. Tage, die in der Vergangenheit liegen, können nicht ausgewählt werden. Die von Ihnen ausgewählten geschäftsfreien Tage werden in einer Liste auf der rechten Seite angezeigt, wobei das Datum zweimal pro Zeile angezeigt wird. Wählen Sie das linke Datum aus, um einen Namen oder eine Beschreibung für den geschäftsfreien Tag einzugeben.

   Um einen geschäftsfreien Tag aus der Liste zu entfernen, klicken Sie neben dem Tag auf ![bus_cal_trash](assets/bus_cal_trash.png) .

1. [] OptionalWenn dieser Kalender der Standardkalender sein soll, wählen Sie &quot;Standardkalender&quot;. Der Standardkalender wird verwendet, wenn keine anderen Kalenderzuordnungen für Benutzern zugeordnete Ereignisse vorhanden sind oder wenn kein Geschäftskalender für das Timer-Ereignis oder den Wait-Dienst festgelegt ist. Der Standardkalender kann nicht gelöscht werden.
1. Wenn die Definition der geschäftsfreien Tage fertig gestellt ist, wählen Sie „Kalender aktiviert“, um den Kalender zu aktivieren, und klicken dann auf „Speichern“.

   Wenn Sie einen vorhandenen Kalender aktualisieren, wird die neue Version sofort gültig und wird für alle Geschäftskalenderberechnungen verwendet, einschließlich Aufgaben, die bereits ausgeführt werden.

   >[!NOTE]
   >
   >Wird der Kalender nicht aktiviert, wird der Standardkalender verwendet.

## Benutzer und Gruppen einem Geschäftskalender zuordnen  {#mapping-users-and-groups-to-a-business-calendar}

Es gibt zwei Methoden, um einem Benutzer einen Geschäftskalender zuzuordnen. Sie können Geschäftskalender Benutzern auf Grundlage eines Geschäftskalenderschlüssels zuweisen oder auf Basis der Ordnergruppe, der der jeweilige Benutzer angehört. Die von AEM Forms zu verwendende Methode wird auf der Registerkarte „Zuordnung“ festgelegt, wo auch die Geschäftskalenderschlüssel und Gruppen den Geschäftskalendern zugeordnet werden. Detaillierte Informationen zum Verknüpfen von Geschäftskalendern mit Benutzern finden Sie unter [Mehrere Geschäftskalender einrichten](configuring-business-calendars.md#setting-up-multiple-business-calendars).

### Benutzern Geschäftskalender auf Grundlage von Geschäftskalenderschlüsseln zuordnen  {#associate-business-calendars-with-users-based-on-business-calendar-keys}

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Geschäftskalender“, und klicken Sie dann auf die Registerkarte „Zuordnung“.
1. Wählen Sie in der Liste &quot;System Will Use&quot;die Option User Manager Business Calendar Key Resolution.
1. Wählen Sie „User Manager-Geschäftskalenderschlüssel anzeigen“. Eine Liste mit einem Satz eindeutiger Geschäftskalenderschlüssel, die in User Management definiert wurden, wird angezeigt.

   Bei lokalen und Hybriddomänen zeigt die Liste die Werte an, die in User Management in das Feld „Geschäftskalenderschlüssel“ eingegeben wurden. Bei Unternehmensdomänen (LDAP) zeigt die Liste den eindeutigen Satz an, der von dem LDAP-Feld zurückgegeben wird (z. B. „country“), das in den LDAP-Domäneneinstellungen konfiguriert wurde.

   Wenn der User Management-Administrator keine Geschäftskalenderschlüssel definiert hat, ist die Liste leer.

1. Wählen Sie für jedes Element in der Liste UM-Geschäftskalenderschlüssel einen Kalender aus.
1. Klicken Sie auf Speichern.

### Benutzern und Gruppen Geschäftskalender auf Grundlage von Ordnerdienstgruppen zuordnen  {#associate-business-calendars-with-users-and-groups-based-on-directory-service-groups}

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Geschäftskalender“, und klicken Sie dann auf die Registerkarte „Zuordnung“.
1. Wählen Sie in der Liste &quot;System Will Use&quot;die Option vom Verzeichnisserver definierte Gruppen aus.
1. Wählen Sie auf der Registerkarte „Zuordnung“ die Option „Verzeichnisdienstgruppen anzeigen“. Eine Liste mit den Gruppen, die in User Management definiert wurden, wird angezeigt. (Siehe [Ordnereinstellungen](/help/forms/using/admin-help/configuring-directories.md#directory-settings).)

   >[!NOTE]
   >
   >Wenn Sie in Workbench einen User-Dienst für die Verwendung von Geschäftskalendern konfiguriert haben und der Dienst einer Gruppe zugewiesen ist, verwendet AEM Forms die hier angegebenen Gruppenzuordnungen, um den Kalender für die Gruppe aufzulösen. AEM Forms verwendet immer Gruppenzuordnungen für die Auflösung des Kalenders für Gruppen, selbst wenn Sie Geschäftskalenderschlüssel für die Auflösung des Kalenders für Benutzer verwenden. Wenn keine Gruppenzuordnung gefunden wird, wird der Standardgeschäftskalender verwendet.

1. Wählen Sie für jedes Element in der Liste „Verzeichnisdienstgruppe“ einen Kalender aus.
1. Klicken Sie auf Speichern.

## Geschäftskalender exportieren und importieren  {#exporting-and-importing-business-calendars}

AEM Forms ermöglicht Ihnen das Exportieren und Importieren Ihrer Geschäftskalender als XML-Dateien. Mithilfe dieser Funktion können Sie Kalender aus einem Testsystem in ein Produktionssystem verschieben.

>[!NOTE]
>
>Diese Funktion exportiert und importiert alle definierten Geschäftskalender, einschließlich des von AEM Forms bereitgestellten Standardgeschäftskalenders. Ein importierter Geschäftskalender mit demselben Namen wie ein bereits vorhandener Kalender überschreibt den vorhandenen Kalender.

### Geschäftskalender exportieren  {#export-business-calendars}

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Geschäftskalender“.
1. Klicken Sie auf „Exportieren“ und speichern Sie die XML-Datei.

### Geschäftskalender importieren  {#import-business-calendars}

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Geschäftskalender“.
1. Wählen Sie Importieren.
1. Wählen Sie die XML-Datei aus, die die exportierten Geschäftskalender enthält, und klicken Sie auf „Öffnen“.

## Einen Geschäftskalender löschen  {#delete-a-business-calendar}

Alle Geschäftskalender, die in Ihrer Organisation nicht mehr benötigt werden, können entfernt werden. Wird ein Geschäftskalender gelöscht, der noch Benutzern oder Gruppen zugeordnet ist, wird der Standardkalender verwendet.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Geschäftskalender“.
1. Wählen Sie den Kalender aus.
1. Klicken Sie auf Löschen.
