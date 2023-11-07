---
title: Konfigurieren von Geschäftskalendern
seo-title: Configuring Business Calendars
description: Geschäftskalender definieren Geschäftstage und geschäftsfreie Tage für Ihre Organisation. Erfahren Sie, wie Sie die Geschäftskalender konfigurieren.
seo-description: Business calendars define business and non-business days for your organization. Learn how to configure the business calendars.
uuid: 0ba610b8-72a8-480c-8783-70d98cbe890a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 7a85e13d-4800-47c4-812a-5c6e2355298a
exl-id: 4282718a-41f1-411a-9cd7-8c470005107d
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '1901'
ht-degree: 16%

---

# Konfigurieren von Geschäftskalendern {#configuring-business-calendars}

*Geschäftskalender* Definieren Sie Geschäftstage und geschäftsfreie Tage (z. B. gesetzliche Feiertage, Wochenenden und Betriebsferien) für Ihre Organisation. Bei Verwendung von Geschäftskalendern überspringen AEM Formulare geschäftsfreie Tage bei der Durchführung bestimmter Datumsberechnungen. In Workbench können Sie festlegen, ob Geschäftskalender für benutzerverknüpfte Ereignisse wie Aufgabenerinnerungen, Termine und Eskalationen oder für Aktionen, die Benutzern nicht zugeordnet sind, wie z. B. Timer-Ereignisse und Wait-Dienst, verwendet werden sollen.

Beispielsweise ist eine Aufgabenerinnerung so konfiguriert, dass sie drei Werktage nach der Zuweisung der Aufgabe an einen Benutzer erfolgt. Die Aufgabe wird am Donnerstag zugewiesen. Die folgenden drei Tage sind jedoch keine Geschäftstage, da der Freitag ein Nationalfeiertag ist und die nächsten zwei Tage Wochenendtage sind. Die Erinnerung wird daher am Mittwoch der nächsten Woche versandt.

>[!NOTE]
>
>Bei der Berechnung von Daten und Uhrzeiten mithilfe von Geschäftskalendern verwenden AEM Formulare das Datum und die Uhrzeit des Servers, auf dem sie ausgeführt werden, und passen nicht den Unterschied zwischen Zeitzonen an. Wenn beispielsweise eine Aufgabenerinnerung um 10:00 Uhr auf einem Server geplant ist, der in London ausgeführt wird, sich der Benutzer, der die Erinnerung erhält, jedoch in New York City befindet, erhält der Benutzer die Erinnerung um 5:00 Uhr Ortszeit.

## Standardgeschäftskalender verwenden {#using-the-default-business-calendar}

AEM Forms bietet einen Standardgeschäftskalender (namens *Integrierter Kalender*), in dem Samstage und Sonntage als geschäftsfreie Tage festgelegt sind. Wenn alle Benutzer in Ihrer Organisation dieselben geschäftsfreien Tage haben, können Sie den Standardgeschäftskalender entsprechend Ihrer Organisation aktualisieren. Wenn Sie nur den Standardgeschäftskalender verwenden, müssen Sie keine Geschäftskalender in User Management aktivieren oder Zuordnungen bereitstellen. Wenn keine anderen Geschäftskalender definiert sind, verwenden AEM Formulare den Standardgeschäftskalender.

## Einrichten mehrerer Geschäftskalender {#setting-up-multiple-business-calendars}

Wenn einige Benutzer in Ihrer Organisation unterschiedliche geschäftsfreie Tage haben, können Sie mehrere Geschäftskalender definieren und Zuordnungen konfigurieren, die die Auflösung eines Geschäftskalenders für einen Benutzer zur Laufzeit ermöglichen.

### Mehrere Geschäftskalender definieren {#define-multiple-business-calendars}

1. Entscheiden Sie, wie Sie den entsprechenden Geschäftskalender mit einem Benutzer verknüpfen. Es gibt zwei Möglichkeiten, einen Geschäftskalender mit einem Benutzer zu verknüpfen:

   **Gruppenmitgliedschaft**: Einem Benutzer kann ein Geschäftskalender auf Basis seiner Gruppenmitgliedschaft zugewiesen werden. In diesem Fall verwendet jeder Benutzer der Gruppe denselben Geschäftskalender.

   Wenn ein Benutzer Mitglied zweier verschiedener Gruppen ist und diese Gruppen zwei verschiedenen Geschäftskalendern zugeordnet sind, verwenden AEM Formulare den ersten Kalender, den er in den Suchergebnissen findet. In diesem Fall sollten Sie die Verwendung von Geschäftskalenderschlüsseln erwägen, um Benutzer mit Geschäftskalendern zu verknüpfen.

   **Geschäftskalenderschlüssel**: Einem Benutzer kann ein Geschäftskalender auf Basis eines Geschäftskalenderschlüssels zugewiesen werden, wobei es sich um eine Einstellung handelt, die in User Management festgelegt wird. Anschließend ordnen Sie den Geschäftskalenderschlüssel einem Geschäftskalender im Arbeitsablauf für Formulare zu.

    Die Methode zum Zuweisen von Geschäftskalenderschlüsseln zu Benutzern ist davon abhängig, ob eine Unternehmens-, eine lokale oder eine Hybrid-Domain verwendet wird. Detaillierte Informationen zum Einrichten von Domains finden Sie unter [Hinzufügen von Domains](/help/forms/using/admin-help/adding-domains.md#adding-domains). 

    Wenn Sie eine lokale oder Hybrid-Domain verwenden, werden Informationen zu Benutzern nur in der User Management-Datenbank gespeichert. Um den Geschäftskalenderschlüssel für diese Benutzer festzulegen, geben Sie beim Hinzufügen oder Bearbeiten eines Benutzers in User Management im Feld Geschäftskalenderschlüssel eine Zeichenfolge ein. (Siehe [Benutzer hinzufügen und konfigurieren](/help/forms/using/admin-help/adding-configuring-users.md#adding-and-configuring-users). Anschließend ordnen Sie die Geschäftskalenderschlüssel (die Zeichenfolgen) den Geschäftskalendern im Arbeitsablauf für Formulare zu. (Siehe [Benutzer und Gruppen einem Geschäftskalender zuordnen](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar).

    Wenn Sie eine Unternehmens-Domain verwenden, befinden sich Informationen zu Benutzern in einem Speichersystem von Drittanbietern wie etwa einem LDAP-Ordner, der von User Management mit der User Management-Datenbank synchronisiert wird. Auf diese Weise können Sie einen Geschäftskalenderschlüssel einem Feld im LDAP-Ordner zuordnen. Wenn beispielsweise jeder Benutzerdatensatz in Ihrem Verzeichnis das Feld &quot;country&quot;enthält und Sie Geschäftskalender basierend auf dem Land zuweisen möchten, in dem sich der Benutzer befindet, geben Sie den Feldnamen &quot;country&quot;im Feld Geschäftskalenderschlüssel an, wenn Sie die Benutzereinstellungen für den Ordner angeben. (Siehe [Ordner konfigurieren](/help/forms/using/admin-help/configuring-directories.md#configuring-directories). Anschließend können Sie die Geschäftskalenderschlüssel (die für das Feld &quot;country&quot;im LDAP-Ordner definierten Werte) Geschäftskalendern im Arbeitsablauf für Formulare zuordnen. (Siehe [Benutzer und Gruppen einem Geschäftskalender zuordnen](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar).

1. Definieren Sie im Arbeitsablauf für Formulare einen Kalender für jeden Satz von Benutzern, die dieselben geschäftsfreien Tage nutzen. (Siehe [Einen Geschäftskalender erstellen oder aktualisieren](configuring-business-calendars.md#create-or-update-a-business-calendar).
1. Ordnen Sie im Arbeitsablauf für Formulare die Geschäftskalenderschlüssel oder Gruppenmitgliedschaften für jeden Kalender zu. (Siehe [Benutzer und Gruppen einem Geschäftskalender zuordnen](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar).
1. In Workbench entscheidet der Prozessentwickler, ob er Geschäftskalender für Erinnerungen, Termine und Eskalationen verwendet. (Siehe [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63_de).

   Wenn der Prozessentwickler Geschäftskalender verwendet, wählen AEM Formulare den entsprechenden Geschäftskalender dynamisch anhand der User Management-Einstellung und der in Administration Console definierten Geschäftskalenderzuordnungen aus. Wenn keine Zuordnungen vorhanden sind, wird der Standardkalender verwendet.

   Wenn der Prozessentwickler keine Geschäftskalender verwendet, behandelt die Datumsberechnung für das Ereignis jeden Tag als Geschäftstag. Beispielsweise wird ein Aufgabentermin so konfiguriert, dass er drei Tage nach der Zuweisung der Aufgabe an einen Benutzer eintritt. Die Aufgabe wird am Donnerstag zugewiesen. Die Aufgabentermin findet am Sonntag statt, obwohl es sich um ein Wochenende handelt.

## Einen Geschäftskalender erstellen oder aktualisieren {#create-or-update-a-business-calendar}

Wenn Ihr Unternehmen verschiedene Benutzergruppen mit unterschiedlichen geschäftsfreien Tagen enthält, können Sie mehrere Geschäftskalender definieren. Sie können auch vorhandene Kalender ändern, einschließlich des integrierten Standardkalenders, der mit AEM Formularen bereitgestellt wird.

>[!NOTE]
>
>Wenn Sie keinen Geschäftskalender erstellen, wird der Standardkalender verwendet.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Forms-Workflow&quot;> &quot;Geschäftskalender&quot;.
1. Um einen neuen Geschäftskalender hinzuzufügen, klicken Sie auf ![bus_cal_plus](assets/bus_cal_plus.png). Der Text *Neuer Kalender* in der Dropdown-Liste angezeigt. Wählen Sie den Text aus und geben Sie einen anderen Namen für Ihren Kalender ein.

   Um einen vorhandenen Geschäftskalender zu bearbeiten, wählen Sie ihn aus der Dropdownliste aus.

1. Wählen Sie unter &quot;Standardgeschäftsfreie Tage&quot;alle geschäftsfreien Wochentage aus, z. B. Wochenenden.
1. [Optional] Wählen Sie „Geschäftszeiten verwenden“ und geben Sie die Anfangs- und Endzeiten für die Geschäftstage an.

   Wenn Sie diese Option auswählen, wird ein Ereignis, das vor dem angegebenen Zeitraum eintritt, an den Anfang des Zeitraums verschoben und ein Ereignis, das nach dem Zeitraum eintritt, wird an die Startzeit des nächsten Geschäftstags verschoben.

   Betrachten Sie beispielsweise eine Situation, in der einem Benutzer am Dienstag um 2:00 Uhr eine Aufgabe zugewiesen wird und die Erinnerung für diese Aufgabe auf zwei Geschäftstage festgelegt ist. Ohne Geschäftszeiten erfolgt die Erinnerung am Donnerstag um 2:00 Uhr. Wenn die Geschäftszeiten auf 8:00 Uhr bis 17:00 Uhr festgelegt sind, wird die Erinnerung am Donnerstag auf 8:00 Uhr morgens gesendet. Ohne Geschäftszeiten würde die Erinnerung nach den Geschäftszeiten am Donnerstag, wenn am Dienstag um 18:00 Uhr ein Erinnerungsereignis erstellt wurde. Wenn die Geschäftszeiten auf 8:00 Uhr bis 17:00 Uhr festgelegt sind, wird die Erinnerung am Freitag um 8:00 Uhr morgens ausgeführt.

1. Doppelklicken Sie im Kalender auf der linken Seite auf alle anderen geschäftsfreien Tage, z. B. Feiertage. Sie können keine Tage in der Vergangenheit auswählen. Die von Ihnen ausgewählten geschäftsfreien Tage werden in einer Liste auf der rechten Seite angezeigt, wobei das Datum zweimal in einer Zeile angezeigt wird. Wählen Sie links das Datum aus, um einen Namen oder eine Beschreibung für den geschäftsfreien Tag einzugeben.

   Um einen arbeitsfreien Tag aus der Liste zu entfernen, klicken Sie auf ![Bus_cal_trash](assets/bus_cal_trash.png) neben dem Tag.

1. [Optional] Wenn dieser Kalender der Standardkalender sein soll, wählen Sie „Standardkalender“. Der Standardkalender wird verwendet, wenn keine andere Kalenderzuordnung für benutzerverknüpfte Ereignisse vorhanden ist oder für das Timer-Ereignis oder den Wait-Dienst kein Geschäftskalender angegeben ist. Der Standardkalender kann nicht gelöscht werden.
1. Wenn Sie mit der Definition der geschäftsfreien Tage fertig sind, wählen Sie &quot;Kalender aktiviert&quot;, um den Kalender zu aktivieren, und klicken Sie dann auf &quot;Speichern&quot;.

   Wenn Sie einen vorhandenen Kalender aktualisieren, wird die neue Version sofort wirksam und für alle Geschäftskalenderberechnungen verwendet, auch für bereits ausgeführte Aufgaben.

   >[!NOTE]
   >
   >Wenn Sie den Kalender nicht aktivieren, wird der Standardkalender verwendet.

## Benutzer und Gruppen einem Geschäftskalender zuordnen {#mapping-users-and-groups-to-a-business-calendar}

Es gibt zwei Methoden, mit denen Sie einem Benutzer einen Geschäftskalender zuordnen können. Sie können Benutzern Geschäftskalender basierend auf einem Geschäftskalenderschlüssel oder auf der Ordnergruppe zuweisen, zu der der Benutzer gehört. Auf der Registerkarte Zuordnung können Sie die Methode angeben, die AEM Formulare verwenden soll, und auch die Geschäftskalenderschlüssel und -gruppen Geschäftskalendern zuordnen. Weitere Informationen zum Verknüpfen von Geschäftskalenderschlüsseln mit Benutzern finden Sie unter [Einrichten mehrerer Geschäftskalender](configuring-business-calendars.md#setting-up-multiple-business-calendars).

### Geschäftskalender Benutzern basierend auf Geschäftskalenderschlüsseln zuordnen {#associate-business-calendars-with-users-based-on-business-calendar-keys}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Arbeitsablauf für Formulare&quot;> &quot;Geschäftskalender&quot;und dann auf die Registerkarte &quot;Zuordnung&quot;.
1. Wählen Sie in der Liste „Das System verwendet“ den Eintrag „User Manager-Geschäftskalenderschlüssel-Auflösung“ aus.
1. Wählen Sie &quot;User Manager-Geschäftskalenderschlüssel anzeigen&quot;. Es wird eine Liste mit einem eindeutigen Satz von Geschäftskalenderschlüsseln angezeigt, die in User Management definiert wurden.

   Bei lokalen und Hybrid-Domains zeigt die Liste die Werte an, die in User Management in das Feld „Geschäftskalenderschlüssel“ eingegeben wurden. Bei Unternehmens-Domains (LDAP) zeigt die Liste den eindeutigen Satz an, der von dem LDAP-Feld zurückgegeben wird (z. B. „country“), das in den LDAP-Domain-Einstellungen konfiguriert wurde.

   Wenn der User Management-Administrator keine Geschäftskalenderschlüssel definiert hat, ist die Liste leer.

1. Wählen Sie für jedes Element in der Liste UM-Geschäftskalenderschlüssel einen Kalender aus.
1. Klicken Sie auf Speichern.

### Verknüpfen von Geschäftskalendern mit Benutzern und Gruppen basierend auf Ordnerdienstgruppen {#associate-business-calendars-with-users-and-groups-based-on-directory-service-groups}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Arbeitsablauf für Formulare&quot;> &quot;Geschäftskalender&quot;und dann auf die Registerkarte &quot;Zuordnung&quot;.
1. Wählen Sie in der Liste „Das System verwendet“ den Eintrag „vom Verzeichnis-Server definierte Gruppen“ aus.
1. Wählen Sie auf der Registerkarte Zuordnung die Option Verzeichnisdienstgruppen anzeigen aus. Es wird eine Liste mit den in User Management definierten Gruppen angezeigt. (Siehe [Ordnereinstellungen](/help/forms/using/admin-help/configuring-directories.md#directory-settings).

   >[!NOTE]
   >
   >Wenn Sie in Workbench einen User-Dienst für die Verwendung von Geschäftskalendern konfiguriert haben und der Dienst einer Gruppe zugewiesen ist, verwendet AEM Formulare die hier angegebenen Gruppenzuordnungen, um den Kalender für die Gruppe aufzulösen. AEM Formulare verwenden immer Gruppenzuordnungen, um den Kalender für Gruppen aufzulösen, auch wenn Sie Geschäftskalenderschlüssel verwenden, um den Kalender für Benutzer aufzulösen. Wenn keine Gruppenzuordnung gefunden wird, wird der Standardgeschäftskalender verwendet.

1. Wählen Sie für jedes Element in der Liste &quot;Verzeichnisdienstgruppe&quot;einen Kalender aus.
1. Klicken Sie auf Speichern.

## Geschäftskalender exportieren und importieren {#exporting-and-importing-business-calendars}

Mit AEM Formularen können Sie Ihre Geschäftskalender als XML-Dateien exportieren und importieren. Mit dieser Funktion können Sie Kalender von einem Staging-System in ein Produktionssystem verschieben.

>[!NOTE]
>
>Diese Funktion exportiert und importiert alle definierten Geschäftskalender, einschließlich des von AEM Forms bereitgestellten Standardgeschäftskalenders. Ein importierter Geschäftskalender mit demselben Namen wie ein vorhandener Kalender überschreibt den vorhandenen Kalender.

### Geschäftskalender exportieren {#export-business-calendars}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Arbeitsablauf für Formulare&quot;> &quot;Geschäftskalender&quot;.
1. Klicken Sie auf Exportieren und speichern Sie die XML-Datei.

### Geschäftskalender importieren {#import-business-calendars}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Arbeitsablauf für Formulare&quot;> &quot;Geschäftskalender&quot;.
1. Wählen Sie Importieren.
1. Wählen Sie die XML-Datei aus, die die exportierten Geschäftskalender enthält, und klicken Sie auf &quot;Öffnen&quot;.

## Einen Geschäftskalender löschen {#delete-a-business-calendar}

Sie können alle Geschäftskalender entfernen, die Ihr Unternehmen nicht mehr benötigt. Wenn Sie einen Geschäftskalender löschen, der noch Benutzern und Gruppen zugeordnet ist, wird der Standardkalender verwendet.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Forms-Workflow&quot;> &quot;Geschäftskalender&quot;.
1. Wählen Sie den Kalender aus.
1. Klicken Sie auf Löschen.
