---
title: Erstellen und Verwalten von Richtliniensätzen
description: Richtliniensätze dienen zum Gruppieren von Richtlinien mit einem gemeinsamen Geschäftszweck. Sie können Richtlinien in einem Richtliniensatz erstellen, bearbeiten und löschen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: 736926af-ae41-4da3-b181-444de72407bd
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1297'
ht-degree: 100%

---

# Erstellen und Verwalten von Richtliniensätzen {#creating-and-managing-policy-sets}

Richtliniensätze dienen zum Gruppieren von Richtlinien mit einem gemeinsamen Geschäftszweck. Richtliniensätze können einer Teilmenge der Benutzenden im System zur Verfügung gestellt werden.

Jedem Richtliniensatz ist mindestens eine Richtliniensatzkoordinatorin oder ein Richtliniensatzkoordinator zugeordnet. *Richtliniensatzkoordinatorinnen und -koordinatoren* sind Admins oder Benutzende mit zusätzlichen Berechtigungen. Richtliniensatzkoordinatorinnen und -koordinatoren sind in der Regel spezialisierte Personen im Unternehmen, die die Richtlinien eines bestimmten Richtliniensatzes am besten erstellen können.

Richtliniensatzkoordinatorinnen und -koordinatoren können die folgenden Aufgaben ausführen:

* Erstellen neuer Richtlinien
* Bearbeiten und Löschen einer beliebigen Richtlinie im Richtliniensatz
* Bearbeiten von Einstellungen für Richtliniensätze
* Hinzufügen und Entfernen von Koordinatorinnen und Koordinatoren für den Richtliniensatz
* Anzeigen von Richtlinien- und Dokumentereignissen für jede Richtlinie oder jedes Dokument innerhalb des Richtliniensatzes
* Widerrufen des Zugangs zu Dokumenten
* Wechseln der Richtlinien für das Dokument

Richtliniensätze werden auf der Admin-Schnittstelle der Dokumentensicherheit von Hauptbenutzenden und Richtliniensatzkoordinatorinnen bzw. -koordinatoren erstellt und gelöscht, denen die entsprechenden Berechtigungen erteilt wurden.

Beim Löschen eines Richtliniensatzes können Richtlinien, die Bestandteil des Satzes waren, nicht mehr auf neue Dokumente angewendet werden. Sie können jedoch die Richtlinieninformationen für Richtlinien, die noch in Benutzung sind, sowohl in der Administrationskonsole als auch auf den Web-Seiten für Endbenutzende anzeigen. Sie können die Richtlinieninformationen über die Seite mit den Dokumentdetails für jedes von dieser Richtlinie geschützte Dokument anzeigen. Richtlinien, die noch verwendet werden, können bearbeitet werden.

Der Hauptbenutzer oder Richtliniensatzkoordinator muss für jeden Richtliniensatz in User Management erstellte Domains auswählen und zum sichtbaren Benutzer bzw. zur sichtbaren Gruppe hinzufügen. Diese Liste wird dem Richtliniensatzkoordinator angezeigt und dient zum Eingrenzen der Domains, die der Richtliniensatzkoordinator beim Auswählen von Benutzern durchsuchen kann, die Richtlinien hinzugefügt werden sollen.

Beim Erstellen von Richtliniensätzen weisen Sie Benutzenden die Rolle der Dokumentenherausgeberin bzw. des Dokumentenherausgebers zu. Der *Dokumentherausgeber* ist der Benutzer, der das Dokument mit einer Richtlinie schützt. Diese Person wird stets standardmäßig in eine Richtlinie einbezogen und hat Vollzugriffsrechte, so auch zum Sperren des Dokumentzugriffs oder Wechseln der Richtlinie. Admins können jedoch die Zugriffsrechte von Dokumentherausgeberinnen bzw. -herausgebern für freigegebene Richtlinien ändern. Beispielsweise können Admins den Dokumentherausgeberinnen bzw. -herausgebern die Rechte zum Sperren des Dokumentzugriffs oder Wechseln der Richtlinie entziehen. Wenn Admins die Richtlinie wechseln, die mit dem Dokument verknüpft ist, wird der Herausgebername auf den Namen der Eigentümerin bzw. des Eigentümers der Richtlinie aktualisiert, die zuletzt auf das Dokument angewendet wurde.

Bei der Installation der Dokumentensicherheit wird standardmäßig ein sogenannter *globaler Richtliniensatz* erstellt. Dieser Richtliniensatz wird von der Person, die die Software als Admin installiert hat, oder der Person, die für diesen Richtliniensatz als Richtliniensatzkoordinatorin bzw. -koordinator festgelegt wurde, verwaltet.

## Erstellen eines Richtliniensatzes {#create-a-policy-set}

Der globale Richtliniensatz ist der einzige Standardrichtliniensatz, der bei der Installation erstellt wird. Sie können weitere Richtliniensätze erstellen und dabei Richtlinien, Benutzende, Richtliniensatzkoordinatorinnen sowie -koordinatoren und Dokumentherausgeberinnen sowie -herausgeber hinzufügen. Nach Erstellen eines Richtliniensatzes können Sie Richtlinien in dem Satz erstellen.

Klicken Sie bei der Richtliniensatzerstellung auf die Schaltfläche „Zurück“, um zum vorherigen Bildschirm zurückzukehren. Um den Richtliniensatz zu speichern, klicken Sie zu einem beliebigen Zeitpunkt auf die Schaltfläche „Speichern“.

1. Klicken Sie auf der Document Security-Seite auf „Richtlinien“, auf die Registerkarte „Richtliniensätze“ und anschließend auf „Neu“.
1. Geben Sie in das Feld „Name“ einen Namen für den Richtliniensatz und optional in das Feld „Beschreibung“ eine Beschreibung ein. Klicken Sie danach auf „Weiter“. Der Name darf keinen Doppelpunkt (**:**) enthalten.

   >[!NOTE]
   >
   >Sie können einen Richtliniensatznamen erstellen, der erweiterte Zeichen enthält. Bei einem Vergleich zwischen zwei derartigen Zeichenfolgen werden jedoch Zeichen mit und ohne Akzentzeichen, wie z. B. „e“ und „é“, als identisch bewertet. Beim Erstellen eines Richtliniensatzes wird ein Vergleich durchgeführt, um zu überprüfen, ob bereits ein Richtliniensatz mit demselben Namen vorhanden ist. Der Vergleich kann nicht zwischen Namen unterscheiden, die sich nur durch Akzentzeichen unterscheiden. Es wird dann angenommen, dass der Richtliniensatz bereits zur Datenbank hinzugefügt wurde, sodass der neue nicht hinzugefügt wird.

1. (Optional) Um die Domains festzulegen, die Herausgebern von Dokumenten beim Hinzufügen von Benutzern zu einer Richtlinie angezeigt werden, klicken Sie auf „Domains hinzufügen“, wählen Sie anschließend die Domains aus, die durchsuchbar sein sollen, klicken Sie auf „Hinzufügen“ und danach auf „OK“.
1. Klicken Sie auf der Seite „Sichtbare Benutzer und Gruppen hinzufügen“ auf „Weiter“.
1. (Optional) Um Richtliniensatzkoordinatorinnen bzw. -koordinatoren hinzuzufügen, klicken Sie auf der Seite „Richtliniensatzkoordinator(en) hinzuzufügen“ auf „Benutzer und Gruppen hinzufügen“ (Schritt 3 von 4) und führen Sie die folgenden Schritte aus:

   * Geben Sie in das Feld „Suchen“ den Namen oder die E-Mail-Adresse ein.
   * Wählen Sie in der Liste „Verwendet“ die passende Option aus.
   * Wählen Sie in der Liste „Typ“ die Option „Benutzer“ und in der Liste „In“ eine zu durchsuchende Domain aus.
   * Wählen Sie in der Liste „Anzeigen“ die Anzahl der pro Seite anzuzeigenden Suchergebnisse aus und klicken Sie auf „Suchen“.
   * Aktivieren Sie das Kontrollkästchen der Person oder Gruppe, die hinzugefügt werden soll, und klicken Sie auf „Weiter“.
   * Wählen Sie die Berechtigungen der Richtliniensatzkoordinatorin bzw. des Richtliniensatzkoordinators aus und klicken Sie auf „Hinzufügen“. Die folgenden Berechtigungen können festgelegt werden:

      * Ereignisse anzeigen
      * Dokumente verwalten (Dokumente sperren oder deren Sperren aufheben sowie Richtlinien für Dokumente wechseln)
      * Richtlinien verwalten (Richtlinien erstellen, bearbeiten oder löschen)
      * Herausgeber des Dokuments verwalten (Herausgeber des Dokuments hinzufügen oder entfernen)
      * Delegieren (Richtliniensatzkoordinatoren hinzufügen und entfernen)

1. Wiederholen Sie Schritt 5, um weitere Richtliniensatzkoordinatorinnen und -koordinatoren hinzuzufügen.
1. Überprüfen Sie die Einstellungen der Richtliniensatzkoordinatorin bzw. des Richtliniensatzkoordinators und klicken Sie auf „Weiter“.
1. Klicken Sie auf „Benutzer und Gruppen hinzufügen“, um Dokumentherausgeberinnen oder -herausgeber hinzuzufügen, die zum Schützen von Dokumenten die Richtlinien in diesem Richtliniensatz nutzen können.
1. Führen Sie auf der Seite „Dokumentherausgeber hinzufügen“ die folgenden Aufgaben durch:

   * Geben Sie in das Feld „Suchen“ den Namen oder die E-Mail-Adresse ein.
   * Wählen Sie in der Liste „Verwendet“ die passende Option aus.
   * Wählen Sie in der Liste „Typ“ die Option „Benutzer“ und in der Liste „In“ eine zu durchsuchende Domain aus.
   * Wählen Sie in der Liste „Anzeigen“ die Anzahl der pro Seite anzuzeigenden Suchergebnisse aus und klicken Sie auf „Suchen“.
   * Aktivieren Sie die Kontrollkästchen der hinzuzufügenden Benutzenden und Gruppen. Klicken Sie auf „Hinzufügen“ und dann auf „OK“.

1. Klicken Sie auf Speichern.

Sie können nun dem Richtliniensatz Richtlinien hinzufügen. (Siehe [Erstellen und Bearbeiten von Richtlinien](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).)

## Bearbeiten eines Richtliniensatzes {#edit-a-policy-set}

1. Klicken Sie auf der Seite für die Dokumentensicherheit auf „Richtlinien“, anschließend auf die Registerkarte „Richtliniensätze“ und dann auf den zu bearbeitenden Richtliniensatz.
1. Klicken Sie auf die gewünschte Registerkarte und führen Sie die Bearbeitung durch:

   * **Details:** Bearbeiten Sie den Namen und die Beschreibung des Richtliniensatzes.
   * **Richtlinien:** Erstellen, aktivieren, bearbeiten und löschen Sie Richtlinien im Richtliniensatz.
   * **Sichtbare Benutzer und Gruppen:** Fügen Sie sichtbare Benutzende und Gruppen, die in eine Richtlinie einbezogen werden können, hinzu oder entfernen Sie sie.
   * **Richtliniensatzkoordinatoren:** Fügen Sie Berechtigungen für Koordinierende hinzu, entfernen oder ändern Sie diese.
   * **Herausgeber des Dokuments:** Fügen Sie Benutzende, die Dokumente mithilfe der Richtlinien im Satz veröffentlichen können, hinzu oder entfernen Sie diese.

1. Um eine sichtbare Person oder Gruppe, eine Richtliniensatzkoordinatorin bzw. einen Richtliniensatzkoordinator oder eine Dokumentherausgeberin bzw. einen Dokumentherausgeber zu löschen, klicken Sie auf die entsprechende Registerkarte und aktivieren Sie das Kontrollkästchen des jeweiligen Eintrags. Klicken Sie dann auf „Löschen“ und anschließend auf „OK“.
1. Um eine sichtbare Person oder Gruppe, eine Richtliniensatzkoordinatorin bzw. einen Richtliniensatzkoordinator oder eine Dokumentherausgeberin bzw. einen Dokumentherausgeber hinzuzufügen, klicken Sie auf die entsprechende Registerkarte und dann auf „Benutzer oder Gruppen hinzufügen“. Suchen Sie die Person oder die Gruppe, wählen Sie den Eintrag aus, klicken Sie auf „Hinzufügen“ und anschließend auf „OK“.
1. Auf der Registerkarte „Richtlinien“ können Sie nach Richtlinien suchen, die dem Richtliniensatz hinzugefügt werden sollen, und neue Richtlinien erstellen:

   * Um nach einer Richtlinie zu suchen, wählen Sie „Richtlinien-ID“ oder „Richtlinienname“ aus, geben den gewünschten Wert ein, wählen die Anzahl anzuzeigender Elemente aus und klicken auf „Suchen“.
   * Weitere Informationen zum Erstellen einer Richtlinie finden Sie unter [Erstellen und Bearbeiten von Richtlinien](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).

## Löschen eines Richtliniensatzes {#delete-a-policy-set}

Beim Löschen eines Richtliniensatzes können Richtlinien, die Bestandteil des Satzes waren, nicht mehr auf neue Dokumente angewendet werden. Sie können jedoch die Richtlinieninformationen für Richtlinien, die noch verwendet werden, sowohl in der Administrationskonsole als auch auf den Web-Seiten für Endbenutzende anzeigen. Sie können die Richtlinieninformationen über die Seite mit den Dokumentdetails für jedes von dieser Richtlinie geschützte Dokument anzeigen. Richtlinien, die noch verwendet werden, können bearbeitet werden.

1. Klicken Sie auf „Richtlinien“ und anschließend auf die Registerkarte „Richtliniensätze“.
1. Aktivieren Sie die Kontrollkästchen des Richtliniensatzes, der gelöscht werden soll.
1. Klicken Sie auf „Löschen“ und dann auf „OK“.
