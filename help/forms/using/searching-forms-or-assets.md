---
title: Suchen nach Formularen und Assets
seo-title: Searching for forms and assets
description: Sie können mit der AEM-Suche in Ihrer AEM-Instanz nach Formularen und Assets suchen. Dank der einfachen und der erweiterten Suche können Sie Ihre Assets schnell finden.
seo-description: You can search forms and assets in your AEM instance using AEM search. Basic and advanced search allows you to quickly locate your assets.
uuid: 0928a453-3dc4-448b-9320-dcbf20606dd9
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: e65925ff-1fbf-4da6-bf09-0cf056c86e5a
docset: aem65
role: Admin
exl-id: 1f4f49b7-5f32-47dd-9dc7-a6974faf2bdf
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: ht
source-wordcount: '692'
ht-degree: 100%

---

# Suchen nach Formularen und Assets{#searching-for-forms-and-assets}

Sie können über eine Textzeichenfolge oder eine Textzeichenfolge mit Platzhaltern nach Formularen oder Formular-Assets suchen. Sie können die Suche auch mithilfe der Kriterien einschränken, die in den verschiedenen Kategorien im Suchfeld verfügbar sind.

Wenn Sie eines oder mehrere Kriterien auswählen und eine Textzeichenfolge angeben, wird die Schnittmenge von Text und Kriterien als Suchergebnis zurückgegeben. Die Suchergebnisse sind so gut wie die zur Verfügung gestellten Formular- und Asset-Metadaten.

Klicken Sie auf ![aem6forms_search](assets/aem6forms_search.png), um das Suchfeld ein- oder auszublenden.

## Einfache Suche {#basic-search}

Bei einer einfachen Suche handelt es sich um die Standardsuche, die ohne Angabe von Filtern ausgeführt wird. Eine Volltextsuche in Metadateneigenschaften wird von AEM Forms durchgeführt.

Um eine einfache Suche durchzuführen, geben Sie in das Textfeld die Suchanfrage ein drücken Sie die Enter-Taste. Sie können auch das Platzhalterzeichen (&#42;) eingeben, um eine beliebige Anzahl von Zeichen zu ersetzen.

Adobe Experience Manager sucht in den Metadateneigenschaften nach dem eingegebenen Text und gibt die entsprechenden Ergebnisse wieder. Wenn Sie mehr als ein Wort eingeben, wird beim Suchvorgang für den gesamten Text nach Übereinstimmungen gesucht. 

Beachten Sie bei der einfachen Suche die folgenden Punkte:

* Die Suche wird mithilfe der Formular- und Asset-Metadaten durchgeführt.
* Wenn Sie mehr als ein Wort eingeben, wird beim Suchvorgang für den gesamten Text nach Übereinstimmungen gesucht. 
* Bei der Suche wird die Groß-/Kleinschreibung nicht beachtet. Wenn Sie z. B. `geometrixx` eingeben, werden Assets mit den Titeln `Geometrixx`, `GEOMETRIXX` und `GeoMetRixx` in den Suchergebnissen angezeigt.

* Unvollständige Übereinstimmungen mit einem Wort werden nicht unterstützt. Um mit unvollständigen Zeichenfolgen zu suchen, verwenden Sie den Platzhalter &#42;. Wenn bei der Suchanfrage jedoch eine Übereinstimmung mit einem vollständigen Wort vorliegt, wird das entsprechende Formular bzw. Asset angezeigt.
* Zusätzliche Leerzeichen werden berücksichtigt und während der Suche nicht entfernt. Zum Beispiel ist `My form` nicht die gleiche Suchanfrage wie `My form`.

* Wenn sich die Daten von den Anzeigewerten der Felder in den Metadateneigenschaften abweichen, können Sie Anzeigewerte als Suchparameter nicht verwenden. Beispielsweise können Sie keine Suche auf Basis eines Status, z. B. geändert oder veröffentlicht, durchführen, da diese Eigenschaften in einem anderen Format gespeichert werden.

## Erweiterte Suche {#advanced-search}

In den Suchkriterien können Sie neben der Suchanfrage einige Suchparameter angeben, um die einfache Suche effizienter und fokussierter zu gestalten.

![Suchfeld und Parameter bzw. Filter für die AEM-Formular- und die AEM-Asset-Suche](assets/search_forms_assets.png)

Suchfeld und Parameter bzw. Filter für die Suche nach AEM-Formularen und -Assets

### Asset-Pfad {#asset-path}

Mit einem Asset-Pfad-Filter können Sie die Suchergebnisse auf das aktuelle Verzeichnis beschränken. Wenn die Option „Suche im aktuellen Verzeichnis“ nicht ausgewählt ist, enthalten die Suchergebnisse Assets aus dem Basisverzeichnis. Wenn es sich bei der aktuellen Seite um kein Verzeichnis handelt und die Option „Suche im aktuellen Verzeichnis“ ausgewählt ist, werden bei der Suche die Assets wiedergegeben, die im übergeordneten Verzeichnis vorhanden sind.

### Asset-Änderung {#asset-modification}

Wählen Sie eine der folgenden Optionen, für alle Assets zu durchsuchen, die innerhalb eines bestimmten Zeitraums geändert wurden.

| **Option** | **Beschreibung** |
|---|---|
| Vor zwei Stunden | Durchsuchen Sie alle Assets, die in den letzten zwei Stunden geändert wurden. |
| Vor einer Woche | Durchsuchen Sie alle Assets, die in der letzten Woche geändert wurden. |
| Vor einem Monat | Durchsuchen Sie alle Assets, die in des letzten Monats geändert wurden. |
| Vor einem Jahr | Durchsuchen Sie alle Assets, die im letzten Jahr geändert wurden. |

### Asset-Status {#asset-status}

Sie können mit einem der folgenden Status nach Assets suchen:

* **Veröffentlicht**: Suchen Sie alle veröffentlichten Assets, die nach der Veröffentlichung nicht geändert wurden.

* **Veröffentlichung rückgängig gemacht**: Suchen Sie alle Assets, die nie veröffentlicht werden.

* **Geändert**: Suchen Sie alle Assets, die nach der Veröffentlichung geändert wurden oder deren Veröffentlichung zurückgezogen wurde.

### Asset-Typ {#asset-type}

Sie können beliebig viele Assettypen auswählen. Bei der Suche werden alle ausgewählten Assets gemeinsam zurückgegeben.

<table>
 <tbody>
  <tr>
   <th>Option</th> 
   <th>Beschreibung</th> 
  </tr>
  <tr>
   <td>Formularvorlage<br /> </td> 
   <td>Durchsuchen Sie alle Formularvorlagen.<br /> </td> 
  </tr>
  <tr>
   <td>PDF-Formular</td> 
   <td>Durchsuchen Sie alle PDF-Dokumente.</td> 
  </tr>
  <tr>
   <td>Dokument</td> 
   <td>Durchsuchen Sie alle Dokumente.</td> 
  </tr>
  <tr>
   <td>Adaptives Formular<br /> </td> 
   <td>Durchsuchen Sie alle adaptiven Formulare.</td> 
  </tr>
  <tr>
   <td>Ressource</td> 
   <td>Durchsuchen Sie alle Ressourcen.<br /> </td> 
  </tr>
 </tbody>
</table>

### Tags {#tags}

Tags sind Beschriftungen, die Assets zur Identifikation angehängt werden. Wählen Sie bei der Suche aus der Dropdown-Liste eine beliebige Anzahl an Tags aus oder fügen Sie ggf. benutzerdefinierte Tags hinzu. Das Suchergebnis enthält die Schnittmenge der ausgewählten Tags.
