---
title: Aufzeichnen einer Transaktion für benutzerdefinierte Komponenten-APIs für AEM Forms auf JEE.
description: Erfahren Sie mehr über die Verwendung der TransactionRecorder-API zum Aufzeichnen von Transaktionen für benutzerdefinierte Komponenten.
feature: Transaction Reports
exl-id: 33e1868a-2a7f-4785-8571-95651e661e21
role: Admin, User, Developer
solution: "Experience Manager, Experience Manager Forms"
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: ht
source-wordcount: '218'
ht-degree: 100%

---

# Aufzeichnen einer Transaktion für benutzerdefinierte Komponenten-APIs für AEM Forms on JEE {#record-a-transaction-for-custom-components}

Wenn Sie in Ihrer benutzerdefinierten Komponente kostenpflichtige APIs verwenden, können Sie die Transaktionsberichterstattung für die Komponente aktivieren. Um Transaktionsberichte zu aktivieren, ändern Sie die Datei `component.xml` der Komponente und fügen Sie das Tag hinzu, das unten unter dem Vorgang angegeben ist, für den Transaktionsberichte aktiviert werden müssen.

**Tag**: `<transaction-operation-type>CONVERT</transaction-operation-type> // Supported values are SUBMIT, CONVERT, RENDER.`

| Altes Tag für Vorgänge | Neues Tag für Vorgänge |
| ----------- | ----------- |
| `<operation>`<br> `<.... tags`<br>`<...>`<br>`<operation>` | `<operation>`<br> `<.... tags`<br>`<...>`<br>`<transaction-operation-type>CONVERT</transaction-operation-type`<br>`<operation>` |

Wenn Sie für eine API mehr als eine Transaktion erfassen müssen, z. B. bei einer Batch-API, bei der die Anzahl der Transaktionen je nach Anzahl der Eingaben variiert, verwalten Sie die Transaktionsanzahl auf API-Ebene.

**So zeichnen Sie die veränderte Transaktionsanzahl auf:**

1. Importieren Sie die Klasse `"com.adobe.idp.dsc.InvocationContextStack"` in den Code. Die Klasse ist Teil der SDK-Datei `adobe-livecycle-client.jar`. Die SDK-Datei ist unter `<AEM_Forms_JEE_Install>\sdk\client-libs\common` verfügbar.

   >[!NOTE]
   > Aktualisieren Sie die oben freigegebene Client-Datei in Ihrem Client-Projekt mit der neuen Datei, falls diese bereits gebündelt ist.

1. Tun Sie Folgendes in der API, für die verschiedene Transaktionen protokolliert werden müssen:
   1. Fügen Sie eine Logik hinzu, um die Transaktionsanzahl in einer Ganzzahlvariablen speichern zu können, z. B. `transaction_count`.
   1. Wenn der Vorgang erfolgreich ist, fügen Sie `InvocationContextStack.recordTransactionCount(transaction_count)` hinzu.

<!--For example, you can set count for your custom component by importing class `"com.adobe.idp.dsc.InvocationContextStack"` in the code available at `adobe-livecycle-client.jar`  and determine the transaction count basis API input/result and add (In this case we add count is equal to 3):
`InvocationContextStack.recordTransactionCount(<count>).` to 
`InvocationContextStack.recordTransactionCount(3)`.-->

## Verwandte Artikel

* [Aktivieren und Anzeigen von Transaktionsberichten für AEM Forms on JEE](/help/forms/using/transaction-report-overview-jee.md)
* [Liste der kostenpflichtigen APIs für AEM Forms on JEE](/help/forms/using/transaction-reports-billable-apis-jee.md)
