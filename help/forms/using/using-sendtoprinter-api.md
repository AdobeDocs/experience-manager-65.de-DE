---
title: Verwenden der SendToPrinter-API
description: Verwenden des sendToPrinter-Dienstes zum Senden eines Dokuments an den Drucker.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
feature: Document Services
exl-id: 585d4053-1056-4d2b-a9df-9516775afe50
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 62%

---

# Verwenden der SendToPrinter-API {#using-the-sendtoprinter-api}

## Übersicht {#overview}

Sie können in AEM Forms den sendToPrinter-Dienst verwenden, um ein Dokument an den Drucker zu senden. Der SendToPrinter-Dienst unterstützt die folgenden Druckerzugriffsmechanismen:

* **Drucker mit direktem Zugriff** `: A printer that is installed on the same computer is called a direct accessible printer, and the computer is named printer host. This type of printer can be a local printer that is connected to the computer directly.`

* **Drucker mit indirektem Zugriff** `: The printer that is installed on a print server is accessed from other computers. Technologies such as the common UNIX® printing system (CUPS) and the Line Printer Daemon (LPD) protocol are available to connect to a network printer. To access an indirect accessible printer, specify the print server’s IP or host name. Using this mechanism, you can send a document to an LPD URI when the network has an LPD running. The mechanism lets you route the document to any printer that is connected to the network that has an LPD running.`

  Geben Sie eines der folgenden Druckprotokolle an, wenn Sie ein Dokument an einen Drucker senden:

   * **CUPS** `: A printing protocol named common UNIX printing system. This protocol is used for UNIX operating systems and enables a computer to function as a print server. The print server accepts print requests from client applications, processes them, and sends them to configured printers. On the IBM AIX® operating system, usage of CUPS is not recommended.`
   * ``**DirectIP** `: A standard protocol for remote printing and managing print jobs. This protocol can be used locally or remotely. Print queues are not required.`
   * ``**LPD** `: A printing protocol named Line Printer Daemon protocol or Line Printer Remote (LPR) protocol. This protocol provides network print server functionality for UNIX-based systems.`
   * **SharedPrinter** `: A printing protocol that enables a computer to use a printer that is configured for that computer.`
   * **CIFS**: Der Output-Service unterstützt das CIFS-Druckprotokoll (Common Internet File System).

## Verwenden des SendToPrinter-Dienstes {#using-sendtoprinter-service}

In der folgenden Tabelle ist aufgeführt:

* Informationen zu printerName oder printServer, die für verschiedene Protokolle verwendet werden sollen.
* Wert oder Ausnahme, die ein Drucker für verschiedene Kombinationen von Drucker-Server-URI und Name des Druckers zurückgibt

| Protokoll (Zugriffsmechanismus) | Druckserver-URI (PrinterSpec.printServer) | Name des Druckers (PrinterSpec.printerName) | Ergebnis |
|--- |--- |--- |--- |
| SharedPrinter | Alle | Leer | Ausnahme: Das erforderliche Argument sPrinterName darf nicht leer sein. |
| SharedPrinter | Alle | Ungültig | Ausnahmefehler, der besagt, dass der Drucker nicht gefunden werden kann. |
| SharedPrinter | Alle | Valid | Erfolgreicher Druckauftrag. |
| LPD | Leer | Alle | ein Ausnahmefehler, der besagt, dass das erforderliche sPrintServerUri-Argument nicht leer sein darf. |
| LPD | Ungültig | Leer | Ausnahmefehler, der besagt, dass das erforderliche sPrinterName-Argument nicht leer sein darf. |
| LPD | Ungültig | Nicht leer | Ausnahmefehler, der besagt, dass sPrintServerUri nicht gefunden wurde. |
| LPD | Valid | Ungültig | Ausnahmefehler, der besagt, dass der Drucker nicht gefunden werden kann. |
| LPD | Valid | Valid | Ein erfolgreicher Druckauftrag. |
| CUPS | Leer | Alle | ein Ausnahmefehler, der besagt, dass das erforderliche sPrintServerUri-Argument nicht leer sein darf. |
| CUPS | Ungültig | Alle | Ausnahmefehler, der besagt, dass der Drucker nicht gefunden werden kann. |
| CUPS | Valid | Alle | Erfolgreicher Druckauftrag. |
| DirectIP | Leer | Alle | ein Ausnahmefehler, der besagt, dass das erforderliche sPrintServerUri-Argument nicht leer sein darf. |
| DirectIP | Ungültig | Alle | Ausnahmefehler, der besagt, dass der Drucker nicht gefunden werden kann. |
| DirectIP | Valid | Alle | Erfolgreicher Druckauftrag. |
| CIFS | Valid | Leer | Erfolgreicher Druckauftrag. |
| CIFS | Ungültig | Alle | unbekannter Fehler beim Drucken mit CIF. |
| CIFS | Leer | Alle | ein Ausnahmefehler, der besagt, dass das erforderliche sPrintServerUri-Argument nicht leer sein darf. |

## Authentifizierungsunterstützung {#authentication-support}

Authentifizierung wird nur für CIF Drucken unterstützt. Geben Sie zur Authentifizierung in PrinterSpec Benutzername/Kennwort/Domain ein. Sie können ein Kennwort mit AEM Granite CyprtoSupport Service verschlüsseln, indem Sie die folgenden Schritte ausführen:

1. Wechseln Sie zu https://&lt;server>:&lt;port>/system/console.

1. Rufen Sie **[!UICONTROL Main]** > **[!UICONTROL Crypto Support]** auf.

1. Geben Sie Nur-Text ein und klicken Sie auf **[!UICONTROL Schützen]**.
