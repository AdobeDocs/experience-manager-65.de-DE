---
title: '"Tutorial: Interaktive Kommunikation planen"'
seo-title: Planen Sie Ihre interaktive Kommunikation
description: Planen Sie Ihre interaktive Kommunikation
seo-description: Planen Sie Ihre interaktive Kommunikation
uuid: 1c2b5c5b-c655-4559-8748-3e0b343779c2
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 75b2d424-91d3-45b4-a5d7-fb49ab558582
feature: Interaktive Kommunikation
exl-id: ea0c8971-56f4-4094-87e4-1b222b73951f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 88%

---

# Tutorial: Interaktive Kommunikation planen {#tutorial-plan-the-interactive-communication}

Planen Sie Ihre interaktive Kommunikation

![02-create-adaptive-form-main-image](assets/02-create-adaptive-form-main-image.png)

Dieses Tutorial ist ein Schritt in der Reihe [Erstellen Ihrer ersten interaktiven Kommunikation](/help/forms/using/create-your-first-interactive-communication.md). Es wird empfohlen, der Serie in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall zu verstehen, auszuführen und zu demonstrieren.

Der erste Schritt bei der Planung einer interaktiven Kommunikation besteht darin, den Inhalt der interaktiven Kommunikation abzuschließen. Fachexperten aus Abteilungen wie Recht, Finanzen, Support oder Marketing können Ihnen dabei helfen, die Inhalte zu finalisieren. Nachdem der Inhalt abgeschlossen ist, müssen Sie ihn analysieren, um die verschiedenen Asset-Typen zu ermitteln, die zum Erstellen der interaktiven Kommunikation erforderlich sind.

## Aspekte bei der Planung {#planning-considerations}

Eine interaktive Kommunikation enthält die folgenden Elemente:

* **Statischer Text** umfasst im Wesentlichen die generischen Teile der interaktiven Kommunikation, die in die Kommunikation mit allen Kunden einbezogen werden. Zum Beispiel Kopfzeile, Fußzeile, Anrede oder Haftungsausschluss.
* **Daten aus einem Backend-System (Formulardatenmodell)** sind kundenspezifisch und werden dynamisch mit der interaktiven Kommunikation zusammengeführt. Beispielsweise kann die Richtliniennummer oder Adresse mithilfe eines Formulardatenmodells bezogen werden.
* **Layout oder Vorlagen** für die Print- und Webversion der interaktiven Kommunikation.
* **Reihenfolge**, in der die verschiedenen Textabsätze in der interaktiven Kommunikation angezeigt werden .
* **Daten, die von einem Frontend-Mitarbeiter (Benutzeroberfläche für Agenten) eingegeben wurden, der** die Kommunikation vor dem Versand anpasst. Zum Beispiel das Fälligkeitsdatum der Zahlung.

* **Bedingte Daten**, die basierend auf vordefinierten Bedingungen befüllt werden. Beispielsweise das Datum, an dem die interaktive Kommunikation generiert wird.
* **In einem Repository gespeicherte Bilder** wie Logos und Signaturbilder. Bilder wie das Unternehmenslogo sind in den meisten oder in jeder interaktiven Kommunikation unverändert enthalten.
* **Diagramme und Tabellen** sind erforderlich, um die Darstellung komplexer Daten in einer interaktiven Kommunikation zu vereinfachen

## Anatomie der interaktiven Kommunikation {#anatomy-of-the-interactive-communication}

Nachdem Sie den Inhalt und die Elemente festgelegt haben, die zum Erstellen Ihrer interaktiven Kommunikation verwendet werden, können Sie eine Anatomie der interaktiven Kommunikation erstellen. Die Anatomie muss die Details im Abschnitt [Aspekte bei der Planung](/help/forms/using/planning-interactive-communications.md#planning-considerations) enthalten. Basierend auf unserem Anwendungsfall ist das folgende Beispiel ein Beispiel für eine Anatomie der monatlichen Rechnung, die ein Telekommunikationsbetreiber an seine Kunden sendet.

Die Anatomie enthält Daten mit den folgenden Eingabemodi:

* Statischer Text
* Formulardatenmodell
* Agent-Benutzeroberfläche
* Bedingte Daten
* Bilder

In jedem Abschnitt steht der fettgedruckte Text für statischen Text. Die Datenbank enthält Tabellen für Kunden, Rechnungen und Anrufe. Ein Formulardatenmodell kann Daten aus jeder dieser Tabellen empfangen. Weitere Informationen finden Sie unter [Formulardatenmodell erstellen](/help/forms/using/create-form-data-model0.md).

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
   <td><p>Rechnungsnr.</p> <p>Rechnungsdatum</p> <p>Rechnungszeitraum</p> <p>Ihr Plan</p> </td>
   <td><p>Wert für das Feld <strong>Ihr Plan</strong></p> <p>Tabelle - Kunde</p> </td>
   <td><p>Werte für die folgenden Felder:</p>
    <ul>
     <li>Rechnungsnr.</li>
     <li>Rechnungsdatum</li>
     <li>Rechnungszeitraum</li>
    </ul> <p> </p> </td>
   <td>—</td>
  </tr>
  <tr>
   <td>Kundendetails</td>
   <td><p>Ort der Lieferung</p> <p>Status-Code</p> <p>Mobilfunknummer</p> <p>Alternative Kontaktnummer</p> <p>Verhältnis-Nummer</p> <p>Anzahl von Verbindungen</p> </td>
   <td><p>Werte für die folgenden Felder:</p>
    <ul>
     <li>Name</li>
     <li>Adresse</li>
     <li>Mobilfunknummer</li>
     <li>Alternative Kontaktnummer</li>
     <li>Verhältnis-Nummer</li>
    </ul> <p>Tabelle - Kunde</p> </td>
   <td><p>Werte für die folgenden Felder:</p>
    <ul>
     <li>Ort der Lieferung</li>
     <li>Status-Code</li>
     <li>Anzahl von Verbindungen</li>
    </ul> </td>
   <td>—</td>
  </tr>
  <tr>
   <td>Rechnungszusammenfassung</td>
   <td><p>Vorheriger Saldo</p> <p>Zahlungen</p> <p>Anpassungen</p> <p>Gebühren des aktuellen Rechnungszeitraums</p> <p>Fälliger Betrag</p> <p>Fälligkeitsdatum</p> </td>
   <td><p>Wert für das Feld <strong>Gebühren für den aktuellen Rechnungszeitraum </strong></p> <p>Tabelle - Rechnungen</p> </td>
   <td><p>Werte für die folgenden Felder:</p>
    <ul>
     <li>Vorheriger Saldo</li>
     <li>Zahlungen</li>
     <li>Anpassungen</li>
     <li>Fälliger Betrag</li>
     <li>Fälligkeitsdatum</li>
    </ul> </td>
   <td>—</td>
  </tr>
  <tr>
   <td>Zusammenfassung der Gebühren</td>
   <td><p>Anrufgebühren</p> <p>Gebühren für Telefonkonferenz</p> <p>SMS-Gebühren </p> <p>Mobile Internetgebühren</p> <p>Nationale Roaming-Gebühren</p> <p>Internationale Roaming-Gebühren</p> <p>Mehrwert - Service-Gebühren</p> <p>Gesamgebühren</p> <p>GESAMT ZAHLBAR</p> <p>Bedingung im Feld Mehrwert - Service-Gebühren</p> </td>
   <td><p>Werte für die folgenden Felder:</p>
    <ul>
     <li>Anrufgebühren</li>
     <li>Gebühren für Telefonkonferenz</li>
     <li>SMS-Gebühren </li>
     <li>Mobile Internetgebühren</li>
     <li>Nationale Roaming-Gebühren</li>
     <li>Internationale Roaming-Gebühren</li>
     <li>Mehrwert - Service-Gebühren</li>
     <li>Gesamtkosten (Feld für berechnete Nutzungsgebühren)</li>
     <li>GESAMT ZAHLBAR (Feld für berechnete Benutzergebühren)</li>
    </ul> <p>Tabelle - Rechnungen</p> </td>
   <td>Keine Felder</td>
   <td>—</td>
  </tr>
  <tr>
   <td>Einzeln aufgeführte Anrufe - Ausgehend</td>
   <td><p>Spaltennamen:</p>
    <ul>
     <li>Datum</li>
     <li>Zeit</li>
     <li>Zahl</li>
     <li>Dauer</li>
     <li>Gebühren</li>
    </ul> </td>
   <td><p>Alle Werte</p> <p>Tabelle - Anrufe</p> </td>
   <td>Keine Felder</td>
   <td>—</td>
  </tr>
  <tr>
   <td>Jetzt zahlen</td>
   <td>—</td>
   <td>—</td>
   <td>—</td>
   <td>PayNow</td>
  </tr>
  <tr>
   <td>Mehrwert - Service</td>
   <td>—</td>
   <td>—</td>
   <td>—</td>
   <td>Mehrwert - Service</td>
  </tr>
 </tbody>
</table>
