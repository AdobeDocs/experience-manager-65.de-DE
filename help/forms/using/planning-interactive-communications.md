---
title: "Tutorial: Interaktive Kommunikation planen"
description: Planen Sie Ihre interaktive Kommunikation
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Interactive Communication
exl-id: ea0c8971-56f4-4094-87e4-1b222b73951f
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 55%

---

# Tutorial: Planen einer interaktiven Kommunikation {#tutorial-plan-the-interactive-communication}

Planen Sie Ihre interaktive Kommunikation

![02-create-adaptive-form-main-image](assets/02-create-adaptive-form-main-image.png)

Dieses Tutorial ist ein Schritt in der Reihe [Erstellen Sie Ihre erste interaktive Kommunikation](/help/forms/using/create-your-first-interactive-communication.md). Es wird empfohlen, die Serie in chronologischer Reihenfolge zu durchlaufen, um den vollständigen Anwendungsfall des Tutorials zu verstehen, durchzuführen und zu demonstrieren.

Der erste Schritt bei der Planung einer interaktiven Kommunikation besteht darin, den Inhalt der interaktiven Kommunikation fertigzustellen. Fachleute aus Abteilungen wie Rechtsabteilung, Finanzabteilung, Support oder Marketing können Ihnen bei der Fertigstellung des Inhalts helfen. Anschließend müssen Sie den Inhalt analysieren, um die verschiedenen Asset-Typen zu ermitteln, die zum Erstellen der interaktiven Kommunikation erforderlich sind.

## Planen {#planning-considerations}

Eine interaktive Kommunikation umfasst die folgenden Elemente:

* **Statischer Text** umfasst meist die Teile der interaktiven Kommunikation, die allgemein gehalten sind und in die Kommunikation mit allen Kunden einbezogen sind. Zum Beispiel Kopf-, Fußzeile, Anrede oder Haftungsausschlüsse.
* **Daten aus einem Backend-System (Formulardatenmodell)** sind kundenspezifisch und werden dynamisch mit der interaktiven Kommunikation zusammengeführt. Beispielsweise kann die Richtliniennummer oder Adresse mithilfe des Formulardatenmodells bezogen werden.
* **Layout oder Vorlagen** für die Druck- und Webversion der interaktiven Kommunikation.
* **Reihenfolge**, in der die verschiedenen Textabsätze in der interaktiven Kommunikation angezeigt werden.
* **Daten, die von einem Frontline-Mitarbeiter eingegeben wurden (Agent UI)**, der die Kommunikation vor dem Versenden anpasst. Beispielsweise das Fälligkeitsdatum der Zahlung.

* **Bedingte Daten** , der anhand vordefinierter Bedingungen ausgefüllt wird. Beispielsweise das Datum, an dem die interaktive Kommunikation generiert wird.
* **In einem Repository gespeicherte Bilder**, wie Logos und Signaturbilder. Bilder wie Unternehmenslogos würden in den meisten oder in allen interaktiven Kommunikationen angezeigt.
* **Diagramme und Tabellen** zur Vereinfachung der Darstellung komplexer Daten in einer interaktiven Kommunikation erforderlich ist

## Anatomie der interaktiven Kommunikation {#anatomy-of-the-interactive-communication}

Nachdem Sie den Inhalt und die Elemente, die zum Erstellen Ihrer interaktiven Kommunikation verwendet werden, fertig gestellt haben, können Sie eine Anatomie der interaktiven Kommunikation erstellen. Die Details der Anatomie müssen im Abschnitt [Planen von Überlegungen](/help/forms/using/planning-interactive-communications.md#planning-considerations) Abschnitt. Basierend auf unserem Anwendungsfall ist das folgende Beispiel für eine Anatomie der monatlichen Rechnung, die ein Telekommunikationsbetreiber an seine Kunden sendet.

Die Anatomie umfasst Daten mit den folgenden Eingabemodi:

* Statischer Text
* Formulardatenmodell
* Agent-Benutzeroberfläche
* Bedingte Daten
* Bilder

In jedem Abschnitt steht der fettgedruckte Text für statischen Text. Die Datenbank enthält Tabellen für Kunden, Rechnungen und Anrufe. Ein Formulardatenmodell kann Daten aus jeder dieser Tabellen empfangen. Weitere Informationen finden Sie unter [Erstellen des Formulardatenmodells](/help/forms/using/create-form-data-model0.md).

Die folgende Tabelle zeigt die Datenquelle für jedes Feld in der Anatomie der interaktiven Kommunikation:

<table>
 <tbody>
  <tr>
   <td>Abschnitt</td>
   <td>Statischer Text</td>
   <td>FDM </td>
   <td>Agent-Benutzeroberfläche</td>
   <td>Bilder</td>
  </tr>
  <tr>
   <td>Rechnungsdetails</td>
   <td><p>Rechnungsnummer</p> <p>Rechnungsdatum</p> <p>Rechnungszeitraum</p> <p>Ihr Plan</p> </td>
   <td><p>Wert für <strong>Ihr Plan </strong>field</p> <p>Tabelle - Kunde</p> </td>
   <td><p>Werte für die folgenden Felder:</p>
    <ul>
     <li>Rechnungsnummer</li>
     <li>Rechnungsdatum</li>
     <li>Rechnungszeitraum</li>
    </ul> <p> </p> </td>
   <td>--</td>
  </tr>
  <tr>
   <td>Kundendetails</td>
   <td><p>Ort der Lieferung</p> <p>Statuscode</p> <p>Mobilfunknummer</p> <p>Alternative Kontaktnummer</p> <p>Beziehungsnummer</p> <p>Anzahl von Verbindungen</p> </td>
   <td><p>Werte für die folgenden Felder:</p>
    <ul>
     <li>Name</li>
     <li>Adresse</li>
     <li>Mobilfunknummer</li>
     <li>Alternative Kontaktnummer</li>
     <li>Beziehungsnummer</li>
    </ul> <p>Tabelle - Kunde</p> </td>
   <td><p>Werte für die folgenden Felder:</p>
    <ul>
     <li>Ort der Lieferung</li>
     <li>Statuscode</li>
     <li>Anzahl von Verbindungen</li>
    </ul> </td>
   <td>--</td>
  </tr>
  <tr>
   <td>Rechnungsübersicht</td>
   <td><p>Vorheriger Saldo</p> <p>Zahlungen</p> <p>Anpassungen</p> <p>Gebühren des aktuellen Rechnungszeitraums</p> <p>Fälliger Betrag</p> <p>Fälligkeitsdatum</p> </td>
   <td><p>Wert für das Feld <strong>Gebühren des aktuellen Rechnungszeitraums</strong></p> <p>Tabelle - Rechnungen</p> </td>
   <td><p>Werte für die folgenden Felder:</p>
    <ul>
     <li>Vorheriger Saldo</li>
     <li>Zahlungen</li>
     <li>Anpassungen</li>
     <li>Fälliger Betrag</li>
     <li>Fälligkeitsdatum</li>
    </ul> </td>
   <td>--</td>
  </tr>
  <tr>
   <td>Zusammenfassung der Gebühren</td>
   <td><p>Anrufgebühren</p> <p>Gebühren für Telefonkonferenz</p> <p>SMS-Gebühren </p> <p>Mobile Internetgebühren</p> <p>Nationale Roaming-Gebühren</p> <p>Internationale Roaming-Gebühren</p> <p>Mehrwert-Service-Gebühren</p> <p>Gesamtgebühren</p> <p>GESAMT ZAHLBAR</p> <p>Bedingung im Feld „Mehrwert Service-Gebühren“</p> </td>
   <td><p>Werte für die folgenden Felder:</p>
    <ul>
     <li>Anrufgebühren</li>
     <li>Gebühren für Telefonkonferenz</li>
     <li>SMS-Gebühren </li>
     <li>Mobile Internetgebühren</li>
     <li>Nationale Roaming-Gebühren</li>
     <li>Internationale Roaming-Gebühren</li>
     <li>Mehrwert-Service-Gebühren</li>
     <li>Gesamtkosten (Feld für berechnete Benutzergebühren)</li>
     <li>GESAMT ZAHLBAR (Feld für berechnete Nutzungsgebühren)</li>
    </ul> <p>Tabelle - Rechnungen</p> </td>
   <td>Keine Felder</td>
   <td>--</td>
  </tr>
  <tr>
   <td>Aufgezählte Aufrufe - Ausgehend</td>
   <td><p>Spaltennamen:</p>
    <ul>
     <li>Datum</li>
     <li>Zeit</li>
     <li>Zahl</li>
     <li>Dauer</li>
     <li>Gebühren</li>
    </ul> </td>
   <td><p>Alle Werte</p> <p>Tabelle - Aufrufe</p> </td>
   <td>Keine Felder</td>
   <td>--</td>
  </tr>
  <tr>
   <td>Jetzt bezahlen</td>
   <td>--</td>
   <td>--</td>
   <td>--</td>
   <td>JetztBezahlen</td>
  </tr>
  <tr>
   <td>Mehrwert-Services</td>
   <td>--</td>
   <td>--</td>
   <td>--</td>
   <td>MehrwertServices</td>
  </tr>
 </tbody>
</table>
