---
title: Eogenschaften der Correspondence Management-Konfiguration
seo-title: Eogenschaften der Correspondence Management-Konfiguration
description: In diesem Thema wird beschrieben, wie Sie Asset Composer mit lösungsspezifischen Konfigurationen ändern können. In diesem Thema werden die Eigenschaften, die Sie bearbeiten können, mit ihrer Beschreibung, ihren Standardwerten und ihren zulässigen Werten erläutert.
seo-description: In diesem Thema wird beschrieben, wie Sie Asset Composer mit lösungsspezifischen Konfigurationen ändern können. In diesem Thema werden die Eigenschaften, die Sie bearbeiten können, mit ihrer Beschreibung, ihren Standardwerten und ihren zulässigen Werten erläutert.
uuid: 6b401d51-9332-459b-b751-42a9b5a1462d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: f2955419-c680-44a7-9913-c594b4577551
feature: Korrespondenzverwaltung
exl-id: c9c007d0-c545-4738-b11b-4c50986342ee
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 96%

---

# Eogenschaften der Correspondence Management-Konfiguration {#correspondence-management-configuration-properties}

Um diese Eigenschaften zu konfigurieren, öffnen Sie die folgende URL in einem Browser: `https://<server>:<port>/<contextPath>/system/console/configMgr` und wählen Sie **Correspondence Management-Konfigurationen** aus.

Correspondence Management verfügt über die folgenden Konfigurationseigenschaften:

<table>
 <tbody>
  <tr>
   <th><p><strong>Eigenschaft</strong></p> </th>
   <th><p><strong>Beschreibung</strong></p> </th>
   <th><p><strong>Default</strong></p> </th>
   <th><p><strong>Zulässige Werte</strong></p> </th>
  </tr>
  <tr>
   <td><p>Einzug</p> </td>
   <td>Einzug bei Modulen<p> </p> </td>
   <td><p>12.7mm</p> </td>
   <td><p>Beliebige Zahl</p> </td>
  </tr>
  <tr>
   <td>Mindestbreite von Nummer</td>
   <td>Mindestbreite bei nummerierten Listen für das Aufzählungszeichenfeld, mit Ausnahme römischer Zahlen</td>
   <td>8.0mm</td>
   <td>Beliebige Zahl</td>
  </tr>
  <tr>
   <td><p>Mindestbreite von römischen Zahlen</p> </td>
   <td><p>Mindestbreite für das Aufzählungszeichenfeld bei Verwendung von römischen Zahlen</p> </td>
   <td><p>12.7 mm</p> </td>
   <td><p>Beliebige Zahl</p> </td>
  </tr>
  <tr>
   <td>Darstellungs-Typ</td>
   <td>Der von der Anwendung „Korrespondenz erstellen“ für die Ausgabe der Briefvorschau verwendete Darstellungstyp. </td>
   <td>HTML-Darstellung</td>
   <td>HTML-Darstellung/PDF-Darstellung</td>
  </tr>
  <tr>
   <td><p>Aktivieren der PDF-Hervorhebungen in Anwendung „Korrespondenz erstellen“</p> </td>
   <td><p>Aktiviert die Hervorhebungen in PDF-Dateien in der Anwendung „Korrespondenz erstellen“ </p> </td>
   <td><p>true</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Typ der Zielhervorhebung</p> </td>
   <td><p>Typ der Zielhervorhebung in der Anwendung „Korrespondenz erstellen“</p> </td>
   <td><p>Rahmen</p> </td>
   <td><p>Rahmen/Füllung/keine</p> </td>
  </tr>
  <tr>
   <td><p>Farbe der Zielhervorhebung</p> </td>
   <td><p>Farbe der Zielhervorhebung in der Anwendung „Korrespondenz erstellen“</p> </td>
   <td><p>90;155;245</p> </td>
   <td><p>Beliebige RGB-Farbe im Format R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Typ der Inhaltshervorhebung</p> </td>
   <td><p>Typ der Inhaltshervorhebung in der Anwendung „Korrespondenz erstellen“</p> </td>
   <td><p>Füllung</p> </td>
   <td><p>Rahmen/Füllung/keine</p> </td>
  </tr>
  <tr>
   <td><p>Farbe der Inhaltshervorhebung</p> </td>
   <td><p>Farbe der Inhaltshervorhebung in der Anwendung „Korrespondenz erstellen“</p> </td>
   <td><p>210;225;245</p> </td>
   <td><p>Beliebige RGB-Farbe im Format R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Typ der Feldhervorhebung</p> </td>
   <td><p>Typ der Feldhervorhebung in der Anwendung „Korrespondenz erstellen“</p> </td>
   <td><p>Füllung</p> </td>
   <td><p>Rahmen/Füllung/keine</p> </td>
  </tr>
  <tr>
   <td><p>Farbe der Feldhervorhebung</p> </td>
   <td><p>Farbe der Feldhervorhebung in der Anwendung „Korrespondenz erstellen“</p> </td>
   <td><p>210;225;245</p> </td>
   <td><p>Beliebige RGB-Farbe im Format R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Zeitlimit für die Anwendung</p> </td>
   <td><p>Zeitlimit für die Anwendung in Sekunden</p> </td>
   <td><p>1200</p> </td>
   <td><p>Beliebige Zahl</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für PDF-Dokument</p> </td>
   <td><p>Parametername für PDF-Dokument in der Nachverarbeitung</p> </td>
   <td><p>inPDFDoc</p> </td>
   <td><p>Beliebiger Name für Zeichenfolge</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für XML-Daten</p> </td>
   <td><p>Parametername für XML-Dokument (Daten) in der Nachverarbeitung</p> </td>
   <td><p>inXMLDoc</p> </td>
   <td><p>Beliebiger Name für Zeichenfolge</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für XDP-Dokument</p> </td>
   <td><p>Parametername für XDP-Dokument in der Nachverarbeitung</p> </td>
   <td><p>inXDPDoc</p> </td>
   <td><p>Beliebiger Name für Zeichenfolge</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für umgeleitete URL</p> </td>
   <td><p>Parametername für umgeleitete URL in der Nachverarbeitung. Dieser Wert kann ein beliebiger Name für die Zeichenfolge sein.</p> </td>
   <td><p>redirectURL</p> </td>
   <td><p>Beliebiger Name für Zeichenfolge</p> </td>
  </tr>
  <tr>
   <td><p>Typ der gesendeten PDF</p> </td>
   <td><p>Typ der gesendeten PDF (Typ der PDF, die beim Senden der Anwendung „Korrespondenz erstellen“ erzeugt wird)</p> </td>
   <td><p>nonInteractive</p> </td>
   <td><p>interaktiv/nicht interaktiv</p> </td>
  </tr>
  <tr>
   <td><p>Datenwörterbuchinstanz optimieren</p> </td>
   <td><p>Aktiviert optimierte Übertragung der Datenwörterbuchinstanz zwischen Server und Client</p> </td>
   <td><p>true</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Inkonsistenzen in der Autokorrektur </p> </td>
   <td><p>Wenn diese Funktion aktiviert ist, werden die möglichen Inkonsistenzen in Briefzuweisungen automatisch bearbeitet.</p> </td>
   <td><p>true</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Konfigurierte Datenformate verwenden</p> </td>
   <td><p>Steuert „Konfigurierte Datenformate verwenden“ und „Datenanzeigeformat“</p> </td>
   <td><p>true</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Datenanzeigeformate</p> </td>
   <td><p>Legt bestimmtes Anzeigeformat des Gebietsschemas für Daten fest</p> </td>
   <td><p>locale=en_US; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=truelocale=de_DE; dateFormat=dd-MM-yyyy; numberDecimalSeparator=,; numberGroupSeparator=.; numberUseGroupSeparator=truelocale=fr_FR; dateFormat=dd-MM-yyyy; numberDecimalSeparator=,; numberGroupSeparator= ; numberUseGroupSeparator=truelocale=ja_JP; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=true</p> </td>
   <td><p>—</p> </td>
  </tr>
  <tr>
   <td><p>Datenbearbeitungsformate</p> </td>
   <td><p>Bearbeitet das Format für Daten Wird verwendet, wenn Daten als Zeichenfolge geschrieben oder Daten aus der Zeichenfolge analysiert werden</p> </td>
   <td><p>locale=en_US; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=true</p> </td>
   <td>—<p> </p> </td>
  </tr>
  <tr>
   <td><p>Briefinstanzen in der Veröffentlichungsinstanz verwalten</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion „Briefinstanzen verwalten“ (gilt nur für Veröffentlichungsserver)</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen. Bei „false“ werden Prüfprotokolle für alle Aktionen deaktiviert</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Elementabruf aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für Elementabruf</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Elementerstellung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für die Elementerstellung</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Elementaktualisierung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für Elementaktualisierung</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Elementwiederherstellung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für Elementwiederherstellung</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Elementveröffentlichung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für Elementveröffentlichung</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für das Speichern von Briefentwürfen</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für das Speichern von Briefentwürfen</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für das Senden von Briefen aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für das Senden von Briefen</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für das Senden von Briefen per E-Mail aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für das Senden von Briefen per E-Mail</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für das Drucken von Briefen aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für das Drucken von Briefen</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für die benutzerdefinierte Zustellung von Briefen aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für benutzerdefinierte Zustellung von Briefen</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für Anlagendokumente</p> </td>
   <td><p>Parametername für Anlagendokumente in der Nachverarbeitung</p> </td>
   <td><p>inAttachmentDocs</p> </td>
   <td><p>Beliebiger Name für Zeichenfolge</p> </td>
  </tr>
  <tr>
   <td><p>URL für CM-Benutzerelemente</p> </td>
   <td><p>URL des Ordners, der alle Correspondence Management-Benutzer-Assets enthält</p> </td>
   <td><p>—</p> </td>
   <td><p>Zulässiger Ordnerpfad</p> </td>
  </tr>
  <tr>
   <td><p>Briefcache-Größe</p> </td>
   <td><p>Geben Sie die maximale Anzahl von Briefen an, die im Cache aufbewahrt werden sollen.</p> <p>Das Ändern dieses Werts führt zur Bereinigung  <code>in-memory</code> cache.</p> </td>
   <td><p>100</p> </td>
   <td><p>Ein beliebiger numerischer Wert</p> </td>
  </tr>
  <tr>
   <td><p>Briefcache aktivieren</p> </td>
   <td><p>Briefcache aktivieren/deaktivieren</p> <p>Das Ändern dieses Werts führt zur Bereinigung   <code>in-memory </code> zwischenspeichern.</p> </td>
   <td><p>true</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Reihenfolge von Datenelementen</p> </td>
   <td><p>Hält die Reihenfolge von Datenelementen in der Benutzeroberfläche „Korrespondenz erstellen“ gemäß der Reihenfolge im Brief bei</p> </td>
   <td><p>true</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Neuladen</p> </td>
   <td><p>Aktivieren/deaktivieren Sie das Neuladen von serverseitig gerenderten Briefen.</p> <p>Die Deaktivierung dieser Funktion verbessert die Renderleistung der Briefe.</p> </td>
   <td><p>false</p> </td>
   <td><p>true/false</p> <p> </p> </td>
  </tr>
  <tr>
   <td>Temporärer Ordner  </td>
   <td>Pfad des Temp-Ordners.</td>
   <td>acm.tpmFolder</td>
   <td> </td>
  </tr>
  <tr>
   <td>Remote Speichern</td>
   <td>Speichert die Briefinstanzen auf dem angegebenen verarbeitenden Autorensystem.</td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Kompatibilitätsoptionen</td>
   <td>Kompatibilitätsoptionen des Formats „configname:configvalue“, durch Kommas getrennt.</td>
   <td>acm.compatibilityOptions</td>
   <td> </td>
  </tr>
  <tr>
   <td><p>Debug-Ordner </p> <p> </p> </td>
   <td>Ordnerpfad im Dateisystem für das Debugging. Ist der Ordner nicht   <code>exists</code>, werden keine Debug-Dumps generiert.</td>
   <td>acm.debugDirectory</td>
   <td> </td>
  </tr>
 </tbody>
</table>
