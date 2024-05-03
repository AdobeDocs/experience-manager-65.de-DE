---
title: Erstellen und Konfigurieren von Gruppen
description: Erfahren Sie, wie Sie Gruppen manuell oder dynamisch erstellen, eine Gruppe bearbeiten, Details zu einer Gruppe anzeigen oder eine Gruppe löschen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 72edd8d1-8573-4942-8ced-1a100af58d78
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1576'
ht-degree: 100%

---

# Erstellen und Konfigurieren von Gruppen{#creating-and-configuring-groups}

Durch das Erstellen von Benutzergruppen können Sie der Gruppe statt einzelnen Benutzenden Rollen zuweisen.

Es stehen zwei verschiedene Arten von Gruppen zur Verfügung. Sie können eine Gruppe manuell erstellen und ihr Benutzende und andere Gruppen hinzufügen. Sie können auch dynamische Gruppen erstellen, die automatisch alle Benutzenden einschließen, die einen bestimmten Regelsatz erfüllen.

Bei Benutzenden kann es zu einer langsameren Reaktionszeit kommen, wenn sie vielen Gruppen angehören (z. B. 500 oder mehr) oder wenn die Gruppen tief verschachtelt sind (z. B. 30 Ebenen). Wenn dieses Problem auftritt, können Sie AEM Forms so konfigurieren, dass Informationen aus bestimmten Domains vorher abgerufen werden. (Siehe [AEM Forms zum vorherigen Abrufen von Domain-Informationen konfigurieren](/help/forms/using/admin-help/configure-aem-forms-prefetch-domain.md#configure-aem-forms-to-prefetch-domain-information).)

## Manuelles Erstellen einer Gruppe {#create-a-group-manually}

Wenn Sie eine Gruppe manuell erstellen, können Sie ihr Benutzende und andere Gruppen hinzufügen und der Gruppe Rollen zuweisen. Sie können die Gruppe auch einer übergeordneten Gruppe zuordnen.

Wenn Sie Content Services (nicht mehr unterstützt) verwenden, können Sie auf der Seite „Domain-Verwaltung“ die Option „Wählen Sie diese Option, um für Benutzer und Gruppen ein Pushing in registrierte externe Prinzipalspeicheranbieter durchzuführen“ wählen, um ein Pushing der Informationen für alle neu erstellten Benutzer und Gruppen in Content Services (nicht mehr unterstützt) durchzuführen.

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „User Management“ > „Benutzende und Gruppen“ und dann auf „Neue Gruppe“.
1. Füllen Sie den Abschnitt „Allgemeine Einstellungen“ aus und klicken Sie auf „Weiter“. „Kanonischer Name“ und „Gruppenname“ sind obligatorische Attribute.

   Der kanonische Name ist eine eindeutige Kennung der Gruppe. Jede Gruppe und jeder Benutzer in einer Domain muss einen eindeutigen kanonischen Namen haben. Aktivieren Sie das Kontrollkästchen „Systemgeneriert“, damit User Management einen eindeutigen Wert zuweist, oder deaktivieren Sie das Kontrollkästchen und geben Sie einen benutzerdefinierten Wert für den kanonischen Namen an.

   Vermeiden Sie den Unterstrich (_) in kanonischen Namen z. B. `sample_group`. Wenn Sie anhand von kanonischen Namen nach Gruppen suchen, werden solche, die einen Unterstrich enthalten, nicht zurückgegeben.

1. Um Benutzende und Gruppen zu dieser neuen Gruppe hinzuzufügen, klicken Sie auf „Benutzer/Gruppen suchen“ und führen Sie die folgenden Aufgaben aus:

   * Geben Sie die gewünschten Suchkriterien in das Feld „Suchen“ ein.
   * Wählen Sie in der Liste „Ein“ die Option „Benutzer“, „Gruppen“ oder „Benutzer und Gruppen“ aus.
   * Wählen Sie in der Liste „Verwenden von“ Namen, E-Mail oder Benutzer-ID aus.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf „Suchen“.
   * Wählen Sie in den Suchergebnissen die Kontrollkästchen für die Benutzenden und Gruppen aus, die Sie dieser neuen Gruppe hinzufügen möchten, und klicken Sie auf „OK“.

1. Klicken Sie auf Weiter.
1. Um diese neue Gruppe zu anderen vorhandenen Gruppen hinzuzufügen, klicken Sie auf „Gruppen suchen“ und führen Sie die folgenden Aufgaben aus:

   * Geben Sie die gewünschten Suchkriterien in das Feld „Suchen“ ein.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf „Suchen“.
   * Wählen Sie die Kontrollkästchen in den Suchergebnissen für die Gruppen aus, zu denen die neue Gruppe gehört, und klicken Sie auf „OK“.

1. Klicken Sie auf Weiter.
1. Um der Gruppe Rollen zuzuweisen, klicken Sie auf „Rollen suchen“, wählen Sie die Kontrollkästchen für jede Rolle aus, die Sie der Gruppe zuweisen möchten, und klicken Sie auf „OK“. Benutzende in der Gruppe erben Rollen, die auf Gruppenebene zugewiesen sind.
1. Klicken Sie auf Beenden.

## Erstellen einer dynamischen Gruppe {#create-a-dynamic-group}

In einer dynamischen Gruppe wählen Sie die Benutzenden, die zur Gruppe gehören, nicht einzeln aus. Stattdessen geben Sie einen Satz Regeln an und alle Benutzenden, die diese Regeln erfüllen, werden automatisch der dynamischen Gruppe hinzugefügt.

Verwenden Sie eine dieser beiden Methoden, um dynamische Gruppen zu erstellen:

* Aktivieren Sie die automatische Erstellung dynamischer Gruppen auf Basis von E-Mail-Domains (z. B. @adobe.com). Wenn Sie diese Funktion aktivieren, erstellt User Management eine dynamische Gruppe für jede eindeutige E-Mail-Domain in der AEM Forms-Datenbank. Verwenden Sie einen Cron-Ausdruck, um anzugeben, wie oft User Management die AEM Forms-Datenbank nach neuen E-Mail-Domains durchsuchen soll. Diese dynamischen Gruppen werden der lokalen Domain „DefaultDom“ hinzugefügt und erhalten die Bezeichnung „Alle Benutzer mit einer *`[email domain]`*-E-Mail-ID“.
* Erstellen Sie eine dynamische Gruppe auf der Grundlage von bestimmten Kriterien, wie E-Mail-Domain des Benutzers, Beschreibung, allgemeinem Namen, kanonischem Namen und Domain-Namen. Um zur dynamischen Gruppe zu gehören, muss eine Person alle angegebenen Kriterien erfüllen. Um eine „oder“-Bedingung einzurichten, erstellen Sie zwei separate dynamische Gruppen und fügen Sie beide einer lokalen Gruppe hinzu. Verwenden Sie diese Vorgehensweise beispielsweise, um eine Gruppe von Benutzern zu erstellen, die zur E-Mail-Domain „@adobe.com“ gehören oder deren kanonischer Name ou=adobe.com enthält. Die Benutzer müssten jedoch nicht unbedingt beide Bedingungen erfüllen.

Eine dynamische Gruppe enthält nur Benutzende. Sie kann nicht andere Gruppen enthalten. Eine dynamische Gruppe kann jedoch zu einer übergeordneten Gruppe gehören.

### Dynamische Gruppen auf Basis von E-Mail-Domains automatisch erstellen {#automatically-create-dynamic-groups-based-on-email-domains}

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Erweiterte Systemattribute konfigurieren“.
1. Aktivieren Sie das Kontrollkästchen unter „Automatische Erstellung einer dynamischen Gruppe“.
1. Geben Sie an, wann User Manager auf neue E-Mail-Domains prüfen soll. Diese Zeit sollte nach der Domain-Synchronisierungszeit liegen, da die Erstellung dynamischer Gruppen nur sinnvoll ist, wenn die Domain-Synchronisierung abgeschlossen ist.

   * Um die automatische Synchronisierung täglich zu aktivieren, geben Sie die Uhrzeit im 24-Stunden-Format in das Feld „Erfolgt täglich um“ ein. Wenn Sie Ihre Einstellungen speichern, wird dieser Wert in einen Cron-Ausdruck umgewandelt, der im Feld unten angezeigt wird.
   * Um die Synchronisierung an einem bestimmten Tag der Woche oder im Monat oder in einem bestimmten Monat zu planen, geben Sie den entsprechenden Cron-Ausdruck in das Feld ein. Der Standardwert ist `0 00 4 ? * *`(d. h. jeden Tag um 4 Uhr nachprüfen).

     Die Verwendung des Cron-Ausdrucks basiert auf dem Open-Source-Vorgangsplanungssystem Quartz, Version 1.4.0.

1. Klicken Sie auf Speichern.

### Erstellen einer dynamischen Gruppe basierend auf angegebenen Kriterien {#create-a-dynamic-group-based-on-specified-criteria}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „User Management“ > „Benutzer und Gruppen“.
1. Klicken Sie auf „Neue dynamische Gruppe“.
1. Füllen Sie den Abschnitt „Allgemeine Einstellungen“ aus. „Gruppenname“ ist ein obligatorisches Attribut. Sie können die Gruppe einer beliebigen konfigurierten Domain zuordnen.
1. Geben Sie unter „Kriterien für dynamische Gruppen“ ein oder mehrere Attribute an, die zum Füllen der dynamischen Gruppe verwendet werden.

   >[!NOTE]
   >
   >Bei den Attributen „E-Mail“, „Beschreibung“ und „Kanonischer Name“ muss die Groß-/Kleinschreibung beachtet werden, wenn der Operator „Gleicht“ verwendet wird. Bei den Operatoren „Beginnt mit“, „Endet mit“ und „Enthält“ wird die Groß-/Kleinschreibung nicht beachtet.

   **E-Mail:** Die E-Mail-Domain des Benutzers, z. B. `@adobe.com`.

   **Beschreibung**: Beschreibung des Benutzers, z. B. „Informatiker“.

   **Kanonischer Name:** Der kanonische Name des Benutzers, z. B. `ou=adobe.com`.

   **Domain-Name**: Der Name der Domain, zu der der Benutzer gehört, z. B. `DefaultDom`. Bei dem Attribut „Domain-Name“ muss die Groß- und Kleinschreibung beachtet werden, wenn der Operator „Enthält“ verwendet wird. Bei den Operatoren „Beginnt mit“, „Endet mit“ und „Gleicht“ wird die Groß-/Kleinschreibung nicht beachtet.

1. Klicken Sie auf „Testen“. Auf einer Testseite werden die ersten 200 Benutzenden angezeigt, die die definierten Kriterien erfüllen. Klicken Sie auf Schließen.
1. Wenn der Test die erwarteten Ergebnisse zurückgegeben hat, klicken Sie auf „Weiter“. Andernfalls bearbeiten Sie die Kriterien der dynamischen Gruppe und führen Sie erneut einen Test aus.
1. Um die dynamische Gruppe zu einer übergeordneten Gruppe hinzuzufügen, klicken Sie auf „Gruppen suchen“ und führen Sie die folgenden Aufgaben aus:

   * Geben Sie die gewünschten Suchkriterien in das Feld „Suchen“ ein.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf „Suchen“.
   * Wählen Sie in den Suchergebnissen die Kontrollkästchen für Gruppen aus, zu denen die dynamische Gruppe gehört, und klicken Sie auf „OK“.

1. Klicken Sie auf Weiter.
1. Um der dynamischen Gruppe Rollen zuzuweisen, klicken Sie auf „Rollen suchen“, wählen Sie die Kontrollkästchen für jede Rolle aus, die Sie der Gruppe zuweisen möchten, und klicken Sie dann auf „OK“. Benutzende in der Gruppe erben Rollen, die auf Gruppenebene zugewiesen sind.
1. Klicken Sie auf Beenden.

## Anzeigen von Details zu einer Gruppe {#view-details-about-a-group}

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Benutzer und Gruppen“.
1. Wählen Sie in der Liste „Gruppe“ aus und klicken Sie dann auf „Suchen“. Die Suchergebnisse werden unten auf der Seite aufgelistet. Sie können die Liste sortieren, indem Sie auf eine der Spaltenüberschriften klicken.
1. Klicken Sie auf den Namen der Gruppe, zu der Details angezeigt werden sollen. Die Seite „Gruppendetails“ wird angezeigt.
1. Um direkte Mitglieder der Gruppe anzuzeigen, klicken Sie auf „Untergeordnete Prinzipale“.

## Bearbeiten einer Gruppe {#edit-a-group}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „User Management“ > „Benutzer und Gruppen“.
1. Führen Sie zum Suchen der zu bearbeitenden Gruppe die folgenden Aufgaben aus:

   * Geben Sie die gewünschten Suchkriterien in das Feld „Suchen“ ein.
   * Wählen Sie in der Liste „Verwenden von“ den Suchparameter „Name“ oder „E-Mail“ aus.
   * Wählen Sie in der Liste „Ein“ die Option „Gruppen“ aus.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf „Suchen“.
   * Klicken Sie in den Suchergebnissen auf den Namen der Gruppe, die Sie bearbeiten möchten.

1. Bearbeiten Sie auf der Registerkarte „Details“ die allgemeinen Einstellungen und klicken Sie auf „Speichern“.
1. Um die verknüpften Gruppen zu bearbeiten, klicken Sie auf die Registerkarte „Übergeordnete Gruppen“ und führen Sie diese Aufgaben aus:

   * Um Gruppen zu finden, die der Zuordnung hinzugefügt werden sollen, klicken Sie auf „Gruppen suchen“ und füllen Sie die Suchinformationen aus.
   * Um Gruppen hinzuzufügen, wählen Sie die Kontrollkästchen der hinzuzufügenden Gruppen aus und klicken Sie erst auf „OK“ und anschließend auf „Speichern“.
   * Um eine verknüpfte Gruppe zu löschen, wählen Sie das Kontrollkästchen für die zu löschende Gruppe aus, klicken Sie auf „Löschen“, klicken Sie auf „OK“ und dann auf „Speichern“.

1. Um die Benutzenden und Gruppen in der Gruppe zu bearbeiten, klicken Sie auf die Registerkarte „Untergeordnete Prinzipale“ und führen Sie diese folgenden Aufgaben aus:

   * Um nach Benutzenden und Gruppen zu suchen, die hinzugefügt werden sollen, klicken Sie auf „Benutzer/Gruppen suchen“ und füllen Sie die Suchinformationen aus.
   * Um Benutzende oder eine Gruppe hinzuzufügen, wählen Sie das Kontrollkästchen für die Person oder Gruppe aus, klicken Sie auf „OK“ und dann auf „Speichern“.
   * Um Benutzende oder eine Gruppe zu löschen, wählen Sie das Kontrollkästchen für die Person oder Gruppe aus, klicken Sie auf „Löschen“, klicken Sie auf „OK“ und dann auf „Speichern“.

1. Um Rollenzuweisungen zu bearbeiten, klicken Sie auf die Registerkarte „Rollenzuweisungen“ und führen Sie die folgenden Aufgaben aus:

   * Um nach Rollen zu suchen, die der Gruppe zugewiesen werden sollen, klicken Sie auf „Rollen suchen“.
   * Um eine Rolle hinzuzufügen, aktivieren Sie das Kontrollkästchen für die Rolle und klicken auf „OK“ und anschließend auf „Speichern“.
   * Um die Zuweisung einer Rolle aufzuheben, wählen Sie das Kontrollkästchen für die Rolle aus und klicken Sie auf „Zuweisung aufheben“ und anschließend auf „Speichern“.

## Löschen einer Gruppe {#delete-a-group}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „User Management“ > „Benutzer und Gruppen“.
1. Wählen Sie in der Liste „Suchen“ die Option „Gruppen“ aus und klicken Sie dann auf „Suchen“.
1. Wählen Sie das Kontrollkästchen der zu löschenden Gruppe aus und klicken Sie erst auf „Löschen“ und anschließend auf „OK“.
