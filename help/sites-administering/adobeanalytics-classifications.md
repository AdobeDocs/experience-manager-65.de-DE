---
title: Adobe Classifications
description: Erfahren Sie, wie Sie mit Adobe Classifications Classifications Classification-Daten nach Adobe Analytics exportieren können.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 0e675ce8-ba3b-481d-949e-0c85c97054d2
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 49%

---

# Adobe Classifications{#adobe-classifications}

Adobe Classifications führt geplante Exporte von Klassifizierungsdaten in [Adobe Analytics](/help/sites-administering/adobeanalytics.md) durch. Der Ausführer führt eine **com.adobe.cq.scheduled.exporting.Exporter**.

So konfigurieren Sie Folgendes:

1. Wählen Sie unter **Navigation** die Option **Tools** > **Cloud Services** und dann **Legacy-Cloud-Services** aus.
1. Blättern Sie zu **Adobe Analytics** und wählen Sie **Konfigurationen anzeigen** aus.
1. Klicken Sie auf den Link **[+]** neben Ihrer Adobe Analytics-Konfiguration.

1. Im Dialogfeld **Framework erstellen**:

   * Geben Sie einen **Titel** an.
   * Optional können Sie den **Namen** für den Knoten angeben, der die Framework-Details im Repository speichert.
   * Wählen Sie **Adobe Analytics Classifications** aus

   und klicken Sie auf **Erstellen**.

   ![Dialogfeld „Framework erstellen“](assets/aa-25.png)

1. Das Dialogfeld **Classifications-Einstellungen** wird zur Bearbeitung geöffnet.

   ![Dialogfeld „Classifications-Einstellungen“](assets/aa-classifications-settings.png)

   Die Eigenschaften umfassen Folgendes:

   | **Feld** | **Beschreibung** |
   |---|---|
   | Aktiviert | Auswählen **Ja** um die Adobe Classifications-Einstellungen zu aktivieren. |
   | Bei Konflikt überschreiben | Auswählen **Ja** , um Datenkollisionen zu überschreiben. Standardmäßig ist dies auf **Nein**. |
   | Bearbeitete löschen | Wenn auf **Ja** löscht verarbeitete Knoten, nachdem sie exportiert wurden. Der Standardwert ist **False**. |
   | Beschreibung des Exportvorgangs | Geben Sie eine Beschreibung für den Adobe-Classifications-Auftrag ein. |
   | Benachrichtigungs-E-Mail | Geben Sie eine E-Mail-Adresse für Adobe Classifications-Benachrichtigungen ein. |
   | Report Suite | Geben Sie die Report Suite ein, für die der Importauftrag ausgeführt werden soll. |
   | Datensatz | Geben Sie die Kennung der Datensatzrelation ein, für die der Importauftrag ausgeführt werden soll. |
   | Transformator | Wählen Sie aus dem Dropdown-Menü eine Transformatorimplementierung aus. |
   | Datenquelle | Navigieren Sie zum Pfad für den Datencontainer. |
   | Zeitplan exportieren | Wählen Sie den Exportplan aus. Die Standardeinstellung ist alle 30 Minuten. |

1. Klicks **OK** , um Ihre Einstellungen zu speichern.

## Ändern der Seitengröße {#modifying-page-size}

Datensätze werden auf Seiten verarbeitet. Adobe Classifications erstellt standardmäßig Seiten mit einer Seitengröße von 1.000.

Eine Seite kann (gemäß Definition in Adobe Classifications) maximal die Größe 25.000 haben und über die Felix-Konsole geändert werden. Während des Exports sperrt Adobe Classifications den Quellknoten, um gleichzeitige Änderungen zu verhindern. Der Knoten wird nach dem Export, bei Fehlern oder beim Schließen der Sitzung entsperrt.

So ändern Sie die Seitengröße:

1. Navigieren Sie zur OSGI-Konsole unter **https://&lt;Host>:&lt;Port>/system/console/configMgr** und wählen Sie **Adobe AEM Classifications Exporter** aus.

   ![aa-26](assets/aa-26.png)

1. Aktualisieren Sie die **Seitengröße exportieren** Klicken Sie nach Bedarf auf **Speichern**.

## SAINTDefaultTransformer {#saintdefaulttransformer}

>[!NOTE]
>
>Adobe Classifications war früher als SAINT Exporter bekannt.

Ein Exporter kann einen Transformator verwenden, um die Exportdaten in ein bestimmtes Format umzuwandeln. Für Adobe Classifications wird die Unterschnittstelle `SAINTTransformer<String[]>` bereitgestellt, die die Transformatorschnittstelle implementiert. Diese Schnittstelle dient dazu, den Datentyp auf den von der SAINT-API verwendeten Datentyp `String[]` zu beschränken und eine Markierungsschnittstelle für die Suche nach entsprechenden Services für die Auswahl zu erhalten.

In der Standardimplementierung (SAINTDefaultTransformer) werden die untergeordneten Ressourcen der Exporter-Quelle als Datensätze (mit Eigenschaftsnamen als Schlüssel und Eigenschaftswerten als Werte) behandelt. Die Spalte **Schlüssel** wird automatisch als erste Spalte hinzugefügt und enthält den Knotennamen. Eigenschaften mit Namespace (enthalten `:`) werden ignoriert.

*Knotenstruktur:*

* ID-Klassifikation `nt:unstructured`

   * 1 `nt:unstructured`

      * Produkt = Eigener Produktname (Zeichenfolge)
      * Preis = 120,90 (String)
      * Größe = M (Zeichenfolge)
      * Farbe = schwarz (Zeichenfolge)
      * Color^Code = 101 (String)

**SAINT-Kopfzeile und -Datensatz:**

| **Schlüssel** | **Produkt** | **Preis** | **Größe** | **Farbe** | **Farb-Code** |
|---|---|---|---|---|---|
| 1 | Mein Produktname | 120,90 | M | schwarz | 101 |

Die Eigenschaften umfassen Folgendes:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaftspfad</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Transformator</td>
   <td>Klassenname einer SAINTTransformer-Implementierung</td>
  </tr>
  <tr>
   <td>email</td>
   <td>Benachrichtigungs-E-Mail-Adresse</td>
  </tr>
  <tr>
   <td>reportsuites</td>
   <td>Report Suite-IDs, für die der Importauftrag ausgeführt werden soll </td>
  </tr>
  <tr>
   <td>Datensatz</td>
   <td>Datensatzrelations-ID, für die der Importauftrag ausgeführt werden soll. </td>
  </tr>
  <tr>
   <td>description</td>
   <td>Auftragsbeschreibung. <br /> </td>
  </tr>
  <tr>
   <td>Überschreiben</td>
   <td>Flag zum Überschreiben von Datenkollisionen. Der Standardwert ist <strong>false</strong>.</td>
  </tr>
  <tr>
   <td>Checkdivisionen</td>
   <td>Flag zur Überprüfung der Kompatibilität von Report Suites. Der Standardwert ist <strong>true</strong>.</td>
  </tr>
  <tr>
   <td>deleteprocessed</td>
   <td>Flag zum Löschen der verarbeiteten Knoten nach dem Export. Der Standardwert ist <strong>false</strong>.</td>
  </tr>
 </tbody>
</table>

## Automatisieren des Adobe Classifications-Exports {#automating-adobe-classifications-export}

Sie können einen eigenen Workflow erstellen, sodass bei jedem neuen Import der Workflow gestartet wird, um die entsprechenden und korrekt strukturierten Daten in **/var/export/** , damit sie nach Adobe Classifications exportiert werden können.
