---
title: Eogenschaften der Correspondence Management-Konfiguration
description: In diesem Thema wird erläutert, wie Sie Asset Composer mit lösungsspezifischen Konfigurationen modifizieren können. In diesem Thema werden die Eigenschaften beschrieben, die Sie bearbeiten können, einschließlich Beschreibung, Standardwerte und akzeptable Werte.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
exl-id: c9c007d0-c545-4738-b11b-4c50986342ee
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 100%

---

# Eogenschaften der Correspondence Management-Konfiguration {#correspondence-management-configuration-properties}

Öffnen Sie folgende URL einem Browser, um diese Eigenschaftenin zu konfigurieren: `https://<server>:<port>/<contextPath>/system/console/configMgr` und wählen Sie **Correspondence Management-Konfigurationen**.

Correspondence Management verfügt über die folgenden Konfigurationseigenschaften:

<table>
 <tbody>
  <tr>
   <th><p><strong>Eigenschaft</strong></p> </th>
   <th><p><strong>Beschreibung</strong></p> </th>
   <th><p><strong>Standard</strong></p> </th>
   <th><p><strong>Zulässige Werte</strong></p> </th>
  </tr>
  <tr>
   <td><p>Einzug</p> </td>
   <td>Einzug bei Modulen<p> </p> </td>
   <td><p>12,7 mm</p> </td>
   <td><p>Beliebige Zahl</p> </td>
  </tr>
  <tr>
   <td>Mindestbreite bei Zahlen</td>
   <td>Mindestbreite für das Aufzählungs-/Zahlenfeld bei nummerierten Listen, mit Ausnahme römischer Zahlen</td>
   <td>8,0 mm</td>
   <td>Beliebige Zahl</td>
  </tr>
  <tr>
   <td><p>Mindestbreite bei römischen Zahlen</p> </td>
   <td><p>Mindestbreite für das Aufzählungs-/Zahlenfeld bei Verwendung römischer Zahlen</p> </td>
   <td><p>12,7 mm</p> </td>
   <td><p>Beliebige Zahl</p> </td>
  </tr>
  <tr>
   <td>Typ der Ausgabedarstellung</td>
   <td>Der Ausgabetyp, den die Anwendung „Korrespondenz erstellen“ zum Rendern der Briefvorschau verwendet. </td>
   <td>HTML-Ausgabedarstellung</td>
   <td>HTML-Ausgabedarstellung/PDF-Ausgabedarstellung</td>
  </tr>
  <tr>
   <td><p>CCR-PDF-Hervorhebung aktivieren</p> </td>
   <td><p>Aktiviert die Hervorhebung in PDF in der Anwendung „Korrespondenz erstellen“</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Typ der Zielhervorhebung</p> </td>
   <td><p>Typ der Zielhervorhebung in der Anwendung „Korrespondenz erstellen“</p> </td>
   <td><p>border</p> </td>
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
   <td><p>1.200</p> </td>
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
   <td><p>Parametername für Umleitungs-URL</p> </td>
   <td><p>Parametername für die Umleitungs-URL im Nachbearbeitungsprozess. Dieser Wert kann ein beliebiger Name für die Zeichenfolge sein.</p> </td>
   <td><p>redirectURL</p> </td>
   <td><p>Beliebiger Name für Zeichenfolge</p> </td>
  </tr>
  <tr>
   <td><p>Typ der gesendeten PDF</p> </td>
   <td><p>Typ der gesendeten PDF (Typ der PDF, die beim Absenden von der Anwendung „Korrespondenz erstellen“ erzeugt wird)</p> </td>
   <td><p>nonInteractive</p> </td>
   <td><p>interaktiv/nicht interaktiv</p> </td>
  </tr>
  <tr>
   <td><p>Datenwörterbuchinstanz optimieren</p> </td>
   <td><p>Aktiviert die optimierte Übertragung der Datenwörterbuchinstanz zwischen Server und Client</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Inkonsistenzen in der Autokorrektur </p> </td>
   <td><p>Wenn diese Funktion aktiviert ist, werden die möglichen Inkonsistenzen in Buchstabenzuweisungen automatisch bearbeitet</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Konfigurierte Datenformate verwenden</p> </td>
   <td><p>Steuert „Konfigurierte Datenformate verwenden“ und „Datenanzeigeformat“</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Datenanzeigeformate</p> </td>
   <td><p>Legt ein bestimmtes Anzeigeformat des Gebietsschemas für Daten fest</p> </td>
   <td><p>locale=en_US; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=truelocale=de_DE; dateFormat=dd-MM-yyyy; numberDecimalSeparator=,; numberGroupSeparator=.; numberUseGroupSeparator=truelocale=fr_FR; dateFormat=dd-MM-yyyy; numberDecimalSeparator=,; numberGroupSeparator= ; numberUseGroupSeparator=truelocale=ja_JP; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=true</p> </td>
   <td><p>--</p> </td>
  </tr>
  <tr>
   <td><p>Datenbearbeitungsformat</p> </td>
   <td><p>Das Format für Daten bearbeiten. Wird verwendet, wenn Daten als Zeichenfolge geschrieben oder Daten aus der Zeichenfolge analysiert werden</p> </td>
   <td><p>locale=en_US; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=true</p> </td>
   <td>--<p> </p> </td>
  </tr>
  <tr>
   <td><p>Briefinstanzen in Veröffentlichungsinstanz verwalten</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion „Briefinstanzen verwalten“ (gilt nur für Veröffentlichungs-Server)</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen.  Bei „false“ werden Prüfprotokolle für alle Aktionen deaktiviert.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Asset-Abruf aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für Asset-Lesevorgänge.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Erstellung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für die Asset-Erstellung</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Aktualisierung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für Asset-Aktualisierungen</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Wiederherstellung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für die Asset-Wiederherstellung</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Veröffentlichung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für die Asset-Veröffentlichung</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Speichern von Briefentwürfen aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für das Speichern von Briefentwürfen</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Senden aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für das Senden von Briefen</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für E-Mails aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für das Senden von Briefen per E-Mail</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Drucken aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für das Drucken von Briefen</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für benutzerdefinierten Versand aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für den benutzerdefinierten Versand von Briefen</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für Anlagendokumente</p> </td>
   <td><p>Parametername für Anlagendokumente, die an den Nachbearbeitungsprozess gesendet werden</p> </td>
   <td><p>inAttachmentDocs</p> </td>
   <td><p>Beliebiger Name für Zeichenfolge</p> </td>
  </tr>
  <tr>
   <td><p>CM-Benutzerstamm</p> </td>
   <td><p>URL des Ordners mit allen Correspondence Management-Benutzerelementen</p> </td>
   <td><p>--</p> </td>
   <td><p>Gültiger Ordner-Speicherort</p> </td>
  </tr>
  <tr>
   <td><p>Brief-Cache-Größe</p> </td>
   <td><p>Geben Sie die maximale Anzahl von Briefen an, die im Cache gespeichert werden sollen.</p> <p>Das Ändern dieses Werts führt zur Bereinigung des <code>in-memory</code>-Caches.</p> </td>
   <td><p>100</p> </td>
   <td><p>Jeder numerische Wert</p> </td>
  </tr>
  <tr>
   <td><p>Brief-Cache aktivieren</p> </td>
   <td><p>Brief-Cache aktivieren/deaktivieren</p> <p>Das Ändern dieses Werts führt zur Bereinigung des <code>in-memory </code>-Caches.</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Reihenfolge von Datenelementen</p> </td>
   <td><p>Hält die Reihenfolge der Datenelemente in der Benutzeroberfläche „Korrespondenz erstellen“ gemäß ihrer Sequenz im Brief bei</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Neuladen unterstützen</p> </td>
   <td><p>Aktivieren/Deaktivieren der Unterstützung des Neuladens in Server-seitig gerenderten Briefen.</p> <p>Die Deaktivierung dieser Option verbessert die Render-Leistung der Briefe.</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> <p> </p> </td>
  </tr>
  <tr>
   <td>Temporärer Ordner </td>
   <td>Speicherort des temporären Ordners.</td>
   <td>acm.tpmFolder</td>
   <td> </td>
  </tr>
  <tr>
   <td>Remote speichern</td>
   <td>Speichert die Briefinstanzen auf dem angegebenen verarbeitenden Autorensystem.</td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Kompatibilitätsoptionen</td>
   <td>Kompatibilitätsoptionen des Formats „configName:configvalue“, durch Kommas getrennt.</td>
   <td>acm.compatibilityOptions</td>
   <td> </td>
  </tr>
  <tr>
   <td><p>Debug-Ordner </p> <p> </p> </td>
   <td>Ordnerpfad im Dateisystem für das Debugging. Wenn der Ordner nicht <code>exists</code>, werden keine Debug-Dumps generiert.</td>
   <td>acm.debugDirectory</td>
   <td> </td>
  </tr>
 </tbody>
</table>
