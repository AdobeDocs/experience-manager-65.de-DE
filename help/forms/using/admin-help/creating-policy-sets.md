---
title: Erstellen und Verwalten von Richtliniensätzen
description: Richtliniensätze dienen zum Gruppieren von Richtlinien mit einem gemeinsamen Geschäftszweck. Sie können Richtlinien in einem Richtliniensatz erstellen, bearbeiten und löschen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: 736926af-ae41-4da3-b181-444de72407bd
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1297'
ht-degree: 15%

---

# Erstellen und Verwalten von Richtliniensätzen {#creating-and-managing-policy-sets}

Richtliniensätze dienen zum Gruppieren von Richtlinien mit einem gemeinsamen Geschäftszweck. Richtliniensätze können einer Untergruppe von Benutzern im System zur Verfügung gestellt werden.

Jedem Richtliniensatz ist mindestens ein Richtliniensatzkoordinator zugeordnet. Die *Richtliniensatzkoordinator* ist ein Administrator oder Benutzer mit zusätzlichen Berechtigungen. Der Richtliniensatzkoordinator ist in der Regel ein Spezialist im Unternehmen, der die Richtlinien in einem bestimmten Richtliniensatz am besten verfassen kann.

Richtliniensatz-Koordinatorinnen und -Koordinatoren können die folgenden Aufgaben ausführen:

* Neue Richtlinien erstellen
* Bearbeiten und Löschen einer beliebigen Richtlinie im Richtliniensatz
* Bearbeiten von Einstellungen für Richtliniensätze
* Hinzufügen und Entfernen von Koordinatoren für den Richtliniensatz
* Anzeigen von Richtlinien- und Dokumentereignissen für jede Richtlinie oder jedes Dokument innerhalb des Richtliniensatzes
* Widerrufen des Zugangs zu Dokumenten
* Richtlinien für das Dokument wechseln

Richtliniensätze werden in der Administrator-Benutzeroberfläche von Document Security von Superbenutzern und Richtliniensatzkoordinatoren erstellt und gelöscht, die dazu berechtigt sind.

Wenn Sie einen Richtliniensatz löschen, können Richtlinien, die Teil des Satzes waren, nicht auf neue Dokumente angewendet werden. Sie können die Richtlinieninformationen jedoch sowohl in der Administration Console als auch auf den Webseiten für Endbenutzer für Richtlinien anzeigen, die noch verwendet werden. Sie können die Richtlinieninformationen für jedes durch die Richtlinie geschützte Dokument auf der Dokumentdetailseite anzeigen. Richtlinien, die noch verwendet werden, können bearbeitet werden.

Der Hauptbenutzer oder Richtliniensatzkoordinator muss für jeden Richtliniensatz in User Management erstellte Domains auswählen und zum sichtbaren Benutzer bzw. zur sichtbaren Gruppe hinzufügen. Diese Liste wird dem Richtliniensatzkoordinator angezeigt und dient zum Eingrenzen der Domains, die der Richtliniensatzkoordinator beim Auswählen von Benutzern durchsuchen kann, die Richtlinien hinzugefügt werden sollen.

Beim Erstellen von Richtliniensätzen weisen Sie Benutzern die Rolle des Dokumentherausgebers zu. Der *Dokumentherausgeber* ist der Benutzer, der das Dokument mit einer Richtlinie schützt. Dieser Benutzer wird standardmäßig immer in eine Richtlinie mit vollständigen Zugriffsrechten einbezogen, einschließlich Funktionen zum Sperren und Wechseln von Richtlinien. Administratoren können jedoch die Zugriffsberechtigungen des Dokumentherausgebers für freigegebene Richtlinien ändern. Beispielsweise kann der Administrator die Berechtigung des Dokumentherausgebers zum Sperren des Dokumentzugriffs oder Wechseln der Richtlinie deaktivieren. Wenn ein Administrator die mit dem Dokument verknüpfte Richtlinie wechselt, wird der Herausgebername auf den Namen des Eigentümers der Richtlinie aktualisiert, die zuletzt auf das Dokument angewendet wurde.

Bei der Installation von Document Security wird ein standardmäßiger Richtliniensatz erstellt, der *Globaler Richtliniensatz*. Dieser Richtliniensatz wird vom Administrator, der die Software installiert hat, oder vom Richtliniensatzkoordinator verwaltet, der für diesen Richtliniensatz bestimmt ist.

## Erstellen eines Richtliniensatzes {#create-a-policy-set}

Der globale Richtliniensatz ist der einzige StandardRichtliniensatz, der bei der Installation erstellt wird. Sie können zusätzliche Richtliniensätze erstellen und Richtlinien, Benutzer, Richtliniensatzkoordinatoren und Dokumentherausgeber hinzufügen. Nachdem Sie einen Richtliniensatz erstellt haben, können Sie Richtlinien im Satz erstellen.

Bei der Erstellung von Richtliniensätzen können Sie die Schaltfläche Zurück verwenden, um zum vorherigen Bildschirm zurückzukehren, und die Schaltfläche Speichern , um Ihren Richtliniensatz jederzeit zu speichern.

1. Klicken Sie auf der Document Security-Seite auf &quot;Richtlinien&quot;, klicken Sie auf die Registerkarte &quot;Richtliniensätze&quot;und dann auf &quot;Neu&quot;.
1. Geben Sie in das Feld &quot;Name&quot;einen Namen für den Richtliniensatz ein, geben Sie optional eine Beschreibung ein und klicken Sie auf &quot;Weiter&quot;. Der Name darf keinen Doppelpunkt (**:**) enthalten.

   >[!NOTE]
   >
   >Sie können einen Richtliniensatznamen erstellen, der erweiterte Zeichen enthält. Wenn jedoch ein Vergleich zwischen zwei Zeichenfolgen durchgeführt wird, werden Zeichen mit und ohne Akzentzeichen wie &quot;e&quot;und &quot;é&quot;als identisch betrachtet. Wenn jemand einen Richtliniensatz erstellt, wird ein Vergleich durchgeführt, um zu überprüfen, ob bereits ein Richtliniensatz mit demselben Namen vorhanden ist. Der Vergleich kann nicht zwischen Namen unterscheiden, die mit Ausnahme von Akzentzeichen identisch sind. Es wird davon ausgegangen, dass der Richtliniensatz bereits zur Datenbank hinzugefügt und der neue nicht hinzugefügt wurde.

1. (Optional) Um die Domains festzulegen, die Herausgebern von Dokumenten beim Hinzufügen von Benutzern zu einer Richtlinie angezeigt werden, klicken Sie auf „Domains hinzufügen“, wählen Sie anschließend die Domains aus, die durchsuchbar sein sollen, klicken Sie auf „Hinzufügen“ und danach auf „OK“.
1. Klicken Sie auf der Seite &quot;Sichtbare Benutzer und Gruppen hinzufügen&quot;auf Weiter .
1. (Optional) Um einen Richtliniensatzkoordinator hinzuzufügen, klicken Sie auf der Seite &quot;Richtliniensatzkoordinatoren hinzufügen&quot;(Schritt 3 von 4) auf Benutzer und Gruppen hinzufügen und führen Sie die folgenden Aufgaben aus:

   * Geben Sie in das Feld &quot;Suchen&quot;den Namen oder die E-Mail-Adresse ein.
   * Wählen Sie in der Liste Verwendung die entsprechende Option aus.
   * Wählen Sie in der Liste „Typ“ die Option „Benutzer“ und in der Liste „In“ eine zu durchsuchende Domain aus.
   * Wählen Sie in der Liste &quot;Anzeigen&quot;die Anzahl der pro Seite anzuzeigenden Ergebnisse aus und klicken Sie auf &quot;Suchen&quot;.
   * Aktivieren Sie das Kontrollkästchen für den hinzuzufügenden Benutzer oder die hinzuzufügende Gruppe und klicken Sie auf Weiter .
   * Wählen Sie die Berechtigungen des Richtliniensatzkoordinators aus und klicken Sie auf Hinzufügen. Die folgenden Berechtigungen können festgelegt werden:

      * Ereignisse anzeigen
      * Verwalten von Dokumenten (Sperren und Reaktivieren des Zugriffs auf Dokumente und Wechseln von Richtlinien für Dokumente)
      * Richtlinien verwalten (Richtlinien erstellen, bearbeiten und löschen)
      * Verwalten von Dokumentherausgebern (Hinzufügen und Entfernen von Dokumentherausgebern)
      * Delegieren (Richtliniensatzkoordinatoren hinzufügen und entfernen)

1. Wiederholen Sie Schritt 5, um weitere Richtliniensatzkoordinatoren hinzuzufügen.
1. Überprüfen Sie die Einstellungen des Richtliniensatzkoordinators und klicken Sie auf Weiter.
1. Klicken Sie auf Benutzer und Gruppen hinzufügen , um Dokumentherausgeber hinzuzufügen, die die Richtlinien im Richtliniensatz zum Schützen von Dokumenten verwenden können.
1. Führen Sie auf der Seite &quot;Dokumentherausgeber hinzufügen&quot;die folgenden Aufgaben aus:

   * Geben Sie in das Feld &quot;Suchen&quot;den Namen oder die E-Mail-Adresse ein.
   * Wählen Sie in der Liste Verwendung die entsprechende Option aus.
   * Wählen Sie in der Liste „Typ“ die Option „Benutzer“ und in der Liste „In“ eine zu durchsuchende Domain aus.
   * Wählen Sie in der Liste &quot;Anzeigen&quot;die Anzahl der pro Seite anzuzeigenden Ergebnisse aus und klicken Sie auf &quot;Suchen&quot;.
   * Aktivieren Sie die Kontrollkästchen der hinzuzufügenden Benutzer und Gruppen, klicken Sie auf Hinzufügen und anschließend auf OK.

1. Klicken Sie auf Speichern.

Sie können Ihrem Richtliniensatz jetzt Richtlinien hinzufügen. (Siehe [Richtlinien erstellen und bearbeiten](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).

## Richtliniensatz bearbeiten {#edit-a-policy-set}

1. Klicken Sie auf der Document Security-Seite auf &quot;Richtlinien&quot;, klicken Sie auf die Registerkarte &quot;Richtliniensätze&quot;und dann auf den zu bearbeitenden Richtliniensatz.
1. Klicken Sie auf die entsprechende Registerkarte und bearbeiten Sie sie nach Bedarf:

   * **Detail:** Bearbeiten Sie den Namen und die Beschreibung des Richtliniensatzes.
   * **Richtlinien:** Erstellen, aktivieren, bearbeiten und löschen Sie Richtlinien im Richtliniensatz.
   * **Sichtbare Benutzer und Gruppen:** Fügen Sie sichtbare Benutzer und Gruppen hinzu und entfernen Sie sie, die in eine Richtlinie aufgenommen werden können.
   * **Richtliniensatzkoordinatoren:** Berechtigungen für Koordinatoren hinzufügen, entfernen und ändern.
   * **Dokumentherausgeber:** Fügen Sie Benutzer hinzu und entfernen Sie Benutzer, die Dokumente mithilfe der Richtlinien im Satz veröffentlichen können.

1. Um einen sichtbaren Benutzer, eine sichtbare Gruppe, einen Richtliniensatzkoordinator oder einen Dokumentherausgeber zu löschen, klicken Sie auf die entsprechende Registerkarte, aktivieren Sie das Kontrollkästchen für den Eintrag, klicken Sie auf &quot;Löschen&quot;und klicken Sie auf &quot;OK&quot;.
1. Um sichtbare Benutzer oder Gruppen, einen Richtliniensatzkoordinator oder Dokumentherausgeber hinzuzufügen, klicken Sie auf die entsprechende Registerkarte, klicken Sie auf &quot;Benutzer oder Gruppen hinzufügen&quot;, suchen Sie nach dem hinzuzufügenden Benutzer oder der hinzuzufügenden Gruppe, wählen Sie den Eintrag aus, klicken Sie auf &quot;Hinzufügen&quot;und klicken Sie auf &quot;OK&quot;.
1. Suchen Sie auf der Registerkarte Richtlinien nach Richtlinien, die zum Richtliniensatz hinzugefügt werden sollen, und erstellen Sie neue Richtlinien:

   * Um nach einer Richtlinie zu suchen, wählen Sie &quot;Richtlinien-ID&quot;oder &quot;Richtlinienname&quot;, geben Sie den entsprechenden Wert ein, wählen Sie die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf &quot;Suchen&quot;.
   * Weitere Informationen zum Erstellen einer Richtlinie finden Sie unter [Richtlinien erstellen und bearbeiten](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).

## Richtliniensatz löschen {#delete-a-policy-set}

Wenn Sie einen Richtliniensatz löschen, können Richtlinien, die Teil des Satzes waren, nicht auf neue Dokumente angewendet werden. Sie können die Richtlinieninformationen jedoch sowohl in der Administration Console als auch auf den Webseiten für Endbenutzer für Richtlinien anzeigen, die noch verwendet werden. Sie können die Richtlinieninformationen für jedes durch die Richtlinie geschützte Dokument auf der Dokumentdetailseite anzeigen. Richtlinien, die noch verwendet werden, können bearbeitet werden.

1. Klicken Sie auf Richtlinien und dann auf die Registerkarte Richtliniensätze .
1. Aktivieren Sie das Kontrollkästchen für den zu löschenden Richtliniensatz.
1. Klicken Sie auf Löschen und dann auf OK.
