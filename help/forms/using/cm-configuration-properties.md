---
title: Eogenschaften der Correspondence Management-Konfiguration
description: In diesem Thema wird erläutert, wie Sie Asset Composer mit lösungsspezifischen Konfigurationen ändern können. In diesem Thema werden die Eigenschaften beschrieben, die Sie bearbeiten können, einschließlich Beschreibung, Standardwerten und akzeptabler Werte.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
exl-id: c9c007d0-c545-4738-b11b-4c50986342ee
source-git-commit: ab3d016c7c9c622be361596137b150d8719630bd
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 13%

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
   <td>Einzug in Module<p> </p> </td>
   <td><p>12.7mm</p> </td>
   <td><p>Beliebige Zahl</p> </td>
  </tr>
  <tr>
   <td>Mindestbreite der Zahl</td>
   <td>Mindestbreite für das Aufzählungs-/Zahlenfeld bei nummerierten Listen mit Ausnahme römischer Zahlen</td>
   <td>8.0mm</td>
   <td>Beliebige Zahl</td>
  </tr>
  <tr>
   <td><p>Mindestbreite der römischen Zahlen</p> </td>
   <td><p>Mindestbreite für das Aufzählungszeichenfeld bei Verwendung römischer Zahlen</p> </td>
   <td><p>12.7mm</p> </td>
   <td><p>Beliebige Zahl</p> </td>
  </tr>
  <tr>
   <td>Ausgabedarstellungstyp</td>
   <td>Der Ausgabetyp, den die Anwendung "Korrespondenz erstellen"zum Rendern der Briefvorschau verwendet. </td>
   <td>HTML Rendition</td>
   <td>HTML-Ausgabedarstellung/PDF-Ausgabedarstellung</td>
  </tr>
  <tr>
   <td><p>CCR-PDF-Hervorhebung aktivieren</p> </td>
   <td><p>Aktiviert die Hervorhebung auf PDF in der Anwendung "Korrespondenz erstellen"</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Typ der Zielhervorhebung</p> </td>
   <td><p>Typ der Zielhervorhebung in der Anwendung "Korrespondenz erstellen"</p> </td>
   <td><p>border</p> </td>
   <td><p>Rahmen/Füllung/keine</p> </td>
  </tr>
  <tr>
   <td><p>Farbe der Zielhervorhebung</p> </td>
   <td><p>Farbe der Zielhervorhebung in der Anwendung "Korrespondenz erstellen"</p> </td>
   <td><p>90;155;245</p> </td>
   <td><p>Beliebige RGB-Farbe im Format R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Typ der Inhaltshervorhebung</p> </td>
   <td><p>Typ der Inhaltshervorhebung in der Anwendung "Korrespondenz erstellen"</p> </td>
   <td><p>Füllung</p> </td>
   <td><p>Rahmen/Füllung/keine</p> </td>
  </tr>
  <tr>
   <td><p>Farbe der Inhaltshervorhebung</p> </td>
   <td><p>Farbe der Inhaltshervorhebung in der Anwendung "Korrespondenz erstellen"</p> </td>
   <td><p>210;225;245</p> </td>
   <td><p>Beliebige RGB-Farbe im Format R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Typ der Feldhervorhebung</p> </td>
   <td><p>Typ der Feldhervorhebung in der Anwendung "Korrespondenz erstellen"</p> </td>
   <td><p>fill</p> </td>
   <td><p>Rahmen/Füllung/keine</p> </td>
  </tr>
  <tr>
   <td><p>Farbe der Feldhervorhebung</p> </td>
   <td><p>Farbe der Feldhervorhebung in der Anwendung "Korrespondenz erstellen"</p> </td>
   <td><p>210;225;245</p> </td>
   <td><p>Beliebige RGB-Farbe im Format R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Zeitlimit für Anwendungen</p> </td>
   <td><p>Zeitlimit für Anwendungen in Sekunden</p> </td>
   <td><p>1200</p> </td>
   <td><p>Beliebige Zahl</p> </td>
  </tr>
  <tr>
   <td><p>PDF-Dokumentparametername</p> </td>
   <td><p>Parametername für PDF-Dokument in der Nachverarbeitung</p> </td>
   <td><p>inPDFDoc</p> </td>
   <td><p>Beliebiger Name der string-Variablen</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für XML-Daten</p> </td>
   <td><p>Parametername für XML-Dokument (Daten) in der Nachverarbeitung</p> </td>
   <td><p>inXMLDoc</p> </td>
   <td><p>Beliebiger Name der string-Variablen</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für XDP-Dokument</p> </td>
   <td><p>Parametername für XDP-Dokument, das an den Nachprozess gesendet wird</p> </td>
   <td><p>inXDPDoc</p> </td>
   <td><p>Beliebiger Name der string-Variablen</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für Umleitungs-URL</p> </td>
   <td><p>Parametername für die Umleitungs-URL, die vom Nachprozess gesendet wird. Dieser Wert kann ein beliebiger Name für die Zeichenfolge sein</p> </td>
   <td><p>redirectURL</p> </td>
   <td><p>Beliebiger Name der string-Variablen</p> </td>
  </tr>
  <tr>
   <td><p>PDF Submit Type</p> </td>
   <td><p>PDF Submit Type (Typ der PDF, die beim Senden von der Anwendung "Korrespondenz erstellen"erzeugt wird)</p> </td>
   <td><p>nonInteractive</p> </td>
   <td><p>interaktiv/nicht interaktiv</p> </td>
  </tr>
  <tr>
   <td><p>Datenwörterbuchinstanz optimieren</p> </td>
   <td><p>Aktiviert eine optimierte Übertragung der Datenwörterbuchinstanz zwischen Server und Client</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Inkonsistenzen in der Autokorrektur </p> </td>
   <td><p>Bei Aktivierung werden die möglichen Inkonsistenzen in Briefzuweisungen automatisch verarbeitet</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Konfigurierte Datenformate verwenden</p> </td>
   <td><p>Steuert, ob konfigurierte Datenbearbeitungsformate und Datenanzeigeformat verwendet werden sollen.</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Datenanzeigeformate</p> </td>
   <td><p>Gibt das Gebietsschema-spezifische Anzeigeformat für Daten an</p> </td>
   <td><p>locale=en_US; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=truelocale=de_DE; dateFormat=dd-MM-yyyy; numberDecimalSeparator=,; numberGroupSeparator=.; numberUseGroupSeparator=truelocale=fr_FR; dateFormat=dd-MM-yyyy; numberDecimalSeparator=,; numberGroupSeparator= ; numberUseGroupSeparator=truelocale=ja_JP; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=true</p> </td>
   <td><p>—</p> </td>
  </tr>
  <tr>
   <td><p>Datenbearbeitungsformat</p> </td>
   <td><p>Format für Daten bearbeiten. Dies wird beim Schreiben von Daten als Zeichenfolge oder beim Analysieren von Daten aus Zeichenfolge verwendet</p> </td>
   <td><p>locale=en_US; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=true</p> </td>
   <td>--<p> </p> </td>
  </tr>
  <tr>
   <td><p>Verwalten von Briefinstanzen bei der Veröffentlichung</p> </td>
   <td><p>Aktivierung/Deaktivierung der Funktion "Brief verwalten"(nur für Veröffentlichungsserver verfügbar)</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen. Bei "false"werden Prüfprotokolle für alle Aktionen deaktiviert</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Elementprüfung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für Asset-Lesevorgänge</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für die Asset-Erstellung</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Elementaktualisierung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für die Asset-Aktualisierung</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Elementwiederherstellung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für Elementwiederherstellung</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Veröffentlichung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für Asset-Veröffentlichung</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>SaveAsDraft-Prüfung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für das Speichern von Briefentwürfen</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Prüfung für Übermittlung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für das Senden von Briefen</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Email Audit aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für E-Mail-Nachrichten</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Aktivieren der Druckprüfung</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für das Drucken von Briefen</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Benutzerdefinierte Versandprüfung aktivieren</p> </td>
   <td><p>Aktiviert/Deaktiviert die Funktion zum Prüfen für benutzerdefinierte Brieferstellung</p> </td>
   <td><p>Nein</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Parametername für Anlagendokumente</p> </td>
   <td><p>Parametername für Anlagendokumente, die an den Nachprozess gesendet werden</p> </td>
   <td><p>inAttachmentDocs</p> </td>
   <td><p>Beliebiger Name der string-Variablen</p> </td>
  </tr>
  <tr>
   <td><p>CM-Benutzerstamm</p> </td>
   <td><p>URL des Ordners mit allen Correspondence Management-Benutzerelementen</p> </td>
   <td><p>--</p> </td>
   <td><p>Gültiger Ordnerspeicherort</p> </td>
  </tr>
  <tr>
   <td><p>Briefcache-Größe</p> </td>
   <td><p>Geben Sie die maximale Anzahl von Briefen an, die im Cache gespeichert werden sollen.</p> <p>Das Ändern dieses Werts führt zur Bereinigung  <code>in-memory</code> cache.</p> </td>
   <td><p>100</p> </td>
   <td><p>Beliebiger numerischer Wert</p> </td>
  </tr>
  <tr>
   <td><p>Briefcache aktivieren</p> </td>
   <td><p>Briefcache aktivieren/deaktivieren</p> <p>Das Ändern dieses Werts führt zur Bereinigung  <code>in-memory </code> cache.</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Reihenfolge von Datenelementen</p> </td>
   <td><p>Hält die Reihenfolge der Datenelemente in der Benutzeroberfläche "Korrespondenz erstellen"gemäß ihrer Sequenz im Brief bei</p> </td>
   <td><p>Ja</p> </td>
   <td><p>true/false</p> </td>
  </tr>
  <tr>
   <td><p>Neuladen unterstützen</p> </td>
   <td><p>Aktivieren/deaktivieren Sie die Neuladungsunterstützung in serverseitig gerenderten Briefen.</p> <p>Die Deaktivierung dieser Option verbessert die Renderleistung der Briefe.</p> </td>
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
   <td>Remote Speichern</td>
   <td>Speichert die Briefinstanzen auf dem angegebenen Verarbeitungsautor.</td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Kompatibilitätsoptionen</td>
   <td>Kompatibilitätsoptionen des Formats "configName:configvalue", durch Kommas getrennt.</td>
   <td>acm.compatibilityOptions</td>
   <td> </td>
  </tr>
  <tr>
   <td><p>Debug-Ordner </p> <p> </p> </td>
   <td>Ordnerpfad im Dateisystem für das Debugging. Ist der Ordner nicht  <code>exists</code>, es werden keine Debug-Dumps generiert.</td>
   <td>acm.debugDirectory</td>
   <td> </td>
  </tr>
 </tbody>
</table>
