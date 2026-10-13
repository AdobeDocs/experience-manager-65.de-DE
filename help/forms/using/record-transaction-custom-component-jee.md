---
title: Aufzeichnen einer Transaktion für benutzerdefinierte Komponenten-APIs für AEM Forms auf JEE.
description: Erfahren Sie mehr über die Verwendung der TransactionRecorder-API zum Aufzeichnen von Transaktionen für benutzerdefinierte Komponenten.
feature: Transaction Reports
exl-id: 33e1868a-2a7f-4785-8571-95651e661e21
role: Admin, User, Developer
solution: Experience Manager, Experience Manager Forms
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: bcb3e79d-a57e-59a4-ad50-e03803c9f153
    internal-label: Transaction Reports
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
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

<!--
For example, you can set count for your custom component by importing class `"com.adobe.idp.dsc.InvocationContextStack"` in the code available at `adobe-livecycle-client.jar`  and determine the transaction count basis API input/result and add (In this case we add count is equal to 3):
`InvocationContextStack.recordTransactionCount(<count>).` to 
`InvocationContextStack.recordTransactionCount(3)`.
-->

## Verwandte Artikel

* [Aktivieren und Anzeigen von Transaktionsberichten für AEM Forms on JEE](/help/forms/using/transaction-report-overview-jee.md)
* [Liste der kostenpflichtigen APIs für AEM Forms on JEE](/help/forms/using/transaction-reports-billable-apis-jee.md)
