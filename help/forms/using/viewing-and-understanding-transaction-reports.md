---
title: Anzeigen und Verstehen von Transaktionsberichten
seo-title: Anzeigen und Verstehen von Transaktionsberichten
description: Verwenden Sie Transaktionsberichte, um eine fundierte Entscheidung über die Produktverwendung zu treffen und Investitionen in Hardware und Software neu auszurichten.
seo-description: Verwenden Sie Transaktionsberichte, um eine fundierte Entscheidung über die Produktverwendung zu treffen und Investitionen in Hardware und Software neu auszurichten.
uuid: 56d9f01d-4778-47c9-bbb2-6650a73a3f59
topic-tags: forms-manager
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: c04c488b-73f3-49ba-9e89-f97497965757
docset: aem65
translation-type: tm+mt
source-git-commit: 8f90dc4865126d52e04effc9197ef7145b1a167e

---


# Anzeigen und Verstehen von Transaktionsberichten{#viewing-and-understanding-transaction-reports}

Mit Transaktionsberichten können Sie die Anzahl der gesendeten Formulare, verarbeiteten Dokumente und gerenderten Dokumente erfassen und verfolgen. Das Ziel bei der Verfolgung dieser Transaktionen besteht darin, eine fundierte Entscheidung über die Produktverwendung zu treffen und Investitionen in Hardware und Software neu auszurichten. Weitere Informationen finden Sie unter Übersicht über [AEM Forms-Transaktionsberichte](../../forms/using/transaction-reports-overview.md).

## Transaktionsberichte einrichten {#setting-up-transaction-reports}

Die Funktion &quot;Transaktionsberichte&quot;ist als Teil des Add-On-Pakets für AEM Forms verfügbar. Informationen zum Installieren des Add-On-Pakets auf allen Autoren- und Veröffentlichungsinstanzen finden Sie unter [Installieren und Konfigurieren von AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md). Nachdem Sie das Add-On-Paket für AEM Forms installiert haben, führen Sie folgende Schritte aus:

* Aktivieren der umgekehrten Replizierung bei allen Instanzen im Veröffentlichungsmodus
* Transaktionsberichte aktivieren
* Rechte zum Anzeigen eines Transaktionsberichts bereitstellen
* (Optional) Konfigurieren des Transaktionsflush-Zeitraums und der Outboxes [](/help/forms/using/installing-configuring-aem-forms-osgi.md)

>[!NOTE]
>
>* AEM Forms-Transaktionsberichte unterstützen keine Topologien, die nur Veröffentlichungsinstanzen enthalten.
>* Bevor Sie Transaktionsberichte verwenden, stellen Sie sicher, dass die umgekehrte Replizierung für alle Veröffentlichungsinstanzen aktiviert ist.
>* Transaktionsdaten werden von einer Veröffentlichungsinstanz in nur die entsprechende Autoren- oder Verarbeitungsinstanz umgekehrt repliziert. Der Autor oder die Verarbeitungsinstanz können Daten nicht weiter in eine andere Instanz replizieren.
>



### Aktivieren der umgekehrten Replizierung bei allen Instanzen im Veröffentlichungsmodus {#enable-reverse-replication-on-all-the-publish-instances}

Transaktionsberichte verwenden die umgekehrte Replizierung, um die Anzahl der Transaktionen von Veröffentlichungsinstanzen zu Autoreninstanzen zu konsolidieren. Richten Sie die umgekehrte Replizierung auf allen Instanzen im Veröffentlichungsmodus ein. Detaillierte Anweisungen zum Einrichten der umgekehrten Replizierung finden Sie unter [Replikation](/help/sites-deploying/replication.md).

### Transaktionsberichte aktivieren {#enable-transaction-reports}

Transaktionsberichte sind standardmäßig deaktiviert. Sie können die Berichte über die AEM Web Console aktivieren. Um Transaktionsberichte in einer AEM Forms-Umgebung zu aktivieren, führen Sie die folgenden Schritte für alle Autoren- und Veröffentlichungsinstanzen aus:

1. Melden Sie sich bei einer AEM-Instanz als Administrator an. Gehen Sie zu **Werkzeuge** > **Vorgänge** > **Web-Konsole**.
1. Suchen und öffnen Sie den **Forms Transaction Reporting** -Dienst.
1. Aktivieren Sie das Kontrollkästchen &quot;Vorgänge aufzeichnen&quot;. Klicken Sie auf **Speichern**.

   Wiederholen Sie die Schritte 1 bis 3 für alle Autoren- und Veröffentlichungsinstanzen.

### Rechte zum Anzeigen eines Transaktionsberichts bereitstellen {#provide-rights-to-view-a-transaction-report}

Nur Mitglieder der Gruppe fd-administrator können Transaktionsberichte anzeigen. Damit ein Benutzer Transaktionsberichte anzeigen kann, müssen Sie die Benutzer zur Gruppe &quot;fd-administrator&quot;machen. Anweisungen zum Erstellen eines Benutzers als Mitglied einer AEM-Gruppe finden Sie unter Verwaltung von [Benutzern, Gruppen und Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md).

### (Optional) Konfigurieren des Transaktionsflush-Zeitraums und der Outboxes {#optional-configure-transaction-flush-period-and-outboxes}

Transaktionen werden im Arbeitsspeicher zwischengespeichert, bevor sie im Repository gespeichert werden. Standardmäßig ist die Cachedauer (Transaktions-Flush-Zeitraum) auf 60 Sekunden eingestellt. Führen Sie die folgenden Schritte aus, um die standardmäßige Cachedauer zu ändern:

1. Melden Sie sich bei Autoreninstanzen als Administrator an. Gehen Sie zu **Werkzeuge** > **Vorgänge** > **Web-Konsole**.
1. Suchen und öffnen Sie den **Forms Transaction Repository Storage Provider-Dienst** .
1. Geben Sie die Anzahl der Sekunden im Feld **Transaktionsflush-Zeitraum** an. Klicken Sie auf **Speichern**.

Reverse Replizierung kopiert Transaktionsdaten in den Standard-Postausgang der Autoreninstanzen. Sie können Transaktionsdaten in einem benutzerdefinierten Postausgang platzieren. Führen Sie die folgenden Schritte aus, um einen benutzerdefinierten Postausgang anzugeben:

1. Melden Sie sich bei Autoreninstanzen als Administrator an. Gehen Sie zu **Werkzeuge** > **Vorgänge** > **Web-Konsole**.
1. Suchen und öffnen Sie den **Forms Transaction Repository Storage Provider-Dienst** .
1. Geben Sie den Namen des benutzerdefinierten Postausgangs im Feld **Postausgänge** an. Klicken Sie auf **Speichern**. In allen Autoreninstanzen wird ein Postausgang mit dem angegebenen Namen erstellt.

## Anzeigen des Transaktionsberichts {#viewing-the-transaction-report}

Sie können Transaktionsberichte zu Autoren- oder Veröffentlichungsinstanzen anzeigen. Der Transaktionsbericht für die Autoreninstanz stellt eine aggregierte Summe aller Transaktionen bereit, die in der konfigurierten Autor- und Veröffentlichungsinstanz stattfinden. Der Transaktionsbericht für die Veröffentlichungsinstanz stellt eine Anzahl von Transaktionen bereit, die nur in der zugrunde liegenden Veröffentlichungsinstanz stattfinden. Führen Sie die folgenden Schritte aus, um den Bericht anzuzeigen:

1. Log in to the AEM Forms server at `https://[hostname]:[port]`.
1. Navigieren Sie zu **Extras** > **Formulare**>**Transaktionsbericht** anzeigen.

## Erläuterungen zum Bericht {#understanding-the-report}

AEM Forms zeigt Transaktionsberichte seit dem konfigurierten Datum an, wie in einem Zusammenfassungsbericht unten dargestellt:

![sample-transaction-report-author](assets/sample-transaction-report-author.png)

* Verwenden Sie zum Zurücksetzen von Transaktionsdatensätzen die Optionen **Datum auf heute** zurücksetzen. Wenn Sie das Datum auf heute zurücksetzen, gehen alle vorherigen Transaktionsdatensätze verloren. Wenn Sie das Datum auf eine Autoreninstanz zurücksetzen, wirkt sich die Änderung nicht auf Transaktionsberichte in den Veröffentlichungsinstanzen und umgekehrt aus.
* Verwenden Sie die Option &quot;Transaktionen **anzeigen&quot;nur für Instanzen** im Veröffentlichungsmodus, um alle Transaktionen anzuzeigen, die nur in der konfigurierten Instanz im Veröffentlichungsmodus oder in der Veröffentlichungsfarm aufgetreten sind.
* Verwenden Sie die Kategorien: **Dokumentverarbeitung**, **gerenderte** Dokumente und übermittelte **Formulare** , um die entsprechenden Transaktionen anzuzeigen. Informationen zum Typ der in diesen Kategorien verbuchten Transaktionen finden Sie unter APIs für [abrechnungsfähige Transaktionsberichte](../../forms/using/transaction-reports-billable-apis.md).

## Anzeigen von Transaktionsprotokollen {#view-transaction-reporting-logs}

Bei der Transaktionsberichterstellung werden alle im Bericht angezeigten Informationen und einige zusätzliche Informationen in den Protokollen abgelegt. Die Informationen in den Protokollen sind für fortgeschrittene Benutzer hilfreich. Protokolle unterteilen beispielsweise Transaktionen in mehrere granulare Kategorien im Vergleich zu drei im Bericht angezeigten konsolidierten Kategorien. Die Protokolle finden Sie unter /crx-quickstart/logs/aem-forms-transaction.log.

## Related Articles {#related-articles}

* [Übersicht über Transaktionsberichte](../../forms/using/transaction-reports-overview.md)
* [Transaktionsberichte Abrechnungsfähige APIs](../../forms/using/transaction-reports-billable-apis.md)
* [Eine Transaktion für benutzerdefinierte Implementierungen aufzeichnen](/help/forms/using/record-transaction-custom-implementation.md)

