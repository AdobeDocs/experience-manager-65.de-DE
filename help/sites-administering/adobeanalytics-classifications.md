---
title: Adobe Classifications
description: Erfahren Sie, wie Sie Adobe Classifications verwenden, um Klassifizierungsdaten in Adobe Analytics zu exportieren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 0e675ce8-ba3b-481d-949e-0c85c97054d2
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 100%

---

# Adobe Classifications{#adobe-classifications}

Adobe Classifications führt geplante Exporte von Klassifizierungsdaten in [Adobe Analytics](/help/sites-administering/adobeanalytics.md) durch. Der Exporter ist eine Implementierung von **com.adobe.cq.scheduled.exporter.Exporter**.

Dies konfigurieren Sie wie folgt:

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
   | Aktiviert | Wählen Sie **Ja**, um die Adobe Classifications-Einstellungen zu aktivieren. |
   | Bei Konflikt überschreiben | Wählen Sie **Ja**, um etwaige Datenkollisionen zu überschreiben. Standardmäßig ist dies auf **Nein** festgelegt. |
   | Bearbeitete löschen | Wenn dies auf **Ja** festgelegt ist, werden verarbeitete Knoten nach dem Export gelöscht. Der Standard hierfür ist **Falsch**. |
   | Beschreibung des Exportvorgangs | Geben Sie eine Beschreibung für den Adobe Classifications-Vorgang ein. |
   | Benachrichtigungs-E-Mail | Geben Sie eine E-Mail-Adresse für Adobe Classifications-Benachrichtigungen ein. |
   | Report Suite | Geben Sie die Report Suite ein, für die der Importvorgang ausgeführt werden soll. |
   | Datensatz | Geben Sie die Datensatzbeziehungs-ID ein, für die der Importvorgang ausgeführt werden soll. |
   | Transformer | Wählen Sie im Dropdown-Menü eine Transformer-Implementierung aus. |
   | Datenquelle | Navigieren Sie zum Pfad für den Daten-Container. |
   | Exportzeitplan | Wählen Sie den Zeitplan für den Export aus. Der Standard ist alle 30 Minuten. |

1. Klicken Sie auf **OK**, um Ihre Einstellungen zu speichern. 

## Ändern der Seitengröße {#modifying-page-size}

Einträge werden seitenweise verarbeitet. Adobe Classifications erstellt standardmäßig Seiten mit einer Seitengröße von 1.000.

Eine Seite kann (gemäß Definition in Adobe Classifications) maximal die Größe 25.000 haben und über die Felix-Konsole geändert werden. Während des Exports sperrt Adobe Classifications den Quellknoten, um gleichzeitige Änderungen zu verhindern. Der Knoten wird nach dem Export, bei einem Fehler oder beim Schließen der Sitzung entsperrt.

So ändern Sie die Seitengröße:

1. Navigieren Sie zur OSGI-Konsole unter **https://&lt;Host>:&lt;Port>/system/console/configMgr** und wählen Sie **Adobe AEM Classifications Exporter** aus.

   ![aa-26](assets/aa-26.png)

1. Aktualisieren Sie die **Seitengröße für den Export** nach Bedarf, und klicken Sie dann auf **Speichern**.

## SAINTDefaultTransformer {#saintdefaulttransformer}

>[!NOTE]
>
>Adobe Classifications war früher als SAINT Exporter bekannt.

Ein Exporter kann einen Transformer verwenden, um die Exportdaten in ein bestimmtes Format umzuwandeln. Für Adobe Classifications wird die Unterschnittstelle `SAINTTransformer<String[]>` bereitgestellt, die die Transformatorschnittstelle implementiert. Diese Schnittstelle dient dazu, den Datentyp auf den von der SAINT-API verwendeten Datentyp `String[]` zu beschränken und eine Markierungsschnittstelle für die Suche nach entsprechenden Services für die Auswahl zu erhalten.

In der Standardimplementierung (SAINTDefaultTransformer) werden die untergeordneten Ressourcen der Exporter-Quelle als Datensätze (mit Eigenschaftsnamen als Schlüssel und Eigenschaftswerten als Werte) behandelt. Die Spalte **Schlüssel** wird automatisch als erste Spalte hinzugefügt und enthält den Knotennamen. Eigenschaften mit Namespace (enthalten `:`) werden ignoriert.

*Knotenstruktur:*

* ID-Klassifikation `nt:unstructured`

   * 1 `nt:unstructured`

      * Produkt = Mein Produktname (Zeichenfolge)
      * Preis = 120,90 (Zeichenfolge)
      * Größe = M (Zeichenfolge)
      * Farbe = schwarz (Zeichenfolge)
      * Color^Code = 101 (Zeichenfolge)

**SAINT-Header und -Eintrag:**

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
   <td>Transformer</td>
   <td>Ein Klassenname einer SAINTTransformer-Implementierung</td>
  </tr>
  <tr>
   <td>email</td>
   <td>Benachrichtigungs-E-Mail-Adresse.</td>
  </tr>
  <tr>
   <td>Report Suites</td>
   <td>Report-Suite-IDs, für die der Importvorgang ausgeführt werden soll. </td>
  </tr>
  <tr>
   <td>Datensatz</td>
   <td>Datensatzbeziehungs-ID, für die der Importvorgang ausgeführt werden soll. </td>
  </tr>
  <tr>
   <td>description</td>
   <td>Auftragsbeschreibung. <br /> </td>
  </tr>
  <tr>
   <td>overwrite</td>
   <td>Flag zum Überschreiben von Datenkollisionen. Der Standardwert lautet <strong>false</strong>. </td>
  </tr>
  <tr>
   <td>checkdivisions</td>
   <td>Flag zum Überprüfen von Report Suites auf Kompatibilität. Der Standardwert lautet <strong>true</strong>.</td>
  </tr>
  <tr>
   <td>deleteprocessed</td>
   <td>Flag zum Löschen der verarbeiteten Knoten nach dem Export. Der Standardwert lautet <strong>false</strong>.</td>
  </tr>
 </tbody>
</table>

## Automatisierung des Exports von Adobe Classifications {#automating-adobe-classifications-export}

Sie können Ihren eigenen Workflow erstellen, sodass alle neuen Importe den Workflow starten, um die entsprechenden und korrekt strukturierten Daten in **/var/export/** zu erstellen, sodass sie in Adobe Classifications exportiert werden können.
