---
title: Richtliniensätzen erstellen und verwalten
seo-title: Richtliniensätzen erstellen und verwalten
description: Richtliniensätze dienen zum Gruppieren von Richtlinien mit einem gemeinsamen Zweck. Sie können Richtlinien in einem Richtliniensatz erstellen, bearbeiten und löschen.
seo-description: Richtliniensätze dienen zum Gruppieren von Richtlinien mit einem gemeinsamen Zweck. Sie können Richtlinien in einem Richtliniensatz erstellen, bearbeiten und löschen.
uuid: 11faf67c-b9b7-4394-8672-d43cace131ad
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a4fb1a11-8fe3-4092-a036-1c079aea1250
feature: Dokumentensicherheit
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1326'
ht-degree: 99%

---


# Richtliniensätzen erstellen und verwalten {#creating-and-managing-policy-sets}

Richtliniensätze dienen zum Gruppieren von Richtlinien mit einem gemeinsamen Zweck. Richtliniensätze können einer Untermenge der Benutzer im System zur Verfügung gestellt werden.

Jedem Richtliniensatz ist mindestens ein Richtliniensatzkoordinator zugeordnet. Der *Richtliniensatzkoordinator* ist ein Administrator oder Benutzer mit zusätzlichen Berechtigungen. Der Richtliniensatzkoordinator ist in der Regel ein Spezialist im Unternehmen, der die Richtlinien in einem Richtliniensatz am besten verwalten kann.

Richtliniensatzkoordinatoren können diese Aufgaben ausführen:

* Neue Richtlinien erstellen
* Richtlinien in einem Richtliniensatz bearbeiten und löschen
* Richtliniensatzeinstellungen bearbeiten
* Koordinatoren für den Richtliniensatz hinzufügen und entfernen
* Richtlinien- und Dokumentereignisse für die Richtlinien oder Dokumente im Richtliniensatz anzeigen
* Den Zugriff auf Dokumente aufheben
* Richtlinien für das Dokument wechseln

Richtliniensätze werden auf den Document Security-Administrationswebseiten von Hauptbenutzern und Richtliniensatzkoordinatoren erstellt und gelöscht, denen die entsprechenden Berechtigungen erteilt wurden.

Beim Löschen eines Richtliniensatzes können Richtlinien, die Bestandteil des Satzes waren, nicht mehr auf neue Dokumente angewendet werden. Sie können jedoch die Richtlinieninformationen für Richtlinien, die noch in Benutzung sind, sowohl in Administration Console als auch auf den Webseiten für Endbenutzer anzeigen. Sie können die Richtlinieninformationen über die Seite „Dokumentdetails“ jedes von dieser Richtlinie geschützten Dokuments anzeigen. Richtlinien, die noch verwendet werden, können bearbeitet werden.

Der Hauptbenutzer oder Richtliniensatzkoordinator muss für jeden Richtliniensatz in User Management erstellte Domänen auswählen und zum sichtbaren Benutzer bzw. zur sichtbaren Gruppe hinzufügen. Diese Liste wird dem Richtliniensatzkoordinator angezeigt und dient zum Eingrenzen der Domänen, die der Richtliniensatzkoordinator beim Auswählen von Benutzern durchsuchen kann, die Richtlinien hinzugefügt werden sollen.

Beim Erstellen von Richtliniensätzen weisen Sie Benutzern die Rolle des Dokumentherausgebers zu. Der *Dokumentherausgeber* ist der Benutzer, der das Dokument mit einer Richtlinie schützt. Dieser Benutzer wird stets standardmäßig in eine Richtlinie einbezogen und hat Vollzugriffsrechte, so auch zum Sperren des Dokumentzugriffs oder Wechseln der Richtlinie. Administratoren können jedoch die Zugriffsrechte des Dokumentherausgebers für freigegebene Richtlinien ändern. Beispielsweise kann der Administrator dem Dokumentherausgeber die Rechte zum Sperren des Dokumentzugriffs oder Wechseln der Richtlinie entziehen. Wenn ein Administrator die Richtlinie wechselt, die mit dem Dokument verknüpft ist, wird der Herausgeber-Name auf dem Namen des Eigentümers der Richtlinie aktualisiert, die zuletzt auf das Dokument angewendet wurde.

Bei der Installation von Document Security wird standardmäßig ein so genannter *globaler Richtliniensatz* erstellt. Dieser Richtliniensatz wird von dem Administrator, der die Software installiert hat, oder dem für diesen Richtliniensatz festgelegten Richtliniensatzkoordinator verwaltet.

## Einen Richtliniensatz erstellen {#create-a-policy-set}

Der Richtliniensatz „Global“ ist der einzige Standardrichtliniensatz, der bei der Installation erstellt wird. Sie können weitere Richtliniensätze erstellen und dabei Richtlinien, Benutzer, Richtliniensatzkoordinatoren und Dokumentherausgeber hinzufügen. Nach Erstellen eines Richtliniensatzes können Sie Richtlinien im Satz erstellen.

Klicken Sie bei der Richtliniensatzerstellung auf die Schaltfläche „Zurück“, um zum vorherigen Bildschirm zurückzukehren. Um den Richtliniensatz zu speichern, klicken Sie zu einem beliebigen Zeitpunkt auf die Schaltfläche „Speichern“.

1. Klicken Sie auf der Document Security-Seite auf „Richtlinien“, auf die Registerkarte „Richtliniensätze“ und anschließend auf „Neu“.
1. Geben Sie in das Feld „Name“ einen Namen für den Richtliniensatz und optional in das Feld „Beschreibung“ eine Beschreibung ein. Klicken Sie danach auf „Weiter“. Der Name darf keinen Doppelpunkt **:** enthalten.

   >[!NOTE]
   >
   >Sie können einen Richtliniensatznamen erstellen, der erweiterte Zeichen enthält. Bei einem Vergleich zwischen zwei derartigen Zeichenfolgen werden jedoch Zeichen mit und ohne Akzentzeichen, wie z. B. „e“ und „é“, als identisch bewertet. Beim Erstellen eines Richtliniensatzes wird ein Vergleich durchgeführt, um zu überprüfen, ob bereits ein Richtliniensatz mit demselben Namen vorhanden ist. Der Vergleich kann nicht zwischen Namen unterscheiden, die sich nur durch Akzentzeichen unterscheiden. Es wird angenommen, dass der Richtliniensatz bereits zur Datenbank hinzugefügt wurde, sodass der neue nicht hinzugefügt wird.

1. (Optional) Um die Domänen festzulegen, die Herausgebern von Dokumenten beim Hinzufügen von Benutzern zu einer Richtlinie angezeigt werden, klicken Sie auf „Domänen hinzufügen“, wählen Sie anschließend die Domänen aus, die durchsuchbar sein sollen, klicken Sie auf „Hinzufügen“ und danach auf „OK“.
1. Klicken Sie auf der Seite „Benutzer und Gruppen hinzufügen“ auf „Weiter“.
1. (Optional) Um einen Richtliniensatzkoordinator hinzuzufügen, klicken Sie auf „Benutzer und Gruppen hinzufügen“ (Schritt 3 von 4) und führen Sie die folgenden Schritte aus:

   * Geben Sie in das Feld „Suchen“ den Namen oder die E-Mail-Adresse ein.
   * Wählen Sie in der Liste „Verwendet“ die passende Option aus.
   * Wählen Sie in der Liste „Typ“ die Option „Benutzer“ und in der Liste „In“ eine zu durchsuchende Domäne aus.
   * Wählen Sie in der Liste „Anzeigen“ die Anzahl der pro Seite anzuzeigenden Suchergebnisse aus und klicken Sie auf „Suchen“.
   * Aktivieren Sie das Kontrollkästchen des Benutzers oder der Gruppe, der/die hinzugefügt werden soll, und klicken Sie auf „Weiter“.
   * Wählen Sie die Berechtigungen des Richtliniensatzkoordinators aus und klicken Sie auf „Hinzufügen“. Die folgenden Berechtigungen können festgelegt werden:

      * Ereignisse anzeigen
      * Dokumente verwalten (Sperren und Entsperren von Dokumenten und Wechseln von Richtlinien für Dokumente)
      * Richtlinien verwalten (Richtlinien erstellen, bearbeiten und löschen)
      * Verwalten von Dokumentherausgebern (Dokumentherausgeber hinzufügen und löschen)
      * Delegieren (Richtliniensatzkoordinatoren hinzufügen und entfernen)

1. Wiederholen Sie Schritt 5, um weitere Richtliniensatzkoordinatoren hinzuzufügen.
1. Überprüfen Sie die Einstellungen des Richtliniensatzkoordinators und klicken Sie auf „Weiter“.
1. Klicken Sie auf „Benutzer und Gruppen hinzufügen“, um Dokumentherausgeber hinzuzufügen, die zum Schützen von Dokumenten die Richtlinien in diesem Richtliniensatz nutzen können.
1. Führen Sie auf der Seite „Herausgeber des Dokuments hinzufügen“ die folgenden Aufgaben durch:

   * Geben Sie in das Feld „Suchen“ den Namen oder die E-Mail-Adresse ein.
   * Wählen Sie in der Liste „Verwendet“ die passende Option aus.
   * Wählen Sie in der Liste „Typ“ die Option „Benutzer“ und in der Liste „In“ eine zu durchsuchende Domäne aus.
   * Wählen Sie in der Liste „Anzeigen“ die Anzahl der pro Seite anzuzeigenden Suchergebnisse aus und klicken Sie auf „Suchen“.
   * Aktivieren Sie die Kontrollkästchen der hinzuzufügenden Benutzer und Gruppen. Klicken Sie auf „Hinzufügen“ und danach auf „OK“.

1. Klicken Sie auf Speichern.

Sie können nun dem Richtliniensatz Richtlinien hinzufügen. (Siehe [Richtlinien erstellen und bearbeiten](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).)

## Einen Richtliniensatz bearbeiten  {#edit-a-policy-set}

1. Klicken Sie auf der Document Security-Seite auf „Richtlinien“, anschließend auf die Registerkarte „Richtliniensätze“ und dann auf den zu bearbeitenden Richtliniensatz.
1. Klicken Sie auf die gewünschte Registerkarte und führen Sie die Bearbeitung durch:

   * **Detail:** Bearbeiten Sie den Namen und die Beschreibung des Richtliniensatzes.
   * **Richtlinien:** Dient zum Erstellen, Aktivieren, Bearbeiten und Löschen von Richtlinien im Richtliniensatz.
   * **Sichtbare Benutzer und Gruppen:** Dient zum Hinzufügen und Entfernen sichtbarer Benutzer und Gruppen, die in eine Richtlinie einbezogen werden können.
   * **Richtliniensatzkoordinatoren:** Dient zum Hinzufügen, Entfernen und Ändern von Berechtigungen für Koordinatoren.
   * **Dokumentherausgeber:** Dient zum Hinzufügen und Entfernen von Benutzern, die Dokumente unter Verwendung der Richtlinien im Satz veröffentlichen können.

1. Um einen sichtbaren Benutzer, Richtliniensatzkoordinator oder Dokumentherausgeber oder eine sichtbare Gruppe zu löschen, klicken Sie auf die entsprechende Registerkarte und aktivieren Sie das Kontrollkästchen des jeweiligen Eintrags. Klicken Sie dann auf „Löschen“ und anschließend auf „OK“.
1. Um sichtbare Benutzer, Gruppen, Richtliniensatzkoordinatoren oder Dokumentherausgeber hinzuzufügen, wählen Sie die entsprechende Registerkarte aus und klicken Sie auf „Benutzer oder Gruppen hinzufügen“. Suchen Sie den Benutzer oder die Gruppe, wählen Sie den Eintrag aus, klicken Sie auf „Hinzufügen“ und anschließend auf „OK“.
1. Auf der Registerkarte „Richtlinien“ können Sie nach Richtlinien suchen, die dem Richtliniensatz hinzugefügt werden sollen, und neue Richtlinien erstellen:

   * Um eine Richtlinie zu suchen, wählen Sie „Richtlinien-ID“ oder „Richtlinienname“ aus, geben den gewünschten Wert ein, wählen die Anzahl anzuzeigender Elemente aus und klicken auf „Suchen“.
   * Informationen zum Erstellen einer neuen Richtlinie finden Sie unter [Richtlinien erstellen und bearbeiten](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).

## Einen Richtliniensatz löschen  {#delete-a-policy-set}

Beim Löschen eines Richtliniensatzes können Richtlinien, die Bestandteil des Satzes waren, nicht mehr auf neue Dokumente angewendet werden. Sie können die Richtlinieninformationen aber sowohl in Administration Console als auch auf den Webseiten für Endbenutzer für Richtlinien, die noch in Benutzung sind, anzeigen. Sie können die Richtlinieninformationen über die Seite „Dokumentdetails“ jedes von dieser Richtlinie geschützten Dokuments anzeigen. Richtlinien, die noch verwendet werden, können bearbeitet werden.

1. Klicken Sie auf „Richtlinien“ und anschließend auf die Registerkarte „Richtliniensätze“.
1. Aktivieren Sie die Kontrollkästchen des Richtliniensatzes, der gelöscht werden soll.
1. Klicken Sie auf „Löschen“ und dann auf „OK“.

