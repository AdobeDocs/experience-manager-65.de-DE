---
title: Übersicht über Transaktionsberichte
description: Zählen aller übermittelten Formulare, wiedergegebenen interaktiven Kommunikationen, in ein anderes Format konvertierten Dokumente usw.
topic-tags: forms-manager
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Transaction Reports
exl-id: bb812614-f4d8-4f57-bea2-8f7d31457039
source-git-commit: 744cfcee691ea71f33cd56509f65d4f640d4c6e3
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 98%

---

# Übersicht über Transaktionsberichte{#transaction-reports-overview}

## Einführung {#introduction}

Mit Transaktionsberichten in AEM Forms können Sie alle Transaktionen zählen, die seit einem bestimmten Datum in Ihrer AEM Forms-Bereitstellung stattgefunden haben. Ziel ist es, Informationen über die Produktnutzung bereitzustellen und den Interessengruppen in Unternehmen dabei zu helfen, ihre digitalen Verarbeitungsvolumen zu verstehen. Beispiele für eine Transaktion sind:

* Übermittlung eines adaptiven Formulars, eines HTML5-Formulars oder eines Formularsatzes
* Ausgabe einer Druck- oder Web-Version einer interaktiven Kommunikation
* Konvertieren eines Dokuments aus einem Dateiformat in ein anderes

Weitere Informationen darüber, was als Transaktion gilt, finden Sie unter [Abrechnungsfähige APIs](../../forms/using/transaction-reports-billable-apis.md).

Die Transaktionsaufzeichnung ist standardmäßig deaktiviert. Sie können von der AEM-Web-Konsole aus die [Transaktionserfassung aktivieren](../../forms/using/viewing-and-understanding-transaction-reports.md#setting-up-transaction-reports). Sie können Transaktionsberichte zu Autoren-, Verarbeitungs- oder Veröffentlichungsinstanzen anzeigen. Zeigen Sie Transaktionsberichte zu Autoren- oder Verarbeitungsinstanzen für eine aggregierte Summe aller Transaktionen an. Zeigen Sie Transaktionsberichte zu den Veröffentlichungsinstanzen für eine Zählung aller Transaktionen an, die nur auf derjenigen Veröffentlichungsinstanz stattfinden, von der aus der Bericht ausgeführt wird.

Sie sollten nicht auf der gleichen AEM-Instanz Inhalte erstellen (Erstellen von adaptiven Formularen, interaktive Kommunikation, Designs und andere Authoring-Aktivitäten) und Dokumente verarbeiten (Verwenden von Workflows, Dokumenten-Services und andere Verarbeitungsaktivitäten). Halten Sie die Transaktionsaufzeichnung für AEM Forms-Server, die zum Erstellen von Inhalten verwendet werden, deaktiviert. Lassen Sie dagegen die Transaktionsaufzeichnung für AEM Forms-Server aktiviert, die zur Verarbeitung von Dokumenten verwendet werden.

![sample-transaction-report-author-1](assets/sample-transaction-report-author-1.png)

Eine Transaktion verbleibt für einen bestimmten Zeitraum im Puffer (Leerlauf-Pufferzeit + Rückwärtsreplikationszeit). Standardmäßig dauert es ungefähr 90 Sekunden, bis die Anzahl der Transaktionen im Transaktionsbericht angezeigt wird.

Aktionen wie das Senden eines PDF-Formulars, die Verwendung der Agent-Benutzeroberfläche zur Vorschau einer interaktiven Kommunikation oder die Verwendung nicht standardmäßiger Methoden zur Formularübermittlung werden nicht als Transaktionen gezählt. AEM Forms bietet eine API zum Aufzeichnen solcher Transaktionen. Rufen Sie die API aus Ihren benutzerdefinierten Implementierungen auf, um eine Transaktion aufzuzeichnen.

## Unterstützte Topologie {#supported-topology}

Transaktionsberichte sind nur in AEM Forms in der OSGi-Umgebung verfügbar. Es unterstützt die Topologien „Autor-Veröffentlichen“, „Autor-Verarbeiten-Veröffentlichen“ und „Nur Verarbeiten“. Zum Beispiel Topologien, siehe [Architektur und Bereitstellungstopologien für AEM Forms](../../forms/using/transaction-reports-overview.md).

Die Anzahl der Transaktionen wird von Veröffentlichungsinstanzen zu Autoren- oder Verarbeitungsinstanzen umgekehrt repliziert. Unten finden Sie eine Beispieltopologie für „Autor-Veröffentlichen“:

![simple-author-publish-topology](assets/simple-author-publish-topology.png)

>[!NOTE]
>
>AEM Forms-Transaktionsberichte unterstützen keine Topologien, die nur Veröffentlichungsinstanzen enthalten.

### Richtlinien für die Verwendung von Transaktionsberichten {#guidelines-for-using-transaction-reports}

* Deaktivieren Sie Transaktionsberichte für alle Autoreninstanzen, da Berichte zu Autoreninstanzen die während der Bearbeitung registrierten Transaktionen enthalten.
* Aktivieren Sie die Option **Nur Transaktionen aus der Veröffentlichung anzeigen** auf der Autoreninstanz, um kumulative Transaktionen aus allen Veröffentlichungsinstanzen anzuzeigen. Sie können auch wählen, Transaktionsberichte für jede Veröffentlichungsinstanz nur für tatsächliche Transaktionen in dieser Veröffentlichungsinstanz anzuzeigen.
* Verwenden Sie keine Autoreninstanzen, um Workflows auszuführen und Dokumente zu verarbeiten.
* Stellen Sie vor der Verwendung von Transaktionsberichten sicher, dass die Rückwärtsreplikation für alle Veröffentlichungsinstanzen aktiviert ist, wenn Sie eine Topologie mit Veröffentlichungs-Servern haben.
* Transaktionsdaten werden von einer Veröffentlichungsinstanz in nur die entsprechende Autoren- oder Verarbeitungsinstanz rückwärts repliziert. Die Autoren- oder Verarbeitungsinstanz kann keine Daten in einer anderen Instanz weiter replizieren. Wenn Sie beispielsweise über die Topologie „Autor-Verarbeiten-Veröffentlichen“ verfügen, werden aggregierte Transaktionsdaten nur auf die Verarbeitungsinstanz repliziert.

## Ähnliche Artikel {#related-articles}

* [Anzeigen und Verstehen von Transaktionsberichten](../../forms/using/viewing-and-understanding-transaction-reports.md)
* [Abrechenbare APIs für Transaktionsberichte](../../forms/using/transaction-reports-billable-apis.md)
* [Aufzeichnen einer Transaktion für benutzerdefinierte Implementierungen](/help/forms/using/record-transaction-custom-implementation.md)
