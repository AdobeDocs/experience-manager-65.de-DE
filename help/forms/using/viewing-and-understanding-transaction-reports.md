---
title: Anzeigen und Verstehen von Transaktionsberichten
description: Verwenden Sie Transaktionsberichte, um eine fundierte Entscheidung über die Produktnutzung zu treffen und Investitionen in Hardware und Software neu auszurichten.
topic-tags: forms-manager
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Transaction Reports
exl-id: 3c7cbe1f-ac81-4df9-96b2-662cbc5f2075
source-git-commit: 744cfcee691ea71f33cd56509f65d4f640d4c6e3
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 100%

---

# Anzeigen und Verstehen von Transaktionsberichten{#viewing-and-understanding-transaction-reports}

Mit Transaktionsberichten können Sie die Anzahl der übermittelten Formulare, verarbeiteten Dokumente und gerenderten Dokumente erfassen und nachverfolgen. Das Ziel bei der Verfolgung dieser Transaktionen ist es, eine fundierte Entscheidung über die Produktnutzung und die Neugewichtung der Investitionen in Hardware und Software treffen zu können. Weitere Informationen finden Sie unter [Übersicht über AEM Forms-Transaktionsberichte](../../forms/using/transaction-reports-overview.md).

## Transaktionsberichte einrichten  {#setting-up-transaction-reports}

Die Funktion Transaktionsberichte ist als Teil des Zusatzpakets für AEM Forms verfügbar. Informationen zur Installation des Zusatzpakets auf allen Autoren- und Veröffentlichungsinstanzen finden Sie unter [Installieren und Konfigurieren von AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md). Nachdem Sie das AEM Forms Add-On-Paket installiert haben, führen Sie die folgenden Schritte aus:

* Aktivieren Sie die Rückwärtsreplikation auf allen Veröffentlichungsinstanzen.
* Transaktionsberichte aktivieren
* Berechtigungen zum Anzeigen eines Transaktionsberichts bereitstellen
* (Optional) Konfigurieren des Flush-Zeitraums und der Postausgänge für Transaktionen [](/help/forms/using/installing-configuring-aem-forms-osgi.md)

>[!NOTE]
>
>* AEM Forms-Transaktionsberichte unterstützen keine Topologien, die nur Veröffentlichungsinstanzen enthalten.
>* Bevor Sie Transaktionsberichte verwenden, stellen Sie sicher, dass die Rückwärtsreplikation für alle Veröffentlichungsinstanzen aktiviert ist.
>* Transaktionsdaten werden von einer Veröffentlichungsinstanz in nur die entsprechende Autoren- oder Verarbeitungsinstanz rückwärts repliziert. Die Autoren- oder Verarbeitungsinstanz kann keine Daten in einer anderen Instanz weiter replizieren.
>

### Aktivieren Sie die Rückwärtsreplikation auf allen Veröffentlichungsinstanzen. {#enable-reverse-replication-on-all-the-publish-instances}

Transaktionsberichte verwenden die Rückwärtsreplikation, um die Anzahl der Transaktionen von Veröffentlichungsinstanzen zu Autoreninstanzen zu konsolidieren. Richten Sie die Rückwärtsreplikation auf allen Veröffentlichungsinstanzen ein. Detaillierte Anweisungen zum Einrichten der Rückwärtsreplikation finden Sie unter [Replikation](/help/sites-deploying/replication.md).

### Transaktionsberichte aktivieren {#enable-transaction-reports}

Transaktionsberichte sind standardmäßig deaktiviert. Sie können die Berichte über AEM Web-Konsole aktivieren. Um Transaktionsberichte in einer AEM Forms-Umgebung zu aktivieren, führen Sie die folgenden Schritte für alle Autoren- und Veröffentlichungsinstanzen aus:

1. Melden Sie sich bei Ihrer AEM-Instanz als Administrator an. Gehen Sie zu **Tools** > **Operationen** > **Web-Konsole**.
1. Suchen und öffnen Sie die **Forms-Transaktionsberichte** Dienst.
1. Aktivieren Sie das Kontrollkästchen „Transaktionen aufzeichnen“. Klicken Sie auf **Speichern**.

   Wiederholen Sie Schritte 1-3 für alle Autor- und Veröffentlichungsinstanzen.

### Berechtigungen zum Anzeigen eines Transaktionsberichts bereitstellen {#provide-rights-to-view-a-transaction-report}

Nur Mitglieder der Gruppe fd-administrator können Transaktionsberichte anzeigen. Damit Benutzer Transaktionsberichte einsehen können, müssen sie Mitglied der Gruppe fd-administrator sein. Anweisungen, wie Sie einen Benutzer zum Mitglied einer AEM-Gruppe machen, finden Sie unter [Verwaltung von Benutzern, Gruppen und Zugriffsrechten](/help/sites-administering/user-group-ac-admin.md).

### (Optional) Konfigurieren des Flush-Zeitraums und der Postausgänge für Transaktionen {#optional-configure-transaction-flush-period-and-outboxes}

Transaktionen werden im Speicher zwischengespeichert, bevor sie im Repository gespeichert werden. Der Prozess wird ausgeführt, um sicherzustellen, dass es keine häufigen Schreibvorgänge in das Repository gibt. Standardmäßig ist der Caching-Zeitraum (Transaktions-Flush-Zeitraum) auf 60 Sekunden festgelegt. Sie können den Standardzeitraum an Ihre Umgebung anpassen. Führen Sie die folgenden Schritte aus, um den Standard-Caching-Zeitraum zu ändern:

1. Melden Sie sich bei den Autoreninstanzen als Administrator an. Gehen Sie zu **Tools** > **Operationen** > **Web-Konsole**.
1. Suchen Sie den Dienst **Forms Transaction Repository Storage Provider** und öffnen Sie ihn.
1. Geben Sie die Anzahl der Sekunden im Feld **Transaction Flush Period** an. Klicken Sie auf **Speichern**.

„Rückwärtsreplikation“ kopiert Transaktionsdaten in den standardmäßigen Postausgang der Autoreninstanzen. Sie können Transaktionsdaten in einem benutzerdefinierten Postausgang platzieren. Führen Sie die folgenden Schritte aus, um einen benutzerdefinierten Postausgang anzugeben:

1. Melden Sie sich bei den Autoreninstanzen als Administrator an. Gehen Sie zu **Tools** > **Operationen** > **Web-Konsole**.
1. Suchen Sie den Dienst **Forms Transaction Repository Storage Provider** und öffnen Sie ihn.
1. Geben Sie den Namen des benutzerdefinierten Postausgangs in das Feld **Postausgänge** ein. Klicken Sie auf **Speichern**. Ein Postausgang mit dem angegebenen Namen wird für alle Autoreninstanzen erstellt.

## Anzeigen des Transaktionsberichts {#viewing-the-transaction-report}

Sie können Transaktionsberichte zu Autoren- oder Veröffentlichungsinstanzen anzeigen. Der Transaktionsbericht für die Autoreninstanz liefert eine aggregierte Summe aller Transaktionen, die auf den konfigurierten Autoren- und Veröffentlichungsinstanzen stattfinden. Der Transaktionsbericht für die Veröffentlichungsinstanz liefert eine Zählung der Transaktionen, die nur auf der zugrunde liegenden Veröffentlichungsinstanz stattfinden. Führen Sie die folgenden Schritte aus, um den Bericht anzuzeigen:

1. Melden Sie sich beim AEM Forms-Server unter `https://[hostname]:'port'` an.
1. Navigieren Sie zu **Tools** > **Forms** > **Transaktionsbericht anzeigen**.

## Erläuterungen zum Bericht {#understanding-the-report}

AEM Forms zeigt Transaktionsberichte seit dem konfigurierten Datum an, wie in einem zusammenfassenden Bericht unten gezeigt:

![sample-transaction-report-author](assets/sample-transaction-report-author.png)

* Verwenden Sie die Optionen **Datum auf heute zurücksetzen** zum Zurücksetzen von Transaktionsdatensätzen. Wenn Sie das Datum auf heute zurücksetzen, gehen alle vorherigen Transaktionsdatensätze verloren. Wenn Sie das Datum auf einer Autoreninstanz zurücksetzen, wirkt sich die Änderung nicht auf die Transaktionsberichte auf den Veröffentlichungsinstanzen aus und umgekehrt.
* Verwenden Sie die **Anzeigen von Transaktionen nur von Veröffentlichungsinstanzen** um alle Transaktionen anzuzeigen, die nur in der konfigurierten Veröffentlichungsinstanz oder Veröffentlichungsfarm aufgetreten sind.
* Verwenden Sie diese Kategorien: **Dokument verarbeitet**, **Dokumente gesendet** und **Formulare eingereicht**, um die entsprechenden Transaktionen anzuzeigen. Für die Art der Transaktionen, die in diesen Kategorien berücksichtigt werden, siehe [Abrechnungsfähige Transaktionsberichte APIs](../../forms/using/transaction-reports-billable-apis.md).

## Protokolle der Transaktionsberichte ansehen {#view-transaction-reporting-logs}

Bei der Transaktionsberichterstattung werden alle im Bericht angezeigten Informationen und einige zusätzliche Informationen in den Protokollen gespeichert. Die in den Protokollen enthaltenen Informationen sind für fortgeschrittene Benutzer hilfreich. Zum Beispiel unterteilen Protokolle Transaktionen in mehrere granulare Kategorien im Vergleich zu drei konsolidierten Kategorien, die im Bericht angezeigt werden. Die Protokolle sind in der Datei `error.log` im Verzeichnis `/crx-repository/logs/` verfügbar. Die Protokolle sind auch dann verfügbar, wenn Sie die Transaktionsberichte in der AEM Web Console nicht aktivieren.

## Ähnliche Artikel {#related-articles}

* [Übersicht über Transaktionsberichte](../../forms/using/transaction-reports-overview.md)
* [Abrechenbare APIs für Transaktionsberichte](../../forms/using/transaction-reports-billable-apis.md)
* [Aufzeichnen einer Transaktion für benutzerdefinierte Implementierungen](/help/forms/using/record-transaction-custom-implementation.md)
