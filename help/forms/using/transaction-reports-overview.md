---
title: Übersicht über Transaktionsberichte
seo-title: Übersicht über Transaktionsberichte
description: Alle gesendeten Formulare zählen, die wiedergegebene interaktive Kommunikation, Dokumente in ein anderes Format konvertieren und mehr
seo-description: Alle gesendeten Formulare zählen, die wiedergegebene interaktive Kommunikation, Dokumente in ein anderes Format konvertieren und mehr
uuid: 2c3dc1f3-5bbf-4aab-aa84-7aef5aabadf6
topic-tags: forms-manager
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b2c09e6b-a1d8-4b30-af2c-988442a3a986
docset: aem65
translation-type: tm+mt
source-git-commit: 8f90dc4865126d52e04effc9197ef7145b1a167e

---


# Übersicht über Transaktionsberichte{#transaction-reports-overview}

## Einführung {#introduction}

Mit Transaktionsberichten in AEM Forms können Sie alle Transaktionen zählen, die seit einem bestimmten Datum in Ihrer AEM Forms-Bereitstellung stattgefunden haben. Ziel ist es, Informationen über die Nutzung von Produkten bereitzustellen und Interessengruppen dabei zu unterstützen, ihr digitales Verarbeitungsvolumen zu verstehen. Beispiele für eine Transaktion:

* Übermitteln eines adaptiven Formulars, eines HTML5-Formulars oder eines Formularsatzes
* Darstellung eines Drucks oder einer Webversion einer interaktiven Kommunikation
* Konvertierung eines Dokuments von einem Dateiformat in ein anderes

Weitere Informationen zu einer Transaktion finden Sie unter [Billable APIs](../../forms/using/transaction-reports-billable-apis.md).

Die Transaktionsaufzeichnung ist standardmäßig deaktiviert. Sie können die Transaktionsaufzeichnung über die AEM Web Console [aktivieren](../../forms/using/viewing-and-understanding-transaction-reports.md#setting-up-transaction-reports) . Sie können Transaktionsberichte zu Autoren-, Verarbeitungs- oder Veröffentlichungsinstanzen anzeigen. Zeigen Sie Transaktionsberichte zu Autoren- oder Verarbeitungsinstanzen für eine aggregierte Summe aller Transaktionen an. Zeigen Sie Transaktionsberichte zu den Instanzen im Veröffentlichungsmodus für eine Zählung aller Transaktionen an, die nur in der Instanz im Veröffentlichungsmodus stattfinden, von der aus der Bericht ausgeführt wird.

Erstellen Sie keine Inhalte (Erstellen Sie adaptive Formulare, interaktive Kommunikation, Themen und andere Authoring-Aktivitäten) und Prozessdokumente (Verwenden Sie Workflows, Document Services und andere Verarbeitungsaktivitäten) auf derselben AEM-Instanz. Halten Sie die Transaktionsaufzeichnung für AEM Forms-Server, die zum Erstellen von Inhalten verwendet werden, deaktiviert. Lassen Sie die Transaktionsaufzeichnung für AEM Forms-Server aktiviert, die zur Verarbeitung von Dokumenten verwendet werden.

![sample-transaction-report-author-1](assets/sample-transaction-report-author-1.png)

Eine Transaktion bleibt für einen bestimmten Zeitraum im Puffer (Flush-Pufferzeit + Reverse-Replizierungszeit). Standardmäßig dauert es etwa 90 Sekunden, bis die Transaktionsanzahl im Transaktionsbericht angezeigt wird.

Aktionen wie das Senden eines PDF-Formulars, die Verwendung der Agent-Benutzeroberfläche zur Vorschau einer interaktiven Kommunikation oder die Verwendung nicht standardmäßiger Formularübermittlungsmethoden werden nicht als Transaktionen erfasst. AEM Forms bietet eine API zum Aufzeichnen solcher Transaktionen. Rufen Sie die API Ihrer benutzerdefinierten Implementierungen auf, um eine Transaktion aufzuzeichnen.

## Unterstützte Topologie {#supported-topology}

Transaktionsberichte sind nur in AEM Forms on OSGi-Umgebungen verfügbar. Es unterstützt Autoren-, Veröffentlichungs-, Authoring- und Veröffentlichungstopologien sowie ausschließlich Verarbeitungstopologien. For example topologies, see [Architecture and deployment topologies for AEM Forms](../../forms/using/transaction-reports-overview.md).

Die Transaktionsanzahl wird umgekehrt von Veröffentlichungsinstanzen zu Autoren- oder Verarbeitungsinstanzen repliziert. Eine indikative Autor-Veröffentlichungstopologie wird unten angezeigt:

![simple-author-publish-topology](assets/simple-author-publish-topology.png)

>[!NOTE]
>
>AEM Forms-Transaktionsberichte unterstützen keine Topologien, die nur Veröffentlichungsinstanzen enthalten.

### Richtlinien für die Verwendung von Transaktionsberichten {#guidelines-for-using-transaction-reports}

* Deaktivieren Sie Transaktionsberichte für alle Instanzen im Autorenmodus, da Berichte zu Instanzen im Autorenmodus Transaktionen enthalten, die während der Bearbeitung registriert wurden.
* Aktivieren Sie die Option &quot;Nur **Veröffentlichung** anzeigen&quot;in der Autoreninstanz, um kumulative Transaktionen aus allen Veröffentlichungsinstanzen anzuzeigen. Sie können auch Transaktionsberichte für jede Instanz im Veröffentlichungsmodus nur für die Transaktionen in dieser bestimmten Veröffentlichungsinstanz anzeigen.
* Verwenden Sie keine Autoreninstanzen, um Workflows auszuführen und Dokumente zu verarbeiten.
* Wenn Sie über eine Toplogie mit Veröffentlichungsservern verfügen, stellen Sie vor der Verwendung der Transaktionsberichte sicher, dass die umgekehrte Replizierung für alle Veröffentlichungsinstanzen aktiviert ist.
* Transaktionsdaten werden von einer Veröffentlichungsinstanz in nur die entsprechende Autoren- oder Verarbeitungsinstanz umgekehrt repliziert. Der Autor oder die Verarbeitungsinstanz können Daten nicht weiter in eine andere Instanz replizieren. Wenn Sie z. B. über eine Topologie zum Verarbeiten des Autors und Veröffentlichen verfügen, werden aggregierte Transaktionsdaten nur in die Verarbeitungsinstanz repliziert.

## Related Articles {#related-articles}

* [Anzeigen und Verstehen von Transaktionsberichten](../../forms/using/viewing-and-understanding-transaction-reports.md)
* [Transaktionsberichte Abrechnungsfähige APIs](../../forms/using/transaction-reports-billable-apis.md)
* [Eine Transaktion für benutzerdefinierte Implementierungen aufzeichnen](/help/forms/using/record-transaction-custom-implementation.md)

