---
title: Zeichnen Sie eine Transaktion für die benutzerdefinierte Komponenten-API für AEM Forms on JEE auf.
description: Verwenden Sie die TransactionRecorder-API, um Transaktionen für benutzerdefinierte Komponenten aufzuzeichnen.
feature: Transaction Reports
source-git-commit: d0db00de6b767a12a9492bbbcec49a8c5d25ff27
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Eine Transaktion für benutzerdefinierte Komponenten-APIs für AEM Forms on JEE aufzeichnen {#record-a-transaction-for-custom-components}

Wenn Sie abrechnungsfähige APIs in Ihrer benutzerdefinierten Komponente verwenden, können Sie die Transaktionsberichterstellung für die Komponente aktivieren. Um Transaktionsberichte zu aktivieren, ändern Sie die `component.xml` -Datei der Komponente hinzufügen und das unten angegebene Tag unter dem -Vorgang hinzufügen, für den die Transaktionsberichterstellung aktiviert werden muss.

**Tag**: `<transaction-operation-type>CONVERT</transaction-operation-type> // Supported values are SUBMIT, CONVERT, RENDER.`

| Alter operation tag | Neues Vorgangstag |
| ----------- | ----------- |
| `<operation>`<br> `<.... tags`<br>`<...>`<br>`<operation>` | `<operation>`<br> `<.... tags`<br>`<...>`<br>`<transaction-operation-type>CONVERT</transaction-operation-type`<br>`<operation>` |

Wenn es beispielsweise erforderlich ist, mehr als eine Transaktion für eine API zu erfassen, müssen Sie in diesen Fällen die Transaktionsanzahl auf API-Ebene verarbeiten, wenn die Transaktionsanzahl von der Anzahl der Eingangszahlen abweichen kann. Im Folgenden finden Sie die Schritte zum Aufzeichnen der unterschiedlichen Transaktionsanzahl:

1. Importklasse `"com.adobe.idp.dsc.InvocationContextStack"` im Code. Die Klasse ist Teil der `adobe-livecycle-client.jar` SDK-Datei. Die SDK-Datei ist verfügbar unter `<AEM_Forms_JEE_Install>\sdk\client-libs\common`

   >[!NOTE]
   > Aktualisieren Sie die oben in Ihrem Clientprojekt freigegebene Clientdatei mit der neuen Datei, falls sie bereits gebündelt ist.

1. In der API, für die verschiedene Transaktionen protokolliert werden müssen:
   1. Fügen Sie eine Logik hinzu, um die Transaktionsanzahl in einer Integer-Variablen zu speichern, z. B. `transaction_count`.
   1. Wenn der Vorgang erfolgreich ist, fügen Sie `InvocationContextStack.recordTransactionCount(transaction_count)`.

<!--For example, you can set count for your custom component by importing class `"com.adobe.idp.dsc.InvocationContextStack"` in the code available at `adobe-livecycle-client.jar`  and determine the transaction count basis API input/result and add (In this case we add count is equal to 3):
`InvocationContextStack.recordTransactionCount(<count>).` to 
`InvocationContextStack.recordTransactionCount(3)`.-->

## Ähnliche Artikel

* [Aktivieren und Anzeigen des Transaktionsberichts für AEM Forms on JEE](/help/forms/using/transaction-report-overview-jee.md)
* [Liste der abrechnungsfähigen APIs für AEM Forms on JEE](/help/forms/using/transaction-reports-billable-apis-jee.md)


