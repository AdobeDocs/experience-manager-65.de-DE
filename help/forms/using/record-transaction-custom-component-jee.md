---
title: Zeichnen Sie eine Transaktion für die benutzerdefinierte Komponenten-API für AEM Forms on JEE auf.
description: Erfahren Sie mehr über die Verwendung der TransactionRecorder-API zum Aufzeichnen von Transaktionen für benutzerdefinierte Komponenten.
feature: Transaction Reports
exl-id: 33e1868a-2a7f-4785-8571-95651e661e21
role: Admin, User, Developer
solution: "Experience Manager, Experience Manager Forms"
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 5%

---

# Eine Transaktion für benutzerdefinierte Komponenten-APIs für AEM Forms on JEE aufzeichnen {#record-a-transaction-for-custom-components}

Wenn Sie abrechnungsfähige APIs in Ihrer benutzerdefinierten Komponente verwenden, können Sie Transaktionsberichte für die Komponente aktivieren. Um Transaktionsberichte zu aktivieren, ändern Sie die Datei `component.xml` der Komponente und fügen Sie das Tag hinzu, das unten unter dem Vorgang angegeben ist, für den Transaktionsberichte aktiviert werden müssen.

**Tag**: `<transaction-operation-type>CONVERT</transaction-operation-type> // Supported values are SUBMIT, CONVERT, RENDER.`

| Alter operation tag | Neues Vorgangstag |
| ----------- | ----------- |
| `<operation>`<br> `<.... tags`<br>`<...>`<br>`<operation>` | `<operation>`<br> `<.... tags`<br>`<...>`<br>`<transaction-operation-type>CONVERT</transaction-operation-type`<br>`<operation>` |

Wenn Sie mehr als eine Transaktion für eine API erfassen müssen, z. B. eine Batch-API, bei der die Transaktionsanzahl mit der Anzahl der Eingangszahlen variiert, verwalten Sie die Transaktionsanzahl auf API-Ebene.

**So zeichnen Sie die veränderte Transaktionsanzahl auf:**

1. Import class `"com.adobe.idp.dsc.InvocationContextStack"` im Code. Die Klasse ist Teil der SDK-Datei `adobe-livecycle-client.jar`. Die SDK-Datei ist unter `<AEM_Forms_JEE_Install>\sdk\client-libs\common` verfügbar.

   >[!NOTE]
   > Aktualisieren Sie die oben in Ihrem Clientprojekt freigegebene Clientdatei mit der neuen Datei, falls sie bereits gebündelt ist.

1. In der API, für die verschiedene Transaktionen protokolliert werden müssen:
   1. Fügen Sie eine Logik hinzu, damit Sie die Transaktionsanzahl in einer Integer-Variablen speichern können, z. B. `transaction_count`.
   1. Wenn der Vorgang erfolgreich ist, fügen Sie `InvocationContextStack.recordTransactionCount(transaction_count)` hinzu.

<!--For example, you can set count for your custom component by importing class `"com.adobe.idp.dsc.InvocationContextStack"` in the code available at `adobe-livecycle-client.jar`  and determine the transaction count basis API input/result and add (In this case we add count is equal to 3):
`InvocationContextStack.recordTransactionCount(<count>).` to 
`InvocationContextStack.recordTransactionCount(3)`.-->

## Ähnliche Artikel

* [Aktivieren und Anzeigen von Transaktionsberichten für AEM Forms on JEE](/help/forms/using/transaction-report-overview-jee.md)
* [Liste der kostenpflichtigen APIs für AEM Forms auf JEE](/help/forms/using/transaction-reports-billable-apis-jee.md)
