---
title: Erstellen und Konfigurieren von Gruppen
description: Erfahren Sie, wie Sie Gruppen manuell oder dynamisch erstellen, eine Gruppe bearbeiten, Details zu einer Gruppe anzeigen oder eine Gruppe löschen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 72edd8d1-8573-4942-8ced-1a100af58d78
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1576'
ht-degree: 34%

---

# Erstellen und Konfigurieren von Gruppen{#creating-and-configuring-groups}

Durch das Erstellen von Benutzergruppen können Sie der Gruppe Rollen zuweisen, anstatt einzelnen Benutzern Rollen zuzuweisen.

Es stehen zwei verschiedene Gruppen zur Verfügung. Sie können manuell eine Gruppe erstellen und ihr Benutzer und andere Gruppen hinzufügen. Sie können auch dynamische Gruppen erstellen, die automatisch alle Benutzer einschließen, die einem bestimmten Regelsatz entsprechen.

Für Benutzer kann es zu einer langsameren Reaktionszeit kommen, wenn sie vielen Gruppen angehören (z. B. 500 oder mehr) oder wenn die Gruppen tief verschachtelt sind (z. B. 30 Ebenen). Wenn dieses Problem auftritt, können Sie AEM Forms so konfigurieren, dass Informationen aus bestimmten Domains vorher abgerufen werden. (Siehe [AEM Forms zum vorherigen Abrufen von Domain-Informationen konfigurieren](/help/forms/using/admin-help/configure-aem-forms-prefetch-domain.md#configure-aem-forms-to-prefetch-domain-information).)

## Manuelles Erstellen einer Gruppe {#create-a-group-manually}

Wenn Sie eine Gruppe manuell erstellen, können Sie ihr Benutzer und andere Gruppen hinzufügen und der Gruppe Rollen zuweisen. Sie können die Gruppe auch mit einer übergeordneten Gruppe verknüpfen.

Wenn Sie Content Services (nicht mehr unterstützt) verwenden, können Sie auf der Seite „Domain-Verwaltung“ die Option „Wählen Sie diese Option, um für Benutzer und Gruppen ein Pushing in registrierte externe Prinzipalspeicheranbieter durchzuführen“ wählen, um ein Pushing der Informationen für alle neu erstellten Benutzer und Gruppen in Content Services (nicht mehr unterstützt) durchzuführen.

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Benutzer und Gruppen&quot;und dann auf &quot;Neue Gruppe&quot;.
1. Füllen Sie den Abschnitt Allgemeine Einstellungen aus und klicken Sie auf Weiter. Kanonischer Name und Gruppenname sind obligatorische Attribute.

   Der kanonische Name ist eine eindeutige Kennung für die Gruppe. Jede Gruppe und jeder Benutzer in einer Domain muss einen eindeutigen kanonischen Namen haben. Aktivieren Sie das Kontrollkästchen „Systemgeneriert“, damit User Management einen eindeutigen Wert zuweist, oder deaktivieren Sie das Kontrollkästchen und geben Sie einen benutzerdefinierten Wert für den kanonischen Namen an.

   Vermeiden Sie den Unterstrich (_) in kanonischen Namen z. B. `sample_group`. Wenn Sie nach Gruppen suchen, die auf ihrem kanonischen Namen basieren, werden diejenigen mit Unterstrichzeichen nicht zurückgegeben.

1. Um dieser neuen Gruppe Benutzer und Gruppen hinzuzufügen, klicken Sie auf &quot;Benutzer/Gruppen suchen&quot;und führen die folgenden Schritte aus:

   * Geben Sie die gewünschten Suchkriterien in das Feld „Suchen“ ein.
   * Wählen Sie in der Liste &quot;In&quot;Benutzer, Gruppen oder Benutzer und Gruppen aus.
   * Wählen Sie in der Liste „Verwenden von“ Namen, E-Mail oder Benutzer-ID aus.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf „Suchen“.
   * Aktivieren Sie in den Suchergebnissen die Kontrollkästchen der Benutzer und Gruppen, die dieser neuen Gruppe hinzugefügt werden sollen, und klicken Sie auf &quot;OK&quot;.

1. Klicken Sie auf Weiter.
1. Um diese neue Gruppe zu anderen vorhandenen Gruppen hinzuzufügen, klicken Sie auf &quot;Gruppen suchen&quot;und führen die folgenden Schritte aus:

   * Geben Sie die gewünschten Suchkriterien in das Feld „Suchen“ ein.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf „Suchen“.
   * Aktivieren Sie in den Suchergebnissen die Kontrollkästchen der Gruppen, zu denen die neue Gruppe gehört, und klicken Sie auf &quot;OK&quot;.

1. Klicken Sie auf Weiter.
1. Um der Gruppe Rollen zuzuweisen, klicken Sie auf &quot;Rollen suchen&quot;, aktivieren die Kontrollkästchen der einzelnen Rollen, die der Gruppe zugewiesen werden sollen, und klicken Sie auf &quot;OK&quot;. Benutzer in der Gruppe übernehmen Rollen, die auf Gruppenebene zugewiesen werden.
1. Klicken Sie auf Beenden.

## Dynamische Gruppe erstellen {#create-a-dynamic-group}

In einer dynamischen Gruppe wählen Sie nicht einzeln die Benutzer aus, die zur Gruppe gehören. Stattdessen geben Sie einen Regelsatz an und alle Benutzer, die diese Regeln erfüllen, werden automatisch zur dynamischen Gruppe hinzugefügt.

Verwenden Sie eine der beiden Möglichkeiten, um dynamische Gruppen zu erstellen:

* Aktivieren Sie die automatische Erstellung dynamischer Gruppen auf Basis von E-Mail-Domains (z. B. @adobe.com). Wenn Sie diese Funktion aktivieren, erstellt User Management eine dynamische Gruppe für jede eindeutige E-Mail-Domain in der AEM Forms-Datenbank. Verwenden Sie einen Cron-Ausdruck, um anzugeben, wie oft User Management die AEM Forms-Datenbank nach neuen E-Mail-Domains durchsuchen soll. Diese dynamischen Gruppen werden der lokalen Domain „DefaultDom“ hinzugefügt und erhalten die Bezeichnung „Alle Benutzer mit einer *`[email domain]`*-E-Mail-ID“.
* Erstellen Sie eine dynamische Gruppe auf der Grundlage von bestimmten Kriterien, wie E-Mail-Domain des Benutzers, Beschreibung, allgemeinem Namen, kanonischem Namen und Domain-Namen. Um zur dynamischen Gruppe gehören zu können, muss ein Benutzer alle angegebenen Kriterien erfüllen. Um eine &quot;Oder&quot;-Bedingung einzurichten, erstellen Sie zwei separate dynamische Gruppen und fügen Sie beide zu einer lokalen Gruppe hinzu. Verwenden Sie diese Vorgehensweise beispielsweise, um eine Gruppe von Benutzern zu erstellen, die zur E-Mail-Domain „@adobe.com“ gehören oder deren kanonischer Name ou=adobe.com enthält. Die Benutzer müssten jedoch nicht unbedingt beide Bedingungen erfüllen.

Eine dynamische Gruppe enthält nur Benutzer. Sie kann keine anderen Gruppen enthalten. Eine dynamische Gruppe kann jedoch zu einer übergeordneten Gruppe gehören.

### Dynamische Gruppen auf Basis von E-Mail-Domains automatisch erstellen {#automatically-create-dynamic-groups-based-on-email-domains}

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Erweiterte Systemattribute konfigurieren“.
1. Aktivieren Sie unter &quot;Automatische Erstellung einer dynamischen Gruppe&quot;das Kontrollkästchen.
1. Geben Sie an, wann User Manager auf neue E-Mail-Domains prüfen soll. Diese Zeit sollte nach der Domain-Synchronisierungszeit liegen, da die Erstellung dynamischer Gruppen nur sinnvoll ist, wenn die Domain-Synchronisierung abgeschlossen ist.

   * Um die automatische tägliche Synchronisierung zu aktivieren, geben Sie die Zeit im 24-Stunden-Format in das Feld Täglich um ein. Wenn Sie Ihre Einstellungen speichern, wird dieser Wert in einen Cron-Ausdruck konvertiert, der im Feld unten angezeigt wird.
   * Um die Synchronisation an einem bestimmten Wochentag, Monat oder Monat oder in einem bestimmten Monat zu planen, wählen Sie die Option zum Eingeben des entsprechenden Cron-Ausdrucks in das Feld aus. Der Standardwert ist `0 00 4 ? * *`(d. h. jeden Tag um 4 Uhr nachprüfen).

     Die Verwendung von Cron-Ausdrücken basiert auf dem Open-Source-Auftragsplanungssystem Quartz, Version 1.4.0.

1. Klicken Sie auf Speichern.

### Dynamische Gruppe basierend auf bestimmten Kriterien erstellen {#create-a-dynamic-group-based-on-specified-criteria}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Benutzer und Gruppen&quot;.
1. Klicken Sie auf Neue dynamische Gruppe .
1. Füllen Sie den Abschnitt Allgemeine Einstellungen aus. Gruppenname ist ein obligatorisches Attribut. Sie können die Gruppe einer beliebigen konfigurierten Domain zuordnen.
1. Geben Sie unter &quot;Kriterien für dynamische Gruppen&quot;ein oder mehrere Attribute an, die zum Ausfüllen der dynamischen Gruppe verwendet werden.

   >[!NOTE]
   >
   >Bei den Attributen E-Mail, Beschreibung und Kanonischer Name wird bei der Verwendung des Operators Equals zwischen Groß- und Kleinschreibung unterschieden. Bei den Operatoren &quot;Beginnt mit&quot;, &quot;Endet mit&quot;und &quot;Enthält&quot;wird nicht zwischen Groß- und Kleinschreibung unterschieden.

   **E-Mail:** Die E-Mail-Domain des Benutzers, z. B. `@adobe.com`.

   **Beschreibung**: Beschreibung des Benutzers, z. B. „Informatiker“.

   **Kanonischer Name:** Der kanonische Name des Benutzers, z. B. `ou=adobe.com`.

   **Domain-Name**: Der Name der Domain, zu der der Benutzer gehört, z. B. `DefaultDom`. Bei dem Attribut „Domain-Name“ muss die Groß- und Kleinschreibung beachtet werden, wenn der Operator „Enthält“ verwendet wird. Bei den Operatoren &quot;Beginnt mit&quot;, &quot;Endet mit&quot;und &quot;Gleich&quot;wird nicht zwischen Groß- und Kleinschreibung unterschieden.

1. Klicken Sie auf Test. Auf einer Testseite werden die ersten 200 Benutzer angezeigt, die die definierten Kriterien erfüllen. Klicken Sie auf Schließen.
1. Wenn der Test die erwarteten Ergebnisse zurückgegeben hat, klicken Sie auf Weiter . Bearbeiten Sie andernfalls die Kriterien der dynamischen Gruppe und testen Sie erneut.
1. Um die dynamische Gruppe zu einer übergeordneten Gruppe hinzuzufügen, klicken Sie auf &quot;Gruppen suchen&quot;und führen die folgenden Schritte aus:

   * Geben Sie die gewünschten Suchkriterien in das Feld „Suchen“ ein.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf „Suchen“.
   * Aktivieren Sie in den Suchergebnissen die Kontrollkästchen der Gruppen, zu denen die dynamische Gruppe gehört, und klicken Sie auf &quot;OK&quot;.

1. Klicken Sie auf Weiter.
1. Um der dynamischen Gruppe Rollen zuzuweisen, klicken Sie auf &quot;Rollen suchen&quot;, aktivieren die Kontrollkästchen der einzelnen Rollen, die der Gruppe zugewiesen werden sollen, und klicken Sie auf &quot;OK&quot;. Benutzer in der Gruppe übernehmen Rollen, die auf Gruppenebene zugewiesen werden.
1. Klicken Sie auf Beenden.

## Details zu einer Gruppe anzeigen {#view-details-about-a-group}

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Benutzer und Gruppen“.
1. Wählen Sie in der Liste &quot;In&quot;die Option &quot;Gruppe&quot;und klicken Sie auf &quot;Suchen&quot;. Die Suchergebnisse werden unten auf der Seite aufgelistet. Sie können die Liste sortieren, indem Sie auf eine der Spaltenüberschriften klicken.
1. Klicken Sie auf den Namen der Gruppe, um Details anzuzeigen. Die Seite Gruppendetails wird angezeigt.
1. Um direkte Mitglieder der Gruppe anzuzeigen, klicken Sie auf Untergeordnete Prinzipale .

## Eine Gruppe bearbeiten {#edit-a-group}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Benutzer und Gruppen&quot;.
1. Gehen Sie wie folgt vor, um die zu bearbeitende Gruppe zu finden:

   * Geben Sie die gewünschten Suchkriterien in das Feld „Suchen“ ein.
   * Wählen Sie in der Liste &quot;Verwenden&quot;die Option Name oder E-Mail aus.
   * Wählen Sie in der Liste In die Option Gruppen aus.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf „Suchen“.
   * Klicken Sie in den Suchergebnissen auf den Namen der zu bearbeitenden Gruppe.

1. Bearbeiten Sie auf der Registerkarte Details die allgemeinen Einstellungen und klicken Sie auf Speichern .
1. Um die zugehörigen Gruppen zu bearbeiten, klicken Sie auf die Registerkarte &quot;Übergeordnete Gruppen&quot;und führen die folgenden Schritte aus:

   * Um Gruppen zu finden, die der Zuordnung hinzugefügt werden sollen, klicken Sie auf &quot;Gruppen suchen&quot;und geben Sie die Suchinformationen ein.
   * Um Gruppen hinzuzufügen, aktivieren Sie das Kontrollkästchen der hinzuzufügenden Gruppen, klicken auf &quot;OK&quot;und anschließend auf &quot;Speichern&quot;.
   * Um eine verknüpfte Gruppe zu löschen, aktivieren Sie das Kontrollkästchen der zu löschenden Gruppe, klicken auf &quot;Löschen&quot;, auf &quot;OK&quot;und anschließend auf &quot;Speichern&quot;.

1. Um die Benutzer und Gruppen in der Gruppe zu bearbeiten, klicken Sie auf die Registerkarte &quot;Untergeordnete Prinzipale&quot;und führen die folgenden Aufgaben aus:

   * Um hinzuzufügende Benutzer und Gruppen zu suchen, klicken Sie auf &quot;Benutzer/Gruppen suchen&quot;und geben Sie die Suchinformationen ein.
   * Um einen Benutzer oder eine Gruppe hinzuzufügen, aktivieren Sie das Kontrollkästchen für den Benutzer oder die Gruppe, klicken auf &quot;OK&quot;und anschließend auf &quot;Speichern&quot;.
   * Um einen Benutzer oder eine Gruppe zu löschen, aktivieren Sie das Kontrollkästchen für den Benutzer oder die Gruppe, klicken auf &quot;Löschen&quot;, auf &quot;OK&quot;und anschließend auf &quot;Speichern&quot;.

1. Um Rollenzuweisungen zu bearbeiten, klicken Sie auf die Registerkarte Rollenzuweisungen und führen die folgenden Schritte aus:

   * Um Rollen zu finden, die der Gruppe zugewiesen werden sollen, klicken Sie auf Rollen suchen .
   * Um eine Rolle hinzuzufügen, aktivieren Sie das Kontrollkästchen für die Rolle und klicken auf „OK“ und anschließend auf „Speichern“.
   * Um die Zuweisung einer Rolle aufzuheben, aktivieren Sie das Kontrollkästchen für die Rolle, klicken auf &quot;Zuweisung aufheben&quot;und anschließend auf &quot;Speichern&quot;.

## Gruppe löschen {#delete-a-group}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Benutzer und Gruppen&quot;.
1. Wählen Sie in der Liste &quot;Suchen&quot;die Option &quot;Gruppen&quot;aus und klicken Sie auf &quot;Suchen&quot;.
1. Aktivieren Sie das Kontrollkästchen der zu löschenden Gruppe, klicken Sie auf &quot;Löschen&quot;und anschließend auf &quot;OK&quot;.
