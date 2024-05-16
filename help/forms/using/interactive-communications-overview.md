---
title: Interaktive Kommunikation - Übersicht
description: Dieser Artikel enthält eine Übersicht, Beispiele für Anwendungsfälle, einen Erstellungs-Workflow und Unterschiede zwischen der interaktiven Kommunikation und dem Brief.
contentOwner: gtalwar
topic-tags: interactive-communications, introduction
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 6cfbeec0-0be3-48b2-a4bb-fd19c69c92c7
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '487'
ht-degree: 100%

---


# Interaktive Kommunikation - Übersicht {#interactive-communications-overview}

Dieser Artikel enthält eine Übersicht, Beispiele für Anwendungsfälle, einen Erstellungs-Workflow und Unterschiede zwischen der interaktiven Kommunikation und dem Brief.

![hero-image](do-not-localize/correspondence-management.png)

Interaktive Kommunikation zentralisiert und verwaltet die Erstellung, Anordnung und Bereitstellung von sicheren, personalisierten und interaktiven Korrespondenzen wie Geschäftskorrespondenz, Dokumente, Kontoauszüge, Mitteilungen über finanzielle Leistungen, Marketing-Mails, Rechnungen und Begrüßungssets.

## Schlüsselfunktionen {#key-capabilities}

Im Folgenden sind die wichtigsten Funktionen von interaktiven Kommunikationen aufgeführt:

- Sofort einsatzbereite Integration mit dem Formulardatenmodell, um einen einfachen und optimierten Zugriff auf Backend-Datenbanken und andere CRM-Systeme wie MS® Dynamics zu ermöglichen
- Integrierte Authoring-Oberfläche für Druck- und Web-Kanäle mit der Möglichkeit, automatisch einen Web-Kanal aus dem Druckkanal zu generieren
- Diagramme zur Darstellung von Informationen in leicht verständlichen visuellen Formaten im Druck- und Web-Format
- Dokumentfragmente unterstützen den Regeleditor und das Formulardatenmodell
- Die Benutzeroberfläche für Agenten zeigt die Druck- und Web-Vorschau der interaktiven Kommunikation.
- Drag-and-Drop-Komponenten zum schnellen Erstellen von Druck- und Webkanälen

## Erstellung einer interaktiven Kommunikation {#interactive-communication-creation}

![interactive_communication-01](assets/interactive_communication-01.jpg)

### Workflow {#workflow}

Um eine Interaktive Kommunikation zu erstellen, sollten Sie die [Bausteine](#buildingblocks) für interaktive Kommunikation vorbereitet haben und dann die folgenden Schritte ausführen:

1. Entscheiden Sie sich zum [Erstellen einer interaktiven Kommunikation](/help/forms/using/create-interactive-communication.md).

1. Geben Sie das [Formulardatenmodell](/help/forms/using/data-integration.md), den Vorbefüllungs-Dienst und die [Druck- und Webkanal-Vorlagen](/help/forms/using/web-channel-print-channel.md) an. Sie können den Webkanal über den Druckkanal generieren.

1. Fügen Sie mit der [Drag &amp; Drop-Beutzeroberfläche](/help/forms/using/introduction-interactive-communication-authoring.md) je nach Bedarf Dokumentfragmente, Bilder, Komponenten zum Druck- und Webkanal der interaktiven Kommunikation hinzu.
1. Konfigurieren Sie die Eigenschaften für die eingefügten Komponenten, z. B. die Folgenden:

   1. [Bilder](/help/forms/using/create-interactive-communication.md#step2)
   1. [Tabellen](/help/forms/using/create-interactive-communication.md#tables) (inklusive Layout-Fragmente)
   1. [Diagramme](/help/forms/using/chart-component-interactive-communications.md)
   1. [Dokumentfragmente](/help/forms/using/create-interactive-communication.md#document-fragment-properties)

1. Zeigen Sie Druck- und Web-Kanäle in der Vorschau an und, falls erforderlich, bearbeiten Sie die interaktive Kommunikation.
1. Der Agent verwendet die Agenten-Benutzeroberfläche, um [die interaktive Kommunikation vorzubereiten](/help/forms/using/prepare-send-interactive-communication.md), um sie an die Empfängerin bzw. den Empfänger oder den Nachbearbeitungsprozess zu senden.

### Bausteine {#buildingblocks}

Im Folgenden sind die Bausteine aufgeführt, die zum Erstellen einer interaktiven Kommunikation erforderlich sind:

- [Formulardatenmodell](/help/forms/using/data-integration.md)
- [Druck- und Webkanal-Vorlagen](/help/forms/using/web-channel-print-channel.md)
- [Dokumentfragmente](/help/forms/using/document-fragments.md)
- Bilder
- [Designs](/help/forms/using/themes.md) für den Web-Kanal

## Interaktive Kommunikation im Vergleich zu Correspondence Management {#interactive-communications-vs-correspondence-management}

Interaktive Kommunikation ist der standardmäßige und empfohlene Ansatz, um Kundenkommunikation zu erstellen. Um die Briefe, die in AEM 6.3 Forms und AEM 6.2 Forms erstellt wurden, weiterhin zu verwenden, müssen Sie ein [Kompatibilitätspaket installieren](/help/forms/using/compatibility-package.md). Es folgt ein Vergleich zwischen den Funktionen von interaktiver Kommunikation und Briefen.

<table>
 <tbody>
  <tr>
   <td><strong>Funktion</strong></td>
   <td><strong>Interaktive Kommunikation</strong></td>
   <td><strong>Brief</strong></td>
  </tr>
  <tr>
   <td>Ausgabe</td>
   <td>Druck und Web</td>
   <td>Druck</td>
  </tr>
  <tr>
   <td>Schema</td>
   <td>Formulardatenmodell </td>
   <td>Datenwörterbuch </td>
  </tr>
  <tr>
   <td>Lokalisierung</td>
   <td>Wird im Formulardatenmodell nicht unterstützt.</td>
   <td>Wird im Datenwörterbuch unterstützt.</td>
  </tr>
  <tr>
   <td>Regeleditor</td>
   <td>
    <ul>
     <li>Regeleditor für Text- und Bedingungsunterstützung zum Erstellen von Inline-Bedingungen</li>
     <li>Der Editor für interaktive Kommunikationen unterstützt die Anwendung von Regeln auf Komponenten des Web-Kanals</li>
    </ul> </td>
   <td>Keine Benutzeroberfläche zum Erstellen eines bedingten Ausdrucks</td>
  </tr>
  <tr>
   <td>Authoring –</td>
   <td>Drag-and-Drop-Schnittstelle zum Erstellen von Druck- und Webkanälen</td>
   <td>Kein Drag-and-Drop-Mechanismus </td>
  </tr>
  <tr>
   <td>Diagramme</td>
   <td>Diagramme werden im Druck- und Web-Kanal unterstützt.</td>
   <td>Nicht unterstützt</td>
  </tr>
  <tr>
   <td>Designs</td>
   <td>Verwendet Themen zur Gestaltung des Web-Kanals.</td>
   <td>Themen werden nicht unterstützt.</td>
  </tr>
   <tr>
   <td>Entwürfe</td>
   <td>Unterstützt</td>
   <td>Unterstützt </td>
  </tr>
   <tr>
   <td>Übermittlungen</td>
   <td>Unterstützt</td>
   <td>Unterstützt </td>
  </tr>
  <tr>
  <tr>
   <td>Prüfung</td>
   <td>Nicht unterstützt</td>
   <td>Unterstützt</td>
  </tr>
   <tr>
   <td>Versionierung</td>
   <td>Nicht unterstützt</td>
   <td>Unterstützt</td>
  </tr>
   <td>Batch-Verarbeitung</td>
   <td>Unterstützt </td>
   <td>Unterstützt </td>
  </tr>
  <tr>
   <td>Agentsignatur</td>
   <td>Nicht unterstützt</td>
   <td>Unterstützt</td>
  </tr>
  <tr>
   <td>Remote-Funktionen</td>
   <td>Nicht unterstützt</td>
   <td>Unterstützt</td>
  </tr>
 </tbody>
</table>
